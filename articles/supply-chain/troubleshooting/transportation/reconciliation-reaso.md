---
title: Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account
description: Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account
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
<!-- KFM: The title must be less than 80 chars. Please revise. -->
# Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account

KB Number: 4603538

## Issue description
<!-- KFM: The following is unclear. Please revise. Also, "debut account" or "debit account"?-->
The reconciliation reason does not allow you to add the cost center or any other dimension to the credit account except the main account, whereas the debut account has an option to select other dimensions.

## Resolution

This is the expected behavior. The system doesn't allows users to select a financial dimension for the credit account when the reconsolidation reason is not to pay the vendor but to credit a specific main account.

If the account structure dictates that a specific financial dimension value for the credit main account is required, then the resulting vendor journal can't be automatically posted as the financial dimension value. You must first specify the credit account manually using the **Vendor invoice journal** page. <!-- KFM: Is this the correct page name? I couldn't find it -->

Because a dimension value for the credit account is required, the vendor invoice journal can't be auto posted. It must be posted manually after manually adding the dimension value to the main account for the credit line.
