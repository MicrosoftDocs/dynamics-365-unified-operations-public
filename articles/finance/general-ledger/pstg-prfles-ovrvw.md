---
# required metadata

title: Posting profiles overview
description: This topic describes how posting profiles are used throughout Dynamics 365 applications.  
author: rachel-profitt
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerSystemSetup, CustPosting, VendPosting, InventPosting, AssetPosting, ProjPosting, AssetLeasePostingAccounts, ProjCategory, ITMCostTypeTable, ProdGroup, WrkCtrTable, WrkCtrResourceGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---

# Posting profiles overview

Posting profiles are a term used in Dynamics 365 Finance and Operations apps to describe the configurations that control how subledger accounts are converted to main accounts for use in transactions that post to the general ledger. For example, converting the customer to an accounts receivable main account when posting an invoice. In some modules, there is a page that is specifically named posting profile, for example, **Customer posting profile** or **Vendor posting profile**. Other modules and features do not have a page named posting profile. Some modules may have multiple options for configuring the ledger posting for transactions generated from that subledger. One example of this is the **Production control** module, where you can set up the posting by a **Production group**, **Resources** or **Resource groups**, and so on.

It's also important to note that an alternative to posting profiles, called **Posting definitions**, exists for many types of transactions. For supported documents, you can use posting definitions instead of posting profiles to classify main accounts and financial dimensions on accounting entries. If you plan to use encumbrances or pre-encumbrances, a posting definition is required to define the accounts for the accounting entries.

Before you can configure the posting profiles, posting definitions, or **Accounts for automatic transactions**, you must configure the **Chart of accounts** on the **Ledger** page in the legal entity you want to configure.

## Posting types

A posting type in Finance and Operations apps is used to define a general category of a debit or credit that's independent of the main account in General ledger. Posting types are on each debit or credit in General ledger. A single voucher can have one or more posting types. For example, a transaction posted through a general journal with the account and offset account set to ledger will have the posting type of Ledger journal for both the debit and credit. While a vendor invoice will contain multiple posting types including one line for the Vendor balance and additional lines for the offset entry such as Ledger journal.

The posting type can be viewed on the **Voucher transactions** page by clicking the **General** tab and then viewing the **Posting type** field.

> [!TIP]
> You can use the Personalization toolbar to move or add the **Posting type** field to the grid in the **Overview** tab to make this field easily accessible and visible when viewing vouchers.

## Detail settings for a posting profile 

When you configure posting profiles, the **Account code** determines the level of the setting and includes the following options: **Table**, **Group** or **All**. The matching stops after the first match and is ordered from the most specific level to the least specific level. In some cases, the **Account code** field may have a slightly different name, but the behavior and function of the field remains the same. For example, in the **Inventory posting profile** there is an **Item code** field and an **Account code** field each with the options for Table, Group, and All in the list.

If the **Main account** field is left blank for a posting profile, and you haven't configured a main account in the **Accounts for automatic transaction** page or in a module-specific or feature-specific page, you'll receive an error when you post a transaction that uses that posting type. The message will typically read "The account for \[Posting type\] can't be found.

### Table Option

The **Table** option refers to the master record associated with the posting profile. Each table record is specific to one value that you specify in the field that follows the **Account code**. This field is typically called **Account** or **Account/group number**. The exact label on the field might vary depending on the page it appears on.

For example, when working with a **Customer posting profile**, the option for **Table**, represents a specific **Customer**. If you select **Table** in the **Account code** field, you must select the **Customer number** in the **Account/Group number** field.

The **Table** option is the most specific type of record. The system will always use this value, even if you've configured another record with the option for **Group** or **All** selected. This value also overrides any values that you created as default selection in the **Accounts for automatic transactions** page. We don't recommend using the **Table** setting as the primary mechanism for managing your posting profiles because maintaining a separate posting profile per master data record can lead to data quality issues. It's also difficult to maintain and reconcile. Instead, this option should be used to manage exceptions in your posting profiles.

### Group Option

The **Group** option refers to the grouping record that is supported by the master record associated with the posting profile. Each group record is specific to one value that you specify in the field that follows the **Account code**. This field is typically called **Account** or **Account/group number**. The exact label on the field might vary from page to page.

