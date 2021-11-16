---
# required metadata

title:Multiple Available Payments for In Store Pick-up
description: This topic reviews pick-up in store improvements for Multiple available payments
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 11/15/2021
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2021-11-15
ms.dyn365.ops.version: 

---

# Multiple Available Payments for In Store Pick-up

This article covers the Point-of-sale (POS) capabilities available when there are one or more pre-existing payments available to be used against the transaction.

## Overview

In some cases, a customer has created an order and provided payment which has been authorized. Most commonly, this scenario may be encountered with a payment against an order that will be picked up in store. Once in store, when a customer arrives and their transaction is brought up at POS, it is typically desired to use any existing authorized payments over accepting a new payment method. Dynamics 365 Commerce helps the POS user identify and apply available payments against the transaction.

## Pre-Requisites

In order to operate with the POS behavior as described below, the following settings must be set:

- In HQ, got to **Feature Management** and search for and enable **Omni-channel payments**

- In HQ, go to **Feature Management** and search for and enable **Display all preauthorized payments at checkout in POS** (requires above feature of **Omni-channel payments** to be enabled before this feature can be enabled)

- The hardware station for POS must be active if the HQ POS register **Card not present processing** setting is set to "Use hardware station". Otherwise, the setting should be set to "Use retail server".

  

## Applying Available Payments in POS

When payments are available to be used in a customer's POS transaction, POS provides indicators and flows to easily apply one or multiple available payments against a transaction. In POS with the customer's order located, selecting the order and choosing "Pick Up" will allow the POS user to select which items in the order can be picked up. Selecting the items and confirming the "Pick up" action, POS will then direct to the cart transaction screen.

### Available Payments Indicator

When in the cart transaction screen in POS with existing payment methods available to be used, an information indicator will display above the cart lines showing "There are existing payment options available to apply to this order. Learn more at checkout." This informational banner will signal to the POS user to help ensure the available payment methods are used, instead of selecting a new payment method to process.  If the POS user selects the Pay Card payment option, checkout, or the Amount due total, the options for existing card payments will be displayed along with the option to choose to take a new payment method. Other payment method selections outside of the three mentioned above, when selected from the transaction page, will display normally to accept the new payment method directly.

#### Using Available Payments

The POS user should select the cart Amount Due total to bring up the **Amount due** dialogue showing the total due as well as the available payment methods.

\>[!NOTE]

\>Not all payment methods will prompt the available payments dialogue. Mainly card operations will show as available payments if linked to the order. 

Users can select to use **Existing payment options** or **Choose a payment method** (which allows the user to continue with normal processing of a new payment method).

If multiple existing payment methods are available, the **Existing payment options** section of the **Amount due** dialogue will show an action button to 'Use available payment' with a count of how many existing payments are available. Selecting this action button will update the dialogue to show the existing payment options available. If more than one exists, an **Apply All** action button will be displayed, as well as action buttons for each specific payment method available. Using **Apply All** will use all of the pre-existing payment method amounts up to the total of the amount due for the transaction. For the specific existing payment action buttons, the summarized total amount existing for the payment method, the payment method type (example: Visa), and the last four digits of the payment method are displayed in the button. When a specific available payment method is selected:

- If the amount is less than the transaction total, the payment amount selected will show as a payment line and be applied against the total due
- If the amount is equal to the transaction total, the amount due is adjusted to zero and transaction is automatically completed
- If the amount is more than the transaction total, the available payments up to the total of the transaction will be used and the transaction automatically completed