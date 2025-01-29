---
title: Landed cost reports
description: Learn how to find and use the various types of reports that are available for the Landed cost module, including a step-by-step process.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 02/01/2021
ms.custom:
ms.reviewer: kamaybac
ms.search.form: SysOperationTemplateForm
---

# Landed cost reports

[!include [banner](../../includes/banner.md)]

## Outstanding invoices

The outstanding invoices report contains a list of all outstanding invoices of the various cost levels that are associated with every voyage. It's used to reconcile the voyage and voyage costs together with the ledger transactions list on a regular basis. After an overhead cost has been invoiced, it's removed from the report.

To generate an outstanding invoices report, follow these steps.

1. Go to **Landed cost \> Reports \> Tracking \> Outstanding invoices**.
1. In the **Outstanding invoices** dialog box, in the **As at date** field, specify a date. Any invoice that was outstanding on or before that date will be included in the output.
1. Under **Show**, select one of the following options:

    - **Cost not invoiced** – Include costs for invoiced shipments that have an estimated cost value but no actual cost.
    - **Stock not invoiced** – Include costs that have been invoiced, but that the purchase order hasn't yet been received for.
    - **All not invoiced** – Include the results of both the **Cost not invoiced** option and the **Stock not invoiced** option.

1. Set the **Include new costs** option to *Yes* to include costs that don't yet have an actual cost, and that inventory hasn't been received for. If you set it to *No*, the report will include only costs that have been invoiced.
1. In the **View** section, enable each type of detail that you want to include on the report.
1. As you do for other types of reports in Microsoft Dynamics 365 Supply Chain Management, use the **Destination** FastTab to select the output format of the report.
1. As you do for other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records that will be included on the report.
1. Select **OK** to generate the report.

## Activity/provider analysis reports

The activity/provider analysis reports let you review the accuracy of your time estimates for each provider.

To generate an activity/provider analysis report, follow these steps.

1. Depending on the type of report that you want to create, follow one of these steps:

    - Go to **Landed cost \> Reports \> Analysis of activity/provider by activity**. In this case, the time estimates will be grouped by activity.
    - Go to **Landed cost \> Reports \> Analysis of activity/provider by provider**. In this case, the time estimates will be grouped by provider.

    Either the **Analysis of activity/provider by activity** dialog box or the **Analysis of activity/provider by provider** dialog box appears. Both dialog boxes provide the same options.

1. As you do for other types of reports in Supply Chain Management, use the **Destination** FastTab to select the output format of the report.
1. As you do for other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records that will be included on the report.
1. Select **OK** to generate the report.

## Voyage costing reports

The voyage costing reports show the cost of the items and the import costs per folio, shipping container, or voyage, depending on the options that you select when you generate the report. Each voyage costing report lets you view the estimated cost of a voyage versus the actual cost, and it can be broken down by the several identifying factors.

To generate a voyage costing report, follow these steps.

1. Depending on the type of report that you want to create, follow one of these steps:

    - Go to **Landed cost \> Reports \> Costing \> Voyage costing by individual cost**. In this case, the individual cost option will show import costs per cost area per cost type code.
    - Go to **Landed cost \> Reports \> Costing \> Voyage costing by reporting category**. In this case, the import cost will be broken down into the various reporting categories. Cost types are grouped by reporting categories.

    Either the **Voyage costing by individual cost** dialog box or the **Voyage costing by reporting category** dialog box appears. These dialog boxes are similar. Any differences are noted in the rest of this procedure.

1. If you opened the **Voyage costing by reporting category** dialog box, in the **Cost** field, select one of the following values:

    - **Cost value** – The value is either calculated by using auto costs or manually created in the cost area.
    - **Estimated** – After the goods have been received, the estimated cost is set.
    - **Actual** – After the order has been invoiced, the actual cost is set to the cost on the invoice.
    - **Best** – The system will use whichever of the previous three options is most accurate. (We recommend that you select this option.)

1. Set the **Per item** option to *Yes* to show the cost of each item. Set it to *No* to show costs per voyage.
1. In the **View** section, select the categories to break down the cost by.
1. In the **Dimensions** section, select the dimensions to include on the report.
1. As you do for other types of reports in Supply Chain Management, use the **Destination** FastTab to select the output format of the report.
1. As you do for other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records that will be included on the report.
1. Select **OK** to generate the report.

## Shipping container receipts list

The shipping container receipts list contains all unreceived quantities that are due on or before an expected date. Warehouse staff can use this report to identify the expected goods on a shipping container. It can also be used to manually validate goods as they are received on a shipping container.

To generate a shipping container receipts list, follow these steps.

1. Go to **Landed cost \> Reports \> Tracking \> Shipping container receipts list**.
1. In the **Shipping container receipts list** dialog box, in the **Expected date** field, specify a date. Any quantities that were unreceived on or before that date will be included in the output.
1. In the **Dimensions** section, select the dimensions to include on the report.
1. As you do for other types of reports in Supply Chain Management, use the **Destination** FastTab to select the output format of the report.
1. As you do for other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records that will be included on the report.
1. Select **OK** to generate the report.

## Expected delivery report

The expected delivery report contains basic information about the voyage, shipping container, folio, items, and expected date of delivery.

To generate an expected delivery report, follow these steps.

1. Go to **Landed cost \> Reports \> Tracking \> Expected Delivery**.
1. In the **Expected delivery** dialog box, in the **Expected date** field, select the date when delivery of the goods to the final destination warehouse is expected. Any voyage line that has an expected date on or before that date, and that hasn't yet been received, will be included in the output.
1. Optional: In the **Vendor account** field, select a vendor account to include only deliveries from a specific vendor.
1. In the **Dimensions** section, select the dimensions to include on the report.
1. As you do for other types of reports in Supply Chain Management, use the **Destination** FastTab to select the output format of the report.
1. As you do for other types of reports in Supply Chain Management, use the **Records to include** FastTab to further limit the records that will be included on the report.
1. Select **OK** to generate the report.
