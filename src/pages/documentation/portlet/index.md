---
title: "Portlet"
description: ""
layout: "guide"
icon: "code-file"
weight: 3
---

###### {$page.description}

<article id="1">

## Portlet

Web apps in Liferay Portal are called portlets. Like many web apps, portlets process requests and generate responses. In the response, the portlet returns content (e.g. HTML, XHTML) for display in browsers. One key difference is that portlets run in a portion of the web page, it means you only need to worry about the application because any interface component is handled by other components. Another difference is that portlets run only in a portal server, like the one in Liferay Portal. Portlets can therefore use the portal’s existing support for user management, authentication, permissions, page management, and more. This frees you to focus on developing the portlet’s core functionality. In many ways, writing your application as a portlet is easier than writing a standalone application.

<img src="/images/portlet.png" />

One page can contain several different portlets, for example: a page in a community site could have a calendar portlet for community events, an announcements portlet for important announcements, and a bookmarks portlet for links of interest to the community. And because the portal controls page layout, you can reposition and resize one or more portlets on a page without altering any portlet code. Doing all this in other types of web apps would require manual re-coding.

Since the portlets are components, in other words, they are independent functional objects, it means that will have a lifecycle:

- **Activate:** when a component is being started.
- **Active:** the component is started and available.
- **Deactivate:** the component is being stopped.

<img src="/images/portlet-lc.png" />

Portlets handle requests in multiple phases. This makes portlets much more flexible than servlets. Each portlet phase executes different operations:

- **AInit:** It is the first phase a potlet goes through when it’s deployed. During this phase, portlets typically initialize any backend resources or perform any one-time activities that they need.
- **ARender:** Generates the portlet’s contents based on the portlet’s current state. When this phase runs on one portlet, it also runs on all other portlets on the page. The Render phase runs when any portlets on the page complete the Action or Event phases.
- **AAction:** In response to a user action, performs some operation that changes the portlet’s state. The Action phase can also trigger events that are processed by the Event phase. Following the Action phase and optional Event phase, the Render phase then regenerates the portlet’s contents.
- **AEvent:** Processes events triggered in the Action phase. Events are used for IPC. Once the portlet processes all events, the portal calls the Render phase on all portlets on the page.
- **AResource-serving:** Serves a resource independent from the rest of the lifecycle. This lets a portlet serve dynamic content without running the Render phase on all portlets on a page. The Resource-serving phase handles AJAX requests.
- **ADestroy:** This phase is called by the portlet container when the portlet is uninstalled. This phase is designed to allow the portlet to release any resources it needs to and to save its state if necessary.

The render phase can be further subdivided into different modes, which gives users an easy way to access a particular page in a portlet. Modes distinguish the portlet’s current function:

- **View mode:** The portlet’s standard mode. Use this mode to access the portlet’s main functionality.
- **Edit mode:** The portlet’s configuration mode. Use this mode to configure a custom view or behavior. For example, the Edit mode of a weather portlet could let you choose a location to retrieve weather data from.
- **Help mode:** A mode that displays the portlet’s help information.

<img src="/images/portlet-render.png" />

Most modern applications use View Mode only. Portlet window states control the amount of space a portlet takes up on a page. Window states mimic window behavior in a traditional desktop environment:

- **Normal:** The portlet can be on a page that contains other portlets. This is the default window state.
- **Maximized:** The portlet takes up an entire page.
- **Minimized:** Only the portlet’s title bar shows.

Compared to servlets, portlets also have some other key differences. Since portlets only render a portion of a page, tags like \<html>\, \<head>\, and \<body> aren’t allowed. And because you don’t know the portlet’s page ahead of time, you can’t create portlet URLs directly. Instead, the portlet API gives you methods to create portlet URLs programmatically. Also, because portlets don’t have direct access to the **javax.servlet.ServletRequest**, they can’t read query parameters directly from a URL. Portlets instead access a **javax.portlet.PortletRequest** object. The portlet specification only provides a mechanism for a portlet to read its own URL parameters or those declared as public render parameters. Liferay Portal does, however, provide utility methods that can access the **ServletRequest** and query parameters. Portlets also have a portlet filter available for each phase in the portlet lifecycle. Portlet filters are similar to servlet filters in that they allow request and response modification on the fly.

 More details, access [dev.liferay](https://dev.liferay.com/develop/tutorials/-/knowledge_base/7-0/portlets).


</article>



