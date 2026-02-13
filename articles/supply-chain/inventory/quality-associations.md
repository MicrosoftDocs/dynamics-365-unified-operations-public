---
title: Quality associations
description: Learn how you can use quality associations in Microsoft Dynamics 365 Supply Chain Management to automatically generate quality orders related to your sales.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventTestAssociationTable, WHSConsigner, WHSConsignerGroup
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Quality associations

[!include [banner](../includes/banner.md)]

This article describes how you can use quality associations in Microsoft Dynamics 365 Supply Chain Management to automatically generate quality orders that are related to your sales, purchase, inbound shipment order, and production processes.

A quality association defines all the following information for a quality order that is generated:

- The transaction event
- The set of tests that must be performed on the items
- The acceptable quality level (AQL)
- The sampling plan

You must define a quality association for each variation in a business process that requires automatic generation of quality orders. For example, a quality order can be generated in the business processes for purchase orders, quarantine orders, sales orders, and production orders.

## Prerequisites for sales returns and transfer orders (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

Most of the features that are described in this article are available as a standard part of all current versions of Supply Chain Management. However, if you want to set up quality associations for sales returns and transfer orders, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.47, this feature is turned on by default.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Working with quality associations

The business process that uses a quality association can be related to various source documents, such as purchase orders, sales orders, or production orders.

Each quality association record defines the set of tests, the AQL, and the sampling plan that applies to the quality orders that are generated. You must define a quality association record for each variation in a business process. For example, you can set up a quality association that generates a quality order when a purchase order product receipt is updated. Depending on the setup of the execution plan, the triggering process itself can be blocked while there's an open quality order. Alternatively, subsequent processes, such as purchase order invoicing, can be blocked.

> [!NOTE]
> While there are open quality orders, inventory quantities are automatically blocked from being issued. Depending on the setting of the **Full blocking** field on the **Item samplings** page, the quantity is either the quantity on the quality order or the quantity on the source document line. Learn more in [Quality management item sampling](quality-item-sampling.md).

For a given business process, the quality association record identifies the event and conditions that a quality order is generated for. The conditions can be specific to either a site or a legal entity. A quality order that involves destructive tests can be generated only when on-hand inventory exists for the event.

To work with quality associations, go to **Inventory management \> Setup \> Quality control \> Quality associations**. The following examples show how a quality association record is defined for the variations in each business process. For each example, the following table summarizes the events and conditions that are defined by a quality association record.

> [!NOTE]
> The *Quality management for warehouse processes* feature adds capabilities for quality order processing for production where the **Event type** field is set to *Report as finished* and the **Execution** field is set to *After*, and for purchases where the **Event type** field is set to *Registration*. Learn more in [Quality management for warehouse processes](quality-management-for-warehouses-processes.md).

The following table provides more information about how quality orders can be generated for specific types of processes.

