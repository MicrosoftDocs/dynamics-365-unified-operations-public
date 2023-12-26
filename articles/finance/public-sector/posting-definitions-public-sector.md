---
title: Posting definitions in the public sector
description: This article lists examples of public sector posting definitions that can be used to create subledger journal lines for originating transactions that meet selected criteria.
author: velofog
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: velofog
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Public sector
ms.search.form: BudgetDetailsInquiry, CustGroup, JournalizingDefinition, JournalizingDefinitionTrans, LedgerFund, LedgerParameters, LedgerTransferOpening, MainAccount
---

# Posting definitions in the public sector

[!include [banner](../includes/banner.md)]

This article lists examples of public sector posting definitions that can be used to create subledger journal lines for originating transactions that meet selected criteria. Examples include budget appropriations, pooled cash settlements, write-offs, COD settlements, advanced ledger entries, general ledger year-end close, and proprietary funds.

This article describes the posting definitions functionality available for the public sector. Before you read this article, you should be familiar with posting definitions.

## How do I use these examples of public sector posting definitions?
You can set up the examples in this article on the **Posting definitions** page. Each example contains these sections:

-   Posting definition – Match criteria
-   Posting definition – Generated entries
-   Transactions with the accounts, dimension values, and amounts
-   Ledger entries generated from the posting definition

In the **Match criteria** area, when a match occurs between the accounts and dimension values for the posting definition and the accounts and dimension values on the transaction, ledger entries are generated. These entries are based on the **generated entries** for the posting definition. 

> [!NOTE]
> To associate a posting definition with a specific transaction type, use the **Transaction posting definitions** page. After you associate a posting definition with a transaction type and select the **Use posting definitions** accounting rule on the **General ledger parameters** page, all transactions of the selected transaction type must use posting definitions.

## Example: Budget appropriations
For public sector organizations, original budget balances are recorded as either appropriations for expenses or estimated revenues. The original budget balances are used to track available budget balances against expenditures and the actual revenues that are collected.

A posting definition is created to support the recording of budget register entries to the general ledger, and a transaction posting definition is set up for budget register entries that have a budget type of **Original budget**.

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Expense           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria – Row 1

| Account structure | Generated account number                | Generated debit/credit |
|-------------------|-----------------------------------------|------------------------|
| Balance           | -36300 (Budgetary fund balance account) | Same                   |
| Balance           | -36350 (Appropriation account)          | Balancing              |

### Posting definition – Match criteria – Row 2

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Revenue           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria – Row 2

| Account structure | Generated account number                | Generated debit/credit |
|-------------------|-----------------------------------------|------------------------|
| Balance           | -36300 (Budgetary fund balance account) | Balancing              |
| Balance           | -36340 (Estimated revenue account)      | Same                   |

### Transactions with the accounts, dimension values, and amounts

You enter the accounts, dimension values, and amounts on the budget account entry on the **Budget register entries** list page.

| Account + Dimensions               | Debit | Credit | Comment |
|------------------------------------|-------|--------|---------|
| 101-606400-OU\_1-OU\_3566-Training |  &nbsp; | 250.00 |  &nbsp;  |

### Ledger entries generated from the posting definition

Generated ledger entries are created to record the original budget in each dimension.

| Account + Dimensions | Debit  | Credit | Comment |
|----------------------|--------|--------|---------|
| 101-36300            | &nbsp; | 250.00 | &nbsp;  |
| 101-36350            | 250.00 | &nbsp; | &nbsp;  |

In this example, the fund dimension and account part of the expense account structure match the posting definition criteria. Therefore, when 101-606400-OU\_1-OU\_3566-Training is evaluated, the generated ledger entries are created.

## Examples: Pooled cash settlements
Pooled cash accounting consists of amounts that are deposited by individual funds into a combined ledger account. This improves the control and custody over liquid assets, and promotes the efficient management of excess funds. These amounts can be managed by using a Treasurer’s fund. Therefore, the appropriate proportional amount of the pooled cash and investment balances must be reported for each fund that participates in the pool. To guarantee this, appropriate due-to and due-from entries must be added to the settlements that transfer amounts from one fund to another to accomplish the settlement. 

