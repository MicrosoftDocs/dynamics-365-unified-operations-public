---
# required metadata

title: Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account
description: Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TMSFBDetailReconcile
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: henrikan@microsoft.com

---

# Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account

KB Number: 4603538

Reconciliation reason does not allow to add Cost center or any other dimension in credit account except main account whereas debut account has an option to select other dimensions


## Resolution
It is correct that it is not supported that the user can select a financial dimension for the credit account when the reconsolidation reason is not to pay the vendor but to credit a specific main account. This is not a product bug but a limitation in the current design. As such it works as expected. If the account structure dictates that a specific financial dimension value for the credit main account is required, then the resulting vendor journal cannot be automatiaclly posted as the financial dimension value for the credit account must first be specified. This will have to be done manually in the vendor invoice journal form. As a dimension value for the credit account is required, it means that the vendor invoice journal cannot be auto posted and has to be posted manually after the dimension value has been manually added to the main account for the credit line. 
  
We encourage you to create an entry on the Ideas Portal for this request. That will allow Microsoft to assess this feature extension request with other requests for future product planning.  


