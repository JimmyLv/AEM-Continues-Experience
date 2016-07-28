### Sling & REST 

via [Apache Sling : JCR, OSGi, Scripting and REST](http://www.slideshare.net/cziegeler/apache-sling-jcr-osgi-scripting-and-rest) 👍

& [Effective Web Application Development with Apache Sling](http://www.slideshare.net/rombertw/effective-web-application-development-with-apache-sling)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469706116898.png)

面向对象，Stateless 就是指每次 Request 携带所有相关信息，绝不在服务器端存储。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469708076868.png)

URI 直接对应到 JCR 的每个 Node，即 REST 中的 Resource，每个 Resource 有直接的 Properties 及其 Value：

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469708176725.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469708103920.png)

Scripting 用于处理请求并解析出 Resource，然后交由 Script 进行处理，最终生成 rendered 的页面。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469708731542.png)

### From URL to Content and Scripts

principles: 

- the mapping uses the content path extracted from the request to locate the resource
- when the appropriate resource is located, the sling resource type is extracted, and used to locate the script to be used for rendering the content

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469714659629.png)


终于联系起来了：With Sling, you specify which script renders a certain entity (by setting the sling:resourceType **property** in the JCR node). This mechanism offers more freedom than one in which the script accesses the data entities (as an SQL statement in a PHP script would do) as a resource can have several renditions.

对应到一个 JCR 节点之后，其中含有 Sling 相关的 properties，从而找到 resourceType 进而指定特别的 Script 去做渲染工作。

All Sling scripts are stored in subfolders of either /apps or /libs, which will be searched by order, & in this order (see [Customizing Components and Other Elements](https://docs.adobe.com/docs/en/aem/6-2/develop/the-basics/dev-guidelines-bestpractices.html#Customizing%20Components%20and%20Other%20Elements)).

- Mapping requests to resources：具体找法就是根据 URI 定位到对应的 content node，若没有找到则抛弃 .html 继续找，再没找到就 404
- Locating the script：找到 content node 获取到 sling:resourceType 属性之后就load 相应的 Script：

1.  when the Method (GET, POST) is required, it will be specified in uppercase as according to the HTTP specification e.g. jobs.POST.esp (see below)
2.  various script engines are supported:
    * .esp, .ecma: ECMAScript (JavaScript) Pages (server-side execution)
    * .jsp: Java Server Pages (server-side execution)
    * .java: Java Servlet Compiler (server-side execution)
    * .jst: JavaScript templates (client-side execution)

结合这张图一起看：

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469715454959.png)


### 基于 OSGi

而 OSGi 的作用在于 Runtime，之所以为动态模块加载，用于管理复杂度，并可以动态扩展其依赖。（类 JavaScript 的 Require.js ？）

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469708850072.png)

最佳实现，[Apache Felix - SCR Annotations](http://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html)

这哥们用注解的方式实现 OSGi 标准 bundle。

* [@Component](http://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html#component)
* [@Activate, @Deactivate, and @Modified](http://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html#activate-deactivate-and-modified)
* [@Service](http://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html#service)
* [@Property](http://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html#property)
* [@Reference](http://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html#reference)

```java
@Property(name = "sample",
    options = {
        @PropertyOption(name = "option1", value = "&option.label.1"),
        @PropertyOption(name = "option2", value = "&option.label.2")
    }
)
```

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469709667022.png)

参考项目：[nateyolles/publick-sling-blog: Blog engine using Apache Sling and Sightly](https://github.com/nateyolles/publick-sling-blog)

This architecture allows you to extend Sling with application specific modules.

This enables you to perform the following actions on any of the packages within your installation:

1.  install
2.  start
3.  stop
4.  update
5.  uninstall
6.  see the current status
7.  access more detailed information (e.g. symbolic name, version, location, etc) about the specific bundles

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469717012887.png)

### 总结就是 Sling 背后靠着 CRX 吃饭： 

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710299369.png)

对比传统 Controller，直接对应 JCR 节点（文件结构？），包含相关信息。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710389235.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710400998.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710435546.png)


不是直接对应文件目录，但是也完全可以这样。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710511007.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710571268.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469710594399.png)


**WHAT IS CRX?**

CRX is short for **C**ontent **R**epository e**X**treme, Day's JCR-compliant repository. CRX allows you to store, manage, and access data using a standardized Java interface.

~~好像不关 Jackrabbit 什么事儿了？~~ CRX 基于 Jackrabbit

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469709908396.png)

CRX is drop-in and source-code compatible with Apache Jackrabbit. If you have an existing Jackrabbit repository, you can migrate it to CRX with minimal effort.  via [Jackrabbit Compatibility - docs.adobe.com](https://docs.adobe.com/docs/en/cq/5-6-1/core/developing/jackrabbit_compatibility.html)

> via [How/When is CRX and Apache Jackrabbit used in CQ5/AEM? - Stack Overflow](http://stackoverflow.com/questions/17535911/how-when-is-crx-and-apache-jackrabbit-used-in-cq5-aem): 
> 
> Adobe **CRX** is the commercial content repository component used in the AEM, which uses some elements of Jackrabbit (e.g. some of the [security APIs](http://jackrabbit.apache.org/api/2.4/org/apache/jackrabbit/api/security/user/package-summary.html)).  CRX provides additional features such as [development tools](http://dev.day.com/docs/en/crx/current/developing/development_tools/developing_with_crxde.html) & [clustering capabilities](http://dev.day.com/docs/en/crx/current/administering/cluster.html) and has its own [storage mechanism](http://dev.day.com/content/ddc/blog/2008/11/tarpm.html) which differs from the Jackrabbit implementation. 


### 做一个照片 CMS 

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469707534634.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469707517793.png)

