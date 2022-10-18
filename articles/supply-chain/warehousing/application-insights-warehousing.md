---
title: Enable warehousing telemetry with Application Insights
description: This article describes how to set up Supply Chain Management to send warehousing telemetry data to Azure Application Insights.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: OperationalInsightsProvisioningForm
ms.topic: how-to
ms.date: 10/18/2022
ms.custom: bap-template
---

# Enable warehousing telemetry with Application Insights

[!include [banner](../includes/banner.md)]

This article describes how to set up Supply Chain Management to send warehousing telemetry data to Azure Application Insights.

## Turn telemetry features on or off for your system

Before you can use telemetry features in Supply Chain Management, you must turn them on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *System administration*
- **Feature name:** *Operational insights*

## Set up Azure Application Insights

Start by setting up Application Insights on your Azure subscription. Follow these steps:

1. If you don't already have one, get a subscription to [Microsoft Azure](https://azure.microsoft.com/).

    > [!NOTE]
    > You can set up the Application Insights resource on any Azure tenant that can be accessed by your system. For example, you might set up Application Insights on a tenant that belongs to your Microsoft partner, which would allow them to analyze your telemetry data even if they don't have access to your Azure tenant.

1. Sign in to the [Azure portal](https://portal.azure.com/) for the account where you want to install Application Insights.
1. Create an Application Insights resource by following the instructions given in [Create an Application Insights resource](/azure/azure-monitor/app/create-new-resource).
1. Keep a copy of the **Instrumentation key** for your Application Insights resource (see also [Create an Application Insights resource](/azure/azure-monitor/app/create-new-resource)). You'll need it later to set up Supply Chain Management to submit the data.

## Set up your apps to send telemetry data to Azure Application Insights

Once you have set up Application Insights and have a copy of its instrumentation key, you're ready to enable Supply Chain Management to send telemetry data. Follow these steps:

1. Sign in to Supply Chain Management as a user with system admin privileges.
1. Go to **System administration \> Setup \> Operational insights**.
1. Open the **Configure** tab and make the following settings:
    - **Commerce channel events** – Choose whether to send commerce-channel telemetry data to Application Insights. This setting isn't relevant for warehousing. If you aren't using Dynamics 365 Commerce and/or don't want to collect telemetry about it, you should set this option to *No*.
    - **Warehouse events** – Choose whether to send warehousing telemetry data to Application Insights. You should set this option to *Yes*.

1. Open the **Environments** tab and make the following settings:
    - **LCS Environment ID** – Enter the ID for the Lifecycle Services (LCS) environment that you want to send telemetry data from. To find this ID, [sign in to LCS](https://lcs.dynamics.com/Logon/Index), go to the environment details page for your environment, and look in the **Environment Details** section, which lists the **Environment ID**.
    - **Environment mode** – Identify the mode of your selected environment. The supported environment modes are *Development*, *Test*, and*Production*.

1. Open the **Application Insights registry** tab and make the following settings:
    - **Environment mode** – Identify the mode of your selected environment. This value must match the mode you specified on the **Environments** tab.
    - **Instrumentation key** – Enter the instrumentation key that you copied when setting up Application Insights in Azure.

    > [!NOTE]
    > You can use the same instrumentation key for different environment modes.

1. Select **Save** on the Action Pane to save your settings.

## Pricing

Azure Application Insights is billed based on the volume of telemetry data your application sends (data ingestion) and how long time you want data to be available (data retention). For up-to-date information on pricing, see  [Azure Monitor pricing](https://azure.microsoft.com/pricing/details/monitor/).

## Next steps

- [Monitor mobile device usage and performance](application-insights-wma.md)
