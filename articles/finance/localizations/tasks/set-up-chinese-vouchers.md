---
title: Set up Chinese vouchers
description: This procedure walks you through setting up Chinese vouchers with specific demo data.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: China (PRC)
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: LedgerVoucherType_CN, HcmWorkerLookUp, LedgerParameters, LedgerPrintLayoutGroup_CN
---
# Set up Chinese vouchers

[!include [banner](../../includes/banner.md)]

This procedure walks you through setting up Chinese vouchers with specific demo data.
Chinese voucher numbers are the foundation for Chinese financial reporting. You must set them up before you do any financial transaction posting. You can set up the vouchers one at a time as this procedure demonstrates or you can use the Voucher type setup wizard to set them up.
This procedure was created using the demo data company CNMF. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Set up Chinese Voucher Type
1. Go to General ledger > Journal setup > Chinese voucher type > Voucher type.
2. Click New.
3. In the Voucher type field, type a value.
4. In the Voucher type number field, type a value.
    * This value is used as the Type ID in the GB/T24589 export file.  
5. In the Description field, type a value.
6. In the Priority field, enter a number.
    * For financial vouchers that are generated from source documents, such as posting sales invoices, if more than one voucher type is matched according the voucher type rule, the first priority voucher type will be assigned.  You also can set a voucher type as Default, which will be used as the default voucher type.  
7. In the Number sequence code field, enter or select a value.
8. In the Print layout group field, enter or select a value.
9. Enter the name of the person who is responsible for making this type of voucher.
    * This name will be used in the GB/T24589 export file. This should be a different person than the person who can approve this type of voucher.  
10. Enter the name of the person who can approve this type of voucher.
    * This name will be used in the GB/T24589 export file. This should be a different person than the person who can create this type of voucher.  
11. Click Add.
    * Voucher type rules define the criteria for vouchers. Only transactions in a voucher that meet these criteria can be assigned to this voucher type and can be posted. In this example, only bank accounts and cash accounts are allowed in debit and credit sides for this Cash type voucher.  
12. In the Restriction field, select 'All debits must include (one of the selected accounts)'.
13. Click Add.
14. In the Main account field, specify the values '100101'.
15. Click Add.
16. In the Main account field, specify the values '100102'.
17. Click Add.
18. In the list, mark the selected row.
19. In the Main account field, specify the values '100103'.
20. Click Add.
21. In the Account type field, select 'Bank'.
22. In the Main account field, specify the values 'CNYBANK'.
23. Click Add.
24. In the Account type field, select 'Bank'.
25. In the Main account field, specify the values 'USDBANK'.
26. Click Add.
27. In the Account type field, select 'Bank'.
28. In the Main account field, specify the values 'HKDBANK'.
29. Click Add.
30. In the Restriction field, select 'All credits must include (one of the selected accounts)'.
31. Click Add.
32. In the Main account field, specify the values '100101'.
33. Click Add.
34. In the Main account field, specify the values '100102'.
35. Click Add.
36. In the Main account field, specify the values '100103'.
37. Click Add.
38. In the Account type field, select 'Bank'.
39. In the Main account field, specify the values 'CNYBANK'.
40. Click Add.
41. In the Account type field, select 'Bank'.
42. In the Main account field, specify the values 'USDBANK'.
43. Click Add.
44. In the Account type field, select 'Bank'.
45. In the Main account field, specify the values 'HKDBANK'.
46. Click Save.

## Setup additional parameters
1. Go to General ledger > Ledger setup > General ledger parameters.
    * In the General ledger parameter page, you must first enable Chinese Voucher, then select to allow Duplicate vouchers in fiscal year. Chinse vouchers need to be renumbered from 1 for each fiscal period.  
2. In the Check for voucher used field, select an option.

## Set up the print layout
1. Go to General ledger > Journal setup > Chinese voucher type > Print layout.
2. Click New.
3. In the Print layout group field, type a value.
4. In the Description field, type a value.
5. Click Add.
6. In the Print layout code field, select an option.
7. Click Add.
8. In the Print layout code field, select an option.
9. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
