---
title: Enable Copilot capabilities in finance and operations apps
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

# Enable Copilot capabilities in finance and operations apps

This article describes how Copilot capabilities in finance and operations apps are constructed, how to enable or disable these capabilities, and how to troubleshoot them.

## Copilot architecture in finance and operations apps

Copilot in finance and operations apps is built from user experience components, application code, and AI services such as large language models (LLMs) hosted on Azure and connected through Dataverse (provided through Power Platform integration).

Finance and operations supports two fundamental types of Copilot features:

- **Side car features** – Open in a pane at the right side of the page, and provide natural-language chat features such as [Generative help and guidance with Copilot](../../fin-ops/copilot/copliot-generative-help.md).
- **Summary and content-generation features** – Are embedded in relevant parts of each application to provide summaries and other relevant information. These features include the [Confirmed purchase orders with changes workspace](../../../supply-chain/procurement/purchase-order-changes-after-confirmation.md) and various [Copilot summaries](../../../supply-chain/get-started/copilot-summaries-overview.md).

The following illustration shows the components needed to use Copilot summary and content-generation features in finance and operations apps.

:::image type="content" source="media/copilot-summaries-components.svg" alt-text="Components needed to use Copilot summary features" lightbox="media/copilot-summaries-components.svg":::

The following illustration shows the components needed to use Copilot side car features in finance and operations apps.

:::image type="content" source="media/copilot-sidecar-components.svg" alt-text="Components needed to use Copilot sidecar features" lightbox="media/copilot-sidecar-components.svg":::

All Copilot features require Power Platform integration and are supported only for cloud-hosted environments.

## Regional requirements

Each Copilot feature may be limited to only certain data regions and languages. The region and language support is continuously growing to global availability. Go here to lookup the latest availability information per Copilot feature: [Copilot international availability guide](https://dynamics.microsoft.com/availability-reports/copilotreport/).

## Power Platform requirements

To use Copilot features in finance and operations apps, [Power Platform integration](../power-platform/enable-power-platform-integration.md) must be enabled in Microsoft Dynamics Lifecycle Services. (You don't have to enable dual-write if you don't use it.)

If you have Power Platform integration enabled, all of the required Copilot features are usually deployed to your environment automatically. If the features aren't working for you as expected, review the following subsections for information that may help you troubleshoot any issues.

### Confirm that the required Dynamics 365 apps are installed

The following table lists the Dynamics 365 apps that must be present in your Power Platform environment in order to use each Copilot feature.

|  Copilot feature  | Required Dynamics 365 app |
|---|---|
| Generative help and guidance and the bot for the Copilot side car | `Copilot for finance and operations apps` |
| Copilot summaries in Supply Chain Management and Copilot summaries in Commerce | `Copilot in Dynamics 365 Supply Chain Management` |
| Copilot summaries in Finance | `Copilot in Dynamics 365 Finance` |

Usually, all of the required apps will already be installed for your environment, but if you have only recently enabled the Power Platform integration for your environment, the apps might not yet be installed. To check for and install the required apps, follow these steps:

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select your environment to open its detailed view.
1. In the detailed view (not in the navigator), under Resources, select **Dynamics 365 apps**.
1. Check to make sure each of the apps you require (as listed in the table at the start of this section) is shown as installed. If not, select **Install app** from the toolbar and install each required app, following the instructions on your screen.

### Additional requirements for using Copilot side car features

The Copilot side car uses conversational bots and Generative Answers from Copilot Studio.

Generative answers required Bing Search and, depending on the availability these back-office services in your region, your Dataverse environment might also have to be set up to support cross-region calls. For more information, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot).

You don't have to set up support for cross-region calls if the required AI services are already available in your Dataverse region.

If Bing Search is disabled, or if cross-region data movement is required but is disabled, users won't be able to open the Copilot sidecar, or the Copilot sidecar won't provide answers, depending on the situation.

### Confirm that your Power Platform environment can publish bots with AI features

The tenant-level setting that permits deployment of bots in Dataverse environments is enabled by default, but it can be disabled by a tenant admin. If this setting is disabled, you won't be able to use Copilot features in finance and operations apps.

To check and enable Power Platform to publish bots with AI features, follow these steps.

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the navigation pane, select **Settings**.
1. In the list, select the row where the **Name** is *Publish bots with AI features*.
1. The **Publish bots with AI features** dialog opens. Set the slider to **Enabled**.
1. Select **Save**.

## Feature-specific installations

As mentioned previously, most Copilot features in finance and operations apps require that your environment has Power Platform integration enabled and also meets the other requirements outlined in this article. For some features, this foundation is all that's needed, but other features may require additional installations and/or feature management. The following table lists each Copilot feature and gives links to articles that describe how to enable them.

| Application | Feature | Required installation and setup |
|---|---|---|
| All finance and operations apps | Basic Copilot support | No additional requirements. |
| All finance and operations apps | Generative help and guidance with Copilot | [Enable generative help and guidance with Copilot](enable-copliot-generative-help.md) |
| Dynamics 365 Commerce | Use Copilot in site builder to enrich product detail pages | [Enable Copilot in site builder](../../../commerce/copilot-site-builder.md) |
| Dynamics 365 Finance | Collections coordinator summary | [Enable collections coordinator summary](../../../finance/accounts-receivable/CollectionsCoordinatorSummary.md) |
| Dynamics 365 Finance | Customer page summary | [Enable customer page summary](../../../finance/accounts-receivable/CustomerPageSummary.md) |
| Dynamics 365 Finance | Workflow history summary | [Enable workflow history summary](../../fin-ops/organization-administration/workflow-history-summary.md) |
| Dynamics 365 Supply Chain Management | AI summaries with Copilot | [Enable AI summaries with Copilot](../../../supply-chain/get-started/copilot-summaries-overview.md) |
| Dynamics 365 Supply Chain Management | [Analyze demand plans with Copilot](../../../supply-chain/demand-planning/demand-planning-copilot.md) | Installed and enabled by default in Demand planning version 1.0.0.1067 or newer. |
| Dynamics 365 Supply Chain Management | [Inquire into inventory with Copilot](../../../supply-chain/inventory/inventory-visibility-copilot-api.md) | Installed and enabled by default in Inventory Visibility version 1.2.2.127 or newer. |
| Dynamics 365 Supply Chain Management | Review and accept changes to confirmed purchase orders | [Enable Copilot support for managing changes to confirmed purchase orders](purchase-order-changes-after-confirmation-enable.md) |

## Responsible AI FAQs

For information about the capabilities and limitations of AI-powered Copilot features in Microsoft finance and operations apps, see [Responsible AI FAQs for the Microsoft Dynamics 365 finance and operations platform](../responsible-ai/responsible-ai-overview.md).
