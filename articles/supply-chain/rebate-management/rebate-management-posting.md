---
# required metadata

title: Rebate management posting setup
description: This topic describes how to set up posting profiles. Posting profiles are used to determine posting entries for Rebate management calculation lines.
author: sherry-zheng
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TAMRebateGroup
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: 10.0.18
---

# Rebate management posting setup

[!include [banner](../includes/banner.md)]

Rebate management posting profiles are used to determine posting entries for Rebate management calculation lines. When a posting profile is selected on the deal header, it applies to all deal lines.

This feature works across companies (legal entities). You can specify the company that provisions will be accrued to and that claims will be paid by. You can also set different provision debit accounts and write-off credit accounts per source posting company.

To set up Rebate management posting profiles for customers and vendors, go to **Rebate management \> Rebate management posting setup \> Rebate management posting profiles**. The **Rebate management posting profiles** page includes a list pane that shows all your existing profiles. You can use the buttons on the Action Pane to add profiles to the list or remove them.

The remaining sections of this topic describe how to use the available fields when you create or edit a profile.

## Posting profile header

The following table describes the settings that are available in the header section of each Rebate management posting profile.

| Field | Description |
|---|---|
| Posting profile | Enter a unique name for the profile. |
| Description | Enter a description of the profile. |
| Module | Select the module that the rebates and royalties of the profile are associated with (*Customer* or *Vendor*). |
| Type | Select the profile type (*Rebate* or *Royalty*). |
| Payment type | <p>This field determines the format of the posted rebate output.<p><p>When the **Type** field is set to *Rebate*, the following values are available:</p><ul><li>*Pay using accounts payable* – When you post a customer rebate, a vendor invoice for the remittance vendor that is set up on the rebate customer is created. When you post a vendor rebate, a vendor invoice for the rebate vendor account is created.</li><li>*Customer deductions* – When you post the rebate, a customer deduction journal for the rebate customer is created.</li><li>*Tax invoice customer deductions* – When you post the rebate, a free text invoice for the rebate customer is created.</li><li>*Trade spending* – When you post the rebate, a customer deduction journal for the rebate customer is created.</li><li>*Reporting* – When you post the rebate, a customer deduction journal for the rebate customer is created.</li></ul><p>When the **Type** field is set to *Royalty*, the following values are available:</p><ul><li>*Pay using accounts payable* – When you post the rebate, a vendor invoice for the rebate vendor account is created.</li><li>*Reporting* – When you post the rebate, a vendor invoice for the rebate vendor account is created.</li></ul><p>For more information, see the [Payment types](#payment-types) section that follows. |
| Company | Select the company (legal entity) that provisions will be accrued to and that claims will be paid by. |

### Payment types

The following table summarizes how the various settings of the **Payment type** field affect where payments are posted. Payments can be posted to a customer account, vendor account, or remittance account, depending on the target transaction and the rebate type.

| Payment type | Target transaction type | Rebate type | Payment to (invoice account) |
|---|---|---|---|
| Pay using accounts payable | Vendor invoice journal | Customer rebate | Customer's remittance vendor account |
| Pay using accounts payable | Vendor invoice journal | Customer royalty | Vendor account |
| Pay using accounts payable | Vendor invoice journal | Vendor rebate | Vendor account |
| Customer deductions | Daily journal | Customer rebate | Customer account |
| Tax invoice customer deductions | Free text invoice | Customer rebate | Customer account |
| Trade spending | Daily journal | Customer rebate | Customer account |
| Reporting | Daily journal | Customer rebate | Customer account |
| Reporting | Vendor invoice journal | Customer royalty | Vendor account |
| Reporting | Vendor invoice journal | Vendor rebate | Vendor account |

> [!NOTE]
> Consider the following points when you set up [Rebate management deals](rebate-management-deals.md):
>
> - For deals where the **Reconcile by** field is set to *Deal*, you can't use the dynamic deal account during posting. You must use a specified customer or vendor account.
> - For deals where the **Reconcile by** field is set to *Line*, you can use a posting profile that offsets to a dynamic deal account on the deal line, because the customer or vendor is set per deal line.

## Posting FastTab

The following table describes the fields that are available on the **Posting** FastTab of each Rebate management posting profile.

| Field | Description |
|---|---|
| Credit type | Select whether to credit a ledger account or a customer. If the **Payment type** field on the header is set to *Tax invoice customer deductions*, this field is set to *Ledger account*. For vendor rebates, this field is set to *Ledger account*. |
| Credit account | Select the account that credit amounts are posted to when rebate provisions are made. This account will also be used as an offset account when the rebate is posted to credit the customer or debit the vendor. |
| Name of journal<br>(In the **Provision** section) | Select the name of the journal to use to record the posted provision. |
| Type | Select whether to post the rebate to a ledger account, or to a customer or vendor. If the **Payment type** field on the header is set to *Tax invoice customer deductions*, this field is set to *Customer/Vendor*. |
| Use account source | <p>Select one of the following values:</p><ul><li>*Fixed account* – If you select this value, you must specify an account in the **Rebate account** field.</li><li>*Deal line account* – Use the customer or vendor account that is specified on the rebate line. You can select this value only for deals where the **Reconcile by** field is set to *Line* and deal lines where the **Account code** field is set to *Table*. It doesn't apply to customer royalty posting profiles or vendor rebates that are based on sales orders.</li></ul> |
| Rebate account | The account that actual rebates expense will be posted to. |
| Name of journal<br>(In the **Rebate management** field group) | Select the name of the journal to use to post a credit note for the rebate amount to the customer or vendor. This field is unavailable when the **Payment type** field on the header is set to *Tax invoice customer deductions*. For customer rebates, journal names of the *Daily* journal type will be available. For customer royalties and vendor rebates, journal names of the *Vendor invoice recording* journal type will be available. |
| Item sales tax group | Specify whether the rebate is taxable. |
| Name of journal<br>(In the **Write off** field group) | If the rebate that is posted doesn't equal the provision, the difference can be written off. Select the name of the journal to use to record the posted write-off. |

## Posting by company FastTab

The **Posting by company** FastTab of each Rebate management posting profile lets you specify the posting account that is used by each company (legal entity) in the grid.

Use the buttons on the toolbar to add companies to the grid and remove them. Each time that you add a row to the grid, use the **Company** field to specify the legal entity for that row. The **Name** field is then set automatically.

Select the row for each company, and then enter the following information by using the fields below the grid:

- **Debit type** – Select whether to debit a ledger account or a vendor. For customer rebates and royalties, this field is set to *Ledger account*.
- **Debit account** – Enter the account that the debit amount is posted to when rebate provisions are made.
- **Main account** – Select the main account for write-offs.
