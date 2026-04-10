---
title: ER Use financial dimensions as a data source (Part 1 - Design data model)
description: This article describes how to configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. (Part 1)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionTable, ERSolutionCreateDropDialog, ERDataModelDesigner, ERDataModelContentsItemCreationDialog
---

# ER Use financial dimensions as a data source (Part 1 - Design data model)

[!include [banner](../../includes/banner.md)]

The following steps explain how a system administrator or electronic reporting developer can configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the procedure, "Create a configuration provider and mark it as active".

## Create a new data model

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
    * Make sure that the **Litware, Inc.** provider is available and marked as active.  
1. Select **Reporting configurations**.
1. Select **Create configuration** to open the form.
1. In the **Name** field, type *Financial dimensions sample model*.
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **New** to open the form.
1. In the **Name** field, type *Entry*.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Company*.
1. Select **Add**.
    * Add a new record list to your model. This list exposes the settings of selected financial dimensions for any ER reports that use this model as a data source. Each financial dimension appears in this list as a record with fields that represent the dimension's settings.  
1. Select **New** to open the form.
1. In the **Name** field, type *Dimensions setting*.
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Code*.
1. In the **Item type** field, select **String**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Name*.
1. Select **Add**.
1. In the tree, select **Entry**.
1. Select **New** to open the form.
1. In the **Name** field, type *Journal*.
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Batch*.
1. In the **Item type** field, select **String**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Transaction*.
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Date*.
1. In the **Item type** field, select **Date**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Debit*.
1. In the **Item type** field, select **Real**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Credit*.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Currency*.
1. In the **Item type** field, select **String**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Voucher*.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Dimensions data*.
1. In the **Item type** field, select **Record list**.
1. Select **Add**.
    * You add a new record list to your model. This list exposes the values of selected financial dimensions for any ER reports that use this model as a data source. Each financial dimension appears in this list as a record with fields that represent the dimension's values. The dimension name also appears in this record as a field that you can use for selection purposes.  
1. Select **New** to open the form.
1. In the **Name** field, type *Code*.
1. In the **Item type** field, select **String**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type **Description**.
1. Select **Add**.
1. Select **New** to open the form.
1. In the **Name** field, type *Name*.
1. Select **Add**.
1. Select **Save**.
1. Close the page.

:::image type="content" source="../media/er-financial-dimensions-guides-data-model.png" alt-text="Screenshot of the ER data model designer page.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
