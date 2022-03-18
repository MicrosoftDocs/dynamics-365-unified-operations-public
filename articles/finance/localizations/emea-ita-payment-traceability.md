---
# required metadata

title: Italian localization - Payment traceability 
description: This topic explains how to control the Tender procedure identification and CIPE codes during end-to-end processing from the original invoice to the payment.
author: anasyash
ms.date: 02/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.17

---

# Italian localization - Payment traceability

[!include [banner](../includes/banner.md)]


For Italian companies who work with public sector companies, there might be requirements to control the Tender procedure identification and CIPE codes during end-to-end processing from the original invoice to the payment. This required control can be in both the Accounts Receivable and Accounts Payable modules.

## Prerequisites

Before you can use the payment traceability functionality, the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- The feature **(Italy) Base document tracking improvements** must be turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Feature details

With the feature activated, the Tender procedure identification (CIG) and CIPE (CUP) codes are inherited in relation to the particular customer or vendor transaction. This inheritance allows for higher traceability across the system and could be reviewed by using the standard personalization mechanism. To inherit the values from the original invoice transaction during payment proposal, on the **Methods of payment** page, activate the **Base document payment** attribute. 
To ensure that the mandatory fields correspond to the CIG and CUP codes are populated in the transaction, mark the Customer account, Vendor account, or group as with Public sector parameter.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
