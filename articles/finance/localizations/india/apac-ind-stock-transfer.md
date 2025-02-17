---
title: Stock transfer orders for India
description: Learn about the stock transfer functionality that is available for India in Microsoft Dynamics 365 Finance, including an outline on setting up stock transfers.
author: chuzheng
ms.author: chuzheng
ms.topic: article
ms.date: 06/29/2022
ms.custom:
ms.reviewer: johnmichalak
audience: Application User 
ms.search.region: India
ms.search.validFrom: 2019-08-04
ms.search.form: InventTransferOrders, ReqParameters
ms.dyn365.ops.version: 10.0.5
---

# Stock transfer orders for India

[!include [banner](../../includes/banner.md)]

You can use transfer orders to process inventory transfers between warehouses. In India, if the shipping and receiving branches of the organization have different tax registration numbers, the India Goods and Services Tax (GST) should be calculated and posted for the transfer order. The tax base may be defined as the current cost price of the item being transferred or a special transfer price. The tax amount should be posted as GST payable for the transfer shipment and as GST recoverable upon the transfer receipt. An **Interim transit** account is used as an offset account for the posting and is nullified when the transfer order is fully received. 

The **Stock transfer** functionality that is available for India supports this process.

> [!NOTE]
> Unrealized profit or loss isn't posted during the shipment or receipt of a stock transfer line if the unit price differs from the inventory cost price of the item. If mutual settlements and profit/loss transactions are required for internal transfers between your own company's warehouses, other functionality can be used. For example, purchase orders and sales orders invoices or intercompany invoices can be configured for intracompany transfers.
>
> For more information, see [Set up intercompany trade](../../../supply-chain/sales-marketing/intercompany-trade-set-up.md).

## Set up stock transfers

### Enable stock transfer functionality

Enable the following features in the **Feature management** workspace:

