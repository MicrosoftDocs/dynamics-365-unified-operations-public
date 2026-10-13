---
title: DIOT declaration statement
description: Learn about the DIOT declaration statement for Mexico, including prerequisites and an outline on tax information for unmanaged vendors.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/08/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-02-28
ms.search.form: DIOTDeclarationConcept_MX, DIOTDeclarationTaxCode_MX, VendTable
ms.assetid: 0cdb4da3-dca8-4e31-8fd5-8a1f785b5104
---

# DIOT declaration statement

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to set up and generate the **Declaración Informativa de Operaciones con Terceros (DIOT)** declaration statement for Mexico.

Use the DIOT declaration statement (informative declaration of operation with vendors) to report vendor transactions to the Mexican tax authorities (Servicio de Administración Tributaria \[SAT\]). You might need to report these transactions if you're subject to value-added tax (VAT). The DIOT declaration statement is a text file. You can generate this file in Dynamics 365 Finance, and then import it into the government validation and delivery tool. You can also generate consolidated and detailed reports for control purposes. The statement includes transactions that come from purchase orders, invoice register journals, invoice approval journals, and invoice journals. It also includes vendor transactions that come from the **Project** module. Additionally, you can include open transactions or settled transactions.

The DIOT declaration supports reporting of individual vendors and vendors that are eligible to be included in the consolidated **Proveedor Global** record.

> [!IMPORTANT]
> The values that you enter in the report parameters should reflect the applicable regulatory requirements for the reporting period. Regulatory limits can change. Therefore, verify the applicable requirements before you generate the declaration.

## Prerequisites

Before you generate the DIOT declaration, make sure that the required tax information is configured for the legal entity and vendors.

Before you generate the DIOT text file or related reports, complete the following setup:

1. Enter tax registration IDs or numbers for your legal entity.
1. Enter tax information for vendors.

## Set up vendors for DIOT reporting

For each vendor that you need to include in the DIOT declaration, configure the information required for DIOT reporting.  

The setup includes the vendor classification, operation type, and tax registration information that applies to the vendor.  

For a vendor that qualifies for global reporting:  

- Set the vendor type to **15: global vendor**.
- Specify the **Operation type** that applies to the vendor.
- Enter the vendor's actual **RFC number**.  

The operation type and actual RFC remain relevant even when you configure the vendor as **15: global vendor**. If the vendor doesn't qualify for global reporting for a specific reporting period, the DIOT declaration reports the vendor individually by using the applicable operation type and the vendor's actual RFC.  

A vendor that you configure as **15: global vendor** is considered a candidate for global reporting. This configuration doesn't mean that the vendor is always reported as a global vendor.  

When you generate the DIOT declaration, the report evaluates the transactions of each candidate vendor for the selected reporting period. Depending on the report parameters and the vendor's transactions for that period, the vendor can either:  

- Be included in the consolidated **15: global vendor** record.
- Be reported individually as **04: domestic vendor**.

Therefore, the same vendor can be included in the consolidated global record in one reporting period and be reported individually in another reporting period.

Configure the **Type of operation** for each vendor based on how the vendor would be reported individually.

## Tax information for unmanaged vendors

Unmanaged vendors are vendors that you don't register as vendor accounts in Finance. When you register a purchase transaction for this type of vendor, select any ledger account other than the vendor account. Because all purchase transactions are included in the DIOT declaration statement, purchase transactions for unmanaged vendors also require tax registration IDs (RFC or CURP), the type of operation, and other additional information. For regular vendors, define the extra information on the **Vendors** page. However, you can't do this for unmanaged vendors. To capture the required tax information for unmanaged vendors, enter extra information at the transaction level in the following journal transactions when you don't identify the vendor account:

- Invoice journal
- Invoice register
- Expense journal

To define sales tax codes to make extra information fields available for an unmanaged vendor in journal transactions, specify a sales tax code that you set up to allow for extra information in the journal.

## DIOT report configuration

