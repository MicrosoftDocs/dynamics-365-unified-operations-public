---
title: Update the structure of a business document template
description: Learn about how to update the structure of a business document template by using the Business document management feature.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/09/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.form: ERBDWorkspace, ERBDParameters, ERBDTemplateEditor
ms.search.region: Global
ms.search.validFrom: 2019-12-01
ms.dyn365.ops.version: 10.0.9
ms.assetid: 
---

# Update the structure of a business document template

[!include[banner](../includes/banner.md)]

In the **Template structure** pane of the [Business document management](er-business-document-management.md) template editor, you can modify a business document template by [adding new fields](er-bdm-add-field-to-excel-template.md) to a template in Microsoft Excel. Dynamics 365 Finance automatically updates the structure of the template to reflect the changes you made in the **Template structure** pane.

You can also modify a template by using Office 365 online functionality. For example, you can add a new named item, such as a picture or shape, to the editable worksheet. In this case, the structure of the template isn't automatically updated in Finance, and the item that you added doesn't appear in the **Template structure** pane. You must manually update the template structure in Finance by selecting **Update structure** on the template editor page.

For more information about this feature, complete the following example.

## Example: Update the structure of a business document template

This example shows how a system administrator can update the structure of a business document template in Finance after modifying the template in Office Online. The following sections explain the steps that are involved.

### Prepare a business document template for editing

Complete the following procedures in [Business document management overview](er-business-document-management.md).

1. [Configure ER parameters](er-business-document-management.md#configure-er-parameters)
1. [Import ER solutions](er-business-document-management.md#import-er-solutions)
1. [Enable Business document management](er-business-document-management.md#enable-business-document-management)
1. [Configure parameters](er-business-document-management.md#configure-parameters)

### Edit a business document template

1. In the **Business document management** workspace, select **New document**.
1. On **Create a new template**, select the **Free text invoice (ER sample)(Excel)** template.
1. Select **Create document**.
1. In the **Title** field, enter **FTI sample Litware**.
1. Select **OK** to create the new template.

    > [!NOTE]
    > If you aren't signed in to Office Online, you're [directed to the Office 365 sign-in page](er-business-document-management.md#frequently-asked-questions). To return to your Finance environment, select the **Back** button in your browser.

    The new template opens for editing in the Excel Online embedded control on the template editor page.

:::image type="content" source="./media/er-bdm-update-structure1.gif" alt-text="Screenshot of using the Business document management workspace to start to edit a business document template.":::

### Review the current structure of the editable template

1. In Excel Online, on the ribbon, on the **View** tab, in the **Show** group, select **Gridlines**.
1. In the editable template, select the rectangle above the template title. This rectangle is a picture that is named **rptHeaderCompLogo**.
1. If the **Template structure** pane is hidden, select **Show structure**.
1. In the **Template structure** pane, expand **Report \> Invoice \> rptHeader \> rptHeaderPart1**.
1. Notice that, in the template structure in Finance, the **rptHeaderCompLogo** item appears as a child item of **Report \> Invoice \> rptHeader \> rptHeaderPart1**.

:::image type="content" source="./media/er-bdm-update-structure2.gif" alt-text="Screenshot of using the Business document management workspace to review the current structure of an editable template.":::

### Update the structure of a business document template by deleting a picture

1. In Excel Online, in the editable template, select the **rptHeaderCompLogo** picture.
1. Use one of the following methods to delete the selected picture from the editable template:

    - Select the **Delete** key on your keyboard.
    - Select and hold (or right-click) the picture, and then select **Cut**.

    > [!NOTE]
    > The **rptHeaderCompLogo** item still appears in the template structure in Finance, even though the picture is no longer included in the Excel template.

1. Select **Update structure** to sync the structure of the editable template in Excel and Finance.
1. In the **Template structure** pane, expand **Report \> Invoice \> rptHeader \> rptHeaderPart1**.
1. The **rptHeaderCompLogo** item is no longer included in the template structure in Finance.

:::image type="content" source="./media/er-bdm-update-structure3.gif" alt-text="Screenshot of using the Business document management workspace to delete a picture from a business document template.":::

### Update the structure of a business document template by adding a picture

1. In Excel Online, on the ribbon, on the **Insert** tab, in the **Illustrations** group, select **Picture**.
1. Select **Choose file**, browse to the image that you want to add, select it, and then select **OK**.
1. Select **Insert**.
1. Move the new picture until it's in the correct place. By default, Excel names the picture. For example, it might name the picture **Picture 2**.
1. Select **Update structure** to sync the structure of the editable template in Excel and Finance.
1. In the **Template structure** pane, expand **Report \> Invoice \> rptHeader \> rptHeaderPart1**.
1. The new picture is now included as an item in the template structure in Finance.

:::image type="content" source="./media/er-bdm-update-structure4.gif" alt-text="Screenshot of using the Business document management workspace to add a picture to a business document template.":::

## Related links

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Business document management overview](er-business-document-management.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
