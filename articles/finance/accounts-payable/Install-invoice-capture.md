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
Invoice capture officially supports the Integrated Power Platform environment. Before you can install the Invoice capture solution, set up the connection between the environment and Dynamics 365 Finance environment by completely the following prerequisites:

### Integrated Power Platform environment
1. Find the environment URL in the Power Platform admin center. Go to **Power Platform admin center > Environment > Environment details** page. 
2. Replace the <Environment URL> in the below URL and open the “Finance and Operation Virtual Data Source configuration”. 

https://<Environment URL>/main.aspx?cmdbar=true&forceUCI=1&navbar=off&pagetype=entityrecord&etn=msdyn_financeandoperationsvirtualentity&id=47c40dcb-35d6-e911-a95e-000d3a110bbd 

3. Keep the existing entries. 
4. Fill the finance and operations target URL, Tenant Id, Application Id and Application Secret to the corresponding fields.  

    
### Non-integrated Power Platform environment    

For non-integrated Power Platform environment, it requires installing finance and operations virtual entity:
1. Go to **Power Platform admin center > Resources > Dynamics 365 apps**. Find “Finance and Operations Virtual Entity”. 
2. Select the environment and accept the terms of service. 
3. Click **Install** to install finance and operations virtual entity in the selected environment. 


>[!NOTE]
>Invoice capture is supported on Dynamics 365 finance and operations version 10.0.31 and later.

### Install and set up the solution

Install the Invoice capture solution:

1. Go to AppSource, and select the link for the preview version of [Dynamics 365 Invoice capture](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamics365-invoice-capture-preview?flightCodes=invoicecapture). After the installation is completed, you will see the solution installed in the selected environment in Power Apps.

>[!NOTE]
>Go to **Setup system > Manage legal entities** and **Manage vendors** to confirm the entries are synchronized from Dynamics 365 Finance in the list.     
