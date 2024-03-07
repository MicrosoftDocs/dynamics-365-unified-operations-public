---
title: Enable prospect in prospect to cash with Dynamics 365 Sales
description: This article provides a conceptual overview of how the improved prospect-to-cash system works and how it can help improve your business processes.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 03/01/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable prospect in prospect-to-cash with Dynamics 365 Sales

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.39 and later, this capability has been improved to integrate accounts of type prospect and customer seamlessly in the quotation process flow and the prospect qualification process across the two systems. These changes are intended to be used only in the context of prospect-to-cash integration between Sales and Supply Chain Management.

## Definition of a prospect in prospect-to-cash with Dynamics 365 Sales
In Dynamics Supply Chain Management version 10.0.34, Microsoft enabled Sales quotation lifecycle integration with Dynamics 365 Sales. An integral part of any quotation process is to engage with prospective customers, prospects, in the process. Only when the quotation is won with the prospect, does a prospect move forward in the lifecycle to become a customer for a sales order. With 10.0.39, prospects are  supported in the prospect-to-cash process across Dynamics 365 Sales and Dynamics 365 Supply Chain management. 

A prospect in Dynamics 365 Sales is an account of type Prospect. From an integration perspective, a lead in neither Dynamics 365 Sales nor in Dynamics 365 Supply Chain management is considered a prospect. A prospect in Dynamics 365 Supply Chain Management is a business relation with the business relation type Prospect, while a prospect in Dynamics 365 Sales is an account of type prospect. The feature _Enable prospect in sales quotation lifecycle with Dynamics 365 Sales_ covers the lifecycle integration of Dynamics 365 Sales account type Prospect and Dynamics 365 SCM business relation, business relation type Prospect.

When **Integrate quotation lifecycles** feature is enabled [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md) it is possible to enable the **Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales** feature in feature management. When the **Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales** feature is enabled and turned on in Accounts Receivables parameters, then prospect integration between the two systems is supported. 

### Basic integration design assumption 
It is very important to note that the integration design of prospects between Dynamics 365 Sales and Dynamics 365 Supply Chain Management **requires** that prospect account numbers are the same in Dynamics 365 Sales and Dynamics 365 Supply Chain Management. To support this design, it is **required** that number sequences for prospect and the number sequence for customer account in Dynamics 365 Supply Chain management do not overlap. If number sequences overlap, conflicts can occur when converting a prospect to a customer account dissallowing the prospect to be converted to a customer.

### Scenario 1: Prospect lifecycle managed from Dynamics 365 Supply Chain Management - prospect of type organization
The following sections provides some of the more common scenarioes enabled by this new capability.

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type organization.
1. In Supply Chain Management, navigate to Sales and Marketing>Relationships>Prospects>All prospects. Create New prospect as type organization.
Result: The new prospect is created using the number sequence setup for the prospect entity. A new account of type Prospect is created in Dynamics 365 Sales with same account number as in Dynamics 365 Supply Chain Management.

2. Add an address of role Delivery to the prospect. Add an address of role invoice. Create a new contact of type person for the prospect.
Result: A contact is created in Dynamics 365 Sales and associated with the account type Prospect.

    > [!NOTE]
    > Depending on whether the dual write GAB solution is deployed, either both the delivery address and invoice address is created in   Dynamics 365 Sales for the new account, or only a delivery address. Depending on whether the dual write GAB solution is deployed, the  contact surfaces either in Associated Contacts tab for the account or on the Account page, Summary tab in the primary contact section. 
    > 
   
4. In Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships > Prospects > All prospects. Open the prospect and select header ribbon action General > Convert > Convert to customer.
Result:A customer account is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. It cannot be changed in the converting process. Customer group is defaulted into the process from the setup in Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account created in Dynamics 365 Supply Chain Management. The account of type Prospect in Dynamics 365 Sales is changed to account type customer.

 > [!NOTE]
    > If the dual write GAB solution is deployed there are no changes to the already created and synchronized delivery address and invoice address and contact. If the dual write GAB solution is not deployed, then the address of type invoice would now be synchronized and created from the newly created customer account in Dynamics 365 Supply Chain Management to the account in Dynamics 365 Sales. 

### Scenario 2: Prospect lifecycle managed from Dynamics 365 Sales

The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Sales.
1. In Dynamics 365 Sales, navigate to Customers > Accounts. Create New account type Prospect. A new prospect is created with the account number selected by the user. Create a new contact for the prospect.
Result:A new business relation type Prospect is created in Dynamics 365 Supply Chain Management with same number as in Sales, irrespective of number sequence for prospect setup in Dynamics 365 Supply Chain Management. A contact is created in Dynamics 365 Supply Chain Management and associated with the prospect. 

