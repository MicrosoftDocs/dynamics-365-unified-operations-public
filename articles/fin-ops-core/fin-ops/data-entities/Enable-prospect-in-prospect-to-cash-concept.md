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

# Enable prospect in prospect-to-cash with Microsoft Dynamics 365 Sales

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.39 and later, this capability has been improved to integrate accounts of type prospect seamlessly in the quotation and qualification process across the two systems. 

The changes are introduced to allow companies to have a seamless prospect lifecycle integration and quotation process flow across Sales and Supply Chain Management allowing for fewer touch points and higher efficiency and transparency. The changes are enabled in a combination of a feature in feature management in Supply Chain Management and an updated dual write supply chain solution to support the prospect lifecycle integration with Sales. These changes are an extension to the sales quotation lifecycle integration generally available from Microsoft Dynamics Supply Chain Management version 10.0.34. 

These changes are intended to be used only in the context of prospect-to-cash integration between Microsoft Dynamics 365 Sales and Microsoft Dynamics 365 Supply Chain Management.

## Enable prospect in prospect-to-cash with Microsoft Dynamics 365 Sales
In order to leverage prospect integration **

## Definition of a prospect in prospect-to-cash with Dynamics 365 Sales
A prospect in Microsoft Dynamics 365 Sales is an account of type Prospect. From an integration perspective, a lead in neither Microsoft Dynamics 365 Sales nor in Microsoft Dynamics 365 Supply Chain management is considered a prospect. A prospect in Microsoft Dynamics 365 Supply Chain Management is a business relation with the business relation type Prospect, while a prospect inMicrosoft Dynamics 365 Sales is an account of type prospect. The feature _Enable prospect in sales quotation lifecycle with Dynamics 365 Sales_ covers the lifecycle integration of Microsoft Dynamics 365 Sales account type Prospect and Microsoft Dynamics 365 SCM business relation, business relation type Prospect.

When **Integrate quotation lifecycles** feature is enabled [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md) it is possible to enable the **Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales** feature in feature management. When the **Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales** feature is enabled and turned on in Accounts Receivables parameters, then prospect integration between the two systems is supported. 

## Basic integration design assumption - Number sequences 
The integration design of prospects between Microsoft Dynamics 365 Sales and Microsoft Dynamics 365 Supply Chain Management **requires** that prospect account numbers are the same in Dynamics 365 Sales and Dynamics 365 Supply Chain Management. To support this design, it is **required** that number sequences for prospect and the number sequence for customer account in Microsoft Dynamics 365 Supply Chain management do not overlap. If number sequences overlap, conflicts can occur when converting a prospect to a customer account dissallowing the prospect to be converted to a customer.

## Scenarios
The following section provides common scenarioes enabled by **Enable prospects in Sales quotation lifecycle with Dynamics 365 Sales**.

### Scenario 1: Prospect lifecycle managed from Microsoft Dynamics 365 Supply Chain Management - prospect of type organization
The following steps show what happens when you manage prospect lifecycle from Microsoft Dynamics 365 Supply Chain Management and the prospect is of type organization.
1. In Supply Chain Management, navigate to Sales and Marketing>Relationships>Prospects>All prospects. Create New prospect as type organization.
Result: The new prospect is created using the number sequence setup for the prospect entity in Microsoft Dynamics 365 Supply Chain Management. A new account of _relationship type_ Prospect is created in Microsoft Dynamics 365 Sales with same account number as in Microsoft Dynamics 365 Supply Chain Management.

2. Add an address of role delivery to the prospect. Add an address of role invoice. Create a new contact for the prospect.
Result: A contact is created in Microsoft Dynamics 365 Sales and associated with the account type Prospect.

    > [!NOTE]
    > Depending on whether the dual write GAB solution is deployed, either both the delivery address and invoice address is created in Microsoft Dynamics 365 Sales for the new account, or only the delivery address. Depending on whether the dual write GAB solution is deployed, the contact surfaces either in the Associated contacts tab for the account or on the Account page, Summary tab in the primary contact section in Microsoft Dynamics 365 Sales. 
    > 
   
