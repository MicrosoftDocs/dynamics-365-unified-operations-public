---
title: Italian localization - Payment traceability
description: Learn how to control the Tender procedure identification and CIPE codes during end-to-end processing from the original invoice to the payment.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/01/2026
ms.reviewer: johnmichalak
ms.search.region: Italy
ms.dyn365.ops.version: 10.0.17 
---

# Italian localization - Payment traceability

[!include [banner](../../includes/banner.md)]

For Italian companies that work with public sector companies, you might need to control the Tender procedure identification and CIPE codes during end-to-end processing from the original invoice to the payment. Both the Accounts Receivable and Accounts Payable modules can require this control.

## Prerequisites

Before you can use the payment traceability functionality, make sure the following prerequisites are met:

- The primary address of the legal entity is in Italy.
- The feature **(Italy) Base document tracking improvements** is turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Feature details

When you activate the feature, the system associates the Tender procedure identification (CIG) and CIPE (CUP) codes with the particular customer or vendor transaction. This association provides higher traceability across the system and you can review it by using the standard personalization mechanism. To inherit the values from the original invoice transaction during payment proposal, on the **Methods of payment** page, activate the **Base document payment** attribute. 
To ensure that the mandatory fields for the CIG and CUP codes are populated in the transaction, mark the Customer account, Vendor account, or group as with Public sector parameter.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
