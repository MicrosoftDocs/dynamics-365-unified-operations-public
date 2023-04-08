---
# required metadata

title: Install the Invoice capture solution
description: This article provides information about how to install the Invoice capture solution and integrate it with Microsoft Dynamics 365 Finance.
author: sunfzam
ms.date: 04/05/2023
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
ms.custom: ["13971", "intro-internal"]
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

Ensure the **Finance and Operation Virtual Entity** is installed in the environment.

For **Integrated Power Platform environment**, the **Finance and Operation Virtual Entity** is by-default installed.

To ensure the **Finance and Operation virtual entity** is installed in the environment, please go to **Power Platform admin center > Environment > Environment details form and click Resource > Dynamic 365 apps**, **Finance and Operation Virtual Entity** should be shown in the list with status **Installed**.

For the **non-Integrated Power Platform environment**, it requires:

1. Install **Finance and Operation virtual entity** first via steps:

   a.   Go to **Power Platform admin center > Resources > Dynamics 365 apps**, find **“Finance and Operations Virtual Entity”**.
   
   b.	Select the environment and accept the terms of service.
   
   c.	Click “Install” to install **Finance and Operation Virtual Entity** in the selected environment.
   
   d.	Please ensure the installation is complete.

2. Invoice capture officially supports the **Integrated Power Platform environment**. Before installation, Set up the connection between the environment and Dynamics 365 Finance environment via steps:

    a.	Find the environment URL in **Power Platform admin center > Environment > Environment details form**.
    
    b.	Replace the following **<Environment URL>** in the below URL and open the “Finance and Operation Virtual Data Source configuration”.
    
    `https://<Environment URL>/main.aspx?cmdbar=true&forceUCI=1&navbar=off&pagetype=entityrecord&etn=msdyn_financeandoperationsvirtualentity&id=47c40dcb-35d6-e911-     a95e-000d3a110bbd`
    
    c.	Keep existing entries unchanged and fill the following fields. 
    
    - 	Dynamics 365 Finance URL – The URL of the Finance environment that you want to integrate with.
    
    - 	Tenant ID – The tenant ID for the Finance environment.
    
    - 	Client ID – The Azure application ID that was registered.
    
    - 	Client Secret – The client secret that was generated for the Azure application.
    
> [!NOTE]
> For Integrated Power Platform environment, this step is still REQUIRED for current version, but not needed in GA version. 

> [!NOTE]
> Invoice capture is supported in version 10.0.31 and later of finance and operations apps.    
    
## How-To install Invoice capture
Go to AppSource, and select the link for the preview version of [Dynamics 365 Invoice capture](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics365-invoice-capture-preview?flightCodes=invoicecapture). After the installation is completed, you will see the solution installed in the selected environment in Power Apps.
    
> [!NOTE]
> Please go to Setup system > Manage legal entities and Manage vendors to check whether the entries are synchronized from Dynamics 365 Finance in the list.
    
    
Invoice capture officially supports the Integrated Power Platform environment. Before you can install the Invoice capture solution, set up the connection between the environment and the Microsoft Dynamics 365 Finance environment by completing the following prerequisites.

## Upgrade the Invoice capture solution
When the new version is published, please go to **Power Platform admin center > Environment > Environment details form** and click **Resource > Dynamic 365 apps**, **Invoice Capture within Dynamics 365 Finance** will be shown in the list with status **Upgrade available**. Admin can do the update by clicking Update in the ribbon and confirm after accepting the terms of service. 
    
