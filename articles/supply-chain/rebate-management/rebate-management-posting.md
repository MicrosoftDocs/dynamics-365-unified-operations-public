---
# required metadata

title: Rebate management posting setup
description: 
author: sherry-zheng
manager: tfehr
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TAMRebateGroup
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: Release 10.0.18
---

# Rebate management posting setup

[!include [banner](../includes/banner.md)]

Rebate management posting profiles are used to determine posting entries for rebate management calculation lines. When a posting profile is selected on the deal header, it applies to all deal lines.

This feature functions across companies by allowing you to set the legal entity to which provisions will be accrued and by which claims will be paid. You can also set different provision debit accounts and write off credit accounts per source posting company.

To set up customer and vendor rebate management posting profiles go to **Rebate management \> Rebate management posting setup \> Rebate management posting profiles**. The **Rebate management posting profiles** page provides a list pane that shows all of your existing profiles, and provides Action Pane buttons for adding or remove profiles in the list. The remaining sections of this topic describe how to use each available settings when creating or editing a profile.

## Settings in the posting profiles header

The following table describes the settings providing in the header section of each rebate management posting profile.

| Field | Description |
| --- | --- |
| Posting profile | Enter a unique name for the profile. |
| Description | Enter a description for the profile. |
| Module | Choose whether the profile is associated with *Customer* or *Vendor* rebates and royalties. |
| Type | Select the profile type (*Rebate* or *Royalty*) |
| Payment type | Determines the format of the posted rebate output.<p>When **Type** is set to *Rebate*, the following payment types are available:</p><ul><li>*None* - There is no default posting type, so you must define the type when doing the processing.</li><li>*Pay using accounts payable* - Posting the rebate creates a vendor invoice to the remittance vendor set up on the rebate customer.</li><li>*Customer deductions* - Posting the rebate creates a customer deduction journal to the rebate customer.</li><li>*Tax invoice customer deductions* - Posting the rebate creates a free text invoice to the rebate customer.</li><li>*Trade spending* - Posting the rebate creates a customer deduction journal to the rebate customer.</li><li>*Reporting* - Posting the rebate creates a customer deduction journal to the rebate customer.</li></ul><p>When **Type** is set to *Royalty*, the following payment types are available:</p><ul><li>*None* - There is no default posting type, so you must define the type when doing the processing.</li><li>*Pay using accounts payable* - Posting the rebate creates a vendor invoice to the rebate vendor account.</li><li>*Reporting* - Posting the rebate creates a vendor invoice to the rebate vendor account.</li></ul> |
| Company | Select the legal entity (company) to which provisions will be accrued and by which claims will be paid. |

## Settings on the Posting FastTab

The following table describes the settings on the **Posting** FastTab of each rebate management posting profile.
<!-- KFM: I don't see how the example column is helping. Am I missing something? -->

<!-- KFM: Review more carefully from here. -->

| **Field** | **Description** | **Example** |
| --- | --- | --- |
| Debit Type | Select to debit Ledger or Customer/Vendor | Ledger Account |
| Debit account | The account which debit amount is posted to when rebates provision is being made | Rebate expense account |
| Credit Type | Select to credit Ledger or Customer/Vendor | Ledger Account |
| Credit account | The account which credit amount is posted to when rebates provision is being made.This account will also be used as debit account when posting the rebate to credit the customer. | Rebate accrual account |
| Provision: Name of Journal | Use the **Name of journal** field in the **Provision** section to select the name of journal used to record the posted provision. | RDProv |
| Type | Select to post the rebate to a ledger, Customer or Vendor accountThis field is set to Customer/Vendor when Payment type = Tax invoice customer deductions. | Customer/Vendor |
| Use account source | **None** - An account must be specified in the rebate account field **Deal Account** - Use the Customer or Vendor account specified on the rebate line_Note: Deal account can only be used where the Rebate management account code = Table and the reconcile by is completed at line level. It also doesn't apply to Customer royalty posting profiles._ | None |
| Rebate Account | The account which actual rebates expense will be posted to. | Customer account |
| Rebate management: Name of Journal | Use the **Name of journal** field in the **Rebate management** section to select the journal that will be used to post a credit note for the rebate amount to the customer. This field is disabled when Payment type = Tax invoice customer deductions | RDGenJnl |
| Item sales tax group | Specify if the rebate is taxable | |
| Main Account | <!-- KFM: Appears to be missing. Not needed? --> Where the Rebate posted does not equal the Provision, the difference can be written off. The account which the write-off of Rebate management provision will be posted to | Revenue account |
| Write off: Name of journal | Where the Rebate posted does not equal the Provision, the difference can be written off. Use the **Name of journal** field in the **Write off** section to select the journal used to record the posted write off | RDWriteOff |

## The Posting by company FastTab

This FastTab allows you to identify the posting account used be each of the companies listed here.

Use the buttons in the toolbar of the **Posting by company** FastTab to add and remove companies (legal entities) in the grid. Each time you add a new row, use the **Company** to specify the legal entity for that row; the **Name** is then filled in automatically.

For each company listed in the grid, select its row and then make the following settings using the fields below the grid:

- **Debit type** - <!-- KFM: It is what it says it is... -->
- **Debit account** - <!-- KFM: It is what it says it is... -->
- **Main account** - <!-- KFM: It is what it says it is... -->

## Payment types

The following table summarizes how various **Payment type** settings (made in the heading of the profile) affect where payments are posted. Payments can post to a customer account, vendor account, or remittance account based on the target transaction and rebate type.

| **Payment type** | **Target transaction type** | **Rebate type** | **Payment to (invoice account)** |
| --- | --- | --- | --- |
| **Pay using accounts payable** | Vendor invoice journal | Customer rebate | Customer's remittance vendor account |
| **Pay using accounts payable** | Vendor invoice journal | Customer royalty | Vendor account |
| **Pay using accounts payable** | Vendor invoice journal | Vendor rebate | Vendor account |
| **Customer deductions** | Daily journal | Customer rebate | Customer account |
| **Tax invoice customer deductions** | Free text invoice | Customer rebate | Customer account |
| **Trade spending** | Daily journal | Customer rebate | Customer account |
| **Reporting** | Daily journal | Customer rebate | Customer account |
| **Reporting** | Daily journal | Vendor invoice journal | Customer royalty | Vendor account |
| **Reporting** | Daily journal | Vendor rebate | Vendor account |

> [!NOTE] <!-- KFM: review this text. -->
> When configuring the Rebate management agreements:
> - 'Reconcile by' = Deal cannot use the Dynamic deal account in Rebate management posting. It needs the customer/vendor account specified.
> - 'Reconcile by' = Line agreements can have a posting profile offsetting to a Dynamic deal account on the agreement line, as it can use the customer as per the agreement line.