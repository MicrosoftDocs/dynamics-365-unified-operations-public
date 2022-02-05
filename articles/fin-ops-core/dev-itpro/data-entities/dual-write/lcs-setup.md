---
title: Dual-write setup from Lifecycle Services
description: This topic explains how to set up a dual-write connection from Microsoft Dynamics Lifecycle Services (LCS).
author: laneswenka
ms.date: 08/03/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-06
---

# Dual-write setup from Lifecycle Services

[!include [banner](../../includes/banner.md)]



This topic explains how to enable dual-write from Microsoft Dynamics Lifecycle Services (LCS).

## Prerequisites

You must complete the Power Platform integration as described in the following topics:

+ [Power Platform Integration - Enable during environment deployment](../../power-platform/enable-power-platform-integration.md#enable-during-deploy)
+ [Power Platform integration - Enable after environment deployment](../../power-platform/enable-power-platform-integration.md#enable-after-deploy)

## Set up dual-write for new Dataverse environments

Follow these steps to set up dual-write from LCS **Environment Details** page:

1. On the **Environment Details** page, expand the **Power Platform Integration** section.

2. Select the **Dual-write application** button.

    ![Power Platform Integration.](media/powerplat_integration_step2.png)

3. Review the terms and conditions, and then select **Configure**.

4. Select **OK** to continue.

5. You can monitor the progress by periodically refreshing the environment details page. Setup typically takes 30 minutes or less.  

6. When the setup is complete, a message will inform you if the process was successful or if there was a failure. If the setup failed, then a related error message is displayed. You must fix any errors before moving to the next step.

7. Select **Link to Power Platform environment** to create a link between Dataverse and the current environment's databases. This typically takes less than 5 minutes.

    :::image type="content" source="media/powerplat_integration_step3.png" alt-text="Link to Power Platform environment.":::

8. When the linking is complete, a hyperlink is displayed. Use the link to sign in to the dual-write administration area in the Finance and Operations environment. From there, you can set up entity mappings.

## Set up dual-write for an existing Dataverse environment

To set up dual-write for an existing Dataverse environment, you must create a Microsoft [support ticket](../../lifecycle-services/lcs-support.md). The ticket must include:

+ Your Finance and Operations environment ID.
+ Your environment name from Lifecycle Services.
+ The Dataverse organization ID or Power Platform Environment ID from Power Platform Admin Center. In your ticket, request that the ID be the instance used for Power Platform integration.

> [!NOTE]
> You can't unlink environments by using LCS. To unlink an environment, open the **Data integration** workspace in the Finance and Operations environment, and then select **Unlink**.

## Linking mismatch

It is possible that your LCS environment is linked to one Dataverse instance, while your dual-write environment is linked to another Dataverse instance. This linking mismatch can cause unexpected behavior, and it could end up sending data to the wrong environment. The recommended environment to use for dual-write is the one that is created as part of Power Platform integration, and long term, this will be the only way to establish a link between environments.

If your environment has a linking mismatch, LCS displays a warning on your environment details page similar to "Microsoft has detected that your environment is linked via Dual-write to a different destination than specified in Power Platform Integration, which is not recommended":

:::image type="content" source="media/powerplat_integration_mismatchLink.png" alt-text="Power Platform integration link mismatched.":::

If you encounter this error there are two options, based on your needs:

+ [Unlink and relink dual-write environments (Reset or change linking)](relink-environments.md#scenario-reset-or-change-linking) as specified on your LCS environment details page. This is the ideal option, because you can run it without Microsoft support.  
+ If you want to keep your link in dual-write, you can ask for help from Microsoft Support to change the Power Platform integration to use your existing Dataverse environment as documented in the previous section.  

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
