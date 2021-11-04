---
title: You can't confirm a shipment because the customer is on hold
description: You can't confirm a shipment because the customer is on hold.
author: GalynaFedorova
ms.date: 07/30/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-07-30
ms.dyn365.ops.version: 10.0.21
---

# You can't confirm a shipment because the customer is on hold

Error code: WAX:CustomerOnHoldShipmentCannotBeConfirmed

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> Shipment %1 cannot be confirmed because customer is on hold for %2.

Therefore, you can't confirm the shipment for the load.

## Cause

The customer account of the load or shipment is on hold. Therefore, the customer's status prevents shipment confirmation.

## Resolution

Use the following procedure to unblock the customer account.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Open the customer account that the shipment can't be confirmed for.
1. On the **Credit and collections** FastTab, set the **Invoicing and delivery on hold** field to *No*.
1. Repeat this procedure for all blocked customers for the load.
