---
title: Solve dependencies among models by using delegates during code migration
description: Learn about how delegate methods serve as a means for defining a contract between the delegate instance and the delegate handler.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6640ae38-58f0-4a29-abca-5acd9489d45d
---

# Solve dependencies among models by using delegates during code migration

[!include [banner](../includes/banner.md)]

This article explains how delegate methods define a contract between the delegate instance and the delegate handler.

## Overview

Finance and operations is split into several models, with each model in a separate package. The three main models are Application Platform, Application Foundation, and Application Suite. This model split creates a hierarchy where a higher model can take dependencies on and access elements in the models below, but not in models above. For example, Application Suite has full access to its elements, Application Foundation’s elements, and Application Platform’s elements. Application Foundation can access its own elements and those of Application Platform. Finally, Application Platform can only access its own elements. To learn about models and packages, see [Models and packages](../dev-tools/models.md).

:::image type="content" source="./media/del1.jpg" alt-text="Screenshot of models and packages hierarchy diagram.":::

While the model split provides many benefits, it creates a problem when you try to access elements defined in higher models. Delegates are the recommended method for accessing elements in higher models from a lower model. Delegates are similar to events in that when you invoke a delegate instance, it executes a handler with compatible signature code. This approach permits lower layer code, the delegate instance, to call higher layer code, the handler.

## Create delegates and handlers

A delegate declaration must have three things:

- The delegate keyword
- Type `void`
- Empty method

Delegate methods serve as a means for defining a contract between the delegate instance and the delegate handler. A delegate takes no action itself. This contract is enforced by using a `void` type and having no code in the method.

```xpp
delegate void applyDiscountDelegate(real _receiptTotal, EventHandlerResult _result)
{
}
```

Adding the **SubscribesTo** keyword to a method creates a static delegate handler. **SubscribesTo** requires the class name of the delegate, and the string name of the delegate method.

For a delegate to be properly handled, the delegate method declaration, the delegate instance, and the delegate handler must have the *same* method signature. For example, the delegate instance in the following code takes two inputs, a real number and an `EventHandlerResult`, matching the delegate declaration and handler signatures.

:::image type="content" source="media/static-delegate-handler.png" alt-text="Screenshot of static delegate handler code.":::

Because delegates don't have a return value, an `EventHandlerResult` is passed as a parameter to provide access to the needed result value after the delegate returns. This article focuses on static delegate handlers that use the **SubscribesTo** keyword. The delegate functionality from Dynamics AX 2012 remains. [How to use X++ Delegates in Dynamics AX 2012](https://blogs.msdn.com/b/x/archive/2011/08/02/how-to-use-x-delegates-in-dynamics-ax-2012.aspx) is a great blog post on MSDN by Microsoft developer Marcos Calderon that explains delegate concepts in Dynamics AX 2012. These concepts still apply.

## Example scenarios

### Overlaying an existing delegate

In many cases where you need delegates, Microsoft already moved the code that you formerly overlaid to a delegate handler. In these instances, you can leverage the delegates that Microsoft created and overlay the code in the delegate handler. In this scenario, an independent software vendor (ISV) is migrating code from Dynamics  AX 2012 R3 where they overlaid the `showSalesTax()` method in the `LogisticsEntityPostalAddressFormHandler` class. After migration, the CodeUpgrade project contains the `LogisticsEntityPostalAddressFormHandler` with the *Your Solution*, *Microsoft AX 2012,* and *Microsoft AX* sections to resolve for the `showSalesTax()` method. The commented Your Solution section shows that the `showSalesTax()` method was overlaid by adding an additional table to approve showing sales tax from. This overlay is shown between the &lt;isv&gt; tags circled in red in the following image.

:::image type="content" source="./media/41.png" alt-text="Screenshot of the overlay shown in the CodeUpgrade project." lightbox="./media/41.png":::

When you compare this overlay with the code from Dynamics AX 2012, you see that this is a simple change. The overlay adds an extra table to the switch statement.

:::image type="content" source="./media/51.png" alt-text="Screenshot of the overlay showing an additional table added to the switch statement." lightbox="./media/51.png":::

However, the section for finance and operations doesn't appear to resemble either of the Dynamics AX 2012 code snippets.

:::image type="content" source="./media/61.png" alt-text="Screenshot of the finance and operations code section that doesn't resemble the Dynamics AX 2012 code snippets." lightbox="./media/61.png":::

Upon deeper inspection, the code calls a delegate method, `showSalesTax_delegate()`.

:::image type="content" source="./media/showsalestax_delegate.png" alt-text="Screenshot of code calling the showSalesTax delegate method." lightbox="./media/showsalestax_delegate.png":::

The use of a delegate implies that the code is moved to another location. The `showSalesTax_delegate()` is declared in the Application Foundation and handled in the Application Suite. To view the code that was moved, find the delegate handler. The **Finding Delegates and Handlers** section contains methods to locate delegates and handlers. After you find the delegate handler method in the Application Suite, you see the code that was moved from the `showSalesTax()` method. You can apply the same overlayered changes in the delegate handler that you applied in Dynamics AX 2012.

