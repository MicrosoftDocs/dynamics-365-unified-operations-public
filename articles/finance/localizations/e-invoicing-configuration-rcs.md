---
# required metadata

title: Configure Electronic invoicing in Regulatory Configuration Services (RCS)
description: This topic explains how to configure Electronic invoicing in Dynamics 365 Regulatory Configuration Services (RCS). 
author: gionoder
ms.date: 11/08/2021
ms.topic: article
ms.prod: 
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
ms.dyn365.ops.version: AX 10.0.12

---

# Configure Electronic invoicing in Regulatory Configuration Services (RCS)

[!include [banner](../includes/banner.md)]

This topic provides information about the configuration capabilities of Electronic invoicing in Dynamics 365 Regulatory Configuration Services (RCS).

It is through the configuration capabilities that Electronic invoicing helps you meet business and regulatory requirements of electronic invoices without having to do any coding. And in the scenarios where electronic invoices must be electronically approved by a web service, the configuration capabilities also help you meet the requirements for exchanging messages with a web service, without doing any code.

## Electronic reporting

Electronic reporting (ER) supports Electronic invoicing.

The data model mapping and formats are configurable components that are created and maintained through ER and used in Electronic invoicing. The ER format designer is the tool for creating and maintaining file formats. It's used to configure the electronic invoicing features.

