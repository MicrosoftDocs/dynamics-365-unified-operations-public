---
# required metadata

title: Statistical dimension members and statistical measure provider templates
description: This topic provides information about statistical dimension members and statistical measure provider templates. Statistical dimension members can be used as an allocation base in policies such as cost distribution and cost allocation. They can also be used to report non-monetary cost consumption.
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

# Statistical dimension members and statistical measure provider templates

[!include[banner](../includes/banner.md)]

A statistical dimension and its members are used to register and control non-monetary entries in Cost accounting. Statistical dimension members can be used for two purposes:

- As an allocation base in policies such as cost distribution or cost allocation
- For reporting of non-monetary consumption

## Statistical dimension

A statistical dimension has a unique name and a set of unique dimension members. The statistical dimension is assigned to a Cost accounting ledger ID. This relationship ties all corresponding statistical dimension members to the Cost accounting ledger. Therefore, all statistical entries will be created in the context of the Cost accounting ledger.

> [!NOTE]
> A statistical dimension can be assigned to more than one Cost accounting ledger.

Here is an example of a statistical dimension.

| Name                        | Data connector for dimension members |
|-----------------------------|--------------------------------------|
| Shared Statistical elements | Imported dimension members           |

Here is an example of a statistical dimension that has been assigned to a Cost accounting ledger.

| Name                  | Accounting currency | Exchange rate type | Fiscal calendar | Cost element dimension | Statistical dimension       |
|-----------------------|---------------------|--------------------|-----------------|------------------------|-----------------------------|
| Managerial accounting | USD                 | Constant currency  | Fiscal period   | Shared Cost elements   | Shared Statistical elements |

## Statistical dimension members

A statistical dimension member represents an entity that you want to register non-monetary measures for. These measures can be used either as an allocation base or just to report non-monetary values.

Statistical dimension members can be created manually. Alternatively, they can be imported from a file by using the Data management import/export tool.

A statistical dimension member automatically becomes a predefined allocation base. It can be used as an allocation base in policies or as input in other types of allocation bases.

Here are some examples of typical statistical dimension members.

| Statistical dimension name  | Statistical elements | Description             | Unit |
|-----------------------------|----------------------|-------------------------|------|
| Shared Statistical elements | FTE                  | Full time employees     | Ea.  |
| Shared Statistical elements | Electricity          | Electricity consumption | kWh  |
| Shared Statistical elements | Pack CC              | Packaging Cost center   | Hrs. |

## Statistical measure provider template

Statistical measures can originate from many kinds of sources. Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, is a great source to extract statistical measures from. You can use a statistical measure provider template to easily configure the statistical measures that you want to extract.

The definition of a statistical measure provider template is generic and can be reused in multiple statistical dimension members.

> [!NOTE]
> All tables that contain financial dimensions can be used as sources for statistical measures.

**Example: Count of employees per cost center**

The count of employees per cost center is a statistical measure that can be used for various purposes that provide managerial insight:

- A statistical reporting measure by cost center
- An allocation base for various types of expenses
- Internal cost rates by cost center:

    - Cost by employee
    - Revenue by employee

The HcmEmployment table holds a list of all employees in the instance. This table is a global table. Therefore, the records aren't related to a specific data area ID.

Here is an example of employees in the HcmEmployment table.

| Name       | Cost center | Description   | Worker type |
|------------|-------------|----|-------------|
| Employee 1 | CC001       | HR | Employee    |
| Employee 2 | CC002       | FI | Employee    |
| Employee 3 | CC002       | FI | Employee    |
| Employee 4 | CC003       | IT | Employee    |
| Employee 5 | CC003       | IT | Employee    |
| Employee 6 | CC002       | FI | Contractor  |

When you create a **Statistical measure provider template** record, you must decide which function to use:

- **Count** – A count of records per cost object is transferred.
- **Sum** – A sum for records per cost object is transferred. (The **Sum** field and **Date** field are required.)

## Using the Count function

For example, a statistical measure provider template can be set up as follows.

| Name  | Function | Source table  | Sum field      | Date field     |
|-------|----------|---------------|----------------|----------------|
| FTEs  | Count    | HcmEmployment | Not applicable | Not applicable |