| Type of process | When quality orders can be automatically generated | When quality orders can be generated if destructive testing is required | Condition information | Manual generation information |
|---|---|---|---|---|
| Purchase order | Before or after a receipts list or product receipt is posted for the material that is received | After the product receipt is posted for the material that is received, because the material must be available for destructive testing | The requirement for a quality order can reflect a specific site, item, or vendor, or a combination of these conditions. | A manually generated quality order that refers to a purchase order can use information in a quality association record, such as the test sampling plan. |
| Inbound shipment order | As part of the registration process (warehouse receiving) | As part of the registration process (warehouse receiving) | The requirement for a quality order can reflect a specific site, item, or consigner, or a combination of these conditions. | A manually generated quality order that refers to an inbound shipment order can use information in a quality association record, such as the test sampling plan. |
| Quarantine order | Before or after the quarantine order is reported as finished or ended | Quality orders that require destructive tests can't be generated. The assumption is that the quarantine order functionality handles the disposition of the material that is destroyed. | The requirement for a quality order can reflect a specific site, item, or vendor, or a combination of these conditions. | A manually generated quality order that refers to a quarantine order can use information in a quality association record, such as the test sampling plan. |
| Sales order | Before a scheduled picking process or packing slip update for the items that are being shipped | At any step | The requirement for a quality order can reflect a specific site, item, or customer, or a combination of these conditions. | A manually generated quality order that refers to a sales order can use information in a quality association record, such as the test sampling plan. |
| Production order | Before or after the finished quantity is reported for the production order | After the finished quantity is reported for the production order | The requirement for a quality order can reflect a specific site or item, or a combination of these conditions. | A manually generated quality order that refers to a production order can use information in a quality association record, such as the test sampling plan. |
| Production order that has a route operation | Before or after the report is finished for an operation | After the reporting production is finished for the last operation | The requirement for a quality order can reflect a specific site, item, or operations resource, or a combination of these conditions. | A manually generated quality order that refers to a route operation can use information in a quality association record, such as the test sampling plan. |
| Inventory | A quality order can't be automatically generated for a transaction in an inventory journal or for transfer order transactions. | | | A quality order must be manually created for an item's inventory quantity. Physical on-hand inventory is required. |
| Sales return | A quality order is generated when the packing slip on the sales return order is posted. | After the product receipt is posted for the material that is received, because the material must be available for destructive testing. | Before the packing slip is posted on the return order, the quantity on the return line must be registered. To register the quantity, on the **Update line** menu, select **Registration**. Then, on the **Assign disposition code** dropdown menu, select one of the applicable disposition codes. The selected disposition code must be set up to search for an applicable quality association. To complete this setup, select the **Check for quality association** checkbox in the definition of the disposition code. | |
| Transfer order | A quality order can be generated when you do the picking, when you ship the product, or when you receive it. | After registration of the receipt of the material, because the material must be available for destructive testing. | | |

> [!NOTE]
> When you filter quality associations for the *Inbound shipment order* reference type, and the **Account code** value is *Table* or *Group*, you must create consigners (for *Table*) or consigner groups (for *Group*) beforehand.

## Set up a quality association

Follow these steps to create a quality association:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Quality associations**.
1. On the Action Pane, select **New**.
1. On the header, make the following settings:
    - **Reference type** – Select the business process for which quality orders are generated by the system, such as *Purchase* or *Production*.
    - **Item code** – Select which products should be included in the rule. Choose one of the following values:
        - *Table* – A specific product.
        - *Group* – A group of products.
        - *All* – All products.
    - **Item** – Depending on what you selected for **Item code**, choose the specific product or product group for which this rule should apply. Leave blank if **Item code** is set to *All*.

1. On the **Conditions** FastTab, make the following settings:
    - **Site** – Select the site where the rule applies.
    - **Applicable warehouse type** – Select the type of warehouse for which the quality association is used for. Choose one of the following values:
        - *All* – Includes all warehouses. Quality order functionality for warehouse processes isn't available for the quality association when **Applicable warehouse type** is set to *All*.
        - *Quality order for warehouse processes only* – Includes only warehouses where **Enable quality order for warehouse processes** is set to *Yes*.
    - **Account code** – Select the vendor or customer account to whom this rule applies. Available options depend on the selected **Reference type**.
    - **Account selection** – Depending on which **Account code** is selected, choose a specific account or account group. Leave this blank if **Account code** is set to *All*.
    - **Resource code** – Select the scope of resources to which the rule applies. This option only applies if the **Reference type** is *Route operation*. Choose one of the following values:
        - *All* – Applies to all resources.
        - *Group* – Applies to a group of resources.
        - *Table* – Applies to a single, selected resource.
    - **Resource** – Depending on what you selected for **Resource code**, choose the specific resource or resource group to which this rule should apply. Leave this blank if **Resource code** is set to *All*.

1. On the **Process** FastTab, make the following settings:
    - **Event type** – Depending on the **Reference type**, select the business event that should generate the quality order. For example, if the **Reference type** is *Production* you can choose between *Report as finished* and *Registration*.
    - **Execution** – Choose one of the following values:
        - *Before* – Automatically create the quality order before the business event occurs.
        - *After* – Automatically create the quality order after the business event occurs.
    - **Show info** – Select whether an info-log should be shown after the quality order is automatically created based on the business event.

