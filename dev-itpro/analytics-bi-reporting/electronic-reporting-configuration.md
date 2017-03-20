---
# required metadata

title: Create an Electronic reporting configuration
description: As part of the requirements for LCS solutions for localization &amp; translation, localization ISV solution providers must implement country/region-specific or solution-specific features by using the Electronic reporting tool. This article provides background information that will help you start to use Electronic reporting to create configurations. This article isn't meant to replace any available and upcoming Electronic reporting documentation, but is intended as a supplemental view from the perspective of localization requirements.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-12-14 16 - 02 - 18
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: e3f7960d-2e01-46a7-9ac8-c355ac933cd6
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create an Electronic reporting configuration

As part of the requirements for LCS solutions for localization &amp; translation, localization ISV solution providers must implement country/region-specific or solution-specific features by using the Electronic reporting tool. This article provides background information that will help you start to use Electronic reporting to create configurations. This article isn't meant to replace any available and upcoming Electronic reporting documentation, but is intended as a supplemental view from the perspective of localization requirements.

Electronic reporting
--------------------

General electronic reporting (GER) is a new configurable tool that helps you create and maintain regulatory electronic reporting and payments, based on the following three concepts.

### Configuration instead of coding

-   Configuration can be done by a business user and doesn't require a developer.
-   The data model is defined in business terms.
-   Visual editors are used to author all components of the GER configuration.
-   A Microsoft Excel–like formula language is used for data transformation.

### One configuration for multiple Microsoft Dynamics AX releases

-   Manage one domain specific data model that is defined in business terms.
-   Isolate Dynamics AX release specifics in release-dependent data model mappings.
-   Maintain one format configuration for multiple releases of the current version of Dynamics AX, based on the data model.

### Easy or automatic upgrade

-   Versioning of GER configurations is supported.
-   The Microsoft Dynamics Lifecycle Services (LCS) Assets library can be used as a repository for GER configurations for version exchange.
-   Localizations that are based on origin GER configurations can be introduced as child versions.
-   A GER configuration tree is provided as a tool that helps control dependencies for versions.
-   Only differences in localization (delta configuration) are recorded to enable automatic upgrade to a new version of the origin GER configuration.
-   It's easy to manually resolve conflicts that are discovered during automatic upgrade of localization versions.

GER lets users define electronic format structures, and then describe how those structures should be filled by using data and algorithms that exist in Dynamics AX. Users can use a formula language that is very similar to the Excel language for data transformation. To make the database-to-format mapping more manageable, reusable, and independent of format changes, an intermediate data model concept is introduced. This concept enables Dynamics AX implementation details to be hidden from the format mapping and also enables a single data model to be reused for multiple format mappings.

## What's new here
| What can you do?                                                                                         | Microsoft Dynamics AX 2012                                                                                         | Current version of Dynamics AX                                                                                                                                                                                                                                                                                                                         | Why is this important?                                                                                                                                                                                                                                                                                                 |
|----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configure and generate electronic documents to meet the legal requirements in various countries/regions. | Electronic documents are hard-coded in X++ or as Extensible Stylesheet Language Transformations (XSLTs).           | GER is a new tool for configuring and generating electronic documents that target a business user instead of a developer.                                                                                                                                                                                                                              | GER simplifies the creation, maintenance, and upgrade of electronic document formats to meet legal requirements in various countries/regions.                                                                                                                                                                          |
| Configure regulatory updates to formats.                                                                 | Any format adjustments require development effort.                                                                 | A business user can configure the formats, based on domain-specific data models (for example, for payments, Intrastat reports, or tax reports).                                                                                                                                                                                                        | GER makes the process of creating or changing electronic document formats faster and easier. These changes can be made by business users instead of developers.                                                                                                                                                        |
| Separation of data and formats makes updates easier.                                                     | Access to data and access to formatting aren't isolated.                                                           | GER lets you set up data models that are domain-specific and independent of the Dynamics AX database as data sources for document formats. Formats can be configured based on these domain-specific data models by using simple visual tools that are similar to Excel. Data models and formats support versioning, and formats can be date-effective. | GER makes it faster and easier for partners and customers to upgrade their format and customizations to new versions of formats that are released by Microsoft or other partners.                                                                                                                                      |
| Distribute data models and formats.                                                                      | An adjusted format deployment requires a new Dynamics AX hotfix package that overrides the existing format.        | Each data model or format version is stored in a separate configuration, and is distributed to partners and customers through LCS. By using LCS, partners can share their data model and format configurations with other partners and customers, who can customize and share them further.                                                            | GER provides one common way (through LCS) for Microsoft and partners to distribute electronic document configurations to other partners and customers. GER also makes it easier for partners and customers to customize, upgrade, and distribute electronic document formats for their specific business requirements. |
| Customization and upgrade are easier.                                                                    | Custom modification of each format must be manually ported to the source code of a new Dynamics AX hotfix package. | Partners and customers can customize Microsoft data models and formats, or create their own. GER saves partner and customer configuration changes as deltas to Microsoft configurations to simplify upgrades to new versions of Microsoft configurations. Delta customization and easy upgrade are supported through the whole customization chain.    | GER provides one common way (through LCS) for Microsoft and partners to distribute electronic document configurations to other partners and customers. GER also makes it easier for partners and customers to customize, upgrade, and distribute electronic document formats for their specific business requirements. |

