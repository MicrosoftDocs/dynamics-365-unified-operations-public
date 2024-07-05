---
title: Add lookup values for financial dimensions to Excel templates
description: Learn about how you can add the ability to look up dimension values in Microsoft Excel templates, including a table outlining dimensions and related entities.
author: RyanCCarlson2
ms.author: rcarlson
ms.topic: article
ms.date: 06/24/2024
ms.reviewer: johnmichalak
audience: Developer
ms.assetid: f3ab87ab-ee8b-462c-bb6f-4d98e0030513
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: 
ms.dyn365.ops.version: Version 1611
---

# Add lookup values for financial dimensions to Excel templates

[!include [banner](../includes/banner.md)]

This article provides information about how you can add the ability to look up dimension values in Microsoft Excel templates.

The only value that is present on Microsoft Excel templates after installation is MainAccount. This is the only dimension that all customers will have. To add the dimensions to Microsoft Excel templates, you need to complete the steps in the [Add dimensions to Excel templates](dimensions-overview.md) article. After you have added the dimensions, if you want the ability to look up a list of dimension values, complete the steps in this article. 

> [!NOTE]
> This information is subject to change for each release, so be sure to check back frequently for the most up-to-date information.

1.  In Visual Studio, open the project where you modified **DimensionCombinationEntity** or **DimensionSetEntity.**
2.  Right-click **DimensionCombinationEntity** or **DimensionSetEntity**. Select **Open**.
3.  Right click **Relations**. Select **New** and then click **Relation.**
4.  In the **Properties** pane, set the following properties.
    -   **Validate** - No
    -   **Cardinality** - ZeroMore
    -   **Name** - Enter the name of the financial dimension, such as Department.
    -   **Related Data Entity** - Select the entity for the financial dimension that you entered in the **Name** field. The following table contains a list of the financial dimensions and the related entities.

        | Financial dimension 'Use values from'     | Related entity                            |
        |-------------------------------------------|-------------------------------------------|
        | &lt; Custom dimension &gt;                | DimAttributeFinancialTagEntity            |
        | Agreements                                | DimAttributeAgreementHeaderExt\_RUEntity  |
        | Bank accounts                             | DimAttributeBankAccountTableEntity        |
        | BusinessUnits                             | DimAttributeOMBusinessUnitEntity          |
        | Campaigns                                 | DimAttributeSmmCampaignTableEntity        |
        | Cash accounts                             | DimAttributeRCashTable\_RUEntity          |
        | Cost centers                              | DimAttributeOMCostCenterEntity            |
        | Customer groups                           | DimAttributeCustGroupEntity               |
        | Customers                                 | DimAttributeCustTableEntity               |
        | Deferrals                                 | DimAttributeRDeferralsTable\_RUEntity     |
        | Departments                               | DimAttributeOMDepartmentEntity            |
        | Expense and income codes                  | DimAttributeRTax25ProfitTable\_RUEntity   |
        | Expense Purposes                          | DimAttributeTrvTravelTxtEntity            |
        | Fiscal establishments                     | DimAttributeFiscalEstablishment\_BREntity |
        | Fixed asset groups                        | DimAttributeAssetGroupEntity              |
        | Fixed assets                              | DimAttributeAssetTableEntity              |
        | Fixed assets (Russia)                     | DimAttributeRAssetTable\_RUEntity         |
        | Funds                                     | DimAttributeLedgerFund\_PSN               |
        | Item groups                               | DimAttributeInventItemGroupEntity         |
        | Items                                     | DimAttributeInventTableEntity             |
        | Jobs                                      | DimAttributeHcmJobEntity                  |
        | Legal entities                            | DimAttributeCompanyInfoEntity             |
        | POS registers                             | DimAttributeRetailTerminalEntity          |
        | Positions                                 | DimAttributeHcmPositionEntity             |
        | Project contracts                         | DimAttributeProjInvoiceTableEntity        |
        | Project groups                            | DimAttributeProjGroupEntity               |
        | Projects                                  | DimAttributeProjTableEntity               |
        | Prospects                                 | DimAttributeSmmBusRelTableEntity          |
        | Resource groups                           | DimAttributeWrkCtrResourceGroupEntity     |
        | Resources                                 | DimAttributeWrkCtrTableEntity             |
        | Stores                                    | DimAttributeRetailStoreEntity             |
        | Value streams                             | DimAttributeOMValueStreamEntity           |
        | Vendor groups                             | DimAttributeVendGroupEntity               |
        | Vendors                                   | DimAttributeVendTableEntity               |
        | Workers                                   | DimAttributeHcmWorkerEntity               |

    -   **Related Data Entity Cardinality** - **ZeroOne**
    -   **Related Data Entity Role** - Enter a unique name, such as "Dimension Department Lookup".
    -   **Relationship Type** - **Association**
    -   **Role** - Enter a unique name, such as Dimension Department.

5.  Right-click the **Financial dimension** name under **Relations.**
6.  Select **New**, and then click **Normal.**
7.  In the Properties pane, choose the name of the Financial dimension in the **Field**.
8.  In the Related field, type **Value**. The new relation is similar to the following example.
    
    ```xpp
    DimensionCombinationEntity.DimensionIntegration.Department==DimAttributeOMDepartmentEntity.Value
    ```

    ![Relation properties in Visual Studio.](./media/lookupwiki.png)

9.  Build the project and then synchronize it with the database.


## Additional resources

[Add lookup values for financial dimensions to Excel templates](add-dimensions-excel-templates.md)

[Extensibility home page](../extensibility/extensibility-home-page.md)

[Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
