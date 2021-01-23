---
# required metadata

title: Configure the Electronic invoicing add-on in the Regulatory configuration service (RCS)
description: This topic explains how to configure the electronic invoicing add-on in RCS. 
author: gionoder
manager: AnnBe
ms.date: 01/22/2021
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
ms.dyn365.ops.version: AX 10.0.12

---

# Configure the Electronic invoicing add-on in the Regulatory configuration service (RCS)

[!include [banner](../includes/banner.md)]


This topic provides information about the configuration capabilities of the Electronic invoicing add-on in the Regulatory configuration service (RCS).

The most important configuration pillar allows you to fulfill business and regulatory requirements of electronic invoices without any required coding. In scenarios where electornic invoices must be sent to submitted to an external party through web services, the configuration capabilities fulfill file formatting and communication requirements.

## Electronic reporting

Electronic reporting supports the Electronic invoicing add-on.

The data model mapping and formats are configurable components that are created and maintained through Electronic reporting and utilized in the Electronic invoicing add-on. The Format designer from Electronic reporting, is the tool for creating and maintaining file formats. The designer is used to configure electronic invoicing features.

For more information, see [Electronic reporting (ER) overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

## Electronic invoicing features

Electronic invoicing feature. within the Electronic invoicing add-on, is the element responsible for transforming the electronic document data, sent by Dynamics 365 Finance and Dynamics 365 Supply Chain Management, into electronic invoices, since the scenarios where the requirement is simply the generation of the invoice as a digital media, until the scenarios where the requirement is the submitting the electronic invoice for a digital approval granted by an external party, through web services, hosted by the own government tax authority, or by a party accredited by the tax authority.

### Electronic invoicing feature availability

The availability of Electronic invoicing features is based on country/region. While some features are generally available, others are in preview.

#### Generally available features

The features in the following table are generally available at this time. 

| Country/Region    | Feature name                             | Business document                      |
|-------------------|------------------------------------------|----------------------------------------|
| Egypt             | Egypt e-Invoicing                        | Sales and Project invoices             |

#### Preview features

The features in the following table are still in preview.

| Country/Region    | Feature name                             | Business document                      |
|-------------------|------------------------------------------|----------------------------------------|
| Austria           | Austrian electronic invoices (AT)        | Sales and Project invoices             |
| Belgium           | Belgian electronic invoice (BE)          | Sales and Project invoices             |
| Brazil            | NF-e                                     | Fiscal document model 55, Correction letter, Cancellation and Discard|
| Brazil            | NFS-e ABRASF Curitiba                    | Service fiscal document                |
| Brazil            | NFS-e São Paulo city                     | Service fiscal document                |
| Denmark           | Danish electronic invoice (DK)           | Sales and Project invoices             |
| Estonia           | Estonian electronic invoice (EE)         | Sales and Project invoices             |
| Finland           | Finnish electronic invoice (FI)          | Sales and Project invoices             |
| France            | French electronic invoice (FR)           | Sales and Project invoices             |
| Germany           | German electronic invoice (DE)           | Sales and Project invoices             |
| Italy             | FatturaPA (IT)                           | Sales and Project invoices             |
| Mexico            | CFDI                                     | Sales invoices, Packing slip, Invent transfer, Payment complement, Cancellation |
| Netherlands       | Dutch electronic invoice (NL)            | Sales and Project invoices             |
| Norway            | Norwegian electronic invoice (NO)        | Sales and Project invoices             |
| Spain             | Spanish electronic invoice (ES)          | Sales and Project invoices             |
| Europe            | PEPPOL electronic invoice                | PEPPOL Sales and Project invoices      |

### Electronic invoicing configurable components

Electronic invoicing features are composed of following groups of configurable components:

  - Formats: Allows you to configure what the Electronic invoicing add-on must generate when an electronic document becomes an electronic invoice. Formats include the format configuration for the electronic invoice and the format configuration for files and messages used to submit requests and receive responses when communication with an external web service is required.
  - Actions: Allows you to configure how the Electronic invoicing add-on generates the transformation of an electronic document that was submitted by Finance and Supply Chain Management into an electronic invoice.
  - Applicability rules: Allows you to configure the context the Electronic invoicing add-on must consider to process an electronic invoicing feature.
  - Variables: Allows you to configure the variables used to support the construction of the configuration logic. Variables can work as an input of values to accomplish a specific action, or an exchange of values between Finance and Supply Chain Management and the Electronic invoicing add-on.
  - Electronic document model mapping: Alloww you to configure the Electronic reporting model mapping. The model mapping defines the data mapping of the abstract invoice that's integrated to the Electronic invoicing add-on when electronic documents are submitted.
  - Invoice context model: Allows you to configure the Electronic reporting invoice context model and define the context of the Electronic invoicing feature.
  - Response types: Allows you to configure what the Electronic invoicing add-on must update in Finance and Supply Chain Management as the result of the electronic invoice processing.

### Formats

The following tables list the available ER format configurations for the Electronic invoicing features:

| Austrian (AT) electronic invoices: Sales and Project invoices for Austria    |
|------------------------------------------------------------------------------|
| OIOUBL Sales invoice                                                         |
| OIOUBL Project invoice                                                       |
| OIOUBL Sales credit note                                                     |
| OIOUBL Project credit note                                                   |

| Belgian (BE) electronic invoice: Sales and Project invoices for Belgium      |
|------------------------------------------------------------------------------|
| UBL Sales invoice BE                                                         |
| UBL Project invoice BE                                                       |
| UBL Project credit note BE                                                   |
| UBL Sales credit note BE                                                     |

| Brazilian (BR) NF-e: NF-e Federal (Brazil)                                   |
|------------------------------------------------------------------------------|
| NF-e submit export format (BR)                                               |
| NF-e correction letter export format (BR)                                    |
| NF-e cancel export format (BR)                                               |
| NF-e discard export format (BR)                                              |

| Brazilian NFS-e (BR): NFS-e ABRASF Curitiba city                             |
|------------------------------------------------------------------------------|
| NFS-e ABRASF Curitiba (BR))                                                  |

