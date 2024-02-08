---
# required metadata

title: Use financial tags to diplay the free text invoice description
description: This article explains how to use financial tags to diplay the free text invoice description.
author: prabhatb
ms.date: 2/08/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPosting, CustPaymMode, CustCashDiscount, CommissionPosting, MarkupTable\_Cust, CustPaymFee
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---

# Use financial tags to diplay the free text invoice description

[!include [banner](../includes/banner.md)]

This article explains how to use financial tags to diplay the free text invoice description.

When posting a voucher transaction for a free text invoice, only the description of the first line is displayed. This poses a problem when users split a free text invoice into multiple lines for differentiation 
purposes as the voucher transaction doesn't reflect the description of each split line.
 
To resolve this issue, the financial tags feature is available in the free text invoice area. Free text invoices provide flexibility in capturing transaction details, allowing businesses to include specific 
information not covered by predefined invoice fields. One challenge in free text invoices is the requirement for a proper description that accurately stands for the invoice items. This article describes how the 
financial tag feature addresses the description requirement for free text invoices. Additionally, it highlights the feature's relevance in managing credit invoices, credit notes, free text invoice 
corrections, invoice line splits, and free text invoice templates.
 
### Financial tag feature extension in free text invoice
 
The financial tag feature is a powerful tool integrated into invoicing that enables businesses to categorize and organize their financial transactions. It introduces a structured approach that can enhance 
the description of free text invoices and effectively manage variable invoice types.
 
### Free text invoices description requirements
 
In free text invoices, descriptions play a crucial role in conveying essential information about the invoice items. It should clearly describe the goods or services provided, and any other relevant details.
The open-ended nature of free text invoices can sometimes lead to inconsistent or incomplete descriptions, making it challenging for both parties to understand the transaction.
 
## Financial tags to enhance descriptions
 
Using the financial tag feature in free text invoicing, businesses can overcome the challenges associated with description requirements. The feature can assign specific tags to each invoice item, creating a 
structured framework for capturing transaction details.
 
To use this feature, users can define multiple financial tags to be available in the header of the free text invoice under the **Financial tags** FastTab. If the user needs to record multiple descriptions 
for each free text invoice line, the user fills in the financial tag value in the header, and these values default on the lines. The user can then update the defaulted value if necessary.
 
If the user needs to define a brief description for each free text invoice line, and each line holds a different description, the user should define the financial tag value on the free text invoice line
level only.
 
In cases where the user splits the free text invoice line, the description defined through financial tags will also be copied for the split line.
 
### Extend financial tag feature to other invoice types

The financial tag feature can also be used for managing various other invoice types, including:
 
 - **Credit invoices** - When issuing credit invoices, financial tags can be assigned to the items being credited, providing a clear reference to the original invoice.
 - **Credit notes** -  By tagging credit notes with proper financial tags, businesses can distinguish them from regular invoices and ensure proper accounting of returned goods or services.
 - **Free text invoice corrections** - The financial tag attached with the original invoice to display description of the item will default in the corrected invoice and cancelled invoice as well. This maintains 
consistency of description in all the three invoices.
 - **Free text invoice templates** - Financial tags can be used to create standardized templates for free text invoices to ensure consistent and right descriptions across various transactions.
 



