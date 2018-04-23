---
title: "Soy Templates"
description: ""
layout: "guide"
icon: "code-file"
weight: 7
---

###### Soy templates are a templating system for dynamically generating re-usable HTML and UI elements in both Java and JavaScript. Soy templates are also referred to as [Closure templates](https://developers.google.com/closure/templates/). For the client side, Soy templates are precompiled into efficient JavaScript.Soy templates use an easy templating language that also lets you use MetalJS components. With all these benefits and more, Soy can be a good front-end tool to have in your utility belt.

<article id="1">

## Quick Guide

1. Create a Soy File
- All files that contain Closure Templates end with the .soy file extension and are called Soy files. 

2. Write your template
- Each Soy file needs a namespace declaration at the top of the file. It must be declared before any templates are declared:
```javascript
{namespace examples.simple}
```

- For templates that need parameters, these must be declared in JavaDoc style immediately before the template:
```java
/*
 * Renders a table of selected AJS.params
 * @param userName
 */
```

- Parameters use this syntax within the template:
```javascript
{$userName}
```

- Here a example of a template that says Hello to a specific user:
```javascript
{namespace simples.example}
/*
 /Renders a Hello message.
 /@param userName
 */
{template .helloWorld}
<div>Hello {$userName}!</div>
{/template}
```

3. Call the Soy template in a separate JavaScript file
- You can now invoke the template by simply calling a javascript function with your previously declared namespace. In this example it would be something like:

```javascript
//display a hello message on the page
var template = simples.example.helloWorld({userName: "John Smith"});
AJS.messages.info(jQuery("body"), {body: template, closeable: true});
```


 More details, access [closure.templates](https://developers.google.com/closure/templates/).


</article>
