# REST APIs

Using the same web hosting platform as the rest of Universal Dashboard, you can create REST APIs that have no user interface component. You can accept input from the user from URLs and HTTP request bodies and accept four different HTTP methods.

## Creating new endpoints

To create a new endpoint, you will use the New-UDEndpoint cmdlet. This cmdlet lets you specify the URL, the HTTP method and the Endpoint Script Block that will process the data.

To create a simple endpoint to return data, you can create an with the following script.

```text
$Endpoint = New-UDEndpoint -Url "/process" -Method "GET" -Endpoint {
    Get-Process | ForEach-Object { [PSCustomObject]@{ Name = $_.Name; ID=$_.ID} }  | ConvertTo-Json
}
Start-UDRestApi -Endpoint $Endpoint
```

This endpoint could be invoked with Invoke-RestMethod like so. Notice that all URLs are prefixed with "api".

```text
Invoke-RestMethod -Uri http://localhost:80/api/process
```

### Endpoints with variables in the URL

In REST, resources are identified by the variables in the path of the URL. Universal Dashboard, supports variables by specifying a colon \(:\) in the URL path. These variables are then passed to the script block of the endpoint.

For example, if you wanted to get a process by ID, you could specify the ID variable in the URL and add a $ID parameter to the param block of the Endpoint script block.

```text
New-UDEndpoint -Url "/process/:id" -Method "GET" -Endpoint {
    param($Id)

    Get-Process -Id $Id | ForEach-Object { [PSCustomObject]@{ Name = $_.Name; ID=$_.ID} }  | ConvertTo-Json
}
```

### Using RegEx in Endpoint URLs

Instead of simple variables, you can instead use RegEx expressions to match URL patterns. This is handy for integration with systems like the DSC PullServer that provides complex URL patterns. Named groups will be passed to the endpoint as parameters. You'll need to include the `-EvaluateUrlAsRegex` parameter to `New-UDEndpoint`.

```text
New-UDEndpoint -Url "Nodes\(AgentId='(?<AgentId>.*)'\)" -Method PUT -Endpoint {
    param (
        $AgentId
    )
} -EvaluateUrlAsRegex
```

### Endpoints that take data from the HTTP request body

HTTP methods like POST take data from the request body. UD supports form data and string data. Form data will automatically be parsed and provided to the script block via parameters.

```text
$Endpoint = New-UDEndpoint -Url "/process" -Method "POST" -Endpoint {
     param($FilePath, $Arguments)

     Start-Process -FilePath $FilePath -ArgumentsList $Arguments
}
Start-UDRestApi -Endpoint $Endpoint 

Invoke-RestMethod -Uri http://localhost:80/api/process -Method POST -Body @{FilePath = "code"; Arguments = "script.ps1" }
```

Additionally, you can specify any string value and that value will be provided to the script block via the Body parameter.

```text
$Endpoint = New-UDEndpoint -Url "/process" -Method "POST" -Endpoint {
     param($Body)

     $Parameters = $Body | ConvertFrom-Json

     Start-Process -FilePath $Body.FilePath -Arguments $Body.Arguments
}
Start-UDRestApi -Endpoint $Endpoint 

Invoke-RestMethod -Uri http://localhost:80/api/process -Method POST -Body (@{FilePath = "code"; Arguments = "script.ps1" } | ConvertTo-Json)
```

## Managing the REST API Servers

Endpoints will need to be passed to Start-UDRestApi to create a new REST API server. Start-UDRestApi has all the same hosting options as Start-UDDashboard. It supports HTTPS and can be hosted in Azure and IIS.

```text
Start-UDRestApi -Port 80 -Endpoint $MyEndpoints
```

Just as with Get-UDDashboard and Stop-UDDashboard, you can locate and stop any running dashboards with Get-UDRestApi and Stop-UDRestApi.

```text
Get-UDRestApi -Name "ProcessApi" | Stop-UDRestApi
```

You can also add REST API endpoints to existing dashboards with the Endpoint parameter of Start-UDDashboard. This allows you to have a user interface for your dashboard but also provide REST API endpoints on the same port.

```text
Start-UDDashboard -Endpoint $MyEndpoints -Dashboard $MyDashboard
```

## Returning XML

By default, REST API endpoints set the Content-Type HTTP header to application/json. Any web-client consuming your endpoint will assume the content returned is formatted as JSON. In order to return content as XML, you can use the Set-UDContentType cmdlet to set the content type to application/xml.

```text
 New-UDEndpoint -Url "project" -Method "GET" -Endpoint {
      Set-UDContentType "application/xml"

      "<Project name=`"test`"></Project>"
 }
```

If you would like to support both JSON and XML in the same endpoint, you can also use Get-UDContentType to get the requested content type.

```text
New-UDEndpoint -Url "project" -Method "GET" -Endpoint {
    $ContentType = Get-UDContentType
    if ($ContentType -eq "application/json") {
       "{Project:{name:'test'}}"
    } else {
       Set-UDContentType "application/xml" 
       "<Project name=`"test`"></Project>"
    }
}
```

