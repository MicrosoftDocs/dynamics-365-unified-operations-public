---
# required metadata

title: Upgrade from AX 2012 - Go live (Cutover)
description: This topic explains the final cutover process that starts after you turn off Dynamics AX 2012 and completes with Finance and Operations running an upgraded version of your code and database.
author: jorisdg
manager: AnnBe
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata
# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2018-03-31
ms.dyn365.ops.version: Platform update 12
---

# Upgrade from AX 2012 - Go live (Cutover)

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

After you have successfully completed upgrade testing in a Standard or Premier Acceptance Test environment (Sandbox Tier 2 or higher), and you have also completed a successful test cutover, the time has arrived to upgrade your production environment and go live.

*Cutover* is the term that we use for the final process of getting a new system live. This cutover process consists of the tasks that occur after Microsoft Dynamics AX 2012 is turned off but before Finance and Operations is turned on. Before you plan your final cutover, you need to successfully complete one successful mock cutover as described in [Cutover testing](./upgrade-cutover-testing.md)

The following illustration shows the overall process for cutover to go-live as it will occur in the production environment.

![Cutover process](./media/cutover_1.png)

> [!NOTE]
> In this topic, we use the term *sandbox* to refer to a Standard or Premier Acceptance Testing (Tier 2 or 3) or higher environment connected to a SQL Azure database.

## Overall process

The high-level steps of the production environment upgrade process are the same as the Mock cutover process, refer to [Upgrade from AX 2012 - Cutover testing (Mock cutover)](./upgrade-cutover-testing.md) for detailed instructions.


1. Turn off the AX 2012 AOS instances
2. Create a copy of the AX 2012 database. We strongly recommend that you use a copy, because you must delete some objects in the copy that will be exported.
3. Export the copied database to a bacpac file by using a free SQL Server tool that is named SQLPackage.exe. This tool provides a special type of database backup that can be imported into SQL Database.
4. Upload the bacpac file to Azure storage.
5. Download the bacpac file to the Application Object Server (AOS) machine in the sandbox environment, and then import it by using SQLPackage.exe. You must then run a script against the imported database to reset the SQL database users.
6. Run the appropriate data upgrade package against the imported database.

## Prerequisites 
Before you can perform an upgrade in the production environment the following prerequisites must be met:
-	Complete the code upgrade and data upgrade in a sandbox environment and successfully completed a functional test pass
-	Deploy the production environment. Before the option to request the deployment of the production environment lights up you must have completed:
    - The Subscription estimator in LCS. We use this to help us size your production environment because it provides details of the throughput you’ll require.
    - The Test phase of the methodology in LCS. This is to help ensure that you’re at the stage in your project where you’re ready to start testing in the production environment.
    - After a request is submitted to Microsoft to deploy the production environment, it will take roughly 24 hours to deploy, so ensure that you leave enough time for this to happen.
-	Apply all necessary updates and customizations (AOT deployable packages) to the production environment. There should not be any code change after signing off on a Mock cutover.
-	To schedule an upgrade, request a timeslot with the DSE team by submitting “Other” type service requests from LCS as described in the [Upgrade from AX 2012 - Cutover testing (Mock cutover)](./upgrade-cutover-testing.md). This is to ensure that the preferred timeslots will be available for you. Be aware that there is significantly higher demand for slots during the weekend, so requesting these as far in advance as possible will help attain your preferred schedule.

## Related articles
- [Onboarding](../../fin-ops/imp-lifecycle/onboard.md)
- [Submit service requests to the Dynamics Service Engineering team](../lifecycle-services/submit-request-dynamics-service-engineering-team.md).
- [Upgrade from AX 2012 - Cutover testing (Mock cutover)](./upgrade-cutover-testing.md)
