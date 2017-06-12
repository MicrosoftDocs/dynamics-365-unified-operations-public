---
# required metadata

title: Statistical dimension members and statistical measure provider template
description: Statistical dimension members serve two purposes. They can be used as allocation base in policies such as cost distribution and cost allocation. They can also be used for reporting non-monetary cost consumption.
author: YuyuScheller
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMCostAccountingLedgerSourceEntryProvider, CAMStatisticalDimension, CAMAXStatisticalMeasureProviderTemplate
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

# Statistical dimension members and statistical measure provider template

[!include[banner](../includes/banner.md)]

A statistical dimension and its members are used to register and control non-monetary entries in Cost accounting. Statistical dimension members can serve two purposes:

1.  As allocation base in policies such as cost distribution or cost allocation.

2.  For reporting non-monetary consumption.

## Statistical dimension

A **Statistical dimension** has a unique name with a set of unique dimension members. The **Statistical dimension** is assigned to a **Cost accounting ledger ID**. This relationship ties all corresponding statistical dimension members to the **Cost accounting ledger** and **Statistical entries** will be created in the context of **Cost accounting ledger**.

> [!NOTE]
> A **Statistical dimension** can be assigned to more than one **Cost accounting ledger**.

Here is an example of **Statistical dimension**.

| Name                        | Data connector for dimension members |
|-----------------------------|--------------------------------------|
| Shared Statistical elements | Imported dimension members           |

Here is an example of a **Statistical dimension** being assigned to a **Cost accounting ledger**.

| Name                  | Accounting currency | Exchange rate type | Fiscal calendar | Cost element dimension | Statistical dimension       |
|-----------------------|---------------------|--------------------|-----------------|------------------------|-----------------------------|
| Managerial accounting | USD                 | Constant currency  | Fiscal period   | Shared Cost elements   | Shared Statistical elements |

## Statistical dimension members

A **Statistical dimension member** represents an entity for which you want to register non-monetary measures to be used either as allocation base or purely for reporting non-monetary values.

Statistical dimension members can be created manually or imported from a file via **Data management import/export** tool.

A **Statistical dimension member** automatically becomes a predefined allocation base and can be used as allocation base in policies or as input in other types of allocation bases.

Here are a few examples of a few common **Statistical dimension members**.

**Statistical dimension members**

| Statistical dimension name  | Statistical elements | Unit                    |      |
|-----------------------------|----------------------|-------------------------|------|
| Shared Statistical elements | FTE                  | Full time employees     | Ea.  |
| Shared Statistical elements | Electricity          | Electricity consumption | kWh  |
| Shared Statistical elements | Pack CC              | Packaging Cost center   | Hrs. |

## Statistical measure provider template

**Statistical measures** can origin from many kinds of sources. Microsoft Dynamics 365 for Finance and Operations, Enterprise edition is a perfect source to extract **Statistical measures** and with the **Statistical measure provider template**, you can easily configure which statistical measures you want to extract.

A **Statistical measure provider template** definition is generic and can be reused in multiple **Statistical dimension members**.

> [!NOTE]
> All tables that contain financial dimensions can be used as sources for statistical measures.

**Example: Count of employees per cost center**

The count of employees per cost center is a statistical measure that can be used for various purposes to provide managerial insights.

-   A statistical reporting measure by cost center

-   Serve as allocation base for various types of expenses

-   Internal cost rates by cost center

    -   Cost by employee

    -   Revenue by employee

The table **HcmEmployment** holds a list of all employees in the instance. This table is a global table, which means that the records are not related to a specific data area ID.

For example, the table **HcmEmployment** has these employees.

| Name       | Cost center | Worker Type |            |
|------------|-------------|-------------|------------|
| Employee 1 | CC001       | HR          | Employee   |
| Employee 2 | CC002       | FI          | Employee   |
| Employee 3 | CC002       | FI          | Employee   |
| Employee 4 | CC003       | IT          | Employee   |
| Employee 5 | CC003       | IT          | Employee   |
| Employee 6 | CC002       | FI          | Contractor |

When creating a **Statistical measure provider template** record, you must decide on which function to use.

-   Count: A count of records per cost object is transferred.

-   Sum: A sum over records per cost object is transferred. (Sum field and Date
    field are required)

