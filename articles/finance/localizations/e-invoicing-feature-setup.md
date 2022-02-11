---
# required metadata

title: Work with feature setup
description: This topic provides description of the process of setting up the Electronic invoicing feature.
author: dkalyuzh
ms.date: 12/15/2021
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
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Work with feature setup

[!include [banner](../includes/banner.md)]


To set up the process of generating electronic files and additional processing steps including digital signing, submission to the government Web service, receiving a response, or storing the file, set up the electronic invoicing features **Processing pipeline**, **Applicability rules**, and **Variables**.

The setup information is combined in the **Feature setup** concept and can be created, deleted, adjusted. Additionally, for the completed versions of electronic invoicing features, the information can also be viewed. 

You can create as many **Feature setup** items as needed to define different scenarios of electronic files generation, processing, and receiving. While these setup items have independent processing actions and conditions for execution, they are created as a part of an individual electronic invoicing feature, and inherit the lifecycle and deployment process.

## Add new Feature setup
To add new **Feature setup**, complete the following steps.

1. Select an electronic invoicing feature version that is in a state of **Draft**.
2. On the **Setups** tab, select **Add**. You will see a dialog with several options.
 
   - **Custom setup**: A new feature setup is created with empty channels, an empty processing pipeline list, an empty section of applicability rules, and a default set of variables.
   
     1. Enter a name and description for the fature setup item.
     2. Select the setup type.
     
     	- **Processing pipeline** - Select this main type of feature setup to generate and process outbound electronic documents. For this setup type, the system creates an empty processing pipeline list, an empty section of applicability rules, and a default set of variables. You will not be able to work with the channels for inbound electronic documents.
       - **Data channel** - Select this type of feature setup to set up the process of receiving inbound electronic documents from one of the defined channels and then pass these electronic documents directly to Finance or Supply Chain management without additional actions. For this setup type, the system creates a pre-defined list of parameters for the data channels, an empty section of applicability rules, and a set of default variables. You will not be able to add any actions in the processing pipeline.
      - **Data channel and processing pipeline** - Select this setup type which is similar to Data channel, but differs in one way. Before passing an inbound electronic document to Finance or Supply Chain management, you can set up additional actions in the processing pipeline.				
      - **From feature setup** - Select this setup type to have the system create a copy from another feature setup in the scope of the current electronic invoicing feature.
    
    > [!NOTE]
    > For the setup types, **Data channel** and **Data channel and processing pipeline**, provide the channel to integrate with in the **Select data channel**.
		
 3. Select **Create**. Now you can select **Edit** and configure the created feature setup.


## Edit feature setup
Depending on the type of feature setup, you can configure the process of outbound electronic file generation and submission to external channels, or the process of inbound document receipt and passing to your Dynamics 365 Finance or Dynamics 365 Supply Chain Management application.

### Data channel

The data channel takes the electronic file and processes it or directly passes it to Finance or Supply Chain management. This option isn't available when the feature setup type is **processing pipeline**. 

To set up the data channel, provide the name of the channel, and depending on the selected channel type, define the parameters.
The data channel identifier must refer to the variable that's created specifically for the data channel identification and will be used in Finance or Supply Chain Management as a reference.

In the **Attachments** filter tab you should define a set of filters to get particular files from the channel. You can create several lines if you expect that there will be files of a different extension, or must be processed differently based on the file name. The main parameters are:
 - **Name** - a name of the file that the system will refer to during the processing, and in Finance and Supply chain management applications you will be able to see the files in the Submission log
 - **Filter** - define the filter to select files
 - **Optional** - If the flag is not set, system will generate an error if the channels will not contain the file that correspond to the Filter (applicable for e-mails)

If a channel is mail box, and inbound e-mail contains several attachments, you can configure the rules - the service will consider each attachment as a separate electronic invoice, or it will determine only one attached file as a main invoice, and other documents will be considered as additions. 


### Processing pipeline

To set up the process to generate electronic files and perform steps such as digital signing, and submission to external web services with the parsing responses, or receiving inbound documents and processing them, work with the **processing pipeline**. This is a set of **Actions** that will be executed one after another until the steps are successfully completed.

The list of **Actions** is predefined. You can add any combination that will logically define the process of the document submission or receiving by selecting **New** or **Delete**.

The order of the **Actions** is important and can be adjusted by selecting **Up** or **Down**.

