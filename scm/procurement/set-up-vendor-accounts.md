---
# required metadata

title: Set up vendor accounts
description: This topic describes the types of information that you must specify when you create a new vendor account.
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: smmContactPerson, VendBankAccounts, VendTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 191053
ms.assetid: 06168199-7c54-40e9-a038-4eb274ca958d
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up vendor accounts

[!include[banner](../includes/banner.md)]


This topic describes the types of information that you must specify when you create a new vendor account.

When you create a vendor account, you enter information about the vendor. This information is used to automatically enter data in documents and to track activity that involves the vendor. For example, you can configure the following information for a vendor:

-   Assign a vendor group. Every vendor must be assigned to a vendor group. The vendors in a vendor group have parameters that they share. For example, they might have the same terms of payment.
-   Configure the vendor for catalog import. Vendors can provide a file that contains the catalog of their items and services. This file can be uploaded so that your workers can order from the vendor.
-   Assign the vendor to procurement categories.
-   Allow an existing vendor to do business with another legal entity in your organization.
-   Put a vendor on hold for specific types of transactions.
-   Set up banking information for the vendor, so that you can send payments electronically.
-   Set up tax, delivery, invoice, and payment information for the vendor. By default, these settings are copied to new documents that you create for the vendor.
-   Set up default financial dimensions that are used to automatically post transactions with the vendor to financial accounts.

To speed up the process of creating vendor accounts, you can create templates. To create a template, on the **Vendor** page, on the Action Pane, click **Options** &gt; **Record info**. Then click **Company accounts template**. Company account templates are shared with other users.  

You can also create a user template for your own use. You can't delete a vendor that is associated with other records, such as contacts or products.

## Vendor account numbers
The account number is a unique identifier for a vendor. You can set up account numbers so that they're generated automatically when you create a vendor. You can also configure the number sequence so that account numbers are entered manually. For example, you might want to use the vendor’s telephone number as the identifier.

## Vendor organizations and individual vendors
When you create a new vendor account, you must select whether the vendor is an organization or a person. Your selection affects the information that you must fill in for the vendor. For a person, this information includes the first name, last name, and title. For an organization, this information includes the organization number and the number of employees.

## Addresses
For each vendor, you can define multiple addresses, each of which is used for a different purpose. For example, you can create an address that has a purpose of **Invoice**. Or, if you will pay the vendor by using checks, you can set up an address that has a purpose of **Remit-to**. If you must specify an address to use for money transfers to foreign banks, the purpose will be **SWIFT**.

## Vendor contacts
You can store contacts for a vendor. These contacts can then be used on documents such as purchase orders or requests for quotation (RFQs).  

To add contacts for a vendor, on the **All vendors** page, on the **Vendor** tab, in the **Set up** group, click **Contacts** &gt; **Add contacts**.  

You can create vendor contacts from scratch. Alternatively, you can copy details from another person who is already registered in Microsoft Dynamics 365 for Operations, and edit the information as you require.  

**Note:** Adding a contact for a vendor isn't the same as adding contact information for that vendor. Although you might add general contact information for a vendor, you might also have several specific people who are contacts at that company, and who all have their own contact information.  

You can't delete a contact person record if the contact is referenced on a document. Instead, you can inactivate the contact.  

You can add vendor contacts to your personal contacts in Microsoft Office 365. However, you must first set up synchronization between Dynamics 365 for Operations and Office 365 in both Microsoft Exchange Server synchronization and the Microsoft Outlook setup wizard.

## Vendors in different legal entities
If a vendor is registered for only one legal entity in your organization, and other legal entities must register the same vendor, you can use the **Add vendor to another legal entity** page to configure the vendor to do business with another legal entity. You must select a vendor group, currency, and hold status for the vendor in the selected legal entity.  

If multiple legal entities in your organization do business with the same vendor, and each legal entity maintains a separate vendor account for that vendor, you can merge the party IDs for the vendor accounts. In this way, information such as the address and the number of employees can be shared, so that you must update it in only one place.  

To merge party IDs, follow these steps.

1.  On the **Global address book** page, select the address book records that represent the vendor in each legal entity that should be included in the mapping.
2.  On the Action Pane, click **Merge records**.

## Agreements
When you set up a vendor account, you might also want to register the agreements that you have with the vendor. You can set up price and discount agreements by using the actions on the vendor record. You can also set up a purchase agreement on the **Purchase agreements** page.

## Putting a vendor on hold
You can put a vendor on hold for various transaction types. The following options are available:

-   **No** – No holds have been put on the vendor.
-   **Invoice** – No invoices can be posted for the vendor.
-   **All** – The vendor is on hold for all transaction types. These transaction types include purchase requisitions, invoices, and payments.
-   **Payment** – No payments can be generated for the vendor.
-   **Requisition** – Only purchase requisitions can be created. No other transactions can be created.
-   **Never** – The vendor is never put on hold for inactivity.

When you put a vendor on hold, you can also specify a reason and a date when the on-hold status will end. If you don't enter an end date, the vendor's on-hold status lasts indefinitely.

## Vendor invoice account
If more than one vendor has the same billing address, or if a vendor is invoiced through a third party, you can specify an invoice account on the vendor record. The invoice account is the account that the invoice amount is credited to when you create a vendor invoice from a purchase order. If you don't enter an invoice account on the vendor record, the vendor account is used as the invoice account.

## Vendor bank accounts
If you must make payments to a vendor bank account, you can enter information about the vendor’s bank and bank accounts on the **Vendor bank accounts** page. You can also enter information about validation and payments for the bank account. For example, you can add prenotes to vendor bank accounts. These prenotes can be used to verify the accuracy of account data, such as routing numbers and account numbers. You must specify a default account for payments to the vendor. However, when you make an actual payment, you can change this account to one of the vendor's other accounts.

## Ledger accounts
You can specify the default accounts that automatically appear in vendor invoice journals for the specified vendor. This functionality can be useful if you typically pay for the same types of items or services from the same vendors over time. When you specify a default account, you can quickly and efficiently enter journal entries in the invoice journal. The default accounts that you specify aren't used for purchase orders, or for vendor invoices that are entered on the **Vendor invoice** page.  

You select default accounts on the **Default account setup** page, which you can open from the **Invoice** tab on the vendor record. The accounts that you select here appear in the filtered list of accounts for the vendor account when you enter a journal entry. You can set one of the accounts as a default account.


