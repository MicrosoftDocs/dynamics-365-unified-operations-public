---
# required metadata

title: Prospect to cash   
description: The topic provides an overview of the Prospect to cash solution between Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics 365 for Sales. 
author: ChristianRytt 
manager: AnnBe
ms.date: 10/26/2017
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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.intro: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Prospect to cash  

[!include[banner](../includes/banner.md)]

The Prospect to cash solution uses [Data Integration](/common-data-service/entity-reference/dynamics-365-integration) to synchronize data across Microsoft Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics 365 for Sales instances via the Common Data Service (CDS). The Prospect to cash templates available with the Data Integration feature enable the flow of accounts, contacts, products, sales quotes, sales orders, and sales invoices data between Finance and Operations and Sales. While the data is flowing between Finance and Operations and Sales, you can carry out sales and marketing activities in Sales and handle the order fulfillment with inventory management in Finance and Operations. 

This solution provides integration in the following areas: 

-   [Maintain accounts in Sales and sync them to Finance and Operations](accounts-template-mapping.md)
-   [Maintain contacts in Sales and sync them to Finance and Operations](contacts-template-mapping.md)
-   [Maintain products in Finance and Operations and sync them to Sales](products-template-mapping.md)
- 	[Create sales quotes in Sales and sync them to Finance and Operations](sales-quotation-template-mapping.md)
-   [Create sales orders in Finance and Operations and sync them to Sales](sales-order-template-mapping.md)
-   [Create sales invoices in Finance and Operations and sync them to Sales](sales-invoice-template-mapping.md)

This solution provides direct synchronization in the following areas:

-   [Maintain accounts in Sales and sync them directly from Sales to Finance and Operations](accounts-template-mapping-direct.md)
-   [Maintain products in Finance and Operations and sync them directly to Sales](products-template-mapping-direct.md)
-   [Maintain contacts in Sales and sync them directly to contacts or customers in Finance and Operations](contacts-template-mapping-direct.md)
-   [Create sales orders in Finance and Operations and sync them directly to Sales](sales-order-template-mapping-direct.md)
-  [Synchronize sales order headers and lines directly between Sales and Finance and Operations](sales-order-template-mapping-between-sales-fin.md)
-   [Synchronize sales quotation headers and lines directly from Sales to Finance and Operations](sales-quotation-template-mapping-sales-fin.md)
-   [Synchronize sales orders directly between Sales and Finance and Operations](sales-order-template-mapping-direct-two-ways.md)
-   [Create sales invoices in Finance and Operations and sync them directly to Sales](sales-invoice-template-mapping-direct.md)


## System requirements for Dynamics 365 for Finance and Operations, Enterprise edition

To use the Prospect to cash solution, you must install the following:

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) with Platform update 8 (App 7.2.11792.56024 w/ Platform 7.0.4565.16212)

- Hotfixes for Dynamics 365 for Finance and Operations, Enterprise edition (July 2017).
        
    -  [KB4045570](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4045570&bugId=3851320&qc=ac1145034fd04ab71ccc4d14aa012f245176712c9af7c36bb77a118726d46160) - This hotfix enabels support for sales order synchronization with the Data Integration feature from Sales to Finance and Operations, along with a number of other enhancements.

    -  [KB4036524](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036524&bugId=3847504&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2) - This hotfix enables sales order line synchronization with the Data Integration feature from Finance and Operations to Sales.
        
    -  [KB4036461](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036461&bugId=3847029&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2) - This hotfix enables sales order synchronization with the Data Integration feature from Finance and Operations to Sales.

**Note**: You only need to install KB4045570 because the installation includes the changes from the other KB's.
 
## System requirements for Dynamics 365 for Sales

To use the Prospect to cash solution, you must install the following:

- Dynamics 365 for Sales version 1612 (8.2.1.207) (DB 8.2.1.207) online.
- Prospect to cash solution for Dynamics 365 for Sales, version 1.14.0.0 (v14) or later.

### Install the Prospect to cash solution for Sales

- Download the [Prospect to cash for Dynamics 365 for Sales solution package zip file](https://mbs.microsoft.com/customersource/Global/365Enterprise/downloads/product-releases/MD365FNOPENTProspectToCash) on CustomerSource.

- Make sure that the zip file is unblocked so that you do not get the error message "No import packages were found" when you install the solution package. To unblock the file, do the following:

    -  Right-click the zip file.
    -  Select **Properties** and then select **Unblock**. 

- Unzip and run PackageDeployer.exe.

- Install the Prospect to Cash solution in your Sales instance.

    - Select the **Office 365** Deployment type.
    - Select **Show advanced**.
    - For a quick installation, select a **Region**. If you select **Don’t know**, the system searches for all regions and it will take longer to install.
    - Enter **User name** and **Password** for an admin user who has the user rights to install.
