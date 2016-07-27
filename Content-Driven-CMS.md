## What is Adobe Experience Manager?

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469613935722.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469426041703.png)

Adobe Experience Manager (AEM) is an enterprise-grade web content management system with a wide array of powerful features. With AEM people in your organization can: Author and publish websites.

It’s a comprehensive content management solution for building websites, mobile apps, and forms. And it makes it easy to manage your marketing content and assets.

Search for: [What is Adobe Experience Manager?](https://www.google.com/search?newwindow=1&q=What+is+Adobe+Experience+Manager%3F&sa=X&ved=0ahUKEwicuLvl9Y3OAhUFKpQKHfqDBOYQzmcIYQ)

### 前身：[CQ5 - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/CQ5)

CQ5 or Communique5 (renamed as **Adobe Experience Manager**) is a Web Content Management System (WCMS) designed to enable users (mainly marketers and IT professionals) to create, edit, manage and optimize websites across different digital channels such as web, mobile, social and more.

## AEM Overview

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469613962134.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469613309028.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469614691277.png)

### JCR （[JSR-170](https://jcp.org/en/jsr/detail?id=170) & [JSR-283](https://jcp.org/en/jsr/detail?id=283) Specification）

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469623943917.png)


实际文档，现已更新至 [v2.0](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/)：[javax.jcr (Content Repository for Java Technology API Version 2.0)](https://docs.adobe.com/docs/en/spec/jsr170/javadocs/jcr-2.0/index.html?overview-summary.html)

> David Nuescheler Day Software的CTO，也是Java Content Repository（Java內容錄倉庫）JCR 170專家組負責人。Java Content Repository是一個定址內容倉庫的標準化API建議。2002年2月，該建議提交到JCR(Java Community Process)，JCR專家組於2003年下半年完成最終草案。  —— [Java界技術名人堂|精彩博文 - 博搜網](http://cocboso.com/subject/about/28941.html)


- [David Nuescheler on JCR and REST](https://www.infoq.com/articles/nuescheler-jcr-rest)
- [译：David Nuescheler谈JCR和REST](http://www.infoq.com/cn/articles/nuescheler-jcr-rest)
- [Content repository API for Java - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Content_repository_API_for_Java)

### [Jackrabbit Oak - the next generation content repository](https://jackrabbit.apache.org/oak/)

Jackrabbit Oak is a scalable, high-performance hierarchical content
repository designed for use as the foundation of modern world-class
web sites and other demanding content applications.

The Oak effort is a part of the [Apache Jackrabbit](http://jackrabbit.apache.org/jcr/index.html) project.
Apache Jackrabbit is a project of the Apache Software Foundation.

The Apache Jackrabbit™ content repository is a fully conforming implementation of the Content Repository for Java Technology API (JCR, specified in JSR 170 and JSR 283).

A content repository is a hierarchical content store with support for structured and unstructured content, full text search, versioning, transactions, observation, and more.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469622369891.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469624617168.png)

[Jackrabbit Oak - Understanding the node state model](https://jackrabbit.apache.org/oak/docs/architecture/nodestate.html)

### CRX （**C**ontent **R**epository e**X**treme）

[CRX Concepts - docs.adobe.com](https://docs.adobe.com/docs/en/crx/2-0/getting_started/crx_concepts.html)

[CRX and JCR - docs.adobe.com](https://docs.adobe.com/docs/en/crx/2-3/getting_started/jcr_content_repository.html)

JCR Repository Model

Inside a JCR repository, content is organized into one or more _workspaces_, each of which holds of a hierarchical structure of _nodes_ and _properties_.

Beginning with the root node at the top, the hierarchy descends much like the directory structure of a file system: each node can have zero or more child nodes and zero or more properties. Properties cannot have children but do have _values___. 

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469626168800.png)

Assuming you have administrator access, simply go to the CRX Launchpad page and click the link **CRXDE Lite** (http://localhost:7402/crx/de/ in a default installation). This opens the web-based development environment for CRX.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469626279777.png)


via EXAMPLE NODE TYPES IN CRX: **Node Type Administration** will take you to a console that shows all the regsitered node types in your CRX instance. Scroll down until you see nt:file in the left pane and click on it. This will reveal the defintion of that node type:

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469626406567.png)

### WCM

收购！[Adobe acquires Day Software](http://www.adobe.com/investor-relations/day-acquisition.html), a market leader in next-generation web content management (WCM), was an enterprise content management software company.

With the acquisition of Day, Adobe is positioned to help organizations transform themselves by enabling them to create, manage, distribute, and monetize content while optimizing the web, mobile, and social collaboration experience for their customers.

[Day Software - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Day_Software) 

Roy T. Fielding 是首席科学家（chief scientist），所以才有了 [REST in AEM](http://www.slideshare.net/royfielding/rest-in-aem)，现在是 [Senior Principal Scientist  at Adobe Systems](https://www.linkedin.com/in/royfielding)，在 Adobe 继续担任首席科学家。

Day is engaged in the content repository API for Java standardization process and contributes to open source software projects such as Apache Jackrabbit and Apache Sling.

知道真相的我眼泪掉下来：Product history of Adobe CQ

Date | Product      
---- | ----------
2002 | Day CQ 3.5                           
2005 | Day CQ 4.0                         
2006 | Day CQ 4.1                       
2008 | Day CQ 4.2                        
2008 | Day CQ 5.0                        
2009 | Day CQ 5.2                        
2010 | Day CQ 5.3                        
2011 | Adobe CQ 5.4                      
2012 | Adobe CQ 5.5                      
2013 | [Adobe Experience Manager](https://en.wikipedia.org/wiki/Adobe_Marketing_Cloud "Adobe Marketing Cloud") (AEM) 5.6
2014 | [Adobe Experience Manager](https://en.wikipedia.org/wiki/Adobe_Marketing_Cloud "Adobe Marketing Cloud") (AEM) 6.0
2015 | [Adobe Experience Manager](https://en.wikipedia.org/wiki/Adobe_Marketing_Cloud "Adobe Marketing Cloud") (AEM) 6.1
2016 | [Adobe Experience Manager](https://en.wikipedia.org/wiki/Adobe_Marketing_Cloud "Adobe Marketing Cloud") (AEM) 6.2

## 结语

有了 JCR 仓库，则需要通过某种方式暴露出去，即 Sling，符合 REST 规范。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469624381359.png)

通过 URI 交由 Sling 进行处理，content + apps 得出最后的渲染内容。