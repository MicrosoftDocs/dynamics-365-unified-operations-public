---
# required metadata

title: Tax branch dimensions
description: This topic provides information about tax branches for Thailand.
author: anasyash
ms.date: 01/25/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: 
# ms.devlang: 
ms.reviewer: kfend 
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: 
# ms.search.industry:
ms.author: anasyash
ms.search.validFrom: 2
ms.dyn365.ops.version:
---

# Tax branch dimensions

[!include[banner](../includes/banner.md)]

A tax branch is used to record inventory movement and track the value-added tax (VAT) liability of a legal entity branch. The branches of a Thai legal entity are referred to as tax branches. Each tax branch is assigned the same tax registration number as its head office. All tax transactions that are performed for the legal entity must contain a tax branch, and they must be reported to the government.

The number of tax branches that a legal entity has depends on the number of offices in different locations of the company. For example, if the legal entity has only one office, there is only one tax branch. This tax branch is referred to as the head office. If the legal entity has three offices, there is one head office, and a unique code is assigned to the other two offices.

Specify a default tax branch for vendors and customers. When you post a purchase invoice or sales invoice, the default tax branch code on the purchase order lines or sales order lines is used as the tax branch code for that transaction.

You can create a financial dimension to add tax branch as a dimension. You can then use the tax branch dimension as account segments for shared charts of accounts.

You can view the tax branch code on the following pages:

- **Posted sales tax** (**Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Posted sales tax**): The **Tax branch code** field is updated with the tax branch code that is specified on the purchase order headers and sales order headers, and in the invoice journals, general journals, payment journals, and free text invoices.

- **Posted withholding tax** (**Tax** > **Inquiries and reports** > **Withholding tax inquiries** > **Posted withholding tax**): The **Tax branch code** field is updated with the tax branch code that is specified in the general journals and payment journals.

- **Transaction details** (**Inventory management** > **Inquiries and reports** > **Transactions**, and then, on the Action Pane, select **Transaction details**): The **Taxbranch** field on the **Financial dimensions – financial** and **Financial dimensions – physical** FastTabs is updated with the tax branch code that is assigned to each site on the **Sites** page.

- **Voucher transactions** (**General ledger** > **Inquiries and reports** > **Voucher transactions**): The **Tax branch code** field is updated with the tax branch code that is specified on the purchase order headers and sales order headers, and in the invoice journals, general journals, payment journals, and free text invoices.

You can add tax branch as a dimension to track stock transfers between sites. When you transfer items from one site to another, the tax branch codes are updated for the transferred items.

## Set up tax branches

Before you can set up tax branches, you must set up tax registration numbers for the legal entity on the **Legal entities** page.

For more information, see [Create a legal entity](../../fin-ops-core/fin-ops/organization-administration/tasks/create-legal-entity.md).

The **Tax branch** page is available only if you turn on the **Use tax branch** option on the **General ledger parameters** page.

1. Go to **General ledger** &gt; **Ledger setup** &gt; **General ledger parameters**.

2. On the **Sales tax** tab, on the **Tax options** FastTab, set the **Use tax branch** option to **Yes**.

### Create a tax branch

Use the **Tax branch** page to create tax branches for a legal entity. VAT-registered legal entities must provide the tax branch code that is used for VAT, withholding tax transactions, and inventory movement between branches in the legal entity. You can select a branch as the head office and then update the tax branch code in the transactions by using tax branch as one of the financial dimensions for all financial postings. If a legal entity has many branches, the head office and all the tax branches will use the same tax registration number to report the transactions.

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Tax branch**.

2. On the Action Pane, select **New**.

3. In the **Code** field, enter a unique tax branch code.

4. In the **Name** field, enter a name for the tax branch.

5. Set the **Head office** option to **Yes** to indicate that the tax branch is the head office. Specify at least one tax branch as the head office.

6. On the **Address** FastTab, select **Select address**.

7. In the **Address selection** dialog box, select a company or site address for the tax branch. You must specify a unique address for each tax branch.

## Set up a tax branch for a legal entity

Use the **Financial dimensions** page to set up a tax branch for a legal entity. After you set up a tax branch for a legal entity, you must add the tax branch to the active account structures to make the tax branch dimension value available on all pages that include a **Financial dimensions** tab. You only have to add the tax branch to an account structure one time.

After you've added the tax branch financial dimension to an account structure, the dimension is available on the **Financial dimensions** FastTab on all the journal headers in Accounts payable, Accounts receivable, and General ledger. The tax branch dimension value is also available on the **Sales orders**, **Purchase orders**, **Free text invoices**, and **Inventory journal lines** pages.

For more information, see [Financial dimensions](../general-ledger/financial-dimensions.md) and [Configure account structures](../general-ledger/configure-account-structures.md).

## Set up a tax branch for a vendor or a customer

Create a record of the vendor and customer transactions that are performed at tax branches. Therefore, you must assign a tax branch to each vendor and customer. The tax branch that you specify for a vendor or customer is then used as the default tax branch for all vendor or customer transactions. Use the **All vendors** and **All customers** pages to specify a tax branch for vendors and customers.

1. Go to **Accounts payable** &gt; **Vendors** &gt; **All vendors** or **Accounts receivable** &gt; **Customers** &gt; **All customers**.

2. Open an existing vendor or customer account or create a new vendor or customer account.

3. On the Action Pane, select **Edit**.

4. On the **Financial dimensions** tab, in the **Taxbranch** field, select a tax branch dimension.

## Assign a tax branch to a site

Use the **Sites** page to create one or more sites, and to assign a tax branch to a site to track the inventory movement at that tax branch.

1. Go to **Inventory management** &gt; **Setup** &gt; **Inventory breakdown** &gt; **Sites**.

2. Create a site.

3. In the **Site** field, enter a unique identifier.

4. In the **Name** field, enter a unique name for the site.

5. On the **Tax branch** FastTab, in the **Tax branch** field, select the tax branch code.

6. On the **Addresses** FastTab, select **Add**, and then, in the **New address** dialog box, enter the address details.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]