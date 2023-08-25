---
title: Prepayments in Dynamics 365 Commerce for Russia
description: This article provides an overview of processing for prepayment transactions in Microsoft Dynamics 365 Commerce for Russia.
author: EvgenyPopovMBS
ms.date: 08/02/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Russia
ms.author: josaw
ms.search.validFrom: 2021-06-28
ms.dyn365.ops.version: 10.0.21
ms.search.industry: Retail
---
# Prepayments in Dynamics 365 Commerce for Russia

[!include[banner](../includes/banner.md)]

This article provides an overview of processing for prepayment transactions in Microsoft Dynamics 365 Commerce for Russia.

Dynamics 365 Commerce processes prepayment transactions for the following payment types that are used in Russian retail:

- **Customer account deposit payment** – A customer makes a prepayment at the point of sale (POS), and Commerce processes the deposit payment as a prepayment transaction. When you post the transaction, a payment journal is created and posted on the **Journal voucher** page. The **Prepayment journal voucher** checkbox on the **Payment** tab is automatically selected for the payment journal. For more information, see [Prepayments management](../../finance/localizations/rus-prepayments-management.md).
- **Customer order with deposit** – A customer creates a customer order at the POS. The customer can deposit a payment for the order, based on the default deposit percentage that is configured on the **Commerce parameters** page. Commerce processes the deposit payment for the customer order as a prepayment transaction. When you post the transaction, a payment journal is created and posted on the **Journal voucher** page. The **Prepayment journal voucher** checkbox on the **Payment** tab is automatically selected for the payment journal. The payment is settled, and the customer invoice is automatically issued when the order is picked up or delivered.

Commerce for Russia performs the following tasks to process a prepayment:

- **Process a customer account deposit payment** – A payment that a customer deposits is transferred to Commerce by using a service that synchronizes data. Commerce creates a retail payment transaction for the payment. When you post the retail transaction, a cash journal or customer payment journal is posted. The **Prepayment journal voucher** checkbox on the **Payment** tab of the **Journal voucher** page is automatically selected for the payment journal. Prepayments can't be processed if the payment amount is negative.
- **Process a customer order that has a deposit** – A customer makes a required deposit for a customer order by using Commerce Data Exchange: Real-time Service. Commerce creates either a customer payment journal or a cash journal, depending on the method of payment that the customer uses. The **Prepayment journal voucher** checkbox on the **Payment** tab of the **Journal voucher** page is automatically selected for the journal. If a customer uses multiple methods of payment to make partial payments, Commerce processes each partial payment, based on the method of payment that was used for it.

When you cancel a customer order, the prepayment amount is refunded, and a refund payment journal is posted for the deposit amount. The refund amount is calculated and posted, based on the method of payment that you specified when you posted the refund payment. Commerce might apply a cancellation charge, based on the percentage that you set on the **Commerce parameters** page.

When you return a customer order, a return order and a refund payment journal are created. When you post the return order, Commerce creates either a customer payment journal or a cash journal, depending on the method of payment that the customer used for the original transaction.

## Additional resources

[Commerce home page](../welcome.md)

[Russian localization scope](../../finance/localizations/russia.md)

[Prepayments management](../../finance/localizations/rus-prepayments-management.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