:::image type="content" source="./media/findingdelegatesandhandles.png" alt-text="Screenshot of finding delegates and handlers code sample." lightbox="./media/findingdelegatesandhandles.png":::

After you add the new table to the switch statement in the delegate handler, the code functions as it did in Dynamics AX 2012.

:::image type="content" source="./media/showsalestaxmethod.png" alt-text="Screenshot of the ShowSalesTax method code." lightbox="./media/showsalestaxmethod.png":::

### Adding a new delegate

In this scenario, you modify an existing tax calculation method in the Application Foundation layer to account for discounts created in the Application Suite layer. The following class in the Foundation layer calculates the tax based on the gross total.

:::image type="content" source="media/simple-tax.png" alt-text="Screenshot of the Foundation layer class that calculates tax based on the gross total.":::

In the Application Suite, you introduce the notion of discounts by adding a ProductDiscount class that contains the current discount.

:::image type="content" source="./media/112.png" alt-text="Screenshot of the ProductDiscount class in the Application Suite." lightbox="./media/112.png":::

The TaxCalculator class in the lower Foundation layer doesn't have access to the DiscountRate in the Suite layer. It must use a delegate to update receipt total to use in the tax calculation. In the SimpleTax class, you create a delegate method, applyDiscountDelegate, with the state information that the handler needs in the signature. A delegate method is always empty because its only purpose is to define the contract between the delegate instance and the handler.

```xpp
delegate void applyDiscountDelegate(real _receiptTotal, EventHandlerResult _result)
{
} 
```

> [!NOTE]
> The signature for the delegate declaration, the delegate instance, and the delegate handler must match. You now need to create an instance of the delegate at the point in the code where you want the delegate handler to run. The changes between the &lt;isv&gt; tags represent the added code.

:::image type="content" source="media/calculate-total-tax.png" alt-text="Screenshot of the calculateTotalTax method.":::

With the delegate in place, add a handler method in the Application Suite layer that has access to the discount information.

:::image type="content" source="media/apply-discount-delegate-handler.png" alt-text="Screenshot of the applyDiscountDelegateHandler method.":::

By using the SubscribesTo keyword, you tie the applyDiscountDelegateHandler method as a handler to the applyDiscountDelegate delegate.

> [!NOTE]
> There can be more than one handler per delegate. There's **not** a defined order in the processing of handler methods. If order is important, chain together delegate handler pairs. By using the following final classes, when you run the calculateTotalTax() method, the applyDiscountDelegate fires and handles, updating the receiptTotal to provide an accurate tax calculation.

#### Full code

##### SimpleTax class in the Application Foundation Layer

:::image type="content" source="media/simple-tax-full-code.png" alt-text="Screenshot of the SimpleTax class in the Application Foundation Layer.":::

##### ProductDiscount class in the Application Suite layer

:::image type="content" source="media/product-discount-full-code.png" alt-text="Screenshot of the ProductDiscount class.":::

## Find delegates and handlers

You can find delegates and handlers by using three key methods:

- Metadata search
- Class references
- SubscribesTo references

For the best results, use the Metadata search tool described in [Metadata search in Visual Studio](../dev-tools/metadata-search-visual-studio.md). In Visual Studio, go to **Dynamics 365 &gt; Metadata Search** to open the metadata search tool.

:::image type="content" source="./media/del15.png" alt-text="Screenshot of the Metadata Search tool in Visual Studio." lightbox="./media/del15.png":::

In the search field, type `code:<delegate name>`. This search term restricts the search to code and finds any use of the delegate name. The search returns both the delegate and handler. Metadata search searches the entire code base and might take some time to complete, but it returns any use of the search term in code.

:::image type="content" source="./media/del16.png" alt-text="Screenshot of metadata search results for a delegate name." lightbox="./media/del16.png":::

You can use methods two and three in parallel with the metadata search. The class where a delegate is defined can also help you narrow down the search for a delegate or handler. The `SubscribesTo` keyword requires the class name where the delegate was defined. Visual Studio’s **find references** (right-click the class name > find references) returns a list of files that reference the class. This list includes both the class definition where the delegate is declared and the handler referencing the class. Finding class references isn't a perfect method and requires some manual searching through class references. However, it produces a smaller subset of files and can be faster than a metadata search.

:::image type="content" source="./media/del17-1024x300.png" alt-text="Screenshot of find references results for a class name." lightbox="./media/del17.png":::

Similar to finding class references, you can find all references on the `SubscribesTo` keyword. The resulting list includes all static delegate handlers. Manually going through this list provides another way to find static delegate handlers. This list doesn't include dynamically declared delegate handlers that don't use the `SubscribesTo` keyword.

:::image type="content" source="./media/del18-1024x328.png" alt-text="Screenshot of find references results for the SubscribesTo keyword." lightbox="./media/del18.png":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