You can also add one or more ranges to narrow the measures from the source table.

In this example, if you just want a count of all full-time employees (FTEs), you can add a range in the **Worker type** field. In the **Criteria** field, select **Employee** to limit the output range as follows.

**Ranges**

| Source table  | Field       | Criteria |
|---------------|-------------|----------|
| HcmEmployment | Worker type | Employee |

Before you can get statistical measures into Cost accounting, you must establish the relation between the statistical measure provider template and the statistical dimension member. This relation is created per Cost accounting ledger and version. The relation consists of a data connector and a data provider. You can have several data connectors and data providers per statistical dimension member.

> [!NOTE]
> In this example, we will create a relation only for the **Actual** version.

Go to **Cost accounting ledger** \> **Actual version** \> **Manage** \> **Statistical measures** to establish the relation. For this scenario, select the **Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures** data connector, because we want to extract data from Finance and Operations.

**Data source**

| Name        | Data connector                                                                     | Statistical dimension member |
|-------------|------------------------------------------------------------------------------------|------------------------------|
| FTEs D365FO | Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures | FTEs                         |

**Data provider configuration**

| Statistical template name |
|---------------------------|
| FTEs                      |

After the source data for the statistical measure is processed, the following statistical entries are created in Cost accounting.

**Journal**

| Journal | Journal type                       | Fiscal calendar period | Year   |  Period  |  Version | Data connector source entries|
|---------|------------------------------------|------------------------|--------|----------|----------|------------------------------|
| 00001   | Statistical entry transfer journal | Fiscal                 | 2017   | Period 1 | CA ledger USMF | FTEs                   |

**Statistical entry transfer journal entries**

| Accounting date | Magnitude | Statistical element |   Description       | Cost center |
|-----------------|-----------|---------------------|---------------------|-------------|
| 31-01-2017      | 1.00      | FTEs                | Full time employees | CC001       |
| 31-01-2017      | 2.00      | FTEs                | Full time employees | CC002       |
| 31-01-2017      | 2.00      | FTEs                | Full time employees | CC003       |

**Statistical entries**

| Cost object |    | Accounting date | Statistical dimension member |  Description        | Magnitude |
|-------------|----|-----------------|------------------------------|---------------------|-----------|
| CC001       | HR | 31-01-2017      | FTEs                         | Full time employees | 1.00      |
| CC002       | FI | 31-01-2017      | FTEs                         | Full time employees | 2.00      |
| CC003       | IT | 31-01-2017      | FTEs                         | Full time employees | 2.00      |

If the FTEs predefined dimension member allocation basis is assigned as an allocation base in a cost distribution rule, the cost will be distributed by using the following allocation factor.

| Cost object | Description    | Magnitude | Allocation factor |
|-------------|----|-----------|-------------------|
| CC001       | HR | 1.00      | (1/5) × Amount    |
| CC002       | FI | 2.00      | (2/5) × Amount    |
| CC003       | IT | 2.00      | (2/5) × Amount    |

## Using the Sum function

A production cost center, CC010 (Packaging), is responsible for packaging the products before they are shipped to customers. The direct labor cost is added to the products via the bill of materials (BOM) and route. The indirect cost of running the cost center must also be allocated to the produced products. Often, the best statistical measure for such an allocation is the number of registered production hours per product within the given period.

The ProdRouteTrans table holds all production labor transactions per legal entity DataAreadID.

Here is an example of the ProdRouteTrans table.

| Reference        | Number | Operation | Type | Time  | Physical date | Product group (Financial dimension) | Legal entity |
|------------------|--------|-----------|------|-------|---------------|-------------------------------------|--------------|
| Production order | P0001  | Packaging | Time | 8.00  | 01-01-2017    | Orange juice B2B                    | USMF         |
| Production order | P0001  | Packaging | Time | 8.00  | 02-01-2017    | Orange juice B2B                    | USMF         |
| Production order | P0002  | Packaging | Time | 4.00  | 03-01-2017    | Orange juice Consumer               | USMF         |
| Production order | P0003  | Packaging | Time | 4.00  | 03-01-2017    | Orange juice Consumer               | USMF         |
| Production order | P0004  | Reconst.  | Time | 10.00 | 03-01-2017    | Orange juice Consumer               | USMF         |