## Use the Count function 

For example, a **Statistical measure provider template** can be set up as follows.

| Name  | Function | Source table  | Sum field | Date field |
|-------|----------|---------------|-----------|------------|
| FTE’s | Count    | HcmEmployment | NA        | NA         |

You can also add a range(s) to narrow the measures from the source table.

In this example, if you only want a count of all full time employees (FTEs), you can add a range in the field **Worker type** and in the field **Criteria**, select **Employee** to limit the output range as follows.

**Ranges**

| Source table  | Field       | Criteria |
|---------------|-------------|----------|
| HcmEmployment | Worker type | Employee |

Before you can get **Statistical measures** into Cost accounting, you need to establish the relation between the **Statistical measure provider template** and **Statistical dimension member**. This relation is created per **Cost accounting ledger and version**. The relation consists of a **Data connector** and **Data provider**. You can have several **Data connectors** and **Data providers** per
**Statistical dimension member**.

> [!NOTE]
> In this example, we will only create a relation for the version **Actual**.

Go to **Cost accounting ledger** \< **Actual version** \< **Manage \< Statistical measures** to establish the relation. In this case, the data connector Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures is selected as we want to extract data from Finance and Operations.

**Data source**

| Name        | Data connector                                                                     | Statistical dimension member |
|-------------|------------------------------------------------------------------------------------|------------------------------|
| FTEs D365FO | Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures | FTEs                         |

**Data provider configuration**

| Statistical template name |
|---------------------------|
| FTEs                      |

After the **Statistical measure source data** processing is completed, the following statistical entries are created in Cost accounting.

**Journal**

| Journal | Journal type                       | Fiscal calendar period | Version | Data connector source entries |                |       |
|---------|------------------------------------|------------------------|---------|-------------------------------|----------------|-------|
| 00001   | Statistical entry transfer journal | Fiscal                 | 2017    | Period 1                      | CA ledger USMF | FTE’s |

**Statistical entry transfer journal entries**

| Accounting date | Magnitude | Statistical element | Cost center         |       |
|-----------------|-----------|---------------------|---------------------|-------|
| 31-01-2017      | 1,00      | FTE’s               | Full time employees | CC001 |
| 31-01-2017      | 2,00      | FTE’s               | Full time employees | CC002 |
| 31-01-2017      | 2,00      | FTE’s               | Full time employees | CC003 |

**Statistical entries**

| Cost object | Accounting date | Statistical dimension member | Magnitude |                     |      |
|-------------|-----------------|------------------------------|-----------|---------------------|------|
| CC001       | HR              | 31-01-2017                   | FTE’s     | Full time employees | 1,00 |
| CC002       | FI              | 31-01-2017                   | FTE’s     | Full time employees | 2,00 |
| CC003       | IT              | 31-01-2017                   | FTE’s     | Full time employees | 2,00 |

In case the **Predefined dimension member allocation basis FTEs** is assigned as an allocation base in a cost distribution rule, the cost will be distributed by following allocation factor.

| Cost object | Magnitude | Allocation factor |                 |
|-------------|-----------|-------------------|-----------------|
| CC001       | HR        | 1,00              | (1/5) \* Amount |
| CC002       | FI        | 2,00              | (2/5) \* Amount |
| CC003       | IT        | 2,00              | (2/5) \* Amount |

## Use the Sum function 

A production cost center CC010 Packaging is responsible for packaging the products before they are shipped to customers. The direct labor cost is added to the products via the **BOM** and **Route**. The indirect cost of running the cost center also needs to be allocated to the produced products. The best statistical measure for such an allocation would often be the registered production hours per product within the given period.

The table **ProdRouteTrans** holds all production labor transactions per legal entity DataAreadID.

Here is an example of how the table **ProdRouteTrans** can look like.

| Reference        | Number | Operation | Type | Time  | Physical date | Product group (Financial dimension) | Legal entity |
|------------------|--------|-----------|------|-------|---------------|-------------------------------------|--------------|
| Production order | P0001  | Packaging | Time | 8,00  | 01-01-2017    | Orange juice B2B                    | USMF         |
| Production order | P0001  | Packaging | Time | 8,00  | 02-01-2017    | Orange juice B2B                    | USMF         |
| Production order | P0002  | Packaging | Time | 4,00  | 03-01-2017    | Orange juice Consumer               | USMF         |
| Production order | P0003  | Packaging | Time | 4,00  | 03-01-2017    | Orange juice Consumer               | USMF         |
| Production order | P0004  | Reconst.  | Time | 10,00 | 03-01-2017    | Orange juice Consumer               | USMF         |

