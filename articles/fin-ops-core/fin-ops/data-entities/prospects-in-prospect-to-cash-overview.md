---
title: Work with prospects in prospect-to-cash with Dynamics 365 Sales
description: This article provides a conceptual overview of how the prospect-to-cash system works and how it can help improve your business processes.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 03/19/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Work with prospects in prospect-to-cash with Dynamics 365 Sales

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Microsoft Dynamics 365 Sales. This capability includes the ability to integrate accounts of type *Prospect* into the quotation and qualification process across the two systems. The combined solution enables companies to integrate the prospect lifecycle and quotation process flow across Dynamics 365 Sales and Dynamics 365 Supply Chain Management, allowing for few touch points, high efficiency, and high transparency.

The features described in this article build on the [sales quotation lifecycle integration features](add-efficiency-in-quote-to-cash-concept.md) introduced previously.

This article describes how prospects work in prospect-to-cash scenarios and presents examples that illustrate this functionality. For details about how to enable and configure prospects in prospect-to-cash with Dynamics 365 Sales, see [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md).

## Definition of a prospect in prospect-to-cash with Dynamics 365 Sales

A prospect in Supply Chain Management is a *business relation* of type *Prospect*, while a prospect in Dynamics 365 Sales is an *account* of type *Prospect*. From an integration perspective, leads are completely different from prospects in both Dynamics 365 Sales and in Dynamics 365 Supply Chain management. The features described in this article integrate accounts of type *Prospect* in Dynamics 365 Sales with business relations of type *Prospect* in Dynamics 365 Supply Chain Management.

## Basic integration design assumption - Number sequences

The integration design of prospects between Dynamics 365 Sales and Dynamics 365 Supply Chain Management *requires* that prospect account numbers are the same in Dynamics 365 Sales and Dynamics 365 Supply Chain Management. To support this design, it is *required* that number sequences for prospect and the number sequence for customer account in Dynamics 365 Supply Chain management do not overlap. If number sequences overlap, conflicts can occur when converting a prospect to a customer account disallowing the prospect to be converted to a customer.

## Scenario 1: Prospect lifecycle managed from Dynamics 365 Supply Chain Management - prospect of type organization

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type organization.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create New prospect as type organization.

    **Result:** The new prospect is created using the number sequence setup for the prospect entity in Dynamics 365 Supply Chain Management. A new account of *relationship type* Prospect is created in Dynamics 365 Sales with same account number as in Dynamics 365 Supply Chain Management.

1. Add an address of role delivery to the prospect. Add an address of role invoice. Create a new contact for the prospect.

    **Result:** A contact is created in Dynamics 365 Sales and associated with the account type Prospect.

    > [!NOTE]
    > Depending on whether the dual write GAB solution is deployed, either both the delivery address and invoice address is created in Dynamics 365 Sales for the new account, or only the delivery address. Depending on whether the dual write GAB solution is deployed, the contact surfaces either in the Associated contacts tab for the account or on the Account page, Summary tab in the primary contact section in Dynamics 365 Sales.

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Open the prospect and select header ribbon action **General** \> **Convert** \> **Convert to customer**.

    **Result:**A customer account is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. It is intentional that it cannot be changed in the converting process. Customer group is defaulted into the process from the setup in Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the *relationship type* is changed from Prospect to Customer. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account created. The account of *relationship type* Prospect in Dynamics 365 Sales is changed to account *relationship type* customer.

    > [!NOTE]
    > If the dual write GAB solution is deployed, then there are no changes to the already created and synchronized delivery and invoice addresses and contact. If the dual write GAB solution is not deployed, then the address of type invoice is synchronized from the newly created customer account in Dynamics 365 Supply Chain Management to the account in Dynamics 365 Sales. 

## Scenario 2: Prospect lifecycle managed from Dynamics 365 Sales - Prospect as account

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Sales.

1. In Dynamics 365 Sales, go to **Customers** \> **Accounts**. Create New account *relationship type* Prospect. A new prospect is created with the account number selected by the user. Create a new contact for the prospect.

    **Result:** A new business relation type Prospect (of type organization) is created in Dynamics 365 Supply Chain Management with same number as in Dynamics 365 Sales, irrespective of number sequence for prospect setup in Dynamics 365 Supply Chain Management. A contact is created in Dynamics 365 Supply Chain Management and associated with the prospect. 

