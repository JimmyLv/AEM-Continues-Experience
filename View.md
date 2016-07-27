## Components

Model & View

[Ask the Experts: MVC in Adobe CQ5 | 6D Labs](http://labs.6dglobal.com/blog/2013-05-20/ask-experts-mvc-adobe-cq5/)

实际上就是 MVC：Technically speaking, CQ5 IS MVC, just a form that seems to be unfamiliar to most MVC developers. I think that most people find CQ5's architecture "too coupled" to call it MVC. The biggest complaint I hear is that they would like the data more decoupled from the rendition. Regardless, Sling provides the controller, CRX provides the model, and JSP's/Scripts (ecma, etc) provide the view.

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469608623653.png)

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469608844086.png)

### Template

- [HTL Getting Started](https://docs.adobe.com/docs/en/htl/getting-started.html)
- [Sightly - Quick Reference - AEM Tuts](http://aemtuts.com/aem-sightly-quick-reference/)
- [Adobe-Marketing-Cloud/aem-htl-repl: Read–Eval–Print Loop environment for Sightly.](https://github.com/Adobe-Marketing-Cloud/aem-htl-repl)
- [Adobe-Marketing-Cloud/aem-htl-sample-todomvc: AEM Sightly code example of a simple web application.](https://github.com/Adobe-Marketing-Cloud/aem-htl-sample-todomvc)
- [Sightly intro part 1 - Experience Delivers](http://blogs.adobe.com/experiencedelivers/experience-management/sightly-intro-part-1/)

**data-sly-use**: Initializes a helper object (defined in JavaScript or Java) and exposes it through a variable.

Initialize a JavaScript object, where the source file is located in the same directory as the template. Note that the filename must be used:

    <div data-sly-use.nav="navigation.js">${nav.foo}</div>


Initialize a Java class, where the source file is located in the same directory as the template. Note that the classname must be used, not the file name:

    <div data-sly-use.nav="Navigation">${nav.foo}</div>

Initialize a Java class, where that class is installed as part of an OSGi bundle. Note that its fully-qualified class name must be used:

    <div data-sly-use.nav="org.example.Navigation">${nav.foo}</div>

![](http://7xjbdq.com1.z0.glb.clouddn.com/images/2016/1469608153580.png)

### Others

- [React.js + AEM](http://slides.com/benwestrate/deck-1#/)
- [Developing a VanityPath Manager for Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/vanitypath.html)
- [Integrating the AngularJS Framework into Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/AngularJS.html)
- [Oracle Nashorn: A Next-Generation JavaScript Engine for the JVM](http://www.oracle.com/technetwork/articles/java/jf14-nashorn-2126515.html)


## Tools 

- [AEM Brackets Extension - docs.adobe.com](https://docs.adobe.com/content/docs/en/dev-tools/aem-brackets.html)