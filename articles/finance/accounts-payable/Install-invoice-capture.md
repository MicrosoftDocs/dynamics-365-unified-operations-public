---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution and integrate it with Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 06/19/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Install the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

> [!IMPORTANT]
> If you installed the solution in private preview, you must uninstall the old solution before you continue.

## Prerequisites

Before you can install the Invoice capture solution, the following prerequisites must be met:

- The **Invoice capture for Dynamics 365 Finance** feature should be enabled.
- The Power Platform environment must be created.
- The finance and operations virtual entity must be installed in the Power Platform environment.

## Configure Dynamics 365 Finance

Invoice capture is generally available in Dynamics 365 Finance version 10.0.33 and later.

After the **Invoice capture for Dynamics 365 Finance** feature is enabled, users can go to **Accounts payable \> Set up \> Invoice capture**.

Before you install Invoice capture, complete the following setup in Invoice capture.

1. In the **Synced legal entities** list, select the legal entities to onboard.
2. Select whether an invoice attachment should be transferred together with the invoice from Invoice capture.
3. Maintain the mapping relationship between the invoice type in Invoice capture and the invoice framework to create the invoice in Dynamics 365 Finance.

    In the current version, the following options are available.

    | Invoice type in Invoice capture | Invoice framework in Dynamics 365 Finance |
    |------|---------|
    | PO invoice | Vendor invoice |
    | Header-only invoice | Vendor invoice |
    | Cost invoice | Vendor invoice or Invoice journal |

## Install and set up the solution

Invoice capture supports integrated Power Platform environments.

### Integrated Power Platform environment

For an *integrated* Power Platform environment, the finance and operations virtual entity is already installed. To confirm that it's installed in the environment, follow these steps.

1. In Power Platform admin center, go to **Environment**, and open the **Environment details** page.
2. Select **Resource \> Dynamic 365 apps**.
3. Confirm that **Finance and Operations Virtual Entity** appears in the list, and that it has a status of **Installed**.

To install Invoice capture, follow this step.

- In AppSource, search for **Invoice Capture for Dynamics 365 Finance**. Before general availability, the app can be found [here](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.dynamics365-fno-invoice-capture-preview?flightCodes=15e3cf87e5e04ac5872c702deb9f7ae7). After the installation is completed, you should see the solution installed in the selected environment in Power Apps.

> [!NOTE]
> After installation, go to **Setup system \> Manage legal entities** and **Manage vendors** to sync the entries from Dynamics 365 Finance.

## Upgrade the Invoice capture solution

1. In Power Platform admin center, go to **Environment**, and open the **Environment details** page.
2. Select **Resource \> Dynamic 365 apps**.
3. If **Invoice Capture within Dynamics 365 Finance** has a status of **Upgrade available**, select **Update**, accept the terms of service, and confirm that you want to update the solution.

## Delete the Invoice capture solution

If you must delete the Invoice capture solution, follow these steps.

1. In Microsoft Power Platform, select the correct environment, and then select **Solution**.
2. To completely delete the Invoice capture solution, delete the solutions in the following order:

    1. Dynamics 365 Invoice capture - FNO Integration
    2. Dynamics 365 Invoice capture - Application
    3. Dynamics 365 Invoice capture Solution Anchor
    4. Dynamics 365 Invoice capture - Controls
    5. Dynamics 365 Invoice capture - Backend
    6. Dynamics 365 Invoice capture Base

> [!NOTE]
> To delete Invoice capture but keep the data, don't delete the Dynamics 365 Invoice capture Base solution.

