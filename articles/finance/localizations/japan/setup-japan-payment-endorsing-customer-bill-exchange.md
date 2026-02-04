---
title: Set up Japan payment by endorsing a customer bill of exchange
description: Learn how to set up payments by endorsing a customer bills of exchange for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - CustPosting
  - CustParameters
ms.custom: 
  - bap-template
---

# Set up Japan payment by endorsing a customer bill of exchange

[!include [banner](../../includes/banner.md)]

This article explains how to set up payments by endorsing a customer bills of exchange for Japan in Microsoft Dynamics 365 Finance.

The following procedures use the demo data company JPMF.

## Set up a posting profile for endorsing bills of exchange

To set up a posting profile for endorsing bills of exchange, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Customer posting profiles**.
1. Select **New**.
1. In the **Posting profile** field, enter a value. For example, enter "New BoE".  
1. Select **Add**.
1. In the **Account code** field, select an option. For example, select **All**.  
1. In the **Endorse account** field, enter a value.
1. Select **Save**.

## Set up bills of exchange information in accounts receivable parameters

To set up bills of exchange information in accounts receivable parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Select the **Ledger and sales tax** FastTab.
1. Expand the **Bill of exchange** section.
1. In the **Endorse bill of exchange** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
