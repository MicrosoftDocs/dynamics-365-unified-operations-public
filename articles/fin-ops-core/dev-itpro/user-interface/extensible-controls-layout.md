---
title: Extensible control layout guidelines
description: This article provides guidelines that you should follow when you specify the layout and sizing of extensible controls.
author: jasongre
ms.date: 04/27/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 53d1f66a-1e69-4548-9fd2-a87a3b370882
---

# Extensible control layout guidelines

[!include [banner](../includes/banner.md)]

This article provides guidelines that you should follow when you specify the layout and sizing of extensible controls.

## Dos and don'ts for achieving the desired layout

-   Don't use the layout classes on your control directly. (For example, **layout-container** and **layout-horizontal** are classes that you might see on controls in the DOM.) Instead, use the layout binding handlers to apply these classes. Internet Explorer uses a different layout framework, and to add some inline styles to elements, this framework requires the extra binding information that the handlers provide. Therefore, make sure that the classes are **not** hard-coded into the controls.
-   Don't use absolute positioning (**position: absolute** and **top**/**bottom**/**left**/**right** positions) for elements that are children of a container that uses the layout binding handler. Absolute positioning of these elements prevents the CSS classes that are applied from laying things out correctly.
-   Be careful about using **width: 100%** and **height: 100%**. These settings might not always work when they are combined with our layout CSS classes. If you want filling behavior, it's a good idea to use the **$dyn.layout.Size.available** option of the sizing binding handler instead.

## Layout binding handlers
### Layout

Used to apply **ArrangeMethod** and **Columns** attributes to containers Options: **arrangeMethod**, **Columns**, **Children**

#### ArrangeMethod

-   $dyn.layout.ArrangeMethod.vertical
-   $dyn.layout.ArrangeMethod.horizontalLeft
-   $dyn.layout.ArrangeMethod.horizontalWrap
-   $dyn.layout.ArrangeMethod.horizontalRight
-   $dyn.layout.ArrangeMethod.none (No layout CSS classes should be applied to the element.)

#### Columns

-   **$dyn.layout.Columns.fill** – Use this constant. Depending on the control, either "fill" and "balanced" columns are used.
-   **$dyn.layout.Columns.fixed** – Use a fixed value, such as **1**, **2**, or **3**.

#### Children

-   Use **$data.Children** if the content handlers (append, replace) will be used to append children through this container. It should be used only if this control is a container.

**Example usage:**

```html
<div data-dyn-bind="layout: { arrangeMethod: $dyn.layout.ArrangeMethod.vertical, columns: '1' }"> </div>
```

### Sizing

#### Height/width

-   **$dyn.layout.Size.available (SizeToAvailable)** – Fill the available space in that direction.
-   **$dyn.layout.Size.content (SizeToContent)** – Size to the contents in that direction.
-   **$dyn.layout.Size.fixed (Manual)** – A fixed pixel value.

**Example usage:**

```html
<div data-dyn-bind="sizing: { height: $dyn.layout.Size.available, width: $dyn.layout.Size.content }"> </div>
```

**Things to note about the sizing binding handler:**

-   When you use the sizing binding handler in combination with the **SizeToAvailable** option (**$dyn.layout.Size.available**), the layout binding handler must be used on the parent **&lt;div&gt;**/DOM element. This is how we know which axis to fill along (horizontal or vertical).

**Should you use layout/sizing handlers or set the properties directly?**

-   If your extensible control inherits from a client control (such as Group or PivotItem), you won't use the binding handlers directly on the **&lt;div&gt;** that is associated with that control, because the binding is already there. However, you might have to set the properties as you want them directly in the **data-dyn-bind** attribute.

**Example:**

```html
<div data-dyn-role="Group" data-dyn-bind="ArrangeMethod: $dyn.layout.ArrangeMethod.vertical, Columns: $dyn.layout.Columns.fill, Height: $dyn.layout.Size.available"></div>
```

## FAQ

#### Is my control being laid out as expected?

A good way to tell is to inspect the element and look for the desired classes.

-   Layout classes to look for, depending on the options applied:
    -   layout-container
    -   layout-vertical
    -   layout-horizontal
-   Sizing classes to look for:
    -   For **$dyn.layout.Size.available**,  you should see either **fill-width** or **fill-height**.
    -   For manual size, you should see either **fixed-height** or **fixed-width**.
    -   For **$dyn.layout.Size.content**, there should be no extra classes, and the manual height/width should be specified inline on the element.

If these classes don't appear as you expected, examine the usage of your binding handlers, and make sure that you've read through the list of dos and don'ts on this page.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
