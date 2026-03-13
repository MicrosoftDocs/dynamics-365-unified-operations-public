---
title: Configure ER formats to use parameters that are specified per legal entity
description: Learn about how you can configure Electronic reporting (ER) formats to use parameters that are specified per legal entity.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-01-01
ms.search.form: ERSolutionTable, EROperationDesigner, ERLookupDesigner, ERComponentLookupStructureEditing
ms.dyn365.ops.version: Release 8.1.3
ms.assetid: 
---

# Configure ER formats to use parameters that are specified per legal entity

[!include[banner](../includes/banner.md)]

## Overview

In many of the Electronic reporting (ER) formats that you design, you must filter data by using a set of values that are specific to each legal entity of your instance (for example, a set of tax codes to filter tax transactions). Currently, when you configure this type of filtering in an ER format, you use values that depend on the legal entity (for example, tax codes) in expressions of the ER format to specify data filtering rules. Therefore, the ER format is legal entity–specific. To generate the required reports, you must create derived copies of the original ER format for each legal entity where you want to run the ER format. You must edit each derived ER format to add legal entity–specific values. You must rebase each derived ER format whenever the original (base) version is updated. You must export each derived ER format from a test environment and import it into a production environment when it must be deployed for production use. Maintenance of this type of configured ER solution is complex and time-consuming for several reasons:

-	The more legal entities there are, the more ER format configurations you need to maintain.
-	Maintenance of ER configurations requires that business users have ER knowledge.

By using the ER application-specific parameters feature, power users can configure data filtering in an ER format so that it's based on a set of abstract rules. They can configure this set of rules can to use the data sources available in an ER format. Business users can then specify real rules beyond the ER framework by using the user interface (UI) that is automatically generated based on the settings of the corresponding ER format and the current legal entity data that the ER format's dat asources can access.  The set of rules specified for an ER format can be exported from the current legal entity of the Dynamics 365 Finance (Finance) instance. It can then be imported into another legal entity of either the same Finance instance or a different instance as a set of rules for the same ER format.

## Prerequisites

To complete the examples in this article, you must have access to the instance of Regulatory Configuration Services (RCS) provisioned for the same tenant as Finance for one of the following roles:

- Electronic reporting developer
- Electronic reporting functional consultant
- System administrator

You need to complete the steps in the [Support parameterized calls of ER data sources of CALCULATED FIELD type](er-calculated-field-type.md) article. If you completed those steps, you can skip the steps in the **Import ER configurations into RCS** section that follows.

## Import ER configurations into RCS

Download and save the following ER configurations to your local device.

