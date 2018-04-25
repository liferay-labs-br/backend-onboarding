---
title: "Modularity and OSGI"
description: ""
layout: "guide"
icon: "code-file"
weight: 3
---

###### {$page.description}

<article id="1">

## Modularity and OSGI

Modularity refers to a software/Web application that may be divided into smaller modules. Software modularity indicates that the number of application modules are capable of serving a specified business domain. Some of the modularity benefits for the software are: distinct functionality, dependencies, encapsulation and reusability.

Liferay Portal is modular too. It comprises code modules created and tested independently and in parallel. It’s a platform on which modules and modular applications are installed, started, used, stopped, and uninstalled. Liferay Portal’s components use the OSGi modularity standard.

Modules are the basic unit of modularity for applications. They act as containers for the application’s features and functionality. These self-contained units are deployed within Liferay’s OSGI Container. In order to deploy a module, it must be packaged in a bundle.

<img src="/images/osgi-apps.png" />

An OSGI bundle is nothing but a JAR file with extra meta data. A bundle contains java classes, a manifest file and other resources (JSPs, properties files, text data). So we can say that every OSGI bundle is JAR file, but reverse is not true. That means that if you want to convert a JAR file into bundle it's necessary to add extra metadata into the MANIFEST.MF file. These extra meta data are known as OSGI Headers, key elements which turns a normal JAR file into a Bundle.

<img src="/images/osgi-module.png" />

OSGI Bundle Life Cycle:

**INSTALLED:** The bundle has been installed into the OSGi container, but some required bundle dependencies are missing. A bundle in this state can’t be started.

**RESOLVED:** All Java classes that the bundle needs are available. This state indicates that the bundle is either ready to be started or has stopped. 

**STARTING:** The bundle is being started, the `BundleActivator.start` method has been called but the start method has not yet returned. When the bundle has an activation policy, the bundle will remain in the STARTING state until the bundle is activated according to its activation policy.

**ACTIVE:** The bundle has been successfully activated and is running. Its Bundle Activator start method has been called and returned.

**STOPPING:** The bundle is being stopped. The `BundleActivator.stop` method has been called but the stop method has not yet returned.

**UNINSTALLED:** The bundle has been uninstalled. It cannot move into another state.

<img src="/images/osgi.png" />


 More details, access [dev.liferay](https://dev.liferay.com/develop/tutorials/-/knowledge_base/7-0/modularity-and-osgi).

</article>



