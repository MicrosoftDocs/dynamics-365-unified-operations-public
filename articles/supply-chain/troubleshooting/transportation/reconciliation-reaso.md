---
title: Can only add the main account as the credit account for reconciliation reasons
description: When you setup a reconciliation reason in transportation management, you can only add the main account as the credit account. You can't add a cost center, or any other dimension, as the credit account.
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

# Can only add the main account as the credit account for reconciliation reasons

KB Number: 4603538

## Symptoms

When you setup a reconciliation reason in transportation management, you can only add the main account as the credit account. You can't add a cost center, or any other dimension, as the credit account. However, the debit account has an option to select other dimensions.

## Resolution

The system doesn't allows you to select a financial dimension for the credit account when the reconsolidation reason is not to pay the vendor but to credit a specific main account.

If the account structure dictates that a specific financial dimension value for the credit main account is required, then the resulting vendor journal can't be automatically posted because the financial dimension value is missing. You must therefore first specify the credit account manually using the **Invoice journal** page.

Because a dimension value for the credit account is required, the vendor invoice journal can't be auto-posted. It must be posted manually after manually adding the dimension value to the main account for the credit line.
