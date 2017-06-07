---
# required metadata

title: Dimension hierarchy
description: Use dimension hierarchy to define reporting structure, cost policies, and security setup in Cost acocunting.  
author: YuyuScheller
manager: AnnBe
ms.date: 06/24/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMDimensionHierarchy,
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope:  AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: YuyuScheller
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

## Dimension hierarchy overview  

[!include[banner](../includes/banner.md)]

Dimension hierarchy is used in different places in Cost accounting. It lets you define

-  Reporting structure to fit into organization needs
-  Cost policies
-  Security setup

Here is an example of how a dimension hierarchy can look like. 

![A screenshot that displays a dimension hierarchy](./media/dimension-hierarchy.png)

A dimension hierarchy can be created for the following types of dimensions.

-  Cost element dimensions
-  Cost object dimensions
-  Statistical dimensions

> [!NOTE]
> You can create multiple dimension hierarchies for the same dimension when different perspectives are needed.

> [!NOTE]
> A dimension hierarchy can only be associated with one dimension. 

> [!NOTE]
> A dimension hierarchy can have unlimited levels in its structure and they will all be available in the **Cost control** workspace. When you use Excel or Power BI for reporting purpose, only the first 15 levels of the dimension hierarchy gets exported. The reason is that both Excel and Power BI require a fixed schema.

> [!NOTE]
> A dimension hierarchy is not date effective, which means that any change made to a dimension hierarchy will immediately be saved to the record and you cannot do comparison of the before date and after date.  

## Dimension hierarchy type  

When you create a new dimension hierarchy, you need to select a hierarchy type. Go to **Cost accounting** > **Dimensions** > **Dimension hierarchies**. Click **New** to select a dimension hierarchy type. You can select either **Dimension categorization hierarchy** or **Dimension classification hierarchy**.

### Dimension categorization hierarchy

The dimension categorization hierarchy type is used for reporting purpose. It only supports the cost element dimensions. When you select this type,

-  A dimension member can be associated more than once in the hierarchy structure.
-  A cost element dimension member can be placed in different nodes by assigning a **Cost behavior** to the leaf node.

### Dimension classification hierarchy

This dimension classification hierarchy type is used for defining rules and reporting purposes. It supports all dimensions, such as cost object, cost elements, and statistical dimensions. When you select this type, a dimension member can only be associated once in the hierarchy structure.

## Create and maintain a dimension hierarchy 

A dimension hierarchy is created as a tree structure with nodes and leaf nodes relationships.

-  A node can have 1: n subnodes.
-  A node can’t have both subnodes and leaf nodes assigned.
-  A leaf node can only be assigned at the lowest level in the hierarchy.

### Example

A small company has the following organization structure where Finance and Human resource are departments under Admin and Assembly and Packaging are departments under Production. 

![a diagram that shows the organization structure](./media/dimension-hierarchy-org.png)

A cost object dimension represents all the cost centers in the organization.

| Cost object dimension    | 
|--------------------------|
| Cost centers|

The cost oject dimension that represents all the cost centers can be set up as follows.

| Cost centers                    | Description                      |
|---------------------------------|----------------------------------|
| CC001                           | HR                               |
| CC002                           | Finance                          |
| CC003                           | Tax                              |
| CC007                           | AR/AP                            |
| CC005                           | Assembly                         |
| CC006                           | Packaging                        |

A cost element dimension represents all the cost elements in the organization.

| Cost element dimension    | 
|-------------------------- |
| Cost elements             |

A cost element dimension that represents all the cost elements can be set up as follows.

| Cost elements                   | Description                      |
|---------------------------------|----------------------------------|
| 10001                           | Electricity                      |
| 10010                           | Cleaning                         |
| 10011                           | Heating                          |
| 40001                           | COGS                             |

A dimension hierarchy that meets the organizational reporting requirements can be set up as follows.

Dimension hierarchy details 

| Dimension hierarchy name | Dimension    | Dimension hierarchy type name      | Access list hierarchy |
|--------------------------|--------------|------------------------------------|-----------------------|
| Organization             | Cost centers | Dimension classification hierarchy | No                    |

Dimension hierarchy for reporting can be set up as follows.

|                        |  **Dimension member ranges**  |                      |
|------------------------|-------------------------------|---------------------------|
|    **Nodes**           |  **From dimension member**    |  **To dimension member**  |
|    Organization        |                               |                           |
|      Admin             |                               |                           |
|          Finance       |    CC002                      |    CC003                  |
|                        |    CC007                      |    CC007                  |
|          HR            |    CC001                      |    CC001                  |
|      Production        |                               |                           |
|         Packaging      |    CC005                      |    CC005                  |
|         Assembly       |    CC006                      |    CC006                  |

A dimension hierarchy that meets the policy requirement can be set up as follows. 

Dimension hierarchy details 

| Dimension hierarchy name | Dimension     | Dimension hierarchy type name      |
|--------------------------|---------------|------------------------------------|
| Cost behavior            | Cost elements | Dimension classification hierarchy |

Dimension hierarchy for policy can be set up as follows.

