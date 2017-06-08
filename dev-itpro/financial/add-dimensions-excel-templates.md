---
# required metadata

title: Add look up values for financial dimensions to Excel templates
description: This topic provides information about how you can add the ability to look up dimension values in Microsoft Excel templates.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 261064
ms.assetid: f3ab87ab-ee8b-462c-bb6f-4d98e0030513
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Add look up values for financial dimensions to Excel templates

[!include[banner](../includes/banner.md)]


This topic provides information about how you can add the ability to look up dimension values in Microsoft Excel templates.

In Dynamics 365 for Operations, the only value that is present on Microsoft Excel templates after installation is MainAccount. This is the only dimension that all customers will have. To add the dimensions to Microsoft Excel templates, you need to complete the steps in the [Add dimensions to the Microsoft Excel templates](dimensions-overview.md) topic. After you have added the dimensions, if you want the ability to look up a list of dimension values, complete the steps in this topic. **Note:**  This information is subject to change for each release, so be sure to check back frequently for the most up-to-date information.

1.  In Visual Studio, open the project where you modified **DimensionCombinationEntity** or **DimensionSetEntity.**
2.  Right-click **DimensionCombinationEntity** or **DimensionSetEntity**. Select **Open**.
3.  Right click **Relations**. Select **New** and then click **Relation.**
4.  In the **Properties** pane, set the following properties.
    -   **Validate** - No
    -   **Cardinality** - ZeroMore
    -   **Name** - Enter the name of the financial dimension, such as Department.
    -   **Related Data Entity** - Select the entity for the financial dimension that you entered in the **Name** field. The following table contains a list of the financial dimensions and the related entities.

        | **Financial dimension 'Use values from'** | **Related entity**                        |
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

    -   **Related Data Entity Cardinality** - **ZeroOne**
    -   **Related Data Entity Role** - Enter a unique name, such as Dimension Department.
    -   **Relationship Type** - **Association**
    -   **Role** - Enter a unique name, such as Dimension Department.

5.  Right-click the **Financial dimension** name under **Relations.**
6.  Select **New**, and then click **Normal.**
7.  In the Properties pane, choose the name of the Financial dimension in the **Field**.
8.  In the Related field, type **Value**. The new relation is similar to the following example.

        DimensionCombinationEntity.DimensionIntegration.Department==DimAttributeOMDepartmentEntity.Value

    ![lookupwiki](./media/lookupwiki.png)

9.  Build the project and then synchronize it with the database.


# See also

[Add dimensions to Microsoft Excel templates](add-dimensions-excel-templates.md)

[Extensibility home page](..\extensibility\extensibility-home-page.md)