For more information, see [Electronic reporting (ER) overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

## Electronic invoicing features

The electronic invoicing features are responsible for generating electronic invoices through Electronic invoicing. They encapsulate the configuration rules and use them to process the data that Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management send to Electronic invoicing and to electronic invoices.

The features also support scenarios where compliance with file format specifications is required and the output is a standalone electronic file. In most cases, the file format specifications are published by the tax authority.

Finally, the features support the exchange of messages with external web services that are hosted either by the tax authority or by some accredited party, and requests for authorization or an approval stamp in the electronic invoice.

## Availability of electronic invoicing features

Availability of the electronic invoicing features depends on the country or region. Although some features are generally available, others are in preview.

### Generally available features

The following table shows the electronic invoicing features that are generally available.

| Country/region | Feature name                         | Business document |
|----------------|--------------------------------------|-------------------|
| Austria        | Austrian electronic invoices (AT)    | Sales invoices and project invoices |
| Belgium        | Belgian electronic invoice (BE)      | Sales invoices and project invoices |
| Brazil         | Brazilian NF-e (BR)                  | Fiscal document model 55, correction letters, cancellations, and discards |
| Brazil         | Brazilian NFS-e ABRASF Curitiba (BR) | Service fiscal documents |
| Brazil         | Brazilian NF-e import from e-mail (BR) | Fiscal document model 55 |
| Denmark        | Danish electronic invoice (DK)       | Sales invoices and project invoices |
| Egypt          | Egyptian electronic invoice (EG)     | Sales invoices and project invoices |
| Estonia        | Estonian electronic invoice (EE)     | Sales invoices and project invoices |
| Finland        | Finnish electronic invoice (FI)      | Sales invoices and project invoices |
| France         | French electronic invoice (FR)       | Sales invoices and project invoices |
| Germany        | German electronic invoice (DE)       | Sales invoices and project invoices |
| Italy          | FatturaPA (IT)                       | Sales invoices and project invoices |
| Netherlands    | Dutch electronic invoice (NL)        | Sales invoices and project invoices |
| Norway         | Norwegian electronic invoice (NO)    | Sales invoices and project invoices |
| Spain          | Spanish electronic invoice (ES)      | Sales invoices and project invoices |
| Europe         | PEPPOL electronic invoice            | PEPPOL sales invoices and project invoices |
| Europe         | PEPPOL vendor invoice                | PEPPOL import vendor invoices |
| Saudi Arabia   | Saudi Arabian electronic invoice (SA)| Sales invoices and project invoices |

### Preview features

The following table shows the electronic invoicing features that are currently in preview.

| Country/region | Feature name                         | Business document |
|----------------|--------------------------------------|-------------------|
| Mexico         | Mexican CFDI (MX)                    | Sales invoices, packing slips, inventory transfers, payment complements, and cancellations |

### Configurable components of electronic invoicing features

The electronic invoicing features consist of the following groups of configurable components:

- **Formats**: Formats let you configure what Electronic invoicing must generate when an electronic document becomes an electronic invoice. Formats include the format configuration for the electronic invoice, and for files and messages that are used to submit requests and receive responses when communication with an external web service is required.
- **Actions**: Actions let you configure how Electronic invoicing generates the transformation of an electronic document that Finance and Supply Chain Management submitted into an electronic invoice.
- **Applicability rules**: Applicability rules let you configure the context that Electronic invoicing must consider to process an electronic invoicing feature.
- **Variables**: Variables let you configure the support for the construction of the configuration logic. Variables can work as the input of values to perform a specific action. Alternatively, they can work as an exchange of values between Finance and Supply Chain Management and Electronic invoicing.
- **Electronic document model mapping**: The electronic document model mapping lets you configure the ER model mapping. The model mapping defines the data mapping of the abstract invoice that is integrated into Electronic invoicing when electronic documents are submitted.
- **Invoice context model**: The invoice context model lets you configure the ER invoice context model and define the context of an electronic invoicing feature.
- **Response types**: Response types let you configure what Electronic invoicing must update in Finance and Supply Chain Management as a result of the electronic invoice processing.

### Formats

The following lists show the ER format configurations that are available for the electronic invoicing features.

#### Austrian (AT) electronic invoices: Sales and project invoices for Austria

- OIOUBL Sales invoice
- OIOUBL Project invoice
- OIOUBL Sales credit note
- OIOUBL Project credit note

#### Belgian (BE) electronic invoice: Sales and project invoices for Belgium

- UBL Sales invoice BE
- UBL Project invoice BE
- UBL Project credit note BE
- UBL Sales credit note BE

#### Brazilian (BR) NF-e: NF-e Federal (Brazil)

- NF-e submit export format (BR)
- NF-e correction letter export format (BR)
- NF-e cancel export format (BR)
- NF-e discard export format (BR)

#### Brazilian NFS-e (BR): NFS-e ABRASF Curitiba city

- NFS-e ABRASF Curitiba (BR)
- NFS-e ABRASF Inquire Curitiba (BR)

#### Danish (DK) electronic invoice: Sales and project invoices for Denmark

- OIOUBL Sales invoice
- OIOUBL Project invoice
- OIOUBL Sales credit note
- OIOUBL Project credit note

#### Dutch (NL) electronic invoice: Sales and project invoices for Netherlands

- UBL Sales invoice NL
- UBL Project invoice NL
- UBL Project credit note NL
- UBL Sales credit note NL

#### Egyptian (EG) electronic invoice: Sales and project invoices for Egypt

- Sales invoice (EG)(Invoicing)
- Project invoice (EG)(Invoicing)

#### Estonian (EE) electronic invoice: Sales and project invoices for Estonia

- Sales invoice (EE)
- Project invoice (EE)

#### Finnish (FI) electronic invoice: Sales and project invoices for Finland

- Sales invoice (FI)
- Project invoice (FI)

#### French (FR) electronic invoice: Sales and project invoices for France

- UBL Sales invoice FR
- UBL Project invoice FR
- UBL Project credit note FR
- UBL Sales credit note FR

#### German (DE) electronic invoice: Sales and project invoices for Germany

- Sales invoice (DE)
- Project invoice (DE)

#### Italian (IT) electronic invoice: Sales and project invoices for Italy

- Sales invoice (IT)
- Project invoice (IT)

#### Mexican (MX) CFDI: CFDI for Mexico

- CFDI invoice format (MX)
- CFDI Packing slip (MX)
- CFDI Inventory transfer (MX)
- CFDI payment format (MX)
- CFDI invoice cancel format (MX)

#### Norwegian (NO) electronic invoice: Sales and project invoices for Norway

- OIOUBL Sales invoice
- OIOUBL Project invoice
- OIOUBL Sales credit note
- OIOUBL Project credit note

#### PEPPOL electronic invoice: PEPPOL sales and project invoices

- PEPPOL Sales invoice
- PEPPOL Project invoice
- PEPPOL Sales credit note
- PEPPOL Project credit note

#### Spanish (ES) electronic invoice: Sales and project invoices for Spain

- Sales invoice (ES)
- Project invoice (ES)

#### Saudi Arabian (SA) electronic invoice: Sales and project invoices for Saudi Arabia

- Sales e-invoice (SA)
- Project e-invoice (SA)

In addition to the ER format configurations that are available out of the box to use with the Electronic Invoicing service, you can also create your own ER format configurations. However, the format configurations that are created to use with Electronic Invoicing features don't support direct reference to Finance or Supply Chain Management tables or any of the corresponding metadata. Only references to the ER model mapping are supported.

### Actions

The following table lists the available actions, and whether they are currently generally available or still in preview.

| Action                                        | Description                                                                  | Availability         |
|-----------------------------------------------|------------------------------------------------------------------------------|----------------------|
| Transform document                            | Run Electronic Reporting format to transform the document.                   | Generally available  |
| Sign xml document                             | Sign xml documents with digital signature.                                   | Generally available  |
| Sign json document for Egyptian Tax Authority | Sign json documents with digital signature for Egyptian Tax Authority.       | Generally available  |
| Integrate with Egyptian ETA service           | Communicate with Egyptian Tax Authority.                                     | Generally available  |
| Call Brazilian SEFAZ Service                  | Integrate with Brazilian SEFAZ service for fiscal document submission.       | Generally available  |
| Call Mexican PAC Service                      | Integrate with Mexican PAC service for CFDI submission.                      | In preview           |
| Process response                              | Analyze the response received from the web service call.                     | Generally available  |
| Use MS Power Automate                         | Integrate with flow built in Microsoft Power Automate.                       | In preview           |

### Applicability rules

Applicability rules are configurable clauses that are defined at the Electronic invoicing feature level. The rules are configured to provide a context for execution of electronic invoicing features through the Electronic Invoicing capability set.

When a business document from Finance or Supply Chain Management is submitted to electronic invoicing, the business document doesn't carry an explicit reference that allows the Electronic Invoicing capability set to call a particular electronic invoicing feature to process the submission.

Nevertheless, when properly configured, the business document contains the necessary elements that allow electronic invoicing to resolve which electronic invoicing feature must be selected and then generate the electronic invoice.

Applicability rules allow the Electronic Invoicing capability set to find the exact electronic invoicing features that must be used to process the submission. This is done by matching the contents from the submitted business document with the clauses from the Applicability rules.

For example, two electronic invoicing features with related Applicability rules are deployed into the Electronic Invoicing capability set.

| Electronic invoicing feature | Applicability rules        |
|------------------------------|--------------------------- |
| A                            | <p>Country = BR</p><p>and</p><p>Legal entity = BRMF</p>  |
| B                            | <p>Country = MX</p><p>and</p><p>Legal entity = MXMF</p>  |

If a business document from Finance or Supply Chain Management is submitted to the Electronic Invoicing capability set, the business document contains the following attributes filled as:

- Country = BR
- Legal entity = BRMF

The Electronic Invoicing capability set will select the electronic invoicing feature **A** to process the submission and generate the electronic invoice.

In the same way, if the business document contains:

- Country = MX
- Legal entity = MXMF

Electronic invoicing feature **B** is selected to generate the electronic invoice.

The configuration of Applicability rules can't be ambiguous. This means that two or more electronic invoicing features can't have the same clauses, otherwise it will lead to no selection. If there is a duplication of electronic invoicing features, to avoid ambiguity, use additional clauses to allow the Electronic Invoicing capability set to distinguish between the two electronic invoicing features.

For example, consider electronic invoicing feature **C**. This feature is a copy of electronic invoicing feature **A**.

| Electronic invoicing feature | Applicability rules        |
|------------------------------|--------------------------- |
| A                            | <p>Country = BR</p><p>and</p><p>Legal entity = BRMF</p>  |
| C                            | <p>Country = BR</p><p>and</p><p>Legal entity = BRMF</p>  |

In this example, feature **C** is in front of a business document submission that contains the following:

- Country = BR
- Legal entity = BRMF

The Electronic Invoicing capability can't distinguish which electronic invoicing feature must be used to process the submission because the submissions contain the exact same clauses.

To create a distinction between the two features through Applicability rules, a new clause must be added to one of the features to allow the Electronic Invoicing capability set to select the proper electronic invoicing feature.

| Electronic invoicing feature | Applicability rules        |
|------------------------------|--------------------------- |
| A                            | <p>Country = BR</p><p>and</p><p>Legal entity = BRMF</p>  |
| C                            | <p>Country = BR</p><p>and</p><p>Legal entity = BRMF</p><p>and</p><p>Model=55</p>  |

To support creating more complex clauses, the following resources are available:

Logic operators:
- And
- Or

Operator types:
- Equal
- Not equal
- Greater than
- Less than
- Greater than or equal to
- Less than or equal to
- Contains
- Begins with

Data types:
- String
- Number
- Boolean
- Date
- UUID

Capability to group and ungroup clauses.
The example looks like this.

| Electronic invoicing feature | Applicability rules        |
|------------------------------|--------------------------- |
| C                            | <p>Country = BR</p><p>and</p><p>(Legal entity = BRMF</p><p>or</p><p>Model=55)</p>  |


## Configuration providers

Configuration providers provide the electronic invoicing features and their ER components, such as the model mapping, format configuration, and context model. They publish the electronic invoicing features and ER components in the associated Global repository. From there, other organizations can download them.

Before you configure the electronic invoicing features through RCS, you must configure your own organization as a configuration provider in the **Electronic reporting** module. For information about how to set a configuration provider to **Active**, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

## Viewing electronic invoicing features in the Global repository

To browse the electronic invoicing features that are available in the Global repository for a specific configuration provider, sync your organization's RCS instance. After synchronization is completed, the list of available electronic invoicing features is updated.

## Importing electronic invoicing features

Before you use or configure the electronic invoicing features, you must import them into your organization's RCS instance. The import operation creates a local copy of the features and copies all the ER artifacts that the features use (for example, format configurations and model configurations) to your organization's RCS instance.

You can import the electronic invoicing features from any configuration provider.

## Creating electronic invoicing features

You can create an electronic invoicing feature from scratch, or you can derive it from another electronic invoicing feature.

When you create an electronic invoicing feature from scratch, you must manually add the ER components (for example, feature version configurations and other configurations, such as the feature version setup and application setup). When you create a feature by deriving it from another feature, the new feature inherits all configurations from the original. 

## Electronic invoicing feature version

The electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented. An "effective from" date can be defined for the new version.

Electronic invoicing feature versions follow a lifecycle that has up to three statuses:

- **Draft** – If a feature version is in this status, you can edit its configuration attributes and any of its artifacts (for example, file format configurations).
- **Complete** – If a feature version is in this status, it has been published to the Global repository that is associated with your organization. You can no longer edit the feature version or any of the ER components.
- **Published** – If a feature version is in this status, it has been published to Electronic invoicing. You can no longer edit the feature version or any of the ER components.

### Feature configurations

Feature configurations hold all the ER format configurations that the electronic invoicing features use. All the electronic files that an electronic invoicing feature uses during processing come from the format configurations that have been added to the feature configurations of that feature.

From the feature configurations, you can access the ER format designer, which is the ER tool that is used to create format configurations.

### Feature setup

Feature setups are used in combination with feature configurations. Each feature setup encapsulates a set of actions, applicability rules, and variables that provide the expected behavior so that an electronic invoicing feature can meet a specific requirement of the electronic invoice.

### Application setup

The application setup must be associated with a previously created connected application.

Through the application setup, you can configure the part of an electronic invoicing feature that must be done in Finance and Supply Chain Management. At least three configurable components are mandatory, regardless of the electronic invoicing feature:

- **Table name** – The entity in Finance and Supply Chain Management that holds the posted invoices, and that the electronic invoicing feature is based on.
- **Context** – The name of the invoice context model that was configured through ER.
- **Business document mapping** – The name of the invoice mapping model that was configured through ER.

> [!IMPORTANT]
> The configuration that is entered in the application setup can be viewed in Finance and Supply Chain Management. Go to **Organization administration \> Setup \> Electronic document parameter**. On the **Electronic document** tab, select **Deploy**, and then select the **Connected application** option.

### Deploying feature versions

In RCS, you use the **Deploy** command to target-publish an electronic invoicing feature version. Select **Deploy**, and then select one of the following options to define the target of the deployment: 

- **Service environment** – When the target of the deployment is the service environment, the electronic invoicing feature version is published to the service environment. Electronic invoicing is then ready to receive and process electronic documents that Finance and Supply Chain Management send.
- **Connected application** – When the target of the deployment is the connected application, the configuration that is provided by the application setup is written in the Finance and Supply Chain Management instance that was previously associated with it.

Only electronic invoicing feature versions that have a status of **Completed** can be deployed to either a service environment or a connected application.

### Removing feature versions

In RCS, you use the **Undeploy** command to remove a specific electronic invoicing feature version from a service environment in Electronic invoicing.

> [!IMPORTANT]
> The **Undeploy** command works only in service environments. It doesn't remove electronic invoicing feature versions from connected applications.

### Rebasing electronic invoicing features

When one electronic invoicing feature is derived from another, the **Rebase** command updates the derived feature with the changes that have been introduced in the original feature.

## Additional resources

- [Issue electronic invoices in Finance and Supply Chain Management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
