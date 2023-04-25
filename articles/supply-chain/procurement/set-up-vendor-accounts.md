---
title: Set up vendor accounts
description: This article describes the types of information that you must specify when you create a new vendor account.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: smmContactPerson, VendBankAccounts, VendTable, VendOnHoldUpdate
ms.topic: how-to
ms.date: 01/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Set up vendor accounts

[!include [banner](../includes/banner.md)]

This article describes the types of information that you must specify when you create a new vendor account.

When you create a vendor account, you enter information about the vendor. This information is used to automatically enter data in documents and to track activity that involves the vendor. For example, you can configure the following information for a vendor:

- Assign a vendor group. Every vendor must be assigned to a vendor group. The vendors in a vendor group have parameters that they share. For example, they might have the same terms of payment.
- Configure the vendor for catalog import. Vendors can provide a file that contains the catalog of their items and services. This file can be uploaded so that your workers can order from the vendor.
- Assign the vendor to procurement categories.
- Allow an existing vendor to do business with another legal entity in your organization.
- Put a vendor on hold for specific types of transactions.
- Set up banking information for the vendor, so that you can send payments electronically.
- Set up tax, delivery, invoice, and payment information for the vendor. By default, these settings are copied to new documents that you create for the vendor.
- Set up default financial dimensions that are used to automatically post transactions with the vendor to financial accounts.

To speed up the process of creating vendor accounts, you can create templates. To create a template, on the **Vendor** page, on the Action Pane, select **Options \> Record info**. Then select **Company accounts template**. Company account templates are shared with other users.  

You can also create a user template for your own use. You can't delete a vendor that is associated with other records, such as contacts or products.

## Vendor account numbers

The account number is a unique identifier for a vendor. You can set up account numbers so that they're generated automatically when you create a vendor. You can also configure the number sequence so that account numbers are entered manually. For example, you might want to use the vendor’s telephone number as the identifier.

## Vendor organizations and individual vendors

When you create a new vendor account, you must select whether the vendor is an organization or a person. Your selection affects the information that you must fill in for the vendor. For a person, this information includes the first name, last name, and title. For an organization, this information includes the organization number and the number of employees.

## Addresses

For each vendor, you can define multiple addresses, each of which is used for a different purpose. For example, you can create an address that has a purpose of *Invoice*. Or, if you'll pay the vendor by using checks, you can set up an address that has a purpose of *Remit-to*. If you must specify an address to use for money transfers to foreign banks, the purpose will be *SWIFT*.

## Vendor contacts

You can store contacts for a vendor. These contacts can then be used on documents such as purchase orders or requests for quotation (RFQs).  

To add contacts for a vendor, on the **All vendors** page, on the **Vendor** tab, in the **Set up** group, select **Contacts \> Add contacts**.  

You can create vendor contacts from scratch. Alternatively, you can copy details from another person who is already registered in Supply Chain Management, and edit the information as you require.  

> [!NOTE]
> Adding a contact for a vendor isn't the same as adding contact information for that vendor. Although you might add general contact information for a vendor, you might also have several specific people who are contacts at that company, and who all have their own contact information.  

You can't delete a contact person record if the contact is referenced on a document. Instead, you can inactivate the contact.  

You can add vendor contacts to your personal contacts in Microsoft 365. However, you must first set up synchronization between Supply Chain Management and Microsoft 365 in both Microsoft Exchange Server synchronization and the Microsoft Outlook setup wizard.

## Vendors in different legal entities

If a vendor is registered for only one legal entity in your organization, and other legal entities must register the same vendor, you can use the **Add vendor to another legal entity** page to configure the vendor to do business with another legal entity. You must select a vendor group, currency, and hold status for the vendor in the selected legal entity.  

If multiple legal entities in your organization do business with the same vendor, and each legal entity maintains a separate vendor account for that vendor, you can merge the party IDs for the vendor accounts. In this way, information such as the address and the number of employees can be shared, so that you must update it in only one place.  

To merge party IDs, follow these steps.

1. On the **Global address book** page, select the address book records that represent the vendor in each legal entity that should be included in the mapping.
1. On the Action Pane, select **Merge records**.

## Agreements