1. Do one of the following steps:

    - If the Dual write GAB solution is deployed, in Dynamics 365 Sales on the account, on the Addresses tab of the account, add a new address with the role of delivery, and a new address with the role of invoice.

        **Result:** An address of role delivery and an address of role invoice is created in Dynamics 365 Supply Chain Management and associated with the prospect.

    - If the Dual write GAB solution is not deployed, in Dynamics 365 Sales on the account, on the Summary tab, add a delivery address and an invoice address.

        **Result:** It is intentional that no addresses are created in Dynamics 365 Supply Chain Management and associated with the prospect.

    > [!NOTE]
    > For addresses created on the account in Dynamics 365 Sales to synchronize to Dynamics 365 Supply Chain Management, a role must be associated with each address. It is only possible to associate a role when creating an address on an account in Dynamics 365 Sales when the dual write GAB solution is deployed.

1. In Dynamics 365 Sales go to **Customers** \> **Accounts**. Select the account *relationship type* prospect. Change the  *relationship type* to Customer. Select the appropriate Customer group.

    **Result:**The business relation type for the prospect in Dynamics 365 Supply Chain Management is changed from Prospect to Customer. A customer account is created with the same account number as the prospect, irrespective of the number sequence for customer accounts in Dynamics 365 Supply Chain Management. The contact is associated with the customer account in Dynamics 365 Supply Chain Management.

> [!NOTE]
>
> - If the Dual write GAB solution is deployed, then delivery and invoice addresses already synchronized are associated with the customer account in Dynamics 365 Supply Chain Management. The contact is associated with the customer account. If the Dual write GAB solution is not deployed, then no delivery and invoice addresses are synchronized and created in Dynamics 365 Supply Chain Management for the customer account.
> - If the dual write GAB solution is not deployed, then best practice is to create and maintain delivery and invoice addresses for customers and prospects in Dynamics 365 Supply Chain Management.

## Scenario 3: Prospect lifecycle managed from Dynamics 365 Supply Chain Management - Prospect of type person

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type person.

1. In Dynamics 365 Supply Chain Management, go to Sales and **Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a new prospect of type person.

    **Result:** The new prospect is created using the number sequence setup for the prospect entity in Dynamics 365 Supply Chain Management. The new prospect is created as a contact with the *Is Prospect* value set to Yes in Dynamics 365 Sales.

1. Add an address of role delivery to the prospect. Add an address of role invoice. Create a new contact for the prospect.

    > [!NOTE]
    > Depending on whether the dual write GAB solution is deployed, either both the delivery and invoice addresses or only the delivery address are created in Dynamics 365 Sales for the contact with the Is Prospect value set to Yes. If dual write GAB solution is deployed, then the contact is associated to the prospect represented by the contact *IS Prospect* Yes via the party relation. The contact can be accessed in the *Contacts for Party* tab for the contact in Dynamics 365 Sales.

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Open the prospect and select header ribbon action **General** \> **Convert** \> **Convert to customer**.

    **Result:** A customer account of type person is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. It is intentional that it cannot be changed in the converting process. Customer group is defaulted into the process from the setup in Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account created in Dynamics 365 Supply Chain Management. The contact in Dynamics 365 Sales is changed from *Is Prospect* value Yes to No, and *Is Customer* value No to Yes. The contact associated with the contact *IS Customer* Yes, can now be accessed from the *Associated Contacts* tab.

## Scenario 4:  Prospect lifecycle managed from Dynamics 365 Sales - Prospect of type person

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Sales.

1. In Dynamics 365 Sales, go to **Customers** \> **Contacts**. Create new contact with **Is Prospect** set to *Yes*. Create a new contact from the **Contacts for Party** tab.

    **Result:** A new business relation type prospect (of type person) is created in Dynamics 365 Supply Chain Management with contact Last name as prospect ID irrespective of number sequence for prospect setup in Dynamics 365 Supply Chain Management.  

