---
title: Chronological invoice and voucher numbers
description: Learn how to set up and use chronological numbers for invoices and vouchers in Accounts receivable, including prerequisites.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: France
ms.search.validFrom: 2016-11-30
ms.search.form: CustParameters, NumberSequenceGroup
ms.dyn365.ops.version: Version 1611
---

# Chronological invoice and voucher numbers

[!include [banner](../../includes/banner.md)]

This article explains how to set up and use chronological numbers for invoices and vouchers in Accounts receivable.  

In some countries or regions, a legal requirement exists that all invoices and related vouchers that you issue are numbered in chronological order. Fiscal periods must support the chronology. All the numbers that belong to earlier periods are less than the numbers that belong to later periods. Within one fiscal period, chronological order isn't mandatory, but the numbering can't have gaps. To meet this requirement, chronological numbering in Accounts receivable affects the following documents:

- Free text invoice
- Free text invoice voucher
- Free text credit note
- Free text credit note voucher
- Sales invoice
- Sales invoice voucher
- Sales credit note
- Sales credit note voucher

## Prerequisites

| Category            | Prerequisite                                                                                                                                                                                                                                                                                                                                                                                   |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Country/region  | The primary address of the legal entity must be in France.|
| Parameters      | Set **Chronological numbering** to **Yes** on the **Accounts receivable parameters** page, on the **Updates** tab.                                                                                                                                                                                                |
| Related setup tasks | On the **Number sequences** page, define as many number sequences as you require to cover the affected fiscal periods. You should specify a company for each number sequence. The segments of the number sequences must be defined so that they provide chronological order for periods. For example, the segment names can contain a special prefix that identifies a specific period.  |

## Set up chronological numbering

### Accounts receivable parameters

On the **Accounts receivable parameters** page, on the **Number sequences** tab, select one of the supported references, such as **Free text invoice**. Then select the **Chronological numbering setup** button that appears for the supported references. On the **Chronological numbering setup** page, define the date-effective number sequences that have valid periods.

:::image type="content" source="../media/emea-chronological-numbering.jpg" alt-text="Screenshot of the Chronological numbering setup page showing date-effective number sequences configuration.":::

### Number sequence groups

If different customers use different patterns for numbering, set up chronological numbering at the level of the number sequence group. On the **Accounts receivable parameters** page, on the **Number sequences** tab, select one of the supported references, and then select **Group**. On the **Number sequence group** page, select an existing group, or create a new group. In the **Reference** section, select one of the supported references, and then select **Chronological numbering setup**. On the **Chronological numbering setup** page, define date-effective number sequences that have valid periods.

## Invoice posting

When you post an invoice or a credit note, the system uses the appropriate number sequence to generate a number. The system selects this number sequence based on the valid period that contains the invoice date. Customer-specific chronological numbering takes priority over chronological numbering.

### Dates control

The system performs an additional invoice dates check for customer invoices:

- Posting new invoices with dates earlier than the date of the latest posted invoice is forbidden if no reason code is defined. To enable posting, enter a reason code either in an invoice or order header or in one of the lines.
- A warning is raised if the new invoice date is later than the system date.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
