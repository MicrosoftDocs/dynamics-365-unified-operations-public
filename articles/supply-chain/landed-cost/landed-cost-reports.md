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

## Expected delivery report

The expected delivery report contains basic information regarding the voyage, shipping container, folio and items and the expected due date of delivery.

The expected delivery report is used by navigating to _Landed cost \> Reports \> Tracking \> Expected Delivery._

The following parameters determine what information is populated on the report output.

| Setting | Description |
| --- | --- |
| **Expected date** | The expected date of delivery of the goods to the final destination warehouse. Any voyage line that has an expected date of this date or prior that has not been received will appear in the output. |
| **Vendor account** | Filter the report output by selecting the vendor associated to the voyage line. |
| **Records to include** | Standard Supply Chain Management filter that allows users to further limit the data output of the report. |

Run the expected delivery report:

1. Enter expected date.
1. Enter vendor account (Optional).
1. Select **Records to include \> Filter** to specify the search criteria if required.
1. Select **OK**.

## Voyage costing report

The Landed cost report displays the cost of the item and the import costs per folio, shipping container, or voyage, depending on the criteria specified when the report is running. The voyage costing report will allow users to see the estimate costs of the voyage versus the actua cost of the voyage and can be broken down by the several identifying factors

The costing report can be used by navigating to **Landed cost \> Reports \> Costing \> Voyage Costing**.

Run the shipment costing report:

1. **Report views** :

    - **Individual cost** : The individual cost option will display import costs per cost area per cost type code.
    - **Reporting category** : When the &#39;reporting categories&#39; option is selected to run the report, the import cost will be broken down into the different reporting categories. Cost types are grouped by reporting categories.

1. **Cost** : It is possible to view the report at the different stages of the import process.

    - **Cost value** : This is the value that is either calculated using auto cost or manually created on the cost area.
    - **Estimated** : Once the goods have been received the estimated cost is populated.
    - **Actual** : After the order has been invoiced, the actual cost field is populated with the cost on the invoice.
    - **Best (Recommended)**: When best is selected Dynamics 365 Finance and Operations, Enterprise Edition will use the most accurate value of the ones above.

1. **Per item** : When ticked will show the cost of an individual item.
1. **View** : Specify how the cost must be broken down, by ticking the cost areas that must show on the report.

## Outstanding invoices

The outstanding invoice report contains a list of all outstanding invoices of the various cost levels that are associated to every voyage. Once an overhead cost has been invoiced, it is removed from the outstanding invoices report. The outstanding invoices report is used to reconcile the voyage and voyage costs along with the ledger transactions list on a regular basis. Depending on the filters set on the outstanding invoices parameters, different can be viewed.

The outstanding invoices report can be used by navigating to _Landed cost \> Reports \> Outstanding invoices._

Run the outstanding invoices report:

1. Select the **as at date**.
1. Select which un **-invoiced transactions** to view.
    - **All not invoiced** lists the results of both **cost not invoiced** and **stock not invoiced**.
    - **Cost not invoiced** lists costs for invoiced shipments with an estimated cost value, but no actual cost.
    - **Stock not invoiced** lists costs that have been invoiced, but where the purchase order is yet to be received.
1. Select to **include/exclude new costs**. This allows the inclusion of costs which do not yet have an actual cost and have also not had inventory received.
1. Select the level at which to **view** the information.
1. Select the **records to include \> filter** to specify the search criteria.
1. Select **OK**.

## Shipping container receipts list

The shipping container receipts list report contains all unreceived quantities due on or before an expected date. The shipping containers receipts list can be used by the warehouse staff to identify the expected goods on a shipping container, and can be used to manually validate goods as they are received on a shipping container.

The shipping container receipts list can be printed and used by navigating to _Landed cost \> Reports \> Tracking \> Shipping container receipts list._

Run the container receipts list report:

1. Select the **expected date**.
1. Select the **records to include \> filter** to specify the search criteria.
1. Select **OK**.
