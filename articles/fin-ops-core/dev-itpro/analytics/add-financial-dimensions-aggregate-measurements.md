---
title: Add financial dimensions to aggregate measurements
description: Learn how a power user can include financial dimensions in ready-made Power BI reports, including learning how the feature works.
author: MilindaV2
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/14/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 8 for finance and operations
ms.assetid: c04e0a7b-1747-4b88-b729-fd820f8ab600
---

# Add financial dimensions to aggregate measurements

[!include [banner](../includes/banner.md)]

This feature lets power users include financial dimensions in ready-made Microsoft Power BI reports. Power users can also create new Power BI reports that use financial dimensions.

Financial dimensions are user-defined configuration data that enables the ledger chart of accounts to retain extra information. By adding financial dimensions, you can configure extra data fields that appear with the chart of accounts and financial reports. You can slice and dice the ledger chart of accounts based on those fields. This feature provides powerful financial reporting. For example, you can explore ledger data by using the new financial dimensions that you add. Because the ready-made Power BI reports don't include financial dimensions when they're released, you must add these extra fields to the ready-made reports. 

After you add financial dimension fields to the report, you can share the report with other users. Those other users can modify existing visuals, such as charts, by including all or some of the financial dimension fields.

> [!NOTE]
> This feature is available in Microsoft Dynamics 365 Finance, Enterprise edition (July 2017). Platform update 8 or later is also required. 

## How does this feature work?

The Entity store is an operational data warehouse that power users can use to create reports. Whenever the Entity store updates, it includes all available financial dimensions. Here's an example from the **Ledger Activity** aggregate measurement that contains General ledger journal-level details.

The following list shows some of the tables that the Entity store fills when it updates. Tables that changed are bold.

- LedgerActivityMeasure\_LedgerActivityMeasureGroup
- LedgerActivityMeasure\_TransactionDate
- LedgerActivityMeasure\_Currency
- LedgerActivityMeasure\_FiscalPeriodDateAggregtateDimension
- LedgerActivityMeasure\_LedgerFactDimension
- LedgerActivityMeasure\_FiscalYearOffsetDimension
- LedgerActivityMeasure\_MainAccount
- **LedgerActivityMeasure\_DimensionCombination**
- LedgerActivityMeasure\_Ledger
- LedgerActivityMeasure\_MainAccountCategory
- LedgerActivityMeasure\_Company
- LedgerActivityMeasure\_MainAccountLegalEntity
- **LedgerActivityMeasure\_Agreement**
- **LedgerActivityMeasure\_BankAccount**
- **LedgerActivityMeasure\_BusinessUnit**
- **LedgerActivityMeasure\_Campaign**
- **LedgerActivityMeasure\_Cargo**
- **LedgerActivityMeasure\_Cargo\_CN**

For each financial dimension that you define in your system, you might see a corresponding table in the Entity store.

If you examine the LedgerActivityMeasure\_DimensionCombination table, you see that the list of fields has been expanded and now includes additional fields. Each new field corresponds to a financial dimension. For example, here are some of the additional fields:

- Agreement\_FK
- Agreement\_Description
- Agreement\_Value
- BankAccount\_FK
- BankAccount\_Description
- BankAccount\_Value
- BusinessUnit\_FK
- BusinessUnit\_Description
- BusinessUnit\_Value

If a user defines a new financial dimension named **vendor**, the Entity store adds a new table named LedgerActivityMeasure\_Vendor when it updates.

The LedgerActivityMeasure\_DimensionCombination table also contains the following new set of fields:

- Vendor\_FK
- Vendor\_Description
- Vendor\_Value

## How a Power BI report author can create reports that use financial dimensions

A business user can create a new report that uses financial dimensions by using Power BI desktop. Existing reports that use financial dimensions can be updated so that they include extra fields.

In this example, use Power BI desktop to create a report that uses the Ledger Activity measure group. 

1. In a development environment, connect to the Entity store database by using Power BI desktop. 
1. Select the following tables:

    - LedgerActivityMeasure\_LedgerActivityMeasureGroup
    - LedgerActivityMeasure\_FiscalPeriodDateAggregtateDimension
    - LedgerActivityMeasure\_DimensionCombination

1. Use the **Manage relationships** option in Power BI desktop to define the following relationships between table fields:

    - Define a join between **LedgerActivityMeasure\_LedgerActivityMeasureGroup.LEDGERDIMENSION** and **LedgerActivityMeasure\_DimensionCombination.DIMENTIONCOMBINATIONRECID**.
    - Define a join between **LedgerActivityMeasure\_LedgerActivityMeasureGroup.LEDGERGREGORIANDATEID** and **LedgerActivityMeasure\_FiscalPeriodDateAggregateDimension.LEDGERPERIODGREGORIANDATEID**.

1. Create a matrix report that uses the **Sales** and **YearName** fields. The report should resemble the following example.

    :::image type="content" source="media/d1d0e190896bec3a755b9b586a3cb657.png" alt-text="Screenshot of a matrix report that uses the Sales and YearName fields.":::

    Next, add financial dimension values.