> [!NOTE] 
> No error message is displayed if a posting definition for settlements isn't specified or match criteria in the posting definition aren't available. Installations that don't use pooled cash settlements or don't require balancing entries on the settlement voucher don't have to set up posting definitions for settlements when posting definitions are enabled for other transactions. 

For accounts payable settlements, vendor payables in one or more funds are used to record the appropriate fund equity transactions in the Treasurer’s fund. For accounts receivable settlements, the customer credit from the payments in the Treasurer’s fund is used to settle the receivables in one or more funds. The vendor balance or customer balance posting entries on the transactions that are being settled are automatically reversed. The use of posting definitions for settlement is optional. The posting definitions are applied at the time of settlement to generate the additional ledger transactions for due-to and due-from entries to balance the settlement voucher by fund. 

You can use posting definitions for the following settlement transaction types:

-   Vendor payment journals, which include vendor payments against invoices, reimbursements, and general ledger credit vouchers and credit memos against invoices
-   Promissory notes, which include payments that use the draw, redraw, remit, and settlement of promissory notes
-   Customer payment journals, which include customer payments, customer general ledger credit vouchers, and credit notes against free text invoices, project invoices, interest notes, and collection letter transactions

To set up posting definitions for vendor payment journals, promissory notes, and customer payment journals, on the **Posting definitions** page, in the **Module** field, select **Bank**. Then, on the **Transaction posting definitions** page, on the **Bank** tab, you can select the appropriate transaction types to associate with the posting definitions.

> [!NOTE] 
> A single posting definition, if it's widely defined, can be used for most vendor, and customer settlement scenarios. The single posting definition must still be associated with both vendor and customer payment journals on the **Bank** tab. 

You can specify a different posting definition for a specific bank and method of payment for vendor and customer payment journals. 

Before posting definitions are applied on settlements, you should complete the following tasks:

-   Associate each vendor or customer who has the Treasurer’s fund (999) on the **Financial dimensions** FastTab of the vendor’s or customer’s details page. Vendor or customer payments can then be generated in the Treasurer’s fund against the vendor or customer summary account that is specified in the vendor or customer posting profiles.
-   To set the default fund, in Accounts receivable, on the **Customer groups** page, on the Action Pane, click **Setup**, and then click **Default financial dimensions**. The Treasurer’s fund will then become the default fund when new customers are associated with a customer group.
-   Associate the Treasurer’s fund with each bank account that is used in settlements. The posted bank account can then be in balance, by fund, with the vendor or customer payment.

You should also complete one of the following tasks:

-   **Option A:** Specify a single due-to account in the Treasurer’s fund for all funds.
-   **Option B:** Specify a different due-to account in the Treasurer’s fund for each fund.

### Option A: Specify a single due-to account for all funds

You can specify a single due-to account in the Treasurer’s fund for all funds. In this case, a single global match criterion addresses all funds (except the Treasurer’s fund), and you must specify the following match criteria and generated entries on the posting definition.

#### Settlement posting definition – Match criteria

| Account structure | Match account number\*                 | Priority |
|-------------------|----------------------------------------|----------|
| Balance           | 999 – Specify a higher priority match entry for the Treasurer’s fund, so that balancing entries aren't generated for this fund. | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Settlement posting definition – Generated entries for match criteria

| Account structure | Generated account number                                                           | Generated debit/credit |
|-------------------|------------------------------------------------------------------------------------|------------------------|
|    &nbsp;         | No generated entries are defined against the match entry for the Treasurer’s fund. |    &nbsp;              |

#### Settlement posting definition – Match criteria

| Account structure | Match account number\*                                                                      | Priority |
|-------------------|---------------------------------------------------------------------------------------------|----------|
| Balance           | Use a global match entry of lower priority to create balancing entries for all other funds. | 10       |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Settlement posting definition – Generated entries for match criteria