2a. If the Dual write GAB solution is deployed, in Dynamics 365 Sales on the account, on the Addresses tab of the account, add a new address with the role of delivery, and a new address with the role of invoice. 
Result: An address of role delivery and an address of role invoice is created in Dynamics 365 Supply Chain Management and associated with the prospect. 
2b. If the Dual write GAB solution is not deployed, in Dynamics 365 Sales on the account, on the Summary tab, add a delivery address and an invoice address. 
Result:No addresses are created in Dynamics 365 Supply Chain Management and associated with the prospect. 

 > [!NOTE]
    > For addresses created on the account in in Dynamics 365 Sales to synchronize to Dynamics 365 Supply Chain Management, a role must be associated with each address. it is only possible to associate a role when creating an address on an account in Dynamics 365 Sales   when the dual write GAB solution is deployed.
> 

3. In Sales navigate to Customers>Accounts. Select the account type prospect. Change the type to Customer. Select the appropriate Customer group.
Result:The business relation type for the prospect in Dynamics 365 Supply Chain Management is changed from Prospect to Customer, a customer account is created with the same account number as the prospect, irrespective of the number sequence for customer accounts in Dynamics 365 Supply Chain Management. The contact is now associated with the customer account  in Dynamics 365 Supply Chain Management.

If the Dual write GAB solution is deployed, delivery and invoice addresses already synched are associated with the customer account in Dynamics 365 Supply Chain Management. Contact is associated with the customer account.
If the Dual write GAB solution is not deployed, no delivery and invoice addresses associated with the customer account in Dynamics 365 Sales are synchronized and created in Dynamics 365 Supply Chain Management.

 > [!NOTE]
    > If the dual write GAB solution is not deployed then best practice is to create and maintain delivery and invoice addresses for accounts in Dynamics 365 Supply Chain Management.
> 

### Scenario 3: Prospect lifecycle managed from Dynamics 365 Supply Chain Management - prospect of type person (Need to be tested)
The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type person.
1. In Supply Chain Management, navigate to Sales and Marketing>Relationships>Prospects>All prospects. Create New prospect as type person.
Result: The new prospect is created using the number sequence setup for the prospect entity in Dynamics 365 Supply Chain Management. The new prospect is createdas a Contact with the Is Prospect value set to Yes in Dynamics 365 Sales. 

2. Add an address of role Delivery to the prospect. Add an address of role invoice. Create a new contact for the prospect.
Result: A contact is created in Dynamics 365 Sales and associated with the contact with the Is Prospect value set to Yes in Dynamics 365 Sales.

    > [!NOTE]
    > Depending on whether the dual write GAB solution is deployed, either both the delivery address and invoice address is created in Dynamics 365 Sales for the contact with the Is Prospect value set to Yes. Depending on whether the dual write GAB solution is deployed, the  contact surfaces either in Associated organizations tab for the contact or ?? **Does it at all synchronize??**. *** Henrikan: Test at contacts kun synkroniseres dersom contacten er knyttet til en type account (organization) og ikke type contact (type person) *** 
    > 
   
4. In Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships > Prospects > All prospects. Open the prospect and select header ribbon action General > Convert > Convert to customer.
Result:A customer account is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. It cannot be changed in the converting process. Customer group is defaulted into the process from the setup in Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account created in Dynamics 365 Supply Chain Management. The contact in Dynamics 365 Sales is changed from Is Prospect value  Yes to No, and Is Customer value No to Yes.

 > [!NOTE]
    > If the dual write GAB solution is deployed there are no changes to the already created and synchronized delivery address and invoice address and contact. If the dual write GAB solution is not deployed, then the address of type invoice would now be synchronized and created from the newly created customer account in Dynamics 365 Supply Chain Management to the account in Dynamics 365 Sales ?? **Would it??**

### Scenario 4:  Prospect lifecycle managed from Dynamics 365 Sales - prospect of type person (Need to be tested)
The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Sales.
1. In Dynamics 365 Sales, navigate to Customers > Contacts. Create New contact with Is Prospect set to Yes. 
Result:A new business relation type Prospect of type person is created in Dynamics 365 Supply Chain Management with contact Last name as prospect ID, irrespective of number sequence for prospect setup in Dynamics 365 Supply Chain Management.  

