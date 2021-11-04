---
# required metadata

title: Generate QR codes and print them on receipts for Saudi Arabia
description: This topic provides an overview of the QR code printing functionality that is available for Saudi Arabia.
author: EvgenyPopovMBS
manager: annbe
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: RetailFunctionalityProfile, RetailFormLayout, RetailParameters
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Saudi Arabia
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2021-11-04
ms.dyn365.ops.version: 10.0.21

---
# Generate QR codes and print them on receipts

This topic provides an overview of the QR code printing functionality that is available for Saudi Arabia.

## Overview

QR code for Saudi Arabia contains the following information:

| Sequence | Field                                                  | Data source |
|----------| -------------------------------------------------------|---------|
| 1        | Company name                                           | The name of the legal entity that the store belongs to |
| 2        | Company VAT registration number                        | The tax registration number of the legal entity that the store belongs to |
| 3        | Date and time of transaction                           | The date and time of the retail store transaction |
| 4        | Total receipt amount (including value-added tax (VAT)) | The total amount of the retail store transaction |
| 5        | Total amount of VAT included in receipt                | The total tax amount of the retail store transaction |

> [!NOTE]
> For create customer order transactions, the total receipt amount is calculated as the sum of total amounts of all transaction lines with the Carry-out delivery mode.

Filed name: INVOICEQRCODE_SA
