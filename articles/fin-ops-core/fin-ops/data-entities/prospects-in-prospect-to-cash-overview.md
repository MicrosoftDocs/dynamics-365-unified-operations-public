---
title: Work with prospects in prospect-to-cash with Dynamics 365 Sales
description: This article provides a conceptual overview of how the prospect-to-cash system works and how it can help improve your business processes.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
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

## Scenario 1: Prospect lifecycle managed from Dynamics 365 Supply Chain Management (prospect of type *Organization*)

The following steps show what happens when you manage the prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type *Organization*.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create New prospect as type *Organization*.

    **Result:** The new prospect is created using the number sequence set up for the prospect entity in Dynamics 365 Supply Chain Management. A new account with a **Relationship type** of *Prospect* is created in Dynamics 365 Sales with the same account number as in Dynamics 365 Supply Chain Management.

1. Add an address of role *Delivery* to the prospect. Add an address of role *Invoice*. Create a new contact for the prospect.

    **Result:** A contact is created in Dynamics 365 Sales and associated with the account type Prospect.

    > [!NOTE]
    > Depending on whether the dual-write global address book (GAB) solution is deployed, either both the delivery address and invoice address are created in Dynamics 365 Sales for the new account, or only the delivery address. Depending on whether the dual-write GAB solution is deployed, the contact surfaces in Dynamics 365 Sales either in the **Associated contacts** tab for the account or on the **Summary** tab in the **Primary contact** section of the **Account** page.

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Open the prospect. On the Action Pane, open the **General** tab and, in the **Convert** group, select **Convert to customer**.

    **Result:** A customer account is created in Dynamics 365 Supply Chain Management from the prospect. The customer account number is the same as the prospect, irrespective of the customer number sequence set up in Dynamics 365 Supply Chain Management. It can't be changed in the conversion process. The customer group is defaulted based on the setup on the **Prospects** tab of the **Sales and Marketing parameters** page. The prospect in Dynamics 365 Supply Chain Management is retired and the **Relationship type** is changed from *Prospect* to *Customer*. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account. The account with a **Relationship type** of *Prospect* in Dynamics 365 Sales is changed to have a **Relationship type** of *Customer*.

    > [!NOTE]
    > If the dual-write GAB solution is deployed, then no changes are made to the already created and synchronized delivery and invoice addresses and contact. If the dual-write GAB solution is not deployed, then the address of type *Invoice* is synchronized from the newly created customer account in Dynamics 365 Supply Chain Management to the account in Dynamics 365 Sales.

## Scenario 2: Prospect lifecycle managed from Dynamics 365 Sales (prospect as account)

The following steps show what happens when you manage the prospect lifecycle from Dynamics 365 Sales.

1. In Dynamics 365 Sales, go to **Customers** \> **Accounts**. Create a new account with a **Relationship type** of *Prospect*. A new prospect is created with the account number you selected. Create a new contact for the prospect.

    **Result:** A new business relation of type *Prospect* (of type *Organization*) is created in Dynamics 365 Supply Chain Management with same number as in Dynamics 365 Sales, irrespective of the number sequence for prospects set up in Dynamics 365 Supply Chain Management. A contact is created in Dynamics 365 Supply Chain Management and associated with the prospect.

1. Do one of the following steps:

    - If the dual-write GAB solution is deployed, then in Dynamics 365 Sales, on the **Addresses** tab of the account, add a new address with a role of *Delivery*, and a new address with a role of *Invoice*.

        **Result:** An address of role *Delivery* and an address of role *Invoice* is created in Dynamics 365 Supply Chain Management and associated with the prospect.

    - If the dual-write GAB solution is not deployed, then in Dynamics 365 Sales, on the **Addresses** tab of the account, add a delivery address and an invoice address.

        **Result:** No addresses are created in Dynamics 365 Supply Chain Management and associated with the prospect.

    > [!NOTE]
    > To sync addresses from an account in Dynamics 365 Sales to Dynamics 365 Supply Chain Management, each address needs a role assigned to it. When the dual-write GAB solution is deployed, roles can only be assigned when adding an address on an account in Dynamics 365 Sales.