|               | **Dimension member ranges** |                     |
|---------------|-------------------------|---------------------|
| **Nodes**         | **From dimension member**   | **To dimension member** |
| Cost behavior |                         |                     |
|      Fixed cost   | 10001                   | 10011               |
|      Variable cost   | 40001                   | 40010               |

> [!NOTE]
> In the **Dimension member ranges**, a node can contain 1: n dimension member ranges. You can insert dimension member IDs that don’t exist as dimension members yet. This makes the hierarchy resilient for future.  

### Copy a hierarchy

You can copy a current dimension hierarchy as the starting point for the new dimension hierarchy. This can be useful if you want to compare the previous dimension hierarchy to the new dimension hierarchy.

### Rearrange nodes in the hierarchy

You can move up and down a node within its current level in the structure to rearrange the order of nodes for reporting in the **Cost control** workspace.

Move a node to a new designated location in the hierarchy by selecting a target node. There are two ways to move a node: Move below and Move after. 

-   **Move below**

    Moves the highlighted node in the hierarchy from its current position and inserts it **under** the selected target node.

-   **Move after**

    Moves the highlighted node in the hierarchy from its current position and inserts it **after** the selected target node at its level of the hierarchy.

> [!NOTE] 
> The order of the nodes is not maintained when exporting data to Excel or Power BI because these tools use alphanumeric sorting order by default and you should manually rearrange the order.

## Define dimension hierarchies for reporting

Dimension hierarchies are important for reporting. It lets you define the specific structure that fits into the individual organization. The aggregations performed at the node level of the dimension hierarchy allow stakeholders at any level of the organization to see data at any level.

Dimension hierarchies are available in the reporting tools listed below. This ensures consistent reporting structure. 

Dimension hierarchies are available in the following reporting tools. This ensures consistency in reporting structure.

-   Cost control workspace (Dynamics 365 for Operations client)

    -   Controlled by configuration

-   Cost control workspace (Dynamics 365 for Operations mobile application)

    -   Controlled by configuration

-   Microsoft Excel

    -   Provides the option to select specific dimension hierarchies per export
        definition

        -   One cost element dimension hierarchy (mandatory)

        -   One cost object dimension hierarchy (optional)

        -   One statistical dimension hierarchy (optional)

-   Microsoft Power BI

    -   All dimension hierarchies are available
    
If you create reports using **Excel** or **Power BI**, only the first 15 levels of the dimension hierarchies will be exported. This is because a fixed schema is required in Excel and Power BI. In case a hierarchy has more than 15 levels, these levels will not be exported. The normalized table contains a record per all dimension members in the hierarchy so an automated aggregation will take place. This ensures that the balances at any of the 15 available levels in the hierarchy are still correct.

Here is an example of how a dimension hierarchy can look lik in the reporting structure.

| Cost object dimension hierarchy - level 1 | Cost object dimension hierarchy - level 2 | Cost object dimension hierarchy - level 3 | Cost object dimension hierarchy - level 4 | Cost object dimension hierarchy - level 15 |
|-------------------------------------------|-------------------------------------------|-------------------------------------------|-------------------------------------------|--------------------------------------------|
| Organization                              | Admin                                     | Finance                                   | CC002                                     |                                            |
| Organization                              | Admin                                     | Finance                                   | CC003                                     |                                            |
| Organization                              | Admin                                     | Finance                                   | CC007                                     |                                            |
| Organization                              | Admin                                     | HR                                        | CC001                                     |                                            |
| Organization                              | Production                                | Packaging                                 | CC005                                     |                                            |
| Organization                              | Production                                | Assembly                                  | CC006                                     |                                            |

### Update the dimension hierarchies used for reporting 

Over time, dimension hierarchies used for reporting in these tools discussed above will need to be updated. You can update any dimension hierarchies by refreshing the client.

-   Cost control workspace (Dynamics 365 for Operations client)

-   Cost control workspace (Dynamics 365 for Operations mobile application)

Any update in dimension hierarchies will be picked up every 24 hours by a pre-cached job. After refreshing the exported data, the updated dimension hierarchies are available in

-   Microsoft Excel

-   Microsoft Power BI

> [!NOTE] 
> To manually trigger a refresh of the dimension hierarchy cache, you can create a new export to Excel for the dimension hierarchy or hierarchies that need to be refreshed.

## Define dimension hierarchies for cost policy

Cost accounting consists of multiple policies where detailed rules are defined. The list below shows the policies for which you need to define one or more dimension hierarchies.

-   Cost behavior
-   Cost distribution
-   Cost allocation
-   Cost rollup

Dimension hierarchies make it easy to create rules. You can leverage the aggregations of dimension members provided by dimension hierarchy levels to avoid creating rules for every single dimension member. In case you have overlapping rules, you must define specific rules, which will be considered by the system when performing the overhead calculation.

### Example: Define a cost behavior policy

A new cost behavior policy can be created and appropriate dimension hierarchies are assigned to the policy as follows.

Cost behavior policy

| Policy name   | Cost element dimension hierarchy | Cost object dimension hierarchy | Accounting currency |
|---------------|----------------------------------|---------------------------------|---------------------|
| Cost behavior | Cost behavior                    | Organization                    | USD                 |

