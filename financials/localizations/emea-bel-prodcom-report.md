---
# required metadata

title: Set up and maintain PRODCOM
description: This topic explains how to set up and maintain PRODCOM in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: IntrastatToProdcom, InventProdComLineDetail, InventProdComLineWithCode, InventProdComParameters, InventProdComTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 264804
ms.search.region: Belgium
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up and maintain PRODCOM

[!include[banner](../includes/banner.md)]


This topic explains how to set up and maintain PRODCOM in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 

Manufacturers of industrial products are required to report the quantities and values of products sold, as well as employment data, to the Nationaal Instituut voor de Statistiek (NIS) in response to the routine PRODCOM survey. Most producers submit an itemized PRODCOM report to the NIS monthly, using one of six standard report formats. The NIS determines the report layout, depending on the nature of the materials produced. The PRODCOM report displays production statistics for industrial products that are manufactured by production companies operating in Belgium. This report is typically used by accounting managers and accountants.

## Set up PRODCOM reporting
Before you can generate the PRODCOM report, you must set up the following on the **PRODCOM parameters** page.

1.  Enter a primary contact ID. This is the identification that is printed under the primary contact information section of the PRODCOM declaration.
2.  Enter an external contact ID - This is the identification that is printed under the external contact information section of the PRODCOM declaration.
3.  Select a company or warehouse.
    -   If the local branch is **Company**, the branch number of the company is transferred to the PRODCOM lines.
    -   If the local branch is **Warehouse**, the branch number of the warehouse where the sale took place is transferred to the PRODCOM lines.
    -   If the warehouse does not have a branch number, the branch number of the company is used.

4.  Specify an automatic recalculation preference.
5.  Set up number sequences.
6.  Specify the branch ID for Legal entity or Warehouses. For more information about the branch ID of Legal entity processing, including required prerequisites, see [Registration IDs](emea-registration-ids.md).

## Assign PRODCOM properties to an item
Assign PRODCOM properties to an item (**Product information management** &gt; **Products** &gt; **Released products**). Open the **Released product details** page, in the **Foreign trade** section, open the PRODCOM dialog box and provide the following details.

-   **Product made in company** - Select this check box to report quantities and values of products that were delivered by companies.****
-   **Delivery to a third party** - Select this check box to report quantities and values of products that were delivered by third parties.
-   **Work done for** **enterprises** - Select this check box to report quantities and values of products that were delivered by enterprises.****

After you've set up PRODCOM, you can use the **PRODCOM** page to create PRODCOM periods and transfer sales lines to the PRODCOM report.

## Convert Intrastat to PRODCOM
Use the **Intrastat to PRODCOM conversion** page to assign PRODCOM codes to Intrastat commodity codes. These codes can change every year. On the **Intrastat to PRODCOM conversion** page, click **Import PRODCOM data** to import the information.

## Use PRODCOM
Use the **PRODCOM** page to create PRODCOM periods and transfer sales lines to the PRODCOM report. After you enter the dates for the declaration period and then enter the section codes, you can transfer the sales lines to the PRODCOM report. After you transfer the sales lines to the report, you can review and edit the products on the PRODCOM list, and then you can print the report.