| Brazilian (BR) NFS-e: NFS-e São Paulo city                                   |
|------------------------------------------------------------------------------|
| NFS-e Sao Paulo (BR)                                                   |

| Danish (DK) electronic invoice: Sales and Project invoices for Denmark       |
|------------------------------------------------------------------------------|
| OIOUBL Sales invoice                                                         |
| OIOUBL Project invoice                                                       |
| OIOUBL Sales credit note                                                     |
| OIOUBL Project credit note                                                   |

| Dutch (NL) electronic invoice: Sales and Project invoices for Netherlands    |
|------------------------------------------------------------------------------|
| UBL Sales invoice NL                                                         |
| UBL Project invoice NL                                                       |
| UBL Project credit note NL                                                   |
| UBL Sales credit note NL                                                     |

| Egyptian (EG) electronic invoice: Sales and Project invoices for Egypt       |
|------------------------------------------------------------------------------|
| Sales invoice (EG)(Invoicing)                                                |
| Project invoice (EG)(Invoicing)                                              |

| Estonian (EE) electronic invoice: Sales and Project invoices for Estonia     |
|------------------------------------------------------------------------------|
| Sales invoice (EE)                                                           |
| Project invoice (EE)                                                         |

| Finnish  (FI) electronic invoice: Sales and Project invoices for Finland      |
|------------------------------------------------------------------------------|
| Sales invoice (FI)                                                           |
| Project invoice (FI)                                                         |

| French (FR) electronic invoice: Sales and Project invoices for France        |
|------------------------------------------------------------------------------|
| UBL Sales invoice FR                                                         |
| UBL Project invoice FR                                                       |
| UBL Project credit note FR                                                   |
| UBL Sales credit note FR                                                     |

| German (DE) electronic invoice: Sales and Project invoices for Germany       |
|------------------------------------------------------------------------------|
| Sales invoice (DE)                                                           |
| Project invoice (DE)                                                         |

| Italian (IT) electronic invoice: Sales and Project invoices for Italy         |
|------------------------------------------------------------------------------|
| Sales invoice (IT)                                                           |
| Project invoice (IT)                                                         |

| Mexican (MX) CFDI: CFDI for Mexico                                                     |
|------------------------------------------------------------------------------|
| CFDI invoice format (MX)                                                     |
| CFDI Packing slip (MX)                                                       |
| CFDI Inventory transfer (MX)                                                 |
| CFDI payment format(MX)                                                      |
| CFDI invoice cancel format (MX)                                              |

| Norwegian (NO) electronic invoice: Sales and Project invoices for Norway     |
|------------------------------------------------------------------------------|
| OIOUBL Sales invoice                                                         |
| OIOUBL Project invoice                                                       |
| OIOUBL Sales credit note                                                     |
| OIOUBL Project credit note                                                   |

| PEPPOL electronic invoice: PEPPOL Sales and Project invoices                 |
|------------------------------------------------------------------------------|
| PEPPOL Sales invoice                                                         |
| PEPPOL Project invoice                                                       |
| PEPPOL Sales credit note                                                     |
| PEPPOL Project credit note                                                   |

| Spanish (ES) electronic invoice: Sales and Project invoices for Spain        |
|------------------------------------------------------------------------------|
| Sales invoice (ES)                                                           |
| Project invoice (ES)                                                         |

### Actions

The following table lists the available actions and the availability status (Preview or Generally available):

| Action                                        | Description                                                 | Availability                |
|-----------------------------------------------|-------------------------------------------------------------|-----------------------------|
| Transform document                            | Generates a file following a specific ER format configuration.  | Preview                     |
| Transform document from OData source          |                                                             | Preview                     |
| Sign xml document                             | Applies a digital signature in the XML file.                 | Preview                     |
| Sign json document for Egyptian Tax Authority | Applies a digital signature in a JSON file.                  | Preview                     |
| Egyptian Tax Authority REST client            | Submits an e-invoice to Egyptian tax authority web service.  | Preview                     |
| Call Brazilian SEFAZ Service                  | Submits an e-invoice to Brazilian tax authority web service. | Preview                     |
| Call Mexican PAC Service                      | Submits an e-invoice to PAC web services.                    | Preview                     |
| Process response                              | Analyze the web service response.                            | Preview                     |
| Use MS Power Automate                         |                                                             | Preview                     |
| File store action name                        |                                                             | Preview                     |

