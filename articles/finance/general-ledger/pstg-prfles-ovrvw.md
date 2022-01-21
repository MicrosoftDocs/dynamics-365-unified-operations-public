---
# required metadata

title: Posting profiles overview
description: This topic explains how posting profiles are used throughout Microsoft Dynamics 365 apps.
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

In Finance and Operations apps, the term *posting profiles* is used to describe the configurations that control how subledger accounts are converted to main accounts so that they can be used in transactions that are posted to the general ledger. For example, they control how the customer is converted to an Accounts receivable main account when an invoice is posted.

Some modules and features have a page that includes the words "posting profile" in the name (for example, **Customer posting profile** or **Vendor posting profile**). Additionally, some modules have multiple options for configuring the ledger posting for transactions that are generated from the subledger. For example, in the **Production control** module, you can set up the posting by production group, resource, or resource group.

Note that, for many types of transactions, there is an alternative to posting profiles: posting definitions. For supported documents, you can use posting definitions instead of posting profiles to classify main accounts and financial dimensions for accounting entries. If you plan to use encumbrances or pre-encumbrances, a posting definition is required to define the accounts for the accounting entries.

Before you can configure the posting profiles, posting definitions, or the **Accounts for automatic transactions** page, you must configure the chart of accounts on the **Ledger** page in the legal entity that you want to configure.

## Posting types

In Finance and Operations apps, a posting type is used to define a general category for a debit or a credit. This category is independent of the main account in General ledger. There are posting types for each debit or credit in General ledger.

A single voucher can have one or more posting types. For example, a transaction that is posted through a general journal where the account and offset account are set to **Ledger** will have a posting type of **Ledger journal** for both the debit and the credit. By contrast, a vendor invoice will have multiple posting types. Those posting types will include one line for the vendor balance and additional lines for the offset entry, such as **Ledger journal**.

You can view the posting type in the **Posting type** field on the **General** tab of the **Voucher transactions** page.

> [!TIP]
> You can use the **Personalization** toolbar to add the **Posting type** field to the grid on the **Overview** tab, or to move it. In this way, you can make this field easier to access or view when you view vouchers.

## Detail settings for a posting profile 

When you configure posting profiles, the **Account code** field defines the level of the setting. The following options are available: **Table**, **Group**, and **All**. The matching stops after the first match, and the order is from the most specific level to the least specific level. Although the **Account code** field might have a slightly different name in some cases, the behavior and function of the field remain the same. For example, the inventory posting profile includes an **Item code** field and an **Account code** field. Both fields have **Table**, **Group**, and **All** values.

If the **Main account** field is left blank for a posting profile, and you haven't configured a main account on the **Accounts for automatic transaction** page or on a module-specific or feature-specific page, you will receive an error message when you post a transaction that uses the posting type. Typically, the message will be, "The account for \[Posting type\] can't be found."

### Table value

The **Table** value refers to the master record that is associated with the posting profile. Each table record is specific to one value. You specify that value in the field that appears after the **Account code** field. Typically, this field is named **Account** or **Account/Group number**. The exact name varies, depending on the page where it appears.

For example, if you're working with a customer posting profile, the **Table** value represents a specific customer. Therefore, if you select **Table** in the **Account code** field, you must select the customer number in the **Account/Group number** field.

The **Table** value represents the most specific type of record. The system always uses this value, even if you've configured another record where the **Group** or **All** value is selected. This value also overrides any values that you created as default values on the **Accounts for automatic transactions** page.

We don't recommend that you use the **Table** value as the primary mechanism for managing your posting profiles, because data quality issues can occur if a separate posting profile is maintained for each master data record. It's also difficult to maintain and reconcile a separate posting profile for each master data record. Instead, this value should be used to manage exceptions in your posting profiles.

### Group value

The **Group** value refers to the grouping record that is supported by the master record that is associated with the posting profile. Each group record is specific to one value. You specify that value in the field that appears after the **Account code** field. Typically, this field is named **Account** or **Account/Group number**. The exact name varies, depending on the page where it appears.

