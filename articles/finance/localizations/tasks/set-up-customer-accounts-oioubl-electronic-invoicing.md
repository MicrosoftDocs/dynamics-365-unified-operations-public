--- 
# required metadata 
 
title: Set up customer accounts for OIOUBL electronic invoicing
description: This task walks you through how to set up a customer account for OIOUBL electronic invoicing. 
author: mrolecki
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustTable, RegNumTaxIdLookup, smmContactPerson, DirPartyLookup, ContactPersonLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Denmark
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up customer accounts for OIOUBL electronic invoicing

[!include [banner](../../includes/banner.md)]

This task walks you through how to set up a customer account for OIOUBL electronic invoicing. 



This task was created using the demo data company USMF with the country/region of legal entity primary address updated to be Denmark.



This is the third procedure, out of six, that demonstrates the process of generating e-invoices using electronic reporting configurations. This task uses the OIOUBL e-invoice example which is common for Denmark, Austria, and Norway.

1. Go to Accounts receivable > Customers > All customers.
2. Use the Quick Filter to find records. For example, filter on the Account field with a value of 'US-023'.
3. Click Edit.
4. In the list, click the link in the selected row.

## Enable a customer account for OIOUBL electronic invoicing
1. Expand the Invoice and delivery section.
2. In the Tax exempt number field, enter or select a value.
3. Select Yes in the eInvoice field.
4. In the EAN field, type a value. For example '5798000362147'..

## Set up contact information for a customer