| Account structure | Generated account number                                           | Generated debit/credit |
|-------------------|--------------------------------------------------------------------|------------------------|
| Balance           | - 10110 (Equity account in the match entry – Cash account)         | Balancing              |
| Balance           | 999 - 37000 (Equity account in the Treasurer’s fund for all funds) | Same                   |

### Option B: Specify a different due-to account for each fund

You can specify a different due-to account in the Treasurer’s fund for each fund. For every fund that a vendor payable or customer receivable will be generated in (except the Treasurer’s fund), you must specify the following match criteria and generated entries on the posting definition.

#### Settlement posting definition – Match criteria

| Account structure | Match account number\*                                                                                                                | Priority |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------|----------|
| Balance           | 101 – If you use a fund value and a blank main account, the match criterion applies to both customer receivables and vendor payables. | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Settlement posting definition – Generated entries for match criteria

| Account structure | Generated account number                                          | Generated debit/credit |
|-------------------|-------------------------------------------------------------------|------------------------|
| Balance           | 101 - 10110 (Equity account in Fund 101 – Cash account)           | Balancing              |
| Balance           | 999 - 37101 (Equity account in the Treasurer’s fund for Fund 101) | Same                   |

You must add **Match criteria** rows for each fund that has generated entries, to reflect the appropriate fund balancing entry and the equity account of the fund in the Treasurer’s fund. 

From the vendor or customer payment journal, enter the vendor or customer accounts, or create a payment proposal, and then select the invoices to pay. When the journal is posted, the vendor or customer balance posting entries on both the invoice and payment are matched against the posting definition for settlement. If match criteria are found, the generated due-to and due-from entries are added to the settlement voucher. 

The following vouchers are representative of a typical invoice, payment, and settlement scenario.

## Accounts payable example
### Accounts payable invoice voucher

| Account + Dimensions | Debit  | Credit | Comment             |
|----------------------|--------|--------|---------------------|
| 101 - 66100 - 150    | 250.00 | &nbsp; | Expenditure account |
| 101 - 24210          | &nbsp; | 250.00 | Accounts payable    |

### Accounts payable payment voucher

| Account + Dimensions | Debit  | Credit | Comment           |
|----------------------|--------|--------|-------------------|
| 999 - 24210          | 250.00 | &nbsp; | Vendor summary    |
| 999 - 11020          | &nbsp; | 250.00 | Bank/cash account |

### Accounts payable settlement voucher

The accounts payable settlement voucher is accessed through the related vouchers on the vendor payment voucher. 

In this example, the **Match account number** values for the posting definition match the vendor balance posting type accounts. When 999 - 24210 and 101 - 24210 are evaluated, the generated ledger entries will be created only for Fund 101, because no match entries are set up for the Treasurer’s fund (999).

| Account + Dimensions | Debit  | Credit | Comment                                                                  |
|----------------------|--------|--------|--------------------------------------------------------------------------|
| 999 - 24210          | &nbsp; | 250.00 | Vendor summary (System-generated)                                        |
| 101 - 24210          | 250.00 | &nbsp; | Invoice payable (System-generated)                                       |
| 101 - 11010          | &nbsp; | 250.00 | Equity for Fund 101 (Posting definition for settlement)                  |
| 999 - 37101          | 250.00 | &nbsp; | Treasurer’s fund – Due from Fund 101 (Posting definition for settlement) |

### Summarizing the entries across the invoice, payment, and settlement vouchers

The following table shows how the final ledger accounts are affected.

| Account + Dimensions | Debit  | Credit | Comment                                                                  |
|----------------------|--------|--------|--------------------------------------------------------------------------|
| 999 - 11020          | &nbsp; | 250.00 | Bank/cash account                                                        |
| 101 - 66100 - 150    | 250.00 | &nbsp; | Expenditure account                                                      |
| 101 - 11010          | &nbsp; | 250.00 | Equity for Fund 101 (Posting definition for settlement)                  |
| 999 - 37101          | 250.00 | &nbsp; | Treasurer’s fund – Due from Fund 101 (Posting definition for settlement) |