The **Group** value requires that you first configure a group and link it to one or more records for the account. The **Group** value is less specific than the **Table** value but more specific than the **All** value. If no record has been configured for a table, the system tries to find a record for the group that the record belongs to.

For example, if you're working with a customer posting profile, and you select **Group** in the **Account code** field, you must select a customer group in the **Account/Group number** field. You must predefine the customer groups on the **Customer group** page, and you must specify a customer group when you create a customer.

If you must track multiple main accounts for a given posting type, we recommend that you use the **Group** value. For example, you have three Accounts receivable trade main accounts: one for regular customers, one for employees, and one for intercompany sale. In this case, we recommend that you create three customer groups to segment the customers. Then map each customer group to the correct main account in the customer posting profile. The following table shows the three customer groups for this example.

| Customer group | Name | Description |
|----------------|------|-------------|
| EXT | External customer | This group is used for all standard external-facing customers. |
| EMP | Employees | This group is used for all employees who make purchases from your organization. |
| INT | Intercompany sales | This group is used for all intercompany customer accounts that are used with integration sales and purchase orders. |

In the posting profile, you will then set up three lines. On each line, you select the **Group** value and the related main account.

### All value

The **All** value indicates that the settings apply to all records. If you select the **All** value in the **Account code** field, the **Account/Group number** field is unavailable, and you can't select a specific record to apply the configuration to.

The **All** value is the least specific value. It's used only if the system can't find a match for the **Table** or **Group** value. You should select the **All** value when you have only one main account for a specific posting type.

For example, when you're working with a customer posting profile, the main accounts that you specify apply to all other customers and customer groups that don't have a record for a specific table (customer) or group (customer group).

### Category

Inventory posting profiles have an additional value that is specific to the sales category or procurement category. This value resembles the **Table** value, in that it applies only to a specific sales or procurement category.

### Default value

If you don't create a record for a posting type in a posting profile where the **Account code** field is set to **All**, and the system can't find a matching posting profile record for the **Group** or **Table** value, the system reverts to the default value that can be specified on the **Accounts for automatic transaction** page. For more information, see [Accounts for automatic transactions](accounts-for-auto-transactions.md).

## Clearing accounts

The term *clearing account* is often used in accounting. Some posting types in Microsoft Dynamics 365 apps are clearing accounts. In other words, the balance in the account is cleared out or reversed when another transaction is posted. For example, when you post a purchase order product receipt, the sum of estimated costs of the products, plus tax and any charges on the purchase order lines, is posted to the purchase accrual posting type as a liability. Later, when you invoice the purchase order, the balance is reversed from the purchase accrual posting type and moved to the Accounts payable trade account.

## Additional resources

Many modules in Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and Dynamics 365 Project Operations have a posting profile or additional configurations that control how posting to the general ledger works. Use the following topics to learn more about the posting profiles and posting setups in each module:

- [Accounts for automatic transactions](accounts-for-auto-transactions.md)
- [Accounts payable posting](accts-payble-posting.md)
- [Accounts receiveable posting](accts-recvble-posting.md)
- [Asset leasing posting](../asset-leasing/set-up-lease-posting-accts.md)
- Asset management posting (Coming soon)
- Cash and bank management (Coming soon)
- Currency revaluation posting accounts (Coming soon)
- Expense management posting (Coming soon)
- [Fixed asset posting profile](../fixed-assets/tasks/set-up-fixed-asset-posting-profiles.md)
- Intercompany accounting posting (Coming soon)
- Inventory posting profile (coming soon)
- [Landed cost posting](../../supply-chain/landed-cost/costing-parameters-setup.md)
- [Posting definitions overview](posting-definitions.md)
- Production control posting (Coming soon)
- Project management and accounting posting (Coming soon)
- Service management posting (Coming soon)
- Tax posting (Coming soon)
- Time and attendance posting (Coming soon)
- Transportation management posting (Coming soon)
- Rebate management posting profiles (Coming soon)
