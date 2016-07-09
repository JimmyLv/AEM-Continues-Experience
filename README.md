# AEM-Continues-Experience

learning AEM...

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1468060034522.png)

> Adobe Experience Manager is a web-based client-server system for building, managing and deploying commercial websites and related services. It combines a number of infrastructure-level and application-level functions into a single integrated package.

- 基于 Java，基于 Web 的 client-server 全栈解决方案
- 涵盖网站和相关服务的管理、部署，一揽子方法（环境定制化：[完美契合您的 Adobe Experience Manager 需求 | Rackspace](https://www.rackspace.com/zh-cn/web-content-management/adobe-experience-manager)）
- 集成软件套装，包含 infrastructure 和 application 层面的工具和服务，前者是后者的基础

Infrastructure

1.  **Web Application Server**: 可以单独集成 Jetty web server，也可以用于第三方
2.  **Web Application Framework**: 简化 RESTful 面向对象的 Web 应用，即内容优先
4.  **Content Repository**: AEM 引入了 JCR，用于处理非结构化或半结构化的数据；不仅包含内容，还有相关代码、模板等所有内部数据

一些新概念：

- Sling Web Application Framework
    + [Apache Sling首页、文档和下载 - Web内容存储框架 - 开源中国社区](http://www.oschina.net/p/apache+sling)
    + [Build Your Own CMS with Apache Sling](http://www.slideshare.net/rpaulin1/build-your-own-cms-with-apache-sling) Slideshare 很多好东西 -> 右边
- Java Content Repository (JCR)
    + [David Nuescheler 谈 JCR 和 REST](http://www.infoq.com/cn/articles/nuescheler-jcr-rest)
- AEM "instance"
    + 运行在服务器上的一个 AEM 拷贝
    + Author + Publish
        *  前者用于创建、上传、编辑和管理，准备好内容之后就会复制到 publish
        *  后者就是用于发布于公众
        *  两者只是配置不同，通过 Dispatcher 来安装？
    + Dispatcher 就是一个静态内容服务器，可以使用页面缓存提高性能
- [OSGi](https://www.osgi.org/developer/specifications/) 即 [Apache Felix](http://felix.apache.org/)，更底层的东西
    + 一句话，The Dynamic Module System for Java

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1468053191213.png)

综上，[Apache Sling](https://sling.apache.org/) 遵从内容存储规范（Java Content Repository）即 JSR-170（Java Specification Request），基于 REST 规范/原则，使 Web 开发变得更简单（Bringing Back the Fun!），通过 JAR 包就可以启动。

> 随着apache sling和restful的逐渐成熟，我们写的不只是web page 而是web application。

Apache Sling in five bullets points：

- REST based web framework
- Content-driven, using a JCR content repository
- Powered by OSGi
- Scripting inside, multiple languages (JSP, server-side javascript, Scala, etc.)
- Apache Open Source project

[java - What does it mean that Apache Sling "more REST" than Spring-mvc? - Stack Overflow](http://stackoverflow.com/questions/22694602/what-does-it-mean-that-apache-sling-more-rest-than-spring-mvc)

## References

- [AEM - Administer Best Practices](https://docs.adobe.com/docs/en/aem/6-2/administer/best-practices.html)
- [AEM - Developing](https://docs.adobe.com/docs/en/aem/6-2/develop.html)

## Basic

- 隶属于 [Adobe Marketing Cloud - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Adobe_Marketing_Cloud#Adobe_Experience_Manager)
- [Enterprise content management, ECM | Adobe Experience Manager](http://www.adobe.com/marketing-cloud/enterprise-content-management.html) & [企业内容管理 (ECM) | Adobe Experience Manager](http://www.adobe.com/cn/marketing-cloud/enterprise-content-management.html)
- [AEM 6.0 - 中文概述 docs.adobe.com](https://docs.adobe.com/docs/zh-cn/aem/6-0.html)
- [AEM - Adobe CMS 扒坑记之始](http://owenyang0.github.io/2014/12/13/AEM-Adobe-CMS-%E6%89%92%E5%9D%91%E8%AE%B0%E4%B9%8B%E5%A7%8B/)


## Relationship

- [Continuous integration - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Continuous_integration)
- [Continuous delivery - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Continuous_delivery)
- [From Continuous Integration to Continuous Delivery | ThoughtWorks](https://www.thoughtworks.com/continuous-delivery)