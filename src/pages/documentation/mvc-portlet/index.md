---
title: "Liferay MVC Portlet"
description: ""
layout: "guide"
icon: "code-file"
weight: 4
---

###### {$page.description}

<article id="1">

## MVC Portlet

Web applications are often developed following the Model View Controller (MVC) pattern. But Liferay has developed a different implementation for the MVC model. The Liferay MVC portlet framework is light, it hides part of the complexity of portlets, and it makes the most common operations easier..

In MVC pattern, there are three layers:
- **Model:** The model layer holds the application data and logic for manipulating it.
- **View:** The view layer contains logic for displaying data.
- **Controller:** The middle man in the MVC pattern, the Controller contains logic for passing the data back and forth between the view and the model layers.

<img src="/images/portlet.png" />

Liferay’s applications are divided into multiple discrete modules. With Service Builder, the model layer is generated into a **service** and an  **api** module. That accounts for the model in the MVC pattern. The view and the controller share a module, the  **web** module.

In a larger application, Liferay provides MVC command classes to break up your controller functionality:
- **MVCActionCommand:** Use -ActionCommand classes to hold each of your portlet actions, which are invoked by action URLs.
- **MVCRenderCommand:** Use -RenderCommand classes to hold a render method that dispatches to the appropriate JSP, by responding to render URLs.
- **MVCResourceCommand:** Use -ResourceCommand classes to execute resource serving in your MVC portlet, by responding to resource URLs.

</article>


<article id="2">

## MVC Action Command

Liferay’s MVC framework lets you split your portlet’s action methods into separate classes. This can be very helpful in portlets that have many actions. Each action URL in your portlet’s JSPs then calls the appropriate action class when necessary.

First, use the <portlet:actionURL> tag to create the action URL in your JSP. For example, the edit blog entry action in Liferay’s Blogs app is defined in the **edit_entry.jsp** file as follows:

```xml
<portlet:actionURL name="/blogs/edit_entry" var="editEntryURL" />
```

When the action URL is triggered, the matching action class processes the action. Implement the action by creating a class that implements the **MVCActionCommand** interface. To avoid writing oodles of boilerplate code, your ***MVCActionCommand** class should extend the **BaseMVCActionCommand** class instead of implementing **MVCActionCommand** directly. The **BaseMVCActionCommand** class already implements **MVCActionCommand** and provides many useful method implementations. Naming your **MVCActionCommand** class after the action it performs is a good convention. For example, if your action edits some kind of entry, you could name its class **EditEntryMVCActionCommand**.

Your ***MVCActionCommand** class must also have a **@Component** annotation like the following. Set the property **javax.portlet.name** to your portlet’s internal ID, and the property **mvc.command.name** to the value of the **name** property in your JSP’s matching **actionURL**. To register the component in the OSGi container as using the **MVCActionCommand** class, you must set the **service** property to **MVCActionCommand.class**:

```Javascript
@Component(
    immediate = true,
    property = {
        "javax.portlet.name=your_portlet_name_YourPortlet",
        "mvc.command.name=/your/jsp/action/url"
    },
    service = MVCActionCommand.class
)
public class YourMVCActionCommand extends BaseMVCActionCommand {
  // implement your action
}
```

For example, this is the **@Component** annotation for the Blogs app’s **EditEntryMVCActionCommand** class:

```javascript
@Component(
    immediate = true,
    property = {
        "javax.portlet.name=" + BlogsPortletKeys.BLOGS,
        "javax.portlet.name=" + BlogsPortletKeys.BLOGS_ADMIN,
        "javax.portlet.name=" + BlogsPortletKeys.BLOGS_AGGREGATOR,
        "mvc.command.name=/blogs/edit_entry"
    },
    service = MVCActionCommand.class
)
public class EditEntryMVCActionCommand extends BaseMVCActionCommand {
    // the app's edit blog entry action implementation
}
```
Note that you can use multiple **javax.portlet.name** values to indicate the component works with multiple portlets.

In your ***MVCActionCommand** class, process the action by overriding the **BaseMVCActionCommand** class’s doProcessAction method. This method takes **javax.portlet.ActionRequest** and **javax.portlet.ActionResponse** parameters that you can use to process your action. Your **MVCActionCommand** class should also contain any other code required to implement your action. 