This section describes how to define the concepts and attach the sales tax codes that are required to generate the DIOT declaration statement. In Finance, a concept represents purchase transaction amounts that the tax authorities in Mexico group under different VAT percentages. In the DIOT text file, the total amounts are grouped for each vendor, based on the concepts that you previously defined. Report these concepts in columns 8 through 53 of the DIOT layout format. The other columns of the report are automatically filled in based on vendor information such as the RFC, type of operation, and other related data.
For reporting periods starting from January 2025, the last column reports the **Declare fiscal effects** (**01** - Yes, **02** - No) field.

### Example of concepts

| Concept ID | Concept description                               | Column position in the text file (Order number) |
|------------|---------------------------------------------------|-------------------------------------------------|
| 1          | The base amount of purchases at VAT 16% (settled) | 8                                               |
| 2          | The base amount of purchases at VAT 15% (settled) | 9                                               |
| 3          | VAT amount non recoverable at 16% or 15%          | 10                                              |

Create new concepts on the **DIOT declaration** page. However, you can create only 46 concepts. The first concept should be order number 8 and the last should be order number 53. You can start to create the concepts in a different order, but you must complete all of them (8 through 53) to prevent inconsistencies in the government validation tool. For each concept, you must specify a column type. Specify a column type of **None** if the column is deprecated. Some columns no longer apply and must be reported with a **0,00** amount. If the check box isn't selected, the DIOT declaration statement shows the complete net amount or the tax amount. Additionally, for each column, you can indicate the non-deductible percentage of the net amount or tax amount that appears in the DIOT declaration statement.

#### Example

If the net amount or tax amount is 10,000.00 pesos, and the percentage of the non-deductible amount is 30 percent, the report displays only 30 percent of 10,000.00 pesos, or 3,000.00 pesos. Use the **Sales tax code** button to attach one or more sales tax codes to a concept.

## Generate the DIOT declaration statement

To generate the DIOT declaration statement, select **Tax** > **Declarations** > **Sales tax** > **Generate DIOT declaration**. Specify or select the following information.

