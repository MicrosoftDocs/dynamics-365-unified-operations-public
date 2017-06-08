---
# required metadata

title: Upgrade validation: Functional test pass
description: This topic describes how to perform a functional test pass to validate an upgraded Dynamics 365 for Finance and Operations, Enterprise edition environment. 
author: tariqbell
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer;IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations Platform
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade validation: Functional test pass

[!include[banner](../includes/banner.md)]

After data upgrade is complete, we recommend that you complete a full functional test pass of all business processes. This will be an extensive re-test of all business processes that are performed using Dynamics 365 Finance and Operations, Enterprise edition. Tests should include both processes brought forward from Dynamics AX 2012 and new processes that use features from Finance and Operations.

Depending on your code quality, you may require several iterations of functional test pass to allow for bug remediation and re-testing. Take care to retest all involved processes when a bug is fixed to ensure your downstream and upstream processes are not affected by the change.

## Old data vs new data

As you create a list of tests to perform, consider the impact of old data vs new data. For example, let’s say the business process we are testing is cancelling a purchase order – can we cancel a purchase order that was started before it was upgraded to the new system? Can we also cancel a purchase order that was started after the upgrade to the new system? This type of testing will help you uncover data related bugs – as the old and new data may have been created by quite different code, this can be a common root cause of bugs.

We used a very simple example to above, but the testing requirement can be more complex, becausea lot of business processes within the system are interconnected, and the effect of old data vs new data effect is cumulative. 

Production test flow stages: 
-	Item master is designed and released to a legal entity
-	Item requirements are created
-	Production orders are generated 
-	Purchase orders are generated
-	Production order processing (shop floor)
-	Vendor payment (pay PO) etc..

In the production test flow above each mentioned stage could be performed using either new or old records as input, which creates a matrix of tests covering every combination of old and new data. For some processes, test matrices may seem like overkill, and pragmatically that may be true – you can decide to focus on certain combinations that you predict will be used the most. However, it is still helpful for you to know what you are not covering – make a conscious decision knowing what you have out there, what you’re going to focus most testing on, and what you’re not going to focus on.

## Document states
The state of a particular document, such as a production order or sales order, can affect how  
