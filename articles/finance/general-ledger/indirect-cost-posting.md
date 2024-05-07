---
title: Indirect cost posting
description: Learn how to post indirect costs, create cost groups, and add nodes to the costing sheet for indirect costs, including step-by-step processes.
author: rachelprofitt
ms.author: raprofit
ms.topic: overview
ms.date: 04/25/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: CostSheetDesigner, BOMCostGroup, ProjCategory, CostingVersion, CostSheetCalculationFactor
---

# Indirect cost posting

Indirect costs are costs that aren't directly related to any single activity in the production process. Examples include administrative costs such as employee salaries, accounting department costs, and overhead costs such as rent, utilities, and machinery costs.

## Calculating indirect costs

Microsoft Dynamics 365 Finance doesn't have an automated way to calculate the rate for indirect costs. You must determine your indirect costs, create indirect cost codes, and maintain the rate for each indirect cost in the costing sheet.

The exact process that is used to calculate indirect costs might vary slightly from company to company. However, in general, the process consists of the following basic steps:

1. Create a list of indirect costs to recognize in production. This list might include rent, administrative expenses, accounting fees, and legal fees. It should not include raw material costs or labor costs that are recognized in production routes.
2. Sum all the indirect costs. You can group similar types of indirect costs or keep them separated. Each indirect cost that is configured can have different main accounts that are used for posting to the general ledger.
3. Compare the indirect costs to a factor, which is also referred to as the absorption basis. The factor can be anything that you choose. Here are a few common examples:

    - Revenue
    - Total quantity that is produced
    - Setup time
    - Run time

    You can select the period that you want to calculate your indirect costs for, such as monthly, quarterly, or yearly. The sum of your indirect costs and the sum of your factor should be for the same amount of time. The following formula is used to calculate the indirect cost rate:

    *Indirect cost rate* = *Total indirect cost expenses* &divide; *Total factor*

4. Create indirect cost groups.
5. Configure the costing sheet with your rates.
6. Maintain the cost for your indirect costs in the costing version.

> [!NOTE]
> You can use the **Cost accounting** module to accumulate costs and determine your overhead from different sources, such as production, projects, and the general ledger. For more information, see [Cost accounting](../cost-accounting/cost-accounting-home-page.md).

> [!IMPORTANT]
> Different regulatory establishments have published guidance about the types of costs that can be included as indirect costs or overhead in the cost of your finished goods. Before you start to configure indirect costs, we recommend that you check with your accountant and local regulations to ensure that you're compliant.

## Create cost groups for indirect costs

You must create at least one cost group to use for indirect costs. There is no limit to the number of cost groups that you can use. Consider how you calculate your costs and whether there are different rates for different types of costs. For example, your organization manufactures food products. Some raw materials and finished goods are dry goods, and have one indirect cost for warehousing. Other raw materials and finished goods are refrigerated, and have a higher indirect cost. In this case, you might want to create two cost groups: **Dry material overhead** and **Refrigerated material overhead**.

To create a cost group for indirect costs, follow these steps.

1. Go to **Production control &gt; Setup &gt; Routes &gt; Cost groups**.
2. Select **New** to create a group.
3. In the **Cost group** field, enter a unique name for the cost group, such as **MATOVH**.
4. In the **Name** field, enter a description of the cost group, such as **Material overhead**.
5. In the **Cost group type** field, select **Indirect**.
6. Optional: In the **Behavior** field, select **Fixed cost** or **Variable cost**.

## Configure the costing sheet for indirect costs

After you've created one or more cost groups, you can configure your costing sheet with indirect costs and define your calculation. You might want to group indirect costs in the costing sheet. To group indirect costs, you can create an optional header in the costing sheet. You must create at least one node for each cost group in the costing sheet. For each cost group for indirect costs, you can add one more indirect cost calculations.

### Indirect cost node types

This section describes the different types of nodes for indirect costs.

#### Surcharge

**Surcharge** is one of the most common types of indirect costs. It calculates a percentage of cost from an absorption basis of costs on the production order. You define the absorption basis by selecting the cost groups that are linked to your material or time components in the costing sheet.

For example, a 3-percent surcharge might be added to the cost of production for all the raw materials on a production order.

#### Rate

An indirect cost of the **Rate** type is used to add a fixed amount of cost to the production order from an absorption basis of costs on the production order. The rate can be based on one of three subtypes:

- **Process** – The rate is based on the run time in the route.
- **Setup** – The rate is based on the setup time in the route.
- **Quantity** – The rate is based on the quantity that is produced.

You define the absorption basis by selecting the cost groups that are linked to the material or time components in the costing sheet.

For example, a fixed amount of 2.00 US dollars (USD) is added to each production order, based on the run time in the route for the labor cost group in your costing sheet.

