---
# required metadata

title: Update structure of a business document template in Finance
description: This topic provides information about how to update structure of a business document template in Finance by using Business document management feature.
author: NickSelin
manager: AnnBe
ms.date: 11/5/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERBDWorkspace, ERBDParameters, ERBDTemplateEditor
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2019-12-01
ms.dyn365.ops.version: 10.0.9

---

# Update structure of a business document template in Finance

[!include[banner](../includes/banner.md)]

You can use the **Template structure** panel of the [Business document management](er-business-document-management.md) template editor to modify a business document template by [adding new fields](er-bdm-add-field-to-excel-template.md) to a template in Microsoft Excel format. When a template is updated this way, the structure of this template is automatically modified in Finance reflecting all changes on the **Template structure** panel.

Alternatively, you can modify a template by using Office online functionality. For example, you can add a new named item (a picture, a shape, etc.) to the editable worksheet. In this case the structure of this template is not automatically modified in Finance and an added item is not visible on the **Template structure** panel. To force a template structure update, select the **Update structure** option on the template editor page.

For more information about this feature, complete the following steps of an example.

## Example: Update structure of a business document template

This example shows how a user in the System administrator role can update the structure of a business document template in Finance after this template has been modified in Office online. Here is an overview of the steps that are involved.

### Prepare a business document template for editing

Complete the following steps of the example in the [Business document management overview](er-business-document-management.md) topic:

1.  [Configure ER parameters](er-business-document-management.md#configure-er-parameters)
2.  [Import ER solutions](er-business-document-management.md#import-er-solutions)
3.  [Enable Business document management](er-business-document-management.md#enable-business-document-management)
4.  [Configure parameters](er-business-document-management.md#configure-parameters)

### Start editing a business document template

1.  Open the **Business document management** workspace.
2.  On the **Business document management** workspace, select **New**.
3.  On the **Create a new template** page, select the **Free text invoice (ER sample)(Excel)** template.
4.  Select **Create document**.
5.  In the **Title** field, enter **FTI sample Litware**.
6.  Select **OK** to confirm a new template creation.
        > [!NOTE]
    > You will be [navigated](er-business-document-management.md#i-selected-edit-document-but-instead-of-opening-the-bdm-template-editor-page-in-finance-and-operations-i-have-been-sent-to-the-microsoft-365-web-page) to the Office 365 sign-in page if you have not signed in to Office online yet. Select the **Back** button of your browser to navigate back to Finance.

When you come back to Finance, the created template is opened for editing in Excel online embedded control of the Business document management template editor page.

[![Use Business document management workspace to start editing a business document template](./media/er-bdm-update-structure1.gif)](./media/er-bdm-update-structure1.gif)

### Review the current structure of the editable template

1.  In Excel online, enable the **Show gridlines** option.
2.  In the editable template, select the rectangle that is located above the template title.
3.  Note that in Excel this picture is named as **rptHeaderCompLogo**.
4.  Toggle the **Show structure** button if the **Template structure** panel is hidden.
5.  On the **Template structure** panel, expand tree nodes to access the content of the **Report \> Invoice \> rptHeader \> rptHeaderPart1**.
    > Note that the **rptHeaderCompLogo** item is presented in the template structure of Finance as the child item of the **Report \> Invoice \> rptHeader \> rptHeaderPart1** one.

[![Use Business document management workspace to review the current structure of the editable template](./media/er-bdm-update-structure2.gif)](./media/er-bdm-update-structure2.gif)

### Update structure of a business document template - delete a picture

1.  In Excel online, select the **rptHeaderCompLogo** picture.
2.  Use one of the following options to delete a selected picture from the editable template:
    1.  Press the **Delete** keyboard button.
    2.  Right click to the selected picture and use the **Cut** option.
    > Note that the **rptHeaderCompLogo** item is still presented in the template structure of Finance despite the fact that this picture is not available in the Excel template anymore.
3.  Select **Update structure** to synchronize the structure of the editable template in Excel and Finance.
4.  On the **Template structure** panel, expand tree nodes to access the content of the **Report \> Invoice \> rptHeader \> rptHeaderPart1**.
    > Note that the **rptHeaderCompLogo** item is not presented any more in the template structure of Finance.

[![Use Business document management workspace to update a business document template](./media/er-bdm-update-structure3.gif)](./media/er-bdm-update-structure3.gif)

### Update structure of a business document template - add a picture

1.  In Excel online, select **Insert \> Picture**.
2.  Select **Choose file**, browse to find an image file, point at the found file and select **OK**.
3.  Select **Insert**.
4.  Move the added picture to properly position it.
    > Note that by default it is named automatically, for example, as **Picture 2**.
5.  Select **Update structure** to synchronize the structure of the editable template in Excel and Finance.
4.  On the **Template structure** panel, expand tree nodes to access the content of the **Report \> Invoice \> rptHeader \> rptHeaderPart1**.
    > Note that the **Picture 2** item is now presented in the template structure of Finance.

[![Use Business document management workspace to update a business document template](./media/er-bdm-update-structure4.gif)](./media/er-bdm-update-structure4.gif)

## Related links

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Business document management overview](er-business-document-management.md)
