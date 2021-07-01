---
# required metadata

title: Prepaymants in Retail for Russia
description: This topic provides an overview of processing prepayment transactions in Microsoft Dynamics 365 Commerce for Russia.
author: 67962652+akviklis
ms.date: 06/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 2021-6-28
ms.dyn365.ops.version: 10.0.21

---
# Prepayments in Retail for Russia

[!include[banner](../includes/banner.md)]

This topic describes how Microsoft Dynamics 365 Commerce processes prepayment transactions for the following payment types in Rusian Retail:

- **Customer account deposit payment** – A customer makes a prepayment at the Retail point of sale (POS). Microsoft Dynamics 365 Commerce processes the deposit payment as a prepayment transaction. When you post the transaction, a payment journal is posted in the Journal voucher form. The Prepayment journal voucher check box on the Payment tab in the Journal voucher form is automatically selected for the payment journal. For more information see [Prepayments management](../../finance/localizations/rus-prepayments-management.md).

- **Customer order with deposit** – A customer provides a customer order at the Retail POS. The customer can deposit a payment for the order based on the parameters that you have set up in the Retail parameters form. Microsoft Dynamics 365 Commerce processes the deposit payment for the customer order as a prepayment transaction. When you post the transaction, a customer payment journal is created and posted in the Journal voucher form. The Prepayment journal voucher check box on the Payment tab in the Journal voucher form is automatically selected for the payment journal. The payment is settled and the customer invoice is issued automatically when the order is picked up or delivered.

Microsoft Dynamics 365 Commerce for Russia performs the following tasks to process a prepayment:

- **Processes a customer account deposit payment** – The payment that the customer deposits, is transferred to Microsoft Dynamics 365 Commerce using a service that synchronizes data. Microsoft Dynamics 365 Commerce creates a retail payment transaction for the payment. When you post the retail transaction, a cash journal or customer payment journal is posted. The Prepayment journal voucher check box on the Payment tab in the Journal voucher form is automatically selected for the payment journal. You cannot process the prepayments if the payment amount is negative.

- **Processes a customer order with a deposit** – The customer makes a required deposit for a customer order using the Real-time service. Whether Microsoft Dynamics 365 Commerce creates a customer payment journal or a cash journal depends on the method of payment that the customer uses. The Prepayment journal voucher check box on the Payment tab in the Journal voucher form is automatically selected for the journal. If the customer makes partial payments by using multiple methods of payment, Microsoft Dynamics 365 Commerce processes each partial payment by using the method of payment for that partial payment.

When you cancel a customer order, the prepayment amount is refunded and a refund payment journal is posted for the deposit amount. The refund amount is calculated and posted based on the method of payment that you specify when you post the refund payment. Microsoft Dynamics 365 Commerce may apply a cancellation charge based on the parameters that you set in the Retail parameters form. For more information about the fields in the form, see Retail parameters (form).

When you return a customer order, a return order and a refund payment journal are created. When you post the return order, Microsoft Dynamics 365 Commerce creates a customer payment journal or a cash journal. The type of journal that is created depends on the method of payment that is used by the customer for the original transaction.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
