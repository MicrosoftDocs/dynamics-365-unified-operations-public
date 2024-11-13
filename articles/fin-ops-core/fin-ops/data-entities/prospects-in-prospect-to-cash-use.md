---
title: Work with prospects in prospect-to-cash with Dynamics 365 Sales
description: This article provides a conceptual overview about how the prospect-to-cash system works and how it can help improve your business processes.
author: AditiPattanaik
ms.author: adpattanaik
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

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. This capability includes the ability to integrate accounts of the *Prospect* type into the quotation and qualification process across the two systems. The combined solution enables companies to integrate the prospect lifecycle and quotation process flow across Sales and Supply Chain Management. Therefore, it allows for fewer touch points, better efficiency, and more transparency.

The features that are described in this article build on the [sales quotation lifecycle integration features](add-efficiency-in-quote-to-cash-concept.md) that were previously introduced.

This article describes how prospects work in prospect-to-cash scenarios and presents examples that illustrate this functionality. For details about how to enable and configure prospects in prospect-to-cash with Sales, see [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md).

## Definition of a prospect in prospect-to-cash with Sales

A prospect in Supply Chain Management is a *business relation* of the *Prospect* type, whereas a prospect in Sales is an *account* of the *Prospect* type. From an integration perspective, leads are completely different from prospects in both Sales and in Supply Chain Management. The features that are described in this article integrate accounts of the *Prospect* type in Sales with business relations of the *Prospect* type in Supply Chain Management.

## Scenario 1: Prospect lifecycle managed from Supply Chain Management (prospect of the Organization type)

The following steps show what happens when you manage the prospect lifecycle from Supply Chain Management, and the prospect is of the *Organization* type.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a prospect of the *Organization* type.

    **Result:** The new prospect is created by using the number sequence that's set up for the prospect entity in Supply Chain Management. An account that has a **Relationship type** value of *Prospect* is created in Sales. This account has the same account number that's used in Supply Chain Management.

1. Add an address of the *Delivery* role and an address of the *Invoice* role to the prospect. Create a contact for the prospect.

    **Result:** A contact is created in Sales and associated with the *Prospect* account type.

    > [!NOTE]
    > Depending on whether the dual-write global address book (GAB) solution is deployed, either the delivery address and the invoice address are created in Sales for the new account, or only the delivery address is created. Depending on whether the dual-write GAB solution is deployed, the contact is surfaced in one of two places in Sales: either on the **Associated contacts** tab for the account or on the **Summary** tab in the **Primary contact** section of the **Account** page.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Open the prospect. On the Action Pane, on the **General** tab, in the **Convert** group, select **Convert to customer**.

    **Result:** A customer account is created in Supply Chain Management from the prospect. This customer account has the same account number as the prospect, regardless of the customer number sequence that's set up in Supply Chain Management. It can't be changed during the conversion process. A default customer group is assigned based on the setup on the **Prospects** tab of the **Sales and Marketing parameters** page. The prospect in Supply Chain Management is retired, and the **Relationship type** value is changed from *Prospect* to *Customer*. Addresses and contacts in Supply Chain Management are related to the new customer account. The account that has a **Relationship type** value of *Prospect* in Sales is changed so that it has a **Relationship type** value of *Customer*.

    > [!NOTE]
    > If the dual-write GAB solution is deployed, no changes are made to the previously created and synced delivery address, invoice address, and contact. If the dual-write GAB solution isn't deployed, the address of the *Invoice* role is synced from the newly created customer account in Supply Chain Management to the account in Sales.

## Scenario 2: Prospect lifecycle managed from Sales (prospect as account)

The following steps show what happens when you manage the prospect lifecycle from Sales.

1. In Sales, go to **Customers** \> **Accounts**. Create an account that has a **Relationship type** value of *Prospect*. A prospect is created that has the account number that you selected. Create a contact for the prospect.

    **Result:** A business relation of the *Prospect* type (of the *Organization* type) is created in Supply Chain Management. It has the same number that's used in Sales, regardless of the number sequence that's set up for prospects in Supply Chain Management. A contact is created in Supply Chain Management and associated with the prospect.

