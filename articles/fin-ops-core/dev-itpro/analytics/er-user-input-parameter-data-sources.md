---
# required metadata

title: Use USER INPUT PARAMETER data sources to specify parameters for a report that you want to generate
description: This topic explains how to use USER INPUT PARAMETER data sources to specify parameters for a report that you want to generate.
author: NickSelin
ms.date: 03/30/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERModelMappingDesigner, EROperationDesigner
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: Version 10.0.27

---

# Use USER INPUT PARAMETER data sources to specify parameters for a report that you want to generate

[!include[banner](../includes/banner.md)]

When you design [Electronic reporting](general-electronic-reporting.md) (ER) [model mapping](er-overview-components.md#model-mapping-component) and ER [format](er-overview-components.md#format-component) components, use the data sources of the USER INPUT PARAMETER type to obtain the necessary values that user can specify at runtime on the dialog box in data entry fields before the execution of an ER format begins. The currently supported data sources of the USER INPUT PARAMETER type are described below in this article. 

## Mandatory properties

Regardless of the USER INPUT PARAMETER type of the added data source, you must specify for it the following properties:

-   In the **Name** field, enter the data source internal name. You can use this name in other [expressions](er-formula-language.md) and bindings of the configured model mapping or format component.

## Optional properties

For any data source of the USER INPUT PARAMETER type, the following properties can be specified:

-   In the **Label** field, specify the label that is used at runtime on the dialog box for the related data entry field. Notice that you can add different label text for different language codes. For doing this, activate the **Label** field and select the **Translate** button.

-   In the **Help** field, specify the help text that is shown at design time in the bottom of the **Format designer** page or the **Model mapping designer** page when the editable data source of the USER INPUT PARAMETER type is selected. This text may provide additional details about this data source for a user while he configures the editable format or model mapping component. Notice that you can add different help text for different language codes. For doing this, use the **Translate** button.

    > [!NOTE]
    > Notice that you must add this data source, save changes, and open it for editing again to see the **Translate** button that you can use to add [language specific labels](er-design-multilingual-reports.md#format-component).

-   In the **Read only** field, configure an expression that returns the *[Boolean](er-formula-supported-data-types-primitive.md#boolean)* value.
    -   When the expression is configured and returns **True** value at runtime, the related data entry field is grayed out on the dialog box and user is not able to change its value.
    -   When the expression is configured and returns **False** value at runtime or the expression is not configured at all, the related data entry field is enabled on the dialog box and user is able to change its value.

-   In the **Default value** field, configure an expression that returns the value of the referred parameter type. This value can be used to initiate at runtime the value of the related data entry field on the dialog box.

    > [!TIP]
    > When a user runs an ER format and filled in the related data entry field at runtime on the dialog box, the entered value is memorized individually for every such field, running ER format, current user, and current organization (company) as the previously used value.

    -   Set the **Always reset to default value** option to **Yes** to always use the returned by the **Default value** expression value as a default one regardless of its the previously used value.
    -   Set the **Always reset to default value** option to **No** to use the returned by the **Default value** expression value as a default one only when its previously used value is missing.

    > [!NOTE]
    > Notice that when you set the **Always reset to default value** option to **Yes**, the **Default value** expression must be specified.

-   Set the **Allow multiple selection** field to **Yes** to allow user select at runtime multiple values for the configured parameter. When you set it to **No**, the only single value can be selected.

    > [!NOTE]
    > Notice that this option is applicable not for all USER INPUT PARAMETER types. An exception is thrown at design time informing that the configured user input parameter does not support multiple selection and only single value selection or entry is allowed.

    > [!NOTE]
    > When you set the **Allow multiple selection** field to **Yes** and configured the **Default value** expression, this expression can be used to set the only a single default value.

-   Select the **Edit visibility** option to specify whether the configured parameter will be shown at runtime on the dialog box.

    > [!TIP]
    > The default visibility a data source of the USER INPUT PARAMETER type depends on an ER component that holds it.
    >
    >   -   When a data source is configured in the format component, it is visible by default.
    >
    >   -   When a data source is configured in the model mapping component, it is visible only if the value of this data source affects the outcome of an ER component run. For example, if you added a data source but did not use it in expressions and bindings of the current model mapping component, by default the relevant data entry field will not be offered for user at runtime on the dialog box. 

    -   On the **Formula designer** page, in the **Formula** field, configure an expression that returns the *Boolean* value.

        -   When the expression is configured and returns **True** value at runtime or the expression is not configured at all, the related data entry field is visible on the dialog box at runtime.

        -   When the expression is configured and returns **False** value, the related data entry field is hidden on the dialog box at runtime. When it is called by other expressions at runtime, it returns either the default value, or the previously used value, or the default for the current data type value depending on other settings.

## Type specific properties

### Application dependent user input parameter

Use a data source of the **General \> User input parameter** type to obtain the necessary value or values of a data type that is specified for the current instance of the Finance application. When you add a data source of this type to an ER component, specify the following properties:

-   In the **Operations data type name (EDT, enum)**, select either an application [extended data type (EDT)](../extensibility/extensible-edts.md) or an application enumeration.

> [!NOTE]
> It is recommended to review the configured **Read only** and **Default value** expressions when you changed the **Operations data type name (EDT, enum)** reference in the editable data source of the USER INPUT PARAMETER type.

The following illustration shows properties of the `$TaxRegNum` data source that was configured in the **Instat XML (DE)** ER format configuration. This data source is configured as using the *Description* EDT to offer at runtime on the dialog box the **Tax registration number** data entry field.

![Reviewing properties of the data source of the USER INPUT PARAMETER type on the dialog box of the Format designer page.](./media/er-user-input-parameter-data-sources-01.png)

The following illustration shows the dialog box that is offered at runtime when the **Instat XML (DE)** ER format configuration is running to [generate](../../../finance/localizations/tasks/eur-00002-eu-intrastat-declaration.md) the Intrastat declaration. Notice that the configured **Tax registration number** field is available for data entry.  

![Reviewing the 'Intrastat Report' dialog box of the running ER format on the Intrastat page.](./media/er-user-input-parameter-data-sources-02.png)

### Data model enumeration user input parameter

Use a data source of the **Data model \> Enumeration user input parameter** type to obtain the necessary value or values of a single data model enumeration. When you add a data source of this type to an ER component, specify the following properties:

-   In the **Model** field, refer to the base data model.
-   In the **Model enumeration** field, refer to an enumeration of the referred data model.
-   In the **Version** field, select the revision number of the ER data model component that contains the referred model enumeration.

    > [!TIP]
    > At design time, you can keep this field blank to access the list of enumerations of the referred data model component that resides in the draft version of the corresponding ER data model configuration. This allows you to simultaneously edit the draft version of your model mapping or format component simultaneously with the draft version of the base data model component.
    
    > [!NOTE]
    > The **Version** field can be blank only in the draft version of model mapping or format component. When you change the status of an ER model mapping or format configuration from **Draft** to **Completed**, this field is automatically filled in by the highest model revision number that is available in the current Finance instance. So, if you introduced a new enumeration or a new enumeration value in the draft version of your base data model and referred it in the editable model mapping or format component, complete that draft version of the base data model configuration BEFORE the completion of the draft version of your model mapping or format configuration. Otherwise, the **Path not found** exception will be thrown when you change the status of an ER model mapping or format configuration from **Draft** to **Completed** informing you that the referred enumeration or enumeration value is missing in the base data model.

The following illustration shows properties of the `$ReportDirection` data source that was configured in the **Instat XML (DE) Contoso** ER format configuration. The **Instat XML (DE) Contoso** configuration has been [derived](general-electronic-reporting.md#Configuration) from the **Instat XML (DE)** one. This data source is configured as using the *ReportDirection* model enumeration to offer at runtime on the dialog box the appropriate lookup field.

![Reviewing properties of the data source of the USER INPUT PARAMETER type on the dialog box of the Format designer page.](./media/er-user-input-parameter-data-sources-03.png)

### Format enumeration user input parameter

Use a data source of the **Format enumeration \> Enumeration user input parameter** type to obtain the necessary value or values of a single format enumeration. When you add a data source of this type to an ER component, specify the following properties:

-   In the **Format enumeration** field, refer to an enumeration of the editable format.

> [!NOTE]
> This type of data sources can be configured only in scope of the editable format component.

## Additional resources

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Initiate data source values of the USER INPUT PARAMETER type from source code](er-initiate-uip-data-source-value-from-source-code.md)
