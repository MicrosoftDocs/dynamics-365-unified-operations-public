---
# required metadata

title: Electronic reporting conponents
description: This topic describes the Electronic reporting components.
author: AnastasiaMiroshkina
ms.date: 15/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERWorkspace
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58941
ms.assetid: 5d51b6a6-ad12-4af9-a66d-a1eb820ae57f
ms.search.region: global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Electronic reporting (ER) components

ER supports next types of components: **Data model**, **Model mapping**,  **Format** and **Metadata**.

## Data model component

A data model component is an abstract representation of a data structure. It's used to describe a specific business domain area with enough detail to satisfy the reporting requirements for that domain. A data model component consists of the following parts:

- <a name="DataModelComponent"></a>A data model, as a set of domain-specific business entities and a hierarchically structured definition of relations between those entities.
- <a name="ModelMappingComponent"></a>A model mapping that links selected application data sources to individual elements of a data model that specifies, at run time, the data flow and rules of business data population to a data model component.

A business entity of a data model is represented as a container (record). Business entity properties are represented as data items (fields). Each data item has a unique name, label, description, and value. The value of each data item can be designed so that it's recognized as a string, integer, real, date, enumeration, Boolean, and so on. Additionally, it can be another record or records list.

A single data model component can contain several hierarchies of domain-specific business entities. It can also contain model mappings that support a report-specific data flow at run time. The hierarchies are differentiated by a single record that has been selected as a root for model mapping. For example, the data model of the payment domain area might support the following mappings:

- Company \> Vendor \> Payment transactions of the AP domain
- Customer \> Company \> Payment transactions of the AR domain

Note that business entities such as company and payment transactions are designed one time. Different mappings then reuse them.

## Model Mapping component

Model mapping links application data sources to individual elements of a data model that specifies, at run time, the data flow and rules of business data population to a data model component.

A model mapping that supports outgoing electronic documents has the following capabilities:

- It can use different data types as data sources for a data model. For example, it can use tables, data entities, methods, or enums.
- It supports user input parameters that can be defined as data sources for a data model when some data must be specified at run time.
- It supports the transformation of data into required groups. It also lets you filter, sort, and sum data, and append logical calculated fields that are designed through formulas that resemble Microsoft Excel formulas. For more information, see [Formula designer in Electronic reporting (ER)](general-electronic-reporting-formula-designer.md)).

A model mapping that supports incoming electronic documents has the following capabilities:

- It can use different updatable data elements as targets. These data elements include tables, data entities, and views. The data can be updated by using the data from incoming electronic documents. Multiple targets can be used in a single model mapping.
- It supports user input parameters that can be defined as data sources for a data model when some data must be specified at run time.

A data model component is designed for each business domain that should be used as a unified data source for reporting that isolates reporting from the physical implementation of data sources. It represents domain-specific business concepts and functionalities in a form that makes a reporting format's initial design and further maintenance more efficient.

#### <a name="FormatComponentOutbound"></a>Format components for outgoing electronic documents

A format component is the scheme of the reporting output that will be generated at run time. A scheme consists of the following elements:

- A format that defines the structure and content of the outgoing electronic document that is generated at run time.
- Data sources, as a set of user input parameters and a domain-specific data model that uses a selected model mapping.
- A format mapping, as a set of bindings of format data sources that have individual elements of a format that specify, at run time, the data flow and rules for format output generation.
- A format validation, as a set of configurable rules that control report generation at run time, depending on the running context. For example, there might be a rule that stops output generation of a vendor's payments and throws an exception when specific attributes of the selected vendor are missing, such as the bank account number.

A format component supports the following functions:

- Creation of reporting output as individual files in various formats, such as text, XML, Microsoft Word document, or worksheet.
- Creation of multiple files separately and encapsulation of those files into zip files.

A format component lets you attach specific files that can be used in the reporting output:

- Excel workbooks that contain a worksheet that can be used as a template for output in the OPENXML worksheet format
- Word files that contain a document that can be used as a template for output in the Microsoft Word document format
- Other files that can be incorporated into the format's output as predefined files

The following illustration shows how the data flows for these formats.

[![Data flow for outgoing format components](./media/ER-overview-02.png)](./media/ER-overview-02.png)

To run a single ER format configuration and generate an outgoing electronic document, you must identify the mapping of the format configuration.

#### <a name="FormatComponentInbound"></a>Format components for incoming electronic documents

A format component is the scheme of the incoming document that is imported at run time. A scheme consists of the following elements:

- A format that defines the structure and content of the incoming electronic document that contains data that is imported at run time. A format component is used to parse an incoming document in various formats, such as text and XML.
- A format mapping that binds individual format elements to elements of a domain-specific data model. At run time, the elements in the data model specify the data flow and the rules for importing data from an incoming document, and then store the data in a data model.
- A format validation, as a set of configurable rules that control data import at run time, depending on the running context. For example, there might be a rule that stops data import of a bank statement that has a vendor's payments and throws an exception when a specific vendor's attributes are missing, such as the vendor identification code.

The following illustration shows how the data flows for these formats.

[![Data flow for incoming format components](./media/ER-overview-03.png)](./media/ER-overview-03.png)

To run a single ER format configuration to import data from an incoming electronic document, you must identify the desired mapping of a format configuration, and also the integration point of a model mapping. You can use the same model mapping and destinations together with different formats for different type of incoming documents.

#### Component versioning

Versioning is supported for ER components. The following workflow is provided to manage changes in ER components:

1. The version that is originally created is marked as a **Draft** version. This version can be edited and is available for test runs.
2. The **Draft** version can be converted to a **Completed** version. This version can be used in local reporting processes.
3. The **Completed** version can be converted to a **Shared** version. This version is published on LCS and can be used in global reporting processes.
4. The **Shared** version can be converted to a **Discontinued** version. This version can then be deleted.

Versions that have either **Completed** or **Shared** status are available for other data interchange. The following actions can be performed on a component that has these statuses:

- The component can be serialized in XML format and exported as a file in XML format.
- The component can be reserialized from an XML file and imported into the application as a new version of an ER component.

#### Component date effectivity

ER component versions are date-effective. You can set the **Effective from** date for an ER component to specify the date that the component becomes effective for reporting processes. The application session date is used to define whether a component is valid for execution. If more than one version is valid for a particular date, the latest version is used for reporting processes.

#### Component access

Access to ER format components depends on the setting for the ISO country/region code. When this setting is blank for a selected version of a format configuration, a format component can be accessed from any company at run time. When this setting contains ISO country/region codes, a format component is available only from companies that have a primary address that is defined for one of a format component's ISO country/region codes.

Different versions of a data format component can have different settings for ISO country/region codes.