1. In the list of fields in Power BI desktop, expand the **LedgerActivityMeasure\_DimensionCombination** table. You see that the list of dimension fields is expanded into table fields, as shown here.

    :::image type="content" source="media/b5099b0c03fa16f0c2ab70943c7cce8b.png" alt-text="Screenshot of list of dimension fields expanded into table fields.":::

1. Include the **BusinessUnit\_Description** field in the report. Your report now shows sales by business unit, as shown in the following example.

    :::image type="content" source="media/c39e94631896301db6675d36fc9d3886.png" alt-text="Screenshot of report that shows sales by business unit.":::

    Notice that you have the **BusinessUnit\_description** field and the **BusinessUnit\_Value** field. The value field lets you get a numerical value that you can use to sort columns.

1. Define a new financial dimension, and update the Entity store. 
1. When the update finishes, right-click the **LedgerActivityMeasure\_DimensionCombination** table, and then select **Refresh data**. Notice that the new financial dimension that you defined is reflected in the list of fields that are available for reporting.

    :::image type="content" source="media/6d345e2f68dfb0413daebfd5f469db2c.png" alt-text="Screenshot of refresh data dialog.":::

1. You can include the new financial dimension fields in the report.

### Creating reports that use expanded financial dimension tables

As discussed earlier, new tables are created in the Entity store. Each financial dimension field is added to a new table. The new tables contain individual fields for the name, value, and description.

The new tables contain a key that you can use to join them with the **LedgerActivityMeasure\_DimensionCombination** table that you use to create the report. If you want to use fields from these additional tables, include them in the report and relate them by using the keys.

1. Open the report that you created earlier.

    Now, add a financial dimension table to the report.

1. In Power BI Desktop, select **Recent Sources** on the menu, and then select the **AXDW** data connection. The table navigator is shown.
1. Select the **LedgerActivityMeasure\_LegalEntity** table for the report.

    > [!NOTE]
    > If you're using a development or demo environment, you see this table because **LegalEntity** is a financial dimension that's defined in demo data. If you're working with your own data, the tables that you see correspond to financial dimensions that you define.

    Now, relate the selected table to existing tables in the report. 

1. In the report, open the **Manage relationships** dialog box.
1. Join **LedgerActivityMeasure\_DimensionCombination.LegalEntity\_FK** to **LedgerActivityMeasure\_LegalEntity.KEY\_**.

If you select a different dimension table in step 3, you must relate the corresponding **FieldName\_FK** field from the combination table to the **KEY\_** field in the dimension table.

## How a developer can enable financial dimensions

Before users can see expanded financial dimensions in the Entity store, a developer must enable the use of financial dimensions in aggregate measurements. As a best practice, include financial dimensions when you model any aggregate measurement that involves financial data. To include financial dimensions, create an aggregate dimension that is based on "financial dimension tables." As shown earlier, an aggregate dimension that you create by using financial dimension tables expands at runtime.

### What are financial dimension tables?

Financial dimension tables are base tables that contain financial dimension data. Examples include **DimensionAttributeValueCombination** and **DimensionAttributeValueSet**.

If you use a table, a view, or an entity that's based on those two tables, you see the fields of the aggregate dimension expanded at runtime.

Consider the following example from the LedgerActivityMeasure aggregate measurement.

![DimensionCombination aggregate dimension in the LedgerActivityMeasure aggregate measurement.](media/08437296a512478e99b3c377170edeee.png)

DimensionCombination is an aggregate dimension that the DimensionAttributeValueCombination base table models. In this case, the developer references the aggregate dimension by using the LedgerActivityMeasureGroup measure group.

At runtime, new dimension fields are added (that is, the DimensionCombination table is expanded) as you define new financial dimensions in the system.

### Creating role-playing financial dimensions

When you report by using ledger data, you might need to report on primary accounts and offset accounts. For example, if a ledger transaction involves the transfer of an amount from one account to another account, the primary account is the "from" account, whereas the offset account is the "to" account. This pattern is known as the *role-playing dimensions* pattern.

You must associate both primary accounts and offset accounts with transaction data. Therefore, you must expand financial dimension fields of both primary accounts and offset accounts. The following example shows how you can meet this requirement.

![Example of role-playing dimensions.](media/062a0d860fe1633a6616bca6e871f95e.png)

You model two dimension references for `LedgerActivityMeaureGroup`. The first reference, `DimensionCombination`, is joined by using the **LedgerDimension** field. You saw this pattern earlier in this article.

The second reference, `OffsetDimensionCombination`, is another reference to the same dimension. You reuse the `DimensionCombination` aggregate dimension and give it a new name. In the second case, you can join by using the **OffsetLedgerDimension** field.

At runtime, the system expands both these dimensions with extra fields. Therefore, you can report on primary and offset dimension fields.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
