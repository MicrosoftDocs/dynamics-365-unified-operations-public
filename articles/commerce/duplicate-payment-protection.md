---
# required metadata

title: Duplicate payments prevention
description: This topic describes how Dynamics 365 Commerce helps to prevent duplicate payments in the Modern POS.
author: rubendel
manager: AnnBe
ms.date: 01/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2018-11-01
ms.dyn365.ops.version: AX 7.0.1

---

# Duplicate payments prevention

[!include [banner](includes/banner.md)]

This topic provides an overview of the duplicate payments protection feature for Dynamics 365 Commerce Modern POS.

## Overview

This topic describes the user experience when the point of sale (POS) recovers from a loss of communication with the payment terminal, which causes the POS and the payment terminal to be out of sync.

The duplicate payment protection feature ensures that Modern POS can seamlessly recover from a loss of communication without requiring the shopper to process another payment through the payment terminal, which can lead to duplicate payments.

This topic covers the following aspects of the duplicate payment protection feature:

- [Prerequisites](#prerequisites) – Set of prerequisites to leverage this feature in Modern POS.
- [Scenario details](#scenario-details) – Detailed description of the scenarios covered by the duplicate payment protection feature.
- [Troubleshooting](#troubleshooting) – Steps to take when encountering issues with the duplicate payment protection feature.
- [Additional resources](#additional-resources) – List of related articles you might find useful when using the duplicate payment protection feature.

## Prerequisites

- The payment connector and corresponding payment gateway or processor must support this feature. The *payment connector* is an extension which facilitates communication between Commerce (and associated components) and a payment service. The connector described in this topic was implemented using the standard payments SDK.
- If a connector implements the corresponding duplicate payment protection interfaces, the feature is automatically enabled in Modern POS. Otherwise, it is automatically turned off.

<!---
The [Implement Duplicate Payment Protection](TODO) article describes in detail how to implement support for the duplicate payment protection feature for a given payment connector.
The [Dynamics 365 Payment Connector for Adyen](TODO) has built in support for the duplicate payment protection feature.
-->

## Scenario details

The duplicate payment protection feature is applicable to any scenario in which a payment is initiated and completed on a payment terminal, but Modern POS is unable to receive the corresponding response. As a result, the customer's card (such as a credit card) is charged but the payment line is not added to the POS. In most cases, the cashier will trigger a subsequent payment on the payment terminal, which results in a duplicate payment for the customer.

### How duplicate payments scenarios are triggered

1. **Cashier initiates payment**

    The cashier initiates a card payment by clicking **Pay card**, navigates to the **Payment** page, and clicks **Tender**.

2. **Customer interacts with payment terminal**

    After the payment is initiated, the payment terminal prompts the customer for payment. The customer initiates the payment process on the payment terminal. 

3. **Modern POS loses connectivity to the payment terminal**

    - While the customer is running a payment on the payment terminal, Modern POS loses connectivity to the payment terminal because it either crashes, loses network connectivity, is closed, or the terminal is rebooted.
    - The cashier will re-launch Modern POS and address any connectivity issues.

4. **Customer completes payment on the payment terminal**

    As Modern POS is being reset, the customer completes the payment on the payment terminal and is charged.

5. **Modern POS is launched**

    The cashier completes the reset/launch of Modern POS but the payment is not added to the cart.

### Payment recovery scenarios

Once the point of sale or network communications have been recovered, there are several scenarios that will result in the cashier being prompted to use the previous payment. Here are a few scenarios that can trigger payment recovery:

If there is a unrecovered payment and the cashier takes one of the following actions, the cashier is shown a dialog box indicating that a payment has already been made.

- Invokes another payment for any amount using a card payment.
- Invokes another payment for any amount using a cash payment.
- Attempts to void a line on the cart.
- Attempts to void the transaction.
- Attempts to suspend the transaction.

![Recover Payment](media/Payments/Duplicate-Payment-Protection/Recover-Payment.png)

When the cashier clicks **OK**, the payment is recovered and added as a payment line to the cart.

The primary function of the duplicate payment protection feature is to put Modern POS back into the same state it would be if the original payment would have been successfully processed and the corresponding payment line was added to the cart.

### How to skip payment recovery

In some cases, the cashier might explicitly choose to skip the duplicate payment protection and opt not to recover a previous payment. In those cases, the cashier can use the following steps described to void the transaction without recovering the payment.

1. **Re-launch Modern POS**

    After Modern POS has lost connectivity to the payment terminal, re-launch the POS.

2. **Void the transaction**

    Navigate to the cart page and click **Void Transaction**.

3. **Ignore the recovered payment**

    A new dialog box will appear indicating that a recovered payment is available. Click **Ignore** to skip the payment recovery.

![Skip Payment Recovery](media/Payments/Duplicate-Payment-Protection/Void-Transaction.png)

### What to do if the customer leaves the store

In some cases, the customer might leave the store before the cashier can finalize the transaction. In those cases, follow the steps described in the [How to skip payment recovery](#how-to-skip-payment-recovery) section to void the transaction and manually void the payment on the portal of the payment gateway/processor.

## Troubleshooting

### General issues

For all general issues, you should always consult the Modern POS or IIS Hardware Station event logs first. The logs can be found under these nodes in the Windows event log:

- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-ModernPOS
- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-Hardware Station

### Validate that the customer is not double charged

Even if the duplicate payment protection feature is enabled, it is generally recommended that the merchant verifies that no double charge has occurred. To do this, check all transactions on the corresponding payment gateway/processor portal.

### Payment recovery fails

An error may occur while a previous payment is being recovered on Modern POS. This can happen if there is an issue in the payment connector or payment gateway/processor that does not allow the previous payment to be recovered. To resolve this issue, because the previous payment cannot be recovered, the cashier must skip the recovery as described in the [How to skip Payment Recovery](#how-to-skip-payment-recovery) section.

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
