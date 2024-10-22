---
title: Enable Copilot capabilities in finance and operations apps
description: Learn how administrators can enable basic Copilot capabilities in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.date: 07/05/2024
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

This article describes how Microsoft Copilot capabilities in finance and operations apps are constructed, how to enable or disable these capabilities, and how to troubleshoot them.

## Copilot architecture in finance and operations apps

Copilot in finance and operations apps is built from the following components:

- User experience (UX) components
- Application code
- AI services such as large language models (LLMs) that are hosted on Azure and connected through Dataverse (The Dataverse connection is provided through Power Platform Integration.)

Finance and operations apps support two fundamental types of Copilot features:

- **Sidecar features** – These features are opened in a pane on the right side of the page. They provide natural-language chat features such as [generative help and guidance with Copilot](../../fin-ops/copilot/copliot-generative-help.md).
- **Summary and content-generation features** – These features are embedded in relevant parts of each application and provide summaries and other relevant information. They include the [Confirmed purchase orders with changes workspace](../../../supply-chain/procurement/purchase-order-changes-after-confirmation.md) and various [Copilot summaries](../../../supply-chain/get-started/copilot-summaries-overview.md).

The following illustration shows the components that are needed to use Copilot sidecar features in finance and operations apps.

:::image type="content" source="media/copilot-sidecar-components.svg" alt-text="Diagram that shows the components needed to use Copilot sidecar features." lightbox="media/copilot-sidecar-components.svg":::

The following illustration shows the components that are needed to use Copilot summary and content generation features in finance and operations apps.

:::image type="content" source="media/copilot-summaries-components.svg" alt-text="Diagram that shows the components needed to use Copilot summary features." lightbox="media/copilot-summaries-components.svg":::

## Regional requirements

Some Copilot features are limited to specific data regions and languages. Region and language support is continuously growing toward global availability. For the latest availability information for each Copilot feature, see the [Copilot international availability guide](https://dynamics.microsoft.com/availability-reports/copilotreport/).

## Microsoft Power Platform requirements

To use Copilot features in finance and operations apps, [Power Platform Integration](../power-platform/enable-power-platform-integration.md) must be enabled in Microsoft Dynamics Lifecycle Services. (You don't have to enable dual-write if you don't use it.)

Usually, if Power Platform Integration is enabled, all the required Copilot features are automatically deployed to your environment. If the features don't work as expected, the information in the following subsections might help you troubleshoot any issues.

### Confirm that the required Dynamics 365 apps are installed

The following table lists the Dynamics 365 apps that must be present in your Power Platform environment before you can use each Copilot feature.

| Copilot feature | Required Dynamics 365 app |
|---|---|
| Generative help and guidance and the bot for the Copilot sidecar | Copilot for finance and operations apps |
| Copilot summaries in Supply Chain Management and Copilot summaries in Commerce | Copilot in Dynamics 365 Supply Chain Management |
| Copilot summaries in Finance | Copilot in Dynamics 365 Finance |

Usually, all the required apps are already installed in your environment. However, if you only recently enabled Power Platform Integration for your environment, the apps might not yet be installed. To check for and install the required apps, follow these steps.

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select your environment to open its detailed view.
1. In the detailed view (not on the navigation pane), under **Resources**, select **Dynamics 365 apps**.
1. Make sure that all the required apps that are listed in the preceding table are shown as installed. If any required apps aren't shown as installed, select **Install app** on the toolbar, and follow the on-screen instructions to install each app.

### Additional requirements for using Copilot sidecar features

The Copilot sidecar uses conversational bots and the generative answers capability from Copilot Studio.

Generative answers require Bing Search. In addition, depending on the availability of back-office services in your region, your Dataverse environment might have to be set up to support cross-region calls. For more information, see [Enable copilots and generative AI features](/power-platform/admin/geographical-availability-copilot).

> [!NOTE]
> If the required AI services are already available in your Dataverse region, you don't have to set up support for cross-region calls.

If Bing Search is disabled, or if cross-region data movement is required but is disabled, users won't be able to open the Copilot sidecar, or the Copilot sidecar won't provide answers, depending on the situation.

### Confirm that your Power Platform environment can publish copilots that have AI features

By default, the tenant-level setting that enables the deployment of Copilot bots in Dataverse environments is enabled. However, a tenant admin can disable this setting. If the setting is disabled, you can't use Copilot features in finance and operations apps.

To check and enable the setting that enables Power Platform to publish copilots that have AI features, follow these steps.

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the navigation pane, select **Settings**.
1. In the list, select the row where the **Name** field is set to *Publish bots with AI features*.
1. In the **Publish Copilots with AI features** dialog box, set the option to *Enabled* or *Disabled*, as you prefer.
1. Select **Save**.

## Feature-specific installations

As was previously mentioned, most Copilot features in finance and operations apps require that Power Platform Integration is enabled for your environment. They also require that your environment meets the other requirements that are outlined in this article. For some features, this foundation is all that's needed. However, other features might require additional installations and/or feature management. The following table lists each Copilot feature and provides links to articles that explain how to enable it.

| Application | Feature | Required installation and setup |
|---|---|---|
| All finance and operations apps | Basic Copilot support | There are no additional requirements. |
| All finance and operations apps | Generative help and guidance with Copilot | [Enable generative help and guidance with Copilot](enable-copliot-generative-help.md). |
| All finance and operations apps | Workflow history summary | [Turn on Copilot support for the Workflow history page](../../fin-ops/organization-administration/workflow-history-summary.md) |
| Dynamics 365 Commerce | Use Copilot in site builder to enrich product detail pages | [Enable Copilot in site builder](../../../commerce/copilot-site-builder.md). |
| Dynamics 365 Finance | Collections coordinator summary | [Enable collections coordinator summary](../../../finance/accounts-receivable/CollectionsCoordinatorSummary.md). |
| Dynamics 365 Finance | Customer page summary | [Enable customer page summary](../../../finance/accounts-receivable/CustomerPageSummary.md). |
| Dynamics 365 Supply Chain Management | AI summaries with Copilot | [Enable AI summaries with Copilot](../../../supply-chain/get-started/copilot-summaries-overview.md). |
| Dynamics 365 Supply Chain Management | [Analyze demand plans with Copilot](../../../supply-chain/demand-planning/demand-planning-copilot.md) | This feature is installed and enabled by default in Demand planning version 1.0.0.1067 and later. |
| Dynamics 365 Supply Chain Management | [Inquire into inventory with Copilot](../../../supply-chain/inventory/inventory-visibility-copilot-api.md) | This feature is installed and enabled by default in Inventory Visibility version 1.2.2.127 and later. |
| Dynamics 365 Supply Chain Management | Review and accept changes to confirmed purchase orders | [Enable Copilot support for managing changes to confirmed purchase orders](purchase-order-changes-after-confirmation-enable.md). |
| Dynamics 365 Supply Chain Management | Workload insights with Copilot in the Warehouse Management mobile app | [Enable Workload insights with Copilot](../../../supply-chain/warehousing/warehouse-management-mobile-app-insights.md) |

## Responsible AI FAQs

For information about the capabilities and limitations of AI-powered Copilot features in finance and operations apps, see [Responsible AI FAQs for the Microsoft Dynamics 365 finance and operations platform](../responsible-ai/responsible-ai-overview.md).
