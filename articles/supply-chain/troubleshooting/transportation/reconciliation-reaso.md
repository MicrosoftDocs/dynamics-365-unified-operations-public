---
title: You can add only the main account as the credit account for reconciliation reasons
description: When you set up a reconciliation reason in Transportation management, you can add only the main account as the credit account.
author: Henrikan
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: TMSFBDetailReconcile
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# You can add only the main account as the credit account for reconciliation reasons

KB number: 4603538

## Symptoms

When you set up a reconciliation reason in Transportation management, you can add only the main account as the credit account. You can't add a cost center or any other dimension as the credit account. However, the debit account lets you select other dimensions.

## Resolution

If the reconciliation isn't done to pay the vendor but to credit a specific main account, the system doesn't allow you to select a financial dimension for the credit account when you set up the reconciliation reason.

If the account structure requires a specific financial dimension value for the credit main account, the resulting vendor journal can't be posted automatically, because the financial dimension value is missing. Therefore, you must first manually specify the credit account by using the **Invoice journal** page.

Because a dimension value is required for the credit account, the vendor invoice journal can't be automatically posted. You must manually post it after you manually add the dimension value to the main account for the credit line.
