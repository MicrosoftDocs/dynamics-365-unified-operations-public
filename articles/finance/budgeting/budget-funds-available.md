---
# required metadata

title: Budget funds available feature
description: This topic introduces the budget funds available feature and provides information to help you configure budget control to optimize management of your organization's financial resources.
author: rcarlson
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetControlConfiguration
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: ["60493", "intro-internal"]
ms.assetid: be964167-43bc-431d-9adb-48bff32d68d5
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2021-11-28
ms.dyn365.ops.version: AX 10.0.24

---

# Budget Funds Available 

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

#### Enhanced calculation feature for budget funds available.

The **Only track amounts in the budget funds available calculation** feature lets you track the underlying budget control tables for document types and states according to the settings marked on the **Define budget control parameters** page. 

Some budget control configuration settings must be set to specific values for this feature to work properly. The settings are marked or cleared in the **Budget funds available** tab on the **Define budget control parameters** page The settings that are required for the budget funds available feature are listed in the following table.

| If this setting is enabled        | This setting also needs to be enabled     |
| :---------------------------------- | :---------------------------------- |
| Budget reservations for pre-encumbrances | Budget reservations for encumbrances *and* Actual expenditures |
| Budget reservations for encumbrances | Actual expenditures |
| Budget reservations for encumbrances with Purchase Requisition type documents | Budget reservations for pre-encumbrances |

This feature will only affect new documents.  Existing documents will still have their amounts tracked and displayed accordingly in the budget control statistics inquiry until a budget-funds-available setting is changed and the new budget control configuration is activated.  At that point documents that were removed from the budget funds available calcualtion will have their budget tracking data removed. 

We recommended not marking the **Unposted actual expenditures** field. If this field *is* marked, a time-consuming budget control calculation will be performed on unposted documents, such as pending vendor invoices. 