## Basic concepts
### Main data flow

[![GER main data flow](./media/ger-main-data-flow.jpg)](./media/ger-main-data-flow.jpg)

### Data model configuration creation

It's a good idea to reuse and customize data models that are released by Microsoft whenever you can, or to create a business domain area–specific data model that will introduce the abstract model of required entities and their relations. In this way, you will be aligned with future updates that are released by Microsoft, or can at least reuse your model for the design and maintenance of multiple domain–specific electronic documents that have different formats that are required in different scenarios or countries/regions.

#### Design the data model of the created model configuration

A data model is designed to recognize and describe the required business entities and the relations between them in the selected domain. A data model consists of descriptors that express entities by using data containers (records). Properties of entities are expressed by using data items. A record definition is an entity that contains fields (the data items). Each data item has a unique name, label, description, and value. The value of each data item can be designed so that it's recognized as string, integer, real, date, enumerate type, and so on. Additionally, the value can be another record or record list. A single record definition can be selected as a root of the data model. (A root is the starting point of the entire model for data source mapping.) In this case, the model is used as a data source that delivers data according to the single predefined data flow. If no record definition was selected as a root of the data model, the data model contains record definitions that can be assigned as a root at the format mapping stage. The data flow of such a model can be defined as a data source in multiple ways, depending on the nature of the format. For example, a single data model can be designed for the payments domain area. This data model can include data record definitions for the company as a legal entity, for vendors and customers, and also for payments. However, according to the nature of the format, the data must be presented in the following way: payer &gt; payee &gt; payments. Therefore, a single data model can offer data according to the following alternative paths:

-   Company &gt; vendor &gt; payment for the Accounts payable domain when the company record definition is selected as a root.
-   Customer &gt; company &gt; payment for the Accounts receivable domain when the customer record definition is selected as a root.

### Format configuration creation

You use the data model configuration that is created to hold abstract data for a new electronic format that you want to design. If you intend to consume a data model that was prepared earlier when you create a new format, make sure that you select the **Format based on data model** option for **Create configuration**. After you a have a format configuration, you must define a format structure. The structure can be created manually or automatically by importing an example of an XML file or an Excel template. The data model of the parent configuration is automatically offered for format mapping, together with a proper root container. Nevertheless, a format might require that data be represented in a specific way. Therefore, you can use formula designer to define expressions as virtual data items (calculated fields) for our data containers.* *Although GER allows for direct mapping of format components to database artifacts (tables or data entities), we don't recommend this approach, because it's likely that multiple formats will be maintained in some business domain areas that use the same Dynamics AX data sources. Whenever the structure of such database artifacts is changed, the format mapping to the database artifacts must also be changed, and the cost of these changes will be multiplied by the number of maintained formats. Therefore, we recommend that you work through the data model as the abstract description of the domain-specific data structure, and that you use the direct binding of format elements to database components only for simplification and for coverage for specific customizations (for example, to refer to custom tables when these references are required in a limited number of maintained formats).

## Version control
One of the principles behind the design of Electronic reporting is that it should be easy to distribute a data model and formats together with an enhanced maintenance model for their customizations. All the configurations are versioned, and an existing customization can be "cloned" to derive a new configuration for localization or customization implementation. For example, we represent a company that is named Proseware, Inc. We have subscribed to the service of a company that is named Litware Inc., which provides us with the Intrastat returns configuration and supports all legal requirements in it. We have already received specific configurations, from Litware Inc., together with data model and formats, and have deployed them. Our company is working in a district where, in addition to the federal requirements, we must support the following regional requirements:

-   As part of Intrastat transactions details, our XML file must show the statistical procedure code that isn't required anywhere else.
-   We must limit the length of the company name that is presented in the Intrastat returns header block to 200 characters.

