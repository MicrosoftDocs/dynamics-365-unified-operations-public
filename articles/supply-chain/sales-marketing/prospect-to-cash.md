---
# required metadata

title: Prospect to cash
description: This topic provides an overview of the Prospect to cash solution between Microsoft Dynamics 365 for Finance and Operations, and Microsoft Dynamics 365 for Sales. 
author: ChristianRytt 
manager: AnnBe
ms.date: 04/25/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustTable, SalesTable, EcoResProductListPage
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.version: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Prospect to cash

[!include [banner](../includes/banner.md)]

The Prospect to cash solution provides direct synchronization across Dynamics 365 for Finance and Operations, and Dynamics 365 for Sales. The Prospect to cash templates that are available with the Data Integration feature enable the flow of data for accounts, contacts, products, sales quotations, sales orders, and sales invoices between Finance and Operations and Sales. While data is flowing between Finance and Operations and Sales, you can perform sales and marketing activities in Sales, and you can handle order fulfillment by using inventory management in Finance and Operations. 

For more information about the Prospect to cash integration, watch the short YouTube video:

[![](https://img.youtube.com/vi/AVV9x5x-XCg/0.jpg)](https://www.youtube.com/watch?v=AVV9x5x-XCg) 

In the current version, the Prospect to cash solution provides the following types of direct synchronization:

- [Maintain accounts in Sales and sync them directly from Sales to Finance and Operations](accounts-template-mapping-direct.md)
- [Maintain products in Finance and Operations and sync them directly to Sales](products-template-mapping-direct.md)
- [Maintain contacts in Sales and sync them directly to contacts or customers in Finance and Operations](contacts-template-mapping-direct.md)
- [Synchronize sales quotation directly from Sales to Finance and Operations](sales-quotation-template-mapping-sales-fin.md)
- [Synchronize sales orders directly between Sales and Finance and Operations](sales-order-template-mapping-direct-two-ways.md)
- [Synchronize sales invoice directly from Finance and Operations to Sales](sales-invoice-template-mapping-direct.md)

## System requirements for Finance and Operations
Prospect to cash integration is supported on the following versions:

### Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3 (December 2017)

- Dynamics 365 for Finance and Operations, Enterprise edition (December 2017) - Application build 7.3.11971.56116 with Platform Update 12 (7.0.4709.41129)

### Dynamics 365 for Finance and Operations, Enterprise edition (July 2017)

- Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) - with platform update 8 (application build 7.2.11792.56024 with platform build 7.0.4565.16212).
- The following hotfixes are required:

  - **[KB4045570](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4045570&bugId=3851320&qc=ac1145034fd04ab71ccc4d14aa012f245176712c9af7c36bb77a118726d46160)** – This hotfix enables sales order synchronization from Sales to Finance and Operations via the Data Integration feature. It also provides several other enhancements.
  - **[KB4036524](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036524&bugId=3847504&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2)** – This hotfix enables sales order line synchronization from Finance and Operations to Sales via the Data Integration feature.
  - **[KB4036461](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4036461&bugId=3847029&qc=e2fcfae08b1a5d5ce9f53f330e8c212b0636c375368ff7d8d9b5ec6701523ad2)** – This hotfix enables sales order synchronization from Finance and Operations to Sales via the Data Integration feature.

    > [!NOTE]
    > You only have to install KB4045570 because the installation includes the changes from other hotfixes. 

### Dynamics 365 for Finance and Operations version 1611 (November 2016)

- Dynamics 365 for Finance and Operations version 1611 (November 2016)  with platform update 8 or higher

- The following hotfixes are required:

  - **[KB4051266](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4051266&bugId=3863566&qc=ee80faaa7bc6c77b368d5eaf456c9c08e0b9fba5903a7b6fd8c13756c3a4b757)** - Enable sales order synchronization with Data integrator from Finance and Operations to Sales. 
  - **[KB4037542](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4037542&bugId=3848253&qc=8323b93c15280172c5ab4159e0256e37104ced1729462c91ab2f7d00cb8d419c)** - Enable sales order header and line synchronization with Data integrator from Finance and Operations to Sales.
  - **[KB4033093](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4033093&bugId=3824604&qc=bd7e15e1fb56066b3a82ce48b691cf1ffbc934a7473fa888545b2211a8d416c5)** - Support for prospect to cash integration through data entities is required.
    
    > [!NOTE]
    > After you install the hotfixes, you must trigger the following batch job from the **SalesPopulateProspectToCash** form. This form is hidden because you only need it once. To access the form, log in to the environment and add the following to the URL in your browser address: *&mi=action:SalesPopulateProspectToCash*, for example, `https://ax123456.cloud.test.dynamics.com/?cmp=USMF&mi=action:SalesPopulateProspectToCash`. When the form opens, click OK. This will populate a new **LineCreationSequnceNumber** field in the **SalesLine**, **SalesQuotationLine**, and **CustInvoiceTrans** tables with unique values, and the product list will be refreshed. This is required for the Prospect to cash integration to work.


## System requirements for Sales

To use the Prospect to cash solution, you must install the following components:

- Dynamics 365 for Sales version 1612 (8.2.1.207) (DB 8.2.1.207) online or a later version
- Prospect to cash solution for Dynamics 365 for Sales, version 1.15.0.0 or a later version. The solution is available for download from AppSource. [Download Dynamics 365, Prospect to Cash](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.c7a48b40-eed3-4d67-93ba-f2364281feb3).
