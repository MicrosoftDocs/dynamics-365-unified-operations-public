---
# required metadata

title: Upgrade from AX 2012 - Prepare for go-live
description: This topic describes how you can help ensure that the source Dynamics AX 2012 system and the upgrade process remain stable and consistent for go-live.
author: tariqbell
ms.date: 02/17/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade from AX 2012 - Prepare for go-live

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

As the go-live date approaches, it's important that you implement this series of steps to help ensure that the source Microsoft Dynamics AX 2012 system and the upgrade process both remain stable and consistent for go-live.

As part of this process, you must lock down any further code changes or application setup changes before you run the final cutover test.

## Code freeze

All code changes in the AX 2012 environment should be frozen. Implement an escalation process to handle any critical issues that appear in AX 2012. By default, any new code changes that are required should be implemented only in the new system, not in the AX 2012 environment. Implementation of proposed code changes in the AX 2012 environment should be discussed at the management level. If a code change is made in AX 2012, the same change must be made in the new system. In that case, another iteration of cutover testing and functional testing might be required.

## Application configuration freeze

All application configuration changes should be frozen in the AX 2012 environment, because these changes could affect how the new system behaves or how the data upgrade scripts behave. Configuration changes are changes in the AX 2012 application that are related to the configuration of system functionality. By freezing these changes, you help guarantee the stability of the data upgrade process.

Because configuration changes are typically controlled by the AX 2012 system administrator or a small group of trusted super users, we don't recommend that you enforce the freeze by changing security access. Instead, implement the freeze through a business process that is communicated to those users. Changes to security access might require a code change (changes to the role definitions themselves) or a configuration change (reassignment of users), and these changes could affect the upgrade process.

## Running the final cutover test

After no further code or setup changes will occur, run a final cutover test to make sure that all data and code upgrade tasks still run as expected.

> [!NOTE]
> You must complete this step even if you freeze code and setup changes at the beginning of the upgrade project, because the data itself changes every day. This final cutover test also validates that the current data is upgraded successfully.

Complete an end-to-end data upgrade test. 

> [!WARNING]
> It is critical that you have completed at least one final test data upgrade, and that this was tested again in the live AX 2012 Production Environment to ensure the replication process works with the active transactional database. Testing replication against a copy of production is not the same, as active transactions in the SQL database affect how the replication works. Also, this test run should be within a short time frame, such as a few weeks of the actual go live. Leaving a large time between the final test run and the go-live could invalidate the testing if the data volume has increased significantly.

Make sure that functional testing is performed against this last upgraded copy.

At this point in the upgrade project, we recommend that you categorize any bugs that are found:
- **Blocking** – The upgrade project can't proceed until every bug of this type is fixed. The upgrade must be postponed, and can proceed only after the bug is remediated and the cutover test is run again. For a bug to be classified as blocking, it must meet these conditions:

    - It prevents a critical business process from being completed.
    - No workaround or mitigation is available for it.

- **Non-blocking** – The upgrade project can proceed. Bugs of this type can be fixed in the upgraded system.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