When creating a **Statistical measure provider template** record, you must decide which function to use.

-   Count: A count of records per cost object is transferred.

-   Sum: A sum over records per cost object is transferred. (Sum field and Date
    field are required)

The **Statistical measure provider template** can be set up as follows.

| Name    | Function | Source table   | Sum field | Date field    |
|---------|----------|----------------|-----------|---------------|
| Pack CC | Sum      | ProdRouteTrans | Hours     | Physical date |

You can also add ranges to narrow the measures from the source table.

In this example, if you only want the sum of hours related to the cost center CC010 Packaging, you can add a range in the field **Operation** and in the field **Criteria**, select **Packaging** to limit the output range.

**Ranges**

| Source table   | Field     | Criteria  |
|----------------|-----------|-----------|
| ProdRouteTrans | Operation | Packaging |

Before you can get **Statistical measures** into Cost accounting, you need to establish the relation between the **Statistical measure provider template** and **Statistical dimension member**. This relation is created per **Cost accounting ledger and version**. The relation consists of a **Data connector** and **Data provider**. You can have several **Data connectors** and **Data providers** per
**Statistical dimension member**.

> [!NOTE]
> In this example, we will only create a relation for the version **Actual.**

Go to **Cost accounting ledger** \< **Actual version** \< **Manage \< Statistical measures** to establish the relation. In this case, the data connector Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures is selected as we want to extract data from Finance and Operations.

**Data source**

| Name           | Data connector                                                                     | Statistical dimension member |
|----------------|------------------------------------------------------------------------------------|------------------------------|
| Pack CC D365FO | Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures | Pack CC                      |

The system recognize that **ProdRouteTrans** is a table where each record belongs to a separate legal entity and therefore you will be asked to select for which legal entity you want to import transactions from.

Data provider configuration

| Statistical template name | Legal entity |
|---------------------------|--------------|
| Pack CC                   | USMF         |

After the **Statistical measure source data processing** is completed, these statistical entries are created in Cost accounting.

**Journal**

| Journal | Journal type                       | Fiscal calendar period | Version | Data connector source entries |                |         |
|---------|------------------------------------|------------------------|---------|-------------------------------|----------------|---------|
| 00002   | Statistical entry transfer journal | Fiscal                 | 2017    | Period 1                      | CA ledger USMF | Pack CC |

**Statistical entry transfer journal entries**

| Accounting date | Magnitude | Statistical element | Product group         |                       |
|-----------------|-----------|---------------------|-----------------------|-----------------------|
| 31-01-2017      | 16,00     | Pack CC             | Packaging Cost center | Orange juice B2B      |
| 31-01-2017      | 8,00      | Pack CC             | Packaging Cost center | Orange juice Consumer |

**Statistical entries**

| Cost object           | Accounting date | Statistical dimension member | Magnitude             |       |
|-----------------------|-----------------|------------------------------|-----------------------|-------|
| Orange juice B2B      | 31-01-2017      | Pack CC                      | Packaging Cost center | 16,00 |
| Orange juice Consumer | 31-01-2017      | Pack CC                      | Packaging Cost center | 8,00  |

In case the **Predefined dimension member allocation basis Pack CC** is assigned as an allocation base in a cost distribution rule, the cost will be distributed by using the following allocation factor.

| Cost object           | Magnitude | Allocation factor |
|-----------------------|-----------|-------------------|
| Orange juice B2B      | 16,00     | (16/24) \* Amount |
| Orange juice Consumer | 8,00      | (8/24) \* Amount  |

## Imported statistical measures 

**Statistical measures** can be imported into Cost accounting using the **Data management import/export tool.**

The data entity used for the import is called **Imported statistical measures**.

> [!NOTE]
> The data entity is designed to allow a maximum of up to 5 unique dimension values for each entry.

In Microsoft Excel, the consumption of electricity is recorded as follows using the predefined format of the data entity.

