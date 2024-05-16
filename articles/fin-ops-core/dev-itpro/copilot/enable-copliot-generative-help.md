---
title: Enable generative help and guidance with Copilot
description: This article describes how administrators can enable generative help and guidance with Copilot in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 04/19/2024
audience: Application User
ms.custom: 
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# Enable generative help and guidance with Copilot

[!include [banner](../includes/banner.md)]

Microsoft Copilot provides in-app help and guidance that uses the power of generative AI to give contextual support to users. Copilot accesses the full range of public documentation to offer precise assistance and streamline navigation through the extensive capabilities of Dynamics 365 finance and operations apps.

This article describes availability and explains how to enable generative help and guidance with Copilot.

After you complete the steps in this article, the Copilot icon appears at the top of all finance and operations apps. Users can then select the Copilot icon to access generative help and guidance.

> [!NOTE]
> Unless the Copilot capabilities that this article describes are turned off for the Dataverse environment or at the tenant level, you can use the Copilot icon to open the Copilot sidecar after the Copilot bot is successfully deployed and published.

## Prerequisites

To enable generative help and guidance with Copilot in finance and operations apps, you must be running version 10.0.38 or later of finance and operations apps.

> [!NOTE]
> As of version 10.0.40, and in proactive quality updates (PQUs) for versions 10.0.39 and 10.0.38, the required Copilot solutions are automatically deployed in the Dataverse environment that's associated with the organization where you're running finance and operations apps.

## Country/region and language availability

For information about which countries/regions and languages the Copilot capability in Dynamics 365 Supply Chain Management is available for, see the [Copilot international availability guide](https://dynamics.microsoft.com/availability-reports/copilotreport/).

## Step 1: Connect your finance and operations apps to a Dataverse environment

The subscription for your finance and operations apps includes an initial Dataverse environment that's deployed in your tenant. To support copilots, your finance and operations apps environment must be associated with a Dataverse environment. Typically, this association is automatically enabled. However, in some situations, the tenant or environment admin must enable it.

Confirm that [Power Platform Integration is enabled](../power-platform/enable-power-platform-integration.md) in [Microsoft Dynamics Lifecycle Services](../lifecycle-services/lcs-user-guide.md). You don't have to enable dual-write for this feature.

## Step 2: Turn on copilots and generative AI features

> [!NOTE]
> Copilots and generative AI features that are generally available are turned on by default.
>
> If you have to turn on any of the features from this section in your environment, you might also have to redeploy the Copilot application and publish the Copilot bot in Copilot Studio.

Depending on the availability of Copilot and generative AI back-office services in your region, you might have to [turn on copilots and generative AI features](/power-platform/admin/geographical-availability-copilot) in your Dataverse environment. You must complete the steps in the Dataverse environment that's connected to the environment where you're running your finance and operations apps.

### Allow cross-region data movement for your Dataverse environment

Depending on the availability of Copilot and generative AI back-office services in your region, you might have to enable your Dataverse environment for cross-region data movement. For more information, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot).

> [!IMPORTANT]
> If cross-region data movement is required, but it's disabled, deployment of the Copilot solution will fail, users won't be able to open the Copilot sidecar, or the Copilot sidecar won't provide answers, depending on the situation.

If the **Move data across regions** checkbox is available, but it's cleared, review the terms of use, and then select the checkbox.

For information about the capabilities and limitations of AI-powered Copilot features in finance and operations apps, see [Responsible AI FAQs for the Microsoft Dynamics 365 finance and operations platform](../responsible-ai/responsible-ai-overview.md).

### Make sure that Bing Search is enabled for your Dataverse environment

Generative help and guidance is based on [generative answers in Copilot Studio](/microsoft-copilot-studio/nlu-boost-conversations). The generative answers feature uses Bing Search to identify relevant articles from the public documentation. It then composes the answers that Copilot provides.

> [!IMPORTANT]
> If Bing Search is disabled, deployment of the Copilot solution will fail, users won't be able to open the Copilot sidecar, or the Copilot sidecar won't provide answers, depending on the situation.

If the **Bing Search** checkbox is cleared, review the terms of use, and then select the checkbox.

### Make sure that Copilot bots can be used in your tenant

In the Power Platform admin center, tenant admins can disable the ability to publish copilots for your tenant.

> [!IMPORTANT]
> If the **Publish bots with AI features** option is disabled, you can't deploy the Copilot solution.

If the **Publish bots with AI features** option is disabled, review the terms of use, and then enable the option.

## Step 3: Enable the feature in the Feature management workspace

Follow one of these steps, depending on the version of finance and operations apps that you're running:

- For environments on version 10.0.40, the ability to show the sidecar user experience for Copilot in finance and operations apps is always enabled.
- For environments on versions 10.0.38 and 10.0.39, turn on the *User experience for Copilot in Finance and Operations* feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Troubleshooting

Specific conditions [govern and secure the deployment of Copilot Studio components and the way that generative AI features can be used in your organization](/microsoft-copilot-studio/security-and-governance). These conditions determine whether Copilot can be enabled in your organization.

Here are some typical causes that can prevent Copilot from being deployed and enabled in finance and operations apps:

- In the Power Platform admin center, your tenant admin disabled the ability to publish copilots with generative answers and actions for your tenant. This ability is governed by the **Publish bots with AI features** [tenant setting](/microsoft-copilot-studio/security-and-governance).
- [Data movement across geographic locations](/microsoft-copilot-studio/manage-data-movement-outside-us) has been disabled for Copilot Studio generative AI features outside the United States.
- Your admin disabled the use of Copilot for your organization through a support request.

After a governing condition is addressed, you might have to take additional action. Here are some examples:

- Trigger the deployment of the Copilot application in the Dataverse environment. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/applications), on the left navigation, select **Resources** \> **Dynamics 365 apps**. Select the *Copilot for finance and operations apps* application, select **Install**, and then select the Dataverse environment.
- Republish the Copilot Studio chatbot in Copilot Studio. In the [Power Apps maker experience](https://make.powerapps.com/), select the Dataverse environment, and then, on the left navigation, select **More** \> **Chatbots**. Open the *Copilot for finance and operations apps* chatbot, select **Publish** on the left navigation, and then select **Publish**.
- In your finance and operations app, you might have to refresh the browser before you can use Copilot.
