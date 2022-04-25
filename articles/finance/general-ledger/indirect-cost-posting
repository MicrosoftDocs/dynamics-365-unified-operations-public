---
# required metadata

title: Indirect cost posting
description: Details about how to post indirect costs, create cost groups, add nodes to the costing sheet and so on for indirect costs.
author: raprofit
ms.date: 04/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CostSheetDesigner, BOMCostGroup, ProjCategory, CostingVersion, CostSheetCalculationFactor
# ROBOTS: 
audience: Application User
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit

---

# Indirect cost posting

Indirect costs are costs that are not directly related to a single activity in the production activity. Examples of indirect costs might include administrative costs such as salaries of employees, accounting department costs, and overhead costs such as rent, utilities, and machinery costs.

## Calculating indirect costs

Dynamics 365 does not have an automated way to calculate the rate for indirect costs, so you will need to determine your indirect costs and create indirect cost codes and maintain the rate for each indirect cost in your costing sheet. The exact process that you use to calculate indirect costs might vary slightly from company to company. The basic process includes several steps.

1.  Create a list of indirect costs to recognize in production. This list might include rent, administrative expenses, accounting, legal fees, and so on. The list should not include raw material costs or labor costs that are recognized in your routes.
2.  Sum all the indirect costs. You can choose to group similar types of indirect costs or keep them separated. Each indirect cost you configure in Dynamics 365 can have different main accounts for posting to the general ledger.
3.  Compare the indirect costs to a factor, which is also referred to as the absorption basis. The factor can be anything you choose, but a few common examples are the revenue, total quantity produced, setup time, run time, and so on. You can choose the period that you want to calculate your indirect costs for such as monthly, quarterly, or yearly. The sum of your indirect costs and sum of your factor should be added for the same amount of time. The formula for calculating your indirect cost rate is:

Indirect cost rate = Total indirect cost expenses / Total factor

4.  Create indirect cost groups.
5.  Configure the costing sheet with your rates.
6.  Maintain the cost for your indirect costs in the Costing version.

> [!NOTE]
> You can use the Cost accounting module to help accumulate costs and determine your overheads from a variety of sources including production, projects, and the general ledger. For more information, refer to [Cost accounting home page](/cost-accounting/cost-accounting-home-page.md).

> [!IMPORTATNT] 
> Different regulatory establishments have published guidance on what types of costs can be included as indirect costs or overheads in the costs of your finished goods. Before you start to configure indirect costs, we recommend that you check with your accountant and local regulations to ensure you are complaint.

## Create cost groups for indirect costs

You will need to create at least one cost group to be used for indirect costs. There is no limit to the number of cost groups that you create; however, consider how you calculate your costs and if there are different rates for different types of costs. For example, your organization manufactures food products. Some raw materials and finished goods are dry goods and carry one indirect cost for warehousing, while other raw materials and finished goods are refrigerated, which have a higher indirect cost. In this example, you might want to create two cost groups. One for Dry Material Overheads and another for Refrigerated Material Overheads.

To create a cost group for indirect costs, follow these steps.

1.  Open **Production control &gt; Setup &gt; Routes &gt; Cost groups**.
2.  Click **New** to create a new group.
3.  In the **Cost group** field, enter a unique name for the cost group such as MATOVH.
4.  In the **Name** field, enter a description for the cost group such as Material Overheads.
5.  In the **Cost group type** field, select Indirect.
6.  Optionally, select the **Behavior** as Fixed cost or Variable cost.

## Configure the costing sheet for indirect costs

After you have created one or more cost groups, you can start to configure your costing sheet with your indirect costs and define your calculation. You may want to group your indirect costs in the costing sheet; you can do this by creating an optional header in your costing sheet. You will need to also create at least one node for each cost group in your costing sheet. Under each cost group for indirect costs, you can add one more indirect cost calculations.

### Indirect cost node types

**Surcharge**

A surcharge is one of the most common types of indirect costs. This type of cost calculates a percentage of cost from an absorption basis of costs in the production order. The absorption basis is defined by selecting the cost groups that are linked to your material or time components in the costing sheet. An example of a surcharge is 3% is added to the cost of the production for all the raw materials in a production order.

**Rate**

A rate indirect cost type is used to add a fixed amount of cost to the production order from an absorption basis of costs in the production order. The rate can be based on one of three sub types: Process, Setup, or Quantity. Process is based on the run time from the route, Setup is based on the Setup time in the route, and Quantity is based on the Quantity produced. The absorption basis is defined by selecting the cost groups that are linked to the material or time components in the costing sheet. An example of a rate is $2.00 USD are added to each production order based on the run time on the route for the labor cost group in your costing sheet.

