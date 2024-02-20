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

In Dynamics 365 finance and operations, invoices are an essential part of the sales process. It is assumed that the customer who places the order will also receive the invoice. However, there may be situations 
where the customer to be invoiced is different from the customer placing the order. This document aims to explain the concept of customer accounts and invoice usage in such scenarios. 
 
## Invoice and Delivery Fast Tab: 
 
When creating an order or sales order in Dynamics 365 finance and operations, the user can navigate to the "Invoice and Delivery" fast tab. This tab provides the necessary fields to manage the invoicing process, 
including the "Invoice account" field. 
 
## Customer Account for Invoicing: 
 
The "Invoice account" field allows users to select a different customer account to invoice, other than the customer account associated with the order. This feature is particularly useful when dealing with 
intermediary parties, such as resellers or distributors, who act as an intermediary between the order customer and the invoicing party. 
 
### Example
 
•	Same Customer Account: 
 
In most cases, the customer account selected for invoicing will be the same as the customer account associated with the order. This scenario is applicable when the order customer is also responsible for receiving 
the invoice directly. The system will automatically populate the "Invoice account" field with the order customer's account, eliminating the need for manual selection. 
 
  
•	Separate Customer Account: - 
 
There are situations where the customer placing the order is not responsible for receiving the invoice directly. For example, consider a sales scenario involving a distributor placing an order on behalf of a 
retailer. In such cases, the distributor's account may be selected in the "Invoice account" field, as they will handle the invoicing process. 
 
•	Additional Considerations: 
 
a)	Billing Address: When invoicing a different customer account, it is essential to ensure that the correct billing address associated with the invoice recipient is provided. 
b)	Financial Agreement: Any financial agreements, such as payment terms or credit limits, should be aligned with the selected invoice account. 
c)	Communication: Clear communication and information exchange between involved parties, including the order customer and invoice recipient, are critical to avoiding any misunderstandings or delays. 
 
The Dynamics 365 F&O platform provides flexibility in managing invoice recipients through the "Invoice account" field. Whether the same or separate customer account is selected depends on the specific sales 
scenario and the roles played by intermediary parties. By understanding these dynamics and utilizing the appropriate customer account and invoice setup, businesses can streamline their invoicing process 
effectively.  
 