Rules

| Cost element dimension hierarchy node | Cost object dimension hierarchy node | Fixed percentage | Fixed amount | Valid from | Valid to |
|---------------------------------------|--------------------------------------|------------------|--------------|------------|----------|
| Fixed cost                            | Organization                         | 100,00           | 0,00         | 1/1/2017   | Never    |
| 10001                                 | Organization                         | 0,00             | 150,00       | 1/1/2017   | Never    |
| 10001 (*)                    | Finance                              |                  | 50,00        | 1/1/2017   | Never    |
| Cost behavior or Variable cost (**)     | Organization                         | 0,00             | 0,00         | 1/1/2017   | Never    |

- *: The variable cost node is not required, if a cost is not classified as fixed cost, then it must be variable cost.

- **: A detailed rule is created for the combination of cost element member 10001 and all cost object members aggregated under the hierarchy level Finance. (CC002, CC003, CC007)

The rules listed above demonstrate the flexibility provided by the dimension hierarchies. High-level rules can be defined to minimize maintenance and detailed rules can be defined to fit into a specific business objective.

Updates performed on dimension hierarchies that are used in rules will be brought forward automatically by the system.

In case a level of granularity in the rules are no longer required, the rule can be expired.

For example, a specific cost behavior rule for the cost object dimension hierarchy node Finance is no longer required. Click **Expire rule** to expire the rule.

| Cost element dimension hierarchy node | Cost object dimension hierarchy node | Fixed percentage | Fixed amount | Valid from | Valid to  |
|---------------------------------------|--------------------------------------|------------------|--------------|------------|-----------|
| Fixed cost                            | Organization                         | 100,00           | 0,00         | 1/1/2017   | Never     |
| 10001                                 | Organization                         | 0,00             | 150,00       | 1/1/2017   | Never     |
| 10001 (**)                        | Finance                              |                  | 50,00        | 1/1/2017   | 20/1/2017 |
| Cost behavior or Variable cost (*)| Organization                         | 0,00             | 0,00         | 1/1/2017   | Never     |

Any overhead calculation that is executed after January 20, 2017 will no longer consider this rule.

> [!NOTE] 
> The **Valid from** and **Valid to** fields are date and time effective. You can expire the rule and run a new overhead calculation on the same day.

## Dfine dimension hierarchies for security setup

Cost accounting data should be made available to all managers who are responsible for a reporting unit, which in Cost accouting terminology are represented as a cost object or a set of cost objects.

Potentially, all managers will be able to access the high sensitive business data, for example, revenues and margins, it is important to secure that only the data that are relevant to them is displayed. You define dimension hierarchies to control data security.

-   This only applies when the dimension value selected in the **Dimension hierarchy** reference is a **Cost object dimension**.

-   Only one **Dimension hierarchy** per **Cost object dimension** can be enabled in the **Access list hierarchy**.

Dimension hierarchy details

| Dimension hierarchy name | Dimension    | Dimension hierarchy type name      | Access list hierarchy |
|--------------------------|--------------|------------------------------------|-----------------------|
| Organization             | Cost centers | Dimension classification hierarchy | **Yes**               |

A new FastTab **Users** are visible in the hierarchy designer and one or several **User ID**s can be inserted at each node in the hierarchy.

|              | **Users**        | Dimension member ranges |                     |
|--------------|------------------|-------------------------|---------------------|
| Nodes        | User ID          | From dimension member   | To dimension member |
| Organization | Benjamin, Claire |                         |                     |
|   Admin      | April            |                         |                     |
|     - Finance           | Alicia           | CC002                   | CC003               |
|              |                  | CC007                   | CC007               |
|     - HR     | Arnie            | CC001                   | CC001               |
|   Production | David            |                         |                     |
|     - Packaging        | Ellen            | CC005                   | CC005               |
|     - Assembly| Chris            | CC006                   | CC006               |

> [!NOTE] 
> Cost accountants should be assigned to the top level of the hierarchy, so they can see all entries in Cost accounting.

To enable the **Access list hierarchy** and its security settings, go to **Cost accounting** > **Setup** > **Parameters** > **General**. Select the parameter **Enable view access for cost object dimension members**.

The Access list hierarchy settings are used to control data displayed in the following areas.

-   Cost control workspace (Dynamics 365 for Operation client)

    -   Data in forms used to drill through scenarios

-   Cost control workspace (Dynamics 365 for Operations mobile application)

    -   Balances in cards

-   Microsoft Power BI

    -   Data displayed in Power BI visualizations

    -   Data Power BI visualizations embedded into Dynamics 365 for operation
        client

> [!NOTE] 
> Before **Access list hierarchy** can affect data in Power BI, access level hierarchy and row level security in Power BI needs to be paired. For more information, see <a href="/dynamics365/operations/dev-itpro/analytics/setup-security-cost-accounting-content-pack">Set up security for Cost accounting content pack</a>.

> [!NOTE] 
> Exporting data to Excel is not secured by **Access list hierarchy**. Therefore, this reporting tool should only be used by cost accountants and managers who need to have full access to view the data.
