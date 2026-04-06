---
title: PCI Software Security Framework (SSF) evaluation
description: Learn about how the payment connectors built using Payments SDK such as Adyen payment connector can help reduce PCI DSS compliance scope for merchants across their commerce environment
author: Shalabh Jain
ms.date: 04/06/2026
ms.topic: how-to
ms.reviewer: johnmichalak@microsoft.com
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2026-01-01
ms.custom: 
  - bap-template
---

# PCI Software Security Framework (SSF) evaluation

[!include [banner](../includes/banner.md)]

This whitepaper is intended to help merchants understand how the payment connectors built using Payment SDK e.g., Microsoft Dynamics 365 Payment Connector for Adyen, when implemented as described, can support efforts to reduce PCI DSS compliance scope across their commerce environment. Based on an independent evaluation commissioned by Microsoft against applicable PCI Software Security Framework (SSF) requirements, the paper outlines how payment transactions initiated through Dynamics 365 Commerce including POS, Call center, and E-commerce channels are designed such that the application receives and processes transaction tokens only, without receiving, processing, or storing clear text cardholder data. By leveraging this tokenization based architecture in accordance with the documented deployment guidance, merchants may become eligible for a reduction in applicable PCI DSS controls, helping simplify their compliance responsibilities without compromising payment security.

Download the whitepaper for the evaluation here: [PCI SSF evaluation](<link to be added here Microsoft%20Dynamics%20365%20SSF%20Whitepaper%203%2019%202026.pdf>)
