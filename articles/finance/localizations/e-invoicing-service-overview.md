---
# required metadata

title: Electronic invoicing overview
description: This topic provides information about Electronic invoicing in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
ms.date: 01/21/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata
---

# Electronic invoicing overview

[!include [banner](../includes/banner.md)]

Electronic invoicing for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management is a hyper-scalable multitenant service that enables configurable processing of electronic invoices and configurable electronic document exchange. The processing and integration rules are fully configurable, and the logic is run outside Finance and Supply Chain Management. The service is targeted mainly at e-invoice processing in business-to-government scenarios, but it can be custom-configured for other purposes including business-to-business scenarios of different types of the documents.

Electronic invoicing can help you achieve the following goals:
  - Fast and easy adoption of country/region-specific requirements
  - Standardized implementations of an Electronic invoicing solution
  - Enhanced traceability of document history
  - Shorter implementation cycle
  - Reduced total cost of ownership (TCO)
  - Easily adjustable configurations that don't required code changes
  - Simplified configuration packaging
  - Built-in export, import, and integration, and easy extensibility in the processing of e-invoice documents
  - Easy reuse of the same export, import, and integration configurations across companies


## Service availability
Currently, Electronic invoicing functionality is available for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management customers. 
Please check license terms and conditions for the details.
Because functionality that addresses country/region-specific requirements might be limited at different phases of the release, you should always check the most up-to-date documentation that highlights the coverage and scope of supported country/region-specific solutions.
Electronic invoicing is deployed in the following Azure geographies:
  - United States
  - Europe
  - Asia

> [!NOTE]
> Electronic invoicing doesn't support on-premises deployments.


## Feature highlights
  - Out-of-box integration with Finance and Supply Chain management
  - Consistent user experience for the configuration and monitoring of the e-invoice process for all countries or regions
  - Faster, easier, and less expensive adoption of Electronic invoicing solutions in new countries or regions
  - Configuration of the service through the Regulatory Configuration Service (RCS) and Globalization feature setup
  - Transformation of business data into multiple e-invoice formats (XML, JavaScript Object Notation [JSON], TXT, and comma-separated values [CSV]) by using configurations that are defined in RCS:
    - Electronic reporting formats that are available for countries or regions where configurability for e-invoice transformation isn't available
  - Configurable submission of e-invoices to external web services, including certification handling through digital signatures:
    - Built-in, easily extendable, and configurable integration with additional content for several countries
  - Handling of responses from web services, including configurable exception message handling
  - Support for electronic signatures (for example, by using the XMLDSig signing algorithm)
  - Sending documents to e-mails and store them in Sharepoint
  - Batch processing of e-invoice messages
  - Configurable transformation of incoming documents and processing them in Finance and Supply Chain management
  - Receiving incoming documents from channels:
    - e-mail
    - Sharepoint


## Privacy notice
Enabling and using Electronic invoicing may require sending limited data, which includes the organization tax registration ID. This will be transmitted to third-party agencies authorized by the tax authorities for purposes of sending electronic invoices in the predefined formats required for integration with these government’s web services. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
