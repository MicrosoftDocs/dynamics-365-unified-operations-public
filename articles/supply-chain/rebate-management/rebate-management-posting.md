---
# required metadata

title: Rebate management posting setup
description: This topic describes how to set up posting profiles, which are used to determine posting entries for rebate management calculation lines
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

| **Field** | **Description** |
| --- | --- |
| Credit Type | Chose whether to credit *Ledger account* or *Customer/Vendor*. |
| Credit account | The account to which credit amounts are posted  when rebates provisions are being made. This account will also be used as the debit account when posting the rebate to credit the customer. |
| Provision: Name of Journal | Use the **Name of journal** field in the **Provision** section to select the name of journal used to record the posted provision. |
| Type | Choose whether to post the rebate to a *Ledger account* or to *Customer/Vendor*. This field is set to *Customer/Vendor* when **Payment type** is *Tax invoice customer deductions*. |
| Use account source | Select one of the following:<ul><li>*None* - An account must be specified in the rebate account field</li><li>*Deal Account* - Use the customer or vendor account specified on the rebate line</li></ul><p>*Deal account* can only be used for deals where **Reconcile by** is *Line* and deal lines where the **Account code** is *Table*. It also doesn't apply to customer royalty posting profiles.</p> |
| Rebate Account | The account which actual rebates expense will be posted to. |
| Rebate management: Name of journal | Use the **Name of journal** field in the **Rebate management** section to select the journal that will be used to post a credit note for the rebate amount to the customer. This field is disabled when **Payment type** = *Tax invoice customer deductions*. |
| Item sales tax group | Specify whether the rebate is taxable. |
| Write off: Name of journal | Where the rebate posted does not equal the provision, the difference can be written off. Use the **Name of journal** field in the **Write off** section to select the journal used to record the posted write off. |

## The Posting by company FastTab

This FastTab allows you to identify the posting account used be each of the companies listed here.

Use the buttons in the toolbar of the **Posting by company** FastTab to add and remove companies (legal entities) in the grid. Each time you add a new row, use the **Company** to specify the legal entity for that row; the **Name** is then filled in automatically.

For each company listed in the grid, select its row and then make the following settings using the fields below the grid:

- **Debit type** - Choose whether to debit *Ledger account* or *Customer/Vendor*.
- **Debit account** - Enter the account to which debit amount is posted when rebate provisions are being made.
- **Main account** - Select the main account for write-offs.

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

> [!NOTE]
> When you are setting up [Rebate management deals](rebate-management-deals.md):
>
> - For deals where **Reconcile by** is *Deal*, you can't use the dynamic deal account when posting. You must use a specified customer/vendor account.
> - For deals where **Reconcile by** is *Line*, you can use a posting profile offsetting to a dynamic deal account on the deal line, because the customer is set per the deal line.