- *(India) Improvements in unit price and cost price handling in Stock transfer orders* (As of version 10.0.43, this feature is turned on by default.)
- *Enable uniform tax amount and GST transaction ID for both shipment and receipt transaction of a stock transfer order* (As of version 10.0.43, this feature is mandatory and can't be turned off.)

> [!NOTE]
> In future releases, the preceding features will be turned on by default.

For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

You also need to configure the India GST functionality to enable GST calculation for stock transfer orders. For more information, see [India Goods and Services Tax (GST) overview](apac-ind-gst.md).

### Set up default transfer type and price type for transfer orders

You can define a default transfer order type and a default price type for transfer orders that are created manually. On the **Inventory and warehouse management parameters** page, on the **Transfer orders** tab, select **Stock transfer** in the **Transfer type** field to enable the **Stock transfer** functionality for all newly created transfer orders. In the **Price type** field, select a default price type for newly created stock transfer orders:

- **Cost price** – The cost price, or the on-hand price, of the item will be used for stock transfer orders.
- **Transfer price** – The transfer price that is set up for the item will be used for stock transfer orders.

> [!NOTE]
> In the case of the **Cost price** price type, the system calculates a running average cost price, based on the inventory dimensions that are specified for an item line. This running average price is stored in the **Cost price** field when the line is created or updated. The saved cost price is never recalculated when shipping and receiving transactions are posted.

### Configure Master planning parameters

You can define a default transfer order type and a default price type for transfer orders that are created when confirming planned orders in the **Master planning** module. On the **Master planning parameters** page, on the **Standard update** tab, select **Transfer type** and **Price type** in the **Firm - Transfer** group.

### Set up item master parameters

To calculate GST for an item in a stock transfer order, you need to configure certain parameters on the **Released product details** page, such as **HSN codes** and **Tax rate type**. For more information, see [Assign HSN codes and SACs to products](apac-ind-GST-hsn-service-accounting-codes.md#assign-hsn-codes-and-sacs-to-products).

### Configure transfer pricing

You can configure the prices that will be used when processing stock transfers for an item. To do this, open the **Transfer price** page from the **Released product details** page.

### Configure stock transfer posting

You must configure the **Interim transit** account, which is done on the following pages:

- In the **Inventory management** module, on the **Posting** page, on the **Transfer order** tab, specify the **Interim transit** account.
- On the **Tax setup** page, click **Setup**, and on the **Setup** page specify the **Interim transit for stock transfer** account for all GST components that may be created for GST on stock transfer. For more information, see [Define main accounts](apac-ind-GST-map-configuration-tax-types.md#define-main-accounts-1).

> [!NOTE]
> The accounts that are used to post interim transit amounts should have **Interim transit** specified in the **Posting type** field on the **Posting validation** tab of the **Main accounts** page.

You must also set up main accounts to post inventory cost for transfer orders to. Specify the following accounts from the **Inventory** tab on the **Posting** page in **Inventory management**: 

- **Inventory issue**
- **Inventory receipt**
- **Inter-unit payable**
- **Inter-unit receivable**
- **Inventory expenditure, loss**

> [!NOTE]
> The **Inventory expenditure, loss** account is required to post the scrap amount when receiving a transfer order with scrap.

### Configure posting to General ledger based on financial dimension links to sites

In the standard finance and operations functionality, transfer orders are only posted to General ledger if *both* the following conditions are met:

- A dimension link is enabled, so that there is a link between the **Site inventory** dimension and some financial dimension.
- The transfer order movement occurs between warehouses that belong to different sites. This condition applies to the **From**, **Transit**, and **To** warehouses. If the **From** warehouse and **Transit** warehouse belong to the same site, the transfer order shipment isn't posted to General ledger. Similarly, if the **Transit** warehouse and **To** warehouse belong to the same site, the transfer order receipt isn't posted to General ledger.

If you must post stock transfers to General ledger and track inventory in transit warehouses, we recommend that you enable a dimension link and create separate sites for transit warehouses.

For more information, see [Configure and manage financial dimension links to sites](/dynamicsax-2012/appuser-itpro/configure-and-manage-financial-dimension-links-to-sites).

> [!NOTE]
> Financial dimensions are derived from product master data and the dimension link. Financial dimensions can't be changed in transfer orders.

## Create and post a stock transfer order

The following example scenario shows frequently performed actions that are associated with transfer orders where the **Transfer type** field is set to **Stock transfer** and the dimension link is enabled.

1. Go to **Inventory management** > **Outbound orders** > **Transfer order** and create a new transfer order.
2. In the **From warehouse** field, select the supply warehouse that the items are dispatched from.
3. In the **To warehouse** field, select the receiving warehouse that the items are delivered to.

    > [!NOTE]
    > If the **From** warehouse and **Transit** warehouse belong to the same site, the transfer order shipment isn't posted to General ledger. Similarly, if the **Transit** warehouse and **To** warehouse belong to the same site, the transfer order receipt isn't posted to General ledger.

4. In the **Transfer type** field, select **Stock transfer** to apply GST to the transfer of items.

    > [!NOTE]
    > If you select **Transfer order** in the **Transfer type** field, the transfer order is posted based on the standard transfer order process.

5. In the **Price type** field, select a default price type for transfer order lines.
6. On the **Transfer order lines** tab, create a new line. In the **Item number** field, select the item to transfer.
7. In the **Transfer quantity** field, enter the quantity of the items to transfer. In the **Unit** field, change the default unit of measurement, if required.

    > [!NOTE]
    > Changes to the unit of measure of stock on a transfer order line are restricted.

8. In the **Price type** field, select the price type for the transfer order line, from the following options:

    - **Cost price** – The cost price, or the on-hand price, of the item is used for the transfer order line.
    - **Transfer price** – The transfer price that is set up for the item is used for the transfer order line.

    > [!NOTE]
    > If the **Price type** field is set to **Transfer price**, the **Transfer quantity** field shows the quantity of the items that are defined for the combination of an item and a dimension on the **Transfer price** page. This value can be modified.

9. In the **Unit price** field, enter the cost price or the transfer price for one unit of the item.

    > [!NOTE]
    > The unit price on a stock transfer order line is recalculated based on the inventory dimensions that are specified on the line until the first shipment is posted for the line.
    > 
    > Shipment of a stock transfer order line that has a unit price of 0 (zero) can be controlled through the **Prevent shipment with zero unit price** field in Inventory and warehouse management parameters.

10. Select **Tax information** to review the tax configuration for the transfer order.

    - At the line level, on the **Invent transfer order from location** tab, you will find tax information that is linked to the shipment (from warehouse).
    - At the line level, on the **Invent transfer order to location** tab, you will find tax information that is linked to the receipt (to warehouse).

11. Go to **Inquiries** > **Tax document**, and verify that the tax is calculated correctly.
12. Select **Ship** > **Ship transfer order**. Then, on the **Shipment** page, post the transfer order shipment:

    1. Select the **Explode lines** checkbox, and then, in the **Update** field, select **All**.
    2. Select **Setup** > **Tax document**, and review the tax settings and amounts. Make any adjustments that are required.
    3. Close the **Tax document** page, and then select **OK** on the **Ship** page to post the operation.

13. Select **Receive** > **Receive**. Then, on the **Receive** page, post the transfer order receipt:

    1. Select the **Explode lines** checkbox, and then, in the **Update** field, select **All**.
    2. Select **Setup** > **Tax document**, and review the tax settings and amounts. Make any adjustments that are required.
    3. Close the **Tax document** page, and then select **OK** on the **Receive** page to post the operation.

    > [!NOTE]
    > If the "Enable uniform tax amount and GST transaction ID for both shipment and receipt transaction of a stock transfer order" feature is enabled in the **Feature management** workspace, only a previously posted shipment can be received. You must select **Shipment** in the **Update** field when you post a receipt, and you must select a previously posted shipment in the **Shipment voucher** field.

You can also cancel a previously posted stock transfer order shipment if no receipts have been posted for this order. On the **Transfer orders** page, select **Transfer order** > **Transfer order history**. On the **Transfer order history** page, select a previously posted shipment. Select **Cancel**, and confirm the cancellation of the shipment. The shipment will be canceled, and all inventory movements and GST that was posted for the shipment will be reversed. The "Transfer Order Cancellation" feature in the **Feature management** workspace must be enabled to cancel transfer order shipments.

The rest of this article provides several examples that show how stock transfer orders are posted under different conditions.

### Example 1: Standard transfer order posting

This example has the following preconditions:

- Current inventory cost price at the moment when the shipment is posted = 100 Indian rupees (Rs.)
- From warehouse = Site 1
- Transit warehouse = Site 2
- To warehouse = Site 3

#### Transfer order shipment posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 1                             |                    | 100                 |
| Inventory inter-unit receivable | Site 1                             | 100                |                     |
| Inventory inter-unit payable    | Site 2                             |                    | 100                 |
| Inventory receipt               | Site 2                             | 100                |                     |
 
#### Transfer order receipt posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 2                             |                    | 100                 |
| Inventory inter-unit receivable | Site 2                             | 100                |                     |
| Inventory inter-unit payable    | Site 3                             |                    | 100                 |
| Inventory receipt               | Site 3                             | 100                |                     |

The balance on the inventory in transit can be calculated as *InventoryIssue-Site2* – *InventoryReceipt-Site2*. This balance is nullified upon the receipt.

### Example 2: Standard transfer order posting without a transit site

This example has the following preconditions:

- Current inventory cost price at the moment when the shipment is posted = 100 Rs.
- From warehouse = Site 1
- Transit warehouse = Site 1
- To warehouse = Site 3

##### Transfer order shipment posting

No posting to General ledger occurs.

##### Transfer order receipt posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 1                             |                    | 100                 |
| Inventory inter-unit receivable | Site 1                             | 100                |                     |
| Inventory inter-unit payable    | Site 3                             |                    | 100                 |
| Inventory receipt               | Site 3                             | 100                |                     |

In this case, **no inventory in transit balance** is tracked.

### Example 3: Stock transfer order that has tax on the transfer price (GST)

This example has the following preconditions:

- Current inventory cost price at the moment when the shipment is posted = 100 Rs.
- Unit price that is specified on the line = 120 Rs. This price can be the inventory cost price at the moment when the line was created or updated, or it can be the transfer price of the item.
- Taxable value (base amount) = 120.00.
- GST rate = 10 percent.
- From warehouse = Site 1.
- Transit warehouse = Site 2.
- To warehouse = Site 3.

#### Transfer order shipment posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 1                             |                    | 100                 |
| Inventory inter-unit receivable | Site 1                             | 100                |                     |
| Inventory inter-unit payable    | Site 2                             |                    | 100                 |
| Inventory receipt               | Site 2                             | 100                |                     |
| GST payable                     | Site 1                             |                    | 12                  |
| Interim account                 | Site 1                             | 12                 |                     |

#### Transfer order receipt posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 2                             |                    | 100                 |
| Inventory inter-unit receivable | Site 2                             | 100                |                     |
| Inventory inter-unit payable    | Site 3                             |                    | 100                 |
| Inventory receipt               | Site 3                             | 100                |                     |
| GST receivable                  | Site 3                             |                    | 12                  |
| Interim account                 | Site 3                             | 12                 |                     |

The balance on the inventory in transit can be calculated as *InventoryIssue-Site2* – *InventoryReceipt-Site2*. The balance is nullified upon the receipt.

> [!NOTE]
> - The **Inventory issue** and **Inventory receipt** accounts are probably the same balance account, such as **Finished goods**.
> - The settings for dimension links and sites (that is, a separate site for the transit warehouse) are recommended if you must track the in-transit inventory in General ledger.

### Example 4: Stock transfer order with standard cost

This example has the following preconditions:

- Create an item that uses the **Standard cost** inventory model.
- Create and activate different item prices for the item, where **Costing type** = **Standard cost** and **Price type** = **Cost**:

    - Price = 115 for Site 1
    - Price = 112 for Site 2
    - Price = 111 for Site 3

- Inventory cost price is defined by the standard cost on the **From warehouse** site and equals 115 Rs. in this case.
- From warehouse = Site 1.
- Transit warehouse = Site 2.
- To warehouse = Site 3.

#### Transfer order shipment posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 1                             |                    | 115                 |
| Inventory inter-unit receivable | Site 1                             | 115                |                     |
| Inventory inter-unit payable    | Site 2                             |                    | 115                 |
| Inventory receipt               | Site 2                             | 112                |                     |
| Cost change variance            | Site 2                             | 3                  |                     |

#### Transfer order receipt posting

| Ledger account name             | Financial dimension linked to site | Debit amount (Rs.) | Credit amount (Rs.) |
|---------------------------------|------------------------------------|--------------------|---------------------|
| Inventory issue                 | Site 2                             |                    | 112                 |
| Inventory inter-unit receivable | Site 2                             | 112                |                     |
| Inventory inter-unit payable    | Site 3                             |                    | 112                 |
| Inventory receipt               | Site 3                             | 111                |                     |
| Cost change variance            | Site 3                             | 1                  |                     |

The balance on the inventory in transit can be calculated as *InventoryIssue-Site2* – *InventoryReceipt-Site2*. The balance is nullified upon receipt.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
