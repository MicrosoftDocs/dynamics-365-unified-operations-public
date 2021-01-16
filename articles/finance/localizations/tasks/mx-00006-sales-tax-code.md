--- 
# required metadata 
 
title: MX-00006 Set up sales tax code
description: Legal financial documents such as tax declarations or electronic invoices that are submitted to the tax authorities in Mexico must contain different types of tax registration IDs and other related information. 
author: sndray
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxVatReportCategory_MX, TaxTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MX-00006 Set up sales tax code

[!include [banner](../../includes/banner.md)]

Legal financial documents, such as tax declarations or electronic invoices submitted to the tax authorities in Mexico, must contain different types of tax registration IDs and other related information. This guide details the necessary steps to complete the information about registration IDs in Mexican legal entities.

1. Go to Organization administration > Organizations > Legal entities.
2. Click New.
    * If you have already created your legal entity for Mexico, edit an existing legal entity instead of creating a new one.  
3. In the Name field, type a value.
4. In the Company field, type a value.
5. In the Country/region field, Select the Country/region code.
6. Click OK.
7. Expand or collapse the Registration numbers section.
8. In the Company type field, select an option.
9. In the RFC number field, enter the 12-character RFC number of the legal entity.
    * Federal Registration for Taxpayers (RFC) number is the tax identification number assigned by tax authorities to a person or a corporation. The system validates the tax registration IDs according to the format specified by tax authorities in Mexico.  
10. In the CURP number field, enter the 18-character CURP number of the legal entity.
    * Unique Fiscal Card Identification (CURP) number, which is the tax identification number assigned by the tax authorities to a person. The system validates the tax registration IDs according to the format specified by tax authorities in Mexico.  This field is required when the RFC field is empty.  
11. In the State inscription field, type a value.
12. In the Legal representative field, type a value.
13. In the Legal representative RFC field, Enter the 12-character RFC number of the legal entity representative.
    * The system validates the tax registration IDs according to the format specified by tax authorities in Mexico.  
14. In the Legal representative CURP field, Enter the 12-character CURP number of the legal entity representative.
    * The system validates the tax registration IDs according to the format specified by tax authorities in Mexico.  
15. Click Save.

