---
title: Modify the properties of form controls through extension
description: Learn about how you can modify the properties of a control by using an extension, including a step-by-step example.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4
---

# Modify the properties of form controls through extension

[!include [banner](../includes/banner.md)]

Often, you need to change how users interact with the application. Typically, you hide or disable controls on the page, replace standard labels with labels that are more appropriate, or even add new controls that the user requires. You can also create a form extension.

> [!TIP]
> You can achieve even more flexibility through event subscription on form control events. This approach is discussed in other topics. In this article, the focus is on metadata changes.

## Example

The customer requires changes to the **Manage inventory** FastTab on the **Released product details** page. You must change the label of the FastTab, disable the field group that shows the catch weight configuration, and add new controls. (For this example, the new controls aren't bound to existing fields in the data source).

Follow these steps to make the required changes.

1. In the extension model, create an extension of the **EcoResProductDetailsExtended** form.
1. Navigate through the form design tree to the **TabPageInventory** tab page (**Design** &gt; **Tab** &gt; **Details** &gt; **GroupDetails** &gt; **TabHeader** &gt; **TabPageInventory**), select it in the designer, and open the **Property** sheet.
1. Update the **Caption** property to the desired value.

    :::image type="content" source="media/ModifyControlProperties01.jpg" alt-text="Screenshot of the Caption property.":::

1. Right-click the tab page, and then select **New**. Set the required properties on the new control. You can also move the control up and down in the immediate container to position it correctly.

    > [!NOTE]
    > Alternatively, right-click the subnode that the new control should appear after, select **Insert sibling**, and then select the type of control to add.

    :::image type="content" source="media/ModifyControlProperties02.jpg" alt-text="Screenshot of the Insert sibling command.":::

    Of course, you can just drag bound controls over from the corresponding data source.

1. Select the **PdsCatchWeight** group control, and change the **Enabled** property to **No**.

    :::image type="content" source="media/ModifyControlProperties03.jpg" alt-text="Screenshot of the Enabled property of the PdsCatchWeight group control.":::

    > [!NOTE]
    > If you change metadata properties such as **Enabled** and **Visible**, there's no guarantee that the control stays in that state at runtime. After a form loads, business logic on that form can change the state of controls through code.

When you finish, the page includes additional fields, catch weight information can't be edited, and the whole FastTab has a different caption.

:::image type="content" source="media/ModifyControlProperties04.jpg" alt-text="Screenshot of the Modified FastTab.":::

> [!NOTE]
> You can't modify the **AutoDeclaration** property on controls. However, you can still access the controls by name from code.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
