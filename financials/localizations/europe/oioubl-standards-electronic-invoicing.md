---
# required metadata

title: OIOUBL standards for electronic invoicing | Microsoft Docs
description: This topic explains what Offentlig Information Online Universal Business Language (OIOUBL) is.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-10-19 23:02:38
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 10274
ms.assetid: 96504a56-07c4-496b-bf91-e6ddb616cdda
ms.region: Denmark
ms.industry: Public sector
ms.author: mrolecki

---

# OIOUBL standards for electronic invoicing

This topic explains what Offentlig Information Online Universal Business Language (OIOUBL) is.

Danish companies must submit sales order invoices, free text invoices, project invoices, sales order credit notes, and project invoice credit notes as .xml files to the government. These .xml files must comply with the Offentlig Information Online Universal Business Language (OIOUBL) standards. OIOUBL is a customization of the international Universal Business Language (UBL) 2.1 standard from the Organization for the Advancement of Structured Information Standards (OASIS) for Danish business requirements. The primary advantage of OIOUBL is that business documents can be standardized for different purposes. Because UBL 2.0 is a flexible, international standard that supports many business requirements, these business documents can be exchanged across national borders. The electronic invoices and credit notes that you generate include required information, such as a European Article Numbering (EAN) number, contact person, dimension account number, and address information for the customer. In Microsoft Dynamics AX, validation rules are applied when invoices are generated so you can verify that the correct information has been entered. If you find errors, you can correct the errors before you submit the invoices to the government.



