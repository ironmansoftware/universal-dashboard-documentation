# PowerShell Elements

## Static Elements

The `New-UDElement` cmdlet can be used to create HTML tags that define the markdown for a custom component. `New-UDElement` can be nested and attributes can be added.

A simple custom component may be defined such as this.

```text
New-UDElement -Tag "a" -Attributes @{
href = "https://www.poshud.com"
target = "_self"
} -Content {"Poshud"}
```

This custom component would define a React class in JavaScript that would eventually translate into an HTML link with the following markup.

```text
<a href="https://www.poshud.com" target="_self">Poshud</a>
```

The `Content` parameter can define text as well as nested elements. For example, if you wanted to define a [Materialize Preloader](http://materializecss.com/preloader.html), you would need to define the following HTMl.

```text
<div class="progress">
<div class="determinate" style="width: 70%"></div>
</div>
```

To define the same component using `New-UDElement`, you could use the following script.

```text
New-UDElement -Tag "div" -Attributes @{ className = "progress" } -Content {
New-UDElement -Tag "div" -Attributes @{ className = "determinate"; style=@{width = "70%"}
}
```

For some examples of custom components, visit [GitHub](https://github.com/ironmansoftware/ud-material-design/blob/master/UniversalDashboard.MaterialDesign.psm1).

## Dynamic Elements

All elements created with `New-UDElement` can be managed within any endpoint or event handler. In order to manage a component you need to specify an Id.

```text
New-UDElement -Tag span -Id "targetSpan" -Content { "My Span" }
```

The above span could now be managed within any endpoint. You can use the following cmdlets to get data, update elements, add children or remove the element entirely.

### Getting data from an element

To get data from an element, use the `Get-UDElement` cmdlet to return the state of the element. You will receive the attributes and content of that element. The content may be another element or a string.

In any endpoint, simply call `Get-UDElement` with the `-Id` parameter.

```text
New-UDCounter -Title "Value of text box" -AutoRefresh -Endpoint {
    (Get-UDElement -Id txtNumber).Attributes["value"]
}
```

### Setting data on an element

From any endpoint, you can call `Set-UDElement` to update the attributes and content of an element. You need to specify the Id and the values you would like to update.

```text
Set-UDElement -Id "txtName" -Attributes @{
    width = '100px'
}
```

The above call sets the width of the txtName to 100 pixels.



```text
Set-UDElement -Id "txtName" -Content {"Hello World"}
```

The above call sets the content of an element to "Hello World"

### Adding Child Elements

You can add additional content to an existing element by using the `Add-UDElement` cmdlet. It appends the element to the current set of child elements for the specified parent.

For example, assume you had a collection of paragraphs in a div.

```text
New-UDElement -Tag div -Id parentDiv -Content {
    New-UDElement -Tag p -Content { "Paragraph 1" }
    New-UDElement -Tag p -Content { "Paragraph 2" }
    New-UDElement -Tag p -Content { "Paragraph 3" }
}
```

In an endpoint, you can add an element, such as a new paragraph, using `Add-UDElement`.

```text
Add-UDElement -ParentId parentDiv -Content {
    New-UDElement -Tag p -Content { "Paragraph 4" }
}
```

### Clearing Child Elements

You can clear the child elements of a parent by using the `Clear-UDElement` cmdlet.

For example, assume you had a collection of paragraphs in a div.

```text
New-UDElement -Tag div -Id parentDiv -Content {
    New-UDElement -Tag p -Content { "Paragraph 1" }
    New-UDElement -Tag p -Content { "Paragraph 2" }
    New-UDElement -Tag p -Content { "Paragraph 3" }
}
```

In an endpoint, you can add an element, such as a new paragraph, using `Add-UDElement`.

```text
Clear-UDElement -Id parentDiv
```

### Removing elements

You can remove an element completely by using the `Remove-UDElement` cmdlet.

You simply need to pass in the Id of the target element to remove in order to remove it from the UI.

```text
Remove-UDElement -Id elementToRemove
```

### Broadcasting updates to all connected clients

When a user uses a Universal Dashboard application, a websocket is opened between the client and the server. Each web socket maintains a connection ID. When using the element cmdlets to update the client UI, the connection ID is used to identify which client to send UI updates to.

Sometimes, like in a chatroom when a user posts a message, there is a need to update the UI for all connected clients. All of the element cmdlets support a `-Broadcast` parameter to perform the UI update across all connected clients.

