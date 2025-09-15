---
title: Budget funds available
description: Learn about the budget funds available parameter and how to configure budget control to optimize management of your organization's financial resources.
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 09/15/2025
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-28
ms.search.form: BudgetControlConfiguration
ms.dyn365.ops.version: AX 10.0.42
ms.assetid: be964167-43bc-431d-9adb-48bff32d68d5
---

# Budget funds available

[!include [banner](../includes/banner.md)]

This article provides information that helps configure budget control to optimize management of your organization's financial resources.

## Enhanced calculation parameter for budget funds available

The **Only track amounts in the budget funds available calculation** parameter lets you track the underlying budget control tables for document types and states, based on the settings on the **Define budget control parameters** page.

Some budget control configuration options must have specific settings for this parameter to work correctly. Those options are selected or cleared on the **Budget funds available** tab of the **Define budget control parameters** page. The following table shows the settings that are required for the **Only track amounts in the budget funds available calculation** parameter.

| If this option is selected | This option must also be selected |
| ------------------------- | -------------------------------- |
| Budget reservations for preencumbrances | Budget reservations for encumbrances *and* Actual expenditures |
| Budget reservations for encumbrances | Actual expenditures |
| Budget reservations for encumbrances with Purchase requisition type documents | Budget reservations for preencumbrances |

This parameter affects only new documents and new budget control configurations during activation. Amounts for existing documents continue to be tracked and shown in the budget control statistics inquiry until a budget funds available setting is changed and the new budget control configuration is activated. At that point, budget tracking data is removed for documents that were removed from the budget funds available calculation. If you try to activate new budget control configuration that doesn't align with the requirements defined in the table above, an error message appears. 

We recommend that you leave the **Unposted actual expenditures** option cleared. If it's selected, a time-consuming budget control calculation is done on unposted documents, such as pending vendor invoices.

To prevent incorrect setup on the **Document and journals** tab in the **Budget control configuration** that could lead to the inaccurate budget tracking, the following specific configuration options must be applied:

| If this option is selected to include on Documents and journals tab | Select this option on the Budget funds available tab | This option is optional on the Budget funds available tab |
| ------------------------- | -------------------------------- |-------------------------------- |
| **Purchase order** (header or line entry) | **Budget reservations for encumbrances** | **Budget reservations for unconfirmed encumbrances** and **Reduction to Budget reservations for unconfirmed encumbrances** |
| **Purchase requisition** (header or line entry) | **Budget reservations for preencumbrances** | **Budget reservations for unconfirmed preencumbrances** |
| **General budget reservation** (header or line entry) | **Budget reservations for encumbrances** | **Budget reservations for unconfirmed encumbrances** and **Reduction to Budget reservations for unconfirmed encumbrances** |
