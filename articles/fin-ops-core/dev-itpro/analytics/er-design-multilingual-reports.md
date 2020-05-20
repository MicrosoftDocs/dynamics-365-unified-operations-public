---
# required metadata

title: ER Design multilingual reports
description: This topic explains how you can use ER labels for generation of multilingual reports.
author: NickSelin
manager: AnnBe
ms.date: 04/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERModelMappingDesigner, EROperationDesigner, ERExpressionDesignerFormula
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Design multilingual reports

[!include[banner](../includes/banner.md)]

## Overview

As a business user, you can use the [Electronic reporting (ER)](general-electronic-reporting.md) framework to configure formats of outbound documents that must be generated in accordance with the legal requirements of various countries/regions. When such requirements demand to generate outbound documents in different languages for various countries/regions, you may configure a single ER [format](general-electronic-reporting.md#FormatComponentOutbound) containing language dependent resources to re-use this format for generation of outbound documents for various countries/regions. You may also want to use a single ER format for generation of an outbound document in different languages for corresponding customers, vendors, subsidiaries, or any other parties.

You can configure ER data models and ER model mappings as data sources of configured ER formats to define the dataflow specifying what application data is placed in generated documents. As an ER solution provider, you can [publish](tasks/er-upload-configuration-into-lifecycle-services.md#upload-configuration-into-lcs) configured [data model](general-electronic-reporting.md#data-model-and-model-mapping-components), [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) and [format](general-electronic-reporting.md#FormatComponentOutbound) as components of an ER solution to generate specific outbound documents. You may allow customers to [upload](general-electronic-reporting-manage-configuration-lifecycle.md) the published ER solution for usage and customization. When you expect that customers may speak other languages, you may configure mentioned ER components as containing language dependent resources allowing at design time to present the content of an editable ER component in customer's user preferred language.

ER allows you to configure language dependent resources as ER labels. You can use ER labels to configure ER components for achieving the
following:

-   At design time

    -   Present the content of configured ER components in user preferred language

-   At runtime

    -   Generate language dependent content of outbound documents
    -   Place to user Infolog informational messages about warnings/errors in user preferred language
    -   Prompt fields that must be filled in by user in user preferred language

ER labels can be configured in every ER [configuration](general-electronic-reporting.md#Configuration) containing different ER components. They can be maintained independently from the configured logic of ER data models, ER model mappings and ER format components.

Every ER label is identified by the ID that is unique in scope of the ER configuration holding this label. Every label may contain a label text for every language that is supported in the current Finance instance including languages of deployed customizations.

## Entry

When you design an ER data model, an ER model mapping or an ER format, the **Translate** option is offered to you whenever you select a field that may contain the translatable context. When you select this option, you can link a selected field with an ER label. You can either select an existing one or add a new ER label if it is not available yet. When you added or selected an ER label, you can add a text of it for every language that is supported in the current Finance instance.

The presented below screenshot illustrates how this translation is performed to DE-AT and JA languages in an editable ER data model for the **Description** attribute of the **PurchaseOrder** data model’s field that has been selected for this.

![ER data model designer](./media/er-multilingual-labels-refer.png)

>
> Note that you can translate label’s text for the only labels that reside in the editable now ER component. For example, when you select **Translate** for a label attribute of an ER model mapping data source and selected a parent ER data model residing label, you will only see the content of this label but can’t modify it. In such cases the **Translated text** field is disabled for entry.
>
>![ER model mapping designer](./media/er-multilingual-labels-refer-mapping.png)

>
> Note that you cannot delete an entered label from the editable ER component by using the ER designers.

## Scope

ER labels can be referred in several translatable attributes of ER components.

### Data model component

When you configure an ER data model, you can add ER labels for it. **Label** and **Description** attributes of the model item, every model’s field and every <a name="LinkModelEnum">model enumeration</a> value can be linked to an ER label that you added to this ER data model.

![ER data model designer](./media/er-multilingual-labels-refer.png)

When an ER data model is configured this way, the content of this data model will be presented for end user in the ER data model designer in user preferred language simplifying model maintenance. Presented below screenshots illustrate this for users with DE-AT and JA preferred languages.

![ER data model designer](./media/er-multilingual-labels-refer-de.png)

![ER data model designer](./media/er-multilingual-labels-refer-ja.png)

### Model mapping component

As an ER model mapping is based on an ER data model, referred to labels data model elements are presented in ER model mapping designer in user preferred language as well. The presented below picture illustrates how the meaning of the **PurchaseOrder** field is explained in the editable model mapping by using the label of the **Description** attribute that has been added to the earlier configured data model. Note that this label is presented in the user preferred DE-AT language.

![ER model mapping designer](./media/er-multilingual-labels-show-mapping.png)

When the **Label** attribute of the **User input parameter** data source is configured as linked to an ER label, the corresponding with this parameter field on the user dialog page at runtime is offered for end user as prompted in user preferred language.

### Format component

When you configure an ER format, you can add ER labels for it. **Label** and **Help text** attributes of every configured data source can be linked to an ER label that you added to this ER format. **Label** and **Description** attributes of every <a name="LinkFormatEnum">format enumeration</a> value can be also linked to an ER label that is accessible from the editable ER format.

>
> Note that you can also link these attributes to an ER label of the parent ER data model reusing model’s labels in every ER format that might be configured for this ER data model.

When an ER format is configured this way, the content of this format will be presented for end user in the ER Operation designer in user preferred language simplifying its maintenance and analysis of the configured logic.

As an ER format is based on an ER data model, referred to labels data model elements are presented in ER format designer in user preferred language as well.

When the **Label** attribute of the configured the **User input parameter** data source is linked to an ER label, the corresponding with this parameter field on the user dialog page at runtime is offered for end user as prompted in user preferred language. The pictures below illustrate how you can link the **Label** attribute of the **User input parameter** data source at design time to prompt this parameter for end users in different user preferred languages at runtime. 

![ER Operation designer](./media/er-multilingual-labels-refer-format.png)
Desing time

![ER Vendor payment processing](./media/er-multilingual-labels-show-runtime-en.png)
Runtime for EN-US user preferred language

![ER Vendor payment processing](./media/er-multilingual-labels-show-runtime-de.png)
Runtime for DE-AT user preferred language

### Expressions

When you want to use a label in an ER [expression](er-formula-language.md), you need to follow this syntax: `@"GER_LABEL:X"` where `@` is the prefix meaning that this operand refers to a label, `GER_LABEL` informs that this label is an ER one and `X` is an ER label ID.

![ER formula designer](./media/er-multilingual-labels-expression1.png)

If you want to refer to a system (application) label, you the following syntax: `@"X"` where `@` is the prefix meaning that this operand refers to a label and `X` is a system label ID.

![ER formula designer](./media/er-multilingual-labels-expression2.png)

#### Model mapping

An ER expression of an ER model mapping can be configured as using a label. When this mapping is called by an ER format that is executed to generate an outbound document, the context of this execution includes a language code. A label of a configured expression will be filled in by that label text that has been configured for a language of the context of this execution.

>
> When a referred label contains no translation to a language of the context of an executed format that calls this model mapping, the EN-US language text is used instead.

#### Format

An ER expression of an ER format can be configured as using labels. When this format is executed to generate an outbound document, the context of this execution includes a language code. A label of a configured expression will be filled in by that label text that has been configured for a language of the context of this execution.

![ER formula designer](./media/er-multilingual-labels-refer-in-expression.png)

![ER Operation designer](./media/er-multilingual-labels-refer-in-binding.png)

You can configure the **FILE** component of an ER format to use user preferred language as the language that must be used to generate this report.

![ER Operation designer](./media/er-multilingual-labels-language-context-user.png)

If you configured an ER format this way, the report is generated by using the corresponding text of configured ER labels as shown below for EN-US and DE-AT user languages.

![Report preview](./media/er-multilingual-labels-report-preview-en.png)

![Report preview](./media/er-multilingual-labels-report-preview-de.png)

> 
> When a referred label contains no translation to a language of the context of format execution, the EN-US language text is used instead.

## Language

Note that the ER supports different ways to specify a language for a generated report:

-   select **Company preference** to generate a report in a language of the company in the context of which this report is generated.

    ![ER Operation designer](./media/er-multilingual-labels-language-context-company.png)
    
-   select **User preference** to generate a report in a language that is preferred by user that starts the report execution.

    ![ER Operation designer](./media/er-multilingual-labels-language-context-user.png)

-   select **Explicitly defined** to generate a report in a fixed language that is specified in this report at design time.

    ![ER Operation designer](./media/er-multilingual-labels-language-context-fixed.png)

-   select **Defined at run-time** to generate a report in a language that is specified at runtime. In the **Language** field, configure an ER expression returning the language code for this, for example, the language of the corresponding customer.

    ![ER Operation designer](./media/er-multilingual-labels-language-context-runtime.png)

## Translation

As described above, you can add required ER labels to the editable ER component. When an ER label is added, it can be translated in two ways.

### Manual

When you added an ER label, you can translate it manually in all languages that are supported in the current Finance instance. You can select the desire language in the **Language** field either **System language** or **User language** group of fields, type the appropriate text in the corresponding **Translated text** field and select **Translate**. It must be repeated for all required languages and every single label you added.

### Automatic

When you configure your ER component, you do it in the draft version of an ER configuration the editable ER component resides in.

![ER Configurations page](./media/er-multilingual-labels-configurations.png)

As described above, you can add required ER labels to the editable ER component. Doing this, you can specify the text of added ER labels in the only one EN-US language. Then, you can export labels of this ER component by using the built-in ER function. You need to select the draft version of an ER configuration containing the editable ER component and select **Export labels**.

![ER Configurations page](./media/er-multilingual-labels-export.png)

You can export either all labels or the only labels for a single language that you can specify at the beginning of export. Labels are exported as a zipped file containing XML files. Every XML file contains label for a single language.

![ER Configurations page](./media/er-multilingual-labels-in-xml.png)

This format suites for the automatic translation of labels by using external translation services like [Dynamics 365 Translation Service](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/translation-service-overview). When you received those labels translated, you can import them back to the draft version of an ER configuration containing ER components that own those labels. You need to select the draft version of an ER configuration containing the editable ER component and select **Load labels**.

![ER Configurations page](./media/er-multilingual-labels-load.png)

Translated labels will be imported to the selected ER configuration. Missing in this ER configuration translations of labels will be appended. Existing in this ER configuration translations of labels will be replaced.

## Lifecycle

Labels of an editable ER component are kept along with other content of this component in the appropriate version of an ER configuration.

Labels of a base ER component can be referred in a derived version of this ER component when you created a derived copy of it to introduce your modifications.

Label assignment to any attribute in an ER component is controlled in ER versioning. Changes of such assignment is the subject to record in in the list of changes (delta) of an editable ER component that has been created as a derived version of the provided ER component. Such changes will be validated while a derived version is rebased to a new base version. 

## Functions

[LISTOFFIELDS](er-functions-list-listoffields.md) built-in ER function can access ER labels that have been configured for some items of ER components.

As described above, **Label** and **Description** attributes of every [model](#LinkModelEnum) or [format](#LinkFormatEnum) ER enumeration’s value can be linked to an ER label that is accessible in the appropriate ER component. You can configure an ER expression in which you call the `LISTOFFIELDS` function using such ER enumeration as an argument. This expression returns a list containing a record for every value of an ER enumeration that has been defined as an argument of this function. Every record contains the value an ER label that is linked with an ER enumeration value:

-   Value of an ER label that is linked with the **Label** attributes is stored in the **Label** field of the returned record.
-   Value of an ER label that is linked with the **Description** attributes is stored in the **Description** field of the returned record.

## Additional resources

-   [Electronic Reporting overview](general-electronic-reporting.md)
-   [Electronic Reporting functions](er-formula-language.md#functions)
