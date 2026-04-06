---
title: Electronic Invoicing service FAQ
description: This article provides answers to frequently asked questions about Electronic invoicing, including questions about the importance of electronic invoicing.
author: ilikond
ms.author: ikondratenko
ms.topic: faq
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.custom: 
  - bap-template
---

# Electronic Invoicing service FAQ

[!INCLUDE[banner](../../includes/banner.md)]

This article provides answers to frequently asked questions about the Electronic Invoicing service. Electronic invoicing extends the electronic invoicing capabilities that exist in Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Project Operations.

## What's important about electronic invoicing, and why should it matter to my organization?

Operational complexity and risk intensify as organizations grow globally and expand their footprints across regions. Maintaining compliance and adapting to frequently changing regulations are growing challenges. These challenges are especially important for invoicing. Invoicing is traditionally expensive and prone to errors because companies rely on paper documents and manually intensive processes.

Organizations have begun to move away from paper invoices to help reduce cost and speed up the end-to-end process. Governments are increasingly turning to electronic invoicing as a key component of tax digitalization. By requiring that organizations digitally submit real-time tax information to tax authorities, governments can minimize tax evasion and manipulation, and reduce fraud. 

The world is shifting to paperless document processing. Customers that don't implement electronic invoicing might risk compliance issues and unnecessary costs. They might also risk lagging behind their competitors. 

## Don't Finance, Supply Chain Management, and Project Operations already include electronic invoicing functionality? What value does this functionality provide to me as a customer? 

Electronic invoicing extends the electronic invoicing capabilities that exist in Finance, Supply Chain Management, and Project Operations. Additionally, the functionality simplifies adherence to the newest electronic invoicing standards. It also provides coherent experiences for different geographies in electronic invoice processing and exchange. Electronic invoicing's capabilities unlock a range of benefits. Here are some examples: 

- Faster and easier adoption of country/region-specific requirements
- Standardization of e-invoicing solution implementations
- Enhanced traceability of e-invoice processing
- Easier maintenance to comply with changing legal requirements and local business practices
- Simplified solution packaging
- Scaling capabilities for a large volume of submitted documents, to achieve faster turnaround
- The ability to share your solutions with other companies

## Does the Electronic Invoicing service support on-premises installations of Finance, Supply Chain Management, and Project Operations?

No, the current platform doesn't support the on-premises versions, and there are no plans to support them in the future.

## Does the Electronic Invoicing service interface with the vendor import automation feature?

No. There are plans for this interface, but there's no timeline. When Microsoft plans a timeline, it announces the dates in the [Release plans](/dynamics365/release-plans/).

## How does the Electronic Invoicing service handle file attachments for an electronic invoice? Is a SharePoint server needed to embed PDF files into the XML file?

The Electronic Invoicing service handles files attached to an electronic invoice as embedded binary data in an XML element. You don't need a SharePoint server to embed PDF files. However, you must store the attachment in the Finance, Supply Chain Management, and Project Operations document management system.

## Is the Electronic Invoicing service available according to the regulations of my country/region?

The Electronic Invoicing service is a microservice platform that's globally available.

Microsoft plans to publish the electronic invoice formats and integrations for the countries/regions that are functionally localized by Microsoft. For more information, see [Availability of electronic invoicing features](e-invoicing-country-specific-availability.md).

If the electronic invoicing format for your country/region isn't listed, the platform aims to support this scenario in the future. You can still benefit from the configuration capabilities of Electronic invoicing and configure the electronic invoicing format by yourself. Alternatively, you can work with a partner or independent software vendor (ISV) to configure the electronic invoicing format for your organization. For more information, see [Electronic Invoicing service ISV last-mile connector](e-invoicing-isv-connector.md).

## Do I have to sign up to get the Electronic Invoicing service, or do I just have to turn it on in Feature management?

If you have a license for Finance, Supply Chain Management, and Project Operations, see [Get started with Electronic invoicing add-on service administration](../e-invoicing-get-started-service-administration.md) to sign up for Electronic invoicing.

## Does the Electronic Invoicing service work with Tier 1 virtual machines? What's the minimal required environment?

