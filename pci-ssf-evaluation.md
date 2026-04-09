---
title: PCI Software Security Framework (SSF) evaluation
description: Learn about how the payment connectors built using Payments SDK such as Adyen payment connector can help reduce PCI DSS compliance scope for merchants across their commerce environment
author: Shalabh Jain
ms.date: 04/09/2026
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

This whitepaper helps merchants understand how payment connectors built using Payment SDK, such as Microsoft Dynamics 365 Payment Connector for Adyen, can support efforts to reduce PCI DSS compliance scope across their commerce environment when implemented as described. Based on an independent evaluation commissioned by Microsoft against applicable PCI Software Security Framework (SSF) requirements, the paper outlines how payment transactions initiated through Dynamics 365 Commerce, including POS, call center, and e-commerce channels, are designed such that the application receives and processes transaction tokens only, without receiving, processing, or storing clear text cardholder data. By leveraging this tokenization-based architecture in accordance with the documented deployment guidance, merchants might be eligible for a reduction in applicable PCI DSS controls, which helps simplify their compliance responsibilities without compromising payment security.

Download the whitepaper for PCI SSF evaluation: [Microsoft Dynamics 365 Commerce SSF Whitepaper](download.microsoft.com/download/3650a88d-62f7-4814-b566-f1b643ec27fe/Microsoft Dynamics  365 Commerce SSF  Whitepaper.pdf)