| Field | Description |
|---|---|
| Unrealized settlement period | Select the unrealized settlement period. Use this period in the configuration of sales tax codes for conditional taxes. |
| Realized settlement period | Select the realized settlement period. Use this period in the configuration of sales tax codes. |
| From date | Select the period. |
| DIOT report type | Select either **Consolidated** or **Detailed**. |
| Include transactions | Select the available options: **Unrealized** – Include only the unrealized purchase transactions (transactions that aren't settled and created in the period). **Realized** – Include only the realized purchase transactions (transaction that were settled in the period). Both |
| Generate file | Select **Yes** to generate the text file. |
| Percentage of global vendor operations | Enter a percentage of the total vendor transaction amount, based on which the vendor is identified as a **Global** or **Local** vendor. However, on the **Vendors** page, on the **Invoice and delivery** FastTab, **15:domestic/global vendor** must be specified for the vendor in the **Type of vendor** field. |
| Upper limit | Enter the upper threshold amount for the global vendor. For a global vendor, the total payment amount that you must declare is less than or equal to the value in this field. For a domestic vendor, the total payment amount that you must declare is more than the value in this field. |
| Declare fiscal effects | The **Declare fiscal effects** field is mandatory. Starting in the year 2025, it's mandatory to affirm that fiscal effects were given to the receipts that support the transactions carried out with the supplier. Select **Yes** to affirm that fiscal effects were given to the receipts that support the transactions carried out with the suppliers in the reporting period. |

### Upper limit

Specify the maximum amount that the report considers for an individual vendor when it determines whether a vendor that you configure as **15: global vendor** remains eligible for global reporting.

The report calculates the relevant amount for each candidate global vendor for the reporting period.

If the vendor's amount satisfies the **Upper limit**, the vendor remains eligible for the next stage of the global-vendor evaluation.

If the vendor's amount doesn't satisfy the **Upper limit**, the vendor isn't included in the consolidated global record. Instead, the vendor is reported individually as **04: domestic vendor**, by using:

- The specified operation type for the vendor in **Type of operation** of the vendor master data.
- The vendor's actual RFC.
- The DIOT amounts that belong to that vendor.

For example, if the applicable regulation defines a specific maximum amount per supplier, enter that amount in the **Upper limit** field. The report uses the value when it evaluates each candidate global vendor.

> [!NOTE]
> The report evaluates the **Upper limit** for each candidate vendor for the reporting period. It isn't the maximum amount of the final consolidated global record.

### Percentage of global vendor operations

Specify the maximum percentage of the relevant period amount that you can report through the consolidated **15: global vendor** record.

After the report evaluates candidate vendors against the **Upper limit**, it evaluates the combined amount of the remaining candidate global vendors against the **Percentage of global vendor operations**.

The report calculates the relevant total for the reporting period and uses the percentage that you specify to determine the maximum amount that can remain under global-vendor treatment.

For example, if the applicable regulation allows global-vendor operations up to a specified percentage of the relevant payments for the period, enter that percentage in the **Percentage of global vendor operations** field.

> [!IMPORTANT]
> Use the **Upper limit** and **Percentage of global vendor operations** parameters together. Passing the individual-vendor evaluation doesn't by itself guarantee that a vendor is included in the final consolidated global record.

### Amounts in the DIOT declaration statement

In the DIOT declaration statement, the amounts have either positive or negative signs, depending on the amount type that you enter for the purchase transaction. See the following table.

| Amount type in the purchase transaction      | Sign displayed in the DIOT |
|----------------------------------------------|----------------------------|
| Credit amount                                | Plus sign (+)              |
| Debit amount                                 | Minus sign (–)             |
| Credit amount with positive-sales tax amount | Plus sign (+)              |
| Credit amount with negative-sales tax amount | Minus sign (–)             |
| Debit amount with positive-sales tax amount  | Minus sign (–)             |
| Debit amount with negative-sales tax amount  | Plus sign (+)              |

## How `15: global vendor` transactions are processed

When you generate the DIOT declaration, the report evaluates vendors that are configured as **15: global vendor** for the selected reporting period.

The evaluation process consists of the following stages.

### 1. Evaluate each candidate global vendor

The report identifies vendors that are configured as **15: global vendor** and groups the relevant transactions for each vendor for the reporting period.

The report calculates the amount that each vendor contributes to the declaration and compares that amount with the **Upper limit** parameter.

If the vendor satisfies the **Upper limit**, the vendor remains a candidate for global reporting.

If the vendor doesn't satisfy the **Upper limit**, the vendor is reported individually.

For an individually reported vendor, the DIOT output uses:

- **Type of third party:** `04 – Proveedor Nacional`
- **Type of operation:** The applicable operation type for the vendor
- **RFC:** The vendor's actual RFC

The report shows the vendor's amounts in the applicable DIOT fields for that vendor.

### 2. Evaluate the combined global vendor amount

After the report finishes the individual vendor evaluation, it evaluates the vendors that remain eligible for global reporting.

The report:

1. Calculates the relevant total amount for the reporting period.
1. Uses the **Percentage of global vendor operations** parameter to determine the maximum amount that can remain under global-vendor treatment.
1. Groups the remaining candidate transactions by vendor.
1. Calculates each candidate vendor's contribution to the global amount.
1. Processes the candidate vendors according to their contribution amount.
1. Moves vendors to individual reporting when necessary until the amount that remains eligible for global reporting satisfies the configured percentage.

When you move a vendor to individual reporting at this stage, report it as:

- **Type of third party:** `04 – Proveedor Nacional`
- **Type of operation:** The applicable operation type for the vendor
- **RFC:** The vendor's actual RFC

The report continues the evaluation until the remaining global vendor amount satisfies the limit that you calculate from the **Percentage of global vendor operations** parameter.

### 3. Create the consolidated Proveedor Global record

After both eligibility evaluations finish, the report combines all vendors that remain eligible for global reporting into a single DIOT record.

The consolidated record uses the following values:

| DIOT field | Value |
|---|---|
| Type of third party | `15 – Proveedor Global` |
| Type of operation | `87 – Operaciones globales` |
| RFC | `XAXX010101000` |

The report doesn't use the individual vendors' RFCs or their original operation types in this consolidated record.

Instead, the report aggregates the monetary and VAT amounts of all vendors that remain eligible for global reporting into the corresponding fields of the consolidated record.

For each applicable DIOT amount field, the value in the global record represents the combined value of that field for all vendors that are included in the global record.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
