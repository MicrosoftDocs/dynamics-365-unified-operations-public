---
title: Copilot prerequisites
description: Learn about instructions for administrators on how to enable basic Copilot capabilities in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.date: 02/16/2024
ms.custom:
 - bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

[!include [banner](../includes/banner.md)]

# What is behind Copilot and what you need to enable it

This article describes how Copilot capabilities in finance and operations apps are constructed to provide an understanding of this basic foundation. This understanding helps to answer question on how to enable or disable Copilot capabilities and troubleshoot.

Copilot in Finance and operations is built from user experience components, application code, and AI services such as Large Language Models (LLM) hosted on Azure and connected through Data Verse provided through Power Platform integration.

Finance and operations supports two fundamental types of Copilot.

- Copilot side car features, such as Generative Help and Guidance
- Summarization and content generation features with Copilot, such as can be found in the Confirmed Purchase Orders With changes workspace, or various summarizations throughout the applications.



All of these require Power Platform integration and are supported only for cloud-hosted environments. Each Copilot feature may be limited to only certain data regions and languages. The region and language support is continuously growing to global availability. Go here to lookup the latest availability information per Copilot feature: [Copilot international availability guide](https://dynamics.microsoft.com/availability-reports/copilotreport/).

## Power Platform requirements

You must have enabled the [Power Platform integration](../power-platform/enable-power-platform-integration.md) in Microsoft Dynamics Lifecycle Services. (However, you don't have to enable dual-write for this feature.)

If you have Power Platform integration enabled the deployment of Copilot features will happen automatically.

The following solutions for respective Copilot features must be present in the Power Platform environment.

|Copilot package | Solution name prefix | Copilot feature  |
|---------|---------|---------|
|Copilot for finance and operations apps | msdyn_FnoCopilot...  | Generative help and guidance and the bot for the Copilot side car |
|Copilot in Supply Chain Management | msdyn_SCMAIApp...    | Copilot Summarization in Supply Chain Management |
|Finance AI Solution | msdyn_FinanceAIApp... | Copilot Summarization in Finance |
|Commerce AI Solution | TBD | Copilot Summarization in Commerce |

### Additional requirements for using Copilot side car features

The Copilot side car uses conversational bots and Generative Answers from Copilot Studio.

Depending on the availability these back-office services in your region, your Dataverse environment might also have to be set up to support cross-region calls. For more information, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot).

You don't have to set up support for cross-region calls if the required AI services are already available in your Dataverse region.

### Check that your Power Platform to publish bots with AI features

The Tenant level setting that permits deployment of bots in Dataverse environments is enabled by default. 

To check and enable Power Platform to publish bots with AI features, follow these steps.

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the navigation pane, select **Settings**.
1. In the list, select the row where the **Name** is *Publish bots with AI features*.
1. The **Publish bots with AI features** dialog opens. Set the slider to **Enabled**.
1. Select **Save**.

## Further Copilot installation information
Detailed information for individual Copilot features that may require additional installations and/or feature management (see also [Overview of enabling Copilot capabilities and features](enable-copilot-overview.md)).


## Responsible AI FAQ
For information about the capabilities and limitations of AI-powered Copilot features in Microsoft finance and operations apps, see [Responsible AI FAQs for the Microsoft Dynamics 365 finance and operations platform](../responsible-ai/responsible-ai-overview.md).
