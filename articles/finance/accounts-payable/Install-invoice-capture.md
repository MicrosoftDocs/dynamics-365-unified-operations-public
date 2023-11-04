---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution and integrate it with Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 11/01/2023
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

> [!IMPORTANT]
> If you installed the solution in private preview, you must uninstall the old solution before you continue.

## Prerequisites

Before you can install the Invoice capture solution, the following prerequisites must be met:

- The **Invoice capture for Dynamics 365 Finance** feature should be enabled.
- The Power Platform environment must be created.
- The finance and operations virtual entity must be installed in the Power Platform environment.

## Configure Dynamics 365 Finance

Invoice capture GA version is supported in version 10.0.33 and later. The following Dynamics 365 Finance versions are required before installing Invoice capture (1.1.0.10 +):
- Dynamics 365 Finance 10.0.36 10.0.1695.28 or later
- Dynamics 365 Finance 10.0.35 10.0.1627.86 or later
- Dynamics 365 Finance 10.0.34 10.0.1591.124 or later

After the **Invoice capture for Dynamics 365 Finance** feature is enabled, users can go to **Accounts payable \> Set up \> Invoice capture**.

Before you install Invoice capture, complete the following setup in Invoice capture.

1. In the **Synced legal entities** list, select the legal entities to onboard.

   By default, the option **Sync all vendors** is enabled. This option synchronizes any changes or additions to vendors within onboarded legal entities from Dynamics 365 finance and operations to Invoice capture in real-time. Manual vendor synchronization is needed for each individual legal entity to avoid potential failure due to a virtual entity bottleneck with larger data volume.
   
3. Select whether an invoice attachment should be transferred together with the invoice from Invoice capture.

   When the parameter is enabled, confirm the default document file is assigned to the **File** field on the **Default document types** page.
   
5. Maintain the mapping relationship between the invoice type in Invoice capture and the invoice framework to create the invoice in Dynamics 365 Finance.

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

- In AppSource, search for **Invoice Capture for Dynamics 365 Finance**. The preview version of Invoice capture can be found [here](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.dynamics365-fno-invoice-capture-preview?flightCodes=15e3cf87e5e04ac5872c702deb9f7ae7). After the installation is completed, you should see the solution installed in the selected environment in Power Apps.

> [!NOTE]
> After installation, go to **Setup system \> Manage legal entities** and **Manage vendors** to sync the entries from Dynamics 365 Finance.

## Upgrade the Invoice capture solution
When a new solution is available, the user will be notified of the availability of the new version. Follow the steps below to complete the upgrade:

1. In Power Platform admin center, go to **Environment**, and open the **Environment details** page.
2. Select **Resource \> Dynamic 365 apps**.
3. If **Invoice Capture within Dynamics 365 Finance** has a status of **Upgrade available**, select **Update**, accept the terms of service, and confirm that you want to update the solution.

## Delete the Invoice capture solution

If you must delete the Invoice capture solution, follow these steps.

1. In Microsoft Power Platform, select the correct environment, and then select **Solution**.
2. To completely delete the Invoice capture solution, delete the solutions in the following order:

    1. Dynamics 365 Invoice capture - FNO Integration
    2. Dynamics 365 Invoice capture - Application
    3. Dynamics 365 Invoice capture Solution anchor
    4. Dynamics 365 Invoice capture - Controls
    5. Dynamics 365 Invoice capture - Backend
    6. Dynamics 365 Invoice capture Base

> [!NOTE]
> To delete Invoice capture but keep the data, don't delete the Dynamics 365 Invoice capture base solution.
> The preview version of Invoice capture (1.0.0.x) will be deprecated September 2023. Customers will want to migrate to the General availability (GA) version. It's mandatory to remove **Dynamics 365 Invoice capture base** before installing the GA version. It will take 10 to 15 minutes to complete the uninstallation. 

