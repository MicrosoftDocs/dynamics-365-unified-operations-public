---
title: Upgrade from AX 2012 - Functional test passes
description: Learn about how to perform a functional test pass to validate an upgraded finance and operations environment, including an overview on old data versus new data.
author: LaneSwenka
ms.author: laswenka
ms.topic: upgrade-and-migration-article
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade from AX 2012 - Functional test passes

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

After data upgrade finishes, complete a full functional test pass of all business processes. In a full functional test pass, extensively retest all business processes that you perform by using finance and operations. Include tests for both processes that you bring forward from Microsoft Dynamics AX 2012 and new processes that use features from finance and operations.

Depending on your code quality, bug remediation and retesting might require several iterations of the functional test pass. After you fix a bug, retest all involved processes to make sure that no downstream or upstream processes are affected by the change.

## Old data vs. new data

As you create a list of tests to perform, consider the impact of old data versus new data. This type of testing helps you uncover data-related bugs. The code that creates the old and new data might be very different. This difference can be a common root cause of bugs.

For example, if the business process that you're testing is cancellation of a purchase order, can you cancel a purchase order that started before the upgrade to the new system? Can you also cancel a purchase order that started after the upgrade to the new system? 

This example is very simple, but the testing requirement can be more complex. Many business processes in the system are interconnected, and the effect of old data versus new data is cumulative.

For example, here are the stages of a production test flow:

1. The item master is designed and released to a legal entity.
1. Item requirements are created.
1. Production orders are generated.
1. Purchase orders are generated.
1. Production order processing  occurs (shop floor).
1. Vendor payment occurs (payment of purchase orders), and so on.

In this production test flow, you can perform each stage by using either new records or old records as input. The result is a matrix of tests that covers every combination of old and new data. For some processes, test matrices might seem excessive, and they might actually be excessive in practice. Therefore, you can decide to focus on certain combinations that you predict you'll use the most. However, it's still helpful for you to know what you aren't covering. Make a conscious decision, where you know what you have, what you’re going to focus most of the testing on, and what you’re not going to focus on.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
