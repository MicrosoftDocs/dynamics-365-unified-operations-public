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
# Generate QR codes and print them on receipts for Saudi Arabia

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

## Set up QR codes

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or higher than 900001.

| Language ID | Text ID | Text ID                   |
|-------------|---------|---------------------------|
| en-US       | 900001  | QR code (SA)              |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name               | Type    | Caption text ID |
|--------------------|---------|-----------------|
| INVOICEQRCODE_SA   | Receipt | 900001          |

### Configure receipt formats

For every required receipt format, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Footer:** Add the following fields:

    - **QR code (SA)** – This field prints the QR code in the receipt.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).