| **Content description**                        | **File name**                                        |
|------------------------------------------------|------------------------------------------------------|
| Sample **ER data model** configuration file    | [Model to learn parameterized calls.version.1.xml](https://download.microsoft.com/download/2/d/b/2db913a0-3622-494e-91a2-97fc494af9b9/Modeltolearnparameterizedcalls.version.1.xml)     |
| Sample **ER metadata** configuration file      | [Metadata to learn parameterized calls.version.1.xml](https://download.microsoft.com/download/1/b/3/1b343968-5a47-4000-b5a8-6487698ef4c0/Metadatatolearnparameterizedcalls.version.1.xml)  |
| Sample **ER model mapping** configuration file | [Mapping to learn parameterized calls.version.1.1.xml](https://download.microsoft.com/download/8/6/6/866e0ab6-2e05-4d98-9d52-d2da2038f6e4/Mappingtolearnparameterizedcalls.version.1.1.xml) |
| Sample **ER format** configuration             | [Format to learn parameterized calls.version.1.1.xml](https://download.microsoft.com/download/e/3/9/e392eadc-b9b4-4834-95c3-b8066dd00b9c/Formattolearnparameterizedcalls.version.1.1.xml)  |

Next, sign in to your RCS instance.

In this example, you create a configuration for the Litware, Inc sample company. Before you can complete this procedure, you must complete the steps in the [Create a configuration provider and mark it as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) article in RCS.

1.	On the default dashboard, select **Electronic reporting**.
1.	Select **Reporting configurations**.
1.	Import the ER configurations that you downloaded earlier into RCS in the following order: data model, metadata, model mapping, and format. For each ER configuration, follow these steps:

    1.	Select **Exchange**.
    1.	Select **Load from XML file**.
    1.	Select **Browse** to select the file for the required ER configuration in XML format.
    1.	Select **OK**.

## Review the ER solution provided.

1.	In the configuration tree, expand the contents of the **Model to learn parameterized calls** item.
1.	Select the **Format to learn parameterized calls** item.
1.	Select **Designer**.
1.	Select **Expand/Collapse**.

    The **Format to learn parameterized calls** ER format is designed to generate a tax statement in XML format that presents several levels of taxation (regular, reduced, and none). Each level has a different number of details.

    :::image type="content" source="./media/RCS-AppSpecParms-ReviewFormat.PNG" alt-text="Screenshot of multiple levels of ER format, Format to learn parameterized calls.":::

1.	On the **Mapping** tab, expand the **Model**, **Data**, and **Summary** items.

        The **Model.Data.Summary** data source returns the list of tax transactions. These transactions are summarized by tax code. For this data source, the **Model.Data.Summary.Level** calculated field is configured to return the code for the taxation level of each summarized record. For any tax code retrieved from the **Model.Data.Summary** data source at runtime, the calculated field returns the taxation level code (**Regular**, **Reduced**, **None**, or **Other**) as a text value. The **Model.Data.Summary.Level** calculated field filters records of the **Model.Data.Summary** data source and enters the filtered data in each XML element that represents a taxation level by using the **Model.Data2.Level1**, **Model.Data2.Level2**, and **Model.Data2.Level3** fields.

    :::image type="content" source="./media/RCS-AppSpecParms-ReviewFormat-Data2Fld.PNG" alt-text="Screenshot of the Model.Data.Summary data source list of tax transactions.":::

        The **Model.Data.Summary.Level** calculated field contains an ER expression. Tax codes (**VAT19**, **InVAT19**, **VAT7**, **InVAT7**, **THIRD**, and **InVAT0**) are hardcoded into this configuration. Therefore, this ER format depends on the legal entity where the tax codes were configured.

    :::image type="content" source="./media/RCS-AppSpecParms-ReviewFormat-LevelFld.PNG" alt-text="Screenshot of the Model.Data.Summary.Level calculated field with hardcoded tax codes.":::

    To support a different set of tax codes for each legal entity, you must follow these steps:

    - Create a derived version of the ER format for each legal entity.
    - Update the tax codes in the **Model.Data.Summary.Level** calculated field, based on the legal entity setting.

1.	Close the **Format designer** page.

## Create a derived format

Next, you will use the ER application-specific parameters feature to support a different set of tax codes for each legal entity in a single ER format.

1.	In the configuration tree, expand the contents of the **Model to learn parameterized calls** item.
1.	Select the **Format to learn parameterized calls** item.
1.	Select **Create configuration**.
1.	Select the **Derive from Name: Format to learn parameterized calls, Microsoft** option.
1.	In the **Name** field, enter **Format to learn how to lookup LE data**.
1.	Select **Create configuration**.

## Configure a derived format

### Add a format enumeration

Next, add a new ER format enumeration. The values of this format enumeration are presented to business users so they can specify legal entity–dependent sets of tax codes for the various taxation levels that are used in the ER format.

1.	Select **Designer**.
1.	Select **Format enumerations**.
1.	Select **Add**.
1.	In the **Name** field, enter **List of taxation levels**.
1.	Select **Save**.
1.	On the **Format enumeration values** tab, select **Add**.
1.	In the **Name** field, enter **Regular taxation**.
1.	Select **Add** again.
1.	In the **Name** field, enter **Reduced taxation**.
1.	Select **Add** again.
1.	In the **Name** field, enter **No taxation**.
1.	Select **Add** again.
1.	In the **Name** field, enter **Other**.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-Enum.PNG" alt-text="Screenshot of a new record on the Format enumerations page.":::

    Because the business users might use different languages to specify legal entity–dependent sets of tax codes, we recommend that you translate the values of this enumeration into the languages that are configured as the preferred languages for those users in Finance.

1.	Select the **No taxation** record.
1.	Click in the **Label** field.
1.	Select **Translate**.
1.	In the **Text translation** pane, in the **Label ID** field, enter **LBL_LEVELENUM_NO**.
1.	In the **Text in default language** field, enter **No taxation**.
1.	Select **DE** in the **Language** field.
1.	In the **Translated text** field, enter **keine Besteuerung**.
1.	Select **Translate**.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-EnumTranslate.PNG" alt-text="Screenshot of the text translation slide out.":::

1.	Select **Save**.
1.	Close the **Format enumerations** page.

### Add a new lookup data source

Next, add a new data source to specify how business users can create legal entity–dependent rules to recognize the correct taxation level for each summarized transaction record.

1.	On the **Mapping** tab, select **Add**.
1.	Select **Format enumeration\Lookup**.

        You just identified that each rule business users specify for taxation level recognition returns a value of an ER format enumeration. Notice that the **Lookup** data source type can be accessed under the **Data model** and **Dynamics 365 for Operations** blocks in addition to the **Format enumeration** block. Therefore, you can use ER data model enumerations and application enumerations to specify the type of values returned for the data sources of that type. To learn more about the **Lookup** data sources, see [Configure Lookup data sources to use the ER application-specific parameters feature](er-lookup-data-sources.md).
    
1.	In the **Name** field, enter **Selector**.
1.	In the **Format enumeration** field, select **List of taxation levels**.

    You specified that for each rule in this data source, a business user must select one of the values of the **List of taxation levels** format enumeration as a returned value.
    
1.	Select **Edit lookup**.
1.	Select **Columns**.
1.	Expand the **Model** item.
1.	Expand the **Data** item.
1.	Expand the **Tax** item.
1.	Select the **Model.Data.Tax.Code** item.
1.	Select the **Add** button (the right arrow).

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-Lookup1.PNG" alt-text="Screenshot of the Columns slide out.":::

    You just specified that for each rule in this data source for taxation level recognition, a business user must select one of the tax codes as a condition. The **Model.Data.Tax** data source returns the list of tax codes that the business user can select. Because this data source contains the **Name** field, the name of the tax code appears for each tax code value in the lookup that is presented to the business user.
    
1.	Select **OK**.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-Lookup2.PNG" alt-text="Screenshot of the Lookup designer page.":::

    Business users can add multiple rules as records of this data source. Each record is numbered by a line code. Rules are evaluated in order of increasing line number.

    Because you selected the **Tax code** field as a condition for rules in this lookup data source, and because **Tax code** is set up as a field of the **String** data type, each rule is evaluated at runtime by comparing the tax code that is passed to the data source with the tax code that is defined in this record of the data source.

    When a rule that satisfies the configured condition is found, this data source returns the lookup value of the rule that is defined in the **Lookup result** field. If no rule is found, an exception is thrown to notify the user that the current data source can't return a correct value.

1.	Select **Save**.
1.	Close the **Lookup designer** page.
1.	Select **OK**.

    You added a new data source that returns the taxation level as the value of the **List of taxation levels** format enumeration for any tax code that is passed to the data source as the argument of the **Code** parameter of the **String** data type.
    
    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-SelectorFld.PNG" alt-text="Screenshot of the Format designer page with new data source.":::

        The evaluation of configured rules depends on the data type of the fields that you select to define conditions of those rules. When you select a field that is configured as a field of either the **Numeric** or **Date** data type, the criteria differ from the criteria described earlier for the **String** data type. For **Numeric** and **Date** fields, the rule must be specified as a range of values. The condition of the rule is considered satisfied when a value that is passed to the data source is in the configured range.
    
    The following illustration shows an example of this type of setup. In addition to the **Model.Data.Tax.Code** field of the **String** data type, the **Model.Tax.Summary.Base** field of the **Real** data type is used to specify conditions for a lookup data source.
    
    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-SelectorFld2.PNG" alt-text="Screenshot of the Lookup designer page with additional columns.":::

    Because the **Model.Data.Tax.Code** and **Model.Tax.Summary.Base** fields are selected for this lookup data source, each rule of this data source is configured in the following way:
    
    -	In the list that is presented, select the value of the **List of taxation levels** format enumeration as a returned value.
    -	Enter the tax code as a condition of this rule. Only tax codes that the **Model.Data.Tax** data source provides are applicable.
    -	Enter minimum and maximum values of the tax base amount as conditions of this rule.

    Here is how each rule of this data source will be evaluated at runtime:
    -	Does the code of the **String** data type that was passed to this data source equal the tax code of a rule?
    -	Does the value of the **Real** data type that was passed to this data source fall between specific minimum and maximum values?

    A rule is applicable when both conditions are satisfied.

### Translate the label of the lookup data source that was added

Because business users might use different languages to specify legal entity–dependent sets of tax codes, translate the label of any lookup data source that you add. This way, it's presented in each user's preferred language on the corresponding page.

1.	Select the **Model.Data.Selector** data source.
1.	Select **Edit**.
1.	Click in the **Label** field.
1.	Select **Translate**.
1.	In the **Text translation** pane, enter **LBL_SELECTOR_DS** in the **Label ID** field.
1.	Enter **Select tax level by tax code** in the **Text in default language** field.
1.	Select **DE** in the **Language** field.
1.	Enter **Steuerebene für Steuerkennzeichen auswählen** in the **Translated text** field.
1.	Select **Translate**.
1.	Select **OK**.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-SelectorFldTranslate.PNG" alt-text="Screenshot of the data source properties slide out.":::

### Add a new field to consume the configured lookup

1.	Expand the **Model.Data** item.
1.	Select the **Model.Data.Summary** item.
1.	Select **Add**.
1.	Select **Functions/Calculated field**.
1.	In the **Name** field, enter **LevelByLookup**.
1.	Select **Edit formula**.
1.	In the **Formula field**, enter **Model.Selector(Model.Data.Summary.Code)**.
1.	Select **Save**.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-AddLevelByLookupFld.PNG" alt-text="Screenshot of adding Model.Selector(Model.Data.Summary.Code) to the Formula designer page.":::

1.	Close the **Formula editor** page.
1.	Select **OK**.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-AddLevelByLookupFld2.PNG" alt-text="Screenshot of the Format designer page with new formula added.":::

        The **LevelByLookup** calculated field that you added returns the taxation level as the value of the **List of taxation levels** format enumeration for each summarized tax transactions record. The tax code of the record is passed to the **Model.Selector** lookup data source, and the set of rules for this data source selects the correct taxation level.

### Add a new format enumeration-based data source

Next, add a new data source that refers to the format enumeration that you added earlier. Values of this data source are used in an ER format expression later.

1.	Select **Add root**.
1.	Select **Format enumerations\Enumeration**.
1.	In the **Name** field, enter **TaxationLevel**.
1.	In the **Format enumeration** field, select **List of taxation levels**.
1.	Select **Save**.

### Modify an existing field to start using the lookup

Next, you modify the existing calculated field so that it uses the configured lookup data source to return the correct taxation level value, depending on the tax code.

1.	Select the **Model.Data.Summary.Level** item.
1.	Select **Edit**.
1.	Select **Edit formula**.

    Notice that the current expression of the **Model.Data.Summary.Level** field includes the following hard-coded tax codes:
    
    `CASE (@.Code, "VAT19", "Regular", "InVAT19", "Regular", "VAT7", "Reduced", "InVAT7", "Reduced", "THIRD", "None", "InVAT0", "None", "Other")`

1.	In the **Formula** field, enter `CASE(@.LevelByLookup, TaxationLevel.'Regular taxation', "Regular", TaxationLevel.'Reduced taxation', "Reduced", TaxationLevel.'No taxation', "None", "Other")`.

    :::image type="content" source="./media/RCS-AppSpecParms-ConfigureFormat-ChangeLookupFld.PNG" alt-text="Screenshot of the ER Operation designer page.":::
    
    The expression of the **Model.Data.Summary.Level** field now returns the taxation level, based on the tax code of the current record and the set of rules that a business user configures in the **Model.Data.Selector** lookup data source.
    
1.	Select **Save**.
1.	Close **Formula designer**.
1.	Select **OK**.
1.	Select **Save**.
1.	Close **Format designer**.

## Complete the draft version of a derived format

1.	On the **Versions** FastTab, select **Change status**.
1.	Select **Complete**.
1.	Select **OK**.

## Export completed version of modified format

1.	In the configuration tree, select the **Format to learn how to look up LE data** item.
1.	On the **Versions** FastTab, select the record that has a status of **Completed**.
1.	Select **Exchange**.
1.	Select **Export as XML file**.
1.	Select **OK**.
1.	The web browser downloads a **Format to learn how to look up LE data.xml** file. Store this file locally.

Repeat the preceding steps for parent items of the **Format to learn how to look up LE data** format, and store the following files locally:

-	Format to learn parameterized calls.xml
-	Mapping to learn parameterized calls.xml
-	Model to learn parameterized calls.xml

To learn how to use the configured **Format to learn how to look up LE data** ER format to set up legal entity–dependent sets of tax codes to filter tax transactions by different taxation levels, complete the steps in the [Set up the parameters of an ER format per legal entity](er-app-specific-parameters-set-up.md) article.

## Additional resources

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Set up the parameters of an ER format per legal entity](er-app-specific-parameters-set-up.md)

[Configure Lookup data sources to use the ER application-specific parameters feature](er-lookup-data-sources.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