To support these requirements and comply with local district authorities, we must implement this localization as a localized configuration. However, we must keep the link with the origin configuration, so that we can adopt any future changes that are introduced at the federal level as new versions of the origin configuration. Therefore, we import the Litware Inc. origin configuration from LCS, derive it as a new localized configuration, introduce the required changes, complete this work by introducing a first version of the localized format, and start to use it internally. Whenever Litware Inc. offers us a new version of the origin configuration, we import it from LCS, rebase our localized configuration to this version, adopt changes to support new federal requirements, complete this work by introducing a next version of the localized format, and continue to use it internally. **Note:** The draft version of any configuration must be "completed" before it can become available locally for further action, such as the following:

-   Make it available so that it can be referenced as a data source from a new format.
-   Enable configuration exchange between companies or Dynamics AX instances via configuration import/export, and so on.

## Electronic reporting domain coverage
Several out-of-box configurations can be used to meet electronic reporting requirements for specific countries/regions. The following list show some examples of format configurations that are grouped into business domains. To get a complete, up-to-date list of available and supported configurations, open a configuration repository setup to show the configurations that are available for import from either Dynamics AX resources or an LCS Assets library.

-   Audit file
    -   FEC
    -   GDPdU...
-   Payments (ISO20022)
    -   SEPA CT
    -   SEPA DD
    -   JBA
    -   BACS...
-   Statistical reports
    -   EU Intrastat...
-   Tax reports
    -   CIS
    -   BAS
    -   ELSTER
    -   EU Sales list...
-   Customer e-Invoice
    -   OIOUBL...

## Your solution uptake
You can choose how to move your electronic reporting functionality into GER. However, you should consider the following high-level steps when you plan that move.

1.  Review the electronic reporting functionality that your solution currently provides.
2.  Identify domain areas that your solution covers, such as Payments and E-Invoices.
3.  Review the configurations that are provided by Microsoft. It's likely that you'll find a configuration that you can use as a base. For example, if your solution customizes the SEPA CT payment format, you should extend the SEPA CT configuration.
4.  Create new configurations that are based on either an existing model or format, or a new model or format.
5.  Define input parameters that users must select when they run the report, and validations for the content of the report.
6.  Define mappings with the model by using arithmetic, string, data, or other available Excel-like functions.
7.  Define labels and translation to different languages, where applicable.
8.  Define templates that have named ranges, and set links from the configuration for the Excel report, if applicable.

## Terminology
| Term                 | Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GER                  | Electronic reporting is an engine that simplifies the creation of electronic reports from Dynamics AX for information interchange with governments, banks, and other parties. Currently, Electronic reporting supports text, XML, and OpenXML spreadsheet formats, and provides an extension interface to support more formats.                                                                                                                                                                                                                                                                                                        |
| Transformation       | If you have a typical action that must be done on the source of data before it is sent as output to a format, you can introduce a transformation and attach it to format components. Transformation is a GER formula that takes one value as a parameter and returns another value. For example, you have many format fields that contain spaces, and the spaces should be replaced by spaces when the fields are exported. In this case, you can create a transformation that takes a string argument and uses the REPLACE function to do the job. You can then create string components and associate them with that transformation. |
| Data model           | A data model provides a structure for data. This structure is used to abstractly describe certain business domain areas at sufficient detail to satisfy the reporting requirements in this domain.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Configuration        | A container for either a data model or a format, together with its mappings to data sources, that can be maintained and executed, and that supports versioning. The configuration is the entity that will be imported or exported to organize electronic document format exchange between Dynamics AX instances.                                                                                                                                                                                                                                                                                                                       |
| Derive action        | An operation that uses a configuration that already exists as a basis to create a new configuration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Rebase action        | An operation that updates a derived configuration with changes that were introduced in a new version of the base configuration. The version number is selected at the rebase initialization stage.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Update conflict      | A conflict that is discovered during the rebase action, where the new base version contains adjustments of a format/mapping element (name, property, and so on) that has also been adjusted in the derived version.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Relocation conflict  | A conflict that is discovered during the rebase action, where the new base version contains a new position (parent element) of a format element (name, property, and so on) that has also been relocated to a different position in the derived version.                                                                                                                                                                                                                                                                                                                                                                               |
| Duplication conflict | A conflict that is discovered during the rebase action, where the new base version introduced a new format element that is the same as an element (in other word, it has the same name and child components) that has also been entered in the derived version.                                                                                                                                                                                                                                                                                                                                                                        |



See also
--------

[Electronic reporting overview](general-electronic-reporting.md)

[Manage the Electronic reporting configuration lifecycle](general-electronic-reporting-manage-configuration-lifecycle.md)

