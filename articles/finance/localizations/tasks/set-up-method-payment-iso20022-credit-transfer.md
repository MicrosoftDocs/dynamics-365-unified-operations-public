--- 
# required metadata 
 
title: Set up method of payment for ISO20022 credit transfer
description: This procedure shows how to set up the vendor method of payment for ISO20022 credit transfer or any other payment type using electronic reporting to generate a file. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendPaymMode   
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
# Set up method of payment for ISO20022 credit transfer

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up the vendor method of payment for ISO20022 credit transfer or any other payment type using electronic reporting to generate a file. 

Before you complete this task, you must export format configurations and set up payment accounts.

This task was created using the DEMF demo data company.

This is the third procedure, out of five, that illustrates the vendor payment process using electronic reporting configurations. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Accounts payable > Payment setup > Methods of payment.
2. Use the Quick Filter to find records. For example, filter on the Method of payment field with a value of 'SEPA CT'.
3. Click Edit.
4. In the Period field, select 'Total'.
5. In the Payment type field, select 'Electronic payment'.
6. Expand the File formats section.
7. Select Yes in the Generic electronic reporting field.
8. In the Export format configuration field, enter or select a value.
    * In the list, select the value ISO20022 Credit transfer (DE). If the list is empty, the vendor payment export format configuration is not imported and active.  
9. In the Account type field, select 'Bank'.
10. In the Payment account field, specify the values 'DEMF OPER'.
11. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]