1. On the **Quality order process** FastTab, make the following settings:
    - **Event blocking** – Choose whether the document should be set on hold until the associated quality order is validated and closed. Choose one of the following values:
        - *End* – Blocks processing of the document until the associated quality order is validated and closed.
        - *None* – Don't block the document from being processed.
    - **Quarantine upon validation failure** – Set to *Yes* to automatically create a quarantine order if the associated quality order fails validation.
    - **Use for certificate of analysis** – Choose one of the following values:
        - *No* – Don't make it possible to generate a certificate of analysis for this quality association.
        - *Yes* – Make it possible to generate a certificate of analysis for this quality association.
    - **Quality processing policy** – Choose one of the following values:
        - *Create quality order* – Uses the full quality process and create quality orders.
        - *Create item sampling work only* – Uses a minimal quality process that creates quality item sampling work but doesn't create quality orders or inventory blocking. This option only applies when the **Applicable warehouse type** is set to *Quality order for warehouse processes only*.

1. On the **Specifications** FastTab, make the following settings:
    - **Test group** – Select a test group with tests defined for acceptance sampling or sample management. Learn more in [Acceptance sampling](quality-acceptance-sampling.md) and [Enable and configure sample management (preview)](quality-sample-management-admin.md).
    - **Item sampling** – Select an item sampling defined for acceptance sampling or sample management. Learn more in [Acceptance sampling](quality-acceptance-sampling.md) and [Enable and configure sample management (preview)](quality-sample-management-admin.md).
    - **Acceptable quality level** – Choose the acceptable quality level (AQL) to be used for the quality association. The AQL determines whether the quality order passes or fails validation.
    - **Flexible sampling** – Choose whether to use the flexible sampling plans as part of this quality association.
    - **Flexible sampling plan code** – If **Flexible sampling** is set to *Yes*, then select a flexible sampling plan code.
    - **Effective** – Select the date on which this quality association becomes effective.
    - **Expiration** – Select the date on which the quality association expires.
    - **Worker** – Select the default worker to be assigned to quality orders generated by this quality association.
    - **Quality order priority** – Select the default priority that should be assigned by default to the quality order generated for this quality association.
    - **Description** – Displays the description of the selected quality order priority.

## Quality associations and flexible sampling plans

Instead of selecting a fixed test group and item sampling, you can set up a *flexible sampling plan*. A flexible sampling plan is a test strategy where you can change both the test and sample sizes over time, based on successful test validation. To use flexible sampling, on the **Specification** FastTab, select **Flexible sampling**. Then, in the **Flexible sampling plan code** field, select the code for a flexible sampling plan. Learn more in [Flexible sampling plans](quality-flexible-sampling-plans.md).

## Examples of automatic generation of quality orders

### Purchasing

In purchasing, if you set the **Event type** field to *Product receipt* and the **Execution** field to *After* on the **Quality associations** page, you get the following results:

- If the **Per updated quantity** option is set to *Yes*, a quality order is generated for every receipt against the purchase order, based on the received quantity and settings in the item sampling. Every time that a quantity is received against the purchase order, new quality orders are generated based on the newly received quantity.
- If the **Per updated quantity** option is set to *No*, a quality order is generated for the first receipt against the purchase order, based on the received quantity. Additionally, one or more quality orders are created based on the remaining quantity, depending on the tracking dimensions. Quality orders aren't generated for subsequent receipts against the purchase order.

### Production

In production, if you set the **Event type** field to *Report as finished* and the **Execution** field to *After* on the **Quality associations** page, you get the following results:

