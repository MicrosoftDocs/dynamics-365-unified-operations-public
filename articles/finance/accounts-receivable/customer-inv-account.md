---
title: Customer and invoice accounts
description: This article describes customer and invoice accounts in Dynamics 365 Finance. 
author: twheeloc
ms.date: 02/20/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.form: LedgerTransVoucher, LedgerJournalTable
---

# Customer and invoice accounts

[!include [banner](../includes/banner.md)]

In Dynamics 365 finance and operations, invoices are an essential part of the sales process. It's assumed that the customer who places the order also receives the invoice. There may be situations when the customer to be invoiced is different from the customer placing the order. This article explains the concept of customer accounts and invoice usage. 

## Sales orders fields
 
When creating an order or sales order in Dynamics 365 finance and operations, the **Invoice and delivery** Fast Tab provides the necessary fields to manage the invoicing process. 
 
The **Invoice account** field allows users to select a different customer account to invoice, other than the customer account associated with the order. This is useful when dealing with intermediary parties, such as resellers or distributors, who act as an intermediary between the order customer and the invoicing party. 
 
### Examples
 
 - Same customer account 
In most cases, the customer account selected for invoicing is the same as the customer account associated with the order. This scenario is applicable when the order customer is also responsible for receiving 
the invoice directly. The **Invoice account** field is updated with the order customer's account, eliminating the need for manual selection. 

 - Separate customer account
There are situations when the customer placing the order isn't responsible for receiving the invoice directly. For example, a sales scenario involving a distributor placing an order on behalf of a 
retailer. In such cases, the distributor's account can be selected in the **Invoice account** field. 
 
Some additional considerations: 
 - **Billing address** - When invoicing a different customer account, it is essential to ensure that the correct billing address associated with the invoice recipient is provided.
 - **Financial agreement** - Any financial agreements, such as payment terms or credit limits, should be aligned with the selected invoice account.
 - **Communication** - Clear communication and information exchange between involved parties, including the order customer and invoice recipient, are critical to avoiding any misunderstandings or delays. 
 