1. Follow one of these steps:

    - If the dual-write GAB solution is deployed: In Sales, on the **Addresses** tab of the account, add an address of the *Delivery* role and an address of the *Invoice* role.

        **Result:** An address of the *Delivery* role and an address of the *Invoice* role are created in Supply Chain Management and associated with the prospect.

    - If the dual-write GAB solution isn't deployed: In Sales, on the **Addresses** tab of the account, add a delivery address and an invoice address.

        **Result:** No addresses are created in Supply Chain Management and associated with the prospect.

    > [!NOTE]
    > Before addresses can be synced from an account in Sales to Supply Chain Management, a role must be assigned to each address. When the dual-write GAB solution is deployed, roles can be assigned only when an address is added for an account in Sales.

1. In Sales, go to **Customers** \> **Accounts**. Select an account that has a **Relationship type** value of *Prospect*. Change the **Relationship type** value to *Customer*. Select the appropriate customer group.

    **Result:** The business relation type for the prospect in Supply Chain Management is changed from *Prospect* to *Customer*. A customer account is created that has the same account number as the prospect, regardless of the number sequence that's set up for customer accounts in Supply Chain Management. The contact is associated with the customer account in Supply Chain Management.

> [!NOTE]
> - If the dual-write GAB solution is deployed, delivery and invoice addresses that were previously synced are associated with the customer account in Supply Chain Management. The contact is associated with the customer account. If the dual-write GAB solution isn't deployed, no delivery or invoice addresses are synced or created in Supply Chain Management for the customer account.
> - If the dual-write GAB solution isn't deployed, the best practice is to create and maintain delivery and invoice addresses for customers and prospects in Supply Chain Management.

## Scenario 3: Prospect lifecycle managed from Supply Chain Management (prospect of the Person type)

The following steps show what happens when you manage the prospect lifecycle from Supply Chain Management, and the prospect is of the *Person* type.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a prospect of the *Person* type.

    **Result:** The new prospect is created by using the number sequence that's set up for the prospect entity in Supply Chain Management. The new prospect is created as a contact that has an **Is prospect** value of *Yes* in Sales.

1. Add an address of the *Delivery* role and an address of the *Invoice* role to the prospect. Create a contact for the prospect.

    > [!NOTE]
    > Depending on whether the dual-write GAB solution is deployed, either the delivery address and the invoice address are created in Sales for the contact that has an **Is prospect** value of *Yes*, or only the delivery address is created. If the dual-write GAB solution is deployed, the contact is associated with the prospect that's represented by the contact that has an **Is prospect** value of *Yes* via the party relation. The contact can be accessed on the **Contacts for party** tab for the contact in Sales.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Open the prospect. On the Action Pane, on the **General** tab, in the **Convert** group, select **Convert to customer**.

    **Result:** A customer account of the *Person* type is created in Supply Chain Management from the prospect. This customer account has the same account number as the prospect, regardless of the customer number sequence that's set up in Supply Chain Management. By design, it can't be changed during the conversion process. A default customer group is assigned based on the setup on the **Prospects** tab of the **Sales and marketing parameters** page. The prospect in Supply Chain Management is retired, and the type is changed from *Prospect* to *Customer*. Addresses and contacts in Supply Chain Management are related to the new customer account that was created in Supply Chain Management. The **Is prospect** value for the contact in Sales is changed from *Yes* to *No*, and the **Is Customer** value is changed from *No* to *Yes*. The contact that's associated with the contact that has an **Is Customer** value of *Yes* can now be accessed on the **Associated contacts** tab.

## Scenario 4: Prospect lifecycle managed from Sales (prospect of the Person type)

The following steps show what happens when you manage the prospect lifecycle from Sales.

1. In Sales, go to **Customers** \> **Contacts**. Create a contact that has an **Is prospect** value of *Yes*. On the **Contacts for Party** tab, create a contact.

    **Result:** A business relation of the *Prospect* type (of the *Person* type) is created in Supply Chain Management. The contact family name is used as the prospect ID, regardless of the number sequence that's set up for prospects in Supply Chain Management.