Each Action has a set of parameters, specific for the action type, and can be setup or adjusted. 

 - **Action** - Select the type of the action available.
 - **Action name** - Enter the name of the action that will be seen by users in submission logs or in other messages in Finance and Supply Chain management applications
 - **Description** - provide more details on the goal of the particular action in the process
 - **Enable retry** - activating of the checkbox makes it possible to select an action in **Retry action** field and additional parameters in **Retry parameters** tab.
   - Retry functionality allows you to configure the behavior of the service when particular action can't be executed. For example, if external Web service you are trying to connect to, doesn't respond, you can define how many times with which interval the system will retry to connect starting from which action in the pipeline.
 - **Export results** - one of the actions in the Processing pipeline can be marked with this flag, that will enable the possibility to export the resulted electronic file of this Action in Finance and Supply chain management application in Electronic documents submission log form.


### Applicability rules

Applicability rules are configurable clauses that provide a context for executing electronic invoicing features through the Electronic Invoicing capability set.
When a business document from Finance or Supply Chain management is submitted to electronic invoicing, the business document doesn't carry an explicit reference that allows the Electronic Invoicing capability set to call a particular **Electronic invoicing feature** version and **Feature setup** item to process the submission.
Nevertheless, when properly configured, the business document contains the necessary elements that allow electronic invoicing to resolve which electronic invoicing feature version and particular processing pipeline must be selected and run.

Applicability rules allow the Electronic Invoicing service to find the exact electronic invoicing features that must be used to process the submission. This is done by matching the **Context** fields from the submitted business document with the clauses from the **Applicability rules**.

1. Select **New** to add a new clause to a set of **Applicability rules**.
2. Select **Delete** to delete a clause.
3. Select several records and use **Group** or **Ungroup** to combine items or logical statements. For example, select the lines you want to group, and select **Group clause**. When clauses are grouped, a new column is added to the grid. This column specifies the logical operator for the grouped clause
4. When you ungroup a clause, always start from the innermost grouping level.
	
   The supported types of operator:
   - Equal
   - Not equal
   - Greater than/Less than
   - Greater than or equal to/Less than or equal to
   - Contains
   - Begin with


### Variables
You can add variables to add more flexibility in setting up the processing pipeline and data flow among **Actions**. When you have a variable, you can refer to it in some of the **Actions** parameters to temporarily store data or electronic files. 

Some variables are used to pass data between Finance or Supply Chain management applications and the electronic invoicing service. 
The system creates some variables by default. For example, the **BusinessDocumentDataModel** variable contains business data in a JSON structure that comes in the call from the connected application in the submission process.

**Type**

- **Constant** - A container for storing temporary data that is being used in the processing pipeline actions.
- **From client** - The content of the variable is acquired from the Dynamics 365 client when the submission process is executed.
- **To client** - The content of the variable is made available for import by the Dynamics 365 client when the submission process is executed.
- **Data type** - Select the data type of the information stored in the variable.

### Parameters
The parameter, **Disable business data reduction** is responsible for optimizing the structure of the business data payload that comes from Finance or Supply Chain management application during electronic document submission. Optimization reduces the data coming in to the electronic invoicing service for further transformation to the required electronic file. The default value of the parameter field is **No**.
 
   - **Yes** - If the field is set to **Yes**, Finance or Supply Chain management sends a JSON file of **Invoice Model** or **Fiscal Model** (for Brazil) structure that's defined in the **Electronic reporting** module. All elements of the Model are populated with business data on the application side regardless of the final electronic file structure. Models usually contain more business data than is required by the target file structure, and generating this data in the application can take more time. This option is required when you want to generate different output files within one electronic invoicing feature and feature setup. This is a rare scenario. This option if useful when you troubleshoot your scenarios and the structure of the electronic files and completeness of the business data.
   - **No** - If the field is set to **No**, Finance or Supply Chain management makes the first call to the service without any business data. The goal is to get information about what Electronic reporting configuration for electronic file transformation will be used in the processing pipeline. This information is returned back to the application and instructs what subset of business data should be included in the JSON file of the **Invoice Model** or **Fiscal Model** (for Brazil) structure. The option limits the volume of business data that the application submits to the service by providing only the business data that is necessary to successfully generate an electronic file.


### Validate feature setup
On the **Feature version setup** page, on the Action Pane, select **Validate** to validate the feature version setup.

The validation checks the consistency of the whole configuration. For example, if a specific parameter for an action is mandatory but its value remains blank, the validation detects this inconsistency, and you receive a warning.

## Delete a feature setup
Complete the following steps to delete a feature setup.
 1. Select an electronic invoicing feature version that is in a state of **Draft**.
 2. On the **Setups** tab, select **Delete**.
 4. Select **Yes** in the dialog box to confirm that you want to delete the feature setup.

