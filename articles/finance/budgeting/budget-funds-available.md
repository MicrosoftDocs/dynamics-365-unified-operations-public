---
# required metadata

title: Budget funds available
description: This article introduces the budget funds available feature and provides information that can help you configure budget control to optimize management of your organization's financial resources.
author: RyanCCarlson2
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetControlConfiguration
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: be964167-43bc-431d-9adb-48bff32d68d5
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2021-11-28
ms.dyn365.ops.version: AX 10.0.24

---

# Budget funds available

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article introduces the budget funds available feature and provides information that can help you configure budget control to optimize management of your organization's financial resources.

## Enhanced calculation feature for budget funds available

The **Only track amounts in the budget funds available calculation** feature lets you track the underlying budget control tables for document types and states, based on the settings on the **Define budget control parameters** page.

Some budget control configuration options must have specific settings for the feature to work correctly. Those options are selected or cleared on the **Budget funds available** tab of the **Define budget control parameters** page. The following table shows the settings that are required for the budget funds available feature.

| If this option is selected | This option must also be selected |
| ------------------------- | -------------------------------- |
| Budget reservations for pre-encumbrances | Budget reservations for encumbrances *and* Actual expenditures |
| Budget reservations for encumbrances | Actual expenditures |
| Budget reservations for encumbrances with Purchase Requisition type documents | Budget reservations for pre-encumbrances |

This feature affects only new documents. Amounts for existing documents will continue to be tracked and shown in the budget control statistics inquiry until a budget funds available setting is changed and the new budget control configuration is activated. At that point, budget tracking data will be removed for documents that were removed from the budget funds available calculation.

We recommend that you leave the **Unposted actual expenditures** option cleared. If it's selected, a time-consuming budget control calculation will be done on unposted documents, such as pending vendor invoices.