4. In Microsoft Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships > Prospects > All prospects. Open the prospect and select header ribbon action General > Convert > Convert to customer.
Result:A customer account is created in Microsoft Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Microsoft Dynamics 365 Supply Chain Management. It is intentional that it cannot be changed in the converting process. Customer group is defaulted into the process from the setup in Sales and Marketing parameters for prospects. The prospect in Microsoft Dynamics 365 Supply Chain Management is retired and the _relationship type_ is changed from Prospect to Customer. Addresses and contacts in Microsoft Dynamics 365 Supply Chain Management are related to the new customer account created. The account of _relationship type_ Prospect in Microsoft Dynamics 365 Sales is changed to account _relationship type_ customer.

 > [!NOTE]
    > If the dual write GAB solution is deployed, then there are no changes to the already created and synchronized delivery and invoice addresses and contact. If the dual write GAB solution is not deployed, then the address of type invoice is synchronized from the newly created customer account in Microsoft Dynamics 365 Supply Chain Management to the account in Microsoft Dynamics 365 Sales. 

### Scenario 2: Prospect lifecycle managed from Dynamics 365 Sales - Prospect as account

The following steps show what happens when you manage prospect lifecycle from Microsoft Dynamics 365 Sales.
1. In Microsoft Dynamics 365 Sales, navigate to Customers > Accounts. Create New account _relationship type_ Prospect. A new prospect is created with the account number selected by the user. Create a new contact for the prospect.
Result: A new business relation type Prospect (of type organization) is created in Microsoft Dynamics 365 Supply Chain Management with same number as in Microsoft Dynamics 365 Sales, irrespective of number sequence for prospect setup in Microsoft Dynamics 365 Supply Chain Management. A contact is created in Microsoft Dynamics 365 Supply Chain Management and associated with the prospect. 

2a. If the Dual write GAB solution is deployed, in Microsoft Dynamics 365 Sales on the account, on the Addresses tab of the account, add a new address with the role of delivery, and a new address with the role of invoice. 
Result: An address of role delivery and an address of role invoice is created in Microsoft Dynamics 365 Supply Chain Management and associated with the prospect. 
2b. If the Dual write GAB solution is not deployed, in Microsoft Dynamics 365 Sales on the account, on the Summary tab, add a delivery address and an invoice address. 
Result: It is intentional that no addresses are created in Microsoft Dynamics 365 Supply Chain Management and associated with the prospect. 

**Delete Bug in the solution - _Cannot save the changes to the database. Unit of Work can not commit transaction.
Unable to write data to entity msdyn_postaladdresses.Unable to lookup msdyn_postaladdresscollections with values {LOC-000001004}.Writes to msdyn_postaladdresses failed with error message Exception message: One or more errors occurred..For information on troubleshooting see https://go.microsoft.com/fwlink/?linkid=2244045..Unable to lookup msdyn_postaladdresscollections with values {LOC-000001004}.Writes to msdyn_postaladdresses failed with error message For information on troubleshooting see https://go.microsoft.com/fwlink/?linkid=2244045.._**

 > [!NOTE]
    > For addresses created on the account in Microsoft Dynamics 365 Sales to synchronize to Microsoft Dynamics 365 Supply Chain Management, a role must be associated with each address. It is only possible to associate a role when creating an address on an account in Microsoft Dynamics 365 Sales when the dual write GAB solution is deployed.
> 

3. In Microsoft Dynamics 365 Sales navigate to Customers>Accounts. Select the account _relationship type_ prospect. Change the  _relationship type_ to Customer. Select the appropriate Customer group.
Result:The business relation type for the prospect in Microsoft Dynamics 365 Supply Chain Management is changed from Prospect to Customer. A customer account is created with the same account number as the prospect, irrespective of the number sequence for customer accounts in Microsoft Dynamics 365 Supply Chain Management. The contact is associated with the customer account in Microsoft Dynamics 365 Supply Chain Management.

 > [!NOTE]
    > If the Dual write GAB solution is deployed, then delivery and invoice addresses already synchronized are associated with the customer account in Microsoft Dynamics 365 Supply Chain Management. The contact is associated with the customer account. If the Dual write GAB solution is not deployed, then no delivery and invoice addresses are synchronized and created in Microsoft Dynamics 365 Supply Chain Management for the customer account.
