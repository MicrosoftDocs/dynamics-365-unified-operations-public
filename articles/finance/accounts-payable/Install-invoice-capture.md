---
title: Install the Invoice capture solution
description: Learn about how to install the Invoice capture solution and integrate it with Microsoft Dynamics 365 Finance, including prerequisites.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 07/25/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Install the Invoice capture solution

[!include [banner](../includes/banner.md)]

## Prerequisites

Invoice capture officially supports only integrated Power Platform environments. For more information, see [Integrated Power Platform environments](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md). For an integrated Power Platform environment, the finance and operations virtual entity is already installed. To confirm that it's installed in the environment, follow these steps:

1. In Power Platform admin center, go to **Environment**, and open the **Environment details** page.
1. Select **Resource** \> **Dynamic 365 apps**.
1. Confirm that **Finance and operations virtual entity** is displayed with a status of **Installed**.

Before you can install the Invoice capture solution, ensure the following prerequisites are met:

- Enable the **Invoice capture for Dynamics 365 Finance** feature.
- Create the Power Platform environment.
- Install the finance and operations virtual entity in the Power Platform environment.

## Configure Dynamics 365 Finance

When you enable the **Invoice Capture for Dynamics 365 Finance** feature, the **Invoice capture** menu is available under **Accounts Payable \> Set up \> Invoice capture**.

Before you install Invoice capture, complete the following setup in Invoice capture:

1. In the **Synced legal entities** list, select the legal entities to onboard.

    By default, the **Sync all vendors** option is enabled. This option synchronizes any changes or additions to vendors within onboarded legal entities from Dynamics 365 finance and operations to Invoice capture in real-time. To avoid potential failure due to a virtual entity bottleneck with larger data volume, you need to manually synchronize vendors for each individual legal entity.

1. Select if an invoice attachment is transferred together with the invoice from Invoice capture.

    When you enable the parameter, the **Document type** column in the **Synced legal entities** list is enabled, and the value in the **File** field is assigned. Administrators can select which document type is used for the attachment from Invoice capture.

1. Maintain the mapping relationship between the invoice type in Invoice capture and the invoice framework to create the invoice in Dynamics 365 Finance.

    In the current version, the following options are supported:

    | Invoice type in Invoice capture | Invoice framework in Dynamics 365 Finance |
    |------|---------|
    | PO invoice | Vendor invoice |
    | Header-only invoice | Vendor invoice |
    | Cost invoice | Vendor invoice or Invoice journal |

When you select the invoice journal, the **Invoice journal name** column in the **Synced legal entities** list is enabled, and the default journal name is assigned. Administrators can select which journal name is used to create the cost invoices in Dynamics 365 Finance.

> [!NOTE]
> The **Document type** and **Invoice journal name** columns are available in Dynamics 365 Finance version 10.0.39 and later.
>
> The attachment transfer of cost invoice to invoice journal header level is supported.

## Invoice capture in Dynamics 365 Finance

The **Invoice capture** tile is available on the home page. The **Invoice capture for Dynamics 365 finance and operations** feature controls whether the tile is displayed.

When you don't install Invoice capture in the integrated Power Platform environment, the tile goes to the installation page of Dynamics 365 Finance. When you install Invoice capture, the tile goes to the Invoice capture home page.

## Install and set up the solution

Invoice capture supports integrated Power Platform environments.

### Integrated Power Platform environment

For an *integrated* Power Platform environment, the finance and operations virtual entity is already installed. To confirm that it's installed in the environment, follow these steps:

1. In Power Platform admin center, go to **Environment**, and open the **Environment details** page.
1. Select **Resource \> Dynamic 365 apps**.
1. Confirm that **Finance and Operations Virtual Entity** appears in the list, and that it has a status of **Installed**.

To install Invoice capture, follow this step.

- In Marketplace, search for **Invoice Capture for Dynamics 365 Finance**. You can find the preview version of Invoice capture [here](https://marketplace.microsoft.com/en-us/product/dynamics-365/mscrm.dynamics365-fno-invoice-capture-preview?flightCodes=15e3cf87e5e04ac5872c702deb9f7ae7). After the installation is completed, you see the solution installed in the selected environment in Power Apps.

> [!NOTE]
> After installation, in Invoice capture, go to **Setup system \> Manage legal entities** and **Manage vendors** to sync the entries from Dynamics 365 Finance.
>
> You can find the implementation guide at **Details and support \> Links**.

## Upgrade the Invoice capture solution

When a new solution version is available, the system notifies you. Follow these steps to upgrade the solution:

1. In Power Platform admin center, go to **Environment**, and open the **Environment details** page.
1. Select **Resource \> Dynamic 365 apps**.
1. If **Invoice Capture within Dynamics 365 Finance** shows **Upgrade available**, select **Update**, accept the terms of service, and confirm that you want to update the solution.

## Delete the Invoice capture solution

If you need to delete the Invoice capture solution, follow these steps:

1. In Microsoft Power Platform, select the correct environment, and then select **Solution**.
1. To completely delete the Invoice capture solution, delete the solutions in the following order:

    1. Dynamics 365 Invoice capture - FNO Integration
    1. Dynamics 365 Invoice capture - Application
    1. Dynamics 365 Invoice capture Solution anchor
    1. Dynamics 365 Invoice capture - Controls
    1. Dynamics 365 Invoice capture - Backend
    1. Dynamics 365 Invoice Capture - Permissions
    1. Dynamics 365 Invoice capture Base

> [!NOTE]
> To delete Invoice capture but keep the data, don't delete the Dynamics 365 Invoice capture base solution.
