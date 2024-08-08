---
title: Business documents supported by Global Inventory Accounting
description: Access a list of the business documents that are supported by Global Inventory Accounting, including a detailed example for purchase order documents.
author: JennySong-SH
ms.author: yanansong
ms.topic: article
ms.date: 06/18/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Business documents supported by Global Inventory Accounting

[!include [banner](../includes/banner.md)]

After the Global Inventory Accounting Add-in is fully set up, it's ready to process inventory-related documents that are entered in Microsoft Dynamics 365 Supply Chain Management.

## Supported business documents

There are two types of business documents:

- **Documents that have a journal** – These documents include product receipt, purchase invoice, packing slip, and sales invoice documents.
- **Documents that don't have a journal** – These documents include counting, movement, and inventory adjustment documents.

Later in this article, purchase orders will be used as an example to illustrate the process.

The following table lists the documents that the current release supports.

| Document type      | Document        |
|--------------------|-----------------|
| Purchase Order     | Product Receipt |
| Purchase Order     | Invoice         |
| Sales Order        | Packing slip    |
| Sales Order        | Invoice         |
| Inventory Journals | Movement        |
| Inventory Journals | Adjustment      |
| Inventory Journals | Counting        |
| Inventory Journals | Transfer        |
| Transfer Order     | Shipment        |
| Transfer Order     | Receive         |

> [!IMPORTANT]
> Global Inventory Accounting asynchronously processes the documents that are entered in Supply Chain Management. No error messages will be shown for problematic documents.

## Example: Purchase order

### Product receipt

Post product receipts in the usual way. On the **All purchase orders** page, select a purchase order, and then, on the Action Pane, on the **Receive** tab, select **Product receipt** to open the **Product receipt journal** page. An operation event and a Global Invntroy Accounting event are generated for each line. Therefore, select the **Lines** tab, and then select **Inventory \> Events and measurements** to open the **Events and measurements** page.

Global Inventory Accounting is an accounting system that is based on events and measurements. The measurement line grid on the **Events and measurements** page shows a list of measurements. Each measurement has a list of dimensions.

For each operation event, there are two types of measurement:

- **Operations measurements** – These measurements describe business documents in generic terms. One measurement is the product quantity using the unit of measure that is used in the document. There are also measurements that affect the inventory value, such as extended price, discount, discount percent, and line charge.
- **Resource accounting measurements** – These measurements are from the inventory register perspective. They describe the document's impact on the inventory in the inventory unit of measure. If there are multiple inventory registrations, there are multiple lines of resource accounting measurements.

The dimensions are organized in the following way:

- **Duality** – Duality describes the agents who participate in the economic events. For external business documents, the primal dimensions describe the legal entity where the document is entered, whereas the dual dimensions describe the vendor, customer, and so on. For internal business documents (for example, transfer orders), the dual dimensions describe the counterpart warehouse.
- **Dimension type** – Dimension types categorize the dimensions.
- **Dimension** – The name of the dimension.
- **Dimension value** – The value of the dimension.

### Global Inventory Accounting event

Global Inventory Accounting takes the operational events and measurements as input. It then does the appropriate accounting for each related ledger, based on the attached currency and convention. You can select **Global inventory accounting events and measurements** to view the Global Inventory Accounting event. The Global Inventory Accounting event follows the same methodology as operation events, but it uses different measurements. There are three major measurement types: product cost quantity, product cost, and variance.

Subledger accounts are used to further classify the measurements. There might be multiple ledgers. These ledgers are linked to the legal entity where the document is entered. You can view the events and measurements for each ledger by changing the value of the **Ledger** field.

### Cost element

Based on the cost element policy that is attached to the ledger, the system assigns a cost element to each accounted operation event measurement that affects the inventory cost. These measurements include extended price, discount, discount percent, and line charge.

### Measurement line details

The **Overview** tab shows the details of the attached policies. The cost object dimensions show the cost object, based on the cost object policy. Specific identification dimensions show the batch number if the cost flow assumption is *Specific – Batch*.

### Purchase invoice

Post the invoice in the usual way. Then, on the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice** to open the invoice journal. An operation event and a Global Inventory Accounting event are generated for each line. Therefore, select the **Lines** tab, and then select **Inventory \> Events and measurements** to open the **Events and measurements** page. The **Events and measurements** page shows the same measure type. However, because the page shows a different measure role and measure modifier, the impact on the agent (legal entity) differs.

Select **Global inventory accounting events and measurements** to view the Global Inventory Accounting event. The inventory quantity and cost now flow out from the *Goods received not invoiced inventory* subledger account and into the *Cost of goods purchased* subledger account.
