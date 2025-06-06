--- 
title: Set up payment slip format for project invoices
description: Learn how to attach printed payment slips to project invoices and provide a payment reference for posting and settlement in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/27/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: OMLegalEntity, CustFormletterParameters
---

# Set up payment slip format for project invoices

[!include [banner](../../includes/banner.md)]

This article explains how to attach printed payment slips to project invoices and provide a payment reference for posting and settlement in Microsoft Dynamics 365 Finance.

Businesses commonly attach printed payment slips to invoices to assist customers and provide a payment reference for posting and settlement. The payment slip can be used for project or service invoices, collection letters, interest notes, and account statements, in addition to sales invoices and free text invoices. To process payment slips, first set up your creditor identification number and payment slip attachment formats.

The following procedures use the DEMF demo company, and the functionality is available for legal entities whose primary address is in Denmark.


## Set up a creditor ID number

To set up a creditor ID number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. Expand or collapse the **Bank account information** section.
1. Select **Edit**.
1. In the **FI-Creditor ID** field, enter a value.
1. Select **Save**.
1. Close the page.

## Set up a payment slip format for invoices, notes, letters, and statements

To set up a payment slip format for invoices, notes, letters, and statements, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Forms \> Form setup**.
1. Select the **Invoice** tab.
1. In the **Associated payment attachment on customer invoice** field, select one of the following options.
    - **None**: Do not print a payment slip. Select this option if the payment amount is in a currency other than Danish kroner (DKK).
    - **FIK 751**: Print an FIK 751 payment slip if you intend to manually write the payment amount and due date on the payment slip.
    - **FIK 752**: Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
1. Select **Save**.
1. Select the **Free text invoice** tab.
1. In the **Associated payment attachment on free text invoice** field, select one of the following options.
    - **None**: Do not print a payment slip. Select this option if the payment amount is in a currency other than Danish kroner (DKK).
    - **FIK 751**: Print an FIK 751 payment slip if you intend to manually write the payment amount and due date on the payment slip.
    - **FIK 752**: Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
1. Select **Save**.
1. Select the **Interest note** tab.
1. In the **Associated payment attachment on interest note** field, select one of the following options.
    - **None**: Do not print a payment slip. Select this option if the payment amount is in a currency other than Danish kroner (DKK).
    - **FIK 751**: Print an FIK 751 payment slip if you intend to manually write the payment amount and due date on the payment slip.
    - **FIK 752**: Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
1. Select **Save**.
1. Select the **Collection letter** tab.
1. In the **Associated payment attachment on collection letter** field, select one of the following options.
    - **None**: Do not print a payment slip. Select this option if the payment amount is in a currency other than Danish kroner (DKK).
    - **FIK 751**: Print an FIK 751 payment slip if you intend to manually write the payment amount and due date on the payment slip.
    - **FIK 752**: Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date. 
1. Select **Save**.
1. Select the **Account statement** tab.
1. In the **Associated payment attachment on account statement** field, select one of the following options.
    - **None**: Do not print a payment slip. Select this option if the payment amount is in a currency other than Danish kroner (DKK).
    - **FIK 751**: Print an FIK 751 payment slip if you intend to manually write the payment amount and due date on the payment slip.
    - **FIK 752**: Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date. 
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