1. In Dynamics 365 Sales, go to **Customers** \> **Accounts**. Select an account with a **Relationship type** of *Prospect*. Change the **Relationship type** to *Customer*. Select the appropriate **Customer group**.

    **Result:** The business relation type for the prospect in Dynamics 365 Supply Chain Management is changed from *Prospect* to *Customer*. A customer account is created with the same account number as the prospect, irrespective of the number sequence for customer accounts in Dynamics 365 Supply Chain Management. The contact is associated with the customer account in Dynamics 365 Supply Chain Management.

> [!NOTE]
>
> - If the dual-write GAB solution is deployed, then delivery and invoice addresses already synchronized are associated with the customer account in Dynamics 365 Supply Chain Management. The contact is associated with the customer account. If the dual-write GAB solution is not deployed, then no delivery or invoice addresses are synchronized and created in Dynamics 365 Supply Chain Management for the customer account.
> - If the dual-write GAB solution is not deployed, then best practice is to create and maintain delivery and invoice addresses for customers and prospects in Dynamics 365 Supply Chain Management.

## Scenario 3: Prospect lifecycle managed from Dynamics 365 Supply Chain Management (prospect of type *Person*)

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type *Person*.

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a new prospect of type *Person*.

    **Result:** The new prospect is created using the number sequence setup for the prospect entity in Dynamics 365 Supply Chain Management. The new prospect is created as a contact with the **Is prospect** value set to *Yes* in Dynamics 365 Sales.

1. Add an address of role *Delivery* to the prospect. Add an address of role *Invoice*. Create a new contact for the prospect.

    > [!NOTE]
    > Depending on whether the dual-write GAB solution is deployed, either both the delivery and invoice addresses or only the delivery address are created in Dynamics 365 Sales for the contact with the **Is prospect** value set to *Yes*. If the dual-write GAB solution is deployed, then the contact is associated to the prospect represented by the contact with **Is prospect** set to *Yes* via the party relation. The contact can be accessed on the **Contacts for party** tab for the contact in Dynamics 365 Sales.

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Open the prospect. On the Action Pane, open the **General** tab and, in the **Convert** group, select **Convert to customer**.

    **Result:** A customer account of type *Person* is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. It is intentional that it cannot be changed in the converting process. The customer group is defaulted based on the setup on the **Prospects** tab of the **Sales and marketing parameters** page. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from *Prospect* to *Customer*. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account created in Dynamics 365 Supply Chain Management. The contact in Dynamics 365 Sales is changed from **Is prospect** value *Yes* to *No*, and **Is Customer** value *No* to *Yes*. The contact associated with the contact **Is Customer** *Yes*, can now be accessed from the **Associated contacts** tab.

## Scenario 4:  Prospect lifecycle managed from Dynamics 365 Sales (prospect of type *Person*)

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Sales.

1. In Dynamics 365 Sales, go to **Customers** \> **Contacts**. Create new contact with **Is prospect** set to *Yes*. Create a new contact from the **Contacts for Party** tab.

    **Result:** A new business relation type prospect (of type *Person*) is created in Dynamics 365 Supply Chain Management with contact Last name as prospect ID irrespective of number sequence for prospect setup in Dynamics 365 Supply Chain Management.  

1. Do one of the following steps:

    - If the dual-write GAB solution is deployed, in Dynamics 365 Sales on the contact, on the Addresses tab of the contact, add a new address with the role of delivery and a new address with the role of invoice.

        **Result:** An address of role delivery and an address of role invoice is created in Dynamics 365 Supply Chain Management and associated with the prospect.

    - If the dual-write GAB solution is not deployed, in Dynamics 365 Sales on the contact, on the Summary tab, add a delivery address and an invoice address.

        **Result:** No addresses are created in Dynamics 365 Supply Chain Management and associated with the prospect. This is intentional.

    > [!NOTE]
    > For addresses created on the contact in Dynamics 365 Sales to synchronize to Dynamics 365 Supply Chain Management, a role must be associated with each address. it is only possible to associate a role when creating an address on an contact in Dynamics 365 Sales when the dual-write GAB solution is deployed.