The **Group** option requires that you first configure a group and link the group to one or more records on the account. The **Group** option is less specific than the **Table** option, and more specific than the **All** option. If no record has been configured for a **Table**, the system will try to find a record for the group that the record belongs to.

For example, when you're working with a **Customer posting profile**, and you select **Group** in the **Account code** field, you'll need to select a **Customer group** in the **Account/Group number** field. You must pre-define the **Customer groups** on the **Customer group** page, and when you create a customer, you must specify the **Customer group**.

When you need to track multiple main accounts for any given posting type, we recommend using the **Group** option. For example, if you have three accounts receivable trade main accounts, we recommend creating three **Customer groups** to segment the customers appropriately and map each **Customer group** to the correct **Main account** in the **Customer posting profile**. Let's say for example you have one accounts receivable trade account for regular customers, another for employees, and a third for intercompany sales. In this example you could create three customer groups:

| Customer group | Name               | Description                                                                                          |
|----------------|--------------------|------------------------------------------------------------------------------------------------------|
| EXT            | External customer  | Used for all standard external facing customers.                                                     |
| EMP            | Employees          | Used for all employees that make purchases from your organization.                                   |
| INT            | Intercompany sales | Used for each intercompany customer account that's used with integration sales and purchase orders.  |

The posting profile would be setup with three lines. On each line, the option for **Group** would be selected, and the related main account would be selected.

### All Option

When you select the option for **All**, this indicates that the settings will apply to all records. When you select the **All** option in the **Account code** field, the **Account/Group number** field will be disabled, and you can't select any specific record to apply the configuration to.

The **All** option is the least specific option and is only used if the system isn't able to find a match for the **Table** or **Group** options. The All option should be used when you only have one main account for a particular posting type.

For example, when you're working with a **Customer posting profile**, the main accounts that you specify will apply to all other customers and customer groups that don't have a record for the specific **Table** (customer) or **Group** (Customer group).

### Category

**Inventory posting profiles** have an additional option that's specific to the Sales category or Procurement category. This option is like the table option in that it only applies to a specific Sales or Procurement category. 

### Default

If you don't create a record for a posting type in a posting profile where the **Account code** is set to **All**, and the system can't find a matching posting profile record for the **Group** or **Table** options, the system will revert to the default which can be specified in the **Accounts for automatic transaction** page. For more information, see [Accounts for automatic transactions.](accounts-for-automatic-transactions.md)

## Clearing accounts
A clearing account is a term that's commonly used in accounting. Some posting types in Dynamics 365 applications are clearing accounts. This means that the balance in the account is cleared out or reversed when another transaction is posted. For example, when you post a purchase order product receipt the sum of estimated cost of the products plus tax and any charges on the purchase order lines is posted into the purchase accrual posting type as a liability. Later, when you invoice the purchase order, the balance is reversed from the purchase accrual posting type and moved into the accounts payable trade account.

## Additional Resources

Many modules in Dynamics 365 Finance, Supply Chain Management, Commerce, and Project Operations have a posting profile or additional configurations that control how posting to the general ledger will function. Use the following pages to learn more about the specific posting profiles and posting setups in each module.

-   [Accounts for automatic transactions](accounts-for-automatic-transactions.md)
-   [Accounts payable posting](accounts-payable-posting.md)
-   [Accounts receivable posting](accounts-receivable-posting.md)
-   [Asset leasing posting](../asset-leasing/set-up-lease-posting-accts.md)
-   Asset management posting (Coming soon)
-   Cash and bank management (Coming soon)
-   Currency revaluation posting accounts (Coming soon)
-   Expense management posting (Coming soon)
-   [Fixed asset posting profile](../fixed-assets/tasks/set-up-fixed-asset-posting-profiles.md)
-   Intercompany accounting posting (Coming soon)
-   Inventory posting profile (coming soon)
-   [Landed cost posting](../../supply-chain/landed-cost/costing-parameters-setup.md)
-   [Posting definitions overview](posting-definitions.md)
-   Production control posting (Coming soon)
-   Project management and accounting posting (Coming soon)
-   Service management posting (Coming soon)
-   Tax posting (Coming soon)
-   Time and attendance posting (Coming soon)
-   Transportation management posting (Coming soon)
-   Rebate management posting profiles (Coming soon)

