---
title: Set up and maintain PRODCOM
description: Learn how to set up and maintain PRODCOM in Microsoft Dynamics 365 Finance, including an outline on assigning PRODCOM properties to an item.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/02/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Belgium
ms.search.validFrom: 2016-11-30
ms.search.form: IntrastatToProdcom, InventProdComLineDetail, InventProdComLineWithCode, InventProdComParameters, InventProdComTable
ms.dyn365.ops.version: Version 1611
---

# Set up and maintain PRODCOM

[!include [banner](../../includes/banner.md)]

This article explains how to set up and maintain PRODCOM. Manufacturers of industrial products must report the quantities and values of products sold, and employment data, to the Nationaal Instituut voor de Statistiek (NIS) in response to the routine PRODCOM survey. Most producers submit an itemized PRODCOM report to the NIS monthly, using one of six standard report formats. The NIS determines the report layout, depending on the nature of the materials produced. The PRODCOM report displays production statistics for industrial products that production companies operating in Belgium manufacture. Accounting managers and accountants typically use this report.

## Set up PRODCOM reporting

Before you generate the PRODCOM report, set up the PRODCOM parameters.

1. Go to **Tax** \> **Setup** \> **Foreign trade** \> **PRODCOM parameters**.
1. Enter a primary contact ID. The PRODCOM declaration prints this identifier in the section for primary contact information.
1. Enter an external contact ID. The PRODCOM declaration prints this identifier in the section for external contact information.
1. Select a company or warehouse:

    - If the local branch is **Company**, the branch number of the company is transferred to the PRODCOM lines.
    - If the local branch is **Warehouse**, the branch number of the warehouse where the sale took place is transferred to the PRODCOM lines.
    - If the warehouse doesn't have a branch number, the branch number of the company is used instead.

1. Specify an automatic recalculation preference.
1. Set up number sequences.
1. Specify the branch ID for the legal entity or warehouses. For more information about the branch ID for legal entity processing, including information about prerequisites, see [Registration IDs](../europe/emea-registration-ids.md).

## Assign PRODCOM properties to an item

1. Go to **Product information management** > **Products** > **Released products** to assign PRODCOM properties to an item. 
1. On the **Released product details** page, in the **Foreign trade** section, open the PRODCOM dialog box, and set the following fields:

    - **Product made in company** – Select this checkbox to report quantities and values of products that the company delivers.
    - **Delivery to a third party** – Select this checkbox to report quantities and values of products that third parties deliver.
    - **Work done for** **enterprises** – Select this checkbox to report quantities and values of products that enterprises deliver.

1. When you finish setting up PRODCOM, go to **Tax** > **Declarations** > **Foreign trade** > **PRODCOM** to create PRODCOM periods and transfer sales lines to the PRODCOM report.

## Convert Intrastat to PRODCOM

1. Go to **Tax** > **Setup** > **Foreign trade** > **Intrastat to PRODCOM conversion** to assign PRODCOM codes to Intrastat commodity codes. These codes can change every year.
1. On the **Intrastat to PRODCOM conversion** page, select **Import PRODCOM data** to import the information.

## Use PRODCOM
Use the **PRODCOM** page to create PRODCOM periods and transfer sales lines to the PRODCOM report. After you enter the dates for the declaration period and then enter the section codes, you can transfer the sales lines to the PRODCOM report. After you transfer the sales lines to the report, you can review and edit the products on the PRODCOM list, and then you can print the report.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
