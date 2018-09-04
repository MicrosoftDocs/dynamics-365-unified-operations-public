---
# required metadata

title: Write extensible code
description: This article provides information about writing extensible code.
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

X++ and the metadata model provide a powerful foundation for building business solutions. One of the design pillars is to enable the engineer to focus on the business domain by automating as many technical concerns as possible. For example, localizing text resources is a technical concern that you don't have to worry about if you place all of the text resources in label files. Similarly, extensibility is another technical concern. You want others to be able to extend your solution in a safe, robust, and maintainable way. By default, your solution is highly extensible, however there are a few guidelines to follow to ensure completeness.  

## Responsibilities
Any Finance and Operations environment is running a business solution with components from many sources. Typically, each solution has code coming from Microsoft, ISVs, Partners, and internally developed code. Each contributor is responsible for their contribution to the solution and how it interacts with other contributions.

When writing extensible code; you invite others to interact with your solution. Your responsibility is to enable others to be good guests. You do this by:

**Make robust extension points**
Extension points must be well-defined and robust release after release. They are the foundation of the extenders' solution.

+ **Invite side-by-side customizations** - Recognize that multiple extenders might use the same extension point. Enable 1:n interactions instead of 1:1.
+ **Trust that extenders will be well behaved** - All responsible parties share the same goal to create great lasting solutions for the customer. When you create extension points, you are giving up control and sharing the responsibility with others. Assume extenders will be cautious and use your extension points as intended.

## Proven principles
All of the good engineering practices you are already using still apply. Everything you learned still applies. You don't have to learn new principles or unlearn old practices. We are simply calling out three principles of software craftmanship that have been sought and taught for decades. Not only do these prinicples make your code easier to read, maintain, test, review, and refactor, they also make your code easier to extend. Apply and advocate these practices.

### Extending code with the SOLID principles
SOLID is an acronym for five principles that you can use to make your code easier to extend.

+ **Single responsibility** - Classes and method should have a single responsibility without side-effects. This will make the automatically created extension points on public and protected methods great extension points.
+ **Open/closed** 
	- **Open for modification** - Open your solution for extensions by designing and considering the extension surface. After an extension point is made available, you are responsible for maintaining it which adds significant restrictions to future development. It is often preferable to open up for extension by demand. For example, internal over public or private over protected.  
	- **Closed for modification** - Make your properties private and your methods either private or final-protected. This means that nobody can take a dependency on your logic whether it's through inheritance or extension.

+ **Liskov substitution** - Derived classes must be substitutable for their base classes. For example, by providing factories, using SysExtension, and simple construct methods.
+ **Interface segregation** - Create concise interfaces. This principle enables extenders to provide replacement implementations, and is particularly valuable when used with dependency inversion.
+ **Dependency inversion** - Depend on abstractions, not on concretions. This principle enables decoupling, and allows extenders to provide concrete instances which conform to the abstraction your logic depends on.
  
### Clean code
Clean code can be read like an article. The name of a method provides the heading of the article, and then comes the body of the method, which is really just few lines of summary. The summary calls a few other methods with good descriptive names. This allows the reader to keep exploring details, and stop at any time without missing any conceptual information.

When code is written like this, methods will be short, often less than 5-10 code lines. The number of parameters will be low, often less than 2 and the conditions and blocks of code are always single line. 

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

In X++ every protected and public method is an extension point. Writing clean code will automatically produce extensible code. In the previous example, an extender can change how approval, confirmation, and rejection is implemented. If the implementations had been inline, the code would not be extensible.

### Don't repeat yourself, or D.R.Y.
Avoid redundancy in your logic to prevent misalignment of implementations. With extensible code this is even more important, as the extender may not extend all required pieces, leaving the solution broken unintentionally.


## Best practices to create an extensible solution in X++
The following list of best practices can help you create extensible solutions in X++ that will enable consumers of your code extend your solution.

+ [Classes](extensible-classes.md)
+ [Methods](extensible-methods.md)
+ [Forms](extensible-forms.md)
+ [Extended data types](extensible-edts.md)
+ [Extensible enums](extensible-enums.md)
+ [Delegates](extensible-code-delegates.md)
+ [Tables](extensible-tables.md)
+ [Extensibility attributes for methods](extensibility-attributes.md)


## Breaking changes
When you make your solution extensible, you also guarantee to not break extension points going forward. For more information, see [Breaking changes](breaking-changes.md).


## External resources
The following list of external resources can help you ensure that you are writing clean code.
+ [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
+ [Pluralsight - Clean Code: Writing Code for Humans](https://www.pluralsight.com/courses/writing-clean-code-humans)
+ [Clean Code: A Handbook of Agile Software Craftsmanship](https:://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
+ [Clean Coders](https://cleancoders.com/)
+ [Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)
