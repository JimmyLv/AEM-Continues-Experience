# Adobe AEM Training / [Feisal Ahmad](https://www.linkedin.com/in/feisal-ahmad-b744922)

## 开场

- 安装（介绍三种方式 GUI + CLI）
- 给出架构（三层 + OSGi）
- 从 Marketing 需求讲起（money）
- NoSQL（快速响应）| structure
- location / file tree => Repository => File system (`repository/segmentstore/*.tar`)
    + can not change
    + runtime
    + `**-b**.tar` 存储真实 info
    + `**-a**.tar` just refs
    + 记录了所有的操作？
    + 不要删除 `*.tar` 文件

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471230899930.png)

## 详解架构图每一部分

主要内容，Overview：

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471230964101.png)

> [Developing Reference Materials](https://docs.adobe.com/docs/en/aem/6-2/develop/ref.html)
> [Adobe Experience Manager 6.2](https://docs.adobe.com/docs/en/aem/6-2.html)

1.  [Apache Sling 8 API](https://sling.apache.org/apidocs/sling8/)
2.  [Jackrabbit Oak API](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)
3.  [Java Content Repository API](http://www.day.com/maven/javax.jcr/javadocs/jcr-2.0/)
4.  [Apache Jackrabbit 2.0.0 API](http://jackrabbit.apache.org/api/2.0/)

OSGi 则用于 Java 模块的动态加载，解决运行时问题

## Building Blocks

Granite 处理请求交给 Sling，对应到 `logs/request.log` 可以找到记录

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471230980252.png)

根据 JCR （`jcr:primaryType` & `sling:resourceType`）线索持续不断地查找节点：

<http://localhost:4505/content/todo.html?debug=layout>

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471230424567.png)

## 演示 Create 一个页面

<http://localhost:4505/siteadmin>

- parsys: paragragh system
- iparsys: inherited paragragh system （Pages 继承）

全程 vs Marketing People，Developer 视角的易操控性（胜于 Drag & Drop）与结构性

Layout 模式对应不同的 Responsive 屏幕，可以指定不同设备显示的 Layout

- http://localhost:4505/content/geometrixx-media/en/thoughtworks.html
- http://localhost:4505/content/geometrixx-media/en/thoughtworks.xml
- http://localhost:4505/content/geometrixx-media/en/thoughtworks.json
- http://localhost:4505/content/geometrixx-media/en/thoughtworks.2.json

防止在以上 url 被 Hack，则可以在 http://localhost:4505/system/console/configMgr 关掉一些配置（这个例子也进一步加深了对 Sling 处理请求的理解）；但是！http://localhost:4505/siteadmin 要能打开，又需要 enable XML & JSON，这也是为什么要 Publish 页面到另外的 Instance。

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471232741133.png)

对 Developer 来说最重要的就是 [CRXDE Lite](http://localhost:4505/crx/de/index.jsp)，Chrome 那个插件可以直接从 Editor 直接定位到 CRXDE。

components -> node | templates -> page

> 先 Copy & Paste，然后等 training 结束再自己慢慢看代码

## Mapping Requests to Resources

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471241255878.png)

## Editor Functionality

Annotation & Workflow > Lots of Email

Persona 用户个性定制化页面

## Sightly（HTL）

Sightly 和 JSP ESP 写出来的组件可以混用兼容，但不可以在同一个文件里面同时用上两种语法。

Any component to inherit from a ‘base’ component. `cq:Page` 基于 Page `cq:Component` 

overlay: Copy to another folder and modified something

> 美国人就是喜欢创造新词，没有的那我们就创造一个。

## 样式 Design

要在 Tools 里面添加 Design 的相关文件，然后 Open Properties 添加 Design 的路径

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471262453551.png)

## Component roles

组件角色取决于怎么用它，就像一个人，在不同的地方扮演不同的角色（Student | Developer）

Template 用于初始化 Page 的默认元素。

区分 runtime 和 createtime （author）

> class -> classification: we are instance of human beings

都是 Node，只是 CRXDE 提供了 Template 和 Component 的快速选项，填好必要参数即可

## 导航栏（演示 smart Component + Script）

[Use-API](https://docs.adobe.com/docs/en/htl/docs/use-api.html) （JavaScript & Java）& [HTL](https://docs.adobe.com/docs/en/htl/overview.html)

`currentPage.listChildren` 显示出所有子页面（进而我回过头添加了所有的子页面，页面继承简直太酷）

## Logging

> AEM is Marketing Products...

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471318096024.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471318138767.png)

    16.08.2016 11:31:06.349 *INFO* [0:0:0:0:0:0:0:1 [1471318266330] GET /content/we-train/English.html HTTP/1.1] apps.training.components.structure.site-topnav.site-topnav$html ########[JS] Root page is: English
    16.08.2016 11:59:56.413 *INFO* [0:0:0:0:0:0:0:1 [1471319996401] GET /content/we-train/English/products.html HTTP/1.1] apps.training.components.structure.site-topnav.site-topnav$html ########[JS] Root page is: English

## Dialog

Classic UI 用的是 ExtJS

要秀出 Touch UI （cq:dialog） 必须先建一个 Classic UI 的 Dialog

`<div class="we-Header" data-sly-resource="${'title' @ resourceType='training/components/structure/title'}"></div>`

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471320681966.png)

> I can only remember diagram, my job is to make it easy to understand.

直接编辑文字：

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471325139658.png)

Design Dialog

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471326434890.png)

## Hero Component

> 教爸妈学上网 => Marketing Peope also 不用考虑 HTML

[AEM Assets](http://localhost:4505/assetdetails.html/content/dam/jimmy-folder/wave-huge.jpg)

## Breadcrumb & ToolBar 

直接借用 `<div class="aem-breadcrumb" data-sly-resource="${'breadcrumb' @ resourceType='/libs/foundation/components/breadcrumb'}"></div>`

对于 ToolBar 来说还可以设置 selector，然后设置属性决定每个 toolBar Item 的显示与否。

`cq:toolbars | String | top(or btm)`

## Responsive

`<div data-sly-resource="${'responsivegrid' @resourceType='wcm/foundation/components/responsivegrid'}"></div>`

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471334136463.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471334190952.png)

Designer 决定可以给 Author 用哪些 Components

Layout 模式对响应式设计的支持无比酷炫至极：

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471335123051.png)

## Internationalization (Globalization/Localization)

没生效，/(ㄒoㄒ)/~~  还有 [AEM Translator](http://localhost:4505/libs/cq/i18n/translator.html) 没找到自己配置的。

## Overlays and Sling Resource Merger?

就是说可以改/覆盖任何 AEM 里面的东西？

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471337754492.png)

修改 Sling servlet，自定义 404 页面，please notice `404.html` page should not have any syntax error.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471337901067.png)

## Sling Redirect

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1471339579945.png)

error: (注意 `"type":"foundation/components/redirect\n"`)

```
<!--cq{"decorated":false,"type":"foundation/components/redirect\n","path":"/content/we-train/jcr:content","selectors":null,"servlet":"DefaultGetServlet","totalTime":1,"selfTime":1}-->
```
