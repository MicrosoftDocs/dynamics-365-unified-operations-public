---
title: Dynamics 365 globalization services
description: This article provides an overview of Microsoft Dynamics 365 globalization services.
author: kfend
ms.date: 04/12/2021
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: AX 10.0.9
ms.collection: get-started
ms.assetid: 
ms.search.form: RCS, Regulatory Configuration Services, Localization, Electronic invoicing, Tax calculation
---
# Dynamics 365 globalization services

[!include [banner](../includes/banner.md)]

The following globalization services can be configured to extend the capabilities that exist in some Microsoft Dynamics 365 online services:

- **Regulatory Configuration Service (RCS)** supports the configuration of different types of electronic documents and reports. RCS provides an enhanced version of the Electronic reporting (ER) designer where the configuration repository is a standalone service. For more information, see [Regulatory Configuration Service](rcs-overview.md).
- **Electronic Invoicing** brings together configurable formats for transformations, digital signatures, and configurable integrations for connectivity with external web services, including certification and response handling. For more information, see [Electronic Invoicing](e-invoicing-service-overview.md).
- **Tax Calculation** provides enhanced flexibility by supporting multiple tax IDs, tax code determination, the tax calculation designer, and a runtime engine to comply with complex tax regulations worldwide. For more information, see [Tax Calculation](global-tax-calcuation-service-overview.md).

These globalization services provide out-of-box integration with the following Dynamics 365 online services.

| Online service | RCS | Electronic Invoicing | Tax Calculation (Preview) |
|----------------|-----|----------------------|---------------------------|
| Dynamics 365 Finance | Yes | Yes | Yes | 
| Dynamics 365 Supply Chain Management | Yes | Yes | Yes | 
| Dynamics 365 Project Operations | Yes | Yes | Not applicable | 
| Dynamics 365 Commerce | Yes | Not applicable | Not applicable | 

> [!NOTE]
> Because of differences in the availability of Azure geographic locations (geos) for RCS, configuration of this service might cause customer data to be transferred outside the geo that is selected for the applicable Dynamics 365 online service. For more information, see [Dynamics 365 and Power Platform: Availability, data location, language, and localization](https://aka.ms/rcs/D365Productavailabilityguide).