| Accounting date | Dimension member name1 | Dimension member name2 | Dimension member name5 | Magnitude | Source identifier |
|-----------------|------------------------|------------------------|------------------------|-----------|-------------------|
| 31-01-2017      | CC001                  |                        |                        | 2450,00   | Electricity       |
| 31-01-2017      | CC002                  |                        |                        | 4100,00   | Electricity       |
| 31-01-2017      | CC003                  |                        |                        | 15000,00  | Electricity       |

When you have imported your data via the **Data management,** the data will be stored in a Cost accounting staging table. This means that the imported data can be used in multiple cost accounting ledgers without requiring a reload of data.

To do the import, go to **Imported data** \< **Data entity** \< **Imported
statistical measures.**

| Source identifier | Accounting date | Magnitude | Dimension member name1 | Dimension member name2 | Dimension member name5 |
|-------------------|-----------------|-----------|------------------------|------------------------|------------------------|
| Electricity       | 31-01-2017      | 2450,00   | CC001                  |                        |                        |
| Electricity       | 31-01-2017      | 4100,00   | CC002                  |                        |                        |
| Electricity       | 31-01-2017      | 15000,00  | CC003                  |                        |                        |

Before you can get **Statistical measures** into Cost accounting, you need to establish the relation between the **Source identifier** and **Statistical dimension member**. This relation is created per **Cost accounting ledger and version.** The relation consists of a **Data connector** and **Data provider**. You can have several **Data connectors** and **Data providers** per **Statistical dimension member**.

> [!NOTE]
> In this example, we will only create a relation for the version **Actual.**

Go to **Cost accounting ledger** \< **Actual version** \< **Manage \< Statistical measures** to establish the relation. In this case, the data connector **Imported statistical measures** is selected as data has been imported into Cost accounting via Excel from a third-party system.

Data source

| Name        | Data connector                | Statistical dimension member |
|-------------|-------------------------------|------------------------------|
| Electricity | Imported statistical measures | Electricity                  |

Data provider configuration

| Import source identifier | Function | Dimension1   | Dimension2 | Dimension5 |
|--------------------------|----------|--------------|------------|------------|
| Electricity              | Sum      | Cost centers |            |            |

> [!NOTE]
> When defining the Data provider configuration, you need to specify which cost object dimensions to match against the imported transactions. After the **Statistical measure source data processing** is completed, these statistical entries are created in Cost accounting.

Journal

| Journal | Journal type                       | Fiscal calendar period | Version | Data connector source entries |                |             |
|---------|------------------------------------|------------------------|---------|-------------------------------|----------------|-------------|
| 00002   | Statistical entry transfer journal | Fiscal                 | 2017    | Period 1                      | CA ledger USMF | Electricity |

Statistical entry transfer journal entries

| Accounting date | Magnitude | Cost element | Cost center             |       |
|-----------------|-----------|--------------|-------------------------|-------|
| 31-01-2017      | 2450,00   | Electricity  | Electricity consumption | CC001 |
| 31-01-2017      | 4100,00   | Electricity  | Electricity consumption | CC002 |
| 31-01-2017      | 15000,00  | Electricity  | Electricity consumption | CC003 |

Statistical entries

| Cost object | Accounting date | Statistical dimension member | Magnitude   |                         |          |
|-------------|-----------------|------------------------------|-------------|-------------------------|----------|
| CC001       | HR              | 31-01-2017                   | Electricity | Electricity consumption | 2450,00  |
| CC002       | FI              | 31-01-2017                   | Electricity | Electricity consumption | 4100,00  |
| CC003       | IT              | 31-01-2017                   | Electricity | Electricity consumption | 15000,00 |

In case the **Predefined dimension member allocation basis Electricity** is assigned as an allocation base in a Cost distribution rule, the cost will be distributed by using the following allocation factor.

| Cost object | Magnitude | Allocation factor |                         |
|-------------|-----------|-------------------|-------------------------|
| CC001       | HR        | 2450,00           | (2450/21550) \* Amount  |
| CC002       | FI        | 4100,00           | (4100/21550) \* Amount  |
| CC003       | IT        | 15000,00          | (15000/21550) \* Amount |

## See also

[Allocation bases](allocation-bases.md)
