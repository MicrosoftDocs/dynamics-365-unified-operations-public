---
title: Generate a transfer document for an internal inventory transfer
description: Learn how to create transfer documents for goods movement inside a company in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/04/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: InventTransferOrders, InventLocationIdLookup, TransportationDocument, HcmWorkerLookUp, SrsReportViewerForm, InventTransferParmShip
---

# Generate a transfer document for an internal inventory transfer

[!include [banner](../../includes/banner.md)]

This article explains how to create transfer documents for goods movement inside a company in Microsoft Dynamics 365 Finance.

The following procedures intended for inventory accountants show how to create transfer documents for goods movement inside a company. The procedures are only available for legal entities with a primary address in Lithuania, and were created using the demo data company DEMF with a primary address in Lithuania. 

Before you can complete the procedures, you first must complete the procedures in [Set up transfer documents for goods movement inside a company](set-up-transfer-documents-goods-movement-inside-company.md).


## Create a transfer order

To create a transfer order, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management \> Inbound orders \> Transfer order**.
1. Select **New**.
1. In the **From warehouse** field, enter or select a value.
1. In the **To warehouse** field, enter or select a value.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.

## Enter transportation details for the transfer order

To enter transportation details for the transfer order, follow these steps.

1. Select **Save**.
1. On the Action Pane, select **Ship**.
1. Select **Transportation details**.
1. In the **Print transportation details** field, select **Yes**.
1. In the **Goods issued by** field, enter or select a value.
1. In the **Package** field, enter a value.
1. In the **Risk level of the load** field, enter a value.
1. In the **Carrier** field, enter or select a value.
1. In the **Model** field, enter or select a value.
1. In the **Registration number** field, enter a value.
1. In the **Trailer registration number** field, enter a value.
1. In the **Driver** field, enter or select a value.
1. In the **Driver name** field, enter a value.
1. Select **Save**.
1. Close the page.

## View the packing slip for the unposted transfer order

To view the packing slip for the unposted transfer order, follow these steps.

1. Select **Packing slip**.
1. Select **OK**.
1. Close the page.

## View the packing slip for the posted transfer order

To , follow these steps.

1. On the Action Pane, select **Transfer order**.
1. On the Action Pane, select **Ship**.
1. Select **Ship** transfer order.
1. Select the **General** tab.
1. In the **Update** field, select an option.
1. Select the **Overview** tab.
1. In the **Packing slip** field, enter a value.
1. Select **OK**.
1. On the Action Pane, select **Ship**.
1. Select **Packing slip**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