2a. If the Dual write GAB solution is deployed, in Dynamics 365 Sales on the contact, on the Addresses tab of the contact, add a new address with the role of delivery, and a new address with the role of invoice. 
Result: An address of role delivery and an address of role invoice is created in Dynamics 365 Supply Chain Management and associated with the prospect. 
2b. If the Dual write GAB solution is not deployed, in Dynamics 365 Sales on the contact, on the Summary tab, add a delivery address and an invoice address. 
Result:No addresses are created in Dynamics 365 Supply Chain Management and associated with the prospect. 

 > [!NOTE]
    > For addresses created on the contact in in Dynamics 365 Sales to synchronize to Dynamics 365 Supply Chain Management, a role must be associated with each address. it is only possible to associate a role when creating an address on an contact in Dynamics 365 Sales when the dual write GAB solution is deployed.
> 

3. In Sales navigate to Customers > Contacts. Find the contact you just created. Change the IS Customer value from No to Yes. Select the appropriate Customer group.
Result:The business relation type for the prospect in Dynamics 365 Supply Chain Management is changed from Prospect to Customer, a customer account is created with the same account number as the contact Last Name, irrespective of the number sequence for customer accounts in Dynamics 365 Supply Chain Management. 

If the Dual write GAB solution is deployed, delivery and invoice addresses already synched are associated with the customer account in Dynamics 365 Supply Chain Management.
If the Dual write GAB solution is not deployed, no delivery and invoice addresses associated with the contact in Dynamics 365 Sales are synchronized and created in Dynamics 365 Supply Chain Management.

 > [!NOTE]
    > If the dual write GAB solution is not deployed then best practice is to create and maintain delivery and invoice addresses for prospects in Dynamics 365 Supply Chain Management.
> 

### Scenario 5:  Use prospect on sales quotation lifecycle from Dynamics 365 Supply Chain Management
1. In Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships>Prospects>All prospects. Create New prospect type organization.
Result: The new prospect is created using the number sequence setup for the prospect entity.
2. In Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Sales Quotations> All quotations. Create New quotation. Select account type Prospect followed by the prospect. Proceed with creating the sales quotation details and add lines. 
Result:The sales quotation is synchronized to Dynamics 365 Sales with the prospect as potential customer on the quotation
3. In Dynamics 365 Supply Chain Management navigate to Sales and Marketing>Sales quotations >All quotations. Select the quotation you just created.Select Header ribbon action Quotation>Generate>Send quotation.
4. Then select Header ribbon action Follow up >Modify>Convert to customer. No dialogue will be presented. 

Result: In Dynamics 365 Supply Chain Management, A customer account is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. Customer group is defaulted into the process from Dynamics 365 Supply Chain Management Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. 
In Dynamics 365 Sales, the account type prospect is automatically changed to type Customer. Account number is unchanged. 

4. In Dynamics 365 Supply Chain Management, from the sales quotation page select header ribbon action Follow up>Generate>Confirm.

Result: A sales order is created in Dynamics 365 Supply Chain Management from the quotation confirmation. The sales order is synchronized to Dynamics 365 Sales. The sales quotation in Dynamics 365 Sales is updated to won.
   
### Scenario 6:  Use prospect on sales quotation lifecycle from Dynamics 365 Sales 
1. In Dynamics 365 Sales, navigate to Customers > Accounts. Create New account type Prospect. A new prospect is created with the account number selected by the user. Create a new contact for the prospect.
Result: A new business relation type Prospect is created in Dynamics 365 Supply Chain Management with same number as in Sales, irrespective of number sequence for prospect setup in Dynamics 365 Supply Chain Management.
A contact is created in Dynamics 365 Supply Chain Management and associated with the prospect. 

2. In Dynamics 365 Sales, navigate to Quotes. Create a new quote, as potential customer select the new account type prospect. Proceed        with creating the sales quotation details and add lines. 
Result: A new sales quotation is syncchronized and created in Dynamics 365 Supply Chain Management for the prospect.

 > [!NOTE]
    > If the dual write GAB solution is deployed then, in Dynamics 365 Sales on the quote, use the address lookup to choose a delivery address. Choose ship to address in the Summary tab, Address section. If the dual write GAB solution is not deployed, there is no address lookup. 

3. In Dynamics 365 Sales "Activate" the quotation. Then select the action "Create order".

Result: In Dynamics 365 Sales, the account type prospect is automatically changed to type customer. In Dynamics 365 Supply Chain Management, a customer account is created from the prospect with the same account number as the prospect irrespective of customer number sequence setup in Dynamics 365 Supply Chain Management. Customer group is defaulted into the process from Dynamics 365 Supply Chain Management Sales and Marketing parameters for prospects. The prospect in Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. The sales quotation in Dynamics 365 Supply Chain Management is processed to confirmed, and the sales order is synched from Dynamics 365 Sales to Dynamics 365 Supply Chain Management.

## Next steps (Update)

- [Enable and configure extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)

