---
# required metadata

title: Dynamics 365 Globalization services
description: This topic provides an overview of Dynamics 365 Globalization services.
author: JaneA07
manager: AnnBe
ms.date: 03/31/2021
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
# Dynamics 365 Globalization service

[!include [banner](../includes/banner.md)]

The following globalization services can be configured to extend the capabilities that exist in some Dynamics 365 online services:

   - **Regulatory Configuration Service (RCS)** supports the configuration of different types of electronic documents and reports. RCS provides an enhanced version of the Electronic Reporting designer with the configuration repository as a standalone service. For more information, see[Regulatory Configuration Service – simplified globalization feature management for globalization services](https://aka.ms/rcs/overview).
   - **Electronic Invoicing** brings together configurable formats for transformations, digital signatures, and configurable integrations for connectivity with external web services including certification and response handling. For more information, see [Electronic Invoicing Add-on for Dynamics 365](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/electronic-invoicing-add-on-dynamics-365-ga) 
   - **Tax Calculation** provides enhanced flexibility by supporting multiple tax IDs, tax code determination, the tax calculation designer, and a runtime engine to comply with complex tax regulations worldwide. For more information, see [Tax service](https://docs.microsoft.com/dynamics365-release-plan/2021wave1/finance-operations/dynamics365-finance/tax-service-preview).

These globalization services provide out-of-the-box integration with the following Dynamics 365 online services.

|Online service | Regulatory Configuration Service* | Electronic Invoicing  | Tax Calculation (Preview) |
|---------------|-----------------------------------|-----------------------|---------------------------|
| Dynamics 365 Finance | Yes | Yes | Yes | 
| Dynamics 365 Supply Chain Management | Yes | Yes | Yes | 
| Dynamics 365 Project Operations | Yes | Yes | Yes | 
| Dynamics 365 Commerce | Yes | N/A | N/A | 

______________________
*Configuring this service may result in the transfer of customer data outside of the selected Azure geographic location (geo) for the applicable Dynamics 365 online service. This is because of different geo availability of the Regulatory Configuration Service. For more information, see [Dynamics 365 and Power Platform:
Availability, data location, language, and localization](https://aka.ms/rcs/D365Productavailabilityguide)
