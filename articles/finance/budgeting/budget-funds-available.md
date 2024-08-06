---
title: Budget funds available
description: Learn about the budget funds available parameter and how to configure budget control to optimize management of your organization's financial resources.
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 07/24/2024
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
[!include [preview banner](../includes/preview-banner.md)]

This article explains the **Only track amounts in the budget funds available calculation** parameter and provides information that helps you configure budget control to optimize management of your organization's financial resources.

## Enhanced calculation parameter for budget funds available

The **Only track amounts in the budget funds available calculation** parameter lets you track the underlying budget control tables for document types and states, based on the settings on the **Define budget control parameters** page.

Some budget control configuration options must have specific settings for this parameter to work correctly. Those options are selected or cleared on the **Budget funds available** tab of the **Define budget control parameters** page. The following table shows the settings that are required for the **Only track amounts in the budget funds available calculation** parameter.

| If this option is selected | This option must also be selected |
| ------------------------- | -------------------------------- |
| Budget reservations for pre-encumbrances | Budget reservations for encumbrances *and* Actual expenditures |
| Budget reservations for encumbrances | Actual expenditures |
| Budget reservations for encumbrances with Purchase Requisition type documents | Budget reservations for pre-encumbrances |

This parameter affects only new documents as well as new budget control configurations during activation. Amounts for existing documents will continue to be tracked and shown in the budget control statistics inquiry until a budget funds available setting is changed and the new budget control configuration is activated. At that point, budget tracking data will be removed for documents that were removed from the budget funds available calculation. If you try to activate new budget control configuration that doesn't align with the requirements defined in the table above, an error message will appear. 

We recommend that you leave the **Unposted actual expenditures** option cleared. If it's selected, a time-consuming budget control calculation will be done on unposted documents, such as pending vendor invoices.
