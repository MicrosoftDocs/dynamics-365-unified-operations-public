---
title: Electronic invoicing overview
description: This article provides an overview of Electronic invoicing in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
ms.date: 01/21/2022
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12
ms.collection: get-started
ms.assetid: 
ms.search.form: 
---

# Electronic invoicing overview

[!include [banner](../includes/banner.md)]

Electronic invoicing for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management is a hyper-scalable multitenant service that enables configurable processing of electronic invoices and configurable electronic document exchange. The processing and integration rules are fully configurable, and the logic is run outside Finance and Supply Chain Management. The service is targeted mainly at processing of electronic invoice documents in business-to-government scenarios. However, it can be custom configured for other purposes, such as business-to-business scenarios for different types of the documents.

Electronic invoicing can help you achieve the following goals:

- Fast and easy adoption of country/region-specific requirements
- Standardized implementations of an Electronic invoicing solution
- Enhanced traceability of document history
- Shorter implementation cycle
- Reduced total cost of ownership (TCO)
- Easily adjustable configurations that don't require code changes
- Simplified configuration packaging
- Built-in export, import, and integration, and easy extensibility in the processing of electronic invoice documents
- Easy reuse of the same export, import, and integration configurations across companies

## Service availability

Currently, Electronic invoicing functionality is available for Finance and Supply Chain Management customers. For more information, review the license terms and conditions for your application.

Because functionality that addresses country/region-specific requirements might be limited at different phases of the release, you should always review the most up-to-date documentation that highlights the coverage and scope of supported country/region-specific solutions.

Electronic invoicing is deployed in the following Azure geographies:

- United States
- Europe
- United Kingdom
- Asia
- Japan
- Switzerland
- Brazil
- United Arab Emirates
- Australia
- Canada
- France
- India
- Norway
- South Africa

> [!NOTE]
> Electronic invoicing doesn't support on-premises deployments.

## Feature highlights

- Out-of-box integration with Finance and Supply Chain Management
- A consistent user experience for the configuration and monitoring of the electronic invoice process for all countries and regions
- Faster, easier, and less expensive adoption of Electronic invoicing solutions in new countries or regions
- Configuration of the service through the setup of Regulatory Configuration Service (RCS) and Globalization features
- Transformation of business data into multiple electronic invoice formats (XML, JavaScript Object Notation \[JSON\], TXT, and comma-separated values \[CSV\]) by using configurations that are defined in RCS:

    - Electronic reporting (ER) formats that are available for countries and regions where configurability for electronic invoice transformation isn't available

- Configurable submission of electronic invoices to external web services, including certification handling through digital signatures:

    - Built-in, easily extendable, and configurable integration with additional content for several countries and regions

- Handling of responses from web services, including configurable handling of exception messages
- Support for electronic signatures (for example, electronic signatures that use the XMLDSig signing algorithm)
- The capability to sending documents to emails and store them in SharePoint
- Batch processing of electronic invoice messages
- Configurable transformation of incoming documents, and processing of those documents in Finance and Supply Chain Management
- The capability to receive incoming documents from channels such as email and SharePoint

## Privacy notice

Enabling and using Electronic invoicing might require that limited data be sent. This data includes the organization's tax registration ID. This data will be transmitted to third-party agencies that are authorized by the tax authorities for the purpose of sending electronic invoices in the predefined formats required for integration with government web services. Data that is imported from these external systems into this Dynamics 365 online service is subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). For more information, see the "Privacy notice" section in country/region-specific feature documentation.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
