# Scheduled Endpoints

{% hint style="info" %}
Required Version: 1.6.0 or later
{% endhint %}

Scheduled endpoints allow you to run PowerShell script blocks on an interval. You can easily run a job every minute, hour or day. You can also got as far as you want and specify a schedule using a CRON expression.

## Uses for scheduling

Scheduling can be useful for collecting data from monitored systems. This data can be stored in a database or within a cache variable. This can greatly improve the performance of your dashboard. Rather than looking up the data when the user visits the dashboard, the data is collected in the background and loaded from the cache.

For example, you could create a scheduled endpoint to retrieve the count of modules on your machine. To expose this data, you could use a REST API. In the below example we have a cached value that is refreshed every hour and a value that is executed every time the REST API is invoked.

```text
$Schedule = New-UDEndpointSchedule -Every 1 -Hour

$EveryHour = New-UDEndpoint -Schedule $Schedule -Endpoint {
    $Cache:ModuleCount = (Get-Module -ListAvailable).Count
}

$moduleCount = New-UDEndpoint -Url "/moduleCount" -Endpoint {
    (Get-Module -ListAvailable).Count
}

$CachedModuleCount = New-UDEndpoint -Url "/cached-moduleCount" -Endpoint {
    $Cache:ModuleCount
}

$dashboard = New-UDDashboard -Title "Test" -Content {
    New-UDCounter -Title "Test" -Id "Counter" -Endpoint {
        $Cache:ModuleCount
    } -AutoRefresh -RefreshInterval 1
} 

$Server = Start-UDDashboard -Port 10001 -Dashboard $dashboard -Endpoint @($EveryHour, $ModuleCount, $CachedModuleCount)
```

You can see from the execution of these APIs that the cached version is much faster. The cached version can be called 100 times in 30 seconds. The uncached version takes 13 minutes to process 100 requests in sequence.

```text
PS C:\Users\adamr> measure-command { 1..100 | % { Invoke-RestMethod http://localhost:10001/api/cached-moduleCount }  }


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 29
Milliseconds      : 50
Ticks             : 290500385
TotalDays         : 0.000336227297453704
TotalHours        : 0.00806945513888889
TotalMinutes      : 0.484167308333333
TotalSeconds      : 29.0500385
TotalMilliseconds : 29050.0385



PS C:\Users\adamr> measure-command { 1..100 | % { Invoke-RestMethod http://localhost:10001/api/moduleCount }  }


Days              : 0
Hours             : 0
Minutes           : 12
Seconds           : 55
Milliseconds      : 253
Ticks             : 7752531632
TotalDays         : 0.00897283753703704
TotalHours        : 0.215348100888889
TotalMinutes      : 12.9208860533333
TotalSeconds      : 775.2531632
TotalMilliseconds : 775253.1632
```

## Defining a schedule

To define a schedule, use the `New-UDEndpointSchedule` cmdlet. A simple schedule to run every 10 minutes could be defined as follows.

```text
New-UDEndpointSchedule -Every 10 -Minute
```

Changing the switch parameter used defines which unit of time to run the schedule on. For example, the following schedule runs every 10 seconds.

```text
New-UDEndpointSchedule -Every 10 -Second
```

To run a more complex schedule, you can use a CRON expression. For more information, see the [Quartz.NET documentation](https://www.quartz-scheduler.net/documentation/quartz-3.x/tutorial/crontrigger.html) about CRON expressions that it supports.

For example, this CRON expression runs at 10:15am every Monday, Tuesday, Wednesday, Thursday and Friday.

```text
New-UDEndpointSchedule -Cron '0 15 10 ? * MON-FRI'
```

## Creating a scheduled endpoint

The `New-UDEndpoint` cmdlet has a `-Schedule` parameter that accepts the object created by `New-UDEndpointSchedule`.

Just pass in your schedule and define your script block for the endpoint to execute.

In the below example, we are look up all the computers in our domain every 10 minutes.

```text
$Schedule = New-UDEndpointSchedule -Every 10 -Minute 
$Endpoint = New-UDEndpoint -Schedule $Schedule -Endpoint {
   $Cache:Computers = Get-ADComputer
}
```

The `$Cache:Computers` variable can now be used in any endpoint within your dashboard. This include endpoints for charts, counters or a REST API.

Finally, you need to pass the `$Endpoint` into the `-Endpoint` parameter of `Start-UDDashboard`.

```text
Start-UDDashboard -Endpoint $Endpoint -Dashboard $Dashboard
```

