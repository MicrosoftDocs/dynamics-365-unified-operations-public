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

Copilot provides in-app help and guidance that uses the power of generative AI to give contextual support to users. Copilot accesses the full range of public documentation to offer precise assistance and streamline the navigation through the extensive capabilities of finance and operations apps.

This article describes availability and how to enable generative help and guidance with Copilot.

When you have completed the steps described in this article, the Copilot icon will be displayed at the top of all Microsoft finance and operations applications and users can use it to access generative help and guidance.

> [!NOTE]
> If the Copilot capabilities described in this article aren't turned off for the Dataverse environment or at the tenant level, and the Copilot bot has been successfully deployed and published, then you can open the Copilot sidecar using the Copilot icon in the page header.

## Prerequisites

To enable generative help and guidance with Copilot in finance and operations apps, you must have the following prerequisites in place:

- You must be running version 10.0.38 or later of finance and operations apps.
- Starting with 10.0.40, and PQUs for 10.0.39 and 10.0.38, the required Copilot solutions are deployed automatically into the Dataverse environment associated with the organization where you are running finance and operations apps.

## Country/region and language availability

For information about which countries/regions and languages the Copilot capability in Microsoft Dynamics 365 Supply Chain Management is available for, see the [Copilot international availability guide](https://dynamics.microsoft.com/availability-reports/copilotreport/).

## Step 1: Connect your finance and operations apps to a Dataverse environment

The subscription for your finance and operations apps includes an initial Dataverse environment, which is deployed into your Tenant. Your finance and operations apps environment must be associated with a Dataverse environment to support Copilots. Typically, this is done automatically, but in some situations, the tenant or environment admin must enable the association.

Confirm that [Power Platform integration is enabled](../power-platform/enable-power-platform-integration.md) in [Microsoft Dynamics Lifecycle Services](../lifecycle-services/lcs-user-guide.md). You don't have to enable dual-write for this feature.

## Step 2: Turn on copilot and generative AI features

> [!NOTE]
> Copilots and generative AI features that are generally available are turned on by default.
>
> If you have to turn on on any of the features from this section in your environment, you might also need to redeploy the copilot application and publish the bot in Copilot Studio.

Depending on the availability of Copilot and generative AI back-office services in your region, you might need to take steps to [turn on copilots and generative AI features](/power-platform/admin/geographical-availability-copilot) in your Dataverse environment. You need to do these steps in the Dataverse environment that is connected to the enviornment where  you are running your finance and operations apps.  

### Allow cross-region data movement for your Dataverse environment

Depending on the availability of Copilot and generative AI back-office services in your region, your Dataverse environment might need to be enabled for cross-region data movement. For more information, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot).

> [!WARNING]
> If cross-region data movement is required but not enabled, then the deployment of the Copilot solution will fail, or the Copilot sidecar won't be available to users or won't provide answers, depending on the situation.

It the **Move data across regions** checkbox is available bu not selected, then review the terms of use and select it.

For information about the capabilities and limitations of AI-powered Copilot features in Microsoft finance and operations apps, see [Responsible AI FAQs for the Microsoft Dynamics 365 finance and operations platform](../responsible-ai/responsible-ai-overview.md).

### Make sure that Bing Search is enabled for your Dataverse environment

*Generative help and guidance* is based on [generative answers in Copilot Studio](/microsoft-copilot-studio/nlu-boost-conversations), which uses Bing Search to identify relevant articles from the public documentation and then composes the answers provided by Copilot.

> [!WARNING]
> If Bing Search is disabled then the deployment of the Copilot solution will fail, or the Copilot sidecar cannot be opened by users or it will not provide answers, depending on the situation.

If the **Bing Search** checkbox isn't selected, then review the terms of use and select it.

### Make sure Copilot bots can be used in your tenant

Tenant admins can disable the ability to publish copilots for your tenant in the Power Platform admin center.

> [!WARNING]
> If the option **Publish bots with AI features** is disabled, then you won't be able to deploy the Copilot solution.

Confirm that **Publish bots with AI features** is enabled. If not, then review the terms of use and enable it.

## Step 3: Enable the feature in the Feature management workspace

Do one of the following steps, depending on which version of Microsoft finance and operations apps you're running:

- For environments on version 10.0.40, the ability to show the sidecar user experience for Copilot in finance and operations apps is always enabled.
- For environments on versions 10.0.38 and 10.0.39, turn on the feature with name *User experience for Copilot in Finance and Operations* in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Troubleshooting

Whether Copilot can be enabled in your organization depends on conditions that [govern and secure the deployment of Copilot Studio components and how using generative AI features may be used in your organization](/microsoft-copilot-studio/security-and-governance).

Typical causes that could prevent Copilot from being deployed and enabled in finance and operations apps include:
  
- The ability to publish copilots with generative answers and actions for your tenant has been disabled by the admin in the Power Platform admin center. This is governed by the [Tenant setting](/microsoft-copilot-studio/security-and-governance) **Publish bots with AI features**.
- [Data movement across geographic locations](/microsoft-copilot-studio/manage-data-movement-outside-us) for Copilot Studio generative AI features outside the United States has been disabled.
- The use of Copilot has been disabled for your organization by your admin through a support request.

Once a governing condition has been resolved, it might be necessary to take additional steps, such as:

- Trigger the deployment of the Copilot application into the Dataverse environment. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/applications), navigate to **Resources/Dynamics 365 apps**, identify the application *Copilot for finance and operations apps*, choose **Install**, and select the Dataverse environment.  
- Republish the Copilot Studio chatbot in Copilot Studio. Open the [PowerApps maker experience](https://make.powerapps.com/), select the Dataverse environment and choose **Chatbots** from the left side navigation pane under **...More**. Open the chatbot *Copilot for finance and operations apps*, select **Publish** from the left side navigation, and select **Publish**.
- In your finance and operations app, you might need to refresh the browser before the Copilot can be used.  