## Accounts receivable example
### Accounts receivable invoice voucher

| Account + Dimensions | Debit  | Credit | Comment             |
|----------------------|--------|--------|---------------------|
| 101 - 44400          | &nbsp; | 250.00 | Revenue account     |
| 101 - 11530          | 250.00 | &nbsp; | Accounts receivable |

### Accounts receivable payment voucher

| Account + Dimensions | Debit  | Credit | Comment           |
|----------------------|--------|--------|-------------------|
| 999 - 11530          | &nbsp; | 250.00 | Customer summary  |
| 999 - 11020          | 250.00 | &nbsp; | Bank/cash account |

### Accounts receivable settlement voucher

The accounts receivable settlement voucher is accessed through the related vouchers on the customer payment voucher.

In this example, the **Match account number** values for the posting definition match the customer balance posting type accounts. When 999 - 11530 and 101 - 11530 are evaluated, the generated ledger entries are created only for Fund 101, because no match entries are set up for the Treasurer’s fund (999).

| Account + Dimensions | Debit  | Credit | Comment                                                                |
|----------------------|--------|--------|------------------------------------------------------------------------|
| 999 - 11530          | 250.00 | &nbsp; | Customer summary (System-generated)                                    |
| 101 - 11530          | &nbsp; | 250.00 | Invoice receivable (System-generated)                                  |
| 101 - 11010          | 250.00 | &nbsp; | Equity for Fund 101 (Posting definition for settlement)                |
| 999 - 37101          | &nbsp; | 250.00 | Treasurer’s fund – Due to Fund 101 (Posting definition for settlement) |

### Summarizing the entries across the invoice, payment, and settlement vouchers

The following table shows how the final ledger accounts are affected.

| Account + Dimensions | Debit  | Credit | Comment                                                                |
|----------------------|--------|--------|------------------------------------------------------------------------|
| 999 - 11020          | 250.00 | &nbsp; | Bank/cash account                                                      |
| 101 - 44400          | &nbsp; | 250.00 | Revenue account                                                        |
| 101 - 11010          | 250.00 | &nbsp; | Equity for Fund 101 (Posting definition for settlement)                |
| 999 - 37101          | &nbsp; | 250.00 | Treasurer’s fund – Due to Fund 101 (Posting definition for settlement) |

In addition to the example earlier in this section, posting definitions for settlements that are associated with the customer payment journal transaction type can also be applied in the following scenarios:

-   Accounts receivable write-offs
-   Accounts receivable free text invoice cash-on-delivery (cash payment) settlements

Accounts receivable write-offs can use posting definitions that are defined for settlement. Therefore, the general ledger credit journal voucher can be generated when balances are posted by fund. Both ledger and customer account type entries on the journal lines are evaluated against the posting definition for settlement. Both use the posting definition that is assigned to the transaction type on the **Accounts receivable** tab on the **Transaction posting definitions** page. Depending on how the write-off is designed to be run, the posting definition for settlement might require additional match criteria. 

When the write-off posting definition is set up to write off balances to an allowance for the Doubtful receivables contra asset account, the posting definition for settlement can also be used for write-offs, provided that the match criterion is already set up for balance sheet accounts that have a mask for the main account. (For more information, see earlier examples, such as the "Settlement posting definition – Match criteria" section.) 

When the write-off posting definition is set up to reverse the originating revenue account, the posting definition for settlement must have the appropriate match criteria for revenue accounting structures, specifically the due-to and due-from accounting entries on the generated entries. For each fund that isn't in the Treasurer’s fund (999), the following entries must be present on the posting definition for settlement.

### Posting definition – Match criteria

| Account structure | Match account number\*                                                     | Priority |
|-------------------|---------------------------------------------------------------------------|----------|
| Revenue           | 101 – If you use a fund value and a blank main account, the criterion is applicable to all ledger entries. | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria

| Account structure | Generated account number                                                           | Generated debit/credit |
|-------------------|------------------------------------------------------------------------------------|------------------------|
| Balance           | 101 - 10110 (Equity account in Fund 101)                                           | Balancing              |
| Same              | 999 - 37101 (Treasurer’s fund – Fund equity account for Fund 101. A single account can be used instead of individual fund equity accounts.) | Same                   |

## Accounts receivable writeoff example
### Accounts receivable invoice voucher

| Account + Dimensions | Debit  | Credit | Comment             |
|----------------------|--------|--------|---------------------|
| 101 - 44400 - -      | &nbsp; | 250.00 | Revenue account     |
| 101 - 11530          | 250.00 | &nbsp; | Accounts receivable |

### Accounts receivable write-off – General ledger credit voucher

In this example, the posting definition for write-off is set to reverse the revenue account.

| Account + Dimensions | Debit  | Credit | Comment                                                                |
|----------------------|--------|--------|------------------------------------------------------------------------|
| 999 - 11530          | &nbsp; | 250.00 | Customer summary                                                       |
| 101 - 44400 - -      | 250.00 | &nbsp; | Bank/cash account                                                      |
| 101 - 11010          | &nbsp; | 250.00 | Equity for Fund 101 (Posting definition for settlement)                |
| 999 - 37101          | 250.00 | &nbsp; | Treasurer’s fund – Due to Fund 101 (Posting definition for settlement) |

### Accounts receivable write-off – Settlement voucher

In this example, the credit that is created in the general ledger voucher is applied to the write-off transaction. Additionally, the **Match account number** values for the posting definition match the customer balance posting type accounts. Therefore, when 999 - 11530 and 101 - 11530 are evaluated, the generated ledger entries are created only for Fund 101, because no match entries are set up for the Treasurer’s fund (999).

| Account + Dimensions | Debit  | Credit | Comment                                                                |
|----------------------|--------|--------|------------------------------------------------------------------------|
| 999 - 11530          | 250.00 | &nbsp; | Customer summary (System-generated)                                    |
| 101 - 11530          | &nbsp; | 250.00 | Invoice receivable (System-generated)                                  |
| 101 - 11010          | 250.00 | &nbsp; | Equity for Fund 101 (Posting definition for settlement)                |
| 999 - 37101          | &nbsp; | 250.00 | Treasurer’s fund – Due to Fund 101 (Posting definition for settlement) |

### Summarizing the entries across the invoice, write-off credit, and settlement vouchers

There is no net effect on the ledger accounts after an invoice is written off in full.

## Accounts receivable free text invoice cash-on-delivery (cash payment) settlement example
Free text invoices use terms of payment where the payment method is set to **COD** and cash payment is enabled. Therefore, they immediately settle themselves at the time of posting without having to use the payment journal. When this kind of settlement occurs, a credit note is created. This note uses the specified cash account on the terms of payment offset and the financial dimensions on the customer summary account. In this kind of settlement, the appropriate receivable accounts that are specified on the invoice aren't automatically reversed. Therefore, the posting definition for settlement must address the reversal of the customer balance posting entries on the invoice and credit, in addition to generating the due-to and due-from entries for settlement. 

To use posting definitions for settlement in this scenario, complete the following additional setup tasks:

-   Create a distinct method of payment for free text invoices that will be settled through this method.
-   Create a new posting definition for the free text invoice cash-on-delivery settlement.
-   Associate the new posting definition (for the customer payment journal against the specific method of payment) on the **Bank** tab on the **Transaction posting definitions** page. To apply the posting definition setup specified for this kind of settlement, select this unique method of payment and the COD/cash payment terms of payment on the invoice.

Then, in the posting definition, enter the following match criteria and generated entries for the Treasurer’s fund (999).

### Posting definition – Match criteria – Row 1

| Account structure | Match account number\*                                          | Generated debit/credit |
|-------------------|-----------------------------------------------------------------|------------------------|
| Balance           | 999 – This match criterion is used only for receivables in the Treasurer’s fund (999). Only two generated entries are required for this match criterion, because due-to and due-from entries aren't applicable for the Treasurer’s fund. | 1                      |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria – Row 1

