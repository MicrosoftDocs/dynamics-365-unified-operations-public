---
title: ER Use financial dimensions as a data source (Part 3 - Design the report)
description: This article describes how to configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. (Part 3)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---

# ER Use financial dimensions as a data source (Part 3 - Design the report)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "ER Use financial dimensions as a data source (Part 2: Model mapping)" procedure.

## Design a report to present financial dimensions

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, select **Financial dimensions sample model**.
1. Select **Create configuration** to open the form.
1. In **New**, enter *Format based on data model Financial dimensions sample model*.
    * Use the model that you created in advance as the data source for your new report.  
1. In **Name**, type *Ledger journal report*.
1. In **Data model definition**, select *Entry*.
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **Add root** to open the form.
1. In the tree, select **XML\Element**.
1. In **Name**, type *Root*.
1. Select **OK**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Attribute**.
1. In **Name**, type *Company*.
1. Select **OK**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Element**.
1. In **Name**, type *Journal*.
1. Select **OK**.
1. In the tree, select **Root: XML Element\Journal: XML Element**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Attribute**.
1. In **Name**, type *Batch*.
1. Select **OK**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Element**.
1. In **Name**, type *Transaction*.
1. Select **OK**.
1. In the tree, select **Root: XML Element\Journal: XML Element\Transaction: XML Element**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Attribute**.
1. In **Name**, type *Voucher*.
1. Select **OK**.
1. Select **Add Attribute**.
1. In **Name**, type *Date*.
1. Select **OK**.
1. Select **Add Attribute**.
1. In **Name**, type *Currency*.
1. Select **OK**.
1. Select **Add Attribute**.
1. In **Name**, type *Dt*.
1. Select **OK**.
1. Select **Add Attribute**.
1. In **Name**, type *Ct*.
1. Select **OK**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Element**.
1. In **Name**, type *Dimensions*.
1. Select **OK**.
1. In the tree, select **Root: XML Element\Journal: XML Element\Transaction: XML Element\Dimensions: XML Element**.
1. Select **Add** to open the form.
1. In the tree, select **XML\Attribute**.
1. In **Name**, type *Code*.
1. Select **OK**.
1. Select **Add Attribute**.
1. In **Name**, type *Value*.
1. Select **OK**.
1. Select **Add Attribute**.
1. In the **Name** field, enter `Desc`.
1. Select **OK**.
:::image type="content" source="../media/er-financial-dimensions-guides-format1.png" alt-text="Screenshot of the Format designer page tree.":::

## Map report elements to data sources

1. Select the **Mapping** tab.
1. In the tree view, expand `model: Data model Financial dimensions sample model`.
1. In the tree view, expand `model: Data model Financial dimensions sample model\Journal: Record list`.
1. In the tree view, expand `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list`.
1. In the tree view, expand `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list`.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Dimensions: XML Element\Desc: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list\Description: String`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Dimensions: XML Element\Value: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list\Code: String`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Dimensions: XML Element\Code: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list\Name: String`.
1. Select **Bind**.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Dimensions data: Record list`.
1. In the tree, select **Root: XML Element\Journal: XML Element\Transaction: XML Element\Dimensions: XML Element**.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Ct: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Credit: Real`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Dt: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Debit: Real`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Currency: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Currency: String`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Date: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Date: Date`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Transaction: XML Element\Voucher: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list\Voucher: String`.
1. Select **Bind**.
1. In the tree, select **Root: XML Element\Journal: XML Element\Transaction: XML Element**.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Transaction: Record list`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Journal: XML Element\Batch: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list\Batch: String`.
1. Select **Bind**.
1. In the tree, select **Root: XML Element\Journal: XML Element**.
1. In the tree view, select `model: Data model Financial dimensions sample model\Journal: Record list`.
1. Select **Bind**.
1. In the tree view, select `Root: XML Element\Company: XML Attribute`.
1. In the tree view, select `model: Data model Financial dimensions sample model\Company: String`.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.
:::image type="content" source="../media/er-financial-dimensions-guides-format2.png" alt-text="Screenshot of the Format designer page, report elements mapped to data sources.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
