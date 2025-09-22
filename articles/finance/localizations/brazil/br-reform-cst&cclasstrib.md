---
title: CST and cClasstrib in Brazil Reformed Tax 
description: The article desribes the CST and cClasstrib in Brazilian tax reform within scope of 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# CST and cClasstrib in Brazil Reformed Tax  

[!include [banner](../../includes/banner.md)]

The article desribes the **CST** and **cClasstrib** in Brazilian tax reform in scope for 2026.

## Overview
In the Brazil Tax Reform, two new tax attributes are introduced to support the new tax types, CBS, IBS, and the Selective Tax.

- **CST** (Código de Situação Tributária) identifies the specific tax situation of a transaction.

   For example,applicable rate, exemption, or tax type

- **cClassTrib** (Código de Classificação Tributária) classifies the transaction for tax purposes.

These two attributes must be maintained to support tax calculation and electronic invoicing compliance as mandated by the new reform.

## Form
A specified form has been created to support CST and cClasstrib located in legacy tax system.

Go to **Tax -> Setup > Sales tax > cClassTrib** which contains the codes published by the Government.

>[!note]
>The initial version is provided by Microsoft. Any later updates must be managed by the customer.

Here is the list for the fields and description.

| Field                                                                   | Description                                                                                                                                                                                                       |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CST code                                                                | CST code under the new Brazilian tax reform, used to classify CBS/IBS application for the transaction                                                                          |
| Descriprion                                                             | Tax situation description                                                                                                                                  |
| Explanation code                                                        | CST code under the new Brazilian tax reform, used to classify CBS/IBS application for the transaction                                                                                                            |
| cClassTrib                                                              | The worker identification number.                                                                                                                                                                                 |
| Description CST-IBS/CBS                                                 | Tax situation description 
| Description cClassTrib                                                  | Tax classification description 
| LC Writing                                                              | Provision from a Brazilian Complementary Law (LC)