| Account structure |                                 Generated account number                                  | Generated debit/credit |
|-------------------|-------------------------------------------------------------------------------------------|------------------------|
|      Balance      | 999 - 11530 (Debit the customer balance posting type entry on the credit that is issued.) |       Balancing        |
|       Same        |                      999 - (Credit the receivable in the 999 fund.)                       |          Same          |

### Posting definition – Match criteria – Row 2

| Account structure | Match account number\*                                                | Priority |
|-------------------|-----------------------------------------------------------------------|----------|
| Balance           | 101 – For match criteria that aren't in the Treasurer’s fund, four sets of generated entries are required. Two entries reverse the customer balance posting type entries on the credit and invoice, and two additional entries generate the required due-to and due-from entries. | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria – Row 2

| Account structure | Generated account number                                          | Generated debit/credit |
|-------------------|-------------------------------------------------------------------|------------------------|
| Balance           | 999 - 11530 (Debit the customer balance posting type entry on the credit that is issued.)  | Balancing              |
| Same              | 999 - (Credit the receivable in Fund 101.)                         | Same                   |
| Balance           | 101 - 10110 (Equity account in Fund 101)                           | Balancing              |
| Same              | 999 - 37101 (Treasurer’s fund – Fund equity account for Fund 101. A single account can be used instead of individual fund equity accounts.) | Same                   |

## Accounts receivable cashondelivery (cash payment) settlement example
### Accounts receivable invoice voucher

| Account + Dimensions | Debit  | Credit | Comment                          |
|----------------------|--------|--------|----------------------------------|
| 101 - 44400 - -      | &nbsp; | 250.00 | Revenue account in Fund 101      |
| 999 - 44400 - -      | &nbsp; | 250.00 | Revenue account in Fund 999      |
| 101 - 11530          | 250.00 | &nbsp; | Accounts receivable in Fund 101  |
| 999 - 11535          | 250.00 | &nbsp; | Accounts receivable in Fund 999  |
| 999-11530            | &nbsp; | 500.00 | Customer summary                 |
| 999 - 11020          | 500.00 | &nbsp; | Cash account on terms of payment |

This includes additional credit entries in the voucher.

### Accounts receivable settlement voucher

In this example, the **Match account number** values for the posting definition match the customer balance posting type accounts only on the invoice.

| Account + Dimensions | Debit  | Credit | Comment                                                                |
|----------------------|--------|--------|------------------------------------------------------------------------|
| 999 - 11530          | 250.00 | &nbsp; | Customer summary (Posting definition for settlement)                   |
| 101 - 11530          | &nbsp; | 250.00 | Invoice receivable (Posting definition for settlement)                 |
| 101 - 11010          | 250.00 | &nbsp; | Equity for Fund 101 (Posting definition for settlement)                |
| 999 - 37101          | &nbsp; | 250.00 | Treasurer’s fund – Due to Fund 101 (Posting definition for settlement) |
| 999 - 11530          | 250.00 | &nbsp; | Customer summary (Posting definition for settlement)                   |
| 999 - 11535          | &nbsp; | 250.00 | Customer summary (Posting definition for settlement)                   |

### Summarizing the entries across the invoice, payment, and settlement vouchers

The following table shows how the final ledger accounts are affected.

| Account + Dimensions | Debit  | Credit | Comment                                                                |
|----------------------|--------|--------|------------------------------------------------------------------------|
| 999 - 11020          | 500.00 | &nbsp; | Cash account on terms of payment                                       |
| 101 - 44400 - -      | &nbsp; | 250.00 | Revenue in Fund 101                                                    |
| 999 - 44400 - -      | &nbsp; | 250.00 | Revenue in Fund 999                                                    |
| 101 - 11010          | 250.00 | &nbsp; | Equity for Fund 101 (Posting definition for settlement)                |
| 999 - 37101          | &nbsp; | 250.00 | Treasurer’s fund – Due-to Fund 101 (Posting definition for settlement) |

