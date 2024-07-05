---
title: Electronic Invoicing service overview
description: Learn about Electronic invoicing in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management, including an overview on service availability.
author: ilikond
ms.author: ikondratenko
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 06/17/2024
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form:
ms.dyn365.ops.version: 10.0.39
---

# Electronic Invoicing service overview

[!INCLUDE[banner](../../includes/banner.md)]

Electronic invoicing for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management is a hyper-scalable multitenant service that enables configurable processing of electronic invoices and configurable electronic documents exchange. The processing and integration rules are fully configurable, and the logic is run outside Finance and Supply Chain Management. The service is targeted mainly at processing electronic invoices in various scenarios. However, it can be configured for other scenarios for different types of documents.

Electronic invoicing can help you achieve the following goals:

- Fast and easy adoption of country/region-specific requirements
- Standardized implementations of an Electronic invoicing solution
- Enhanced traceability of document history
- A shorter implementation cycle
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
- Configuration of the service through the setup of Globalization features in the [Globalization Studio workspace](workspace/merge-rcs-to-gsw.md)
- Transformation of business data into multiple electronic invoice formats (XML, JSON, TXT, and CSV) by using [Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) (ER) format configurations
- Configurable submission of electronic invoices to external web services, including certification handling through digital signatures
- Handling of responses from web services, including configurable handling of exception messages
- Support for electronic signatures (for example, electronic signatures that use the XMLDSig signing algorithm)
- The capability to send documents to emails and store them in SharePoint
- Batch processing of electronic invoice messages
- Configurable transformation of incoming documents and processing of those documents in Finance and Supply Chain Management
- The capability to receive incoming documents from channels such as email and SharePoint

## Privacy notice

Enabling and using Electronic invoicing might require that limited data be sent. This data includes the organization's tax registration ID. This data will be transmitted to third-party agencies that are authorized by the tax authorities for the purpose of sending electronic invoices in the predefined formats required for integration with government web services. Data that's imported from these external systems into this Dynamics 365 online service is subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). For more information, see the "Privacy notice" section in country/region-specific feature documentation.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
