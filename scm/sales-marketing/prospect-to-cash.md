---
# required metadata

title: Prospect to cash   
description: The topic provides an overview of the Prospect to cash solution between Dynamics 365 for Sales and Dynamics 365 for Finance and Operations, Enterprise edition. 
author: YuyuScheller
manager: AnnBe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: YuyuScheller
ms.dyn365.ops.intro: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Prospect to cash  

[!include[banner](../includes/banner.md)]

The Prospect to cash solution uses [Data Integrator](https://docs.microsoft.com/en-us/common-data-service/entity-reference/dynamics-365-integration) to synchronize data across Microsoft Dynamics 365 Finance and Operations, Enterprise edition (Finance and Operations) and Microsoft Dynamics 365 for Sales (Sales) instances via the Common Data Service. The Prospect to cash templates available with the Data Integrator enable the flow of product, account, contact, and sales quote data between Finance and Operations and Sales. While the data is flowing between Finance and Operations and Sales, you can carry out sales and marketing activities in Sales and handle the order fulfillment with inventory management in Finance and Operations. 

This solution provides integration in the following areas: 

-   Maintain accounts in Sales and sync them to Finance and Operations.
-   Maintain contacts in Sales and sync them to Finance and Operations.
-   Maintain products in Finance and Operations and sync them to Sales.
- 	Create sales quotes in Sales and sync them to Finance and Operations.
-   Create sales orders in Finance and Operations and sync them to Sales.
-   Create sales invoices in Finance and Operations and sync them to Sales.

## System requirements for Finance and Operations, Enterprise Edition

To use the Prospect to cash solution, you must install 

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update with Platform update 8 (App 7.2.11792.56024 w/ Platform 7.0.4565.16212). 

- Two hotfixes for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update.

    -  [KB4036461](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036461&bugId=3847029&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2): This hotfix enables sales order synchronization with Data integrator from Dynamics 365 for Finance and Operations to Sales.
    -  [KB4036524](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036524&bugId=3847504&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2): This hotfix enables sales order line synchronization with Data integrator from Dynamics 365 for Finance and Operations to Sales.
 
## System requirements for Sales

To use the Prospect to cash solution, you must install 

- Dynamics 365 for Sales Version 1612 (8.2.1.207) (DB 8.2.1.207) online.
- Prospect to cash solution for Dynamics 365 for Sales, version 1.14.0.0 or later.

### Install the Prospect to cash solution for Sales

- Download [the Prospect to cash for Dynamics 365 for Sales solution package deployer zip](https://mbs.microsoft.com/customersource/Global/365Enterprise/downloads/product-releases/MD365FNOPENTProspectToCash) on CustomerSource.

- Make sure that the zip file is unblocked so that you don't get the errro message No import packages were found when you install the solution package. To unblock the file,

    -  Right-click the zip file.
    -  Select **Poperties** and then select **Unblock**. 

- Unzip and run PackageDeployer.exe.

- Install the Prospect to Cash soolution in your Sales instance.

    - Select the Deployment type: **Office 365**.
    - Select **Show advanced**.
    - To install fast, eelect a **Region**. If you select **Don’t know**, the system searches for all regions and it will take longer to install.)
    - Enter **User name** and **Password** for an admin user who has the privilege to install.

