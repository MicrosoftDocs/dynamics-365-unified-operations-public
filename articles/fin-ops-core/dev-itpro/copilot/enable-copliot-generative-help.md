---
title: Enable generative help and guidance with Copilot
description: This article describes how administrators can enable and troubleshoot generative help and guidance with Copilot in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 08/28/2024
audience: Application User
ms.custom: 
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# Enable generative help and guidance with Copilot

[!include [banner](../includes/banner.md)]

Microsoft Copilot provides in-app help and guidance that uses the power of generative AI to give contextual support to users. Copilot accesses the full range of public documentation to offer precise assistance and streamline navigation through the extensive capabilities of Dynamics 365 finance and operations apps.

This Copilot capability is a conversational experience powered by a Microsoft Copilot Studio bot that's deployed into the Dataverse environment associated with your Microsoft finance and operations apps environment.  

This article describes availability and explains how to enable generative help and guidance with Copilot.

After you complete the steps in this article, the Copilot icon appears at the top of all finance and operations apps. Users can then select the Copilot icon to access generative help and guidance.

## Enable the feature

In most cases, generative help and guidance with Copilot is available by default if [Power Platform Integration](../power-platform/enable-power-platform-integration.md) is enabled for your environment.

If the feature isn't already available on your system, refer to [Enable Copilot capabilities in finance and operations apps](enable-copilot.md) for information about how to enable it.

<!-- KFM: Remove for now

## <a name="follow-ups"></a>Enable follow-up questions in the Copilot sidecar (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]

The *[Follow-up questions in the Copilot sidecar](../../fin-ops/copilot/faq-copilot-suggested-questions.md)* feature makes it fast and easy to post follow-up questions and get answers from Copilot. It's designed to provide a diversity of follow-up questions, and avoids repeating questions you have already asked. The suggested questions are answered using [Generative Answers](/microsoft-copilot-studio/faqs-generative-answers), which is the foundation for the Generative help and guidance with Copilot feature in finance and operation apps.

To use this capability in your environment, your system must meet the following requirements:

- You must be running finance and operations apps version 10.0.42 or later.
- The feature that is named *(Preview) Follow-up questions in the Copilot sidecar* must be turned on in [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

 -->

## Add custom knowledge

You can add custom knowledge sources and/or enable general knowledge for generative help and guidance with Copilot. For more information and instructions, see [Add knowledge to generative help and guidance with Copilot](extend-copilot-generative-help.md).

## Troubleshooting

Specific conditions [govern and secure the deployment of Copilot Studio components and the way that generative AI features can be used in your organization](/microsoft-copilot-studio/security-and-governance). These conditions determine whether Copilot can be enabled in your organization.

Here are some typical causes that can prevent Copilot from being deployed and enabled in finance and operations apps:

- In the Power Platform admin center, your tenant admin disabled the ability to publish copilots with generative answers and actions for your tenant. This ability is governed by the **Publish Copilots with AI features** [tenant setting](/microsoft-copilot-studio/security-and-governance).
- [Data movement across geographic locations](/microsoft-copilot-studio/manage-data-movement-outside-us) has been disabled for Copilot Studio generative AI features outside the United States.
- Your admin disabled the use of Copilot for your organization through a support request.

After a governing condition is addressed, you might have to take additional action. Here are some examples:

- Trigger the deployment of the Copilot application in the Dataverse environment. In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/applications), on the left navigation, select **Resources** \> **Dynamics 365 apps**. Select the *Copilot for finance and operations apps* application, select **Install**, and then select the Dataverse environment.
- Republish the Copilot Studio chatbot in Copilot Studio. In the [Power Apps maker experience](https://make.powerapps.com/), select the Dataverse environment, and then, on the left navigation, select **More** \> **Chatbots**. Open the *Copilot for finance and operations apps* chatbot, select **Publish** on the left navigation, and then select **Publish**.
- In your finance and operations app, you might have to refresh the browser before you can use Copilot.

## Disabling the conversational Copilot sidecar for your organization

If you want to disable the conversational Copilot sidecar for your organization, you can do so by doing any or all of the following steps:

- If you're running finance and operations apps version 10.0.38 or 10.0.39, you can turn off the conversational Copilot sidecar in finance and operations apps by going to the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace and disabling the feature *User experience for Copilot in Finance and Operations*. The feature is on by default and mandatory in finance and operations apps versions 10.0.40 and higher.
- Turn off Bing Search for all copilots and generative AI features in your environment. For instructions, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot).
- Turn off Copilot for all Power Apps applications in your environment. For instructions, see [Copilot in Power Apps overview](/power-apps/maker/canvas-apps/ai-overview).

## See also

- [Add custom knowledge to generative help and guidance with Copilot](extend-copilot-generative-help.md)
- [Responsible AI FAQ for Generative help and guidance with Copilot in finance and operations apps](../../fin-ops/copilot/faq-copilot-generative-help.md)

<!-- KFM: Remove for now
- [Responsible AI FAQ for Follow-up questions in the Copilot sidecar (preview)](../../fin-ops/copilot/faq-copilot-suggested-questions.md)
-->