</article>

<article id="3">

## MVC Render Command

MVCRenderCommand is used to respond to portlet render URLs. To use MVC render commands, you need these things:
- An implementation of the MVCRenderCommand interface.
- A portlet render URL in your view layer.
- A Component that publishes the MVCRenderCommand service, with two properties

##### Implementing MVCRenderCommand
What is it you want to do when a portlet render URL is invoked? Using the **mvcRenderCommandName** parameter, direct the request to an **MVCRenderCommand** implementation. Now override the **render** method.

Some **MVCRenderCommand** will simply render a particular JSP. Here’s what **BlogsViewMVCRenderCommand** looks like:

```js
@Override
public String render(
    RenderRequest renderRequest, RenderResponse renderResponse) {

    return "/blogs/view.jsp";
}
```
Sometimes you’ll want to add logic to render a certain JSP based on one or more conditions:

```js
@Override
public String render(
    RenderRequest renderRequest, RenderResponse renderResponse)
    throws PortletException {

    try {
        ActionUtil.getEntry(renderRequest);
    }
    catch (Exception e) {
        if (e instanceof NoSuchEntryException ||
            e instanceof PrincipalException) {

            SessionErrors.add(renderRequest, e.getClass());

            return "/hello/error.jsp";
        }
        else {
            throw new PortletException(e);
        }
    }

    return "/hello/edit_entry.jsp";
}
```

If there’s an error caught following the call to **ActionUtil.getEntry** in the code above, the error.jsp is rendered. If the call is returned without an exception being caught, **edit_entry.jsp** is rendered.

How does a request get directed to your MVC render command? Using a portlet render URL.

##### Creating a Portlet Render URL

You can generate a render URL for your portlet using the \<portlet:renderURL>\ taglib. To invoke your MVC render command from the render URL, you need to specify the parameter **mvcRenderCommandName** with the same value as your Component property **mvc.command.name**.

For example, you can create a URL that directs the user to a page with a form for editing an entry like this (in a JSP):

```xml
<portlet:renderURL var="editEntryURL">
    <portlet:param name="mvcRenderCommandName" value="/hello/edit_entry" />
    <portlet:param name="entryId" value="<%= String.valueOf(entry.getEntryId()) %>" />
</portlet:renderURL>
```

Now the request will contain a parameter named **mvcRenderCommandName**. To find the proper MVC render command, the OSGi runtime needs to have a **mvc.command.name** property with a matching value.

##### Registering the MVC Render Command

In order to respond to a particular render URL, you need an **MVCRenderCommand** Component that with two properties:

```Js
javax.portlet.name=" + HelloWorldPortletKeys.HELLO_WORLD,"
mvc.command.name=/hello/edit_entry
```
Using the above properties as an example, any portlet render URL for the portlet that includes a parameter called **mvcRenderCommand** with the value **/hello/edit_entry** will be handled by this **MVCRenderCommand**.

The Component must also publish a **MVCRenderCommand.class** service to the OSGi runtime. Here’s a basic Component that publishes an MVC render command:

```Js
@Component(
    immediate = true,
    property = {
       "javax.portlet.name=" + HelloWorldPortletKeys.HELLO_WORLD,
       "mvc.command.name=/hello/edit_entry"
    },
    service = MVCRenderCommand.class
)
public class EditEntryMVCRenderCommand implements MVCRenderCommand {
```

One command can be used by one portlet, as the example above shows. If you want, one command can be used for multiple portlets by adding more **javax.portlet.name entries** in the property list. Likewise, multiple commands can invoke the MVC command class by adding more **mvc.command.name** entries. If you’re really feeling wild, you can specify multiple portlets and multiple command URLs in the same command component, like this:

```Js
@Component(
    immediate = true,
    property = {
       "javax.portlet.name=" + HelloWorldPortletKeys.HELLO_MY_WORLD,
       "javax.portlet.name=" + HelloWorldPortletKeys.HELLO_WORLD,
       "mvc.command.name=/hello/edit_super_entry",
       "mvc.command.name=/hello/edit_entry"
    },
    service = MVCRenderCommand.class
)
```

 More details, access [dev.liferay](https://dev.liferay.com/develop/tutorials/-/knowledge_base/7-0/liferay-mvc-portlet).

</article>
