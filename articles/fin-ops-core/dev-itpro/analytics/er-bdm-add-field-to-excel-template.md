---
title: Add new fields to a business document template in Microsoft Excel
description: Learn about how to add new fields to a business document template in Microsoft Excel by using Business document management feature.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/09/2026
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-10-01
ms.search.form: ERBDWorkspace, ERBDParameters, ERBDTemplateEditor
ms.dyn365.ops.version: 10.0.7
ms.assetid: 
ms.custom:
  - sfi-image-nochange
---

# Add new fields to a business document template in Microsoft Excel

[!include[banner](../includes/banner.md)]

You can add new fields to a template that you use to generate business documents in Microsoft Excel format. Add these fields as placeholders to fill generated documents with required information from the application. For every field that you add, you can also specify a binding to the data sources, to specify what application data goes in the field when the template is used to generate business documents.

To learn more about this feature, complete the example in this article. This example shows how to update a template to fill in the fields in free text invoice forms that are generated.

## Configure Business document management to edit templates

Because Business document management (BDM) is built on top of the [Electronic reporting (ER) overview](general-electronic-reporting.md) framework, you must configure the required ER and BDM parameters before you can start to work with BDM.

1. Sign in to the instance of Microsoft Dynamics 365 Finance as the system administrator.
1. Complete the following steps of the example in the [Business document management overview](er-business-document-management.md) article:

    1. Configure ER parameters.
    1. Turn on BDM.

You can now start to use BDM to edit business document templates.

## Import ER solutions that contain a template

The example in this procedure uses the officially published ER solution. You must import the ER configurations of this solution into your current instance of Finance.

The **Free text invoice (Excel)** ER format configuration of this solution contains the business document template in Excel format that you can edit by using BDM. Import the latest version of this ER format configuration from Microsoft Dynamics Lifecycle Service. The corresponding ER data model and ER model mapping configurations are imported automatically.

For more information about how to import ER configurations, see [Manage the ER configuration lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md).

:::image type="content" source="./media/BDM-AddFldExcel-LCS.png" alt-text="Screenshot of the Lifecycle Services Shared asset library page.":::

### Edit the ER solution template

1. Sign in as a user who has access to the **Business document management** workspace.
1. Open the **Business document management** workspace.

    :::image type="content" source="./media/BDM-AddFldExcel-Workspace.png" alt-text="Screenshot of the Business document management workspace.":::

1. In the grid, select the **Free text invoice (Excel)** template.
1. In the right pane, select **New template** to create a new template that's based on the selected template.
1. In the **Title** field, enter **Free text invoice (Excel) Contoso** as the title of the new template.
1. Select **OK** to confirm the start of the editing process.

The BDM template editor page appears. You can use Microsoft 365 to edit the selected template online in the embedded control.

:::image type="content" source="./media/BDM-AddFldExcel-EditableTemplate.png" alt-text="Screenshot of the BDM template editor page.":::

### Add the label for a new field to the template

1. On the BDM template editor page, on the Excel ribbon, on the **View** tab, select the **Headings and Gridlines** check boxes for the editable Excel template.

    :::image type="content" source="./media/BDM-AddFldExcel-EditableTemplate2.png" alt-text="Screenshot of the Headings and Gridlines check boxes selected.":::

1. Select cells **E8:F8**.
1. On the Excel ribbon, on the **Home** tab, select **Merge & Center** to merge the selected cells into a new merged **E8:F8** cell.
1. In the merged cell **E8:F8**, enter **URL**.
1. Select merged cell **E7:F7**, select **Format painter**, and then select merged cell **E8:F8** to format it in the same way as merged cell **E7:F7**.

    :::image type="content" source="./media/BDM-AddFldExcel-EditableTemplate3.png" alt-text="Screenshot of the new field label added to the template.":::

### Format the template to reserve space for a new field

1. On the BDM template editor page, select merged cell **G8:H8**.
1. On the Excel ribbon, on the **Home** tab, select **Merge & Center** to merge the selected cells into a new merged **G8:H8** cell.
1. Select merged cell **G7:H7**, select **Format painter**, and then select merged cell **G8:H8** to format it in the same way as merged cell **G7:H7**.

    :::image type="content" source="./media/BDM-AddFldExcel-EditableTemplate4.png" alt-text="Screenshot of the space reserved for the new field.":::

