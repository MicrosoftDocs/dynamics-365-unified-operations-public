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

- The feature **Invoice capture for Dynamics 365 Finance** should be enabled. 
- The Power Platform environment must be created.
- The finance and operations virtual entity must be installed in the Power Platform environment.


## Configure Dynamics 365 Finance

Invoice capture is generally available in Dynamics 365 finance version 10.0.33 and later. 

After **Invoice capture for Dynamics 365 Finance** is enabled, users can go to **Accounts Payable > Set up > Invoice capture**. 

Before installing Invoice capture, complete the following set up in Invoice capture:

1.	In the **Synced legal entities**, select the legal entities to onboard. 
2.	Select if an invoice attachment will be transferred with the invoice from Invoice capture.
3.	Maintain the mapping relationship between invoice type in Invoice capture and the invoice framework to create the invoice in Dynamics 365 Finance.
In the current version, the following options are avilable: 

| Invoice type in Invoice capture | Invoice framework in Dynamics 365 Finance | 
|------|---------|
| PO invoice | Vendor invoice |
| Header-only invoice  | Vendor invoice |
| Cost invoice | Vendor invoice or Invoice journal |

## Install and set up the solution

Invoice capture supports integrated Power Platform environments. 

### Integrated Power Platform environment

For an *integrated* Power Platform environment, the finance and operations virtual entity is already installed. To confirm that it's installed in the environment, follow these steps.

1. In the Power Platform admin center, go to **Environment**, and open the **Environment details** page.
2. Select **Resource \> Dynamic 365 apps**.
3. Confirm that **Finance and Operations Virtual Entity** appears in the list, and that it has a status of **Installed**.
   
To install Invoice capture, follow this step.

- In AppSource, select the link for the preview version of [Dynamics 365 Invoice capture](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics365-invoice-capture-preview?flightCodes=invoicecapture). After the installation is completed, you should see the solution installed in the selected environment in Power Apps.

> [!NOTE]
> After installation, please go to **Setup system \> Manage legal entities** and **Manage vendors** to sync the entries from Dynamics 365 Finance.


## Upgrade the Invoice capture solution

1. In the Power Platform admin center, go to **Environment**, and open the **Environment details** page.
2. Select **Resource \> Dynamic 365 apps**.
3. If **Invoice Capture within Dynamics 365 Finance** has a status of **Upgrade available**, select **Update**, accept the terms of service, and confirm that you want to update.


## Delete the Invoice capture solution:
If the invoice capture solution needs to be deleted, follow these steps:

1.	In the Power Platform, select the right environment and select **Solution**.
2.	To complete delete the Invoice capture, delete the solutions in the following order: 
- Dynamics 365 Invoice capture - FNO Integration
- Dynamics 365 Invoice capture - Application
- Dynamics 365 Invoice capture Solution Anchor
- Dynamics 365 Invoice capture - Controls
- Dynamics 365 Invoice capture - Backend 
- Dynamics 365 Invoice capture Base

> [!NOTE]
> If the users want to only delete Invoice capture and keep the data, don't delete Dynamics 365 Invoice capture Base.
 


### Non-integrated Power Platform environment

For a *non-integrated* Power Platform environment, you must install the finance and operations virtual entity by following these steps.

1. In the Power Platform admin center, go to **Resources \> Dynamics 365 apps**, and find **Finance and Operations Virtual Entity**.
2. Select the environment, and accept the terms of service.
3. Select **Install** to install the finance and operations virtual entity in the selected environment.

Invoice capture officially supports *integrated* Power Platform environments. Before you can install the Invoice capture solution, you must set up the connection between the environment and the Microsoft Dynamics 365 Finance environment by following these steps.

1. Register an application, and add a client secret to Microsoft Azure Active Directory (Azure AD) in your Azure subscription. For more information, see [Register a web application with AAD](../../dev-itpro/data-entities/services-home-page.md#register-a-web-application-with-aad).

    > [!NOTE]
    > Make a note of the **Application (client) ID**, **Client secret**, and **Tenant ID** values, because you will need them later.
2. In the Power Platform admin center, go to **Environment**, and open the **Environment details** page.
3. Find and make a note of the environment URL.
4. Replace **\<Environment URL\>** in the following URL with the environment URL that you found, and open the "Finance and Operation Virtual Data Source configuration."

    `https://<Environment URL>/main.aspx?cmdbar=true&forceUCI=1&navbar=off&pagetype=entityrecord&etn=msdyn_financeandoperationsvirtualentity&id=47c40dcb-35d6-e911-a95e-000d3a110bbd`

5. Leave the existing entries unchanged.
6. Enter the **finance and operations target URL, Application (client) ID**, **Client secret**, and **Tenant ID** in the appropriate fields.
7. Register the Azure application in a Dynamics 365 Finance environment. For more information, see [Register your external application](../../dev-itpro/data-entities/services-home-page.md#register-your-external-application).

> [!NOTE]
> For integrated Power Platform environments, this step is still required in the current version. However, it isn't required in the general availability (GA) version.
