---
# required metadata

title: VAT declaration with registers (JPK_V7M, VDEK)
description: This topic walks you through the process of setting up VAT declaration with registers (also called JPK_V7M, VDEK) in Poland. 
author: liza-golub
ms.date: 11/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
ms.search.region: Poland
# ms.search.industry: 
ms.author: elgolu

---

# VAT declaration with registers (JPK_V7M, VDEK)

[!include [banner](../includes/banner.md)]

This topic explains how to set up a value-added tax (VAT) declaration with
registers (also known as a JPK_V7M, VDEK) in Poland.

As of October 1, 2020, businesses in Poland are responsible for reporting VAT in
an electronic document that consists of a Jednolity Plik Kontrolny VAT (JPK_VAT)
together with the declaration (Jednolity Plik Kontrolny VDEK). The requested
electronic document includes the following information:

-   Both VAT records (a set of information about purchases and sales that is
    produced from the entrepreneur's VAT records for a given period)

-   A VAT declaration (VAT-7 declaration)

## Prerequisites

Before you can prepare Microsoft Dynamics 365 Finance to report a JPK_V7M, your
business processes and the system must meet the following conditions:

-   On the **Sales tax authorities** page (**Tax** \> **Indirect tax** \>
    **Sales tax** \> **Sales tax authorities**), for the tax authority that is
    associated with tax codes that are used in tax transactions that must be
    considered by the JPK_V7M report, the **Report layout** field must be set to
    **Default**. For more information about how to set up sales tax authorities,
    see [Set up sales tax
    authorities](https://docs.microsoft.com/dynamics365/finance/general-ledger/tasks/set-up-sales-tax-authorities).

-   When tax transactions that must be considered by the JPK_V7M report are
    posted, the **Date of VAT register** field must be set.

-   On the **Sales tax codes** page (**Tax** \> **Indirect tax** \> **Sales
    tax** \> **Sales tax codes**), for the sales tax codes that are used in tax
    transactions that must be considered by the JPK_V7M report, the **Type of
    tax** field must be set to **Standard VAT** or **Reduced VAT**.

-   On the **Sales tax codes** page, for the sales tax codes that are used in
    tax transactions that must be considered by the JPK_V7M report, the sales
    tax reporting codes that are used in the Electronic reporting (ER) format of
    the report must be appropriately defined.

## Prepare for JPK_V7M reporting

The solution to support JPK_V7M reporting is based on the [Electronic
messaging](https://docs.microsoft.com/dynamics365/finance/general-ledger/electronic-messaging)
functionality. This functionality provides a flexible approach for setting up
and supporting reporting processes.

The following tasks will prepare Dynamics 365 Finance to report a JPK_V7M:

-   Import and set up ER configurations.

-   Set up application-specific parameters.

-   Import a package of data entities that includes a predefined electronic
    message setup.

-   Set up General ledger parameters.

-   Save the executable class parameters for Electronic messaging.

-   Set up security roles for electronic message processing.

-   Set up an office code for electronic message processing.

### Import and set up ER configurations

To prepare Finance for JPK_V7M reporting, you must import the following
versions, or later versions, of ER configurations.

| **ER configuration name**         | **Type**           | **Description**                                                                                                 |
|-----------------------------------|--------------------|-----------------------------------------------------------------------------------------------------------------|
| Standard Audit File (SAF-T)       | Model              | The common ER model for Standard Audit Files.                                                                   |
| Standard Audit File model mapping | Model mapping      | The model mapping that defines data sources for Polish Standard Audit File (JPK) reports.                       |
| JPK-V7M XML format (PL)           | Format (exporting) | The XML format that provides the file that the Polish Ministry of Finance requires to be periodically reported. |
| JPK-V7M Excel format (PL)         | Format (exporting) | The Excel format for preview information that will be reported in XML format.                                   |

Import the latest versions of these configurations. The version description
usually includes the number of the Microsoft Knowledge Base (KB) article that
explains the changes that were introduced in the configuration version. Use the
Issue search tool in [Microsoft Dynamics Lifecycle Services
(LCS)](https://lcs.dynamics.com/v2) to find the KB article by number.

**Note:** After all the ER configurations from the preceding table are imported,
set the **Default for model mapping** option to **Yes** for the **Standard Audit
File model mapping** configuration on the **Configurations** page.

![](media/default-mm.jpg)

For more information about how to download ER configurations from the Microsoft
global repository, see [Download ER configurations from the Global
repository](<https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo>).

### Set up application-specific parameters

Depending on the tax transaction data, the values of some elements in the
JPK_V7M report can be defined for reporting purposes. There must be enough
transactional data to define values for these elements. Therefore, set up enough
sales tax codes, sales tax groups, and item sales tax groups to differentiate
tax transactions for all the parameters (elements) that are introduced in the
JPK_V7M report. The JPK_V7M format includes application-specific parameters that
can be used to define values for these elements in the report.

The format includes the following lookup fields for setup.

| **Name**                      | **Description**                                                                                                                                                                                                                                                                                         | **Impact**                                                                                                                                                                                       |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ImportSelector                | A designation that is related to input tax on imports of goods, including goods that are taxed in accordance with article 33a of the VAT Act                                                                                                                                                            | This lookup field is used to define the value of the **IMP** marker for purchase documents.                                                                                                      |
| ProceduralMarkingsSelector    | Designations that are related to the procedures                                                                                                                                                                                                                                                         | This lookup field is used to define the values of the following markers for sales documents: **SW**, **EE**, **TP**, **TT-WNT**, **TT_D**, **I_42**, **I_63**, **B_SPV**, and **B_SPV_DOSTAWA**. |
| ServiceDeliverySelector       | An indicator that is related to the delivery and provision of services                                                                                                                                                                                                                                  | This lookup field is used to define the values of all **GTU_\*** markers (from **GTU_1** through **GTU_13**) for sales documents.                                                                |
| DeclarationMarkersSelector    | Markers from the declaration part for tax transactions                                                                                                                                                                                                                                                  | This lookup field is used to define the **P_65** and **P_67** markers for the declaration part, based on the information in documents.                                                           |
| ZakupVAT_MarzaSelector        | The amount of purchases of goods and services from other taxpayers for the direct benefit of tourists, and the amount of second-hand goods, works of art, collectors' items, and antiques that are connected with sales that are taxed based on a margin, in accordance with article 120 of the VAT Act | This lookup field is used to define the **ZakupVAT_Marza** marker for purchase documents.                                                                                                        |
| SalesDocumentTypesSelector    | A designation of the type of the sale document                                                                                                                                                                                                                                                          | This lookup field is used to define the **FP**, **RO**, and **WEW** sales document types.                                                                                                        |
| SprzedazVAT_MarzaSelector     | The value of gross sales of supplies of goods and services that are taxed based on a margin, in accordance with articles 119 and 120 of the VAT Act                                                                                                                                                     | This lookup field is used to define the **SprzedazVAT_Marza** marker for sales documents.                                                                                                        |
| PurchaseDocumentTypesSelector | A designation of the type of the purchase document                                                                                                                                                                                                                                                      | This lookup field is used to define the **MK**, **VAT_RR**, and **WEW** purchase document types.                                                                                                 |

1.  In the **Electronic reporting** workspace, select the **Reporting
    configurations** tile.

2.  On the **Configurations** page, expand **StandardAudit File (SAF-T)**, and
    select **JPK-V7M XML format (PL)**.

3.  On the Action Pane, on the **Configurations** tab, in the **Application
    specific parameters** group, select **Setup**.

![](media/setup-app-spec-params.jpg)

1.  On the **Application specific parameters** page, select the latest version
    of the format that you want to define conditions for.

2.  On the **Lookups** FastTab, select each lookup, and define appropriate
    conditions for it.

3.  On the **Conditions** FastTab, define which tax codes or other available
    criteria must correspond to a specific lookup result. If conditions are
    defined on one line, the system applies them to a source tax transaction by
    using the **AND** operator. If conditions must be applied by using the
    **OR** operator, define them on separate lines. As soon as a tax transaction
    from the reporting period meets a condition in the list, the related marker
    from the lookup result will be reported for the related document. For more
    information about the setup of each lookup field, see the subsections that
    follow.

4.  In the **State** field, select **Completed**, and then save the
    configuration.

![](media/complete-app-spec-params.jpg)

### Import transactions (ImportTransaction)

