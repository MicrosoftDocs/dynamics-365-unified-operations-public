---
# required metadata

title: Edit & audit retail store transactions
description: This topic describes the edit & audit retail store transactions functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 09/29/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-09-29
ms.dyn365.ops.version: 

---
# Edit & audit retail store transactions

Dynamics 365 for Retail customers use first party as well as third party POS applications. In the case of first party POS application, retail store transactions are pulled into the HQ from the channels through a batch process and in the case of third party applications, these are pulled into the HQ through integration. After these transactions are pulled into the HQ, there is a consistency check process that needs to be executed that runs multiple validations on these transactions and only successfully validated retail transactions are pulled into the Retail statement to be posted in the HQ. 
It has been observed across multiple customers that many of their retail transactions fail validation for varied reasons like bug in the integration code, bug in the POS application etc. that causes inconsistent data, in addition to user error creating inconsistent data like deleting a product after they have synchronized to the channel, closing a fiscal period without posting retail transactions for that period etc.
While these transactions get flagged and are excluded from the Retail statements, it does create lot of disruption to the customer’s daily process to post daily retail sales to the financials especially given the fact that there is no tool or mechanism available to the customer to fix these inconsistent data on their own. Fixing of these transactions required the customer to log a support ticket with Microsoft which is not empowering enough to the customers.  
As such, this feature was introduced in the product that empowers a customer to edit the retail transactions that fails validation while maintaining audit of all the changes. 

The following set of capabilities was introduced as a part of this feature:

1. To use this feature, the Dynamics Excel Add-in has to be installed & configured on the user’s machine

2. A new tile has been introduced on the **Retail store financials** workspace called **Transaction validation failures** which provides a pre-filtered view of the Retail transaction form that failed one or more of the validation rules.
 
3. On the Retail transaction form, for the record that failed validation, the user can modify the concerned record by clicking on the record and clicking on the **Office Add in** button and clicking on the option **Edit selected transaction**. This will open up an Excel file with the details of the selected transaction in multiple excel worksheet as per below:

    1. Lines: This has the header and product lines related data for the transaction
    2. Payments: This has the details of the payment lines for the transaction
    3. Discounts: This has the discount related details for the transaction
    4. Taxes: This has the tax related details for the transaction
    5. Charges: This has the charges related data for the transaction

  In the Excel worksheet, the user can modify the required fields and upload it back into the system using the standard Dynamics Excel Add in publish capability.

4)	Once published, the changes made by the user are reflected in the system. During the publishing process, no validation is performed on the changes made by the user.

5)	The system maintains a complete audit trail of the change made by the user and the same can be viewed using the **View audit trail** button in the **Retail transaction** header form for the header level changes and in the relevant section and record under the **Transactions** form. For e.g.; all sales line related changes will be visible under the **Sales transactions** form under the **Transaction** button, payment related changes will be visible under the **Payment transactions** form under the **Transaction** button and so on. The details of the audit that are maintained for the changes are as below:

    1. Modified date and time
    2. Field 
    3. Old value
    4. New value
    5. Modified by


6)	After changes are made and published for retail transactions, the **Validate store transactions** option has to be run again to validate that the changes made are all consistent & as per expectations.

7)	By default, the system would only allow to edit the retail transactions that has failed validation. If customers wants to edit records that has passed validation, they can flip the status of the validation status of the transaction to **Error** using the same Excel Add in option. This would allow the transaction to be edited. 

8)	To bulk edit retail transactions, the Excel Add-in option 

9)	As of the version 10.0.6, only cash & carry transactions like sales, returns etc. and cash mgmt. transactions like Declare start amount, Tender declaration, Safe drop, etc. can be edited using this feature. Editing of Customer order or Online order is not supported. 
