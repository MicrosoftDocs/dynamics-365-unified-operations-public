--- 
title: Set up vendors and vendor bank accounts for ISO20022 credit transfers
description: Learn how to set up the vendor and vendor-specific bank account information required for a ISO20022 credit transfer or any other vendor payment file generation in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/28/2025
ms.reviewer: johnmichalak   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: VendTable, VendBankAccounts
---

# Set up vendors and vendor bank accounts for ISO20022 credit transfers

[!include [banner](../../includes/banner.md)]

This article explains how to set up the vendor and vendor-specific bank account information required for a ISO20022 credit transfer or any other vendor payment file generation in Microsoft Dynamics 365 Finance.

The demo data company used to create the following procedures procedures is DEMF.

## Set up bank details

To set up bank details, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. Use the Quick Filter to find records. For example, filter on the **Vendor account** field with a value of "DE-001".
1. Select **DE-001** to open vendor details.
1. On the Action Pane, select **Vendor**.
1. Select **Bank accounts**.
1. Select **Edit**. If there is no bank account available, you must create a new one.  
1. In the **SWIFT code** field, enter "COBADEFFXXX".
1. In the **IBAN** field, enter "DE36200400000628808808".
1. Close the page.

## Set up a method of payment for the vendor

To set up a method of payment for the vendor, follow these steps:

1. Select **Edit**.
1. Expand or collapse the Payment section.
1. In the **Method of payment** field, select the drop-down button to open the lookup.
1. In the list, select the link in the **SEPA CT** row.
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
