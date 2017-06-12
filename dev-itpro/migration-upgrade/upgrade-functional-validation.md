---
# required metadata

title: Upgrade validation: Functional test pass
description: This topic explains how to perform a functional test pass to validate an upgraded Dynamics 365 for Finance and Operations, Enterprise edition, environment. 
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

After data upgrade is completed, we recommend that you complete a full functional test pass of all business processes. In a full functional test pass, you do an extensive retest of all business processes that are performed by using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. Tests should include both processes that have been brought forward from Microsoft Dynamics AX 2012 and new processes that use features from Finance and Operations.

Depending on your code quality, bug remediation and retesting might require several iterations of the functional test pass. After a bug is fixed, take care to retest all  processes that are involved, to make sure that no downstream or upstream processes are affected by the change.

## Old data vs. new data

As you create a list of tests to perform, consider the impact of old data versus new data. This type of testing will help you uncover data-related bugs. The code that created the old and new data might be very different, and this difference can be a common root cause of bugs.

For example, if the business process that you're testing is cancellation of a purchase order, can you cancel a purchase order that was started before it was upgraded to the new system? Can you also cancel a purchase order that was started after the upgrade to the new system? 

We used a very simple example here, but the testing requirement can be more complex, because many business processes in the system are interconnected, and the effect of old data versus new data effect is cumulative.

For example, here are the stages of a production test flow:

1. The item master is designed and released to a legal entity.
2. Item requirements are created.
3. Production orders are generated.
4. Purchase orders are generated.
5. Production order processing  occurs (shop floor).
6. Vendor payment (payment of purchase orders) occurs, and so on.

In this production test flow, each stage can be performed by using either new records or old records as input. The result is a matrix of tests that covers every combination of old and new data. For some processes, test matrices might seem excessive, and they might actually be excessive in practice. Therefore, you can decide to focus on certain combinations that you predict will be used the most. However, it's still helpful for you to know what you aren't covering. Make a conscious decision, where you know what you have, what you’re going to focus most of the testing on, and what you’re not going to focus on.

