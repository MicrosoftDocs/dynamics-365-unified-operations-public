---
title: Write extensible code
description: Learn about how to write extensible code, including overviews on responsibilities, proven principles, and breaking changes.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 09/18/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible code

[!include [banner](../includes/banner.md)]

X++ and the metadata model provide a powerful foundation for building business solutions. One of the design pillars is to automate as many technical concerns as possible, so that the engineer can focus on the business domain. For example, if you put all the text resources in label files, one technical concern that you don't have to worry about is the localization of text resources.

Extensibility is another technical concern. You want other people to be able to extend your solution in a safe, robust, and maintainable way. By default, your solution is highly extensible. However, there are a few guidelines that you should follow to help guarantee completeness.

## Responsibilities
Any finance and operations environment runs a business solution that includes components from many sources. Typically, each solution has code from Microsoft, independent software vendors (ISVs) and partners, and also internally developed code. Each contributor is responsible for its own contribution to the solution and for the way that its contribution interacts with other contributions.

When you write extensible code, you invite other people to interact with your solution. Your responsibility is to enable other people to be good guests. Here is how you meet this responsibility:

+ **Make robust extension points** – Extension points are the foundation of extenders' solutions. They must be well-defined and robust from release to release.
+ **Invite side-by-side customizations** – Recognize that multiple extenders might use the same extension point. Enable 1:n (one-to-many) interactions instead of 1:1 (one-to-one) interactions.
+ **Trust that extenders will be well-behaved** – All responsible parties share the same goal: to create great, lasting solutions for the customer. When you create extension points, you give up control and share the responsibility with other people. Assume that extenders will be cautious and use your extension points as they were intended.

## Proven principles
All the good engineering practices that you're already using still apply. Everything that you've learned still applies. You don't have to learn new principles or unlearn old practices. This article is just highlighting three principles of software craftmanship that have been sought and taught for decades. These principles not only make your code easier to read, maintain, test, review, and refactor, but also make your code easier to extend. Apply and advocate these principles.

### Extend code by using the SOLID principles
SOLID is an acronym for five principles that you can use to make your code easier to extend:

+ **Single responsibility** – Classes and method should have a single responsibility and should not have side-effects. By following this principle, you help guarantee that extension points that are automatically created on public and protected methods will be great extension points.
+ **Open/closed**

    - **Open for extension** – Open your solution for extensions by designing and considering the extension surface. After an extension point is made available, you're responsible for maintaining it. This responsibility adds significant restrictions to future development. It's often preferable to open a solution up for extension by demand. For example, use internal methods over public methods or private methods over protected methods. Limit your extension surface by making your properties private, and your methods either private or final-protected. In this way, no one can take advantage of a dependency on your logic, either through inheritance or extension.
    - **Closed for modification** – Make your logic support extensions without requiring further modifications.


+ **Liskov substitution** – Derived classes must be able to be substituted for their base classes. For example, this substitution can be done by providing factories, by using SysExtension, and by using simple construct methods.
+ **Interface segregation** – Create concise interfaces. This principle lets extenders provide replacement implementations and is particularly valuable when it's used together with the next SOLID principle, dependency inversion.
+ **Dependency inversion** – Depend on abstractions, not concretions. This principle enables decoupling and lets extenders provide concrete instances that conform to the abstraction that your logic depends on.

### Write clean code
Clean code can be read like an article. The name of a method provides the heading of the article. The body of the method comes next and really consists of just a few lines of summary. This summary calls a few other methods that have good descriptive names. In this way, the reader can keep exploring details and can also stop at any time without missing any conceptual information.

When code is written like in this manner, methods are short, often less than 5 to 10 code lines. Additionally, the number of parameters is low, often less than two, and the conditions and blocks of code are always a single code line.

Here is an example.

```xpp
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

In X++, every protected and public method is an extension point. By writing clean code, you automatically produce extensible code. In the previous example, an extender can change how approval, confirmation, and rejection are implemented. If the implementations had been inline, the code would not be extensible.

### Don't repeat yourself (DRY)
To help prevent misalignment of implementations, avoid redundancy in your logic. This principle is especially important in the case of extensible code, because the extender might not extend all required pieces and might therefore unintentionally leave the solution broken.

## Best practices to create an extensible solution in X++
The following best practices can help you create extensible solutions in X++, so that consumers of your code can extend your solution:

+ [Classes](extensible-classes.md)
+ [Methods](extensible-methods.md)
+ [Forms](extensible-forms.md)
+ [Extended data types](extensible-edts.md)
+ [Extensible enums](extensible-enums.md)
+ [Delegates](extensible-code-delegates.md)
+ [Tables](extensible-tables.md)
+ [Attributes that make methods extensible](extensibility-attributes.md)

## Breaking changes
When you make your solution extensible, you also help guarantee that you won't break extension points later. For more information, see [Breaking changes](breaking-changes.md).

## External resources
The following external resources can help you make sure that you're writing clean code:

+ [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
+ [Clean Code: A Handbook of Agile Software Craftsmanship](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
+ [Clean Coders](https://cleancoders.com/)
+ [Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