Integration with the Electronic Invoicing service requires at least a Tier 2 virtual machine to host Finance or Supply Chain Management. For more information about environment planning, see [Environment planning](../../../fin-ops-core/dev-itpro/organization-administration/environment-planning.md).

## Does the Electronic Invoicing service have a test mode for testing invoice submission?

You can achieve testing through configuration. To test invoice submission, you can connect to Finance or Supply Chain Management from a user acceptance testing (UAT) environment and submit the test invoices. Electronic invoicing supports the configuration of test digital certificates. For e-invoices that require digital approval, it also supports the setup of a URL from test web services that the tax authorities publish.

## Does the Electronic Invoicing service enable a legal entity in Finance or Supply Chain Management that's configured for a specific country/region to consume electronic invoicing features from different countries/regions?

Yes. You can use the electronic invoicing features to process business document submissions independently of the country/region of the legal entity. However, the following conditions must be met:

- The business document that's generated uses the appropriate document model mapping.
- There's a match between the business document and applicability rules that are configured in the electronic invoicing feature.

## Does the Electronic Invoicing service use the same configuration and design experience that the Electronic reporting module in Finance and Supply Chain Management provides?

Yes. The same designer tools that the **Electronic reporting** (ER) module in Finance and Supply Chain Management uses are used to create and configure data model mapping and file format configurations.

## Can I extend and configure the applicability rules so that they aren't tied to any specific parameter, such as a legal entity?

Yes. You can fully configure the applicability rules. You can add or remove clauses, build logic operations, and group and ungroup clauses.

## Does the Electronic Invoicing service support adding other ER format configurations to generate other types of documents? Does it support electronically sending these documents to customers as delivery notes, for example?

You can use other ER format configurations to produce the desired output files. However, to generate business documents, the ER format configuration must be derived from the same ER invoice model mapping that's configured in Finance or Supply Chain Management. Out of the box, electronic invoicing doesn't support sending the output file directly to the customer as an electronic data interchange (EDI) transaction.

## Does the Electronic Invoicing service support exchanging electronic invoices with customers? Does it support configuring different invoice formats for the same invoice?

The capability to receive and import vendor electronic invoices is on the roadmap. However, the capability to automatically send electronic invoices to customers isn't currently supported.

## Does the Electronic Invoicing service support exchanging EDI messages with other companies?

The Electronic Invoicing service focuses on exchanging electronic invoice message types, driven by regulatory compliance requirements. The capability to receive and import vendor electronic invoices is on the roadmap. However, the capability to send electronic invoice files to customers isn't currently supported, except in scenarios where the electronic invoice must be sent to the customer as a regulatory requirement.

## Does the Electronic Invoicing service support importing or merging customizations that are made in the ER format configurations from the legacy Electronic invoicing feature?

You can reuse ER format configurations in the Electronic Invoicing service. However, the ER format configuration must come from the same ER invoice model mapping that the Electronic invoicing feature was designed to use. Finance or Supply Chain Management uses this mapping to generate the business documents.

## Does the Electronic Invoicing service support issuing electronic invoices from custom-made tables? If so, how do I create the ER data model configurations for these new tables and entities?

Yes, you can issue electronic invoices from custom-made tables. However, you must customize the invoice model mapping and add the required references to the custom-made tables. Alternatively, depending on the complexity, you must create a new invoice model mapping.

## Does the Electronic Invoicing service support different web service endpoints?

Yes, Electronic Invoicing supports different web service endpoints. You can use configurable integration with REST web services or several parametrized country/region-specific web service integrations. You can configure different endpoints for the same web services and APIs by using different versions of configurations. For more information, see [List of parameters by action](../e-invoicing-setup.md#list-of-parameters-by-action).

## Is Electronic invoicing integrated with the APIs of the various invoice operators from the Nordic countries/regions, or should this integration be handled on a case-by-case basis?

Microsoft continuously extends functional coverage to provide out-of-box integrations by using the Electronic invoicing features. For more information about the formats and integrations that are supported, see [Availability of electronic invoicing features](e-invoicing-country-specific-availability.md) and [Electronic Invoicing service ISV last-mile connector](e-invoicing-isv-connector.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
