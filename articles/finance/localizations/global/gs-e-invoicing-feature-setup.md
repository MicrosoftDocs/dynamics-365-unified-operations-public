---
title: Configure feature setups
description: Learn how to set up Electronic invoicing features, including outlines and step-by-step processes for adding feature setups and editing feature setups.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 01/29/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.39
---

# Configure feature setups

[!INCLUDE[banner](../../includes/banner.md)]

To set up the generation of electronic files and other processing steps (for example, digitally signing files, submitting them to the government web service and receiving a response, or storing them), set up the processing pipeline, applicability rules, and variables for Electronic invoicing features.

The setup information is combined in the *feature setup* concept, and can be created, deleted, and adjusted. For the completed versions of Electronic invoicing features, the information can also be viewed.

You can create as many feature setup items as you require to define different scenarios for generating, processing, and receiving electronic files. Although these feature setup items have independent processing actions and conditions for execution, they're created as part of a single Electronic invoicing feature and inherit its lifecycle and deployment process.

## Add a feature setup

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. On the **Electronic invoicing features** page, select an Electronic invoicing feature version that has a status of **Draft**.
1. On the **Setups** tab, select **Add**.
1. In the **Create feature setup** dropdown dialog box, in the **New** field group, select one of the following options:

    - **Custom setup** – Create a new feature setup that has empty channels, an empty processing pipeline list, an empty section for applicability rules, and a default set of variables, depending on the setup type.
    - **From feature setup** – Create a copy of another feature setup in the scope of the current Electronic invoicing feature.

1. If you selected the **Custom setup** option in the last step, enter a name and description of the feature setup item, and then, in the **Setup type** field group, select one of the following options:

    - **Processing pipeline** – Select this option to generate and process outbound electronic documents. For this setup type, the system creates an empty processing pipeline list, an empty section for applicability rules, and a default set of variables. You won't be able to work with the channels for inbound electronic documents.
    - **Import channel** – Select this option to set up the process of receiving inbound electronic documents from one of the defined channels and passing them directly to Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management without additional actions. For this setup type, the system creates a predefined list of parameters for the data channels, an empty section for applicability rules, and a set of default variables. You won't be able to add any actions in the processing pipeline.
    - **Import channel and processing pipeline** – This setup type resembles the **Import channel** setup type. However, before an inbound electronic document is passed to Finance or Supply Chain Management, you can set up additional actions in the processing pipeline.
    - **Export channel and processing pipeline** – You can set up additional actions in the processing pipeline for outbound electronic documents that are submitted from Finance or Supply Chain Management.

1. If you selected the **Import channel**, **Import channel and processing pipeline**, or **Export channel and processing pipeline** option in the last step, in the **Select data channel** field, you must select the channel to integrate with.
1. Select **Create**.

After a feature setup is created, you can select **Edit** to configure it.

## Edit a feature setup

Depending on the type of feature setup, you can configure the process of generating outbound electronic files and submitting them to external channels, or the process of receiving inbound documents and passing them to your Finance or Supply Chain Management application.

### Import channel

An *import channel* either processes the electronic file or passes it directly to Finance or Supply Chain Management. This option isn't available for feature setups of the **Processing pipeline** type.

To set up an import channel, enter the name of the channel. Then define the parameters, based on the selected channel type. The import channel identifier must refer to the variable that's created specifically to identify the import channel. It will be used as a reference in Finance or Supply Chain Management.

On the **Attachments filter** tab, you should define a set of filters to get specific files from the channel. You can create several lines if you expect that files will have different file name extensions, or if files must be processed differently depending on the file name. Here are the main parameters:

- **Name** – Enter the name of the file that the system will refer to during processing. In the Finance and Supply Chain Management applications, the files are shown in the submission log.
- **Filter** – Define the filter to select files.
- **Optional** – If this checkbox is cleared, the file is required. In this case, the system shows an error message if the channels don't contain files that correspond to the filter. This parameter is applicable to emails.

If the channel is a mailbox, and an inbound email contains several attachments, you can configure rules to define how the service should handle the attachments. The service can consider each attachment a separate electronic invoice, or it can treat one attachment as a main invoice and all other attachments as additions.

### Processing pipeline

A *processing pipeline* is a set of *actions* that are run sequentially until they're successfully completed. You can use a processing pipeline to set up the process of generating electronic files and performing other steps (for example, digitally signing files, submitting them to external web services and parsing the response, and receiving and processing inbound documents).

The list of actions is predefined. You can use the **New** and **Delete** buttons to specify the combination of actions that logically defines the required process for submitting or receiving documents.

The order of actions is important. You can adjust the order by using the **Up** and **Down** buttons.

Each action has a set of parameters that you can configure or adjust. The specific set of parameters depends on the type of action.