When you create a **Statistical measure provider template** record, you must decide which function to use:

- **Count** – A count of records per cost object is transferred.
- **Sum** – A sum for records per cost object is transferred. (The **Sum** field and **Date** field are required.)

The statistical measure provider template can be set up as follows.

| Name    | Function | Source table   | Sum field | Date field    |
|---------|----------|----------------|-----------|---------------|
| Pack CC | Sum      | ProdRouteTrans | Hours     | Physical date |

You can also add ranges to narrow the measures from the source table.

In this example, if you just want the sum of hours that are related to the CC010 Packaging cost center, you can add a range in the **Operation** field. In the **Criteria** field, select **Packaging** to limit the output range.

**Ranges**

| Source table   | Field     | Criteria  |
|----------------|-----------|-----------|
| ProdRouteTrans | Operation | Packaging |

Before you can get statistical measures into Cost accounting, you must establish the relation between the statistical measure provider template and the statistical dimension member. This relation is created per Cost accounting ledger and version. The relation consists of a data connector and a data provider. You can have several data connectors and data providers per statistical dimension member.

> [!NOTE]
> In this example, we will create a relation only for the **Actual** version.

Go to **Cost accounting ledger** \> **Actual version** \> **Manage** \> **Statistical measures** to establish the relation. For this scenario, select the **Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures** data connector, because we want to extract data from Finance and Operations.

**Data source**

| Name           | Data connector                                                                     | Statistical dimension member |
|----------------|------------------------------------------------------------------------------------|------------------------------|
| Pack CC D365FO | Dynamics 365 for Finance and Operations, Enterprise edition – Statistical measures | Pack CC                      |

The system recognizes that ProdRouteTrans is a table where each record belongs to a separate legal entity. Therefore, you will be asked to select the legal entity that transactions should be imported from.

**Data provider configuration**

| Statistical template name | Legal entity |
|---------------------------|--------------|
| Pack CC                   | USMF         |

After the source data for the statistical measure processed, the following statistical entries are created in Cost accounting.

**Journal**

| Journal | Journal type                     | Fiscal calendar period | Year   | Period | Version   |   Data connector source entries  |
|---------|----------------------------------|------------------------|--------|---------|----------------|---------|
| 00002   | Statistical entry transfer journal | Fiscal               | 2017    | Period 1  | CA ledger USMF | Pack CC |

**Statistical entry transfer journal entries**

| Accounting date | Magnitude | Statistical element |  Description          | Product group         |
|-----------------|-----------|---------------------|-----------------------|-----------------------|
| 31-01-2017      | 16.00     | Pack CC             | Packaging Cost center | Orange juice B2B      |
| 31-01-2017      | 8.00      | Pack CC             | Packaging Cost center | Orange juice Consumer |

**Statistical entries**

| Cost object           | Accounting date | Statistical dimension member |    Description        | Magnitude |
|-----------------------|-----------------|------------------------------|-----------------------|-----------|
| Orange juice B2B      | 31-01-2017      | Pack CC                      | Packaging Cost center | 16.00     |
| Orange juice Consumer | 31-01-2017      | Pack CC                      | Packaging Cost center | 8.00      |

If the Pack CC predefined dimension member allocation basis is assigned as an allocation base in a cost distribution rule, the cost will be distributed by using the following allocation factor.

| Cost object           | Magnitude | Allocation factor  |
|-----------------------|-----------|--------------------|
| Orange juice B2B      | 16.00     | (16 ÷ 24) × Amount |
| Orange juice Consumer | 8.00      | (8 ÷ 24) × Amount  |

## Imported statistical measures

You can import statistical measures into Cost accounting by using the Data management import/export tool.

The data entity that is used for the import is named Imported statistical measures.

> [!NOTE]
> This data entity is designed to allow a maximum of five unique dimension values per entry.

The consumption of electricity is recorded in Microsoft Excel by using the predefined format of the data entity. Here is an example.

