---
# required metadata

title: Product receipt against purchase orders
description: This article describes the various options for registering products as received.
author: FrankDahl
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: yuyus

ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail

# ms.tgt_pltfrm: 
ms.custom: 93113
ms.assetid: d4ec3e86-fce2-4546-911b-e0acf64c8887
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Product receipt against purchase orders

[!include[banner](../includes/banner.md)]

[!include[retail name](../includes/retail-name.md)]


This article describes the various options for registering products as received.

Product receipt is the process of recording that products that were ordered have been received, so that the purchase order (PO) lines can then be processed for invoicing. In some cases, products go through preregistration, where additional information from the supplier is recorded before the products are received. When products arrive, they are first marked as **Registered**. The products might then go through additional processes, such as quality management, before they are finally marked as **Received**.

## Preregistration (ASN)
Suppliers might share information about products that will be shipped. In this case, you can preregister the products to record this information before the products are received. By preregistering products, you reduce the amount of work that is required during item registration and receipt. Suppliers can provide product information electronically through an Advance Shipment Notice (ASN) that is then automatically recorded in the system. The information in the ASN includes the quantity of products that will be shipped and the date when they will be shipped. The ASN might also include information such as batch or serial numbers. Registration of the ASN occurs in the **Transportation management** module.

## Registration
Product receipt registration often occurs at the inbound docks in a warehouse. It’s performed either by using a hand-held device or through arrival journals. Alternatively, you can manually register product receipt by using the **Registration** action on the **Purchase order** page. In both cases, the products are marked as **Registered**. Note that the products aren’t yet marked as **Received**.  

Products that are received in a warehouse might go through quality inspection before they are put away into inventory. Either quality orders or quarantine orders can be used to perform quality inspection. If quality orders are used, you can configure the process to temporarily block products through a reservation while they are inspected. If quarantine orders are used, products are moved to another warehouse for inspection. This warehouse is known as the quarantine warehouse. In both quality inspection processes, some of the goods might be scrapped, either because they don’t conform to the quality expectations or because the quality inspection involves destructive testing of a sample of the product.

## Product receipt
Most often, the **Product receipt** action on the **Purchase orders** page is used to mark products as **Received** on the PO. The **Posting product receipt** page has various options for the quantity that is accounted as received. For example, you can set the **Quantity** field to **Ordered quantity** or **Receive now quantity**. Alternatively, if a warehouse arrival process has been used, you will often set this field to **Registered quantity**. You can modify the quantities on each order line that will be marked as **Received**, to account for any discrepancies, such as under-delivery and over-delivery. During product receipt, you must specify a product receipt identifier, which is typically a reference to the packing slip from the supplier. This identifier is required for accounting, because it enables checks or audits of supplier packing slips against what has been received, and the accounted inventory or expense.  

If an employee ordered goods by using a purchase requisition, that employee might be asked to confirm receipt of the product himself or herself. You configure this behavior by using a workflow. You can configure the workflow conditions so that they match your business process.  

POs can be created for products that aren’t intended as inventory but are considered an expense. This category includes order lines where the products are marked as **Not stocked** by their inventory model group, and also lines that use procurement categories. In this case, the items might not go through arrival registration and receipt in the warehouse. Instead, the **Product receipt** action is used to record the receipt directly on the PO, and the receipt is based on the ordered quantity, not a registered quantity.  

You can create PO lines where the **New fixed asset** option is enabled. This option indicates that the purchase should be considered a fixed asset instead of inventory. In this case, the fixed asset determination rules that have been configured determine whether the purchase of the product or category exceeds specific thresholds, and must therefore be accounted for as an asset and go through fixed asset management. Purchases can also be made toward an existing fixed asset. In this case, the amount is adjusted as appropriate.  

You can select multiple orders and process receipt on all those orders together. This approach isn’t used very often, but you might want to use it if a supplier has consolidated shipments for you into a single load. During product receipt on the purchase, there is a function for doing summary updates. Summary updates let you post a single packing slip from the supplier for more than one PO.  

POs might be created from a sales order where the **Direct delivery** option was selected. When direct delivery is used, the products never arrive in your warehouse but are shipped directly from the supplier to the customer. In this case, the receipt is usually recorded directly on the PO. The receipt can be done automatically, such as through electronic data interchange (EDI) integration with the supplier. Alternatively, if the PO is an intercompany PO, Microsoft Dynamics 365 for Finance and Operations automates the receipt on the intercompany sales order when shipment occurs. When direct delivery is used, products are still accounted as inventory, even though they don’t physically arrive at the warehouse. Therefore, when product receipt is registered on the PO, the sales order is automatically updated with a packing slip, so that the overall change to inventory is 0 (zero). In direct delivery scenarios, you should not require preregistration. If you’re using warehouses that are enabled for warehouse management, you can get around the requirement for license plate registration by specifying a virtual warehouse instead. You specify this warehouse in the **Direct delivery warehouse** field on the product. 

After the product receipt has been processed on the PO, the PO status is set to **Received** to indicate that the invoice can be processed for the order. You can review details about products that have already been received by using the **Product receipt journals** page.  

You can access this page from the **Receipt** action group on the **Purchase order** page. The information in the journals includes details about the quantities, dates, and dimensions.

See also
--------

[Purchase order overview](purchase-order-overview.md)

[Purchase order creation](purchase-order-creation.md)

[Purchase order approval and confirmation](purchase-order-approval-confirmation.md)

[Overview of vendor invoices](../../financials/accounts-payable/vendor-invoices-overview.md)



