---
title: Dual-write setup from Lifecycle Services
description: Learn how to set up a dual-write connection from Microsoft Dynamics 365 Lifecycle Services, including prerequisites and the setup process.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.date: 04/03/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User, IT Pro
ms.search.region: global
ms.search.validFrom: 2020-01-06
---


# Dual-write setup from Lifecycle Services

[!include [banner](../../includes/banner.md)]

This article explains how to enable dual-write from Microsoft Dynamics 365 Lifecycle Services.

## Prerequisites

Complete the Power Platform integration as described in the following topics:

- If you don't yet use Microsoft Power Platform and want to expand your finance and operations environments by adding platform capabilities, see [Connect finance and operations apps with a new Microsoft Dataverse instance](../../power-platform/environment-lifecycle-connect-finops-new-dv.md).
- If you already have Dataverse and Power Platform environments, and want to connect them to finance and operations environments, see [Connect finance and operations apps with an existing Microsoft Dataverse instance](../../power-platform/environment-lifecycle-connect-finops-existing-dv.md).

## Set up dual-write for new or existing Dataverse environments

Follow these steps to set up dual-write from Lifecycle Services **Environment Details** page:

1. On the **Environment Details** page, expand the **Power Platform Integration** section.

1. Select the **Dual-write application** button.

    :::image type="content" source="media/powerplat_integration_step2.png" alt-text="Screenshot of the Power Platform Integration section with the Dual-write application button.".:::

1. Review the terms and conditions, and then select **Configure**.

1. Select **OK** to continue.

1. You can monitor the progress by periodically refreshing the environment details page. Setup typically takes 30 minutes or less.  

1. When the setup is complete, a message informs you if the process was successful or if there was a failure. If the setup failed, the process displays a related error message. You must fix any errors before moving to the next step.

1. Select **Link to Power Platform environment** to create a link between Dataverse and the current environment's databases. It typically takes less than five minutes to create the link.

    :::image type="content" source="media/powerplat_integration_step3.png" alt-text="Link to Power Platform environment.":::

1. When the linking is complete, a hyperlink is displayed. Use the link to sign in to the dual-write administration area in the finance and operations environment. From there, you can set up entity mappings.

## Configure app user for one-box environments

> [!NOTE]
> Power Platform integration for cloud-hosted development environments is deprecated and isn't supported. While the option might still appear during environment deployment, don't use it. 
> For testing and development scenarios, use a Sandbox environment or a Unified Developer Environment (UDE), which are fully supported and better suited for integration with Power Platform.
> For more information about UDE, see [Unified developer experience for finance and operations apps](/power-platform/developer/unified-experience/finance-operations-dev-overview).

## Troubleshooting

### Linking mismatch

Your dual-write environment might be linked to a Dataverse instance while Lifecycle Services isn't set up for Power Platform integration. This linking mismatch can cause unexpected behavior. Make sure that Lifecycle Services environment details match what you're connected to in dual-write so business events, virtual tables, and add-ins can use the same connection.

If your environment has a linking mismatch, Lifecycle Services shows a warning on your environment details page that resembles the following example: "Microsoft detected that your environment is linked via dual-write to a different destination than specified in Power Platform Integration, which isn't recommended."

:::image type="content" source="media/powerplat_integration_mismatchLink.png" alt-text="Power Platform integration link mismatched.":::

If you receive this warning, try one of the following solutions:

- If you never set up your Lifecycle Services environment for Power Platform integration, connect to the Dataverse instance that is configured in dual-write by following the instructions in this article.
- If you already set up your Lifecycle Services environment for Power Platform integration, reset your dual-write connection to the one specified by Lifecycle Services by using the [Reset dual-write connections](/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/reset) action.

Previously, a manual support ticket option was available, but that option was before the introduction of option 1. Microsoft no longer supports manual relinking requests through support tickets.

### Incorrect permissions on service principal

You might receive the following error while linking the finance and operations environment to the Dataverse environment in Lifecycle Services:

| Error code | Error message |
| --- | --- |
| DW9003 | Failed to connect to CRM. Ensure that the service principal has the correct permissions to access CRM.|
| DW9003 | Failed to connect to AX. Ensure that the service principal has the correct permissions to access AX. | 

This error indicates that the application users created for dual-write to access data on the target platforms aren't configured with the appropriate permissions. To resolve this error, ensure the application users are configured correctly by following the guidance in [System requirements and prerequisites](./requirements-and-prerequisites.md).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