## Configuration providers

The configuration providers provide the Electronic invoicing features and their Electronic reporting components, such as model mapping, format configuration, and context model.

Electronic invoicing features and any Electronic reporting components are published by the configuration providers in the associated global repository where other organizations can download.  

Before you configure Electronic invoicing features through RCS, you must configure your own organization as a configuration provider in the **Electronic reporting** module. For information about how to set a provider to **Active**, see [Create configuration providers and mark them as active](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11).

## View the Electronic invoicing features in the Global repository

You can browse the available electronic invoicing features in the Global repository for a specific configuration provider, by synchronizing your RCS. After you synchronize, the list of available electronic invoicing features is refreshed and you can view the features.

## Import the Electronic invoicing feature

You can only use or configure Electronic invoicing features that are imported to the instance of your organization in RCS.

If you choose using some of the electronic invoicing feature published by some of the Configuration providers, the importation of Electronic invoicing features is the first step, because it creates a local copy of the selected electronic invoicing feature, as well all its Electronic reporting components, from which you can either start using, configure or customize.

## Create an Electronic invoicing feature

Electronic invoicing features can be created from scratch or they can be derived from another Electronic invoicing feature.

When one feature is created from another, the new feature inherits all configurations from the original. When a feature is created from the scratch, you must manually add the Electronic reporting components such as Feature version configurations and other configurations, such as Feature version setup and Application setup.

## Electronic invoicing feature version

The electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented and an effective from date can be defined.

The feature version follows a life cycle with up to three statuses:

   - **Draft**: In this status, you can edit the configuration attributes of the feature version, and any of its artifacts, such as file format configurations.
   - **Complete**: In this status, the feature version has been published to the Global repository associated to your organization. Editing the feature version or any of the Electronic reporting components is no longer allowed.
    - **Published**: In this status, the feature version has been published to the Electronic invoicing add-on. Editing the feature version or any of the Electronic reporting components is no longer allowed.

### Feature configurations

Feature configurations holds all of the Electronic reporting format configurations the electronic invoicing feature uses. All of the electronic files used by the electronic invoicing feature in the processing come from the format configurations that added to this section of the electronic invoicing feature.

Through Feature configurations, you have access to the Format designer which is the Electronic reporting tool used to create the format configurations.

### Feature setup

Used in combination with the Feature configurations, each Feature setup encapsulates a set of Actions, Applicability rules, and Variables that provide an expected behavior for the Electronic invoicing feature to fulfill a specific requirement of the electronic invoice.

### Application setup

The Application setup must be associated to a previously created Connected application.

Through Application setup, you can configure the part of the electronic invoicing feature that must be accomplished in Finance and Supply Chain Management. At least three configurable components are mandatory, independent of the electronic invoicing feature:

   - **Table name**: The entity in Finance and Supply Chain Management that holds the posted invoices, and over which the electronic invoicing feature is based.
   - **Context**: The name of the invoice context model configured through Electronic reporting.
   - **Business document mapping**: The name of the invoice mapping model configured through Electronic reporting.

> [!IMPORTANT]
> The configuration entered under Application setup can be viewed in Finance and Supply Chain Management by going to **Organization administration** > **Setup** > **Electronic document parameter** page. On the **Electronic document** tab, select **Deploy** with the option to deploy to the connected application.

### Deploy

In RCS, **Deploy** is the command that target-publishes the Electronic invoicing feature version:

   - **Service environment**: When the target of the deploy is the service environment, the Electronic invoicing feature version is published into the Service environment. After that, the Electronic invoicing add-on is ready to receive and process the submissions of electronic documents sent by Finance and Supply Chain Management.
   - **Connected application**: When the target of the deploy is the connected application, the configuration given by the Application setup is written in the Finance and Supply Chain Management instance that was previously associated to it.

Only Electronic invoicing feature versions with a status of **Completed** can be deployed, either to a service environment or a connected application.

### Undeploy

In RCS, **Undeploy** is the command that removes a specific Electronic invoicing feature version from a Service environment in the Electronic invoicing add-on.

> [!IMPORTANT]
> **Undeploy** works only in service environments to remove Electronic invoicing feature versions. **Undeploy** doesn't remove the feature version from the connected applications.

### Rebase

When an Electronic invoicing feature is created from another Electronic invoicing feature, the **Rebase** action updates the derived feature with the updates introduced in the original Electronic invoicing feature.

## Additional resources
- [Issue electronic invoices in Finance and Supply Chain Management](e-invoicing-issuing-electronic-invoices-in-finance-and-supply-chain-management.md)
