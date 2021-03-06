---
title: "Service Builder"
description: "An application without reliable business logic or persistence isn’t much of an application at all. Unfortunately, writing your own persistence code often takes a great deal of time. Fortunately, Liferay provides the Liferay Service Builder to generate it for you. But, you can still write your own persistence code if you wish. And if you choose to use Service Builder, you can edit and customize the code it generates. Regardless of how you produce your persistence code, you can then use it to implement your app’s business logic."
layout: "guide"
icon: "code-file"
weight: 5
---

###### {$page.description}

<article id="2">

## What is Service Builder?

Liferay Service Builder is a tool which is generally used to generate code to interact with database. Liferay Service Builder auto generate service layer code to interact with underlying database. The service builder tool takes xml file (its called service.xml) as an input and generate code based on the input provided in service.xml. This section explains the basics of liferay service builder.
Service Builder is a model-driven code generation tool built by Liferay that allows developers to define custom object models called entities. Service Builder generates a service layer through object-relational mapping (ORM) technology that provides a clean separation between your object model and code for the underlying database.

Besides that, Service Builder takes an XML file as input and generates the necessary model, persistence and service layers for your application. These layers provide a clean separation of concerns. Service Builder generates most of the common operations on the database, such as: create, read, update, find. 

Some of the main benefits of using Service Builder are:
- Integration with Liferay
- Automatically generated model, persistence, and service layers
- Automatically generated local and remote services
- Automatically generated Hibernate and Spring configurations
- Support for generating finder methods for entities and finder methods that account for permissions
- Built-in entity caching support
- Support for custom SQL queries and dynamic queries
- Saved development time

Liferay uses Service Builder to generate all of its internal database persistence code. In fact, all of Liferay’s services, both local and remote, are generated by Service Builder. Additionally, the service [modules](https://github.com/liferay/liferay-portal/tree/7.0.x/modules) in Liferay are generated by Service Builder. Service Builder’s use in Liferay Portal demonstrates it to be a robust and reliable tool. 

One of the main ways Service Builder saves development time is by completely eliminating the need to write and maintain database access code. To generate a basic service layer, you only need to create a **service.xml** file and run Service Builder. This generates a new service **.jar** file for your project. 

The generated service .jar file includes a model layer, a persistence layer, a service layer and related infrastructure. These distinct layers represent a healthy separation of concerns:
- **Model Layer:** define objects to represent the project’s entities.
- **Persistence Layer:** save and retrieve entities from the database.
- **Service Layer:** expose CRUD and related methods for the entities as an API.

Each entity generated by Service Builder contains a model implementation class. Each entity also contains a local service implementation class, a remote service implementation class, or both, depending on how you configure Service Builder in your **service.xml** file. Customizations and business logic can be implemented in these three classes; in fact, these are the only classes generated by Service Builder that are intended to be customized. 

Ensuring that all customizations take place in only a few classes makes Service Builder projects easy to maintain. The local service implementation class is responsible for calling the persistence layer to retrieve and store data entities. Local services contain the business logic and access the persistence layer. They can be invoked by client code running in the same Java Virtual Machine. Remote services usually have additional code for permission checking and are meant to be accessible from anywhere over the Internet or your local network. Service Builder automatically generates the code necessary to allow access to the remote services. The remote services generated by Service Builder include SOAP utilities and can be accessed via SOAP or JSON.

Another way Service Builder saves development time is by providing Spring and Hibernate configurations for the project. Service Builder uses Spring dependency injection for making service implementation classes available at runtime and uses Spring AOP for database transaction management. Service Builder also uses the Hibernate persistence framework for object-relational mapping. As a convenience to developers, Service Builder hides the complexities of using these technologies. Developers can take advantage of Dependency Injection (DI), Aspect Oriented Programming (AOP), and Object-Relational Mapping (ORM) in their projects without having to manually set up a Spring or Hibernate environment or make any configurations.

Another benefit of using Service Builder is that it provides support for generating finder methods. Finder methods retrieve entity objects from the database based on specified parameters. It is only necessary to specify the kinds of finder methods to be generated in the **service.xml** configuration file and Service Builder does the rest.

Beyond that, Service Builder also provides built-in caching support. Liferay caches objects at three levels: *entity*, *finder*, and *Hibernate*. By default, Liferay uses Ehcache as an underlying cache provider for each of these cache levels. However, this is configurable via portal properties.  

Service Builder is a flexible tool. It automates many of the common tasks associated with creating database persistence code but it doesn’t prevent you from creating custom SQL queries or custom finder methods. Service Builder allows developers to define custom SQL queries in an XML file and to implement custom finder methods to run the queries. This could be useful, for example, for retrieving specific pieces of information from multiple tables via an SQL join. Service Builder also supports retrieving database information via dynamic query. Liferay’s dynamic query API leverages Hibernate’s criteria API.

In summary, Service Builder generates distinct model, persistence and service layers, local and remote services, Spring and Hibernate configurations, and related infrastructure without requiring any manual intervention by developers. It also allows basic SQL queries and finder methods to be generated and ones that filter results, taking Liferay’s permissions into account. Service Builder also provides support for entity and query caching. Finally, Service Builder is not a restrictive tool: it allows custom SQL queries and finder methods to be added and it also supports dynamic query.

 More details, access [dev.liferay](https://dev.liferay.com/develop/tutorials/-/knowledge_base/7-0/service-builder).

</article>
