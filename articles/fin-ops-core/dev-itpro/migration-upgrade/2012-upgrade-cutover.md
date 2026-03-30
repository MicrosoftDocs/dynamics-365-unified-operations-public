---
title: Upgrade from AX 2012 - Go live (Cutover)
description: Learn about the final cutover process from Dynamics AX 2012 to the finance and operations app running an upgraded version of your code and database.
author: johnmichalak
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-03-31
ms.dyn365.ops.version: Platform update 12
---

# Upgrade from AX 2012 - Go live (Cutover)

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

After you successfully complete upgrade testing in a Standard or Premier Acceptance Test environment (Sandbox Tier 2 or higher), and you also complete a successful test cutover, you're ready to upgrade your production environment and go live.

> [!NOTE]
> Run the AX 2012 upgrade process on the sandbox environment, not the production environment.

*Cutover* is the term for the final process of getting a new system live. This cutover process consists of the tasks that occur after Microsoft Dynamics AX 2012 is turned off but before finance and operations is turned on. Before you plan your final cutover, you need to successfully complete one successful mock cutover as described in [Cutover testing](./upgrade-cutover-testing.md).

The following illustration shows the overall process for cutover to go-live as it occurs in the production environment.

:::image type="content" source="./media/cutover-selfservice_01.png" alt-text="Screenshot of Cutover process.":::

> [!NOTE]
> In this article, we use the term *sandbox* to refer to a Standard or Premier Acceptance Testing (Tier 2 or 3) or higher environment connected to a SQL Azure database.

## Overall process

The high-level steps of the production environment upgrade process are the same as the mock cutover process. For detailed instructions, see [Upgrade from AX 2012 - Cutover testing (Mock cutover)](./upgrade-cutover-testing.md).


1. Complete the [preupgrade checklist for data upgrade](prepare-data-upgrade.md) and deploy custom code in a sandbox environment. Use the sandbox environment only for data upgrade.
1. Download the **AX 2012 Database Upgrade Toolkit for Dynamics 365** from Microsoft Dynamics Lifecycle Services in the **Shared asset library > Model** area. Use this toolkit from the source SQL Server.
1. Execute replication setup and monitor it regularly by using the toolkit.
1. Turn off the AX 2012 AOS instances at the time of downtime or cutover.
1. Ensure replication completes. Validate replication completion by comparing the number of records between source and target by using this toolkit. For more information about how to validate the replication, see [Reporting section of the application](data-upgrade-self-service.md#reporting-section-of-the-application).
1. Execute cutover steps by using the toolkit and ensure its completion.
1. Trigger the data upgrade by using the toolkit and finish the data upgrade.
1. Use [Self-service database refresh process](../database/database-refresh.md#self-service-database-refresh) to copy your upgraded database from the sandbox environment into your production environment. 
1. Complete application configuration and complete smoke test.
1. Allow users to access the finance and operations app again.


## Prerequisites 
Before you can perform an upgrade in the production environment, complete the following prerequisites:
-	Complete the code upgrade and data upgrade in a sandbox environment and successfully complete a functional test pass.
-	Deploy the production environment. Before you can request the deployment of the production environment, you must complete:
    - The Subscription estimator in Lifecycle Services. We use this tool to help us size your production environment because it provides details of the throughput you require.
    - The Test phase of the methodology in Lifecycle Services. This phase helps ensure that you're at the stage in your project where you're ready to start testing in the production environment.
    - After you submit a request to Microsoft to deploy the production environment, it takes roughly 24 hours to deploy, so ensure that you leave enough time for this step.
-	Apply all necessary updates and customizations (AOT deployable packages) to the production environment. Don't make any code changes after signing off on a mock cutover.


## Additional resources
- [Onboarding](../../fin-ops/imp-lifecycle/onboard.md)
- [Self-service database refresh](../database/database-refresh.md#self-service-database-refresh)
- [Upgrade from AX 2012 - Cutover testing (Mock cutover)](./upgrade-cutover-testing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

