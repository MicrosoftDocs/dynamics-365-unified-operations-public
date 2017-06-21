---
# required metadata

title: Retail statements
description: This topic describes how statements are created and posted.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 85183
ms.assetid: df9c62a2-6f13-4a08-bdca-07d041172c1b
ms.search.region: Global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Retail Version

---

# Retail statements
In Dynamics 365 for Retail, the statement posting process is used to account for the transactions that occur in Cloud POS (point-of sale) or Modern POS (MPOS). The statement posting process uses the Distribution schedule to pull in a set of POS transactions to the HQ client. The parameters defined on the Retail parameters form and the Stores form are used to select the transactions that are pulled into individual statements.  

The following diagram illustrates the statement posting process. In the process, transactions that are recorded in POS are transmitted to the client by using the Retail scheduler. After the client receives the transactions, you can create, calculate and post the transaction statement for the store. 

![this is the alt text](../images/Logo_DotNet.png)

