### [What are good sources present on the web for learning Adobe AEM? - Quora](https://www.quora.com/What-are-good-sources-present-on-the-web-for-learning-Adobe-AEM)

Before you get started with CQ. You should understand the basics beneath it.

- Read about OSGI (Open Services Gateway Initiative).
	- [ ] [Hello, OSGi, Part 1: Bundles for beginners](http://www.javaworld.com/article/2077837/java-se/hello--osgi--part-1--bundles-for-beginners.html)[OSGi in a nutshell](http://gravity.sourceforge.net/servicebinder/osginutshell.html)
- Read about working of Sling
	- [ ] [Apache Sling - The Sling Engine](http://sling.apache.org/documentation/the-sling-engine.html)
	- [ ] [Apache Sling - Architecture](http://sling.apache.org/documentation/the-sling-engine/architecture.html)
	- [ ] [Index - Apache Sling - Apache Software Foundation](https://cwiki.apache.org/confluence/display/SLING/Index)
- JCR 
	- [ ] Once your are done with these, dig a bit into Java Content Repository (JCR) implementation in CQ 
	- [ ] and how to make repository queries in CQ.
- By now, you would have known:
	- [ ] Resource Resolution `cq:template/page/component` The hierarchy of modules in CQ
- Now is the time to take a deep dive and start with practicals. I would suggest to learn first about adding/overlaying JSPs and JavaScripts first. Since they do not require you to add annotations and are fairly direct it should be easy to write one.
	- [ ] Before you are ready to go, read about creating components [Components - docs.adobe.com](https://docs.adobe.com/docs/en/cq/5-6-1/developing/components.html)
	- [ ] Also look at some of the best practices for writing JSPs [My CQ JSP Development Best Practises |  6D Labs](http://labs.6dglobal.com/blog/2013-08-13/my-cq-jsp-development-best-practises/)
- Try out an Hello World example
	- [ ] Move ahead to adding Servlets [Sling OSGI Track pt 6: Sling Servlets I](http://in-the-sling.blogspot.in/2008/09/sling-osgi-track-pt-6-sling-servlets-i.html)
	- [ ] Learn about Handlers, Event Management and then I think you would automatically catch up everything else.



Sling 是 Best of Breed （最佳组合）

- Apache Felix (OSGi)
- Apache Jackrabbit (JCR)
- REST

Sling Post Servlet （一站式网站内容 CRUD 解决方案）

One stop shop for Content CRUD：[Apache Sling - Manipulating Content - The SlingPostServlet (servlets.post)](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html)

## SlingPostServlet Operations[¶](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html#slingpostservlet-operations "Permanent link")

The SlingPostServlet is actually just a front-end to the actual operations. To select the actual operation to execute, the `:operation` request parameter is used. Out of the box（开箱即用）, the SlingPostServlet supports the following operations:

（结合 REST CRUD 理解）

* property not set or empty -- Create new content or modify existing content
* `delete` -- Remove existing content
* `move` -- Move existing content to a new location
* `copy` -- Copy existing content to a new location
* `import` -- Import content structures from JSON/XML/Zip
* `nop` -- Explicitly requests to do nothing and just sets the response status
* `checkin` - Check in a versionable node
* `checkout` - Check out a versionable node

All these operations always operate on the resource of the request as returned by `SlingHttpServletRequest.getResource()`. Some operations require additional parameters to be set to operate completely.

### [Comparing Sling API CRUD to Sling Post Servlet¶](http://sling.apache.org/documentation/the-sling-engine/sling-api-crud-support.html#comparing-sling-api-crud-to-sling-post-servlet)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469540299914.png)

### 实例

Create/Modify

curl -u admin:admin -Fmulti=one -Fmulti=two http://localhost:8080/content/sample

Copy/Move

curl -u admin:admin -F":operation=copy" -F":dest=/content/target" http://localhost:8080/content/sample

Delete

curl -u admin:admin -F":operation=delete" http://localhost:8080/content/target

### Resource Resolution

> How do I get what I want how I want it?

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469536058080.png)

详细举例：[Apache Sling - URL decomposition](http://sling.apache.org/documentation/the-sling-engine/url-decomposition.html)

via [Sling Cheatsheet - docs.adobe.com](https://docs.adobe.com/content/docs/en/cq/5-6-1/developing/sling_cheatsheet.html)

### [How Sling Resource Resolution is done in AEM | AEM CQ5 Tutorials](http://www.aemcq5tutorials.com/tutorials/sling-resource-resolution-aem/)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469536186814.png)

### Dispatching Requests

> how a request is processed in Sling?

[Apache Sling - Dispatching Requests](http://sling.apache.org/documentation/the-sling-engine/dispatching-requests.html)

- Servlet Container gets request and forwards to OSGi HttpService
- OSGi HttpService looks for responsible registered Servlet or resource (see 102.4 of the OSGi compendium)
- OSGi HttpService calls handleSecurity of the HttpContext associated with the servlet/resource.
- After getting a response the HttpService either terminates the request

之后就是 Sling 的事情？OSGi 是其基础，在其之前？

### Everything is content.

- Configuration
- Scripts
- Assets
- Everything...

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469536274750.png)

## OSGi (Open Service Gateway Initiative): 
[OSGi™ Alliance – The Dynamic Module System for Java](https://www.osgi.org/)

[OSGi - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/OSGi)：一个基于Java语言的服务（业务）规范——OSGi服务平台（Service Platform）。目前该平台逐渐成为一个为室内、交通工具、移动电话和其他环境下的所有类型的网络设备的应用程序和服务进行传递和远程管理的开放式服务平台。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469539342406.png)

该规范和核心部分是一个框架，其中定义了**应用程序的生命周期模式和服务注册**。基于这个框架定义了大量的OSGi服务：日志、配置管理、偏好，HTTP（运行servlet）、XML分析、设备访问、软件包管理、许可管理、星级、用户管理、IO连接、连线管理、Jini和UPnP。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469537478121.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469537609984.png)


2003年Eclipse选择 OSGi（标准集束框架）作为其插件的底层运行时架构。

- [Hello, OSGi, Part 1: Bundles for beginners | JavaWorld](http://www.javaworld.com/article/2077837/java-se/java-se-hello-osgi-part-1-bundles-for-beginners.html)
- [首页-OSGi中文社区 | 促进Java模块化开发技术传播](http://www.osgi.com.cn/)
- [OSGi入门教程 | OSGi基础概念 | 天码营](http://course.tianmaying.com/osgi-toturial/lesson/osgi-concept#0)

### Getting Start with OSGi

The Open Services Gateway Initiative (OSGi), also known as the Dynamic Module System for Java, defines defines an architecture for developing and deploying modular applications and libraries.

Similar to the Java Servlet and EJB specifications, the OSGi specification defines two things: a set of services that an OSGi container must implement and a contract between the container and your application. Developing on the OSGi platform means first building your application using OSGi APIs, then deploying it in an OSGi container.

[OSGi in a nutshell](http://gravity.sourceforge.net/servicebinder/osginutshell.html)

The framework can be divided in two main elements:
- A services platform. 
- A deployment infrastructure. 

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469539378883.png)

although only the service registry belongs to the services platform. In the service orientation interaction, service providers publish service descriptions, and service requesters discover services and bind to the service providers. Publication and discovery are based on a service description.


### OSGi containers

let's say you're developing a complex Web application. You want to break the application into multiple modules: one module for the view layer, another for the DAO layer, and a third module for the data access layer. Using an embedded OSGi container to manage the cross-dependencies of these modules would enable you to update your DAO layer (say from slow DAO to fast DAO) without restarting your application.

> What's DAO layer?

In computer software, a **data access object** (**DAO**) is an object that provides an abstract interface to some type of database or other persistence mechanism. By mapping application calls to the persistence **layer**, **DAO** provide some specific data operations without exposing details of the database.

via [Data access object - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Data_access_object) 

As long as your application is compliant with the OSGi specification it should be able to run in any OSGi-compliant container.

### Apache Felix 

[Apache Felix](http://www.javaworld.com/article/2077837/java-se/java-se-hello-osgi-part-1-bundles-for-beginners.html#resources) is the open source OSGi container from the Apache Software Foundation. At the time of writing this container is not fully compliant with the OSGI R4 specification.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1468053191213.png)

Apache Felix is a community effort to implement the OSGi Framework and Service platform and other interesting OSGi-related technologies under the Apache license. **The OSGi specifications originally targeted embedded devices and home services gateways, but they are ideally suited for any project interested in the principles of modularity, component-orientation, and/or service-orientation.** OSGi technology combines aspects of these aforementioned principles to define a **dynamic service deployment** framework that is amenable to remote management.

已经瞧过的名词：

- [HTTP Service](http://felix.apache.org/documentation/subprojects/apache-felix-http-service.html) - An implementation of the OSGi HTTP Whiteboard and Http Service specification.
- [Web Console](http://felix.apache.org/documentation/subprojects/apache-felix-web-console.html) - A simple tool to inspect and manage OSGi framework instances using your favorite Web Browser.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469624952179.png)


### Bundles 即 Module (& console)

In OSGi, software is distributed in the form of a bundle. A bundle consists of Java classes and other resources that deliver functions to device owners, as well as providing services and packages to other bundles.

[Developing a Hello World bundle: Bundles for beginners, Creating, executing, and managing bundles in an OSGi container](http://www.javaworld.com/article/2077837/java-se/java-se-hello-osgi-part-1-bundles-for-beginners.html?page=2)

The OSGi console is a command-line interface to the OSGi container. It allows you to do things like start, stop, install bundles, and update or delete bundles.

In some development scenarios this could mean writing a lot of infrastructure code. [Spring Dynamic Modules for OSGi Service Platforms](http://www.javaworld.com/article/2077837/java-se/java-se-hello-osgi-part-1-bundles-for-beginners.html?page=5#resources) project, which simplifies development of Spring-based OSGi bundles.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469538900948.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469538931943.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469538951333.png)


