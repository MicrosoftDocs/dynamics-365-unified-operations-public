---
# required metadata

title: Writing extensible code
description: This article how to write extensible code.
author: mfp
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Writing extensible code

[!include [banner](../includes/banner.md)]

X++ and the metadata model provide a powerful foundation for building business solutions. One of the design pillars is to enable the engineer to focus on the business domain by automating as many technical concerns as possible. 

Localization of text resources is a technical concern that you hardly have to worry about - as long as you remember to place all text resources in label files.   

Similarly; Extensibility is another technical concern.  You want others to be able to extend your solution in a safe, robust and maintainable way. By default your solution is highly extensible; but there are a few guidelines to follow to ensure completeness.  These are all described in this section.

## Responsibilities
Any Dynamics 365 For Finance and Operation is running a business solution with components from many sources. Typically each solution has code coming from Microsoft, ISV(s), Partner(s) and internally developed code. A chain is not stronger than the weakest link; that is also true here. Each contributor is responsible for their contribution to the solution and how it interacts with other contributions.

When writing extensible code; you invite others to interact with your solution. Your responsibility is to enable others to be good guests. You do this by:

**Making robust extension points**

Extension points must be well-defined, and robust release after release. They are the foundation of the extenders' solution.
+ **Inviting for side-by-side customizations**
Recognize that multiple extenders might use the same extension point. Enable 1:n interactions instead of 1:1.
+ **Trusting that extenders will be well behaved**
All responsible parties share the same goal: Creating great lasting solutions for the customer. When creating extension points you are giving up control and sharing the responsibility with others. Assume extenders will be precautious and use your extension points as intended.

## Proven principles
All the good engineering practices you are already using still applies. Everything you learned still applies. You don't have to learn new principles or unlearn old practices.   We are calling out 3 principles of software craftmanship that have been sought and taught for decades.  Not only do they make your code easier to read, maintain, test, review and refactor - they also make your code easier to extend. Keep applying and advocating these practices.

### S.O.L.I.D.
This is an acronym for 5 principles that each will make your code easier to extend.
+ **Single responsibility**
	Classes and method should have a single responsibility without side-effects. This will make the automatically created extension points on public/protected methods great extension points.
+ **Open/closed**
    - Open your solution for extensions by designing and consider the extension surface. Once an extension point is made available you are responsible for maintaining it.  This adds significant restrictions to future development. Often it is preferable to open up for extension by demand. I.e. Prefer internal over public; prefer private over protected.  
    - **Closed for modification
    Make your properties private, and your methods either private or final protected. This means that nobody through inheritance or extension can take a dependency on your logic.
+ **Liskov substitution**
Derived classes must be substitutable for their base classes, for example by providing factories, using SysExtension and simple construct methods.
+ **Interface segregation**
Create concise interfaces. This principle enables extenders to provide replacement implementations, and is particular valuable when used with dependency inversion.
+ **Dependency inversion**
Depend on abstractions, not on concretions. This principle enables decoupling, and allows extenders to provide concrete instances conforming to the abstraction your logic depends on.
  
### Clean code
Clean code reads like an article. The name of a method provides the heading of the article. Then follows the body of the method - which is really just few lines of summary. The summary is calling few other methods with good descriptive names.  This way the reader can keep exploring more and more details, and stop at any time - without missing any conceptual understanding.

When code is written like this, methods will be short (often less than 5-10 code lines). The number of parameters will be low (often less than 2), conditions and blocks of code are always single line (calling a method). 

For example:
```
public void processOrder(SalesOrder _salesOrder)
    {
        if (this.approveOrder(_salesOrder))
        {
            this.confirmOrder(_salesOrder);
        }
        else
        {
            this.rejectOrder(_salesOrder);
        }
    }
```

In X++ every (protected and public) method is an extension point - writing clean code, will automatically produce extensible code.  In the example above, an extender can change how approval, confirmation and rejection is implemented.  If those implementations had been inline, the code would not be extensible.


### D.R.Y.
**Don't Repeat Yourself.** Avoid redundancy in your logic to prevent misalignment of implementations. With extensible code this is even more important, as the extender may not extend all required pieces, leaving the solution broken unintentionally.


## Best practices for writing extensible code in X++

We have compiled some of the best practices that can help you write extensible code in X++.

+ [Classes](ExtensibleClasses.md)
+ [Methods](ExtensibleMethods.md)
+ [Forms](ExtensibleForms.md)
+ [Extended data types](ExtensibleEDTs.md)
+ [Extensible enums](ExtensibleEnums.md)
+ [Delegates](ExtensibleCodeDelegates.md)
+ [Tables](ExtensibleTables.md)
+ [Extensibility attributes for methods](ExtensibilityAttributes.md)


## Breaking changes
When making your solution extensible, you also guarantee to not break those extension point going forward. Here are a few pointers on how to not break your consumers.

+ [Breaking Changes](BreakingChanges.md)


External resources:
+ [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
+ [Pluralsight - Clean Code: Writing Code for Humans](https://www.pluralsight.com/courses/writing-clean-code-humans)
+ [Clean Code: A Handbook of Agile Software Craftsmanship](https:://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
+ [Clean Coders](https://cleancoders.com/)
+ [Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
