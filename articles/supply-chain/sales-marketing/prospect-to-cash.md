---
# required metadata

title: Prospect to cash
description: This topic provides an overview of the Prospect to cash solution between Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, and Microsoft Dynamics 365 for Sales. 
author: ChristianRytt 
manager: AnnBe
ms.date: 12/11/2017
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
- [Synchronize sales quotation directly from Sales to Finance and Operations](sales-quotation-template-mapping-sales-fin.md)
- [Synchronize sales orders directly from Finance and Operations to Sales](sales-order-template-mapping-direct.md)
- [Synchronize sales orders directly between Sales and Finance and Operations](sales-order-template-mapping-direct-two-ways.md)
- [Synchronize sales invoice directly from Finance and Operations to Sales](sales-invoice-template-mapping-direct.md)

In earlier versions, the Prospect to cash solution provides the following types of non-direct synchronization:

- [Maintain accounts in Sales and sync them to Finance and Operations](accounts-template-mapping.md)
- [Maintain contacts in Sales and sync them to Finance and Operations](contacts-template-mapping.md)
- [Maintain products in Finance and Operations and sync them to Sales](products-template-mapping.md)
- [Create sales quotes in Sales and sync them to Finance and Operations](sales-quotation-template-mapping.md)
- [Create sales orders in Finance and Operations and sync them to Sales](sales-order-template-mapping.md)
- [Create sales invoices in Finance and Operations and sync them to Sales](sales-invoice-template-mapping.md)

## System requirements for Finance and Operations

To use the Prospect to cash solution, you must install the following components:

### July 2017 

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) with platform update 8 (application build 7.2.11792.56024 with platform build 7.0.4565.16212)
- The following hotfixes for Finance and Operations:

    - **[KB4045570](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4045570&bugId=3851320&qc=ac1145034fd04ab71ccc4d14aa012f245176712c9af7c36bb77a118726d46160)** – This hotfix enables sales order synchronization from Sales to Finance and Operations via the Data Integration feature. It also provides several other enhancements.
    - **[KB4036524](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036524&bugId=3847504&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2)** – This hotfix enables sales order line synchronization from Finance and Operations to Sales via the Data Integration feature.
    - **[KB4036461](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036461&bugId=3847029&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2)** – This hotfix enables sales order synchronization from Finance and Operations to Sales via the Data Integration feature.

    > [!NOTE]
    > You only have to install KB4045570 because the installation includes the changes from other hotfixes. 

### November 2016 (Version 1611)

- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (November 2016) with platform update 8 or higher

- The following hotfixes for Finance and Operations:

    - **[KB4051266](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4051266&bugId=3863566&qc=ee80faaa7bc6c77b368d5eaf456c9c08e0b9fba5903a7b6fd8c13756c3a4b757)** - Enable sales order synchronization with Data integrator from Microsoft Dynamics 365 for Finance and Operations to Sales 
    - **[KB4037542](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4037542&bugId=3848253&qc=8323b93c15280172c5ab4159e0256e37104ced1729462c91ab2f7d00cb8d419c)** - Enable sales order header and line synchronization with Data integrator from Microsoft Dynamics 365 for Finance and Operations to Sales
    - **[KB4033093](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4033093&bugId=3824604&qc=bd7e15e1fb56066b3a82ce48b691cf1ffbc934a7473fa888545b2211a8d416c5)** - Support for prospect to cash integration through data entities is required
    
    > [!NOTE]
    > After installing the hotfixes you have to trigger the following batch job from the form SalesPopulateProspectToCash. This form is hidden as you only need it once. To access the form log in to the environment and add the following to the url in your brower address: &mi=action:SalesPopulateProspectToCash  e.g. https://ax123456.cloud.test.dynamics.com/?cmp=USMF&mi=action:SalesPopulateProspectToCash. When the form opens, click OK. This will populate a new **LineCreationSequnceNumber** field in **SalesLine**, **SalesQuotationLine**, and **CustInvoiceTrans** tables with unique values, and the product list will be refreshed. This is required for the Prospect to cash integration to work.


## System requirements for Sales

To use the Prospect to cash solution, you must install the following components:

- Microsoft Dynamics 365 for Sales version 1612 (8.2.1.207) (DB 8.2.1.207) online
- Prospect to cash solution for Microsoft Dynamics 365 for Sales, version 1.15.0.0 (v15) 

   > [!NOTE]
   >
   > Templates with version 1.0.0.0 and 1.0.0.1 are supported on Prospect to cash solution for Microsoft Dynamics 365 for Sales, version 1.14.1.0
   >
   > Templates with version 2.0.0.0 and 2.1.0.0 are upported on Prospect to cash solution for Microsoft Dynamics 365 for Sales, version 1.15.0.0

### Install the Prospect to cash solution for Sales

1. Download the [Prospect to cash for Dynamics 365 for Sales solution package zip file](https://mbs.microsoft.com/customersource/Global/365Enterprise/downloads/product-releases/MD365FNOPENTProspectToCash) from CustomerSource.
2. Make sure that the zip file is unblocked. Otherwise, when you try to install the solution package, you receive the following error message: "No import packages were found." To unblock the zip file, right-click it, and select **Properties**. Then select **Unblock**.
3. Unzip and run **PackageDeployer.exe**.
4. Install the Prospect to cash solution on your Sales instance:

    1. Select **Office 365** as the deployment type.
    2. Select **Show advanced**.
    3. For a quick installation, select a region. If you select **Don't know**, the system searches for all regions, and the installation will take more time.
    4. Enter the user name and password of an admin user who has installation rights.