- If the **Per updated quantity** option is set to *Yes*, a quality order is generated based on every finished quantity and settings in the item sampling. Every time that a quantity is reported as finished against the production order, new quality orders are generated based on the newly finished quantity. This generation logic is consistent with purchasing.
- If the **Per updated quantity** option is set to *No*, a quality order is generated the first time that a quantity is reported as finished, based on the finished quantity. Additionally, one or more quality orders are created based on the remaining quantity, depending on the tracking dimensions of the item sampling. Quality orders aren't generated for subsequent finished quantities.

<table>
<thead>
<tr>
<th>Quality specification</th>
<th>Per updated quantity</th>
<th>Per tracking dimension</th>
<th>Result</th>
</tr>
</thead>
<tbody>
<tr>
<td>Percentage: 10%</td>
<td>Yes</td>
<td>
<p>Batch number: No</p>
<p>Serial number: No</p>
</td>
<td>
<p>Order quantity: 100</p>
<ol>
<li>Report as finished for 30
<ul>
<li>Quality order 1 for 3 (10% of 30)</li>
</ul>
</li>
<li>Report as finished for 70
<ul>
<li>Quality order 2 for 7 (10% of the remaining order quantity, which is 70 in this case)</li>
</ul>
</li>
</ol>
</td>
</tr>
<tr>
<td>Fixed quantity: 1</td>
<td>No</td>
<td>
<p>Batch number: No</p>
<p>Serial number: No</p>
</td>
<td>Order quantity: 100
<ol>
<li>Report as finished for 30
<ul>
<li>Quality order 1 for 1 (for the first reported-as-finished quantity, which has a fixed value of 1)</li>
<li>Quality order 2 for 1 (for the remaining quantity, which still has a fixed value of 1)</li>
</ul>
</li>
<li>Report as finished for 10
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
<li>Report as finished for 60
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
</ol>
</td>
</tr>
<tr>
<td>Fixed quantity: 1</td>
<td>Yes</td>
<td>
<p>Batch number: Yes</p>
<p>Serial number: Yes</p>
</td>
<td>
<p>Order quantity: 10</p>
<ol>
<li>Report as finished for 3: 1 for batch number b1, serial number s1; 1 for batch number b2, serial number s2; and 1 for batch number b3, serial number s3
<ul>
<li>Quality order 1 for 1 of batch number b1, serial number s1</li>
<li>Quality order 2 for 1 of batch number b2, serial number s2</li>
<li>Quality order 3 for 1 of batch number b3, serial number s3</li>
</ul>
</li>
<li>Report as finished for 2: 1 for batch number b4, serial number s4; and 1 for batch number b5, serial number s5
<ul>
<li>Quality order 4 for 1 of batch number b4, serial number s4</li>
<li>Quality order 5 for 1 of batch number b5, serial number s5</li>
</ul>
</li>
</ol>
<p><strong>Note:</strong> The batch can be reused.</p>
</td>
</tr>
<tr>
<td>Fixed quantity: 2</td>
<td>No</td>
<td>
<p>Batch number: Yes</p>
<p>Serial number: Yes</p>
</td>
<td>
<p>Order quantity: 10</p>
<ol>
<li>Report as finished for 4: 1 for batch number b1, serial number s1; 1 for batch number b2, serial number s2; 1 for batch number b3, serial number s3; and 1 for batch number b4, serial number s4
<ul>
<li>Quality order 1 for 1 of batch number b1, serial number s1</li>
<li>Quality order 2 for 1 of batch number b2, serial number s2</li>
<li>Quality order 3 for 1 of batch number b3, serial number s3</li>
<li>Quality order 4 for 1 of batch number b4, serial number s4</li>
<li>Quality order 5 for 2, without a reference to a batch number and a serial number</li>
</ul>
</li>
<li>Report as finished for 6: 1 for batch number b5, serial number s5; 1 for batch number b6, serial number s6; 1 for batch number b7, serial number s7; 1 for batch number b8, serial number s8; 1 for batch number b9, serial number s9; and 1 for batch number b10, serial number s10
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
</ol>
</td>
</tr>
</tbody>
</table>

## Related information

- [Quality management processes](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
