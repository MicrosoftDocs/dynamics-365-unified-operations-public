---
title: Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account
description: Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account
author: SmithaNataraj
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

# Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account

KB Number: 4603538

## Issue description

Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account whereas debut account has an option to select other dimensions

## Resolution

It is correct that it is not supported that the user can select a financial dimension for the credit account when the reconsolidation reason is not to pay the vendor but to credit a specific main account. This is not a product bug but a limitation in the current design. As such it works as expected. If the account structure dictates that a specific financial dimension value for the credit main account is required, then the resulting vendor journal cannot be automatically posted as the financial dimension value for the credit account must first be specified. This will have to be done manually in the vendor invoice journal form. As a dimension value for the credit account is required, it means that the vendor invoice journal cannot be auto posted and has to be posted manually after the dimension value has been manually added to the main account for the credit line.
  
We encourage you to create an entry on the Ideas Portal for this request. That will allow Microsoft to assess this feature extension request with other requests for future product planning.  
