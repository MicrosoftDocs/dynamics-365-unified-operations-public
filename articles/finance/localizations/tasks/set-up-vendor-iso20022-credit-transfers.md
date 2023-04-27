--- 
# required metadata 
 
title: Set up vendors and vendor bank accounts for ISO20022 credit transfers
description: This procedure demonstrates how to set up the vendor and vendor specific bank account information required for ISO20022 Credit transfer or any other vendor payment file generation. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendTable, VendBankAccounts   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up vendors and vendor bank accounts for ISO20022 credit transfers

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to set up the vendor and vendor specific bank account information required for ISO20022 Credit transfer or any other vendor payment file generation. 

The demo data company used to create this procedure is DEMF.
This is the fourth procedure, out of five, that illustrates the vendor payment process using electronic reporting configurations. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Set up bank details
1. Go to Accounts payable > Vendors > All vendors.
2. Use the Quick Filter to find records. For example, filter on the Vendor account field with a value of 'DE-001'.
3. Click DE-001 to open vendor details.
4. On the Action Pane, click Vendor.
5. Click Bank accounts.
6. Click Edit.
    * If there is no bank account available, you need to create a new one.  
7. In the SWIFT code field, type 'COBADEFFXXX'.
8. In the IBAN field, type 'DE36200400000628808808'.
9. Close the page.

## Set up a method of payment for the vendor
1. Click Edit.
2. Expand or collapse the Payment section.
3. In the Method of payment field, click the drop-down button to open the lookup.
4. In the list, click the link in the SEPA CT row.
5. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]