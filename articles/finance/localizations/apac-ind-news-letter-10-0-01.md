---
# required metadata

title: APAC-IND-Newsletter-10-0-01
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-01
author: prabhatb
manager: Wangcheng
ms.date: 05/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
[!include [banner](../includes/banner.md)]

# Welcome to the newsletter for version 10.0.1! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.01 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-1)

# New Features
## New Configuration 
The following configurations, which you can get from the Shared Asset Library in LCS and use it in version 10.0.1 and above:
 
- GSTReturns.version.14.xml
- GST Returns model mapping.version.14.5.xml
- GSTR1CSV.version.14.28.xml
- GSTR2CSV.version.14.32.xml
 
It solved the following GSTR issues:
- Total Item Discount Amount is not coming in GSTR.
- Item Unit Of Measurement should show both unit and its description, and for service item, it should be "Nos".
- No customer billing name for stock transfer in GSTR.

## Non-GST item
You can create Non-GST item, and it would be defaulted into Tax Information in the taxable transactions.


![](media/Non GST item-10.0.1.png)

# Critical Fixes 

- Cannot post a purchase invoice for service item with load on inventory.
- HSN summary is empty and no records in B2CL in GST offline tool format.
- Total transaction value in GSTR1/GSTR2 does not equal to invoice amount when a transaction is price include tax.
- Edit RFQ Reply throw error "Posting Exception has been thrown by the target of an invocation".
- Amount origin of withholding tax is incorrect.
- Unable to save purchase order after changing financial dimension with error "Function MarkupTrans.parmSourceDocLineTypeEnumName
  has  been incorrectly called.".
- Posting sales invoice occasionally gets the warning "Voucher xxx is already used as of date".
- After change the tax formula, its condition is updated with the same content as the formula.
- Invoice date is incorrect in GSTR1/GSTR2.
- Cannot create project invoice proposal for the on-account journal when journal include WHT with error "Object reference not
  set to an instance of an object".
-	Tax journal with tax component as IGST and posting type as Tax Payable is posted with SGST & CGST with zero amount.
- Tax Transaction Inquiry form allows only 11 fields to be selected.
- GSTR2 takes the bill of entry posting date instead of posting date for import order.
- Cannot open tax document when the GST configuration is extended with error message "object reference not set an
  instance of an object".
- After edit formula/condition, then the condition of other nodes also showing the same value string.
- Auto block importing of invalid old AX (AX2012) configuration version to Dynamics 365 for Finance and Operations
- Not able to setup GSTR configuration for two companies
- Not allow a user to add multiple tax measures with the same name.
- Retail statement posting fails during sales invoice posting when there is price include tax sales order with service item, 
  and the tax is different from the tax in the head quarter.

# Upcoming critical fixes in 10.0.2 

- Fixed exchange rate is not considered in GSTR1.
- Unable see the Tax information for a Timesheet in Indian Legal entity.
- GSTIN of Ecommerce operator is always blank in GSTR1.
- Place of supply is incorrect in GSTR2.
- Project expense cannot be posted when there are sales tax group and item sales tax group. 
