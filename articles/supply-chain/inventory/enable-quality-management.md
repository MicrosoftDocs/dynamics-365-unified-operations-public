---
# required metadata

title: Quality management overview
description: This topic describes how you can use quality management in Dynamics 365 Supply Chain Management to help improve product quality within your supply chain.
author: perlynne
manager: tfehr
ms.date: 10/15/2019
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestAssociationTable, InventTestGroup, InventTestItemQualityGroup, InventTestTable, InventTestVariable, InventTestVariableOutcome
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Quality management overview

[!include [banner](../includes/banner.md)]

This topic describes how you can use quality management in Dynamics 365 Supply Chain Management to help improve product quality within your supply chain.

Quality management can help you manage turnaround times when you handle nonconforming products, regardless of their point of origin. Because diagnostic types are linked to correction reporting, Supply Chain Management can schedule tasks to correct problems and prevent them from recurring.

In addition to functionality for managing nonconformance, quality management includes functionality for tracking issues by problem type (even internal problems), and for identifying solutions as short-term or long-term. Statistics about key performance indicators (KPIs) provide insight into the history of previous nonconformance issues and the solutions that were used to correct them. You can use historical data to review the effectiveness of previous quality measures and determine appropriate measures to use in the future.

When you set up a quality association, Supply Chain Management can generate quality orders for various business processes, events, and conditions. The quality association can cover a specific item, a specific group of items, or all items.

## Examples of the use of quality management
Quality management is flexible and can be implemented in various ways to meet the requirements of specific levels of supply chain operations. The following examples illustrate possible uses of these features:

-   Automatically start a quality control process, based on predefined criteria (upon warehouse registration of a purchase order from a specific vendor).
-   Block inventory during inspection to prevent non-approved inventory from being used (full blocking of purchase order quantities).
-   Use item sampling as part of a quality association to define the amount of current physical inventory that must be inspected. Sampling can be based on fixed quantities, a percentage, or full license plate.

> [!NOTE]
> The _Quality management for warehouse processes_ feature extends the capabilities of quality management. If you are using this feature, then see [Quality management for warehouse processes](quality-management-for-warehouses-processes.md) for examples of how quality management works when it's enabled.

-   Create quality orders for partial receipts. To create a quality order that is based on the quantity that is physically received with an order, you must select the **Per updated quantity** check box on the **Item sampling** form.
-   Create test types that include minimum, maximum, and target test values, and perform qualitative-versus-quantitative testing that has predefined validation results.
-   Specify an acceptable quality level (AQL) to control quality measure tolerances.
-   Specify the resources that an inspection operation requires, such as a test area and test instruments.

## Working with quality associations
The business process that uses a quality association can be related to various source documents, such as purchase orders, sales orders, or production orders.

Each quality association record defines the set of tests, the AQL, and the sampling plan that applies to the quality orders that are generated. You must define a quality association record for each variation in a business process. For example, you can set up a quality association that generates a quality order when a purchase order product receipt is updated. Depending on the setup of the execution plan, the triggering process itself can be blocked while there is an open quality order, or the next processes, such as purchase order invoicing, can be blocked.

**Note:** While there are open quality orders, inventory quantities are automatically blocked from being issued. Depending on the **Full blocking** setting on the **Item samplings** page, the quantity is either the quantity on the quality order or the quantity on the source document line.

For a given business process, the quality association record identifies the event and the conditions that a quality order is generated for. The conditions can be specific to either a site or a legal entity. A quality order that involves destructive tests can be generated only when on-hand inventory exists for the event.

The following examples illustrate how a quality association record is defined for the variations in each business process. For each example, the following table summarizes the events and conditions that are defined by a quality association record.