1. In the **Name** box field, select **CompanyInfo**.

    The **CompanyInfo** range of the current Excel template holds all the fields that are used to fill the header of a generated report with the details of the current company as a seller party.

    :::image type="content" source="./media/BDM-AddFldExcel-SelectCompanyInfoRange.png" alt-text="Screenshot of the CompanyInfo range selected.":::

### Add a new field to the template

1. On **BDM template editor**, on the Action Pane, select **Show format**.
1. In the **Template structure** pane, select **Add**.

    > [!NOTE]
    > You must adjust the section of the template that you want to use as a new field. You already made this adjustment by formatting merged cell **G8:H8**.

    :::image type="content" source="./media/BDM-AddFldExcel-AddCell.png" alt-text="Screenshot of adding a new field to the template.":::

1. Select **Excel\Cell** to add a new field as a cell in the template.

    Select **Excel\Range** if you want to add a new range to the template. The range that you enter can contain multiple cells. You can add these cells later.

    The **Template structure** pane automatically selects the **CompanyInfo** template component because it's the most suitable parent component in the current template structure for the field that you're adding.

1. In the **Excel range** field, enter **CompanyURL_Value**.
1. Select **OK**.

    :::image type="content" source="./media/BDM-AddFldExcel-EditableTemplate5.png" alt-text="Screenshot of the CompanyURL_Value field added to the template structure.":::

1. In the **Template structure** pane, select the ellipsis button (...), and then select **Show bindings**.

    :::image type="content" source="./media/BDM-AddFldExcel-ShowBindings.png" alt-text="Screenshot of Show bindings selected.":::

    The **Template structure** pane now shows the data sources that are available in the underlying ER format.

1. Select **CompanyInfo_Value** as the field that you plan to bind to a data source of the underlying ER format.
1. In the **Data sources** section of the **Template structure** pane, expand **Model \> InvoiceBase \> CompanyInfo**.
1. Under **CompanyInfo**, select the **WebsiteURI** item.

    :::image type="content" source="./media/BDM-AddFldExcel-BindURL.png" alt-text="Screenshot of the WebsiteURI item selected.":::

1. Select **Bind**.
1. In the **Template structure** pane, select **Save**, and then close the BDM template editor page.

In the **Business document management** workspace, the **Template** tab in the right pane shows the updated template. In the grid, notice that the **Status** field for the edited template is **Draft**, and the **Revision** field is no longer blank. These changes indicate that the process of editing this template has started.

:::image type="content" source="./media/BDM-AddFldExcel-Workspace2.png" alt-text="Screenshot of the edited template in the Business document management workspace.":::

## Review company settings

1. Go to **Organization administration \> Organizations \> Legal entities**.
1. On the **Contact information** FastTab, verify that the company URL is entered.

:::image type="content" source="./media/BDM-AddFldExcel-CompanyInfo.png" alt-text="Screenshot of the company URL entered on the Legal entities page.":::

## Generate business documents to test the updated template

1. In the application, change the company to **USMF**, and go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select invoice **FTI-00000002**, and then select **Print management**.
1. In the left pane, expand **Module - accounts receivable \> Documents \> Free text invoice**.
1. Under **Free text invoice**, select the **Original document** level to specify the scope of invoices for processing.
1. In the right pane, in the **Report format** field, select the **Free text invoice (Excel) Contoso** template for the specified document level.

    :::image type="content" source="./media/BDM-AddFldExcel-PrintMngtSetting.png" alt-text="Screenshot of the Free text invoice (Excel) Contoso template selected.":::

1. Press **Esc** to close the current page.
1. Select **Print \> Selected**.
1. Download the generated document, and open it in Excel.

    :::image type="content" source="./media/BDM-AddFldExcel-PreviewReport.png" alt-text="Screenshot of the free text invoice in Excel.":::

The modified template is used to generate the free text invoice report for the selected item. To analyze how this report is affected by changes that you make to the template, run the report in one application session immediately after you change the template in another application session.

## Related links

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Business document management overview](er-business-document-management.md)

[Design a configuration for generating reports in OPENXML format](tasks/er-design-reports-openxml-2016-11.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