## Example: Advanced ledger entries
When you create advanced ledger entries, you must select a default posting definition. Then, for each advanced ledger entry line, you can either use the default posting definition or select another one. The posting definitions generate the accounting distributions and subledger journal entries that create, adjust, or reverse the ledger entries and update the ledger accounts. You set up each posting definition for the General ledger app. However, you don't associate the posting definition with a transaction type, as you do for other posting definitions. Instead, you select the posting definition in the advanced ledger entry. 

In this scenario, Accounts payable invoice AP\_0949 was mistakenly posted to Capital improvement fund 300-12300-51002 instead of General fund 100-39810-51001. The following example shows how an advanced ledger entry can use a posting definition to debit the Capital improvement fund and credit the General fund.

### Posting definition – Match criteria – Row 1

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Balance           | 300- -                 | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria – Row 1

| Account structure | Generated account number | Generated debit/credit |
|-------------------|--------------------------|------------------------|
| Balance           | 300-11001                | Balancing              |
| Balance           | 900-11001                | Balancing              |
| Balance           | 900-37300                | Same                   |

### Posting definition – Match criteria – Row 2

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Balance           | 100 - -                | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

### Posting definition – Generated entries for match criteria – Row 2

| Account structure | Generated account number | Generated debit/credit |
|-------------------|--------------------------|------------------------|
| Balance           | 100-11001                | Balancing              |
| Balance           | 900-11001                | Balancing              |
| Balance           | 900-37301                | Same                   |

### Transactions with the accounts, dimension values, and amounts

| Account + Dimensions | Debit | Credit | Comment                    |
|----------------------|-------|--------|----------------------------|
| 300-12300-51002      | 350   | &nbsp; | Advanced ledger entry line |
| 100-39810-51001      |&nbsp; | 350    | Advanced ledger entry line |

### Ledger entries generated from the posting definition

| Account + Dimensions | Debit | Credit | Comment       |
|----------------------|-------|--------|---------------|
| 300-11001            | &nbsp; | 350    | Summary entry |
| 900-11001            | &nbsp; | 350    | Summary entry |
| 900-37300            | 350   | &nbsp; | Summary entry |
| 100-11001            | 350   | &nbsp; | Summary entry |
| 900-11001            | 350   | &nbsp; | Summary entry |
| 900-37301            | &nbsp; | 350    | Summary entry |

## Examples: General ledger year-end close
Organizations use posting definitions in the year-end closing of the general ledger accounts. Posting definitions can be used to close the accounts to fund balances or retained earnings, based on the fund (dimension) class attribute, together with the account close type attribute. Posting definitions are required to close the general ledger accounts and to transfer balances to the opening period in the new fiscal year. 

> [!NOTE]
> To use posting definitions for year-end closing and opening, you need to complete the following setup tasks:

-   On the **General ledger parameters** page, in the **Ledger** section, on the **Fiscal year close** FastTab, select the **Create closing transactions during transfer** option.
-   On the **Main accounts - chart of accounts: %1** page, create a closing account.

The following posting definition examples show the year-end close for governmental funds and proprietary funds.

### Governmental funds example

#### Governmental funds – Posting definition – Match criteria – Row 1

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Expense           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Governmental funds – Posting definition – Generated entries for match criteria – Row 1

| Account structure | Generated account number          | Generated debit/credit |
|-------------------|-----------------------------------|------------------------|
| Account structure | -37300 (Unreserved fund balance ) | Balancing              |

#### Governmental funds – Posting definition – Match criteria – Row 2

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Expense           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Governmental funds – Posting definition – Generated entries for match criteria – Row 2

| Account structure | Generated account number          | Generated debit/credit |
|-------------------|-----------------------------------|------------------------|
| Account structure | -37300 (Unreserved fund balance ) | Balancing              |

#### Governmental funds – Posting definition – Match criteria – Row 3

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Revenue           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Governmental funds – Posting definition – Generated entries for match criteria – Row 3

| Account structure | Generated account number          | Generated debit/credit |
|-------------------|-----------------------------------|------------------------|
| Account structure | -37300 (Unreserved fund balance ) | Balancing              |

