---
title: Specify the cross rate
description: Learn about cross rates in Microsoft Dynamics 365 Finance, including a step-by-step process outlining how to specify cross rates. 
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/16/2018
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Specify the cross rate

[!include [banner](../includes/banner.md)]

This article explains the purpose of a cross rate, and how to specify the cross rate when you settle a payment with an invoice. Use a cross rate when the following criteria apply: 
-	You are settling a payment with an invoice. 
-	The payment line and the invoice line use different currencies. 
-	Neither currency is the accounting currency. 

The cross rate is not used to calculate the payment transaction currency translation to the payment accounting currency. Instead, the exchange rates from the exchange rate tables are retrieved to calculate the value of the payment transaction currency amount and the payment accounting currency amount. 

For example, the accounting currency is USD, the invoice currency is CAD, and the payment currency is EUR. The cross rate lets you enter an exchange rate to translate directly between CAD and EUR, and not have to translate through USD. 
When you select an invoice and a primary payment, you can enter a cross rate for the invoice line. The cross rate is the exchange rate between the currencies for those transactions, as of the settlement date.

1.	Go to one of the following pages:
- **Accounts receivable > Common > Customers > All customers** 
- **Accounts payable > Common > Vendors > All vendors** 
- **Procurement and sourcing > Common > Vendors > All vendors**
2.	Select the customer or vendor whose open transactions you are settling. 
3.	For a customer, on the **All customers** list page, go to **Collect > Settle open transactions**. For a vendor, on the **All vendors** list page, go to **Invoice > Settle open transactions**. 
4.	Select the transaction that is the primary payment, and then click **Mark payment**. The check box in the **Mark** column is selected, and an information icon is shown in the **Primary payment** column. 
5.	In the **Cross rate** field, enter the exchange rate between the invoice currency and the payment currency, as of the settlement date. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