1. In  Dynamics 365 Sales go to **Customers** \> **Contacts**. Find the contact you just created. Change the **Is customer** value from *No* to *Yes*. Select the appropriate customer group.

    **Result:** The business relation type for the prospect in Dynamics 365 Supply Chain Management is changed from *Prospect* to *Customer*. A customer account is created in with the same account number as prospect, irrespective of the number sequence for customer accounts in Dynamics 365 Supply Chain Management.

> [!NOTE]
>
> - If the dual-write GAB solution is deployed, delivery and invoice addresses already synched are associated with the customer account in Dynamics 365 Supply Chain Management. If the dual-write GAB solution is not deployed, no delivery and invoice addresses associated with the contact in Dynamics 365 Sales are synchronized or created in Dynamics 365 Supply Chain Management.
> - If the dual-write GAB solution is not deployed, then best practice is to create and maintain delivery and invoice addresses for prospects in Dynamics 365 Supply Chain Management.

## Scenario 5:  Use a prospect on sales quotation lifecycle from Dynamics 365 Supply Chain Management

The following steps show what happens when you use a prospect on sales quotation lifecycle from Dynamics 365 Supply Chain Management.

1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a new prospect of type *Organization*
1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Sales Quotations** \> **All quotations**. Create a new quotation. Set the account type to *Prospect* and select the prospect. Proceed with creating the sales quotation details and add lines.
1. In Dynamics 365 Supply Chain Management, go to **Sales and Marketing** \> **Sales quotations** \> **All quotations**. Select the quotation you just created. On the Action Pane, open the **Quotation** tab and, from the **Generate** group, select **Send quotation**.
1. On the Action Pane, open the **Follow up** tab and, from the **Modify** group, select **Convert to customer**. No dialog is shown (this is intentional).

    **Result:** In Dynamics 365 Supply Chain Management, a customer account is created from the prospect. The customer account number is the same as the prospect number irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. The customer group is defaulted based on the setup on the **Prospects** tab of the **Sales and marketing parameters** page. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from *Prospect* to *Customer*. In Dynamics 365 Sales, the account type prospect is changed to type *Customer*.

1. Return to the **Sales quotation** page in  Dynamics 365 Supply Chain Management. On the Action Pane, open the **Follow up** tab and, from the **Generate** group, select **Confirm**.

    **Result:** A sales order is created in Dynamics 365 Supply Chain Management from the quotation confirmation. The sales order is synchronized to Dynamics 365 Sales. The sales quotation in Dynamics 365 Sales is updated to *Won*.

## Scenario 6:  Use a prospect on sales quotation lifecycle from Dynamics 365 Sales

The following steps show what happens when you use a prospect on sales quotation lifecycle from Dynamics 365 Sales.

1. In Dynamics 365 Sales, go to **Customers** \> **Accounts**. Create a new account of type *Prospect*. A new prospect is created with the account number you select.
1. In Dynamics 365 Sales, go to **Quotes**. Create a new quote, select the new account of type *Prospect* as a potential customer. Proceed with creating the sales quotation details and add lines.

    > [!NOTE]
    > If the dual-write GAB solution is deployed, then on the quote in Dynamics 365 Sales, choose a delivery address for the **Address** field on the **Summary** tab. If the dual-write GAB solution is not deployed, there is no **Address** field.

1. In Dynamics 365 Sales, **Activate** the quote. Then select **Create order**.

    **Result:** In Dynamics 365 Sales, the account type is changed from *Prospect* to *Customer*. In Dynamics 365 Supply Chain Management, a customer account is created from the prospect with the same account number as the prospect, irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. The customer group is defaulted based on the setup on the **Prospects** tab of the **Sales and marketing parameters** page. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from *Prospect* to *Customer*. The sales quotation in Dynamics 365 Supply Chain Management is processed to confirmed, and the sales order is synchronized from Dynamics 365 Sales and created in Dynamics 365 Supply Chain Management.

## Next steps

- [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)
- [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)
- [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md)
