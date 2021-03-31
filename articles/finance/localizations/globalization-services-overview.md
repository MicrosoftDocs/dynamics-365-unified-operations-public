---
# required metadata

title: Microsoft Dynamics Globalization services overview
description: This topic provides an overview of Dynamics Globalization services
author: JaneA07
manager: AnnBe
ms.date: 03/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RCS, Regulatory Configuration Services, Localization, Electronic invoicing, Tax calculation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: AX 10.0.9

---
# Microsoft Dynamics Globalization service overview

[!include [banner](../includes/banner.md)]

## Overview: 
The following configurable globalization services extend the capabilities that exist in some Dynamics 365 online services:
- **Dynamics Regulatory Configuration Service (RCS)** supports configuration of different types of electronic documents and reports by providing an enhanced version of Electronic Reporting designer with configuration repository as a standalone service. [Learn more.](https://aka.ms/rcs/overview)

- **Electronic Invoicing** brings together configurable formats for transformations, digital signatures, and configurable integrations for connectivity with external web services including certification and response handling. [Learn more.](https://microsoft-my.sharepoint.com/personal/janeaug_microsoft_com/Documents/Products/Regulatory services/Globalization svc/Electronic Invoicing Add-on for Dynamics 365 (general availability) - Dynamics 365 Release Plan | Microsoft Docs.md) 

- **Tax Calculation** provides enhanced flexibility through supporting multiple tax ID’s, tax code determination and tax calculation designer, plus runtime engine to comply with very complex tax regulations worldwide. [Learn more.](https://microsoft-my.sharepoint.com/personal/janeaug_microsoft_com/Documents/Products/Regulatory services/Globalization svc/Tax service (preview) - Dynamics 365 Release Plan | Microsoft Docs.md)

These globalization services provide out of the box integration with the Dynamics 365 online services in the table below:

|Online Service | Regulatory Configuration Service* | Electronic Invoicing  | Tax Calculation (Preview) |
|---------------|-----------------------------------|-----------------------|---------------------------|
| Dynamics 365 Finance | Yes | Yes | Yes | 
| Dynamics 365 Supply Chain Management | Yes | Yes | Yes | 
| Dynamics 365 Project Operations | Yes | Yes | Yes | 
| Dynamics 365 Commerce | Yes | N/A | N/A | 

______________________
*Configuring this service may result in the transfer of customer data outside of the selected Azure geographic location (geo) for the applicable Dynamics 365 online service due to different geo availability of the Regulatory Configuration Service. You can find more information [here.](https://aka.ms/rcs/D365Productavailabilityguide)
