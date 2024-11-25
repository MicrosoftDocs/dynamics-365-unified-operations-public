---
title: Use financial tags to display free text invoice descriptions
description: Learn about how to use financial tags to display the description of free text invoices, including outlines on uses of financial tags and requirements.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 2/08/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-01-03
ms.search.form: CustPosting, CustPaymMode, CustCashDiscount, CommissionPosting, MarkupTable\_Cust, CustPaymFee
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
---

# Use financial tags to display free text invoice descriptions

[!include [banner](../includes/banner.md)]

This article explains how to use financial tags to display the description of free text invoices.

When users post a voucher transaction for a free text invoice, only the description of the first line is shown. When users split a free text invoice into multiple lines for differentiation purposes, this behavior presents an issue because the voucher transaction doesn't reflect the description of each split line.

To fix this issue, the financial tag feature is available in the free text invoice area. Free text invoices provide flexibility in the capture of transaction details. Therefore, businesses can include specific information that isn't covered by predefined invoice fields.

One challenge in free text invoices is the requirement for a proper description that accurately represents the invoice items. This article explains how the financial tag feature addresses the description requirement for free text invoices. Additionally, it highlights the feature's relevance to the management of credit invoices, credit notes, free text invoice corrections, invoice line splits, and free text invoice templates.

## Financial tag feature extension in free text invoices

The financial tag feature is a powerful tool that's integrated into invoicing and enables businesses to categorize and organize their financial transactions. It introduces a structured approach that can enhance the description of free text invoices and effectively manage variable invoice types.

## Requirements for free text invoice descriptions

In free text invoices, descriptions play a crucial role in conveying essential information about the invoice items. A description should clearly describe the goods or services that were provided and any other relevant details. The open-ended nature of free text invoices can sometimes lead to inconsistent or incomplete descriptions. Therefore, it can be challenging for both parties to understand the transaction.

## Using financial tags to enhance descriptions

By using the financial tag feature in free text invoicing, businesses can overcome the challenges that are associated with description requirements. By assigning specific tags to each invoice item, the feature can create a structured framework for capturing transaction details.

To use this feature, users can define multiple financial tags that become available on the **Financial tags** FastTab on the header of the free text invoice. If a user must record multiple descriptions for each free text invoice line, they fill in the financial tag value on the header. Those values are then entered by default on the lines. The user can then update the default value as required.

If a user must define a brief description for each free text invoice line, and each line has a different description, the user should define the financial tag value only at the level of the free text invoice line.

In cases where a user splits the free text invoice line, the description that's defined through financial tags is copied for the split line.

## Extending the financial tag feature to other invoice types

The financial tag feature can also be used to manage other invoice types. Here are some examples:

- **Credit invoices** – When users issue credit invoices, financial tags can be assigned to the items that are being credited to provide a clear reference to the original invoice.
- **Credit notes** – By tagging credit notes with proper financial tags, businesses can distinguish them from regular invoices and ensure a correct accounting of returned goods or services.
- **Free text invoice corrections** – The financial tag that's attached to the original invoice to show a description of the item is also entered by default on the corrected invoice and the canceled invoice. This behavior helps maintain the consistency of the description on all three invoices.
- **Free text invoice templates** – Financial tags can be used to create standardized templates for free text invoices, to ensure consistent and correct descriptions across various transactions.