> 

 > [!NOTE]
    > If the dual write GAB solution is not deployed, then best practice is to create and maintain delivery and invoice addresses for customers and prospects in Microsoft Dynamics 365 Supply Chain Management.
> 

### Scenario 3: Prospect lifecycle managed from Microsoft Dynamics 365 Supply Chain Management - Prospect of type person
The following steps show what happens when you manage prospect lifecycle from Dynamics 365 Supply Chain Management and the prospect is of type person.
1. In Microsoft Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships>Prospects>All prospects. Create a new prospect of type person.
Result: The new prospect is created using the number sequence setup for the prospect entity in Microsoft Dynamics 365 Supply Chain Management. The new prospect is created as a contact with the _Is Prospect_ value set to Yes in Microsoft Dynamics 365 Sales. 

2. Add an address of role delivery to the prospect. Add an address of role invoice. Create a new contact for the prospect.

    > [!NOTE]
    > Depending on whether the dual write GAB solution is deployed, either both the delivery and invoice addresses or only the delivery address are created in Microsoft Dynamics 365 Sales for the contact with the Is Prospect value set to Yes. If dual write GAB solution is deployed, then the contact is associated to the prospect represented by the contact _IS Prospect_ Yes via the party relation. The contact can be accessed in the _Contacts for Party_ tab for the contact in Microsoft Dynamics 365 Sales. 
        > 
   
3. In Microsoft Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships > Prospects > All prospects. Open the prospect and select header ribbon action General > Convert > Convert to customer.
Result: A customer account of type person is created in Microsoft Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Microsoft Dynamics 365 Supply Chain Management. It is intentional that it cannot be changed in the converting process. Customer group is defaulted into the process from the setup in Sales and Marketing parameters for prospects. The prospect in Microsoft Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. Addresses and contacts in Dynamics 365 Supply Chain Management are related to the new customer account created in Microsoft Dynamics 365 Supply Chain Management. The contact in Dynamics 365 Sales is changed from _Is Prospect_ value Yes to No, and _Is Customer_ value No to Yes. The contact associated with the contact _IS Customer _ Yes, can now be accessed from the _Associated Contacts_ tab.

### Scenario 4:  Prospect lifecycle managed from Microsoft Dynamics 365 Sales - Prospect of type person
The following steps show what happens when you manage prospect lifecycle from Microsoft Dynamics 365 Sales.
1. In Microsoft Dynamics 365 Sales, navigate to Customers > Contacts. Create new contact with _Is Prospect _set to Yes. Create a new contact from the _Contacts for Party_ tab.
Result:A new business relation type prospect (of type person) is created in Microsoft Dynamics 365 Supply Chain Management with contact Last name as prospect ID irrespective of number sequence for prospect setup in Microsoft Dynamics 365 Supply Chain Management.  

2a. If the Dual write GAB solution is deployed, in Microsoft Dynamics 365 Sales on the contact, on the Addresses tab of the contact, add a new address with the role of delivery and a new address with the role of invoice. 
Result: An address of role delivery and an address of role invoice is created in Microsoft Dynamics 365 Supply Chain Management and associated with the prospect. 
2b. If the Dual write GAB solution is not deployed, in Microsoft Dynamics 365 Sales on the contact, on the Summary tab, add a delivery address and an invoice address. 
Result: No addresses are created in Microsoft Dynamics 365 Supply Chain Management and associated with the prospect. This is intentional.

 > [!NOTE]
    > For addresses created on the contact in Microsoft Dynamics 365 Sales to synchronize to Microsoft Dynamics 365 Supply Chain Management, a role must be associated with each address. it is only possible to associate a role when creating an address on an contact in Dynamics 365 Sales when the dual write GAB solution is deployed.
> 

3. In  Microsoft Dynamics 365 Sales navigate to Customers > Contacts. Find the contact you just created. Change the _IS Customer_ value from No to Yes. Select the appropriate Customer group.
Result: The business relation type for the prospect in Microsoft Dynamics 365 Supply Chain Management is changed from Prospect to Customer. A customer account is created in with the same account number as prospect, irrespective of the number sequence for customer accounts in Microsoft Dynamics 365 Supply Chain Management. 