**Output unit based**

An output unit based indirect cost is calculated by multiplying the amount that you specify in the Rate FastTab by the Subtype that you select. You can select the quantity, weight, or volume of the finished good to be the multiplier for the indirect cost. One example is to use the quantity to calculate $1.50 USD of machine depreciation for each quantity produced. Another example is to use the volume to calculate $2.00 of refrigeration costs for volume of space of the finished goods in your refrigeration units.

**Input unit based**

An input unit based indirect cost is calculated by multiplying the amount of raw materials that are consumed in a production order by an amount. You can use the weight or volume of the inputs in the production order to calculate the total. You can limit the calculation to a subset of materials by selecting one or more cost groups in the Absorption basis FastTab. One example is to use the volume of inputs for a specific cost group linked to refrigerated products to add $1.00 USD to the production order.

### Create a total node in the costing sheet for indirect costs
To optionally create a total node in the costing sheet for indirect costs, follow these steps.

1.  Open **Cost management > Indirect cost accounting policies setup > Costing sheet**.
2.  Select a node in your tree that represents your costs of goods manufactured.
3.  Click **New** to create a new node.
4.  In the **Select node type** field, select Total.
5.  Enter a unique **Code** such as Production Overheads.
6.  Select the **Header** check box.
7.  Select the **Total** check box.
8.  Click **OK** to create the node.

### Create an indirect cost group node in your costing sheet
To create an indirect cost group node in your costing sheet, follow these steps.

1.  Open **Cost management &gt; Indirect cost accounting policies setup &gt; Costing sheet**.
2.  Select a node in your tree that you want to create the indirect cost under, for example select your total node for Production Overheads.
3.  Click **New** to create a new node.
4.  In the **Select node type** field, select Cost group.
5.  In the **Code** field, enter a unique ID for the node such as TRANSP.
6.  In the **Description** field, enter a brief description such as Transportation Overheads.
7.  Click **OK**.
8.  In the **Cost group** field, select the cost group such as OVH1: Transport Overheads

### Create a surcharge indirect cost 
To create a surcharge indirect cost in your costing sheet, follow these steps.

1.  Open **Cost management &gt; Indirect cost accounting policies setup &gt; Costing sheet**.
2.  Select an indirect cost group node in your tree that you want to create the indirect cost under, for example select your total node for TRANSP - Transportation Overheads.
3.  Click **New** to create a new node.
4.  In the **Select node type** field, select Surcharge.
5.  In the **Code** field, enter a unique ID for the node such as Transportation Surcharge.
6.  Click **OK**.
7.  In the **Subtype** field, select Total.
8.  On the **Absorption basis** FastTab, click **New** to add a cost code.
9.  In the **Code** field select a cost group to be used in the calculation of the surcharge.
10. Optionally, repeat steps 8-9 for each additional cost group to be used in the calculation.
11. On the **Surcharge** FastTab, click **New** to create a new rate.
12. In the **Version** field, select the costing version to add the surcharge to.
13. In the **Site** field, optionally enter a site to apply the surcharge to.
14. In the **Percent** field, enter the percentage to be calculated on production orders from the cost groups defined in the **Absorption basis** FastTab.
15. Click to expand the **Ledger postings** FastTab.
16. Select the main account to be used for **Estimated indirect cost absorbed**, **Estimated cost of indirect costs consumed, WIP**, **Indirect cost absorbed**, and **Cost of indirect cost consumed, WIP** fields.
17. Optionally, expand the **Financial dimensions** FastTab and specify any financial dimensions to default on the transactions when posting to the general ledger.

Similar steps are used to create other types of indirect costs. The differences are described below.

**Rate**
-   In step 4, select **Rate** instead of **Surcharge**.
-   In step 7, select either Process, Setup, or Quantity for the **Subtype**.
-   In step 11, use the **Rate** FastTab instead of the **Surcharge** FastTab.
-   In step 14, enter an **Amount** instead of a **Percent**.

**Output unit based**
-   In step 4, select **Output unit based** instead of **Surcharge**
-   In step 7, select either Quantity, Weight, or Volume for the **Subtype**.
-   Skip steps 8-10.
-   In step 11, use the **Rate** FastTab instead of the **Surcharge** FastTab.

**Input unit based**
-   In step 4, select **Input unit based** instead of **Surcharge**.
-   In step 7, select either Weight or Volume for the **Subtype**.
-   In step 11, use the **Rate** FastTab instead of the **Surcharge** FastTab.
