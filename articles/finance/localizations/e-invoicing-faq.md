---
# required metadata

title: Electronic invoicing FAQ
description: This topic provides information about frequently asked questions regarding Electronic invoicing.
author: gionoder
ms.date: 03/17/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
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
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.17

---

# Electronic Invoicing FAQ

[!include [banner](../includes/banner.md)]

This topic provides answers to frequently asked questions about Electronic Invoicing service. Electronic invoicing extends the electronic invoicing capabilities that exist in Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Project Operations. 

## What is important about electronic invoicing and why should it matter to my organization?

Operational complexity and risk continue to intensify as organizations grow globally and expand their footprints across regions. Maintaining compliance and adapting to frequently changing regulations is a growing challenge and is of particular importance when it comes to invoicing. Invoicing has traditionally been expensive and prone to errors as companies rely on paper documents and manually intensive processes.  

Organizations have begun to move away from paper invoices to reduce cost and speed up the end-to-end process. Governments are increasingly turning to electronic invoicing as a key component of tax digitalization. By requiring organizations to digitally submit real-time tax information to tax authorities, governments can minimize tax evasion and manipulation, and reduce fraud. 

The world is shifting to paperless document processing and without implementing electronic invoicing, customers may risk compliance issues, unnecessary costs, and lag behind competitors. 

## Doesn't Finance, Supply Chain Management, and Project Operations already include electronic invoicing functionality? What value does this provide to me as a customer? 

Electronic Invoicing extends the electronic invoicing capabilities that exist in Finance, Supply Chain Management, and Project Operations. The functionality also simplifies adherence to the newest electronic invoicing standards and provides coherent experiences for different geographies in electronic invoice processing and exchange. Electronic invoicing's capabilities unlock an array of benefits including: 

   - Faster and easier adoption to country/region specific requirements.
   - Standardization of e-invoicing solution implementations. 
   - Enhanced e-invoice processing traceability.  
   - Easier maintenance to comply with changing legal requirements and local business practices. 
   - Simplified solution packaging.
   - Scaling capabilities for a large volume of submitted documents that results in faster turnaround.
   - Ability to share your solutions with other companies.

## Does Electronic Invoicing service support the on-premises installations of Finance, Supply Chain Management, and Project Operations? 

The current platform doesn't allow the use the on-premises version and there are no plans to support it in the future.

## Does Electronic Invoicing service interface with the vendor import automation feature?

No. There are plans for this interface, but there is no planned timeline. When planned, the dates will be announced in the [Release plans](/dynamics365/release-plans/).

## How does Electronic Invoicing service handle file attachments into the electronic invoice? Is a SharePoint server needed when embedding PDF files into the XML file?

The files attached to the electronic invoice are handled as embedded binary data in an XML element. A SharePoint server isn't needed to embed PDF files, but the attachment must be stored in the Finance, Supply Chain Management, and Project Operations document management system.

## Is Electronic Invoicing service available according to the regulations of my country/region?

Electronic Invoicing service is a microservice platform that will be globally available.

Microsoft plans to publish the electronic invoice formats and integrations for the countries that are functionally localized by Microsoft. For more information, see [Availability of electronic invoicing features](e-invoicing-configuration-rcs.md#availability-of-electronic-invoicing-features).

If the electronic invoicing format for your country/region isn't listed, the platform aims to support this scenario in the future. You can still benefit from the configuration capabilities Electronic invoicing has, and configure the electronic invoicing format by yourself, or you can work with a partner/ISV to configure those for your organization.

## Is Dynamics 365 for Regulatory Services a new module like Human Resources or Project Operations that is linked to Finance or Supply Chain Management? Are there extra costs for that?

The Dynamics 365 for Regulatory Services (RCS) is a cloud service for configuring Globalization resources. RCS is free for all Finance, Supply Chain Management, and Project Operations license holders.

For RCS sign-up, go to <https://marketing.configure.global.dynamics.com/>.

For more information, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).

## Do I need to sign up to get Electronic Invoicing service, or just turn it on in Feature Management?

If you are have a license for Finance, Supply Chain Management, and Project Operations, see [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md) to sign up for Electronic invoicing.

## Does Electronic Invoicing service work with Tier 1 virtual machines? What is the minimal required environment?

Integration with Electronic Invoicing service requires at least a Tier 2 virtual machine to host Finance or Supply Chain Management. For more information about environment planning, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).

## Does Electronic Invoicing service have a test mode for testing invoice submission?

