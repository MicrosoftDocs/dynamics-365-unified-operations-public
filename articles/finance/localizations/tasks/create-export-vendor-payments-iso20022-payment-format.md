--- 
# required metadata 
 
title: Create and export vendor payments using ISO20022 payment format
description: This procedure shows how to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example. 
author: mrolecki
ms.date: 01/17/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym, SysQueryForm, VendPaymProposalEdit, BankAccountTableLookUp   
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
# Create and export vendor payments using ISO20022 payment format

[!include [banner](../../includes/banner.md)]

This article explains how to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example.

This is the fifth procedure, out of five, that illustrates the vendor payment process using electronic reporting configurations. Use the DEMF demo data to complete this example.

## Example

1.    Go to **Accounts payable > Payments > Payment journal**.
2.    Click **New**.
3.    In the **Name** field, enter or select a value.
4.    Click **Lines > Payment proposal > Create payment proposal**.
5.    Expand the **Records to include** section.
6.    Click **Filter**.
7.    In the list, select the row for **Vendors table** and **Vendor account field**.
8.    In the **Criteria** field, enter or select a value. You can apply any criteria for selecting vendor transactions to pay, for this example, use DE-001 as a vendor account.
12.    Click **OK**.
13.    Click **OK**.
14.    Click **Create payments**.
15. Generate an ISO20022 payment file.
    1.    Click **Generate payments**.
    2.    In the **Method of payment** field, enter or select a value.
    3.    In the **File name** field, type a value. For this example, because of the EUR payment, the generated file will be SEPA compliant. ISO20022 credit transfer as well as other vendor payment formats can also be used for generating payments in other currencies.
    4.    In the **Bank account** field, enter or select a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]