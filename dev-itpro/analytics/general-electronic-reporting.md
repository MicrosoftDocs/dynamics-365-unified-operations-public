---
# required metadata

title: Electronic reporting overview
description: This article provides an overview of the Electronic reporting (ER) tool. It includes information about key concepts, the scenarios that ER supports, and a list of formats that have been designed and released as part of the solution.
author: kfend
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ERWorkspace
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 58941
ms.assetid: 5d51b6a6-ad12-4af9-a66d-a1eb820ae57f
ms.search.region: global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Electronic reporting overview

This article provides an overview of the Electronic reporting (ER) tool. It includes information about key concepts, the scenarios that ER supports, and a list of formats that have been designed and released as part of the solution.

Electronic reporting (ER) is a tool that you can use to configure formats for electronic documents in accordance with the legal requirements of various countries/regions. ER lets you manage these formats during their lifecycle. For example, you can adopt new regulatory requirements, and can generate business documents in the required format to electronically exchange information with government bodies, banks, and other parties. The ER engine is targeted at business users instead of developers. Because you configure formats, not code, the processes of creating and adjusting formats for electronic documents are faster and easier. ER currently supports the TEXT, XML, and OPENXML worksheet formats. However, an extension interface provides support for more formats.

## Capabilities
The ER engine has the following capabilities:

-   It represents a single common tool for electronic reporting in different domains, and replaces more than 20 different engines that do some type of electronic reporting for Microsoft Dynamics 365 for Operations.
-   It makes a report’s format insulated from the current Dynamics 365 for Operations implementation. (In other words, the format is applicable for different versions of Dynamics 365 for Operations.)
-   It supports the creation of a custom format that is based on an original format. It includes capabilities for automatically upgrading the customized format when changes to the original format occur because localization/customization requirements are introduced.
-   It becomes the primary standard tool to support localization requirements in electronic reporting, both for Microsoft and for Microsoft partners.
-   It supports the ability to distribute formats to partners and customers through Microsoft Dynamics Lifecycle Services (LCS).

## Concepts
### Components

ER supports two types of components: **Data model** and **Format**.

#### Data model components

A data model component is an abstract representation of a data structure and is used to describe a specific business domain area with enough detail to satisfy the reporting requirements for that domain. A data model component consists of the following parts:

-   A data model as a set of domain-specific business entities and a hierarchically structured definition of relations between those entities
-   A model mapping that links selected Dynamics 365 for Operations data sources to individual elements of a data model that specifies, at run time, the data flow and rules of business data population to a data model component.

A business entity of a data model is represented as a container (record). Business entity properties are represented as data items (fields). Each data item has unique name, label, description, and value. The value of each data item can be designed so that it's recognized as a string, integer, real, date, enumerate type, Boolean, and so on. Additionally, it can be another record or records list. A single data model component can contain several hierarchies of domain-specific business entities and also model mappings that support a particular report-specific data flow at run time. The hierarchies are differentiated by a single record that has been selected as a root for model mapping. For example, the data model of the payment domain area might support the following mappings:

-   Company -&gt; Vendor -&gt; Payment transactions of the AP domain
-   Customer -&gt; Company -&gt; payment transactions of the AR domain

Note that business entities (such as Company and Payment transactions) are designed once. Different mappings then reuse them. A model mapping has the following capabilities:

-   It can use different Dynamics 365 for Operations data types as data sources for a data model. For example, it can use tables, data entities, methods, or enums.
-   It supports user input parameters that can be defined as data sources for a data model when some data must be specified at run time.
-   It supports the transformation of Dynamics 365 for Operations data into required groups, filtering, sorting, and summing data, and also appending with logical calculated fields that are designed through Microsoft Excel–like formulas (for more details, see [Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)).

[![Excel-like formula editor](./media/pic-formula-1024x615.png)](./media/pic-formula.png) A data model component is designed for each business domain that should be used as a unified data source for reporting that isolates reporting from the physical implementation of Dynamics 365 for Operations data sources, and represents domain-specific business concepts and functionalities in a form that makes a reporting format's initial design and further maintenance more efficient.

#### Format components

A format component is the scheme of the reporting output that will be generated at run time. A scheme consists of the following elements:

-   A format that defines the structure and content of the electronic reporting document that is generated at run time
-   Data sources as a set of user input parameters and a domain-specific data model that uses a selected model mapping
-   A format mapping as a set of bindings of format data sources that have individual elements of a format that specify, at run time, the data flow and rules of format output generation
-   A format validation as a set of configurable rules that control report generation at run time, depending on the running context (for example, a rule that stops output generation of a vendor’s payments and throws an exception when specific attributes of the selected vendor are missing, such as the bank account number).