- **Action** – Select the type of action.
- **Action name** – Enter the name of the action. This name appears in submission logs, and in messages in Finance and Supply Chain Management applications.
- **Description** – Provide more details about the purpose of the action in the process.
- **Enable retry** – If you select this checkbox, you can select an action in the **Retry action** field and configure additional parameters on the **Retry parameters** tab.

    Retry functionality lets you configure the service's behavior if a specific action can't be run. For example, if the external web service that you're trying to connect to doesn't respond, you can specify how many times the system should reattempt the connection, at what interval, and from what action in the processing pipeline.

- **Export results** – You can select this checkbox for *one* action in the processing pipeline. The electronic file that the action produces in the Finance or Supply Chain Management application can then be exported from the **Electronic documents submission log** page.

### Applicability rules

*Applicability rules* are configurable clauses that provide context for running Electronic invoicing features through the Electronic Invoicing capability set. Business documents that are submitted from Finance or Supply Chain Management to Electronic invoicing don't carry an explicit reference that enables the Electronic Invoicing capability set to call a specific version of an Electronic invoicing feature and a specific feature setup item to process the submission. However, when a business document is correctly configured, it contains the required elements that enable Electronic invoicing to determine which Electronic invoicing feature version and processing pipeline must be selected and run.

Applicability rules enable the Electronic Invoicing service to find the exact Electronic invoicing features that must be used to process a submission. To find the correct features, the service matches the **Context** fields from the submitted business document against clauses from the applicability rules.

You can work with applicability rules in the following ways:

- Select **New** to add a new clause to a set of applicability rules.
- Select **Delete** to delete a clause.
- Select several records, and then use the **Group** or **Ungroup** button to create a combination of items or logical statements. For example, select the lines that you want to group, and then select **Group clause**. When clauses are grouped, a new column is added to the grid. This column specifies the logical operator for the grouped clause. The following operators are supported:

    - Equal
    - Not equal
    - Greater than
    - Less than
    - Greater than or equal to
    - Less than or equal to
    - Contains
    - Begin with

    > [!NOTE]
    > When you ungroup a clause, always start from the innermost grouping level.

### Variables

*Variables* give you more flexibility when you set up a processing pipeline and the data flow among actions. You can refer to a variable in some action parameters to temporarily store data or electronic files. Some variables are used to pass data between the Finance or Supply Chain Management application and the Electronic Invoicing service.

The system creates some variables by default. For example, the **BusinessDocumentDataModel** variable contains business data in a JavaScript Object Notation (JSON) structure. This data comes in the call from the Finance application during the submission process.

The following types of variables are available:

- **Constant** – The variable is a container for storing temporary data that's used in processing pipeline actions.
- **From client** – The content of the variable is acquired from the Dynamics 365 client when the submission process is run.
- **To client** – The content of the variable is made available for import by the Dynamics 365 client when the submission process is run.
- **Data type** – Select the data type of the information that's stored in the variable.

### Parameters

The **Disable business data reduction** option is used to optimize the structure of the business data payload that comes from the Finance or Supply Chain Management application during electronic document submission. Optimization helps reduce the data that goes into the Electronic Invoicing service for further transformation into the required electronic file. The default value is **No**.

- **Yes** – Finance or Supply Chain Management sends a JSON file of the **Invoice Model** or, for Brazil, **Fiscal Model** structure that's defined in the **Electronic reporting** module. All elements of the model are filled with business data on the application side, regardless of the structure of the final electronic file. Models usually contain more business data than the target file structure requires, and more time can be required to generate this data in the application. A value of **Yes** for this option is required in the rare event where you want to generate different output files in one Electronic invoicing feature and feature setup. A value of **Yes** is useful when you troubleshoot your scenarios, the structure of the electronic files, and completeness of the business data.
- **No** – Finance or Supply Chain Management makes the first call to the service without any business data. The purpose of this call is to get information about the Electronic reporting (ER) configuration that will be used for electronic file transformation in the processing pipeline. This information is returned to the application, which uses it to determine the subset of business data that should be included in the JSON file of the **Invoice Model** or, for Brazil, **Fiscal Model** structure. A value of **No** for this option helps reduce the volume of business data that the application submits to the service, because the application can submit only the business data that's required to successfully generate an electronic file.

### Validate a feature setup

You can run validation to check the consistency of the whole configuration. For example, if a mandatory parameter for an action was left blank, the validation detects this inconsistency, and you receive a warning message.

- On the **Feature version setup** page, on the Action Pane, select **Validate**.

## Delete a feature setup

1. On the **Electronic invoicing features** page, select an Electronic invoicing feature version that has a status of **Draft**.
1. On the **Setups** tab, select **Delete**.
1. In the message box that appears, select **Yes** to confirm that you want to delete the feature setup.
