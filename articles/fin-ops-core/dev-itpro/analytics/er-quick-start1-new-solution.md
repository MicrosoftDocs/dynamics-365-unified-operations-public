---
title: Design a new ER solution to print a custom report
description: Learn how to design an Electronic reporting (ER) solution to print a custom report, including additional resources.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERWorkspace, ERSolutionTable, ERParameters, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, EROperationDesigner, ERVendorTable
ms.dyn365.ops.version: Version 7.0.0
ms.assetid: 
---

# Design a new ER solution to print a custom report

[!include[banner](../includes/banner.md)]

The following steps explain how a user in the System Administrator, Electronic Reporting Developer, or Electronic Reporting Functional Consultant role can configure parameters of the ER framework, design the required ER configurations of a new ER solution to access the data of a particular business domain, and generate a custom report in Microsoft Office format. You can complete these steps in the **USMF** company.

- [Configure the ER framework](#ConfigureFramework)

  - [Configure ER parameters](#ConfigureParameters)
  - [Activate an ER configuration provider](#ActivateProvider)

    - [Review the list of ER configuration providers](#ReviewProvidersList)
    - [Add a new ER configuration provider](#AddProvider)
    - [Activate an ER configuration provider](#ActivateAddedProvider)

- [Design a domain-specific data model](#DesignModel)

  - [Import a new data model configuration](#ImportDataModel)
  - [Create a new data model configuration](#DesignDataModel)

    - [Name the data model](#NameDataModel)
    - [Add data model fields](#FieldsEntry)
    - [Complete the design of the data model](#CompleteDataModel)

- [Design a model mapping for the configured data model](#DesignMapping)

  - [Import a new model mapping configuration](#ImportModelMapping)
  - [Create a new model mapping configuration](#CreateModelMapping)

    - [Design a new model mapping component](#DesignMappingComponent)
    - [Add data sources to access application tables](#AddMmDataSource1)
    - [Add data sources to access application enumerations](#AddMmDataSource2)
    - [Add ER labels to generate a report in a specified language](#AddMmLabels)
    - [Add a data source to transform the results of comparing enumeration values to a text value](#AddMmDataSource3)
    - [Bind data sources to data model fields](#AddMmBindings1)
    - [Complete the design of the model mapping](#CompleteModelMapping)

- [Design a template for a custom report](#DesignReportTemplate)
- [Design a format](#DesignFormat)

  - [Import a designed format configuration](#FormatImport)
  - [Create a new format configuration](#FormatCreate)

    - [Import a report template](#ImportReportTemplate)
    - [Configure a format](#ConfigureFormat)
    - [Define the data binding for a report title](#DefineFormatBindings)
    - [Review the model data source](#ReviewModelDataSource)
    - [Bind format elements to data source fields](#BindFormatElements)

  - [Run a designed format from ER](#RunFormatFromER)

- [Tune a designed format](#TuneFormat)

  - [Modify a format to change the name of a generated document](#ModifyToChangeName)
  - [Modify a format to change the order of questions](#ModifyToOrder)
  - [Run a modified format from ER](#RunFormatFromER2)
  - [Complete the format design](#CompleteFormat)

- [Develop application artefacts to call the designed report](#DevelopCustomCode)

  - [Modify source code](#ModifySourceCode)

    - [Add a data contract class](#DataContractClass)
    - [Add a UI builder class](#UIBuilderClass)
    - [Add a data provider class](#DataProviderClass)
    - [Add a labels file](#LabelsFile)
    - [Add a report service class](#ServiceClass)
    - [Add a report controller class](#ControllerClass)
    - [Add a menu item](#MenuItem)
    - [Add a menu item to a menu](#Menu)
    - [Build a Visual Studio project](#BuildVSProject)

  - [Run a format from the application](#RunFormatFromApp)

- [Tune a designed ER solution](#TuneSolution)

  - [Modify a model mapping](#ModifyModelMapping)

    - [Add data sources to access a data contract object](#AddDataSource1)
    - [Add a data source to access ER format mapping records](#AddDataSource2)
    - [Add a data source to access a format mapping record of a running ER format](#AddDataSource3)
    - [Enter the name of the running ER format in the data model](#AddBinding)
    - [Complete the design of the model mapping](#CompleteModelMapping2)

  - [Modify a format](#ModifyFormat)

    - [Add a new format element](#AddFormatElement)
    - [Bind the added format element](#BindAddedFormatElement)
    - [Complete the format design](#CompleteFormat2)

  - [Run a format from the application](#RunFormatFromApp2)
  - [Run a format from ER](#RunFormatFromER3)
  - [Configure a format destination for on-screen preview](#ConfigureDestination)
  - [Run a format from the application to preview it as a PDF document](#RunFormatFromApp3)

- [Additional resources](#References)

In this example, you create a new ER solution for the [Questionnaire](../../../human-resources/hr-learning-questionnaires.md) module. This new ER solution lets you design a report by using a Microsoft Excel worksheet as a template. You can then generate the **Questionnaire** report in Excel or PDF format, in addition to generating the existing SQL Server Reporting Services (SSRS) report. You can also modify the new report later, upon request. No coding is required.

1. To run the existing report, go to **Questionnaire** > **Design** > **Questionnaires report**.

    :::image type="content" source="./media/er-quick-start1-application-menu-origin.png" alt-text="Screenshot of selecting the Questionnaires report menu item in the Questionnaire module to run the existing SSRS report.":::

1. In the **Questionnaires report** dialog box, specify selection criteria. Apply a filter so that the report includes only the **SBCCrsExam** questionnaire.

    :::image type="content" source="./media/er-quick-start1-ssrs-report-dialog.png" alt-text="Screenshot of specifying selection criteria in the Questionnaires report dialog box.":::

The following illustration shows the generated version of the SSRS report for the **SBCCrsExam** questionnaire.

:::image type="content" source="./media/er-quick-start1-ssrs-report.png" alt-text="Screenshot of the generated SSRS report.":::

## <a name="ConfigureFramework"></a>Configure the ER framework

As a user in the Electronic Reporting Developer role, you must configure the minimal set of ER parameters before you can start to use the ER framework to design your new ER solution.

### <a name="ConfigureParameters"></a>Configure ER parameters

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, select **Electronic reporting parameters**.
1. On the **Electronic reporting parameters** page, on the **General** tab, set the **Enable design mode** option to **Yes**.
1. On the **Attachments** tab, set the following parameters:

    - Set the **Configurations** field to **File** for the **USMF** company.
    - Set **Job archive**, **Temporary**, **Baseline**, and **Others** fields to **File**.

For more information about ER parameters, see [Configure the ER framework](electronic-reporting-er-configure-parameters.md).

### <a name="ActivateProvider"></a>Activate an ER configuration provider

Each ER configuration belongs to an ER configuration provider. Therefore, you must activate an ER configuration provider in the **Electronic reporting** workspace before you can add or edit any ER configurations.

> [!NOTE]
> Only the owner of an ER configuration can edit it. Therefore, before you can edit an ER configuration, activate the appropriate ER configuration provider in the **Electronic reporting** workspace.

#### <a name="ReviewProvidersList"></a>Review the list of ER configuration providers

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, in the **Related links** section, select **Configuration providers**.
1. On the **Configuration providers** page, each configuration provider record has a unique name and URL. Review the contents of this page. If a record for **Litware, Inc.** (`https://www.litware.com`) already exists, skip the next procedure, [Add a new ER configuration provider](#ActivateProvider).

#### <a name="AddProvider"></a>Add a new ER configuration provider

1. On the **Configuration providers** page, select **New**.
1. In the **Name** field, enter **Litware, Inc.**
1. In the **Internet address** field, enter `https://www.litware.com`.
1. Select **Save**.

#### <a name="ActivateAddedProvider"></a>Activate an ER configuration provider

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, select the **Litware, Inc.** configuration provider.
1. Select **Set active**.

For more information about ER configuration providers, see [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

## <a name="DesignModel"></a>Design a domain-specific data model

You must create a new ER configuration that contains a data model component for the **Questionnaire** business domain. You use this data model as a data source when you design an ER format to generate the **Questionnaire** report.

By completing the steps in the [Import a new data model configuration](#ImportDataModel) section, you can import the required data model from the provided XML file. Alternatively, you can complete the steps in the [Create a new data model configuration](#DesignDataModel) section to design this data model from scratch.

### <a name="ImportDataModel"></a>Import a new data model configuration

1. Download the [Questionnaires model.version.1.xml](https://download.microsoft.com/download/b/6/3/b633bd34-d200-4422-96d9-8f62eb5218f8/Questionnaires_model.version.1.xml) file, and save it to your local computer.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, select **Reporting configurations**.
1. On the Action Pane, select **Exchange** > **Load from XML file**.
1. Select **Browse**, and then find and select the **Questionnaires model.version.1.xml** file.
1. Select **OK** to import the configuration.

To continue, skip the next procedure, [Create a new data model configuration](#DesignDataModel).

### <a name="DesignDataModel"></a>Create a new data model configuration

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, select **Reporting configurations**.
1. Select **Create configuration**.
1. In the drop-down dialog box, in the **Name** field, enter **Questionnaire model**.
1. Select **Create configuration** to create the configuration.

#### <a name="NameDataModel"></a>Name the data model

1. On **Configurations**, in the configuration tree, select **Questionnaire model**.
1. Select **Designer**.
1. On **Data model designer**, on the **General** FastTab, in the **Name** field, enter <a name="DataModeName"></a>**Questionnaires**.

#### <a name="FieldsEntry"></a>Add new data model fields

1. On **Data model designer**, select **New**.
1. In the drop-down dialog box for adding a data model node, follow these steps:

    1. Select **Model root** as the type of the new node.
    1. In the **Name** field, enter <a name="RootDefinitionName"></a>**Root**.
    1. Select **Add** to add the new node.

    This root descriptor provides data for the **Questionnaire** report. A single data model can have multiple descriptors. Each descriptor can be specified for a single ER format, to identify data that is required to generate the report.

1. Select **New** again. In the drop-down dialog box for adding a data model node, follow these steps:

    1. Select **Child of an active node** as the type of the new node.
    1. In the **Name** field, enter **CompanyName**.
    1. In the **Item type** field, select **String**.
    1. Select **Add** to add the new field.

    This field passes the name of the current company to an ER report that consumes this data model as a data source.

1. Select **New** again. In the drop-down dialog box for adding a data model node, follow these steps:

    1. Select **Child of an active node** as the type of the new node.
    1. In the **Name** field, enter **Questionnaire**.
    1. In the **Item type** field, select **Record list**.
    1. Select **Add** to add the new field.

    This field passes the list of questionnaires to an ER report that consumes this data model as a data source.

1. Select the **Questionnaire** node.
1. Continue to add the required fields of the editable data model in the same manner until you complete the following data model structure.

    | Field path                                                    | Data type   | Field designation/returned value |
    |---------------------------------------------------------------|-------------|----------------------------------|
    | Root                                                          |             | The reference point to request questionnaire data. |
    | Root\\CompanyName                                             | String      | The name of the current company. |
    | Root\\ExecutionContext                                        | Record      | Format execution details. |
    | Root\\ExecutionContext\\FormatName                            | String      | The name of the ER format that is being run. |
    | Root\\Questionnaire                                           | Record list | The list of questionnaires |
    | Root\\Questionnaire\\Active                                   | String      | The status of the current questionnaire. |
    | Root\\Questionnaire\\Code                                     | String      | The code of the current questionnaire. |
    | Root\\Questionnaire\\Description                              | String      | The description of the current questionnaire. |
    | Root\\Questionnaire\\QuestionnaireType                        | String      | The type of the current questionnaire. |
    | Root\\Questionnaire\\QuestionOrder                            | String      | The numerical order of the current questionnaire. |
    | Root\\Questionnaire\\ResultsGroup                             | Record      | The result parameters of the current questionnaire. |
    | Root\\Questionnaire\\ResultsGroup\\Code                       | String      | The identification code of the current result group. |
    | Root\\Questionnaire\\ResultsGroup\\Description                | String      | The description of the current result group. |
    | Root\\Questionnaire\\ResultsGroup\\MaxNumberOfPoints          | Real        | The maximum number of points that can be earned. |
    | Root\\Questionnaire\\Question                                 | Record list | The list of questions for the current questionnaire. |
    | Root\\Questionnaire\\Question\\CollectionSequenceNumber       | Integer     | The sequence number of the current answer collection. |
    | Root\\Questionnaire\\Question\\Id                             | String      | The identification code of the current question. |
    | Root\\Questionnaire\\Question\\MustBeCompleted                | String      | A flag that indicates whether the current question must be answered. |
    | Root\\Questionnaire\\Question\\PrimaryQuestion                | String      | A flag that indicates whether the current question is primary. |
    | Root\\Questionnaire\\Question\\SequenceNumber                 | Integer     | The sequence number of the current question. |
    | Root\\Questionnaire\\Question\\Text                           | String      | The text of the current question. |
    | Root\\Questionnaire\\Question\\Answer                         | Record list | The list of answers for the current question. |
    | Root\\Questionnaire\\Question\\Answer\\CorrectAnswer          | String      | A flag that indicates whether the current answer is correct. |
    | Root\\Questionnaire\\Question\\Answer\\Points                 | Real        | The points that are earned when the current answer is selected. |
    | Root\\Questionnaire\\Question\\Answer\\SequenceNumber         | Integer     | The sequence number of the current answer. |
    | Root\\Questionnaire\\Question\\Answer\\Text                   | String      | The text of the current answer. |

    The following illustration shows the completed editable data model on the **Data model designer** page.

    :::image type="content" source="./media/er-quick-start1-model2.png" alt-text="Screenshot of the configured data model in the ER data model designer.":::

1. Save your changes.
1. Close the **Data model designer** page.

#### <a name="CompleteDataModel"></a>Complete the design of the data model

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, select **Questionnaire model**.
1. On the **Versions** FastTab, select the configuration version that has a status of **Draft**.
1. Select **Change status** > **Complete**.

The status of version 1 of this configuration changes from **Draft** to **Completed**. You can't change version 1 anymore. This version contains the configured data model and can be used as the basis for other ER configurations. Version 2 of this configuration is created and has a status of **Draft**. You can edit this version to adjust the **Questionnaire** data model.

:::image type="content" source="./media/er-quick-start1-model-configuration.png" alt-text="Screenshot of the versions of the editable configuration on the Configurations page.":::

For more information about versioning for ER configurations, see [Electronic reporting (ER) overview](general-electronic-reporting.md).

> [!NOTE]
> The configured data model is your abstract representation of the **Questionnaire** business domain and contains no relations to artifacts that are specific to Microsoft Dynamics 365 Finance.

## <a name="DesignMapping"></a>Design a model mapping for the configured data model

As a user in the Electronic Reporting Developer role, you must create a new ER configuration that contains a model mapping component for the **Questionnaire** data model. Because this component implements the configured data model for Finance, it's Finance-specific. You must configure the model mapping component to specify the application objects that fill the configured data model with application data at runtime. To complete this task, you must be aware of the implementation details of the data structure of the **Questionnaire** business domain in Finance.

By completing the steps in the [Import a new model mapping configuration](#ImportModelMapping) section, you can import the required model mapping configuration from the provided XML file. Alternatively, you can complete the steps in the [Create a new model mapping configuration](#CreateModelMapping) section to design this model mapping from scratch.

### <a name="ImportModelMapping"></a>Import a new model mapping configuration

1. Download the [Questionnaires mapping.version.1.1.xml](https://download.microsoft.com/download/7/b/2/7b258e4e-4bd5-46a4-8114-27419ae4acd8/Questionnaires_mapping.version.1.1.xml) file, and save it to your local computer.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, select **Reporting configurations**.
1. On the Action Pane, select **Exchange** > **Load from XML file**.
1. Select **Browse**, and then find and select the **Questionnaires mapping.version.1.1.xml** file.
1. Select **OK** to import the configuration.

To continue, skip the next procedure, [Create a new model mapping configuration](#CreateModelMapping).

### <a name="CreateModelMapping"></a>Create a new model mapping configuration

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, select **Questionnaire model**.
1. Select **Create configuration**.
1. In the drop-down dialog box, follow these steps:

    1. In **New**, select **Model Mapping based on data model Questionnaires**.
    1. In **Name**, enter **Questionnaire mapping**.
    1. In **Data model definition**, select the **Root** definition.
    1. Select **Create configuration** to create the configuration.

#### <a name="DesignMappingComponent"></a>Design a new model mapping component

1. On **Configurations**, in the configuration tree, select **Questionnaire mapping**.
1. Select **Designer** to open the list of mappings.
1. Select the **Questionnaires mapping** mapping that was automatically added for the **Root** definition.
1. Select **Designer** to start to configure the selected mapping.

A new mapping is automatically added for the **Root** definition. This mapping has the **To model** direction. Therefore, you can use this mapping to fill in a data model with required data.

#### <a name="AddMmDataSource1"></a>Add data sources to access application tables

You must configure data sources to access the application tables that contain questionnaire details.

1. On **Model mapping designer**, in the **Data source types** pane, select **Dynamics 365 for Operations\\Table records**.
1. Add a new data source that you use to access the KMCollection table, where every record represents a single questionnaire:

    1. In the **Data sources** pane, select **Add root**.
    1. In the dialog box, in **Name**, enter **Questionnaire**.
    1. In **Table**, enter **KMCollection**.
    1. Set the **Ask for query** option to **Yes**. You can then specify [filtering](../../fin-ops/get-started/advanced-filtering-query-options.md) options for this table in the system query dialog box at runtime.
    1. Select **OK** to add the new data source.

1. In the **Data source types** pane, select **Dynamics 365 for Operations\\Table records**.
1. Add a new data source that you use to access the KMQuestion table, where every record represents a single question in a questionnaire:

    1. In the **Data sources** pane, select **Add root**.
    1. In the dialog box, in **Name**, enter **Question**.
    1. In **Table**, enter **KMQuestion**.
    1. Select **OK** to add the new data source.

1. In the **Data source types** pane, select **Dynamics 365 for Operations\\Table records**.
1. Add a new data source that you use to access the KMAnswer table, where every record represents a single answer to a question in a questionnaire:

    1. In the **Data sources** pane, select **Add root**.
    1. In **Name**, enter **Answer**.
    1. In **Table**, enter **KMAnswer**.
    1. Select **OK** to add the new data source.

1. In the **Data source types** pane, select **Functions\\Calculated field**.
1. Add a new calculated field that you use to access a record of the KMQuestionResultGroup table from every record of the parent KMCollection table:

    1. In the **Data sources** pane, select **Questionnaire**.
    1. Select **Add**.
    1. In the dialog box, in **Name**, enter **\$ResultGroup**.
    1. Select **Edit formula**.
    1. In the [ER formula editor](general-electronic-reporting-formula-designer.md), in **Formula**, enter **FIRSTORNULL(\@.'\<Relations'.KMQuestionResultGroup)** to use the [path](er-formula-language.md#Paths) of the one-to-many relation between the KMCollection and KMQuestionResultGroup tables.
    1. Select **Save**, and close the formula editor.
    1. Select **OK** to add the new calculated field.

1. In the **Data source types** pane, select **Functions\\Calculated field**.
1. Add a new calculated field that you use to access question records of the KMQuestion table from every record of the parent KMCollectionQuestion table:

    1. In the **Data sources** pane, select **Questionnaire**.
    1. Expand the **\<Relations** node that contains one-to-many relations of the KMCollection table.
    1. Select the related **KMCollectionQuestion** table, and then select **Add**.
    1. In the dialog box, in the **Name** field, enter **\$Question**.
    1. Select **Edit formula**.
    1. In the formula editor, in the **Formula** field, enter **FIRSTORNULL (FILTER(Question, Question.kmQuestionId = \@.kmQuestionId))** to return the appropriate question records from the KMQuestion table.
    1. Select **Save**, and close the formula editor.
    1. Select **OK** to add the new calculated field.

1. In the **Data source types** pane, select **Functions\\Calculated field**.
1. Add a new calculated field that you use to access answer records of the KMAnswer table from every record of the parent KMQuestion table:

    1. In the **Data sources** pane, select **Questionnaire.\<Relations.KMCollectionQuestion.\$Question**, and then select **Add**.
    1. In the dialog box, in the **Name** field, enter **\$Answer**.
    1. Select **Edit formula**.
    1. In the formula editor, in the **Formula** field, enter **FILTER (Answer, Answer.kmAnswerCollectionId = \@.kmAnswerCollectionId)** to return the appropriate answer records from the KMAnswer table.
    1. Select **Save**, and close the formula editor.
    1. Select **OK** to add the new calculated field.

1. In the **Data source types** pane, select **Dynamics 365 for Operations\\Table**.
1. Add a new data source that you use to access methods of the CompanyInfo table. Note that the **find()** method of this table returns a record that represents a company of the current Finance instance that this mapping is called in the context of.

    1. In the **Data sources** pane, select **Add root**.
    1. In the dialog box, in the **Name** field, enter **CompanyInfo**.
    1. In the **Table** field, enter **CompanyInfo**.
    1. Select **OK** to add the new data source.

#### <a name="AddMmDataSource2"></a>Add data sources to access application enumerations

You must configure data sources to access application enumerations and compare their values with values of fields of the **Enumeration** type in the application tables. Use the result of the comparison to fill in appropriate fields of the data model.

1. On the **Model mapping designer** page, in the **Data source types** pane, select **Dynamics 365 for Operations\\Enumeration**.
1. Add a new data source that you use to access values of the **EnumAppNoYes** enumeration:

    1. In the **Data sources** pane, select **Add root**.
    1. In the dialog box, in the **Name** field, enter **EnumAppNoYes**.
    1. In the **Enumeration** field, enter **NoYes**.
    1. Select **OK** to add the new data source.

1. In the **Data source types** pane, select **Dynamics 365 for Operations\\Enumeration**.
1. Add a new data source that you use to access the values of the **KMCollectionQuestionMode** enumeration:

    1. In the **Data sources** pane, select **Add root**.
    1. In the dialog box, in the **Name** field, enter **EnumAppQuestionOrder**.
    1. In the **Enumeration** field, enter **KMCollectionQuestionMode**.
    1. Select **OK** to add the new data source.

#### <a name="AddMmLabels"></a>Add ER labels to generate a report in a specified language

You can add ER labels to configure some of your data sources to return values that depend on the language that is defined in the context of the model mapping's call.

1. On the **Model mapping designer** page, in the **Data sources** pane, select **Answer**, and then select **Edit**.
1. Activate the **Label** field.
1. Select **Translate**.
1. In the **Text translation** dialog box, follow these steps:

    1. In the **Label Id** field, enter **PositiveAnswer**.
    1. In the **Text in default language** field, enter **Yes**.
    1. Select **Translate**.
    1. In the **Label Id** field, enter **NegativeAnswer**.
    1. In the **Text in default language** field, enter **No**.
    1. Select **Translate**.

1. Close the **Text translation** dialog box.
1. Select **Cancel**.

:::image type="content" source="./media/er-quick-start1-adding-labels.png" alt-text="Screenshot of adding ER labels for the editable model mapping.":::

You entered ER labels only for the default language. For information about how to translate ER labels into other languages, see [Design multilingual reports](er-design-multilingual-reports.md).

#### <a name="AddMmDataSource3"></a>Add a data source to transform the results of comparing enumeration values to a text value

Because you must transform the results of the comparison between enumeration values and text values several times for different sources, it's a good idea to configure this logic as a single data source. However, to make this data source reusable, you must then configure it as the parameterized data source. For more information, see [Support parameterized calls of ER data sources of the Calculated field type](er-calculated-field-type.md).

1. On the **Model mapping designer** page, in the **Data source types** pane, select **General\\Empty container**.
1. Add a new container data source:

    1. In the **Data sources** pane, select **Add root**.
    1. In the dialog box, in the **Name** field, enter **Helper**.
    1. Select **OK** to add the new container data source.

1. In the **Data source types** pane, select **Functions\\Calculated field**.
1. Add a new data source:

    1. In the **Data sources** pane, select **Helper**.
    1. Select **Add**.
    1. In the dialog box, in the **Name** field, enter **NoYesEnumToString**.
    1. Select **Edit formula**.
    1. In the formula editor, select **Parameters**.
    1. Follow these steps to specify parameters for the configured expression:

        1. Select **New**.
        1. In the dialog box, in the **Name** field, enter **Argument**.
        1. In the **Type** field, select the **Boolean** data type.
        1. Select **OK**.

    1. In the **Formula** field, enter **IF (Argument = true, \@"GER\_LABEL:PositiveAnswer", \@"GER\_LABEL:NegativeAnswer")** to return the text of the appropriate ER label, depending on the language of the execution context and value of the specified parameter.
    1. Select **Save**, and close the formula editor.
    1. Select **OK** to add the new data source.

:::image type="content" source="./media/er-quick-start1-added-data-sources.png" alt-text="Screenshot of the configured model mapping in the ER model mapping designer.":::

#### <a name="AddMmBindings1"></a>Bind data sources to data model fields

You must bind the configured data sources to the fields of the data model to specify how the data model is filled in with application data at runtime.

1. On the **Model mapping designer** page, in the **Data model** pane, select **CompanyName**.
1. In the **Data sources** pane, expand **CompanyInfo**, and then follow these steps:

    1. Expand the **CompanyInfo.find()** node that represents the **find()** method of the CompanyInfo table.
    1. Select **CompanyInfo.find().Name**.
    1. Select **Bind** to fill in the name of the company that the configured model mapping is called in the context of at runtime.

1. In the **Data model** pane, select **Questionnaire**.
1. In the **Data sources** pane, select **Questionnaire**, and then select **Bind** to fill in questionnaire records.
1. In the **Data model** pane, expand **Questionnaire**, and then follow these steps:

    1. In the **Data model** pane, select **Active**.
    1. In the **Data model** pane, select **Edit**.
    1. In the **Formula** field, enter **Helper.NoYesEnumToString (\@.Active = EnumAppNoYes.Yes)** to fill the text-dependent and language-dependent result of the comparison between enumeration values.

1. Continue to bind data sources to data model fields in the same manner until you achieve the following result.

    | Field path                                              | Data type   | Action | Binding expression |
    |---------------------------------------------------------|-------------|--------|--------------------|
    | CompanyName                                             | String      | Bind   | CompanyInfo.'find()'.Name |
    | Questionnaire                                           | Record list | Bind   | Questionnaire |
    | Questionnaire\\Active                                   | String      | Edit   | Helper.NoYesEnumToString(\@.active = EnumAppNoYes.Yes) |
    | Questionnaire\\Code                                     | String      | Bind   | \@.kmCollectionId |
    | Questionnaire\\Description                              | String      | Bind   | \@.Description |
    | Questionnaire\\QuestionnaireType                        | String      | Bind   | \@.'&gt;Relations'.kmCollectionTypeId.Description |
    | Questionnaire\\QuestionOrder                            | String      | Edit   | CASE (\@.questionMode,<br>EnumAppQuestionOrder.Conditional, "Conditional",<br>EnumAppQuestionOrder.Random, "Random (percentage in questionnaire)",<br>EnumAppQuestionOrder.RandomGroup, "Random (percentage in result groups)",<br>EnumAppQuestionOrder.Sequence, "Sequential",<br>"") |
    | Questionnaire\\ResultsGroup                             | Record      |        | |
    | Questionnaire\\ResultsGroup\\Code                       | String      | Bind   | \@.'\$ResultGroup'.kmQuestionResultGroupId |
    | Questionnaire\\ResultsGroup\\Description                | String      | Bind   | \@.'\$ResultGroup'.description |
    | Questionnaire\\ResultsGroup\\MaxNumberOfPoints          | Real        | Bind   | \@.'\$ResultGroup'.maxPoint |
    | Questionnaire\\Question                                 | Record list | Bind   | \@.'&lt;Relations'.KMCollectionQuestion |
    | Questionnaire\\Question\\CollectionSequenceNumber       | Integer     | Bind   | \@.answerCollectionSequenceNumber |
    | Questionnaire\\Question\\Id                             | String      | Bind   | \@.kmQuestionId |
    | Questionnaire\\Question\\MustBeCompleted                | String      | Edit   | Helper.NoYesEnumToString(\@.mandatory = EnumAppNoYes.Yes) |
    | Questionnaire\\Question\\PrimaryQuestion                | String      | Bind   | \@.parentQuestionId |
    | Questionnaire\\Question\\SequenceNumber                 | Integer     | Bind   | \@.SequenceNumber |
    | Questionnaire\\Question\\Text                           | String      | Bind   | \@.'\$Question'.text |
    | Questionnaire\\Question\\Answer                         | Record list | Bind   | \@.'\$Question'.'\$Answer' |
    | Questionnaire\\Question\\Answer\\CorrectAnswer          | String      | Edit   | Helper.NoYesEnumToString(\@.correctAnswer = EnumAppNoYes.Yes) |
    | Questionnaire\\Question\\Answer\\Points                 | Real        | Bind   | \@.point |
    | Questionnaire\\Question\\Answer\\SequenceNumber         | Integer     | Bind   | \@.sequenceNumber |
    | Questionnaire\\Question\\Answer\\Text                   | String      | Bind   | \@.text |

    The following illustration shows the final state of the configured model mapping on the **Model mapping designer** page.

    :::image type="content" source="./media/er-quick-start1-mapping2.png" alt-text="Screenshot of the fully configured model mapping in the ER model mapping designer.":::

1. Save your changes.
1. Close the **Model mapping designer** page.

#### <a name="CompleteModelMapping"></a>Complete the design of the model mapping

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, select **Questionnaire mapping**.
1. On the **Versions** FastTab, select the configuration version that has a status of **Draft**.
1. Select **Change status** > **Complete**.

The status of version 1.1 of this configuration changes from **Draft** to **Completed**. You can no longer change version 1.1. This version contains the configured model mapping and can be used as the basis for other ER configurations. Version 1.2 of this configuration is created and has a status of **Draft**. You can edit this version to adjust the **Questionnaire mapping** configuration.

:::image type="content" source="./media/er-quick-start1-mapping-configuration.png" alt-text="Screenshot of the versions of the editable ER configuration on the Configurations page.":::

> [!NOTE]
> The configured model mapping is your Finance-specific implementation of the abstract data model that represents the **Questionnaire** business domain.

## <a name="DesignReportTemplate"></a>Design a template for a custom report

The ER framework uses predefined templates to generate reports in Microsoft Office formats (Excel workbooks or Word documents). While generating the required report, the framework fills the template with the required data according to the configured dataflow. Therefore, you must first design a template for your custom report. Design this template as an Excel workbook, the structure of which represents the layout of a custom report. Name every Excel item that you plan to fill with required data.

1. Download the [Questionnaires report template.xlsx](https://download.microsoft.com/download/3/8/2/382c3cf0-87bb-473f-b7bb-3015b4facb74/Questionnaires_report_template.xlsx) file, and save it to your local computer.
1. Open the file in Excel, and review the structure of the workbook.

As the following illustration shows, the downloaded template is designed to print specified questionnaires that present a questionnaire's questions together with appropriate answers.

:::image type="content" source="./media/er-quick-start1-template-layout.png" alt-text="Screenshot of the Excel template to print specified questionnaires.":::

Excel names are added to this template to fill in the questionnaire details. Use Name Manager to review the Excel names.

:::image type="content" source="./media/er-quick-start1-template-names.png" alt-text="Screenshot of using Name Manager to review Excel names in the provided Excel template.":::

Report labels are added as fixed text in the English language. You can replace the report labels with new Excel names that fill in the labels with language-dependent text by using the ER format [labels](#AddMmLabels), as you did for language-dependent expressions in the configured model mapping. In this case, ER labels must be added in the editable ER format.

As the following illustration shows, the custom report header is specified to enable Excel to do paging.

:::image type="content" source="./media/er-quick-start1-template-header.png" alt-text="Screenshot of the custom report header in the provided Excel template.":::

## <a name="DesignFormat"></a>Design a format

As a user in the Electronic Reporting Functional Consultant role, you must create a new ER configuration that contains a format component. You must configure the format component to specify how a report template is filled with required data at runtime.

By completing the steps in the [Import a designed format configuration](#FormatImport) section, you can import the required format from the provided XML file. Alternatively, you can complete the steps in the [Create a new format configuration](#FormatCreate) section to design this format from scratch.

### <a name="FormatImport"></a>Import a designed format configuration

1. Download the [Questionnaires format.version.1.1.xml](https://download.microsoft.com/download/1/b/a/1ba39ec2-257a-44d8-972f-25bf7d18fb41/Questionnaires_format.version.1.1.xml) file, and save it to your local computer.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Electronic reporting** workspace, select **Reporting configurations**.
1. On the Action pane, select **Exchange** > **Load from XML file**.
1. Select **Browse**, and then find and select the **Questionnaires format.version.1.1.xml** file.
1. Select **OK** to import the configuration.

To continue, skip the next procedure, [Create a new format configuration](#FormatCreate).

### <a name="FormatCreate"></a>Create a new format configuration

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, select **Questionnaire model**.
1. Select **Create configuration**.
1. In the drop-down dialog box, follow these steps:

    1. In **New**, select **Format based on data model Questionnaires**.
    1. In **Name**, enter **Questionnaire report**.
    1. In **Data model version**, select **1**.

        > [!NOTE]
        > - If you select a specific version of the base data model, the structure of the corresponding version of the data model appears as the structure of the **Model** data source in the format that you create.
        > - You can leave this field blank. In that case, the structure of the **Draft** version of the data model appears as the structure of the **Model** data source in the format that you create. You can then adjust your model and immediately see those adjustments in your format. This approach might improve the efficiency of ER solution design when you configure your data model, model mapping, and format simultaneously.
        > - If you select a specific version of the base data model, you can switch to using the **Draft** version later, when you start to edit a format.

    1. In **Data model definition**, select the **Root** definition.

1. Select **Create configuration** to create the configuration.

#### <a name="ImportReportTemplate"></a>Import a report template

1. On **Configurations**, in the configuration tree, select **Questionnaire report**.
1. Select **Designer** to start to configure a custom format.
1. On **Format designer**, on the Action Pane, select **Import** > **Import from Excel**.
1. In the dialog box, follow these steps:

    1. Select **Add template**.
    1. Find and select the locally saved **Questionnaires report template.xslx** file, and then select **Open**.
    1. Select **OK** to import the template.

    :::image type="content" source="./media/er-quick-start1-template-import.png" alt-text="Screenshot of importing a report template.":::

The **Excel\\File** format element is automatically added to the editable format as a root element. Additionally, either the **Excel\\Range** format element or the **Excel\\Cell** format element is automatically added for every recognized Excel name of the imported template. The **Excel\\Header** format that has the nested **String** element is automatically added to reflect the header settings of the imported template.

:::image type="content" source="./media/er-quick-start1-template-import2.png" alt-text="Screenshot of the format structure that includes automatically added elements in the ER Operation designer.":::

#### <a name="ConfigureFormat"></a>Configure a format

1. On **Format designer**, in the format tree, select the **Excel** root element.
1. On the **Format** tab, in the **Name** field, enter <a name="AddFormatRootElement"></a>**Report**.
1. In the **Language preference** field, select **User preference** to run the report in the user's preferred language.
1. In the **Culture preference** field, select **User preference** to run the report in the user's preferred culture.

    For information about how to specify the language and culture contexts for an ER process, see [Design multilingual reports](er-design-multilingual-reports.md).

    :::image type="content" source="./media/er-quick-start1-template-format-structure1.png" alt-text="Screenshot of configuring language and culture settings for the designed report in the ER Operation designer.":::

1. In the format tree, expand the root node, and then select **ResultsGroup**.
1. On the **Format** tab, in the **Replication direction** field, select **No replication**, because you don't expect to have multiple result groups for a single questionnaire.

    :::image type="content" source="./media/er-quick-start1-template-format-structure2.png" alt-text="Screenshot of defining the replication direction for Range format elements in the ER Operation designer.":::

1. Select **Save**.

#### <a name="DefineFormatBindings"></a>Define the data binding for a report title

You must specify a data binding for a format element that fills in the title of a generated report.

1. On **Format designer**, on the **Mapping** tab, select the **Report\\ReportTitle** element.
1. Select **Edit formula**.
1. In the formula editor, select **Translate**.
1. In the **Text translation** dialog box, follow these steps:

    1. In the **Label ID** field, enter **ReportTitle**.
    1. In the **Text in default language** field, enter **Questionnaires report**.
    1. Select **Translate**, and then select **Save**.
    1. Select **Translate** to close the **Text translation** dialog box.

1. Close the formula editor.

    :::image type="content" source="./media/er-quick-start1-add-report-title-label.png" alt-text="Screenshot of configuring the binding to fill in the title of a generated report.":::

Use this technique to make all other labels of the current template language-dependent. For information about how to translate the added labels of a single ER configuration into all supported languages, see [Design multilingual reports](er-design-multilingual-reports.md).

#### <a name="ReviewModelDataSource"></a>Review model data source

1. On the **Format designer** page, on the **Mapping** tab, select the <a name="ModelDSName"></a>**model** data source that represents the base data model of this ER format.
1. Select **Edit**.
1. Review the information in the **Data source properties** dialog box. This data source represents version 1 of the **Questionnaires** data model component that resides in the **Questionnaires model** ER configuration.

:::image type="content" source="./media/er-quick-start1-model-data-source.png" alt-text="Screenshot of the properties of the model data source in the ER Operation designer.":::

#### <a name="BindFormatElements"></a>Bind format elements to data source fields

To specify how a template is filled in at runtime, bind every format element that is associated with an appropriate Excel name to a single field of this format's data source.

1. On the **Format designer** page, in the format tree, select the **Report\\CompanyName** format element.
1. On the **Mapping** tab, select the **model.CompanyName** data source field of the **String** type.
1. Select **Bind** to enter a company name in a template.
1. In the format tree, select the **Report\\Questionnaire** element.
1. On the **Mapping** tab, select the **model.Questionnaire** data source field of the **Record list** type.
1. Select **Bind**.
1. Select **Show details** to see more details for format elements.

    The **Questionnaire** range format element is configured as vertically replicated. When it's bound to a data source of the **Record list** type, the appropriate **Questionnaire** range of the Excel template is repeated for every record of the bound data source.

    :::image type="content" source="./media/er-quick-start1-bindings1.png" alt-text="Screenshot of binding the Questionnaire range format element to the appropriate Record list data sources in the ER Operation designer.":::

    Because the **Questionnaire** range of the Excel template is defined between rows 5 through 14, these rows are repeated for every reported questionnaire.

    :::image type="content" source="./media/er-quick-start1-template-questionnaire-range.png" alt-text="Screenshot of rows in the Excel template that will be repeated in a generated report for every record of the Record list data sources.":::

1. Configure similar bindings for the remaining format elements, as described in the following table.

    > [!NOTE]
    > In this table, the information in the "Data source path" column assumes that the [relative path](relative-path-data-bindings-er-models-format.md) ER feature is turned on.

    | Format element path                                      | Data source path |
    |----------------------------------------------------------|------------------|
    | Excel\\ReportTitle                                       | **\@"GER\_LABEL:ReportTitle"** |
    | Excel\\CompanyName                                       | **model.CompanyName** |
    | Excel\\Questionnaire                                     | **model.Questionnaire** |
    | Excel\\Questionnaire\\Active                             | **\@.Active**, where **\@** is **model.Questionnaire** |
    | Excel\\Questionnaire\\Code                               | **\@.Code** |
    | Excel\\Questionnaire\\Description                        | **\@.Description** |
    | Excel\\Questionnaire\\QuestionnaireType                  | **\@.QuestionnaireType** |
    | Excel\\Questionnaire\\QuestionOrder                      | **\@.QuestionOrder** |
    | Excel\\Questionnaire\\ResultsGroup\\Code\_               | **\@.ResultsGroup.Code** |
    | Excel\\Questionnaire\\ResultsGroup\\Description\_        | **\@.ResultsGroup.Description** |
    | Excel\\Questionnaire\\ResultsGroup\\MaxNumberOfPoints    | **\@.ResultsGroup.MaxNumberOfPoint** |
    | Excel\\Questionnaire\\Question                           | **\@.Question** |
    | Excel\\Questionnaire\\Question\\CollectionSequenceNumber | **\@.CollectionSequenceNumber**, where **\@** is **model.Questionnaire.Question** |
    | Excel\\Questionnaire\\Question\\Id                       | **\@.Id** |
    | Excel\\Questionnaire\\Question\\MustBeCompleted          | **\@.MustBeCompleted** |
    | Excel\\Questionnaire\\Question\\PrimaryQuestion          | **\@.PrimaryQuestion** |
    | Excel\\Questionnaire\\Question\\SequenceNumber           | **\@.SequenceNumber** |
    | Excel\\Questionnaire\\Question\\Text                     | **\@.Text** |
    | Excel\\Questionnaire\\Question\\Answer                   | **\@.Answer** |
    | Excel\\Questionnaire\\Question\\Answer\\CorrectAnswer    | **\@.CorrectAnswer**, where **\@** is **model.Questionnaire.Answer** |
    | Excel\\Questionnaire\\Question\\Answer\\Points           | **\@.Points** |
    | Excel\\Questionnaire\\Question\\Answer\\Text             | **\@.Text** |

1. When you finish, select **Save**.

The following illustration shows the final state of the configured data bindings on the **Format designer** page.

:::image type="content" source="./media/er-quick-start1-bindings2.png" alt-text="Screenshot of the configured data bindings in the ER Operation designer.":::

> [!IMPORTANT]
> The whole collection of specified data sources and bindings represents a format mapping component of the configured format. This format mapping is called when you run the configured format for report generation.

### <a name="RunFormatFromER"></a>Run a designed format from ER

You can now run a designed format for testing purposes from the **Configurations** page.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On the **Configuration** page, in the configuration tree, expand **Questionnaire model**, and then select **Questionnaire report**.
1. Select **Designer** for the format version that has a status of **Draft**.
1. On the **Format designer** page, select **Run**.
1. In the **ER parameters** dialog box, on the **Records to include** FastTab, configure the filtering option so that only the **SBCCrsExam** questionnaire is included.
1. Select **OK** to confirm the filter.
1. Select **OK** to run the report.
1. Review the generated report.

By [default](electronic-reporting-destinations.md#default-behavior), a generated report is delivered as an Excel file that you can download. The following illustrations show two pages of the generated report in Excel format.

:::image type="content" source="./media/er-quick-start1-report1a.png" alt-text="Screenshot of an example of a generated report in Excel format, page 1.":::

:::image type="content" source="./media/er-quick-start1-report1b.png" alt-text="Screenshot of an example of a generated report in Excel format, page 2.":::

## <a name="TuneFormat"></a>Tune a designed format

### <a name="ModifyToChangeName"></a>Modify a format to change the name of a generated document

By default, the alias of the current user names a generated document. When you modify the format, you can change this behavior so that a generated document is named based on your custom logic. For example, the name of a generated document can be based on the current session date and time, and on the report's title.

1. On **Format designer**, select the **Report** root item.
1. On the **Mapping** tab, select **Edit file name**.
1. In the **Formula** field, enter `CONCATENATE (\@"GER_LABEL:ReportTitle", " - ", DATETIMEFORMAT(SESSIONNOW(), "yyyy-MM-dd hh-mm-ss"))`.
1. Select **Save**, and close the formula editor.
1. Select **Save**.

### <a name="ModifyToOrder"></a>Modify a format to change the order of questions

The questions don't appear in the correct order in a generated report. You can change the order by modifying the format.

1. On **Format designer**, select the **Report** root item.
1. On the **Mapping** tab, in the format tree, expand **Report\\Questionnaire\\Question**.

    :::image type="content" source="./media/er-quick-start1-bindings3.png" alt-text="Screenshot of the Question format element of the Range type in the ER Operation designer.":::

1. On the **Mapping** tab, select **model.Questionnaire**.
1. Select **Add** \> **Functions\\Calculated field**, and then, in the **Name** field, enter **OrderedQuestions**.
1. Select **Edit formula**.
1. In the formula editor, in the **Formula** field, enter **ORDERBY (model.Questionnaire.Question, model.Questionnaire.Question.SequenceNumber)** to order the list of questions of the current questionnaire by the sequence order number.
1. Select **Save**, and close the formula editor.
1. Select **OK** to complete the entry of a new calculated field.
1. On the **Mapping** tab, select **model.Questionnaire.OrderedQuestions**.
1. In the format tree, select **Excel\\Questionnaire\\Question**.
1. Select **Bind**, and then confirm that the current **model.Questionnaire.Questions** path is replaced by the new **model.Questionnaire.OrderedQuestions** path in all bindings of nested elements.
1. Select **Save**.

:::image type="content" source="./media/er-quick-start1-bindings4.png" alt-text="Screenshot of binding the Question format element to the configured OrderedQuestions data source in the ER Operation designer.":::

### <a name="RunFormatFromER2"></a>Run a modified format from ER

You can now run a modified format for testing purposes from the ER framework.

1. On the **Format designer** page, select **Run**.
1. In the **ER parameters** dialog box, on the **Records to include** FastTab, configure the filtering option so that only the **SBCCrsExam** questionnaire is included.
1. Select **OK** to confirm the filter.
1. Select **OK** to run the report.
1. Review the generated report.

The following illustration shows a generated report in Excel format where the questions are correctly ordered.

:::image type="content" source="./media/er-quick-start1-report2.png" alt-text="Screenshot of the generated report in Excel format that has correctly ordered questions.":::

### <a name="CompleteFormat"></a>Complete the format design

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, expand **Questionnaire model**, and then select **Questionnaire report**.
1. On the **Versions** FastTab, select the configuration version that has a status of **Draft**.
1. Select **Change status** > **Complete**.

The status of version 1.1 of this configuration changes from **Draft** to **Completed**. You can no longer change version 1.1. This version contains the configured format and can be used to print your custom report. Version 1.2 of this configuration is created and has a status of **Draft**. You can edit this version to adjust the format of your **Questionnaire** report.

:::image type="content" source="./media/er-quick-start1-format-configuration.png" alt-text="Screenshot of the editable ER configuration on the Configurations page.":::

> [!NOTE]
> The configured format is your design of the **Questionnaire** report and contains no relations to the Finance-specific artefacts.

## <a name="DevelopCustomCode"></a>Develop application artifacts to call the designed report

As a user in the System Administrator role, you must develop new logic so that the configured ER format can be called from the application user interface (UI) to generate your custom report. Currently, ER doesn't offer any capability for configuring this type of logic. Therefore, some engineering work is required.

To develop the new logic, you must deploy a topology that supports continuous build. For more information, see [Deploy topologies that support continuous build and test automation](../perf-test/continuous-build-test-automation.md). You must also have access to the development environment for this topology. For more information about the available ER API, see [ER framework API](er-apis-app73.md).

### <a name="ModifySourceCode"></a>Modify source code

#### <a name="DataContractClass"></a>Add a data contract class

Add the new **QuestionnairesErReportContract** class to your Visual Studio project. Write code that specifies the data contract to use for running the configured ER format.

```xpp
/// <summary>
///     This class is the data contract class for the <c>QuestionnairesErReportDP</c> class.
/// </summary>
/// <remarks>
///    This is the data contract class for the Questionnaires ER report.
/// </remarks>
[
    DataContractAttribute,
    SysOperationContractProcessingAttribute(classStr(QuestionnairesErReportUIBuilder))
    ]
    public class QuestionnairesErReportContract extends ERFormatMappingRunBaseContract implements SysOperationValidatable
{
    ERFormatMappingId formatMapping;

    /// <summary>
    ///    Validates the report parameters.
    /// </summary>
    /// <returns>
    ///    true if no errors; otherwise, false.
    /// </returns>
    public boolean validate()
    {
        boolean ret = true;
        if (!formatMapping)
        {
            ret = checkFailed(strFmt("@SYS26332", new SysDictType(extendedTypeNum(ERFormatMappingId)).label()));
        }
        return ret;
    }
    [
        DataMemberAttribute('FormatMapping'),
        SysOperationLabelAttribute(literalstr("@ElectronicReporting:FormatMapping")),
        SysOperationHelpTextAttribute(literalstr("@ElectronicReporting:FormatMapping"))
    ]
    public ERFormatMappingId parmFormatMapping(ERFormatMappingId _formatMapping = formatMapping)
    {
        formatMapping = _formatMapping;
        return formatMapping;
    }
}
```

#### <a name="UIBuilderClass"></a>Add a UI builder class

Add the new **QuestionnairesErReportUIBuilder** class to your Visual Studio project. Write code to generate a runtime dialog box that looks up the format mapping ID of the ER format to run. The provided code looks up only ER formats that contain a data source of the **Data model** type that refers to the **[Questionnaires](#DataModeName)** data model by using the **[Root](#RootDefinitionName)** definition.

> [!NOTE]
> Alternatively, you can use ER integration points to filter ER formats. For more information, see [API to show a format mapping lookup](er-apis-app10-0-11.md#api-to-show-a-format-mapping-lookup).

```xpp
/// <summary>
/// The UIBuilder class for Questionnaires ER report
/// </summary>
class QuestionnairesErReportUIBuilder extends SysOperationAutomaticUIBuilder
{
    public const str ERQuestionnairesModel = 'Questionnaires';
    public const str ERQuestionnairesDataContainer = 'Root';

    /// <summary>
    /// Action after build of the dialog UI.
    /// </summary>
    public void postBuild()
    {
        DialogField formatMapping;
        super();
        formatMapping = this.bindInfo().getDialogField(this.dataContractObject(),
            methodStr(QuestionnairesErReportContract, parmFormatMapping));
        formatMapping.registerOverrideMethod(
            methodStr(FormReferenceControl, lookupReference),
            methodStr(QuestionnairesErReportUIBuilder, formatMappingLookup),
            this);
    }

    /// <summary>
    /// Performs the lookup form for format mapping.
    /// </summary>
    /// <param name="_referenceGroupControl">
    /// The control to perform lookup form.
    /// </param>
    public void formatMappingLookup(FormReferenceControl _referenceGroupControl)
    {
        ERObjectsFactory::createFormatMappingTableLookupForControlAndModel(
            _referenceGroupControl,
            ERQuestionnairesModel,
            ERQuestionnairesDataContainer).performFormLookup();
    }
}
```

#### <a name="DataProviderClass"></a>Add a data provider class

Add the new **QuestionnairesErReportDP** class to your Visual Studio project. Write code that introduces the data provider to use for running the configured ER format. The provided code includes only the data contract for this data provider.

```xpp
/// <summary>
/// Data provider class for Questionnaires ER report.
/// </summary>
public class QuestionnairesErReportDP
{
    QuestionnairesErReportContract contract;
    public static QuestionnairesErReportDP construct()
    {
        QuestionnairesErReportDP  dataProvider;
        dataProvider = new QuestionnairesErReportDP();
        return dataProvider;
    }
}
```

#### <a name="LabelsFile"></a>Add a labels file

Add the new **QuestionnairesErReportLabels\_en-US** labels file to your Visual Studio project. Specify the following labels for new UI resources:

- The **\@QuestionnairesReport** label for a new menu item that contains the following text in US English (en-US): **Questionnaires report (powered by ER)**
- The **\@QuestionnairesReportBatchJobDescription** label for a batch job title if a selected ER format is scheduled for execution as a batch job

#### <a name="ServiceClass"></a>Add a report service class

Add the new **QuestionnairesErReportService** class to your Visual Studio project. Write code that calls an ER format, identifies it by a format mapping ID, and provides a data contract as a parameter.

```xpp
using Microsoft.Dynamics365.LocalizationFramework;
/// <summary>
/// The electronic reporting service class for Questionnaires ER report
/// </summary>
class QuestionnairesErReportService extends SysOperationServiceBase
{
    public const str ERModelDataSourceName = 'model';
    public const str DefaultExportedFileName = 'Questionnaires report';
    public const str ParametersDataSourceName = 'RunTimeParameters';

    /// <summary>
    /// Generates report by using Electronic reporting framework
    /// </summary>
    /// <param name = "_contract">The Questionnaires report contract</param>
    public void generateReportByGER(QuestionnairesErReportContract _contract)
    {
        ERFormatMappingId formatMappingId;
        QuestionnairesErReportDP  dataProvider;
        dataProvider = QuestionnairesErReportDP::construct();
        formatMappingId = _contract.parmFormatMapping();
        if (formatMappingId)
        {
            try
            {
                ERIModelDefinitionParamsAction parameters = new ERModelDefinitionParamsUIActionComposite()
                    .add(new ERModelDefinitionObjectParameterAction(ERModelDataSourceName, ParametersDataSourceName, _contract, true));

                // Call ER to generate the report.
                ERIFormatMappingRun formatMappingRun = ERObjectsFactory::createFormatMappingRunByFormatMappingId(formatMappingId, DefaultExportedFileName);
                if (formatMappingRun.parmShowPromptDialog(true))
                {
                    formatMappingRun.withParameter(parameters);
                    formatMappingRun.withFileDestination(_contract.getFileDestination());
                    formatMappingRun.run();
                }
            }
            catch
            {
                // An error occurred while exporting data.
                error("@SYP4861341");
            }
        }
        else
        {
            // There is no data available.
            info("@SYS300117");
        }
    }
}
```

When you use an ER format that runs application data, you must configure a data source of the **Data model** type in the format mapping. This data source refers to a specific part of the specified data model by using a single root definition. When the ER format runs, it calls this data source to access the appropriate ER model mapping that is configured for a given model and root definition.

You can pass all the information you prepare in the source code and store as part of the data contract to the running ER format by using an ER model mapping of this type. In the ER model mapping, you must configure a data source of the **Object** type that refers to the **[QuestionnairesErReportContract](#DataContractClass)** class. To identify a model mapping, you must specify a data source that calls this model mapping. In the provided code, this data source is specified by the **ERModelDataSourceName** constant that has the **[model](#ModelDSName)** value. To identify which data source is used to expose the data contract in the model mapping, you must specify a data source name. In the provided code, this name is specified by the **ParametersDataSourceName** constant that has <a name="DataContractDSName"></a>**RunTimeParameters** value.

> [!NOTE]
> In a new environment, you might have to refresh the ER metadata so that this type of class is available in the ER model mapping designer. For more information, see [Configure the ER framework](electronic-reporting-er-configure-parameters.md#frequently-asked-questions).

#### <a name="ControllerClass"></a>Add a report controller class

Add the new **QuestionnairesErReportController** class to your Visual Studio project. Write code that runs an ER format in either synchronous mode or batch mode, as you prefer, in the dialog box that is built based on the logic of the provided **QuestionnairesErReportUIBuilder** class.

```xpp
/// <summary>
/// The controller for Questionnaires ER report
/// </summary>
class QuestionnairesErReportController extends ERFormatMappingRunBaseController
{
    /// <summary>
    /// The main entrance of the controller
    /// </summary>
    /// <param name = "args">The arguments</param>
    public static void main(Args args)
    {
        QuestionnairesErReportController operation;
        operation = new QuestionnairesErReportController(
            classStr(QuestionnairesErReportService),
            methodStr(QuestionnairesErReportService, generateReportByGER),
            SysOperationExecutionMode::Synchronous);
        operation.startOperation();
    }

    /// <summary>
    /// Gets caption of the dialog.
    /// </summary>
    /// <returns>Caption of the dialog</returns>
    public ClassDescription defaultCaption()
    {
        ClassDescription batchDescription;
        batchDescription = "Questionnaires report (powered by ER)";
        return batchDescription;
    }
}
```

#### <a name="MenuItem"></a>Add a menu item

Add the new **QuestionnairesErReport** menu item to your Visual Studio project. In the **Object** property, this menu item refers to the **QuestionnairesErReportController** class. Use it to specify a user permission to select and run an ER format. In the **Label** property, this menu item refers to the **\@QuestionnairesReport** label that you created earlier, so that correct text is presented in the application UI.

#### <a name="Menu"></a>Add a menu item to a menu

Add the existing **KM** menu to your Visual Studio project. Add a new **QuestionnairesErReport** item of the **Output** type to this menu. This item must refer to the **QuestionnairesErReport** menu item that is described in the previous section.

#### <a name="BuildVSProject"></a>Build a Visual Studio project

Build your project to make the new menu item available to users.

### <a name="RunFormatFromApp"></a>Run a format from the application

1. Go to **Questionnaire** > **Design** > **Questionnaires report (powered by ER)**.

    ![Selecting the Questionnaires report (powered by ER) menu item in the Questionnaire module to run the configured ER format.](./media/er-quick-start1-application-menu-modified.png)

1. In the dialog box, in the **Format mapping** field, select **Questionnaires report**.
1. Select **OK**.
1. In the **Electronic report parameters** dialog box, on the **Records to include** FastTab, set the filter so that it includes only the **SBCCrsExam** questionnaire.
1. Select **OK** to confirm the filter.
1. Select **OK** to run the report.

    ![Specifying the selection criteria in the Electronic report dialog box.](./media/er-quick-start1-report-run-dialog-page.png)

1. Review the generated report.

## <a name="TuneSolution"></a>Tune a designed ER solution

Modify the configured ER solution so that it uses the data provider class you developed to access details of the running ER format. Also, make it enter the name of this ER format in a generated report.

### <a name="ModifyModelMapping"></a>Modify a model mapping

#### <a name="AddDataSource1"></a>Add data sources to access a data contract object

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, expand **Questionnaire model**, and then select **Questionnaire mapping**.
1. Select **Designer** to open **Model to datasource mapping**.
1. Select **Designer** to open the selected mapping in the model mapping designer.
1. On **Model mapping designer**, in the **Data source types** pane, select **Dynamics 365 for Operations\\Object**.
1. In the **Data sources** pane, select **Add root**.
1. In the dialog box, in the **Name** field, enter **[RunTimeParameters](#DataContractDSName)**, as defined in the source code of the **QuestionnairesErReportService** class.
1. In the **Class** field, enter **[QuestionnairesErReportContract](#DataContractClass)**, which you coded earlier.
1. Select **OK**.
1. Expand **RunTimeParameters**.

The added data source provides information about the record ID of the running ER format mapping.

:::image type="content" source="./media/er-quick-start1-mapping3.png" alt-text="Screenshot of the added data source in the ER model mapping designer.":::

#### <a name="AddDataSource2"></a>Add a data source to access ER format mapping records

Continue to edit the selected model mapping by adding a data source to access ER format mapping records.

1. On **Model mapping designer**, in the **Data source types** pane, select **Dynamics 365 for Operations\\Table records**.
1. In the **Data sources** pane, select **Add root**.
1. In the dialog box, in the **Name** field, enter **ER1**.
1. In the **Table** field, enter **ERFormatMappingTable**.
1. Select **OK**.

#### <a name="AddDataSource3"></a>Add a data source to access a format mapping record of a running ER format

Continue to edit the selected model mapping by adding a data source to access the format mapping record of the running ER format.

1. On **Model mapping designer**, in the **Data source types** pane, select **Functions\\Calculated field**.
1. In the **Data sources** pane, select **Add root**.
1. In the dialog box, in the **Name** field, enter **ER2**.
1. Select **Edit formula**.
1. In the formula editor, in the **Formula** field, enter **FIRSTORNULL (FILTER(ER1, ER1.RecId = RunTimeParameters.parmFormatMapping))**.
1. Select **Save**, and close the formula editor.
1. Select **OK**.

#### <a name="AddBinding"></a>Enter the name of the running ER format in the data model

Continue to edit the selected model mapping so that the name of the running ER format is entered in the data model.

1. On **Model mapping designer**, in the **Data model** pane, expand **ExecutionContext**, and then select **ExecutionContext\\FormatName**.
1. In the **Data model** pane, select **Edit** to configure a data binding for the selected data model's field.
1. In the formula editor, in the **Formula** field, enter **FIRSTORNULL (ER2.'\>Relations'.Format).Name**.
1. Select **Save**, and close the formula editor.

Because you used the **FormatName** field, the configured model mapping now exposes the name of an ER format that calls this model mapping during execution.

:::image type="content" source="./media/er-quick-start1-mapping4.png" alt-text="Screenshot of binding the data model field to the method of the added data source in the ER model mapping designer.":::

#### <a name="CompleteModelMapping2"></a>Complete the design of the model mapping

1. On **Model mapping designer**, select **Save**.
1. Close the page.
1. Close the model mappings page.
1. On **Configurations**, in the configuration tree, make sure that the **Questionnaire mapping** configuration is still selected. Then, on the **Versions** FastTab, select the configuration version that has a status of **Draft**.
1. Select **Change status** > **Complete**.

The status of version 1.2 of this configuration changes from **Draft** to **Completed**. You can't change version 1.2 anymore. This version contains the configured model mapping and can be used as the basis for other ER configurations. Version 1.3 of this configuration is created and has a status of **Draft**. You can edit this version to adjust the **Questionnaire** model mapping.

### <a name="ModifyFormat"></a>Modify a format

You can modify the configured ER format so that its name appears in the footer of a report that is generated when the ER format runs.

#### <a name="AddFormatElement"></a>Add a new format element

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, expand **Questionnaire model**, and then select **Questionnaire report**.
1. Select **Designer**.
1. On **Format designer**, select the **Report** root item.
1. Select **Add** to add a new nested format element for the selected **Report** root item.
1. Select **Excel\\Footer**.
1. In the **Name** field, enter **Footer**.
1. Select **Report\Footer**, and then select **Add**.
1. Select **Text\\String**.

#### <a name="BindAddedFormatElement"></a>Bind the added format element

1. On **Format designer**, on the **Mapping** tab, in the format tree, for the active **Footer\\String** element, select **Edit formula**.
1. In the formula editor, in the **Formula** field, enter `CONCATENATE ("\&C\&10", FORMAT("Generated by'\%1' ER solution", model.ExecutionContext.FormatName))`.
1. Select **Save**, and close the formula editor.
1. Select **Save**.

You modified the configured format so that its name is entered in the footer of a generated report by using the **Footer\\String** element.

:::image type="content" source="./media/er-quick-start1-template-format-structure3.png" alt-text="Screenshot of adding the Footer format element to the configured format in the ER Operation designer.":::

#### <a name="CompleteFormat2"></a>Complete the format design

1. Close **Format designer**.
1. On **Configurations**, in the configuration tree, make sure that the **Questionnaire report** configuration is still selected. Then, on the **Versions** FastTab, select the configuration version that has a status of **Draft**.
1. Select **Change status** > **Complete**.

The status of version 1.2 of this configuration changes from **Draft** to **Completed**. You can no longer change version 1.2. This version contains the configured format and can be used as the basis for other ER configurations. Version 1.3 of this configuration is created and has a status of **Draft**. You can edit this version to adjust the **Questionnaire** report.

### <a name="RunFormatFromApp2"></a>Run a format from the application

1. Go to **Questionnaire** > **Design** > **Questionnaires report (powered by ER)**.
1. In the dialog box, in the **Format mapping** field, select **Questionnaires report**.
1. Select **OK**.
1. In the **ER parameters** dialog box, on the **Records to include** FastTab, set the filter so that it includes only the **SBCCrsExam** questionnaire.
1. Select **OK** to confirm the filter.
1. Select **OK** to run the report.
1. Review the generated report in Excel format.

The footer of the generated report contains the name of the ER format that was used to generate it.

![Generated report in Excel format.](./media/er-quick-start1-report4.png)

### <a name="RunFormatFromER3"></a>Run a format from ER

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On **Configurations**, in the configuration tree, expand **Questionnaire model**, and then select **Questionnaire report**.
1. On the Action Pane, select **Run**.
1. In the **Electronic report parameters** dialog box, on the **Records to include** FastTab, set the filter so that it includes only the **SBCCrsExam** questionnaire.
1. Select **OK** to confirm the filter.
1. Select **OK** to run the report.
1. Review the generated report in Excel format.

The footer of the generated report doesn't contain the name of ER format that was used to generate it, because the running model mapping wasn't passed the data contract object when the ER format called it.

### <a name="ConfigureDestination"></a>Configure a format destination for on-screen preview

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting destination**.
1. On **Electronic reporting destination**, add a destination record for the configured **Questionnaire report** ER format.
1. On the **File destination** FastTab, set up the **Screen** [destination](er-destination-type-screen.md) for the **Report** format component that you [added](#AddFormatRootElement) as the root element of the configured **Questionnaire report** ER format.
1. On the **PDF conversion settings** FastTab, configure the destination to convert a report to [PDF format](er-output-conversion-to-pdf.md) that uses the **Landscape** page orientation.

:::image type="content" source="./media/er-quick-start1-destination.png" alt-text="Screenshot of configuring the custom Screen destination for the ER format on the Electronic reporting destination page.":::

### <a name="RunFormatFromApp3"></a>Run a format from the application to preview it as a PDF document

1. Go to **Questionnaire** > **Design** > **Questionnaires report (powered by ER)**.
1. In the dialog box, in the **Format mapping** field, select **Questionnaires report**.
1. Select **OK**.
1. In the **Electronic report parameters** dialog box, on the **Records to include** FastTab, set the filter so that it includes only the **SBCCrsExam** questionnaire.
1. Select **OK** to confirm the filter.

    On the **Destinations** FastTab, notice that the **Output** field is set to **Screen**. If you want to change the configured destination, select **Change**.

    ![ER report runtime dialog box where you can change the configured destination.](./media/er-quick-start1-run-settings.png)

1. Select **OK** to run the report.
1. Review the generated report in PDF format.

    ![On-screen preview of the generated report in PDF format.](./media/er-quick-start1-preview-PDF.png)

## <a name="References"></a>Additional resources

- [Electronic Reporting overview](general-electronic-reporting.md)
- [Electronic reporting formula language](er-formula-language.md)
- [Design multilingual reports](er-design-multilingual-reports.md)
- [ER framework API](er-apis-app73.md)
- [CASE function](er-functions-logical-case.md)
- [CONCATENATE function](er-functions-text-concatenate.md)
- [DATETIMEFORMAT function](er-functions-datetime-datetimeformat.md)
- [FILTER function](er-functions-list-filter.md)
- [FIRSTORNULL function](er-functions-list-firstornull.md)
- [FORMAT function](er-functions-text-format.md)
- [IF function](er-functions-logical-if.md)
- [ORDERBY function](er-functions-list-orderby.md)
- [SESSIONNOW function](er-functions-datetime-sessionnow.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
