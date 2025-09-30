---
title: CST and cClasstrib in Brazil Reformed Tax 
description: Learn about **CST** and **cClasstrib** in the Brazilian tax reform for 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/30/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# CST and cClasstrib in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes **CST** and **cClasstrib** in the Brazilian tax reform for 2026.

## Overview
Brazil's tax reform introduces two new tax attributes to support the new tax types: CBS, IBS, and the selective tax.

1. **CST** (Código de Situação Tributária) identifies the specific tax situation for a transaction. For example, it shows the applicable rate, an exemption, or a tax type.

1. **cClassTrib** (Código de Classificação Tributária) categorizes the transaction for tax purposes.

Maintain both attributes to support tax calculation and ensure compliance with electronic invoicing required by the reform.

## Form
This form supports CST and cClassTrib in the legacy tax system.

Go to **Tax > Setup > Sales tax > cClassTrib** to view the codes published by the government.

> [!NOTE]
> Microsoft provides the initial version, and you manage later updates.

The following table lists the fields and descriptions.

| Field                                                                   | Description                                                                                                                                                                                                      |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CST code                                                                | CST code under the Brazilian tax reform that classifies CBS/IBS for the transaction                                                                          |
| Description                                                             | Description of the tax situation.                                                                                                                                  |
| Explanation code                                                        | CST code under the new Brazilian tax reform, used to classify CBS/IBS application for the transaction                                                                                                            |
| cClassTrib                                                              | Worker identification number.                                                                                                                                                                                 |
| Description CST-IBS/CBS                                                 | Tax situation description 
| Description cClassTrib                                                  | Description of the tax classification. 
| LC Writing                                                              | Provision from Brazilian Complementary Law (LC).
| Suspended                                                              | This checkbox shows the status of the current record. When selected, the value is inactive. Inactive (suspended) records stay in the system for historical reference but don't appear in dropdown lists. Use this status for records that aren't valid, temporarily paused, or created in error.

> [!NOTE]
> This form doesn't support deleting records at the moment.
> This form doesn't support deleting records at the moment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
