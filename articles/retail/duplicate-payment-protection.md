---
# required metadata

title: Duplicate payment protection- Functional experience
description: Duplicate payment protection- Functional experience
author: rubendel
manager: AnnBe
ms.date: 11/22/2018
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

# Duplicate Payment Protection Functional Experience
This topic provides an overview of the duplicate payments protection feature for the Dynamics 365 for Retail Modern POS.

## Key terms
| Term | Description | 
| --- | --- |
| Payment Connector |	An extension which facilitates communication between Dynamics 365 for Retail (and associated components) and a payment service. The connector described in this article was implemented using the standard payments SDK. |

## Overview
This article describes the user experience when the point of sale recovers from a loss of communication with the payment terminal which causes the point of sale and the payment terminal to be out of sync.
The duplicate payment protection features ensures that the Dynamics 365 for Retail Modern POS can seamlessly recover from these type of error escenarios without requiring the shopper to run another payment through the payment terminal, which can lead to duplicate payments. 
This article covers the following aspects of the duplicate payment protection feature:

- **[Prerequisites](#Prerequisites)** - Set of prerequisites to leverage this feature in the Dynamics 365 for Retail Modern POS.
- **[Scenario Details](#Scenario-Details)** - Detailed description of the scenarios covered by the duplicate payment protection feature.
- **[Troubleshooting Steps](#Troubleshooting-Steps)** - Detailed troubleshooting steps when encountering issues with duplicate payment protection feature.
- **[Common Issues](#Common-Issues)** - List of common issues you might encounter when using the duplicate payment protection feature, including the symptoms, root cause, and potential fix for each of them.
- **[Related Articles](#Related-Articles)** - List of related articles you might find useful when using the duplicate payment protection feature.

## Prerequisites
This feature quires the payment connector and corresponding payment gateway or processor to support this feature. 
If a given connector implments the cooresponding duplicate payment protection interfaces the feature is automatically enabled in the Dynamics 365 for Retail Modern POS.
Otherwise it is automatically disabled. 
The [Implement Duplicate Payment Protection](TODO) article describes in detail how to implement support for the duplicate payment protection feature for a given payment connector.
The [Dynamics 365 Payment Connector for Adyen](TODO) has built in support for the duplicate payment protection feature.

## Scenario Details
The duplicate payment protection feature is applicable to **any** scenario in which the a payment is initiated and completed on a payment terminal but the Dynamics 365 for Retail Modern POS is unable to receive the corresponding response. 
As a result, the customer's card (e.g. credit card) is charged but the payment line is not added to the POS. 
In most cases, the cashier will trigger a subsequent payment on the payment terminal, which results in a duplicate payment for the customer.

### How Duplicate Payments Scenarios are triggered
1. **Cashier initiates payments**:
  - Cashier initiaties a card payment by clicking on `Pay card` on the Dynamics 365 for Retail Modern POS, navigates to the `Payment Page`, and click the `Tender` button.
2. **Customer interacts with payment terminal**:
  - Once the payment is initiated the payment terminal is lid up prompting the customer for payment. The customer initiates the payment process on the payment terminal. 
3. **Dynamics 365 for Retail Modern POS loses connectivity to the payment terminal**:
  - While the customer is running a payment on the payment terminal the Dynamics 365 for Retail Modern POS loses connectivity to the payment terminal because it either crashes, loses network connectivity, is closed, or the terminal is rebooted.
  - The cashier will re-launch or Dynamics 365 for Retail Modern POS or address any connectivity issues.
4. **Customer completes payment on the payment terminal**:
  - As the Dynamics 365 for Retail Modern POS is being reset the customer completes the payment on the payment terminal and is charged.
5. **Dynamics 365 for Retail Modern POS is launched**:
  - The cashier completes the reset/launch of the Dynamics 365 for Retail Modern POS but the payment is not added to the cart.

### How Previous Payments are recovered
As the cashier continues to interact with the previous transaction there are several ways in which the previous payment done through the terminal is automatically recovered.
In each of these scenarios the cashier is shown a dialog indicating that a previous payment has already been made, which is automatically recovered and added as a payment line to the cart.
The main principal behind the duplicate payment protection feature is to put the Dynamics 365 for Retail Modern POS back into the same state it would be if the original payment would have been successfully processed and the corresponding payment line was added to the cart.

- **Cashier invokes another payment for the same amount using any payment method**.
- **Cashier invokes another payment for a different amount**.
- **Cashier attempts to void the transaction**.

### How to skip Duplicate Payment Protection
In some cases the cashier might explicitly chose to skip the duplicate payment protection and opt not to recover a previous payment.
In those cases, the cashier can follow the steps described below to void the transaction without recovering the payment:

1. TODO

### How to handle the case when the customer leaves the store
In some cases, the customer might chose to leave the store before the cashier can finalize the transaction. 
In those cases it is recommended to follow the steps described below to avoid the customer from being charged.

1. **Cashier launches the Dynamics 365 for Retail Modern POS**:
  - The cashier relaunches the Dynamics 365 for Retail Modern POS to recover from the previous issues that were encountered.
2. **Cashier recovers the previous payment**:
  - Cashier clicks on the `Pay Card` button and follows the steps to run a regular card payment. 
  - Once done, the cashier will be shown that a payment was recovered.
  - Once the cashier clicks the `OK` button the payment line is automatically added to the cart.
3. **Cashier voids the previous payment**:
  - Cashier clicks on the `Void payment` button and voids all payment lines that were added, including the recovered payment line.
4. **Cashier voids the transaction**:
  - Once all payment lines are voided the cashier can then void the entire transaction.
  
Following these instructions will ensure that the customer will not be charged for the payment.

## Troubleshooting Steps

### General Issues
For all general issues you should always consult the Modern POS or IIS Hardware Station Event Logs first. These can be found under the nodes in the Windows Event Log:
  - **Application and Services Logs > Microsoft > Dynamics > Commerce-ModernPOS**
  - **Application and Services Logs > Microsoft > Dynamics > Commerce-Hardware Station**

### Validating that the customer is not double charged
Even when the duplicate payment protection feature is invoked it is generally recommended that the merchant verifies that no double charge has occurred by checkin all transactions on the corresponding payment gateway/processor portal.

## Common Issues

### Payment Recovery Fails
| Title | Payment Recover Fails |
| :-- | :-- |
| **Symptom** | An error occurs while a previous payment is being recovered on the Dynamics 365 for Retail Modern POS. |
| **Root Cause** | This can happen when there is an issue in the payment connector or payment gateway/processor ths does not allow the previous payment to be recovered. |
| **Fix** | Since the previous payment cannot be recovered the cashier has to skip the recovery as described in the [How to skip Duplicate Payment Protection](#How-to-skip-Duplicate-Payment-Protection) section. | 

## Related Articles
- **[Payments FAQ](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/payments-retail)**

