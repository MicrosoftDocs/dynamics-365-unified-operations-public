---
title: Prepayments in Dynamics 365 Commerce
description: This article provides an overview of processing for prepayment transactions in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 11/11/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2021-06-28

---
# Prepayments in Dynamics 365 Commerce

[!include[banner](../includes/banner.md)]

This article provides an overview of processing for prepayment transactions in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce processes prepayment transactions for the following payment types that are used in accounts receivable or Commerce:

- **Customer account deposit payment** – A customer makes a prepayment at the point of sale (POS), and Commerce processes the deposit payment as a prepayment transaction. When you post the transaction, a payment journal is created and posted on the **Journal voucher** page in Commerce headquarters. The **Prepayment journal voucher** checkbox on the **Payment** tab is automatically selected for the payment journal. For more information, including relevant prepayment and tax-specific information based on the target region, see [Globalization resources - Country/region specific help content](/dynamics365/fin-ops-core/dev-itpro/lcs-solutions/country-region?context=%2Fdynamics365%2Fcontext%2Ffinance#countryregion-specific-help-content).
- **Customer order with deposit** – A customer creates a customer order at the POS. The customer can deposit a payment for the order, based on the default deposit percentage that is configured in headquarters on the **Commerce parameters \> Customer orders** page. Commerce processes the deposit payment for the customer order as a prepayment transaction. When you post the transaction, a payment journal is created and posted on the **Journal voucher** page. The **Prepayment journal voucher** checkbox on the **Payment** tab is automatically selected for the payment journal. The payment is settled, and the customer invoice is automatically issued when the order is picked up or delivered.
- **Call center sales order** - A call center customer service representative creates a sales order on behalf of a customer and the **prepayment** attribute is set to **Yes** during the payment capture.

Commerce performs the following tasks to process a prepayment:

- **Process a customer account deposit payment** – A payment that a customer deposits is transferred to Commerce using a service that synchronizes data, and Commerce creates a retail payment transaction for the payment. When you post the retail transaction, a cash journal or customer payment journal is posted. The **Prepayment journal voucher** checkbox on the **Payment** tab of the **Journal voucher** page in headquarters is automatically selected for the payment journal. Prepayments can't be processed if the payment amount is negative.
- **Process a customer order or sales order that has a deposit** – A customer makes a required deposit for a customer order by using the Commerce Data Exchange: Real-time Service. Commerce creates either a customer payment journal or a cash journal, depending on the method of payment that the customer uses. The **Prepayment journal voucher** checkbox on the **Payment** tab of the **Journal voucher** page is automatically selected for the journal in headquarters. If a customer uses multiple methods of payment to make partial payments, Commerce processes each partial payment, based on the method of payment that was used.

For credit card and digital wallets with underlying credit card payment methods, Commerce sends a "capture" request after authorization success (capturing funds prior to invoicing the sales order).

When you cancel a customer order, the prepayment amount is refunded, and a refund payment journal is posted for the deposit amount. The refund amount is calculated and posted, based on the method of payment that you specified when you posted the refund payment. Commerce may apply a cancellation charge, based on the percentage that you set on the **Commerce parameters** page in headquarters.

When you return a customer order, a return order and a refund payment journal are created. When you post the return order, Commerce creates either a customer payment journal or a cash journal, depending on the method of payment that the customer used for the original transaction.