<table>
<tbody>
<tr>
<th>Reference type</th>
<th>Event type</th>
<th>Execution</th>
<th>Event blocking</th>
<th>Document reference</th>
</tr>
<tr>
<td>Inventory</td>
<td>Not applicable</td>
<td>Not applicable</td>
<td>None</td>
<td>All</td>
</tr>
<tr>
<td rowspan="7">Sales</td>
<td rowspan="4">Picking process is scheduled</td>
<td rowspan="4">Before</td>
<td>None</td>
<td rowspan="22">Specific ID, Group, or All only</td>
</tr>
<tr>
<td>Picking process</td>
</tr>
<tr>
<td>Packing slip</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="3">Packing slip</td>
<td rowspan="3">Before</td>
<td>None</td>
</tr>
<tr>
<td>Packing slip</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="15">Purchase</td>
<td rowspan="7">Receipt list</td>
<td rowspan="4">Before</td>
<td>None</td>
</tr>
<tr>
<td>Receipt list</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="3">After</td>
<td>None</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="3">Registration</td>
<td rowspan="3">Not applicable</td>
<td>None</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="5">Product receipt</td>
<td rowspan="3">Before</td>
<td>None</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="2">After</td>
<td>None</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="8">Production</td>
<td rowspan="3">Registration</td>
<td rowspan="3">Not applicable</td>
<td>None</td>
<td rowspan="12">All</td>
</tr>
<tr>
<td>Report as finished</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td rowspan="5">Report as finished</td>
<td rowspan="3">Before</td>
<td>None</td>
</tr>
<tr>
<td>Report as finished</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td rowspan="2">After</td>
<td>None</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td rowspan="4">Quarantine</td>
<td rowspan="3">Report as finished</td>
<td rowspan="2">Before</td>
<td>Report as finished</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td>After</td>
<td>End</td>
</tr>
<tr>
<td>End</td>
<td>Before</td>
<td>End</td>
</tr>
<tr>
<td rowspan="3">Route operation</td>
<td rowspan="3">Report as finished</td>
<td rowspan="2">Before</td>
<td>None</td>
<td rowspan="3">Specific ID, Group, or All, and Resource specific, Group, or All</td>
</tr>
<tr>
<td>Report as finished</td>
</tr>
<tr>
<td>After</td>
<td>None</td>
</tr>
<tr>
<td rowspan="3">Co-product production</td>
<td>Registration</td>
<td>Not applicable</td>
<td rowspan="3">None</td>
<td rowspan="3">All</td>
</tr>
<tr>
<td rowspan="2">Report as finished</td>
<td>Before</td>
</tr>
<tr>
<td>After</td>
</tr>
</tbody>
</table>

The following table provides more information about how quality orders can be generated for specific types of processes.
<div class="tableSection">

<table>
<tbody>
<tr>
<th>Type of process</th>
<th>When quality orders can be automatically generated</th>
<th>When quality orders can be generated if destructive testing is required</th>
<th>Condition information</th>
<th>Manual generation information</th>
</tr>
<tr>
<td>Purchase order</td>
<td>Before or after a receipts list or product receipt for the material that is received is posted</td>
<td>After the product receipt for the material that is received is posted, because the material must be available for destructive testing</td>
<td>The requirement for a quality order can reflect a particular site, item, or vendor, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a purchase order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Quarantine order</td>
<td>Before or after the quarantine order is reported as finished or ended</td>
<td>Quality orders that require destructive tests can&#39;t be generated. It&#39;s assumed that the quarantine order functionality handles the disposition of the material that is destroyed.</td>
<td>The requirement for a quality order can reflect a particular site, item, or vendor, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a quarantine order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Sales order</td>
<td>Before a scheduled picking process or packing slip update for the items that are being shipped</td>
<td>At any step</td>
<td>The requirement for a quality order can reflect a particular site, item, or customer, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a sales order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Production order</td>
<td>Before or after the finished quantity for the production order is reported</td>
<td>After the finished quantity for the production order is reported</td>
<td>The requirement for a quality order can reflect a particular site or item, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a production order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Production order that has a route operation</td>
<td>Before or after the report is finished for an operation</td>
<td>After the reporting production is finished for the last operation</td>
<td>The requirement for a quality order can reflect a particular, site, item, or operations resource, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a route operation can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Inventory</td>
<td>A quality order cannot be automatically generated for a transaction in an inventory journal or for transfer order transactions.</td>
<td></td>
<td></td>
<td>A quality order must be created manually for an item&#39;s inventory quantity. Physical on-hand inventory is required.</td>
</tr>
</tbody>
</table>

## Quality order auto-generation examples

### Purchasing

In purchasing, if you set the **Event type** field to **Product receipt** and the **Execution** field to **After** on the **Quality associations** page, you get the following results: 

- If the **Per updated quantity** option is set to **Yes**, a quality order is generated for every receipt against the purchase order, based on the received quantity and settings in the item sampling. Every time that a quantity is received against the purchase order, new quality orders are generated based on the newly received quantity.
- If the **Per updated quantity** option is set to **No**, a quality order is generated for the first receipt against the purchase order, based on the received quantity. Additionally, one or more quality orders are created based on the remaining quantity, depending on the tracking dimensions. Quality orders aren't generated for subsequent receipts against the purchase order.

