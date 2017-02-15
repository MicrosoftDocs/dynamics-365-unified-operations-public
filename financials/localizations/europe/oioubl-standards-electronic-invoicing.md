---
# required metadata

title: OIOUBL standards for electronic invoicing
description: This topic explains what Offentlig Information Online Universal Business Language (OIOUBL) is.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-10-19 23 - 02 - 38
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 10274
ms.assetid: 5e953cc6-5783-4aaf-a8ad-7d96d36213e8
ms.search.region: Denmark
ms.search.industry: Public sector
ms.author: mrolecki
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# OIOUBL standards for electronic invoicing

This topic explains what Offentlig Information Online Universal Business Language (OIOUBL) is.

Danish companies must submit sales order invoices, free text invoices, project invoices, sales order credit notes, and project invoice credit notes as .xml files to the government. These .xml files must comply with the Offentlig Information Online Universal Business Language (OIOUBL) standards. OIOUBL is a customization of the international Universal Business Language (UBL) 2.1 standard from the Organization for the Advancement of Structured Information Standards (OASIS) for Danish business requirements. The primary advantage of OIOUBL is that business documents can be standardized for different purposes. Because UBL 2.0 is a flexible, international standard that supports many business requirements, these business documents can be exchanged across national borders. The electronic invoices and credit notes that you generate include required information, such as a European Article Numbering (EAN) number, contact person, dimension account number, and address information for the customer. In Microsoft Dynamics AX, validation rules are applied when invoices are generated so you can verify that the correct information has been entered. If you find errors, you can correct the errors before you submit the invoices to the government.



