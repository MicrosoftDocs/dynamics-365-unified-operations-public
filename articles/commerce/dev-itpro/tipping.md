---
# required metadata

title: Tipping support in the Payments SDK
description: This topic describes SDK-level support for accepting tips on payment terminals
author: rubendel
manager: annbe
ms.date: 10/27/2020
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
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Tipping support in the POS payments SDK

[!include [banner](../includes/banner.md)]

This topic describes payments SDK support for tipping through the payment terminal. The new **TipAmount** property is provided to support scenarios where a payment terminal can be configured to present the customer with predefined tip amounts or percentages, selectable at the time of payment. This feature does not add support for tipping or tip reporting at the point of sale. To build full tipping capabilities, POS extensions will be needed. 

## Key terms

| Term | Description |
|---|---|
| Tips | Also known as a gratuities, tips are common in quick service and hospitalities to provide a payment directly to the store or restaurant employee who is providing services |
| Header level charge | A charge that can be applied to a purchase that is not for a specific line item. |

## Overview

Tipping is very common in certain locales and industries. For example, in quick service and hospitality tipping has become nearly ubiquitous in the United States. For many businesses, the ability to support tipping through payment terminals is becoming a differentiator when attracting employees. This feature adds a discrete **TipAmount** field to the payments SDK so tips selected at the payment terminal can flow back to the point of sale as part of the authorization response. 

While this feature adds support for tipping at the payments SDK level, it does not include support for other critical aspects of tipping support. Those may include reporting to indicate tip payouts at the end of shifts, the ability to pool tips, and the ability to report tips for payroll. To enable full tipping support, those capabilities will need to be implemented via extensions. 

### Prerequisites

| Tip on device | Customer must be able to select tip amount on the payment terminal itself. |
| **isTippingEnabled** support | Payment connectors must support the **isTippingEnabled** variable for payment initialization. |
| **TipAmount** | The tip amount must be returned from the payment connector in the **TipAmount** authorization response field. |
| POS tip support | The tip returned from the payment connector should be added to the sale as a header level charge. In addition, tip reporting an management is not provided out of box. |

### Tipping support by payment processor

This feature adds a new variable called **isTippingEnabled** to the **AuthorizePaymentTermianlDeviceRequest**. This variable indicates at the time a payment is requested if the payment connector can support tips that are returned in a discrete field as part of the authorization response. 

If **isTippingEnabled** is set to **True** and the cutomer chooses a tip on the payment terminal, that amount will be returned in **TipAmount** property of the **AuthorizePaymentCardPaymentResponse** returned from the payment connector. The tip amount is also included in the **ApprovedAmoutn** property of the authorization response. 

### Suggested implementation

It is recommended that a header-level charge is used to add the tip amount to the transaction after the authorization response is returned from the payment connector. To support this, an extension should be created for the **PaymentTerminalAuthorizePaymentRequestHandler**. That extension should add logic to add the header level charge line to the transaction if a **TipAmount** is returned in the authorization response. This extension