### Production

In production, if you set the **Event type** field to **Report as finished** and the **Execution** field to **After** on the **Quality associations** page, you get the following results:

- If the **Per updated quantity** option is set to **Yes**, a quality order is generated based on every finished quantity and settings in the item sampling. Every time that a quantity is reported as finished against the production order, new quality orders are generated based on newly finished quantity. This generation logic is consistent with purchasing.
- If the **Per updated quantity** option is set to **No**, a quality order is generated the first time that a quantity is reported as finished, based on the finished quantity. Additionally, one or more quality orders are created based on the remaining quantity, depending on the tracking dimensions of the item sampling. Quality orders aren't generated for subsequent finished quantities.

<table>
<tbody>
<tr>
<th>Quality specification</th>
<th>Per updated quantity</th>
<th>Per tracking dimension</th>
<th>Result</th>
</tr>
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
<li>Quality order #1 for 3 (10% of 30)</li>
</ul>
</li>
<li>Report as finished for 70
<ul>
<li>Quality order #2 for 7 (10% of the remaining order quantity, which equals 70 in this case)</li>
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
<li>Quality order #1 for 1 (for the first reported-as-finished quantity, which has a fixed value of 1)</li>
<li>Quality order #2 for 1 (for the remaining quantity, which still has a fixed value of 1)</li>
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
<li>Report as finished for 3: 1 for #b1, #s1; 1 for #b2, #s2; and 1 for #b3, #s3
<ul>
<li>Quality order #1 for 1 of batch #b1, serial #s1</li>
<li>Quality order #2 for 1 of batch #b2, serial #s2</li>
<li>Quality order #3 for 1 of batch #b3, serial #s3</li>
</ul>
</li>
<li>Report as finished for 2: 1 for #b4, #s4; and 1 for #b5, #s5
<ul>
<li>Quality order #4 for 1 of batch #b4, serial #s4</li>
<li>Quality order #5 for 1 of batch #b5, serial #s5</li>
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
<li>Report as finished for 4: 1 for #b1, #s1; 1 for #b2, #s2; 1 for #b3, #s3; and 1 for #b4, #s4
<ul>
<li>Quality order #1 for 1 of batch #b1, serial #s1</li>
<li>Quality order #2 for 1 of batch #b2, serial #s2</li>
<li>Quality order #3 for 1 of batch #b3, serial #s3</li>
<li>Quality order #4 for 1 of batch #b4, serial #s4</li>
</ul>
<ul>
<li>Quality order #5 for 2, without a reference to a batch and a serial number</li>
</ul>
</li>
<li>Report as finished for 6: 1 for #b5, #s5; 1 for #b6, #s6; 1 for #b7, #s7; 1 for #b8, #s8; 1 for #b9, #s9; and 1 for #b10, #s10
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
</ol>
</td>
</tr>
</tbody>
</table>

> [!NOTE]
> The *Quality management for warehouse processes* feature adds capabilities for quality order processing for production with **Event type** set to *Report as finished* and **Execution** set to *After*, and for purchases with **Event type** set to *Registration*. For details, see [Quality management for warehouse processes](quality-management-for-warehouses-processes.md).

