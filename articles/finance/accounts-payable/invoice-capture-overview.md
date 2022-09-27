---
# required metadata

title: Invoice capture service overview
description: This article provides general information about the invoice capture service. 
author: sunfzam
ms.date: 09/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: sunfzam
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture service

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about installing and configuring the (Optical Character Recognition) OCR service that will automatically create vendor invoices from 
invoice images.


## Invoice capture service overview 
The Accounts payable (AP) department manages and processes invoices for goods and services received. The AP accountant verifies the vendor invoice data to avoid extra 
effort for adjustment or correction during period close. So, vendor invoices can be paid in a timely manner to prevent financial loss due to error or fraud. 
Optical Character Recognition (OCR) has been widely used by various industries in past years. It's a common method to digitizing printed texts so that they can be electronically edited, searched, stored 
more compactly, displayed on-line, and used in machine processes such as cognitive computing, machine translation, (extracted) text-to-speech, key data and text mining.
With evolvement of AI technology, modern OCR solution can read different invoice formats from various vendors with little human intervention. More and more companies are recognizing the fact that it can 
save lots of effort and improve accuracy by processing invoices via automation than manual processing.

 
## System landscape 
Microsoft provides world-class infrastructure which contains lots of fundamental services. Our vision is to design a seamlessly integrated solution regardless of whether the services are from 
different Microsoft platforms. Below are the major components and steps contained in this solution.

## Required roles

  | Roles                 | Actions | Systems/Role name | 
  |----------------------|----------|--------|------------|
  |Administrator|<ul><li>Set up environment in power platform</li><li>Deploy solutions in power platform</li><li>Setup connection between D365 and AI builder</li><li>Set up
  Azure data lake storage location</li></ul>|<ul><li>Dynamics 365/Dynamics 365 Administrator</li><li>Power Platform/Power Platform administrator</li><li>Azure Data Lake/
  Storage Blob Data Owner</li></ul>|
  |AI Maker |<ul><li>Maintain flow</li><li>Create custom AI model</li></ul>|Power Platform/Citizen Makers|
  |AP clerk |<ul><li>Review and take actions in Vendor invoice staging area</li><ul>|Power Platform/New AP clerk role in Power Platform|
  |AP clear |<ul><li>Daily operation as AP clerk</li><li>Navigate to Vendor invoice staging</li></ul>|Accounts payable clerk|
