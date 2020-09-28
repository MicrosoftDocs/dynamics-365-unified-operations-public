---
# required metadata

title: Vendor invoice entry workspace
description: This topic describes the capabilities that are available through Power BI to display information about vendor invoices that's filtered for specific users in a graphical format.
author: abruer
manager: AnnBe
ms.date: 09/21/2020
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
ms.author: shpandey
ms.search.validFrom: 2020-09-21
ms.dyn365.ops.version: 10.0.14
---



# Vendor invoice entry workspace

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the capabilities that are available through Power BI to display information about vendor invoices that's filtered for specific users in a graphical format.

Dynamics 365 for Finance and Operations has evolved into purpose-built
applications to help you manage specific business functions. For more
information about these changes, see [Dynamics 365 Licensing
Guide](https://go.microsoft.com/fwlink/?LinkId=866544).

The **Vendor invoice entry** workspace shows information that is related to the
processing of vendor invoices. This workspace includes a **My work** view and
an **Analytics** page. The **My work** view shows summary tiles, vendor
transaction grids, and related vendor information. The **Analytics** page uses
the capabilities of Microsoft Power BI to show visuals that are related to
vendor invoices.

## Setup needed to view Power BI content

The following setup needs to be completed for data to display in **Vendor
invoice entry** Power BI visuals.

1.  Go to the **Feature management** workspace.

2.  Filter to find the **Vendor invoice automation** feature.

3.  Click on **Enable** button.

4.  Go to **Accounts payable > Setup > Accounts payable parameters > Vendor
    invoice automation**.

5.  Set **Automatically submit imported invoices to workflow** = Yes.

6.  To **Match product receipts automatically**, set **Automatically match
    product receipts to invoices lines** = Yes.

7.  Review other settings per your desired system behavior.

8.  Go to **System administration > Setup > System Parameters** to
    set **System currency** and **System Exchange Rate**.

9.  Go to **General Ledger > Setup > Ledger** to set **Accounting
    Currency** and **Exchange Rate Type**.

10. Define exchange rates between Transaction currencies and Accounting
    currency, Accounting currency and System currency. To do this, go
    to **General Ledger > Currencies > Currency exchange rates**.

11. Go to **System administration > Setup > Entity Store** and look for
    **Vendor invoice automation measure.** Click the **Refresh** button.

12. Please note the users must have the security role AP Manager or AP Clerk in
    order to view this information.

## My work view

### Company selection

You will see a dropdown menu to select a **Company**. By default, it will show
you the information for the company in which you log in upon signing into D365.
By changing the dropdown, it will update the tile information to reflect that of
the newly selected company. Clicking on the tile will bring you to that form and
change your logged in company (as seen in the upper right hand corner) to that
of the one in the dropdown selection.

### Summary tiles

The tiles in the **Summary of pending invoices** section give an overview of the
state of your vendor invoices. You can see journals that aren't yet posted,
invoices that are on hold, and four tiles associated with vendor invoice
automation feature: **Manual receipt match needed**, **Matching validation not
successful**, **Invoices not submitted to workflow**, and **Invoices not
imported**. These last four require the enabling of the feature in Feature
Management. To use the **Recover vendor invoices**, that must be enabled in
Accounts payable \> Accounts payable parameters\> Invoice \> Allow vendor
invoice recovery. You will also see journals grouped together for **Vendor
invoice journals**, **Journals- Assigned to me**, and **Invoice pool**.

The information in the **Summary** section is for the company set as the default
for your login.

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

### Analytics page

The **Analytics-All companies** page provides important metrics, such as vendor
invoices that are in approval by approver and by company. This page contains two
report pages. One page provides an overview, and the second provides details on
workflow.

These reports are dependent upon the Vendor invoice automation feature being
enabled in Feature management.

The following table shows the visualizations that are available on each report
page.

| ANALYTICS PAGE                  |                                             |
|---------------------------------|---------------------------------------------|
| **Report page**                 | **Visualization**                           |
| Vendor invoice overview         | Pending vendor invoices in automation[^1]   |
| Workflow status                 | Invoices in workflow                        |
| Automation status               | Touchless invoices last 30 days (count)[^3] |
| Invoices that failed to import  | Invoices failed to import(count)            |
| Reasons for automation failures | Invoices failed                             |

[^1]: This value is calculated using the system currency.

-   Pending vendor invoices in automation (count)[^2]

[^2]: This is a count of all pending invoices in automation in any state.

-   Invoices that failed to import

-   Invoices in workflow

-   Touchless invoices last 30 days

-   Balance of open invoices in system currency

-   Reasons for failures, last 30 days

-   Percent of posted invoices that were processed automatically

-   Days to process an invoice

-   Vendor invoice workflow instances

-   Assignment per approver

-   Average days in workflow

-   Per company

[^3]: This metric will only display if the user has enabled “Automatically
submit imported invoice to workflow” In Feature management.

-   Total automated invoices last 30 days (count)

-   Touchless invoices last 30 days per company

-   Touchless invoices last 30 days per vendor group

-   Touchless invoices per company: Percent of posted invoices that were
    processed automatically

-   Touchless invoices per company: Days to process an invoice

-   Invoices failed by vendor

-   Reasons for failures, last 30 days

-   Invoices failed by company by company

-   Invoices failed by vendor