This can be achieved by configuration. To test invoice submission, you can connect to Finance or Supply Chain Management from a User Acceptance Test (UAT) environment and submit the test invoices. Electronic invoicing supports configuring test digital certificates, and in the case of e-invoices requiring digital approval, the setup of a URL from test web services published by the tax authorities.

## Is there any documentation about the out-of-box country-specific Electronic Invoicing features?

Yes. For information about the availability of Electronic Invoicing features and the formats they support, see [Availability of electronic invoicing features](e-invoicing-configuration-rcs.md#availability-of-electronic-invoicing-features).

## Does the Electronic Invoicing service allow a same Legal entity in Dynamics 365 Finance or Supply Chain Management, configured to a specific country, consume electronic invoicing features from different country/regions?

Yes, it does. The electronic invoicing features can be consumed to process business document submissions independent from the country of the Legal entity, as long the business document be generated using the appropriated document model mapping and there is a match between the business document and applicability rules configured in the electronic invoicing feature.

## Does the Electronic Invoicing service use the same configuration/design experience provided by the Electronic reporting module in Dynamics 365 Finance and Supply Chain Management? 

Yes, it does. The same Designer tools used in Dynamics 365 Finance and Supply Chain Management, in the Electronic reporting module, used to create and configure since data model mapping until file format configurations, are also used in the Regulatory Configuration Services (RCS) to create and configure Data model mapping and file format configurations that are later across the configuration of the e-invoicing features.

## Are the Applicability rules extensible and configurable, so that they do not get tied to any specific parameter, such as a legal entity?

Yes, they are. The applicability rules are fully configurable, you can add or remove clauses, build logic operations and group/ungroup clauses. For more information, see [Applicability rules](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs?toc=/dynamics365/finance/toc.json#applicability-rules).

## Does the Electronic Invoicing service support add others ER format configurations for generation of other types of documents? Does it support sending them electronically to the customers, such as a delivery note?

You can use others ER format configuration to produce the desired output files, but the ER format configuration must be derived from the same ER invoice model mapping, configured in the Finance or Supply Chain Management, for generation of the business documents. Sending the output file directly to the customer, as an EDI transaction, is not currently supported out-of-box by Electronic Invoicing.

## Does the Electronic Invoicing service support exchange of electronic invoices with the customers? Does it support configuration of different invoice formats for the same invoice?

The capability of receiving and importing vendor electronic invoices is on the roadmap, but automatically sending the electronic invoices to customers is not currently supported.

## Does the Electronic Invoicing service extend to support exchanging of EDI messages with other companies?

The focus of Electronic Invoicing service is exchange electronic invoices message types driven by regulatory compliance requirements. Receiving and importing vendor electronic invoices is also on the roadmap, but the sending of electronic invoice files to the customers is not currently supported out-of-box, except in the scenarios where sending the electronic invoice to the customers is a regulatory requirement.

## Does the Electronic Invoicing service support importing or merging customizations made in the ER format configurations from the legacy Electronic invoicing feature?

You can reuse ER format configurations in the Electronic Invoicing service, but the ER format configuration must be derived from the same ER invoice model mapping the electronic invoice feature was designed to use, and which is configured in the Finance or Supply Chain Management, for generation of the business documents.

## Does the Electronic Invoicing service support issue of electronic invoices from custom-made tables? If so, then how to create the ER data model configurations for these new tables/entities?

Yes, it does, but in this case, it will require either customizing the invoice model mapping adding the necessary references to the custom-made tables, or depending on the complexity, creation of an entire new invoice model mapping.

## Does the Electronic Invoicing service support different web-services endpoints?

Electronic Invoicing supports different web-services end points. You can use configurable integration with REST web services or a number of parametrized country-specific web service integrations. It is possible to configure different endpoints for the same web-services and APIs using different versions of configurations. To learn more, go to <https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-setup#list-of-parameters-by-action>

## Is the Electronic Invoicing out-of-the-box integrated with the various invoice operators' APIs from the Nordic countries, or is that something that must be handled on a case-by-case basis?

Microsoft continuously extends functional coverage to provide out-of-the box integrations via electronic invoicing features. For more information, please see the [Availability of electronic invoicing features](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs?toc=/dynamics365/finance/toc.json#availability-of-electronic-invoicing-features) with formats and integrations for the most up to date information what integrations are supported.

> [!NOTE] 
> If you didn't find the answer you are looking for, email your question to the Product Development Team at <D365EInvoicePreview@microsoft.com>. We will either contact you or improve the coverage of this FAQ.
