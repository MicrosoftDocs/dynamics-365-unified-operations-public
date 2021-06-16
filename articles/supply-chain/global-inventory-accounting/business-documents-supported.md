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

In this topic, we will use purchase order as example to illustrate the process.

The following table lists the documents supported by the current release:

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

Post product receipt as normally, open the Product receipt journal (Receive \> Product receipt). The Operation event and Cost accounting event are generated per line, so go to **Lines \> Inventory \> Events and measurements** to open the **Events and measurements form**.

Global Inventory Accounting is an event and measurement-based accounting system. In the measurement line grid, you can find a list of measurements, and each measurement has a list of dimensions which are shown in measurement line details grid.

For each operation event, there are following two types of measurement:

- **Operations measurements** – Operations measurements describe the business documents with cost information. There is product quantity with UoM in the document, and measurements which impact the inventory value, including extended price, discount, discount percent and line charge.
- **Resource accounting measurements** – Resource accounting measurements are measurements from inventory register perspective which describe the document impacts to the inventory in inventory UoM. There are multiple lines of resource accounting measurement in case there are multiple inventory registration.

The dimensions are organized as follows:

- **Duality** – Describe the agents participating in the economic events. For external business document, the primal dimensions describe the information of the legal entity where the document is entered, while the dual dimensions describe the information of the vendor, customer, etc. For internal documents, for example transfer order, the dual dimensions describe the counterpart warehouse.
- **Dimension type** – It categorizes the dimensions.
- **Dimension** – It is the name of the dimension.
- **Dimension value** – It is the value of the dimension.

### Cost accounting event

Cost accounting service takes the operational events and measurements as the input, do the proper accounting for each related ledger following the attached currency and convention. By selecting Cost accounting events and measurements to view the cost accounting event. It follows the same methodology of the operation events but use different measurements. As explained above, there are three major measurement types: Product cost quantity, Product cost and Variance. There are subledger accounts to further classify the measurements. There might be multiple ledgers created which are linked to the legal entity where the document is entered. You can view the events and measurements for each ledger by changing the value of the dropdown list Ledger.

### Cost element

Following the cost element policy attached to the ledger, system assign the cost element to each accounted operation event measurements which impact the inventory cost: Extended price, Discount, Discount percent and Line charge.

### Measurement line details

The overview tab shows the details of the attached policies. The cost object dimensions show the cost object based on the cost object policy, and specific identification dimensions show the batch number in case the cost flow assumption is Specific – Batch.

### Purchase invoice

Post the invoice as normal, open the invoice journal (Invoice \> Invoice). The Operation event and Cost accounting event are generated per line, so go to **Lines \> Inventory \> Events and measurements** to open the **Events and measurements** form. It shows the same measure type, but different measure role and measure modifier which indicate different impact to the agent (legal entity)

Select **Cost accounting events and measurements** to view the cost accounting event. The system now outflows the inventory quantity/cost from Goods received not invoiced inventory to into Cost of goods purchased.
