---
# required metadata

title: APAC-IND-Newsletter-10-0-00
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-00
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

# Welcome to the newsletter for version 10.0.! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0)

## New Features
## New Configuration 
The following configurations, which you can get from Shared Asset Library in LCS and use it in version 10, are available:

- Taxable Document.version.81.xml
- Taxable Document (India).version.81.138.xml
- Tax (India GST).version.81.138.246.xml 
 
You can differentiate customer GST registration number from vendor GST registration number in tax setup.

![](media/GST-registration-rate-setup-1-10-0-00.PNG)

You can choose to determine the tax rate based on invoice date for the purchase transactions, like purchase invoice.

![](media/GST-invoice-date-rate-setup-2-10-0-00.PNG)

You can create Non-GST transaction, and it will be reflected in GSTR.

![](media/GST-non-gst-transaction-3-10-0-00.PNG)

## Import/export tax setup

You can import/export tax setup for Rate, Reverse Charge Percentage, Load on Inventory Percentage, etc. 

![](media/GST-import-export-tax-setup-4-10-0-00.PNG)

## GTE designer enhancement

You can multi-select lookup columns, and search available columns.

![](media/GST-gte-multi-select-5-10-0-00.PNG)

## Critical Fixes 

- Cannot synchronize extended configuration if you change the data model in your extended tax document.

  ![](media/GST-extended-configuration-6-10-0-00.PNG)

- Exclude the transactions without GST from GSTR. If there is no GST applicable for the transaction (unless it's exempt or Non-GST),
  it will not be in the GSTR
- Block the posting with GST if there isn't GST transaction ID. 

## Upcoming critical fixes in 10.0.1

- Total Item Discount Amount is not coming in GSTR.
- Item Unit Of Measurement should show both unit and its description.
- Total transaction value in GSTR is not equal to invoice amount for transaction with price include tax-
  No customer billing name for  stock transfer in GSTR
-	No defaulting logic for Original GST transaction ID for credit note 
 