1. Follow one of these steps:

    - If the dual-write GAB solution is deployed: In Sales, on the **Addresses** tab of the contact, add an address of the *Delivery* role and an address of the *Invoice* role.

        **Result:** An address of the *Delivery* role and an address of the *Invoice* role are created in Supply Chain Management and associated with the prospect.

    - If the dual-write GAB solution isn't deployed: In Sales, on the **Summary** tab of the contact, add a delivery address and an invoice address.

        **Result:** No addresses are created in Supply Chain Management and associated with the prospect. This behavior is by design.

    > [!NOTE]
    > Before addresses that are created for the contact in Sales can be synced to Supply Chain Management, a role must be associated with each address. When the dual-write GAB solution is deployed, a role can be assigned only when an address is created for a contact in Sales.

1. In Sales, go to **Customers** \> **Contacts**. Find the contact that you just created, and change the **Is customer** value from *No* to *Yes*. Select the appropriate customer group.

    **Result:** The business relation type for the prospect in Supply Chain Management is changed from *Prospect* to *Customer*. A customer account is created that has the same account number as the prospect, regardless of the number sequence that's set up for customer accounts in Supply Chain Management.

> [!NOTE]
> - If the dual-write GAB solution is deployed, delivery and invoice addresses that were previously synced are associated with the customer account in Supply Chain Management. If the dual-write GAB solution isn't deployed, no delivery or invoice addresses that are associated with the contact in Sales are synced or created in Supply Chain Management.
> - If the dual-write GAB solution isn't deployed, the best practice is to create and maintain delivery and invoice addresses for prospects in Supply Chain Management.

## Scenario 5: Use a prospect on sales quotation lifecycle from Supply Chain Management

The following steps show what happens when you use a prospect on sales quotation lifecycle from Supply Chain Management.

1. In Supply Chain Management, go to **Sales and Marketing** \> **Relationships** \> **Prospects** \> **All prospects**. Create a prospect of the *Organization* type.
1. In Supply Chain Management, go to **Sales and Marketing** \> **Sales Quotations** \> **All quotations**. Create a quotation. Set the account type to *Prospect*, and select the prospect. Create the sales quotation details, and add lines.
1. In Supply Chain Management, go to **Sales and Marketing** \> **Sales quotations** \> **All quotations**. Select the quotation that you just created. On the Action Pane, on the **Quotation** tab, in the **Generate** group, select **Send quotation**.
1. On the Action Pane, on the **Follow up** tab, in the **Modify** group, select **Convert to customer**. By design, no dialog box appears.

    **Result:** In Supply Chain Management, a customer account is created from the prospect. This customer account has the same account number as the prospect, regardless of the customer number sequence that's set up in Supply Chain Management. A default customer group is assigned based on the setup on the **Prospects** tab of the **Sales and marketing parameters** page. The prospect in Supply Chain Management is retired, and the type is changed from *Prospect* to *Customer*. In Sales, the account type is changed from *Prospect* to *Customer*.

1. In Supply Chain Management, return to the **Sales quotation** page. On the Action Pane, on the **Follow up** tab, in the **Generate** group, select **Confirm**.

    **Result:** A sales order is created in Supply Chain Management from the quotation confirmation. The sales order is synced to Sales. The sales quotation in Sales is updated to *Won*.

## Scenario 6: Use a prospect on sales quotation lifecycle from Sales

The following steps show what happens when you use a prospect on sales quotation lifecycle from Sales.

1. In Sales, go to **Customers** \> **Accounts**. Create an account of the *Prospect* type. A prospect is created that has the account number that you select.
1. In Sales, go to **Quotes**. Create a quotation, and select the new account of the *Prospect* type as a potential customer. Create the sales quotation details, and add lines.
1. If the dual-write GAB solution is deployed, on the **Summary** tab of the quotation, in the **Address** field, select a delivery address. If the dual-write GAB solution isn't deployed, there's no **Address** field.
1. In Sales, activate the quotation. Then select **Create order**.

    **Result:** In Sales, the account type is changed from *Prospect* to *Customer*. In Supply Chain Management, a customer account is created from the prospect. This customer account has the same account number as the prospect, regardless of the customer number sequence that's set up in Supply Chain Management. A default customer group is assigned based on the setup on the **Prospects** tab of the **Sales and marketing parameters** page. The prospect in Supply Chain Management is retired, and the type is changed from *Prospect* to *Customer*. The sales quotation in Supply Chain Management is processed to *Confirmed* status, and the sales order is synced from Sales and created in Supply Chain Management.

## Next steps

- [Add efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-concept.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)
- [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)
- [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](prospects-in-prospect-to-cash-enable.md)