A format component supports the following functions:

-   Creation of reporting output as individual files in various formats: text, XML, or worksheet
-   Creation of multiple files separately, and also encapsulation of those files into zip files

A format component provides the capability to attach specific files that can be used in the reporting output:

-   Excel workbooks that contain a worksheet that can be used as a template for output in the OPENXML worksheet format
-   Other files that can be incorporated into the format’s output as predefined files

#### Component versioning

Versioning is supported for ER components. The following workflow is provided for managing changes in ER components:

-   The version that is originally created is marked as a **DRAFT** version. This version can be edited and is available for test runs.
-   The **DRAFT** version can be converted to a **COMPLETED** version. This version can be used in local reporting processes.
-   The **COMPLETED** version can be converted to a **SHARED** version. This version is published on LCS and can be used in global reporting processes.
-   The **SHARED** version can be converted to a **DISCONTINUED** version. This version can then be deleted.

Versions that have either** COMPLETED** or **SHARED** status are available for other data interchange. A component that has these statuses can have these actions performed on them:

-   They can be serialized in XML format and exported from Dynamics 365 for Operations as a file in XML format.
-   They can be reserialized from an XML file and imported into Dynamics 365 for Operations as a new version of an ER component.

#### Component date effectivity

ER component versions are date effective. The **Effective from** date can be defined for an ER component to specify the date that the component becomes effective for reporting processes. The Dynamics 365 for Operations session date is used to define whether a component is valid for execution. If more than one version is valid for a particular date, the latest version is used for reporting processes.

#### Component access

Access to ER format components depends on the setting for the ISO country/region code. When this setting is blank for a selected version of a format configuration, a format component can be accessed from any Dynamics 365 for Operations company at run time. When this setting contains ISO country/region codes, a format component is available only from Dynamics 365 for Operations companies that have a primary address that is defined for one of a format component's ISO country/region codes. Different versions of a data format component can have different settings for ISO country/region codes.

#### Configuration

An ER configuration is the wrapper of a particular ER component, either **Data model** or **Format**. A configuration can include different versions of a particular ER component. Each configuration is marked as owned by a particular configuration provider. The **DRAFT** version of a component of a configuration can be edited when the owner of the configuration has been selected as an active provider in the ER settings in Dynamics 365 for Operations. Each model configuration contains a **Data model** component. A new format configuration can be originated (derived) from a specific data model configuration. The format configuration that is created will be presented in the configuration tree as a child of the original data model configuration. The format configuration that is created contains a **Format** component. The **Data model** component of the original model configuration is automatically inserted into the **Format** component of the child format configuration as a default data source. An ER configuration is shared for Dynamics 365 for Operations companies.

#### Provider

The ER provider is the party identifier that is used to indicate the author (owner) of each ER configuration. ER lets you manage the list of configuration providers. Format configurations that are released for electronic documents as part of the Dynamics 365 for Operations solution are marked as owned by the **Microsoft** configuration provider.

#### Repository

An ER repository stores ER configurations. The following types of ER repositories are currently supported: **Operations resources** and **LCS project**. An** Operations resources** repository provides access to the list of configurations that are released as part of the Dynamics 365 for Operations solution by Microsoft as an ER configuration provider. Those configurations can be imported into the current Dynamics 365 for Operations instance and used for electronic reporting. They can also be used for additional localizations/customizations. An **LCS project** repository provides access to the list of configurations of a specific LCS project (LCS project assets library) that was selected at the repository registration stage. ER lets you upload shared configurations from the current Dynamics 365 for Operations instance to a particular **LCS project** repository. You can also import configurations from a particular **LCS project** repository into the current Dynamics 365 for Operations instance. Required **LCS project** repositories can be registered individually for each configuration provider of the current Dynamics 365 for Operations instance. Each repository can be dedicated to a specific configuration provider.

## Supported scenarios
### Building a data model

ER provides a model designer that you can use to build a data model for a particular business domain. All domain-specific business entities, and the relations between them, can be presented in a data model as a hierarchical structure. The following illustration shows an example of this type of data model (the payment domain data model). [![Example of a data model](./media/pic-data-model-1024x550.png)](./media/pic-data-model.png) To become familiar with the details of this scenario, play the **ER Design domain specific data model** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Translating data model content

Data model content (labels and descriptions) can be translated into other languages that Dynamics 365 for Operations supports. You might want to translate data model content for the following reasons:

