---
title: Electronic invoicing FAQ
description: This article provides information about frequently asked questions regarding Electronic invoicing.
author: gionoder
ms.date: 04/21/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.17
ms.assetid: 
ms.search.form: 
---

# Electronic Invoicing FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about Electronic Invoicing service. Electronic invoicing extends the electronic invoicing capabilities that exist in Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Project Operations. 

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

Microsoft plans to publish the electronic invoice formats and integrations for the countries/regions that are functionally localized by Microsoft. For more information, see [Availability of electronic invoicing features](e-invoicing-configuration-rcs.md#availability-of-electronic-invoicing-features).

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

## Is there any documentation about the out-of-box country/region-specific Electronic Invoicing features?

Yes. For information about the availability of Electronic Invoicing features and the formats they support, see [Availability of electronic invoicing features](e-invoicing-configuration-rcs.md#availability-of-electronic-invoicing-features).

## Does the Electronic Invoicing service allow a legal entity in Finance or Supply Chain Management that is configured for a specific country to consume electronic invoicing features from different country/regions?

Yes. The electronic invoicing features can be consumed to process business document submissions independent from the country/region of the legal entity, if the following is true:

   - The business document being generated uses the appropriate document model mapping.
   - There's a match between the business document and applicability rules configured in the electronic invoicing feature.

## Does the Electronic Invoicing service use the same configuration and design experience provided by the Electronic reporting module in Finance and Supply Chain Management? 

Yes. The same designer tools that are used in the Electronic reporting (ER) module in Finance and Supply Chain Management are used to create and configure data model mapping and file format configurations. These designer tools are also used in Regulatory Configuration Services (RCS) to create and configure Data model mapping and file format configurations that are used in the configuration of the e-invoicing features.

## Can the applicability rules be extended and configured so that they aren't tied to any specific parameter, such as a legal entity?

Yes. The applicability rules are fully configurable. You can add or remove clauses, build logic operations, and group and ungroup clauses. For more information, see [Applicability rules](e-invoicing-configuration-rcs.md?toc=/dynamics365/finance/toc.json#applicability-rules).

## Does the Electronic Invoicing service support adding other ER format configurations to generate other types of documents? Does it support sending the documents electronically to customers, such as a delivery note?

You can use other ER format configurations to produce the desired output files. However, the ER format configuration must be derived from the same ER invoice model mapping that is configured in Finance or Supply Chain Management to generate business documents. Sending the output file directly to the customer as an EDI transaction, isn't supported out-of-the-box by Electronic Invoicing.

## Does the Electronic Invoicing service support exchanging electronic invoices with customers? Does it support configuring different invoice formats for the same invoice?

The capability of receiving and importing vendor electronic invoices is on the roadmap, but automatically sending the electronic invoices to customers isn't currently supported.

## Does the Electronic Invoicing service extend to support exchanging EDI messages with other companies?

The focus of the Electronic Invoicing service is to exchange electronic invoice message types driven by regulatory compliance requirements. Receiving and importing vendor electronic invoices is on the roadmap, but the sending of electronic invoice files to the customers isn't currently supported out-of-the-box, except in scenarios where sending the electronic invoice to the customer is a regulatory requirement.

## Does the Electronic Invoicing service support importing or merging customizations made in the ER format configurations from the legacy Electronic invoicing feature?

You can reuse ER format configurations in the Electronic Invoicing service. However, the ER format configuration must be derived from the same ER invoice model mapping the electronic invoice feature was designed to use, and which is configured in Finance or Supply Chain Management to generate the business documents.

## Does the Electronic Invoicing service support issuing electronic invoices from custom-made tables? If so, how do you create the ER data model configurations for these new tables and entities?

Yes. However, it requires customizing the invoice model mapping and adding the necessary references to the custom-made tables, or depending on the complexity, creating a new invoice model mapping.

## Does the Electronic Invoicing service support different web-service endpoints?

Electronic Invoicing supports different web-services end points. You can use configurable integration with REST web services or a number of parametrized country/region-specific web service integrations. Different endpoints can be configured for the same web-services and APIs using different versions of configurations. For more information, see [List of parameters by action](e-invoicing-setup.md#list-of-parameters-by-action).

## Is Electronic Invoicing integrated with the various invoice operators' APIs from the Nordic countries/regions, or should that be handled on a case-by-case basis?

Microsoft continuously extends functional coverage to provide out-of-the box integrations by using the electronic invoicing features. For more information about the formats and integrations that are supported, see [Availability of electronic invoicing features](e-invoicing-configuration-rcs.md?toc=/dynamics365/finance/toc.json#availability-of-electronic-invoicing-features).

> [!NOTE] 
> If you didn't find the answer you are looking for, email your question to the Product Development Team at <D365EInvoicePreview@microsoft.com>. We will either contact you or improve the coverage of this FAQ.
