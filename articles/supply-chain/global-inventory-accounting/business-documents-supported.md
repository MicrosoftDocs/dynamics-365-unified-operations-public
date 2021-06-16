---
title: Business documents supported by Global Inventory Accounting
description: This topics provides a list of business documents supported by Global Inventory Accounting and examines the example of purchase order documents in detail.
author: AndersGirke
ms.date: 06/18/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: aevengir
ms.search.validFrom: 2021-06-18
ms.dyn365.ops.version: 10.0.20
---

# Business documents supported by Global Inventory Accounting

[!include [banner](../includes/banner.md)]

When the Global Inventory Accounting Add-in is fully set up, it's ready to process inventory-related documents entered in Supply Chain Management.

## Supported business documents

There are two types of business documents:

- **Documents with journal** – these include product receipt, purchase invoice, packing slip, sales invoice, and so on.
- **Documents without journal** – these include counting, movement, inventory adjustment, and so on.

Later in this topic, we will use purchase order as example to illustrate the process.

The following table lists the documents supported by the current release.

| **Document type**  | **Document**    |
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
> Global Inventory Accounting processes the documents entered in Supply Chain Management asynchronously. No error messages will be shown for problematic documents.

## Example: Purchase order

### Product receipt

Post product receipts as usual. On the **All purchase orders page**, select a purchase order and, on the Action Pane, open the **Receive** tab and select **Product receipt** to open the **Product receipt journal** page. The operation event and cost accounting event are generated per line, so open the **Lines** tab and select **Inventory \> Events and measurements** from the toolbar to open the **Events and measurements** page.

Global Inventory Accounting is an event and measurement-based accounting system. In the measurement line grid, you can find a list of measurements, and each measurement has a list of dimensions.

For each operation event, there are following two types of measurement:

- **Operations measurements** – Describe the business documents with cost information. There is product quantity with the unit of measure in the document, and measurements that impact the inventory value, including extended price, discount, discount percent and line charge.
- **Resource accounting measurements** – Measurements from the inventory register perspective, which describe the document impacts to the inventory in inventory unit of measure. There are multiple lines of resource accounting measurement in case there are multiple inventory registrations.

The dimensions are organized as follows:

- **Duality** – Describes the agents participating in the economic events. For external business documents, the primal dimensions describe the information of the legal entity where the document is entered, while the dual dimensions describe the information of the vendor, customer, and so on. For internal documents (for example, transfer order) the dual dimensions describe the counterpart warehouse.
- **Dimension type** – Categorizes the dimensions.
- **Dimension** – The name of the dimension.
- **Dimension value** – The value of the dimension.

### Cost accounting event

The cost accounting service takes the operational events and measurements as the input and does the proper accounting for each related ledger following the attached currency and convention. Selecting **Cost accounting events and measurements** to view the cost accounting event. It follows the same methodology of the operation events, but uses different measurements. There are three major measurement types: product cost quantity, product cost, and variance. There are subledger accounts to further classify the measurements. There might be multiple ledgers, which are linked to the legal entity where the document is entered. You can view the events and measurements for each ledger by changing the value of the **Ledger** field.

### Cost element

Following the cost element policy attached to the ledger, the system assigns a cost element to each accounted operation event measurement that impacts the inventory cost, including: extended price, discount, discount percent and line charge.

### Measurement line details

The **Overview** tab shows the details of the attached policies. The cost object dimensions show the cost object based on the cost object policy, and specific identification dimensions show the batch number in case the cost flow assumption is *Specific – Batch*.

### Purchase invoice

Post the invoice as usual and open the invoice journal (on the Action Pane, open the **Invoice** tab and, from the **Journals** group, select **Invoice**). The operation event and cost accounting event are generated per line, so open the **Lines** tab and select **Inventory \> Events and measurements** from the toolbar to open the **Events and measurements** form. It shows the same measure type, but different measure role and measure modifier, which indicate a different impact to the agent (legal entity).

Select **Cost accounting events and measurements** to view the cost accounting event. The system now outflows the inventory quantity and cost from *Goods received not invoiced inventory* into *Cost of goods purchased*.
