---
# required metadata

title: Vendor invoice entry workspace
description: This topic describes the workspace that's related to vendor invoices and that takes advantage of the capabilities available through Power BI.
author: abruer
manager: AnnBe
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2020-09-21
ms.dyn365.ops.version: 10.0.14
---



# Vendor invoice entry workspace

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the workspace that's related to vendor invoices and that takes advantage of the capabilities available through Power BI. The workspace displays information about vendor invoices that's filtered for specific users in a graphical format.

The **Vendor invoice entry** workspace shows information that's related to 
 vendor invoice processing. This workspace includes a **My work** view and
an **Analytics - all companies** page. The **My work** view shows summary tiles, vendor
transaction grids, and related vendor information. The **Analytics** page uses
the capabilities of Microsoft Power BI to show visuals that are related to
vendor invoices.

## Setup needed to view Power BI content

The following setup needs to be completed for data to display in **Vendor
invoice entry** Power BI visuals.

1.  Go to the **Feature management** workspace.

2.  Filter to find the **Vendor invoice automation** feature.

3.  Click on **Enable** button.

4.  To ensure that the invoice can be processed from start to finish without manual intervention, set up a vendor invoice workflow. To set up a workflow, go to **Accounts payable > Setup > Accounts payable workflows**.

5.  Go to **Accounts payable > Setup > Accounts payable parameters > Vendor
    invoice automation**. For more information, see [Setup options for vendor invoice automation](vnd-invoice-set-up-options.md).

6.  Set **Automatically submit imported invoices to workflow** to **Yes**.

7.  To **Match product receipts automatically**, set **Automatically match
    product receipts to invoices lines** to **Yes**.

8.  Review other settings per your desired system behavior.

9.  Go to **System administration > Setup > System Parameters** to
    set **System currency** and **System Exchange Rate**.

10.  Go to **General Ledger > Setup > Ledger** to set **Accounting
    Currency** and **Exchange Rate Type**.

11. Define exchange rates between Transaction currencies and Accounting
    currency, Accounting currency and System currency. To do this, go
    to **General Ledger > Currencies > Currency exchange rates**.

12. Go to **System administration > Setup > Entity Store** and look for
    **Vendor invoice automation measure.** Click the **Refresh** button.

13. Please note the users must have the security role accounts payable manager or clerk in
    order to view this information.

## My work view

### Company selection
When the **Automate vendor invoices** feature is enabled, you'll see a drop down menu to select a **Company**. By default, it will show
the information for the company that you logged into. You can select a different company to display information for that company on the tile.  Clicking on the tile will bring you to that related page in the company that you selected in the **Company** menu.

### Summary tiles
The tiles in the **Summary of pending invoices** section give an overview of the state of your vendor invoices. You can see journals that aren't yet posted,
invoices that are on hold, and four tiles associated with vendor invoice automation feature: **Manual receipt match needed**, **Matching validation not
successful**, **Invoices not submitted to workflow**, and **Invoices not imported**. These last four require the enabling of the feature in Feature
Management. To use the **Recover vendor invoices**, that must be enabled in Accounts payable \> Accounts payable parameters\> Invoice \> Allow vendor
invoice recovery. You will also see journals grouped together for **Vendor invoice journals**, **Journals- Assigned to me**, and **Invoice pool**.

The information in the **Summary** section is for the company set as the default for your login.

### Creating new records
Use the **New** dropdown menu to create a new invoice record using one of the
available options:

-   Vendor invoice

-   Invoice journal

-   Global invoice journal

-   Invoice register

-   Invoice approval

Please note that you will create a record based upon the company filter and not
the logged-in company. For example, if your logged-in company is UMSF, but your
filter company is GBSI, when you click New and make your selection, it will
create that record in GBSI.

### Documents not invoiced grids

The **Documents not invoiced** section contains grids that show documents
awaiting vendor invoices. From the **Open purchase orders** grid, you will see
all purchase orders that are not yet fully invoiced. Use **Invoice now** button
to create a vendor invoice for that purchase order. Use the **Prepayment invoice
now** button to create a prepayment invoice for that purchase order

The **Product receipts** grid shows purchase receipt transactions that are not
fully invoiced. Use **Invoice now** button to create a vendor invoice for that
purchase order.

The **Pending vendor invoices** grid shows all invoices not submitted to
workflow. Use the **Search** bar and/or the **Company** dropdown to search for a
particular vendor invoice. Use the **Edit** button to edit a transaction showing
in the grid.

On the **Find purchase order** grid, use the **Search** bar to search for a
purchase order.

### Related information

You can view **Posted invoices** information using the links on the right side
of the workspace, to include **Open vendor invoices**, **Invoice journal**, and
**Invoice history and matching details**. Under the Vendors section, you can
access a filtered list to show all **Vendors on hold** or use the **All
vendors** link. **All purchase orders** and **Open prepayments** links are also
available.

### Analytics – all companies page

When the **Automatically submit imported invoices to workflow** field is set to **Yes** on the **Accounts payable parameters** page, you can view automation analytics. The **Analytics-All companies** page provides important metrics, such as vendor invoices that are in approval by approver and by company. This page contains five report pages. One page provides an overview, and the other pages provide details about Accounts payable automation metrics.

The following table shows the visualizations that are available on each report
page.

|      Report page                      	|      Visualization                                    	|
|---------------------------------------	|-------------------------------------------------------	|
|     Vendor invoice overview           	|     Pending vendor invoices in   automation in system currency <br>     Invoices that failed to import  <br>    Invoices in workflow <br>     Touchless invoices last 30 days <br>     Total automated invoices last 30   days <br>     Balance of open invoices in   system currency <br>     Reasons for failures, last 30   days <br>     Percent of posted invoices that   were processed automatically <br>     Days to process an invoice    	|
|     Automation status                 	|     Touchless invoices last 30 days <br>     Touchless invoices last 30 days by company <br>     Touchless invoices last 30 days by vendor group <br>     Percent of posted invoices that were processed   automatically <br>     Days to process an invoice                                                                                                                                                                   	|
|     Invoices that failed to import    	|     Invoices that failed to import <br>     Invoices that failed to import   by company <br>                                                                                                                                                                                                                                                                                                                         	|
|     Reasons for automation failure    	|     Invoices failed <br>     Invoices failed by company <br>     Invoices failed by vendor group <br>                                                                                                                                                                                                                                                                                                                     	|
|     Workflow status                   	|     Invoices in workflow <br>     Vendor invoice workflow   instances <br>     Assignment per approver <br>     Vendor invoice workflow per   company <br>     Average days in workflow by   approver                                                                                                                                                                                                                          	|

