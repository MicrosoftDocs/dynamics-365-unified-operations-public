---
title: Upgrade from AX 2012 - Prepare for go-live
description: Learn about how you can help ensure that the source Dynamics AX 2012 system and the upgrade process remain stable and consistent for go-live.
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

# Upgrade from AX 2012 - Prepare for go-live

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

As the go-live date approaches, implement this series of steps to help ensure that the source Microsoft Dynamics AX 2012 system and the upgrade process both remain stable and consistent for go-live.

As part of this process, lock down any further code changes or application setup changes before you run the final cutover test.

## Code freeze

Freeze all code changes in the AX 2012 environment. Implement an escalation process to handle any critical issues that appear in AX 2012. By default, implement any new code changes in the new system, not in the AX 2012 environment. Discuss implementation of proposed code changes in the AX 2012 environment at the management level. If you make a code change in AX 2012, make the same change in the new system. In that case, you might need another iteration of cutover testing and functional testing.

## Application configuration freeze

Freeze all application configuration changes in the AX 2012 environment, because these changes could affect how the new system behaves or how the data upgrade scripts behave. Configuration changes are changes in the AX 2012 application that are related to the configuration of system functionality. By freezing these changes, you help guarantee the stability of the data upgrade process.

Because the AX 2012 system administrator or a small group of trusted super users typically control configuration changes, don't enforce the freeze by changing security access. Instead, implement the freeze through a business process that you communicate to those users. Changes to security access might require a code change (changes to the role definitions themselves) or a configuration change (reassignment of users), and these changes could affect the upgrade process.

## Running the final cutover test

After making all code and setup changes, run a final cutover test to make sure that all data and code upgrade tasks still run as expected.

> [!NOTE]
> You must complete this step even if you freeze code and setup changes at the beginning of the upgrade project, because the data itself changes every day. This final cutover test also validates that the current data is upgraded successfully.

Complete an end-to-end data upgrade test.

> [!WARNING]
> It's critical that you complete at least one final test data upgrade. Test this upgrade again in the live AX 2012 Production Environment to ensure the replication process works with the active transactional database. Testing replication against a copy of production isn't the same, as active transactions in the SQL database affect how the replication works. Also, this test run should be within a short time frame, such as a few weeks of the actual go live. Leaving a large time between the final test run and the go-live could invalidate the testing if the data volume has increased significantly.

Make sure that functional testing is performed against this last upgraded copy.

At this point in the upgrade project, categorize any bugs that you find:

- **Blocking** – The upgrade project can't proceed until you fix every bug of this type. Postpone the upgrade. You can proceed only after you remediate the bug and run the cutover test again. For a bug to be classified as blocking, it must meet these conditions:

  - It prevents a critical business process from being completed.
  - No workaround or mitigation is available for it.

- **Non-blocking** – The upgrade project can proceed. Fix bugs of this type in the upgraded system.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
