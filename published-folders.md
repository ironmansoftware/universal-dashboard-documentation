# Published Folders

## Publishing a folder

You can publish a folder by specifying the path to the folder. The RequestPath is the path that the web server will server the files. 

```text
$Folder = Publish-UDFolder -Path C:\data\ -RequestPath "/config"

$Dashboard = New-UDDashboard -Title "Published Folders" -Content {}

Start-UDDashboard -Dashboard $Dashboard -Port 9999 -PublishedFolder $Folder
```

You can download a file by invoking the request path.

```text
C:\> Invoke-WebRequest -Uri http://localhost:9999/config/hi.txt


StatusCode        : 200
StatusDescription : OK
Content           : Hello
RawContent        : HTTP/1.1 200 OK
                    Accept-Ranges: bytes
                    Content-Length: 5
                    Content-Type: text/plain
                    Date: Sat, 03 Nov 2018 03:15:34 GMT
                    ETag: "1d473237a178b85"
                    Last-Modified: Sat, 03 Nov 2018 03:15:31 GMT
                    Server: ...
```

