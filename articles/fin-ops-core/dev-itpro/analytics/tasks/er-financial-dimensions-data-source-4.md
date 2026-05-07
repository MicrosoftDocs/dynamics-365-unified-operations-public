---
title: ER Use financial dimensions as a data source (Part 4 - Run the report)
description: This article describes how to configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. (Part 4)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERSolutionTable, SysQueryForm
---

# ER Use financial dimensions as a data source (Part 4 - Run the report)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. You can perform these steps in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Use financial dimensions as a data source (Part 3: Design the report)" procedure. You must also configure default document types on the Electronic reporting parameters page. When you download and import any ER configuration, you also set default document types.

## Run report

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Financial dimensions sample model**.
1. In the tree, select **Financial dimensions sample model\Ledger journal report**.
1. Select **Run**.

   :::image type="content" source="../media/er-financial-dimensions-guides-run1.png" alt-text="Screenshot of the ER configurations page.":::

1. In the **Dimension name** field, enter or select a value.
   * To select all dimensions in the current company, enter the following information:  BusinessUnit;CostCenter;Department;ItemGroup;MainAccount;Project  

   :::image type="content" source="../media/er-financial-dimensions-guides-run2.png" alt-text="Screenshot of the Electronic report parameters slide out, Dimension name drop-down.":::

1. Expand the **Records to include** section.
1. Select **Filter**.
1. Select the row for the **Ledger journal** table and the **Journal batch number** field.
1. In the **Criteria** field, type `00057`.
1. Select **OK**.
1. Select **OK**.

   :::image type="content" source="../media/er-financial-dimensions-guides-run3.png" alt-text="Screenshot of the Electronic report parameters slide out, Reports to include section.":::

   * Review the generated output. For each transaction of the selected batch, the financial dimensions from the corresponding dimensions set are presented. Run this report and select different dimensions to see that the report isn't dependent on the number of selected dimensions or the number of dimensions configured for this instance.  

   :::image type="content" source="../media/er-financial-dimensions-guides-run4.png" alt-text="Screenshot of the ER configurations generated output.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