#### Output unit based

An indirect cost of the **Output unit based** type is calculated by multiplying the amount that is specified on the **Rate** FastTab of the costing sheet by the selected subtype. You can select the quantity, weight, or volume of the finished good as the multiplier for the indirect cost.

For example, you use the quantity to calculate 1.50 USD of machine depreciation for each quantity that is produced. As another example, you use the volume to calculate 2.00 USD of refrigeration costs for the volume of space that the finished goods take in your refrigeration units.

#### Input unit based

An indirect cost of the **Input unit based** type is calculated by multiplying the amount of raw materials that is consumed on a production order by an amount. You can use the weight or volume of the inputs on the production order to calculate the total. You can limit the calculation to a subset of materials by selecting one or more cost groups on the **Absorption basis** FastTab of the costing sheet.

For example, you use the volume of inputs for a specific cost group that is linked to refrigerated products to add 1.00 USD to the production order.

### Create a total node for indirect costs in the costing sheet

To create a total node for indirect costs in the costing sheet, follow these steps.

1. Go to **Cost management &gt; Indirect cost accounting policies setup &gt; Costing sheet**.
2. In the tree, select a node that represents the cost of goods that have been manufactured.
3. Select **New** to create a node.
4. In the **Select node type** field, select **Total**.
5. In the **Code** field, enter a unique ID for the node, such as **Production Overheads**.
6. Select the **Header** checkbox.
7. Select the **Total** checkbox.
8. Select **OK**.

### Create an indirect cost group node in the costing sheet

To create an indirect cost group node in the costing sheet, follow these steps.

1. Go to **Cost management &gt; Indirect cost accounting policies setup &gt; Costing sheet**.
2. In the tree, select the node that you want to create the indirect cost under. For example, select the total node for **Production overhead**.
3. Select **New** to create a node.
4. In the **Select node type** field, select **Cost group**.
5. In the **Code** field, enter a unique ID for the node, such as **TRANSP**.
6. In the **Description** field, enter a brief description, such as **Transportation overhead**.
7. Select **OK**.
8. In the **Cost group** field, select the cost group, such as **OVH1: Transport overhead**.

### Create a surcharge indirect cost

To create a surcharge indirect cost in your costing sheet, follow these steps.

1. Go to **Cost management &gt; Indirect cost accounting policies setup &gt; Costing sheet**.
2. In the tree, select the indirect cost group node that you want to create the indirect cost under. For example, select the total node for **TRANSP - Transportation Overhead**.
3. Select **New** to create a node.
4. In the **Select node type** field, select **Surcharge**.
5. In the **Code** field, enter a unique ID for the node, such as **Transportation Surcharge**.
6. Select **OK**.
7. In the **Subtype** field, select **Total**.
8. On the **Absorption basis** FastTab, select **New** to create a cost code.
9. In the **Code** field, select a cost group to use to calculate the surcharge.
10. Optional: Repeat steps 8 through 9 for each additional cost group that you want to use for the calculation.
11. On the **Surcharge** FastTab, select **New** to create a rate.
12. In the **Version** field, select the costing version to add the surcharge to.
13. Optional: In the **Site** field, enter a site to apply the surcharge to.
14. In the **Percent** field, enter the percentage to calculate on production orders from the cost groups that are defined in the **Absorption basis** FastTab.
15. On the **Ledger postings** FastTab, select the main account to use for **Estimated indirect cost absorbed**, **Estimated cost of indirect costs consumed, WIP**, **Indirect cost absorbed**, and **Cost of indirect cost consumed, WIP** fields.
16. Optional: On the **Financial dimensions** FastTab, specify any financial dimensions to enter by default on transactions when they are posted to the general ledger.

The preceding procedure shows how to create an indirect cost of the **Surcharge** type. Similar steps are used to create other types of indirect costs. The following sections describe the differences for each type.

#### Rate

- In step 4, select **Rate** instead of **Surcharge**.
- In step 7, select **Process**, **Setup**, or **Quantity** instead of **Total**.
- In step 11, use the **Rate** FastTab instead of the **Surcharge** FastTab.
- In step 14, enter an amount in the **Amount** field instead of a percentage in the **Percent** field.

#### Output unit based

- In step 4, select **Output unit based** instead of **Surcharge**.
- In step 7, select **Quantity**, **Weight**, or **Volume** instead of **Total**.
- Skip steps 8 through 10.
- In step 11, use the **Rate** FastTab instead of the **Surcharge** FastTab.

#### Input unit based

- In step 4, select **Input unit based** instead of **Surcharge**.
- In step 7, select **Weight** or **Volume** instead of **Total**.
- In step 11, use the **Rate** FastTab instead of the **Surcharge** FastTab.
