---
title: EUR-00002 Specify a lading address for an intracommunity transaction
description: Learn how to specify a lading address for an intracommunity trade transaction with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - PurchTable, PurchCreateOrder, InventItemIdLookupPurchase, TransportationDocument, LogisticsPostalAddress, SysLookupMultiSelectGrid
  - VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, Intrastat, SysQueryForm
---
# EUR-00002 Specify a lading address for an intracommunity transaction

[!include [banner](../../includes/banner.md)]

This article explains how to specify a lading address for an intra-community trade transaction with Microsoft Dynamics 365 Finance.

The following procedure shows how to specify a lading address for an intra-community trade transaction. For example, a Germany company orders items from a vendor with a German business address. This vendor has a warehouse in Italy and ships the items from there. This delivery must be reported in the Intrastat. The same behavior is valid for customer returns.
This procedure applies to all European countries/regions.

Before you can complete the procedure, you must configure Intrastat reporting. The procedure is intended for accountants.

The following procedure uses the was created using the demo data company DEMF with a primary address in Germany.

To specify a lading address for an intracommunity transaction, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. Enter or select a value. For example, select **DE-001**. This vendor has a German business address.  
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value. For example, enter "D0001".
1. Select **Save**.
1. On the Action Pane, select **Receive**.
1. Select **Transportation details**.
1. In the **Loading date and time** field, enter a date and time.
1. Select **Add address**.
1. Select **New** and create new address.
1. In the **Name or description** field, enter "Italian".
1. Select **Lading** as the value. The address purpose must be **Lading**.  
1. In the **Country/region** field, enter or select a value. For example, enter "ITA".
1. Select **Save**.
1. Close the page.
1. Select **Save**. Verify that the lading address is correct.  
1. Close the page.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. In the **Number** field, enter a number.
1. In the **Invoice date** field, enter a date.
1. Select **Default from: Product receipt quantity** to open the drop dialog.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Select **OK**.
1. Select **Transportation details**. Verify that goods were shipped from Italy. If necessary, you can edit the lading details.  
1. Close the page.
1. Select **Post**.
1. Close the page.
1. Go to **Tax \> Declarations \> Foreign trade \> Intrastat**.
1. Select **Transfer**.
1. In the **Vendor invoice** field, select **Yes**.
1. Select **OK**.
1. Select the **General** tab.
1. Find a newly created line and verify that the sender shipped the goods from Italy.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
