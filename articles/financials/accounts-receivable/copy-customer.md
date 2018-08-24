---
# required metadata

title: Copy a customer to another legal entity and keep the same customer ID using shared number sequences
description: You can copy a customer to another legal entity and keep the same customer ID when a shared number sequence is used
author: mikefalkner
manager: aolson
ms.date: 08/24/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  CustTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Copy a customer using global number sequences

[!include [banner](../includes/banner.md)]

You can use a shared number sequence for assigning customer IDs. In addition, you will be able to copy
a customer from one legal entity to another legal entity and use the same customer ID for both legal entities.  

## Setup

The feature is activated when you use a shared number sequence for assigning customer IDs. You must use the same number sequence in each legal where you want to copy the customer.  Change the customer number sequence to the new number sequence on the parameters page for each legal entity using Accounts receivable > Parameters > Number sequences.

You can also set up customer number sequences for each customer group and these number sequences must also be shared. The number sequences for a customer group will be used first. If there is no number sequence specified for a customer group, then the number sequence found in the parameters form will be used 

You can still use manual customer IDs and copy customers between legal entities. However, if you try to copy a customer to a legal entity where the customer ID already exists, the copy process will not be started.

## Copy a customer

To copy a customer, click on New to display the new customer page. Notice that, unlike previous versions of Dynamics 365 for Finance and Operations, the new customer ID will not be assigned immediately. The customer group has not yet been selected so it is not possible to identify the correct number sequence or use yet. In addition, you may be creating a new customer or you may be copying a customer. Until we know what action will be taken, the customer ID will not be assigned until you click on the Save button at the bottom of the form. 

If you are creating a new customer, you can continue filling in all of the fields as you normally would. When you are done, click on Save and you will see that the customer ID was assigned automatically or, for manual number sequences, your customer ID was used.

To copy a customer, select the Name field and enter one or more characters that represent the customer that you are looking for. The search form will display a list of parties that may represent the customer that you are looking for. When you click on one of the parties, you can see additional information on the right side of the page
1) The General tab shows the party's phone number and address
2) The Role tab shows the roles that the selected party can have and the legal entity in which it has the role
3) Tax registration ID shows the tax registration IDs assigned to the party

You can only copy a party that has a customer role and has that role in a legal entity that is not in the current legal entity. When you find a party that fits this criteria, follow these steps:
1) A Copy customer field is displayed and defaulted to No. 
2) If you want to copy that customer into the current legal entity, change the Copy customer field to Yes. 
3) Another field, Legal entity, is displayed. Select the legal entity from which you want to copy the customer. If the customer only exists in one legal entity, the field will default to that value.
4) Click on Select and the new customer is created

## Validation

When you copy a customer, an attempt is made to save the new customer information. All validations are executed to ensure that the data that was copied is good. If any validations fail, an error message will be display for each validation that did fail, explaining what information needs to be updated. The new customer will not be saved until you have fixed the validation errors. Once they are fixed, you can save the copy of the customer.

**Copying a customer using the tax exempt search**

You can also copy customers using the tax exempt number search found under the Customer > Registration menu. A form will be displayed showing tax exempt numbers, the customer ID, customer name, and legal entity in which the tax exempt ID is used. You can only copy a customer that is in a legal entity that is not in the current legal entity. When you click on a customer that fits this criteria, follow these steps:
1) A Copy customer field is displayed and defaulted to No. 
2) If you want to copy that customer into the current legal entity, change the Copy customer field to Yes. 
3) Click on Select and the new customer is created