> [!NOTE]
    > If the Dual write GAB solution is deployed, delivery and invoice addresses already synched are associated with the customer account in Microsoft Dynamics 365 Supply Chain Management. If the Dual write GAB solution is not deployed, no delivery and invoice addresses associated with the contact in Microsoft Dynamics 365 Sales are synchronized and created in Microsoft Dynamics 365 Supply Chain Management.
> 

 > [!NOTE]
    > If the dual write GAB solution is not deployed, then best practice is to create and maintain delivery and invoice addresses for prospects in Microsoft Dynamics 365 Supply Chain Management.
> 

### Scenario 5:  Use prospect on sales quotation lifecycle from Microsoft Dynamics 365 Supply Chain Management
1. In Microsoft Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Relationships>Prospects>All prospects. Create New prospect of type organization
2. In Microsoft Dynamics 365 Supply Chain Management, navigate to Sales and Marketing>Sales Quotations> All quotations. Create New quotation. Select account type Prospect and selct the prospect. Proceed with creating the sales quotation details and add lines. 
3. In Dynamics 365 Supply Chain Management navigate to Sales and Marketing>Sales quotations >All quotations. Select the quotation you just created. Select Header ribbon action Quotation>Generate>Send quotation.
4. Then select Header ribbon action Follow up >Modify>Convert to customer. It is intentional, that no dialogue is thrown in the UI.

Result: In Microisoft Dynamics 365 Supply Chain Management, A customer account is created in Dynamics 365 Supply Chain Management from the prospect. Customer account number is the same as prospect irrespective of customer number sequence setup in Microsoft Dynamics 365 Supply Chain Management. Customer group is defaulted into the process from Microsoft Dynamics 365 Supply Chain Management Sales and Marketing parameters for prospects. The prospect in Microsoft Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. In Microsoft Dynamics 365 Sales, the account type prospect is changed to type Customer. 

5. In Microsoft Dynamics 365 Supply Chain Management, from the sales quotation page select header ribbon action Follow up>Generate>Confirm.

Result: A sales order is created in Microsoft Dynamics 365 Supply Chain Management from the quotation confirmation. The sales order is synchronized to Microsoft Dynamics 365 Sales. The sales quotation in Microsoft Dynamics 365 Sales is updated to won.
   
### Scenario 6:  Use prospect on sales quotation lifecycle from Microsoft Dynamics 365 Sales 
1. In Microsoft Dynamics 365 Sales, navigate to Customers > Accounts. Create New account type Prospect. A new prospect is created with the account number selected by the user.
2. In Microsoft Dynamics 365 Sales, navigate to Quotes. Create a new quote, select the new account type prospect as potential customer. Proceed with creating the sales quotation details and add lines. 

 > [!NOTE]
    > If the dual write GAB solution is deployed then, in Dynamics 365 Sales on the quote, use the address lookup to choose a delivery address by choosing ship to address in the Summary tab, Address section. If the dual write GAB solution is not deployed, there is no address lookup. 

3. In Microsoft Dynamics 365 Sales _Activate_ the quote. Then select the action _Create order_.

Result: In Microsoft Dynamics 365 Sales, the account type prospect is changed to type customer. In Microsoft Dynamics 365 Supply Chain Management, a customer account is created from the prospect with the same account number as the prospect, irrespective of customer number sequence setup in Microsoft Dynamics 365 Supply Chain Management. Customer group is defaulted into the process from Dynamics 365 Supply Chain Management Sales and Marketing parameters for prospects. The prospect in Microsoft Dynamics 365 Supply Chain Management is retired and the type is changed from Prospect to Customer. The sales quotation in Microsoft Dynamics 365 Supply Chain Management is processed to confirmed, and the sales order is synchronized from Microsoft Dynamics 365 Sales and created in Microsoft Dynamics 365 Supply Chain Management.


## Next steps (Update)

- [Enable and configure prospect integration in prospect-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)

