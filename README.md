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

## Overview

- [Adobe Experience Manager - YouTube](https://www.youtube.com/watch?v=T6N47XV_8s0)
- [Evolve13 cq-commerce-framework](http://www.slideshare.net/paolomoz/evolve13-cqcommerceframework?qid=6a6551d7-6c5b-4ac9-a9f7-9c80e2e4fc90&v=&b=&from_search=19)

## References

- [AEM - Administer Best Practices](https://docs.adobe.com/docs/en/aem/6-2/administer/best-practices.html)
- [AEM - Developing](https://docs.adobe.com/docs/en/aem/6-2/develop.html)
- [Aem best practices](http://www.slideshare.net/JituTomar/aem-best-practices?qid=6a6551d7-6c5b-4ac9-a9f7-9c80e2e4fc90&v=&b=&from_search=48)


## Basic

- [Adobe Experience Manager 6.2 - Developing / The Basics](https://docs.adobe.com/docs/en/aem/6-2/develop/the-basics.html)
- [Top 10 Hottest Features in Adobe Experience Manager (AEM) Sites 6.2 | Adobe](https://blogs.adobe.com/digitalmarketing/web-experience/top-10-hottest-features-adobe-experience-manager-aem-sites-6-2-2/)
- [Adobe Experience Manager 6.1 - docs.adobe.com](https://docs.adobe.com/content/docs/zh-cn/aem/6-1.html) 6.1 版本有部分中文材料（just 参考，but 不推荐）
- 隶属于 [Adobe Marketing Cloud - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Adobe_Marketing_Cloud#Adobe_Experience_Manager)
- [Enterprise content management, ECM | Adobe Experience Manager](http://www.adobe.com/marketing-cloud/enterprise-content-management.html) & [企业内容管理 (ECM) | Adobe Experience Manager](http://www.adobe.com/cn/marketing-cloud/enterprise-content-management.html)
- [AEM 6.0 - 中文概述 docs.adobe.com](https://docs.adobe.com/docs/zh-cn/aem/6-0.html)
- [AEM - Adobe CMS 扒坑记之始](http://owenyang0.github.io/2014/12/13/AEM-Adobe-CMS-%E6%89%92%E5%9D%91%E8%AE%B0%E4%B9%8B%E5%A7%8B/)
- [Adobe CQ5介绍 - 博文_晓峰_新浪博客](http://blog.sina.com.cn/s/articlelist_2660661593_0_1.html)

## Tutorials

- [AEM CQ5 Tutorials | AEM Tutorials and Interview Questions](http://www.aemcq5tutorials.com/)
- [CQ5 AEM Tricks of Trade – One Stop Guide to AEM !!!](https://hashimkhan.in/)
- [AEM Tuts - Adobe Experience Manager Tutorials](http://aemtuts.com/)
- [Home | 6D Labs](http://labs.6dglobal.com/)
- [adobe aem - YouTube](https://www.youtube.com/results?q=adobe+aem&sp=CAM%253D)
- [Learning Series - Adobe Experience Manager (formerly Adobe CQ) - YouTube](https://www.youtube.com/playlist?list=PLKsCe3_0gbqoN6L_Ihoov2XTOIhdl8R-t)

## Others

- [电子商务系统与全渠道电商解决方案 | hybris SAP](https://www.hybris.com/zh/)
- [Adobe Experience Manager | Adobe Digital Marketing Blog](https://blogs.adobe.com/digitalmarketing/tag/adobe-experience-manager/)


## Relationship

- [Continuous integration - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Continuous_integration)
- [Continuous delivery - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Continuous_delivery)
- [From Continuous Integration to Continuous Delivery | ThoughtWorks](https://www.thoughtworks.com/continuous-delivery)