-   At design time, to make the content more intelligible for format designers who speak other language, and who will use a data model for data mapping of format components
-   At run time, to make the content more user friendly by presenting prompts and help for run-time parameters, and also configured validation messages (errors and warnings), in the language that the currently logged-on Dynamics 365 for Operations user prefers

The following illustration shows an example of how data model content can be translated from English to Japanese. [![Data model content in English](./media/pic-translate-en-1024x495.png)](./media/pic-translate-en.png) [![Data model content translated into Japanese](./media/pic-translate-ja-1024x495.png)](./media/pic-translate-ja.png)

### Configuring data model mappings

ER provides a model mapping designer that lets users map data models that they have designed to specific Dynamics 365 for Operations data sources. The following illustration shows an example of this type of data model mapping (the **SEPA Credit Transfer** model mapping of the payment domain data model). [![Example of a data model mapping ](./media/pic-model-mapping-1024x551.png)](./media/pic-model-mapping.png) To become familiar with the details of this scenario, play the **ER Define model mapping and select data sources** and **ER Map data model to selected data sources** task guides (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Storing a designed model component as a model configuration

ER can store a designed data model together with associated data mappings as a model configuration of the current Dynamics 365 for Operations instance. The following illustration shows an example of this type of data model configuration (the payment model configuration). [![Example of a data model configuration ](./media/pic-model-configuration-1024x585.png)](./media/pic-model-configuration.png) To become familiar with the details of this scenario, play the **ER Map data model to selected data sources** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Building a format that uses a data model as a base

ER supports a format designer that you can use to build the format of a particular electronic document for a selected business domain by selecting the model component as a base. The same ER format designer lets you map a format that you create to a selected domain’s data model mapping as a data source. The following illustration shows an example of this type of format (the format configuration that supports the **BACS** payment format for the United Kingdom). [![Example of a format that has a data model as a base](./media/pic-format-1024x690.png)](./media/pic-format.png) To become familiar with the details of this scenario, play the **ER Design domain specific format** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Building a configuration to generate electronic documents in OPENXML worksheet format

ER format designer can be used to build a particular electronic document in OPENXML worksheet format. The following illustration shows an example of this type of format (a format configuration to generate OPENXML worksheet with details of a selected payment journal):[![Pic-ER-format-Excel](./media/pic-er-format-excel.jpg)](./media/pic-er-format-excel.jpg) To become familiar with the details of this scenario, play the **ER Create a configuration for reports in OPENXML format** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process). Use the referred below Excel file as a template of the designing ER format to complete the step of a format template's import of this task guide: [Template of Payment Report (SampleVendPaymWsReport.xlsx)](https://go.microsoft.com/fwlink/?linkid=845202)

### Storing a designed format component in a format configuration

ER can store a designed format together with the configured data mappings as a format configuration of the current Dynamics 365 for Operations instance. The preceding illustration shows an example of this type of format configuration (**BACS (UK)**, which is a child of the **Payment model** configuration). To become familiar with the details of this scenario, play the **ER Design domain specific format** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Configuring Dynamics 365 for Operations to start to use a created format internally

Dynamics 365 for Operations can be configured to start to use a created format to generate electronic reports. The reference to the created format configuration should be defined in the settings of a specific domain. For example, to start to use an ER format configuration for electronic vendor payments in BACS format, the format configuration should be referenced in specific methods of payment, as shown in the following illustrations: 