1. Do one of the following steps:

    - If the Dual write GAB solution is deployed, in Dynamics 365 Sales on the contact, on the Addresses tab of the contact, add a new address with the role of delivery and a new address with the role of invoice.

        **Result:** An address of role delivery and an address of role invoice is created in Dynamics 365 Supply Chain Management and associated with the prospect.

    - If the Dual write GAB solution is not deployed, in Dynamics 365 Sales on the contact, on the Summary tab, add a delivery address and an invoice address.

        **Result:** No addresses are created in Dynamics 365 Supply Chain Management and associated with the prospect. This is intentional.

    > [!NOTE]
    > For addresses created on the contact in Dynamics 365 Sales to synchronize to Dynamics 365 Supply Chain Management, a role must be associated with each address. it is only possible to associate a role when creating an address on an contact in Dynamics 365 Sales when the dual write GAB solution is deployed.

1. In  Dynamics 365 Sales go to **Customers** \> **Contacts**. Find the contact you just created. Change the **IS Customer** value from *No* to *Yes*. Select the appropriate Customer group.

    **Result:** The business relation type for the prospect in Dynamics 365 Supply Chain Management is changed from Prospect to Customer. A customer account is created in with the same account number as prospect, irrespective of the number sequence for customer accounts in Dynamics 365 Supply Chain Management.

> [!NOTE]
>
> - If the Dual write GAB solution is deployed, delivery and invoice addresses already synched are associated with the customer account in Dynamics 365 Supply Chain Management. If the Dual write GAB solution is not deployed, no delivery and invoice addresses associated with the contact in Dynamics 365 Sales are synchronized and created in Dynamics 365 Supply Chain Management.
> - If the dual write GAB solution is not deployed, then best practice is to create and maintain delivery and invoice addresses for prospects in Dynamics 365 Supply Chain Management.

## Scenario 5:  Use prospect on sales quotation lifecycle from Dynamics 365 Supply Chain Management

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a new prospect of type *Organization*
1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Sales Quotations** \> **All quotations**. Create New quotation. Select account type Prospect and select the prospect. Proceed with creating the sales quotation details and add lines.
1. In Dynamics 365 Supply Chain Management go to **Sales and Marketing** \> **Sales quotations** \> **All quotations**. Select the quotation you just created. Select Header ribbon action **Quotation** \> **Generate** \> **Send quotation**.
1. Then select Header ribbon action **Follow up** \> **Modify** \> **Convert to customer**. It is intentional, that no dialogue is thrown in the UI.

    **Result:** In Dynamics 365 Supply Chain Management, A customer account is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. Customer group is defaulted into the process from Dynamics 365 Supply Chain Management Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. In Dynamics 365 Sales, the account type prospect is changed to type Customer.

1. In Dynamics 365 Supply Chain Management, from the sales quotation page select header ribbon action **Follow up** \> **Generate** \> **Confirm**.

    **Result:** A sales order is created in Dynamics 365 Supply Chain Management from the quotation confirmation. The sales order is synchronized to Dynamics 365 Sales. The sales quotation in Dynamics 365 Sales is updated to won.

## Scenario 6:  Use prospect on sales quotation lifecycle from Dynamics 365 Sales

1. In Dynamics 365 Sales, go to **Customers** \> **Accounts**. Create New account type Prospect. A new prospect is created with the account number selected by the user.
1. In Dynamics 365 Sales, go to **Quotes**. Create a new quote, select the new account type prospect as potential customer. Proceed with creating the sales quotation details and add lines.

    > [!NOTE]
    > If the dual write GAB solution is deployed then, in Dynamics 365 Sales on the quote, use the address lookup to choose a delivery address by choosing ship to address in the Summary tab, Address section. If the dual write GAB solution is not deployed, there is no address lookup.

1. In Dynamics 365 Sales *Activate* the quote. Then select the action *Create order*.

    **Result:** In Dynamics 365 Sales, the account type prospect is changed to type customer. In Dynamics 365 Supply Chain Management, a customer account is created from the prospect with the same account number as the prospect, irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. Customer group is defaulted into the process from Dynamics 365 Supply Chain Management Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. The sales quotation in Dynamics 365 Supply Chain Management is processed to confirmed, and the sales order is synchronized from Dynamics 365 Sales and created in Dynamics 365 Supply Chain Management.

## Next steps

- [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)
