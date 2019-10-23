## Clipboard 

You can copy data to the clipboard using the `Set-UDClipboard` cmdlet. It needs to be used within an Endpoint and cannot be called from a top-level content block. 

```
New-UDButton -Text 'Copy to Clipboard' -OnClick {
    Set-UDClipboard -Data 'Copied text'
}
```

## Redirection 

You can redirect users to different pages using `Invoke-UDRedirect`. It needs to be used within an Endpoint and cannot be called from a top-level content block. If you specify the `-OpenInNewWindow` switch parameter, it will open in a new tab or window. 

```
New-UDButton -Text 'Open Google' -OnClick {
    Invoke-UDRedirect -Url https://google.com -OpenInNewWindow
}
```