## Quality management pages
<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>Page</th>
<th>Description</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Quality associations</td>
<td>See the previous sections of this article.</td>
<td>A quality association defines all the following information for a quality order that is generated:
<ul>
<li>The transaction event</li>
<li>The set of tests that must be performed on the items</li>
<li>The AQL</li>
<li>The sampling plan</li>
</ul>
You must define a quality association for each variation in a business process that requires automatic generation of quality orders. For example, a quality order can be generated in the business processes for purchase orders, quarantine orders, sales orders, and production orders.</td>
</tr>
<tr class="even">
<td>Tests</td>
<td>Use this page to define and view the individual tests that determine whether your products meet quality specifications. You can assign one or more individual tests to a test group. In this case, you also specify test-specific information, such as the acceptable measurement values. Measurement values are used for quantitative tests, and test variables are used for qualitative tests.
<ul>
<li>A quantitative test has a test type of <strong>Integer</strong> or <strong>Fraction</strong>, and also has a designated unit of measure. Quality specifications and test results are expressed as numbers.</li>
<li>A qualitative test has a test type of <strong>Option</strong>. Qualitative tests require additional information about the test variable that is being measured and its enumerated options. Quality specifications and test results are expressed according to an outcome.</li>
</ul></td>
<td>A manufacturing company performs two tests on purchased material: a quantitative test about material quality and a qualitative test about packaging damage. The company defines additional information about the qualitative test to identify the test variable (damaged packaging) and its outcomes. The company uses the <strong>Test groups</strong> page to assign the two tests to a test group and to specify the test-specific information. The test group is assigned to a quality order, so that the company can report test results for the two tests.</td>
</tr>
<tr class="odd">
<td>Test groups</td>
<td>Use this page to set up, edit, and view test groups and the individual tests that are assigned to a test group. The upper pane displays test groups, and the lower pane displays the tests that are assigned to a selected test group. You assign several policies to a test group, such as a sampling plan, an AQL, and the requirement for destructive testing. When you assign an individual test to a test group, you define additional information, such as the sequence, documents, and validity dates. For a quantitative test, the information that you define also includes the acceptable measurement values. For a qualitative test, the information includes the test variable and default outcome. The test group that is assigned to a quality order defines the default set of tests that must be performed on the specified item. However, you can add, delete, or change tests on the quality order. Test results are reported for each test on a quality order.</td>
<td>A manufacturing company defines a test group for each variation of its quality guidelines. The various test groups reflect differences in the sampling plans, the sets of tests that must be performed together, the AQL, and other factors. For quantitative tests, there are also differences in the acceptable measurement values. To enforce its quality guidelines, the company assigns a test group to each rule for automatically generating quality orders on the <strong>Quality associations</strong> page, and also assigns a test group to quality orders that are manually created.</td>
</tr>
<tr class="even">
<td>Item quality groups</td>
<td>Use this page to set up, edit, and view the items that are assigned to a quality group or the quality groups that are assigned to an item. A quality group represents common testing requirements for items. After you define the test requirements on the <strong>Test groups</strong> page, you can define the rules for automatically generating quality orders. To simplify the process, you don&#39;t define rules for individual items. Instead, you define rules for a quality group, by using the <strong>Quality associations</strong> page. You can also use the <strong>Item quality groups</strong> page for a selected quality group to assign relevant items to that group. You can also use the <strong>Item quality groups</strong> page for a selected item to assign relevant quality groups to that item.</td>
<td>A manufacturing company purchases various raw materials that have the same testing requirements for incoming inspection. The company defines a quality group and then assigns the item numbers that are associated with the raw materials to that group. Later, the company purchases a new type of raw material that has the same testing requirements. Instead of setting up new testing requirements for the new material, the company adds the item number for the new material to the existing quality group. The same manufacturing company also produces items that have the same production testing requirements and ships items that have the same requirement for pre-shipment testing. The company defines two additional quality groups and then assigns the relevant item numbers to each group.</td>
</tr>
<tr class="odd">
<td>Test variables</td>
<td>Use this page to define and view the variables that are associated with a qualitative test. For each variable, you define enumerated outcomes that represent the possible options. You define tests on the <strong>Tests</strong> page. For qualitative tests, you must set the test type to <strong>Option</strong>. Use the <strong>Test groups</strong> page to assign a test variable to an individual test.</td>
<td>A manufacturing company that produces cookies uses an inspection test for the finished product. This inspection test has several variables. One variable is taste, and the possible outcomes for this variable are good and bad. A second variable is color, and the possible outcomes are too dark, too light, and correct.</td>
</tr>
<tr class="even">
<td>Test variable outcomes</td>
<td>Use this page to set up, edit, and to view the possible test results for a test variable that is associated with a qualitative test. For each outcome, you assign a <strong>pass</strong> or <strong>fail</strong> status. You must define a variable and its outcomes for each qualitative test that is defined on the <strong>Tests</strong> page. (For qualitative tests, the test type is set to <strong>Option</strong> on the <strong>Tests</strong> page.) Use the <strong>Test groups</strong> page to assign a test variable and the default outcome to an individual qualitative test.</td>
<td>A manufacturing company that produces cookies uses an inspection test for the finished product. This inspection test has of several variables. One variable is taste, and the possible outcomes for this variable are good and bad. A second variable is color, and the possible outcomes are too dark, too light, and correct. A status of <strong>pass</strong> or <strong>fail</strong> is assigned to each outcome. During the inspection test for each variable, the inspector reports the test result by selecting one of the outcomes.</td>
</tr>
</tbody>
</table>



Additional resources
--------

[Quality management processes](quality-management-processes.md)

[Nonconformance management](enable-nonconformance-management.md)

[Quality management for warehouse processes](quality-management-for-warehouses-processes.md)