| Accounting date | Dimension member name1 | Dimension member name2 | Dimension member name5 | Magnitude  | Source identifier |
|-----------------|------------------------|------------------------|------------------------|------------|-------------------|
| 31-01-2017      | CC001                  |                        |                        | 2,450.00   | Electricity       |
| 31-01-2017      | CC002                  |                        |                        | 4,100.00   | Electricity       |
| 31-01-2017      | CC003                  |                        |                        | 15,000.00  | Electricity       |

When you've imported your data via Data management, the data will be stored in a Cost accounting staging table. Therefore, the imported data can be used in multiple Cost accounting ledgers. A reload of data isn't required.

To import the data, go to **Imported data** \> **Data entity** \> **Imported statistical measures**.

| Source identifier | Accounting date | Magnitude  | Dimension member name1 | Dimension member name2 | Dimension member name5 |
|-------------------|-----------------|------------|------------------------|------------------------|------------------------|
| Electricity       | 31-01-2017      | 2,450.00   | CC001                  |                        |                        |
| Electricity       | 31-01-2017      | 4,100.00   | CC002                  |                        |                        |
| Electricity       | 31-01-2017      | 15,000.00  | CC003                  |                        |                        |

Before you can get statistical measures into Cost accounting, you must establish the relation between the source identifier and the statistical dimension member. This relation is created per Cost accounting ledger and version. The relation consists of a data connector and a data provider. You can have several data connectors and data providers per statistical dimension member.

> [!NOTE]
> In this example, we will create a relation only for the **Actual** version.

Go to **Cost accounting ledger** \> **Actual version** \> **Manage** \> **Statistical measures** to establish the relation. For this scenario, select the **Imported statistical measures** data connector, because data has been imported from a third-party system into Cost accounting via Excel.

**Data source**

| Name        | Data connector                | Statistical dimension member |
|-------------|-------------------------------|------------------------------|
| Electricity | Imported statistical measures | Electricity                  |

**Data provider configuration**

| Import source identifier | Function | Dimension1   | Dimension2 | Dimension5 |
|--------------------------|----------|--------------|------------|------------|
| Electricity              | Sum      | Cost centers |            |            |

> [!NOTE]
> When you define the data provider configuration, you must specify which cost object dimensions to match against the imported transactions. After the source data for the statistical measure is processed, the following statistical entries are created in Cost accounting.

**Journal**

| Journal | Journal type                       | Fiscal calendar period | Year  | Perid  |Version      |Data connector source entries |
|---------|------------------------------------|------------------------|-------|----- --|---------------|-------------|
| 00002   | Statistical entry transfer journal | Fiscal                 | 2017  | Period 1 | CA ledger USMF | Electricity |

**Statistical entry transfer journal entries**

| Accounting date | Magnitude  | Cost element |   Description           | Cost center |
|-----------------|------------|--------------|-------------------------|-------------|
| 31-01-2017      | 2,450.00   | Electricity  | Electricity consumption | CC001       |
| 31-01-2017      | 4,100.00   | Electricity  | Electricity consumption | CC002       |
| 31-01-2017      | 15,000.00  | Electricity  | Electricity consumption | CC003       |

**Statistical entries**

| Cost object |    | Accounting date | Statistical dimension member |      Description                   | Magnitude  |
|-------------|----|-----------------|------------------------------|-------------------------|------------|
| CC001       | HR | 31-01-2017      | Electricity                  | Electricity consumption | 2,450.00   |
| CC002       | FI | 31-01-2017      | Electricity                  | Electricity consumption | 4,100.00   |
| CC003       | IT | 31-01-2017      | Electricity                  | Electricity consumption | 15,000.00  |

If the Electricity predefined dimension member allocation basis is assigned as an allocation base in a cost distribution rule, the cost will be distributed by using the following allocation factor.

| Cost object |    | Magnitude | Allocation factor          |
|-------------|----|-----------|----------------------------|
| CC001       | HR | 2,450.00  | (2,450 ÷ 21,550) × Amount  |
| CC002       | FI | 4,100.00  | (4,100 ÷ 21,550) × Amount  |
| CC003       | IT | 15,000.00 | (15,000 ÷ 21,550) × Amount |

## See also

[Allocation bases](allocation-bases.md)