When you set up a vendor account, you might also want to register the agreements that you have with the vendor. You can set up price and discount agreements by using the actions on the vendor record. You can also set up a purchase agreement on the **Purchase agreements** page.

## Putting a vendor on hold

You can put a vendor on hold for various transaction types. The following options are available:

- *No* – No holds have been put on the vendor.
- *Invoice* – No invoices can be posted for the vendor.
- *All* – The vendor is on hold for all transaction types. These transaction types include purchase requisitions, invoices, and payments.
- *Payment* – No payments can be generated for the vendor.
- *Requisition* – Purchase requisitions can't be created for the vendor, and requisition lines already created before the vendor was set on hold can't be converted to a purchase order. Requisition lines for the vendor will be canceled if your policy is set to create purchase orders automatically.
- *Never* – The vendor is never put on hold for inactivity.
- *Purchase order* – Purchase orders can't be created for the vendor, but you can still proceed with any open invoices or payments to the vendor. This option is available only when the *Put vendor on hold for purchase orders* feature is turned on. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. For more information about this feature, see [What's new or changed in Dynamics 365 Supply Chain Management 10.0.29 (October 2022)](../get-started/whats-new-scm-10-0-29.md).

When you put a vendor on hold, you can also specify a reason and a date when the on-hold status will end. If you don't enter an end date, the vendor's on-hold status lasts indefinitely.

You can bulk update the on-hold status to *All* for vendors based on the selected criteria on the **Vendor inactivation** page, and assign a reason for why the vendor is on-hold.

The following criteria are used to include vendors that have been inactive in a period, include or exclude vendors that are employees, and exclude vendors that are under a grace time before the next hold.

- Based on the number of days that you enter in the **In activity period** field on the **Vendor inactivation** page, the application calculates the latest date where the vendor can have any activity to be considered inactive. That is, the current date minus the number of days that you enter. If one or more invoices exist for the vendor where the date is later than the calculated latest date, the vendor will be excluded from the inactivation. This is also validated if the vendor has payments after that date, open purchase requisitions, open purchase orders, requests for quotations, or replies.
- The number of days in the **Grace time before next hold** field is used to calculate the latest grace date. That is, the current date minus the days that you enter. This only applies to vendors who have previously been inactivated. In the case of a previous inactivation, the application verifies the history of other occurrences of inactivation for the vendor and checks if the latest inactivation occurred before the latest grace date. If this is the case, the vendor will be included in the inactivation process.
- The parameter **Include employees** refers to vendors that are linked to an employee. You can set if you want to include those employees.

This process will always exclude vendors where the value in the **Vendor hold** field is *Never*.

Vendors that pass the validations are put on-hold, which sets the **Vendor hold** field value to *All* and the **Reason** to what has been selected. A record in the on-hold history is created for the vendor.

## Vendor invoice account

If more than one vendor has the same billing address, or if a vendor is invoiced through a third party, you can specify an invoice account on the vendor record. The invoice account is the account that the invoice amount is credited to when you create a vendor invoice from a purchase order. If you don't enter an invoice account on the vendor record, the vendor account is used as the invoice account.

## Vendor bank accounts

If you must make payments to a vendor bank account, you can enter information about the vendor’s bank and bank accounts on the **Vendor bank accounts** page. You can also enter information about validation and payments for the bank account. For example, you can add prenotes to vendor bank accounts. These prenotes can be used to verify the accuracy of account data, such as routing numbers and account numbers. You must specify a default account for payments to the vendor. However, when you make an actual payment, you can change this account to one of the vendor's other accounts.

## Ledger accounts

You can specify the default accounts that automatically appear in vendor invoice journals for the specified vendor. This functionality can be useful if you typically pay for the same types of items or services from the same vendors over time. When you specify a default account, you can quickly and efficiently enter journal entries in the invoice journal. The default accounts that you specify aren't used for purchase orders, or for vendor invoices that are entered on the **Vendor invoice** page.  

You select default accounts on the **Default account setup** page, which you can open from the **Invoice** tab on the vendor record. The accounts that you select here appear in the filtered list of accounts for the vendor account when you enter a journal entry. You can set one of the accounts as a default account.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
