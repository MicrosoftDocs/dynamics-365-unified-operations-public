---
title: Set up the transfer documents for goods movement inside a company
description: This procedure shows how to set up transfer documents for goods movement inside a company.
author: AdamTrukawka
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: InventTransferOrders, InventLocationIdLookup, TransportationDocument, HcmWorkerLookUp, SrsReportViewerForm, InventTransferParmShip
---
# Set up the transfer documents for goods movement inside a company

[!include [banner](../../includes/banner.md)]

This procedure shows how to create transfer documents for goods movement inside a company. This procedure is only available for legal entities with a primary address in Lithuania. 
The procedure was created using the demo data company DEMF with a primary address in Lithuania. Before you can complete this procedure, you must complete the "Set up transfer documents for goods movement inside a company" procedure. 
This procedure is intended for inventory accountants. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Create a transfer order
1. Go to Inventory management > Inbound orders > Transfer order.
2. Click New.
3. In the From warehouse field, enter or select a value.
4. In the To warehouse field, enter or select a value.
5. Click Add.
6. In the list, mark the selected row.
7. In the Item number field, enter or select a value.

## Enter transportation details for the transfer order
1. Click Save.
2. On the Action Pane, click Ship.
3. Click Transportation details.
4. Select Yes in the Print transportation details field.
5. In the Goods issued by field, enter or select a value.
6. In the Package field, type a value.
7. In the Risk level of the load field, type a value.
8. In the Carrier field, enter or select a value.
9. In the Model field, enter or select a value.
10. In the Registration number field, type a value.
11. In the Trailer registration number field, type a value.
12. In the Driver field, enter or select a value.
13. In the Driver name field, type a value.
14. Click Save.
15. Close the page.

## View the packing slip for the unposted transfer order
1. Click Packing slip.
2. Click OK.
3. Close the page.

## View the packing slip for the posted transfer order
1. On the Action Pane, click Transfer order.
2. On the Action Pane, click Ship.
3. Click Ship transfer order.
4. Click the General tab.
5. In the Update field, select an option.
6. Click the Overview tab.
7. In the Packing slip field, type a value.
8. Click OK.
9. On the Action Pane, click Ship.
10. Click Packing slip.
11. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
