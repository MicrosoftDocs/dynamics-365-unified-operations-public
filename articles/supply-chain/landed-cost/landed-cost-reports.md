---
# required metadata

title: Landed cost reports
description: This topic describes how to find and use the various types of reports available for the Landed cost module.
author: RichardLuan
manager: tfehr
ms.date: 02/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2021-02-21
ms.dyn365.ops.version: Release 10.0.17
---

# Landed cost reports

[!include [banner](../includes/banner.md)]

## Outstanding invoices

The outstanding invoices report contains a list of all outstanding invoices of the various cost levels that are associated to every voyage. Once an overhead cost has been invoiced, it is removed from the outstanding invoices report. The outstanding invoices report is used to reconcile the voyage and voyage costs along with the ledger transactions list on a regular basis.

To generate an outstanding invoices report:

1. Go to **Landed cost \> Reports \> Tracking \> Outstanding invoices**.
1. The **Outstanding invoices** dialog box opens.
1. Set an **As at date**. Any invoice that was outstanding as of this date or earlier will be included in the output.
1. Select one of the following option under **Show**:
    - **Cost not invoiced** includes costs for invoiced shipments with an estimated cost value, but no actual cost.
    - **Stock not invoiced** includes costs that have been invoiced, but where the purchase order is yet to be received.
    - **All not invoiced** includes the results of both **cost not invoiced** and **stock not invoiced**.
1. Set **Include new costs** to *Yes* to include costs that don't yet have an actual cost and that also haven't had inventory received. <!-- KFM: What if I choose "no"? -->
1. In the **View** section, <!-- KFM: Explanation needed. -->
1. As with other types of reports in Supply Chain Management, use the **Destination** FastTab to choose the output format of the report.
1. As with other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records included in the report.
1. Select **OK** to generate the report.

## Activity/provider analysis reports

<!-- KFM: Intro needed -->.

To generate an activity/provider analysis report:

1. Depending on which type of report you'd like to create, choose one of the following from the navigator:
    - **Landed cost \> Reports \> Analysis of activity/provider by activity** - <!-- KFM: documentation needed -->.
    - **Landed cost \> Reports \> Analysis of activity/provider by provider** - <!-- KFM: documentation needed -->.
1. Depending on which option you chose, either the **Analysis of activity/provider by activity** or **Analysis of activity/provider by provider** dialog box opens. Each of these provides the same options from now on.
1. As with other types of reports in Supply Chain Management, use the **Destination** FastTab to choose the output format of the report.
1. As with other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records included in the report.
1. Select **OK** to generate the report.

## Voyage costing reports

The voyage costing reports display the cost of the items and the import costs per folio, shipping container, or voyage, depending on the options you choose when you generate the report. Each voyage costing report lets you see the estimated versus the actual cost of a voyage and can be broken down by the several identifying factors.

To generate a voyage costing report:

1. Depending on which type of voyage costing report you'd like to create, choose one of the following from the navigator:
    - **Landed cost \> Reports \> Costing \> Voyage costing by individual cost** - The individual cost option will display import costs per cost area per cost type code.
    - **Landed cost \> Reports \> Costing \> Voyage costing by reporting category** - The import cost will be broken down into the various reporting categories. Cost types are grouped by reporting categories.
1. Depending on which option you chose, either the **Voyage costing by individual cost** or **Voyage costing by reporting category** dialog box opens. Each of these is similar except as noted in the rest of this procedure
1. If you opened the **Voyage costing by reporting category**, then choose one of the following values from the **Cost** drop-down list:
    - **Cost value** : This is the value that is either calculated using auto cost or manually created on the cost area.
    - **Estimated** : Once the goods have been received, the estimated cost is populated.
    - **Actual** : After the order has been invoiced, the actual cost is populated with the cost on the invoice.
    - **Best**: The system will use the most accurate of the options available here (recommended).
1. Set **Per item** to *Yes* to show the cost of each individual item. <!-- KFM: What if I choose "no"? --> 
1. In the **View** section, choose the categories by which to break down the cost.
1. In the **Dimensions** section, choose which dimensions to include in the report.
1. As with other types of reports in Supply Chain Management, use the **Destination** FastTab to choose the output format of the report.
1. As with other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records included in the report.
1. Select **OK** to generate the report.

## Shipping container receipts list

The shipping container receipts list report contains all unreceived quantities due on or before an expected date. The shipping containers receipts list can be used by the warehouse staff to identify the expected goods on a shipping container, and can be used to manually validate goods as they are received on a shipping container.

To generate a shipping container receipts list:

1. Go to **Landed cost \> Reports \> Tracking \> Shipping container receipts list**.
1. The **Shipping container receipts list** dialog box opens.
1. Set an **Expected date**. Any quantities unreceived as of this date or earlier will be included in the output.
1. In the **Dimensions** section, choose which dimensions to include in the report.
1. As with other types of reports in Supply Chain Management, use the **Destination** FastTab to choose the output format of the report.
1. As with other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records included in the report.
1. Select **OK** to generate the report.

## Expected delivery report

The expected delivery report contains basic information regarding the voyage, shipping container, folio, items, and expected due date of delivery.

To generate an expected delivery report:

1. Go to **Landed cost \> Reports \> Tracking \> Expected Delivery**.
1. The **Expected delivery** dialog box opens.
1. Select the **Expected date** of delivery of the goods to the final destination warehouse. Any voyage line that has an expected date of this date or earlier, and that has not yet been received, will be included in the output.
1. Optionally, select a **Vendor account** to only include deliveries from a specific vendor.
1. In the **Dimensions** section, choose which dimensions to include in the report.
1. As with other types of reports in Supply Chain Management, use the **Destination** FastTab to choose the output format of the report.
1. As with other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records included in the report.
1. Select **OK** to generate the report.
