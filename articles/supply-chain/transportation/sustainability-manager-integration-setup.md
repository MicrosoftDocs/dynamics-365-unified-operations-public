---
title: Integrate with Microsoft Sustainability Manager (preview)
description: 
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: TMSParameters, TMSMethod
ms.topic: how-to
ms.date: 11/28/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Integrate with Microsoft Sustainability Manager (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.38 GA -->

This article describes how to integrate Dynamics 365 Supply Chain Management with Microsoft Sustainability Manager. The integration lets you accurately calculate carbon emissions during rate and route planning in transportation management. Transportation planners can make informed decisions and strategically assign environmentally friendly transportation service providers for each load.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.38 or later.
- You must have valid subscription for Microsoft Sustainability Manager.
- You must be running Microsoft Sustainability Manager version 2.14.0.355 or later.
- The feature that is named *Integrate Microsoft Sustainability Manager with transportation management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Enable impersonation in Power Platform

To enable the two systems to communicate with each other, you must enable impersonation for Supply Chain Management in Power Platform.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Make sure Microsoft Sustainability Manager solution is successfully installed.
1. Enable impersonation for Supply Chain Management in Power Platform.
1. On the left navigation pane, go to **Environment** and then open the environment where you're running Supply Chain Management.
1. On the toolbar, select **Settings**.
1. Expand the **Product** heading and select **Features**.
1. Under the **Finance and Operations in Dataverse** heading, set **Enable Finance and Operations User Impersonation in Dataverse** to *Yes*.
1. Go to **Power Platform Admin Center (PPAC) > Environment > Settings > Features**, Check the [Enable Finance and Operations User Impersonation] checkbox, save the changes.

    :::image type="content" source="media/enable-fno-impersonation.svg" alt-text="Enable Finance and Operations User Impersonation" lightbox="media/enable-fno-impersonation.svg":::

## Map transportation modes in Supply Chain Management

To enable carbon emission calculations, you must map the transportation methods in Supply Chain Management with the transportation modes in Microsoft Sustainability Manager.

1. Sign in to Supply Chain Management.
1. Go to **Transportation management \> Setup \> Carriers \> Transportation methods**.
1. For each transportation method listed on this page, use the **Transportation Mode in Microsoft Sustainability Manager** field to identify the matching mode in Microsoft Sustainability Manager.

    > [!NOTE]
    > The transportation modes (vehicle types) listed here are taken from United State Environment Protection Agency Greenhouse Gas Emissions Factors Hub (EPA GHG Emissions Factors Hub). Microsoft Sustainability Manager uses these modes in its transportation and distribution calculation model. For more information, see  [GHG Emissions Factors Hub](https://www.epa.gov/climateleadership/ghg-emission-factors-hub).

1. On the Action Pane, select **Save**.

## Validate the connection and enable the integration scenario

To complete the setup, you must validate the connection and enable the integration scenario.

1. Go to **Transportation management \> Setup \> Transportation management parameters**.
1. Open the **Microsoft Cloud for Sustainability integration configuration** tab.
1. Select **Validate connection** to check whether your Power Platform environment is correctly set up and ready for the integration.
1. When the validation completes, select a model in the **Model name** field. Select the model that best matches the transportation scenario that you want to calculate carbon emissions for. The following options are available:

    - *None* – Indicates that you haven't selected a model yet. Emission calculations are disabled when this option is selected.
    - *Downstream transportation and distribution* – This model includes emissions generated from transporting and distributing sold products in vehicles that the reporting organization doesn't own or control.
    - *Upstream transportation and distribution* – This model includes emissions generated from third-party transportation and distribution services and emissions generated to transport and distribute purchased products.

    > [!NOTE]
    > For details about how Microsoft Sustainability Manager calculates Scope 3 emissions, see [Categories 4 and 9: Upstream and downstream transportation and distribution](/industry/sustainability/calculate-scope3#categories-4-and-9-upstream-and-downstream-transportation-and-distribution#categories-4-and-9-upstream-and-downstream-transportation-and-distribution).

1. Set **Enable McFS integration** to *Yes*.
1. Select **Save**.