[![BACS (UK) format configuration](media/ger-bacs-uk-format-configuration.png) 

[![Referencing the BACS (UK) format in a payment method](media/ger-bacs-uk-format-method.png) 

To become familiar with the details of this scenario, play the **ER Use format to generate electronic document for payments** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

## Handling ER components
### Publishing an ER component in LCS to offer it externally (localization)

The owner of a component (model or format) that has been created can use ER to publish the completed version of the component to LCS. A repository of the **LCS project** type for the current ER configuration provider is required. When the status of the completed version of a component is changed from **COMPLETED** to **SHARED**, that version is published in LCS. When a component has been published to LCS, the owner of that component becomes a provider of the service to support the component. For example, if the format component is designed to generate an electronic document that is legally required (for example, in accordance with a localization scenario), it's assumed that the format will be kept compliant with legislative changes, and that the provider will issue new versions of the component whenever new legislative requirements arise. To become familiar with the details of this scenario, play the **ER Upload a configuration into Lifecycle Services** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Importing an ER component from LCS to use it internally

ER lets you import ER components from LCS to the current Dynamics 365 for Operations instance. A repository of the **LCS project** type is required. When an ER component has been imported from LCS to the current Dynamics 365 for Operations instance, the owner of the instance becomes a consumer of the service that is provided by the owner (author) of the imported component. For example, if a format component is designed to generate a specific electronic document from Dynamics 365 for Operations in a country/region-specific format (localization scenario), it's assumed that the service consumer will be able to obtain any updates that are made to that format, to keep it compliant with legislative requirements. To become familiar with the details of this scenario, play the **ER Import a configuration from Lifecycle Services** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Building a format selecting another format as a base (customization)

ER lets you create (derive) a new component from the current version of a component (base) that was imported from LCS. For example, a user wants to derive a new format to implement some special requirements for an electronic document (such as an additional field or an extensive description) to support a customization scenario. To become familiar with the details of this scenario, play the **ER Upgrade format by adoption of new base version of it** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

### Upgrading a format selecting a new version of base format (rebase)

ER lets you automatically adopt changes of the latest version of the base component in the current draft version of the derived component. This process is known as *rebasing*. For example, a new regulatory change that has been introduced in the latest version of the format that was imported from LCS can be automatically merged into the customized version of this format of the electronic document. Any changes that can’t be merged automatically are considered conflicts. These conflicts are presented for manual resolution in the designer tool for the appropriate component. To become familiar with the details of this scenario, play the **ER Upgrade format by adoption of new base version of it** task guide (part of the **7.5.4.3 Acquire/Develop IT service/solution components (10677)** business process).

## List of ER configurations that are delivered in the Dynamics 365 for Operations solution
| Domain-specific data model configurations: Title | Domain                | Data model–dependent format configurations: Title | Description                                                        |
|--------------------------------------------------|-----------------------|---------------------------------------------------|--------------------------------------------------------------------|
| Audit file model                                 | Financial audit       |                                                   |                                                                    |
|                                                  |                       | Audit file (NL)                                   | Audit file format for Netherlands                                  |
| BAS model                                        | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | BAS (AU)                                          | BAS format for Australia                                           |
| Construction industry scheme model               | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | CIS Monthly return (UK)                           | CIS monthly return format for the United Kingdom                   |
| Collection letter model                          | Electronic invoicing  |                                                   |                                                                    |
|                                                  |                       | OIOUBL Collection Letter (DK)                     | OIOUBL collection letter format for Denmark                        |
| Electronic ledger accounting model (MX)          | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | Auxiliary Ledger XML (MX)                         | Auxiliary ledger transactions per account report format for Mexico |
|                                                  |                       | Chart of Account XML (MX)                         | Chart of account report format for Mexico                          |
|                                                  |                       | Journals XML (MX)                                 | Journal transactions report format for Mexico                      |
|                                                  |                       | Trial Balance XML (MX)                            | Trial balance report format for Mexico                             |
| Elster model                                     | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | Elster (DE)                                       | Elster format for Germany                                          |
| EU Sales list model                              | Trade reporting       |                                                   |                                                                    |
|                                                  |                       | EU Sales list (DE)                                | EU Sales list TXT format for Germany                               |
|                                                  |                       | EU Sales list (DK)                                | EU Sales list TXT format for Denmark                               |
|                                                  |                       | EU Sales list (FR)                                | EU Sales list XML format for France                                |
|                                                  |                       | EU Sales list (NL)                                | EU Sales list XML format for Netherlands                           |
|                                                  |                       | EU Sales list TXT (UK)                            | EU Sales list TXT format for the United Kingdom                    |
|                                                  |                       | EU Sales list XML (UK)                            | EU Sales list XML format for the United Kingdom                    |
|                                                  |                       | EU Sales list by columns report                   | EU Sales list by columns report                                    |
|                                                  |                       | EU Sales list by rows report                      | EU Sales list by rows report                                       |
| FEC accounting model (FR)                        | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | FEC Accounting data XML (FR)                      | FEC accounting data export XML format for France                   |
| German audit file                                | Financial audit       |                                                   |                                                                    |
|                                                  |                       | German audit file output                          | Audit file output for Germany and Austria                          |
| Intrastat model                                  | Trade reporting       |                                                   |                                                                    |
|                                                  |                       | Intrastat (DE)                                    | Intrastat format for Germany                                       |
|                                                  |                       | Intrastat (DK)                                    | Intrastat format for Denmark                                       |
|                                                  |                       | Intrastat INTRACOM (FR)                           | Intrastat INTRACOM format for France                               |
|                                                  |                       | Intrastat SAISUNIC (FR)                           | Intrastat SAISUNIC format for France                               |
|                                                  |                       | Intrastat (NL)                                    | Intrastat format for the Netherlands                               |
|                                                  |                       | Intrastat (UK)                                    | Intrastat format for the United Kingdom                            |
|                                                  |                       | Intrastat report                                  | Intrastat Excel control report                                     |
| Customer invoice model                           | Electronic invoicing  |                                                   |                                                                    |
|                                                  |                       | OIOUBL Project credit note (DK)                   | OIOUBL Project credit note format for Denmark                      |
|                                                  |                       | OIOUBL Project invoice (DK)                       | OIOUBL Project invoice format for Denmark                          |
|                                                  |                       | OIOUBL Sales credit note (DK)                     | OIOUBL Sales credit note format for Denmark                        |
|                                                  |                       | OIOUBL Sales invoice (DK)                         | OIOUBL Sales invoice format for Denmark                            |
| OB declaration model                             | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | OB declaration (NL)                               | OB declaration format for the Netherlands                          |
| Payment model                                    | Payments              |                                                   |                                                                    |
|                                                  |                       | Betalingsservice (DK)                             | Betalingsservice payment format for Denmark                        |
|                                                  |                       | Bill of exchange remittance (FR)                  | Bill of exchange remittance format for France                      |
|                                                  |                       | BTL91 (NL)                                        | BTL91 vendor payment format for the Netherlands                    |
|                                                  |                       | CFONB Prelevements (FR)                           | CFONB direct debit payment format for France                       |
|                                                  |                       | CFONB Virements (FR)                              | CFONB domestic vendor payment format for France                    |
|                                                  |                       | Nordea Vendor (DK)                                | Nordea corporate netbank vendor payment format for Denmark         |
|                                                  |                       | ANZ Direct Credit Service (AU)                    | Format for ANZ Direct Credit Service for Australia                 |
|                                                  |                       | CBA Direct Credit Service (AU)                    | Format for CBA Direct Credit Service for Australia                 |
|                                                  |                       | NAB Direct Credit Service (AU)                    | Format for NAB Direct Credit Service for Australia                 |
|                                                  |                       | STG Direct Credit Service (AU)                    | Format for STG Direct Credit Service for Australia                 |
|                                                  |                       | WBC Direct Entry System (AU)                      | Format for WBC Direct Entry System for Australia                   |
|                                                  |                       | DirectLink (NZ)                                   | Format for DirectLink for New Zealand                              |
|                                                  |                       | JBA Payment file (JP)                             | JBA Payment format for Japan                                       |
|                                                  |                       | ISO20022 Credit transfer                          | SEPA Credit transfer format for Europe                             |
|                                                  |                       | ISO20022 Credit transfer (FR)                     | SEPA Credit transfer format for France                             |
|                                                  |                       | ISO20022 Credit transfer (DE)                     | SEPA Credit transfer format for Germany                            |
|                                                  |                       | ISO20022 Credit transfer (NL)                     | SEPA Credit transfer format for the Netherlands                    |
|                                                  |                       | ISO20022 Direct debit                             | SEPA Direct debit format for Europe                                |
|                                                  |                       | ISO20022 Direct debit (FR)                        | SEPA Direct debit format for France                                |
|                                                  |                       | ISO20022 Direct debit (DE)                        | SEPA Direct debit format for Germany                               |
|                                                  |                       | ISO20022 Direct debit (NL)                        | SEPA Direct debit format for the Netherlands                       |
|                                                  |                       | BACS (UK)                                         | BACS vendor payment format for the United Kingdom                  |
| Reverse charge                                   | Tax reporting         |                                                   |                                                                    |
|                                                  |                       | Reverse charge sales list                         | Reverse charge sales list format                                   |
| Dutch XBRL integration model                     | XBRL reporting        |                                                   |                                                                    |
|                                                  |                       | Semansys XBRL (NL)                                | Semansys XBRL export format for the Netherlands                    |
| GAF model (MY)                                   | Financial audit       |                                                   |                                                                    |
|                                                  |                       | GAF file (MY)                                     | Format of GAF for Malaysia                                         |
| Vendor aging report (CN)                         | Vendors data analysis |                                                   |                                                                    |
|                                                  |                       | Vendor aging report format (CN)                   | Vendor aging report format for China                               |
| Vendor invoice declaration model                 | Vendors data analysis |                                                   |                                                                    |
|                                                  |                       | Vendor invoice declaration (IS)                   | Vendor invoice declaration format for Iceland                      |
|                                                  |                       | Vendor invoice declaration report (IS)            | Vendor invoice declaration report for Iceland                      |



See also
--------

[Localization requirements – Create an Electronic reporting configuration](electronic-reporting-configuration.md)

[Manage the Electronic reporting configuration lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md)

