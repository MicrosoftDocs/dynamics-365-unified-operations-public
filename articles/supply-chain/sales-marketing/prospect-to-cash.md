---
# required metadata

title: Prospect to cash
description: This topic provides an overview of the Prospect to cash solution between Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and Microsoft Dynamics 365 for Sales. 
author: ChristianRytt 
manager: AnnBe
ms.date: 11/17/2017
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

The Prospect to cash solution provides direct synchronization across Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and Microsoft Dynamics 365 for Sales. The Prospect to cash templates that are available with the Data Integration feature enable the flow of data for accounts, contacts, products, sales quotations, sales orders, and sales invoices between Finance and Operations and Sales. While data is flowing between Finance and Operations and Sales, you can perform sales and marketing activities in Sales, and you can handle order fulfillment by using inventory management in Finance and Operations.

In the current version, the Prospect to cash solution provides the following types of direct synchronization:

- [Maintain accounts in Sales and sync them directly from Sales to Finance and Operations](accounts-template-mapping-direct.md)
- [Maintain products in Finance and Operations and sync them directly to Sales](products-template-mapping-direct.md)
- [Maintain contacts in Sales and sync them directly to contacts or customers in Finance and Operations](contacts-template-mapping-direct.md)
- [Synchronize sales quotation headers and lines directly from Sales to Finance and Operations](sales-quotation-template-mapping-sales-fin.md)
- [Synchronize sales order headers and lines directly from Finance and Operations to Sales](sales-order-template-mapping-direct.md)
- [Synchronize sales order headers and lines directly between Sales and Finance and Operations](sales-order-template-mapping-between-sales-fin.md)
- [Synchronize sales orders directly between Sales and Finance and Operations](sales-order-template-mapping-direct-two-ways.md)
- [Synchronize sales invoice headers and lines directly from Finance and Operations to Sales](sales-invoice-template-mapping-direct.md)

In earlier versions, the Prospect to cash solution provides the following types of non-direct synchronization:

- [Maintain accounts in Sales and sync them to Finance and Operations](accounts-template-mapping.md)
- [Maintain contacts in Sales and sync them to Finance and Operations](contacts-template-mapping.md)
- [Maintain products in Finance and Operations and sync them to Sales](products-template-mapping.md)
- [Create sales quotes in Sales and sync them to Finance and Operations](sales-quotation-template-mapping.md)
- [Create sales orders in Finance and Operations and sync them to Sales](sales-order-template-mapping.md)
- [Create sales invoices in Finance and Operations and sync them to Sales](sales-invoice-template-mapping.md)

## System requirements for Finance and Operations

To use the Prospect to cash solution, you must install the following components:

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) with platform update 8 (application build 7.2.11792.56024 with platform build 7.0.4565.16212)
- The following hotfixes for Finance and Operations:

    - **[KB4045570](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4045570&bugId=3851320&qc=ac1145034fd04ab71ccc4d14aa012f245176712c9af7c36bb77a118726d46160)** – This hotfix enables sales order synchronization from Sales to Finance and Operations via the Data Integration feature. It also provides several other enhancements.
    - **[KB4036524](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036524&bugId=3847504&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2)** – This hotfix enables sales order line synchronization from Finance and Operations to Sales via the Data Integration feature.
    - **[KB4036461](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036461&bugId=3847029&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2)** – This hotfix enables sales order synchronization from Finance and Operations to Sales via the Data Integration feature.

    > [!NOTE]
    > You only have to install KB4045570, because the installation includes the changes from the other Microsoft Knowledge Base (KB) articles.

## System requirements for Sales

To use the Prospect to cash solution, you must install the following components:

- Microsoft Dynamics 365 for Sales version 1612 (8.2.1.207) (DB 8.2.1.207) online
- Prospect to cash solution for Microsoft Dynamics 365 for Sales, version 1.14.0.0 (v14) or later

### Install the Prospect to cash solution for Sales

1. Download the [Prospect to cash for Dynamics 365 for Sales solution package zip file](https://mbs.microsoft.com/customersource/Global/365Enterprise/downloads/product-releases/MD365FNOPENTProspectToCash) from CustomerSource.
2. Make sure that the zip file is unblocked. Otherwise, when you try to install the solution package, you receive the following error message: "No import packages were found." To unblock the zip file, right-click it, and select **Properties**. Then select **Unblock**.
3. Unzip and run **PackageDeployer.exe**.
4. Install the Prospect to cash solution on your Sales instance:

    1. Select **Office 365** as the deployment type.
    2. Select **Show advanced**.
    3. For a quick installation, select a region. If you select **Don't know**, the system searches for all regions, and the installation will take more time.
    4. Enter the user name and password of an admin user who has installation rights.