After you set up the posting definition, assign it to the **General ledger close** transaction type on the **Transaction posting definitions** page.

#### Governmental funds – Transactions with the accounts, dimension values, and amounts

The ledger accounts balance through the selected period appears on the **Opening transactions** page.

| Account + Dimensions | Debit  | Credit | Comment |
|----------------------|--------|--------|---------|
| 101-66100-130        | 250.00 | &nbsp; | &nbsp;  |

#### Governmental funds – Ledger entries generated from the posting definition

Generated ledger entries are created to record the closing entry.

| Account + Dimensions | Debit  | Credit | Comment |
|----------------------|--------|--------|---------|
| 101-66100-130-       | &nbsp; | 250.00 | &nbsp; |
| 101-37300            | 250.00 | &nbsp; | &nbsp;  |

In this example, Fund 101 is defined as a **Governmental** fund class on the **Funds** page in General ledger. On the **Transaction posting definitions** page, the **General ledger** close transaction type is associated with the **Governmental** fund class and the posting definition. 

The posting definition looks for a match on any account part of the Expense account structure. Therefore, when 101-66100-130- is evaluated, the same ledger account is used, the amount is reversed to close the account, and the balancing generated ledger entry is created.

### Proprietary funds example

#### Proprietary funds – Posting definition – Match criteria – Row 1

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Balance           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Proprietary funds – Posting definition – Generated entries for match criteria – Row 1

| Account structure | Generated account number   | Generated debit/credit |
|-------------------|----------------------------|------------------------|
| Account structure | -37310 (Retained earnings) | Balancing              |

#### Proprietary funds – Posting definition – Match criteria – Row 2

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Expense           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Proprietary funds – Posting definition – Generated entries for match criteria – Row 2

| Account structure | Generated account number   | Generated debit/credit |
|-------------------|----------------------------|------------------------|
| Account structure | -37310 (Retained earnings) | Balancing              |

#### Proprietary funds – Posting definition – Match criteria – Row 3

| Account structure | Match account number\* | Priority |
|-------------------|------------------------|----------|
| Revenue           | - - -                  | 1        |

\*A blank value in the **Match account number** field means that all matching accounts in the defined account structure will be part of the matching rule.

#### Proprietary funds – Posting definition – Generated entries for match criteria – Row 3

| Account structure | Generated account number   | Generated debit/credit |
|-------------------|----------------------------|------------------------|
| Account structure | -37310 (Retained earnings) | Balancing              |

After you set up the posting definition, you assign it to the **General ledger** close transaction on the **Transaction posting definitions** page.

#### Proprietary funds – Transactions with the accounts, dimension values, and amounts

The ledger accounts balance through the selected period appears on the **Opening transactions** page.

| Account + Dimensions | Debit  | Credit | Comment |
|----------------------|--------|--------|---------|
| 601-66100-130        | 250.00 | &nbsp; | &nbsp;  |

#### Proprietary funds – Ledger entries generated from the posting definition

Generated ledger entries are created to record the closing entry.

| Account + Dimensions | Debit  | Credit | Comment |
|----------------------|--------|--------|---------|
| 601-66100-130-       | &nbsp; | 250.00 | &nbsp;  |
| 601-37310            | 250.00 | &nbsp; | &nbsp;  |

In this example, Fund 601 is defined as a **Proprietary** fund class on the **Fund** page. On the **Transaction posting definitions** page, the **General ledger** close transaction type is associated with the **Proprietary** fund class and the posting definition. 

The posting definition looks for a match on any account part of the Expense account structure. Therefore, when 601-66100-130- is evaluated, the same ledger account is used, the amount is reversed to close the account, and the balancing generated ledger entry is created.

## Additional resources

[Accounts payable](../accounts-payable/accounts-payable.md)

[Accounts payable in the public sector](accounts-payable-public-sector.md)

[Accounts receivable in the public sector](accounts-receivable-public-sector.md)

[Budgeting in the public sector](budgeting-public-sector.md)

[General ledger in the public sector](general-ledger-public-sector.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
