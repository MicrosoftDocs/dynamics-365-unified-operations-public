---
# required metadata

title: Work with Feature setup
description: This topic provides description of the process of setting up the Electronic invoicing feature.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Work with Feature setup

[!include [banner](../includes/banner.md)]


To setup the process of electronic file generation and further steps of its processing (like digital signing, sending to the government Web service and receiving response, or storing it in SharePoint), you should setup electronic invoicing feature **Processing pipeline**, **Applicability rules**, and **Variables**.

The setup information is combined to the **Feature setup** concept and can be created, deleted, adjusted, and for the completed versions of electronic invoicing features - viewed. 

You can create as many **Feature setup** items as you need to define different scenarios of electronic files generation, processing, and receiving. While all these setup items will bear independent processing actions and conditions for execution, they will be created as a part of an individual electronic invoicing feature, and inherit lifecycle and deployment process.

## Add new Feature setup
To add new **Feature setup**, follow the steps:
 1. Select electronic invoicing feature version in **Draft** state
 2. Go to **Setups** tab
 3. Select **Add** menu item
 4. You will see a dialog with several options:


 5. **New** options:
   - **Custom setup**: a new Feature setup will be created with empty Channels, empty Processing pipeline list, empty section of Applicability rules, and default set of Variables, depending on the Setup type
   
     a. Enter Feature setup item **Name** and **Description**
     
     b. Select Setup type:
     - **Processing pipeline** - is the main type of Feature setup for generation and processing of outbound electronic documents.
       
       The system will create empty Processing pipeline list, empty section of Applicability rules, and default set of Variables for this type. You will not be able to work with the channels for inbound electronic documents.
     - **Data channel** - is the type of Feature setup, that allows to setup the process of receiving inbound electronic documents from one of the defined channels and pass these electronic documents directly to Finance and Supply Chain management applications without additional actions
       
       The system will create predefined list of parameters for the Data channels, empty section of Applicability rules, and a set of default Variables for this channel. You will not be able to add any actions in the Processing pipeline.
	
     - **Data cannel and processing pipeline** - the similar type as Data channel, but before passing over an inbound electronic document to Finance and Supply Chain management applications, you will be able to setup additional actions in the Processing pipeline.
      
        For options Data channel and Data cannel and processing pipeline you must provide the channel to integrate with in **Select data channel** parameter.
				
   - **From feature setup** - system will create a copy from another Feature setup in scope of the current electronic invoicing feature.
		
 6. Select **Create** button

	Now you can select **Edit** and configure the created Feature setup.


## Edit Feature setup
Depending on the type of the Feature setup you will be able to configure the process of outbound electronic files generation and submission to external channels, or the process of inbound document receiving and passing over to Finance and Supply Chain management applications.

### Data channel

Data channel is aimed to listen to Data channels, take electronic file from it, and process the file further, or directly pass it to Finance and Supply Chain management. This option is not available for **Processing pipeline** type of the Feature setup. 
Provide the name of the channel, and then depending on the selected channel type, define **Parameters**.
Data channel identifier must refer to the **Variable**, created specifically for the data channel identification, that will also be used in Finance and Supply Chain management applications as a reference.

In the **Attachments** filter tab you should define a set of filters to get particular files from the channel. You can create several lines if you expect that there will be files of a different extension, or must be processed differently based on the file name. The main parameters are:
 - **Name** - a name of the file that the system will refer to during the processing, and in Finance and Supply chain management applications you will be able to see the files in the Submission log
 - **Filter** - define the filter to select files
 - **Optional** - If the flag is not set, system will generate an error if the channels will not contain the file that correspond to the Filter (applicable for e-mails)

If a channel is mail box, and inbound e-mail contains several attachments, you can configure the rules - the service will consider each attachment as a separate electronic invoice, or it will determine only one attached file as a main invoice, and other documents will be considered as additions. 


### Processing pipeline

![image](https://user-images.githubusercontent.com/78973132/146725727-7f8f0e7b-d115-4619-a103-1b07b297b25c.png)

To setup the process of electronic file generation and performing steps like digital signing, and submission to external web services with the parsing responses, or receiving inbound documents and processing them, you should work with the **Processing pipeline**. This is a set of **Actions** that will be executed one after another until successful completion of failing.
The list of **Actions** is predefined and you can add any combination that logically will define the process of the document submission or receiving by selecting **New** or **Delete** buttons. 
The order of the **Actions** is important and can be adjusted by **Up** and **Down** buttons.
Each Action has a set of parameters, specific for the action type, and can be setup or adjusted. 

 - **Action** - select the type of the Action available currently
 - **Action nam**e - define the name of the action that will be seen by users in submission logs or in other messages in Finance and Supply Chain management applications
 - **Description** - provide more details on the goal of the particular action in the process
 - **Enable retry** - activating of the checkbox makes it possible to select an action in **Retry action** field and additional parameters in **Retry parameters** tab.
   - Retry functionality allows you to configure the behavior of the service when particular action can't be executed. For example, if external Web service you are trying to connect to, doesn't respond, you can define how many times with which interval the system will retry to connect starting from which action in the pipeline.
 - **Export results** - one of the actions in the Processing pipeline can be marked with this flag, that will enable the possibility to export the resulted electronic file of this Action in Finance and Supply chain management application in Electronic documents submission log form.


### Applicability rules

**Applicability rules** are configurable clauses that provide a context for execution of electronic invoicing features through the Electronic Invoicing capability set.
When a business document from Finance or Supply Chain management application is submitted to electronic invoicing, the business document doesn't carry an explicit reference that allows the Electronic Invoicing capability set to call a particular **Electronic invoicing feature** version and **Feature setup** item to process the submission.
Nevertheless, when properly configured, the business document contains the necessary elements that allow electronic invoicing to resolve which electronic invoicing feature version and particular Processing pipeline must be selected and run.
**Applicability rules** allow the Electronic Invoicing service to find the exact electronic invoicing features that must be used to process the submission. This is done by matching the **Context** fields from the submitted business document with the clauses from the **Applicability rules**.

 - Select **New** button to add a new clause to the set of **Applicability rules**.
 - **Delete** - delete the clause.
 - Select several records and use Group clause/Ungroup clause to combine items to Or/And logical statements as it is represented in the example:
   - Select lines you want to group, and select **Group clause** button
  
   - When clauses are grouped, a new column is added to the grid. This column specifies the logical operator for the grouped clause
		

  When you ungroup a clause, always start from the innermost grouping level.
	
  The supported types of operator:
  - Equal
  - Not equal
  - Greater than/Less than
  - Greater than or equal to/Less than or equal to
  - Contains
  - Begin with


### Variables
You can add variables to add more flexibility in setting up **Processing pipeline** and data flow among **Actions**. As soon as you have a variable, you can refer to it in some of actions' parameters to temporary store data or electronic files. 
Also, some of the variables are used for passing data between Finance and Supply Chain management applications and electronic invoicing service. 
System creates some of the variables by default. As an example, ***BusinessDocumentDataModel*** variable contains business data in JSON structure that comes in the call from the connected application in the submission process.

  **Type**:
  - Constant - container for storing temporary data being used in the processing pipeline actions.
  - From client - The content of the variable is acquired from the Microsoft Dynamics 365 client during execution of the submission process.
  - To client - The content of the variable is made available for import by the Microsoft Dynamics 365 client during execution of the submission process.
  - Data type - you should select data type of the information stored in the variable.



### Parameters
Parameter **Disable business data reduction** is responsible for optimization the structure of the business data payload that comes from Finance and Supply Chain management applications during electronic document submission. Optimization is done by reducing data coming to electronic invoicing service for further transformation to required electronic file. Default value is No.
 - Yes - Finance and Supply Chain management applications send JSON file of Invoice Model or Fiscal Model (for Brazil) structure defined in Electronic reporting module. All elements of the Model will be populated with business data on the application side regardless of the final electronic file structure. Usually, Models contain more business data that is required by the target file structure, and generation of this data in the application can take more time. This option is required in the scenarios when you want to generate different output files within one electronic invoicing feature and feature setup, while it is a rare case. Also, this option if useful when you troubleshoot your scenarios and the structure of the electronic files and completeness of the business data.
 - No - in this case Finance and Supply Chain management applications make the first call to the service without any business data, with the goal to get information - what Electronic reporting configuration for electronic file transformation will be used in the Processing pipeline. This information will be returned back to the application and instruct what the subset of business data should be included into JSON file of Invoice Model or Fiscal Model (for Brazil) structure. The option limits the volume of business data that application submits to the service, providing only necessary business data for successful electronic file generation.


### Validate Feature setup
On the **Feature version setup** page, on the Action Pane, select **Validate** to validate the feature version setup.

The validation checks the consistency of the whole configuration. For example, if a specific parameter for an action is mandatory but its value remains blank, the validation detects this inconsistency, and you receive a warning.



## Delete Feature setup
To delete a **Feature setup**, follow the steps:
 1. Select electronic invoicing feature version in Draft state.
 2. Go to **Setups** tab.
 3. Select **Delete** menu item.
 4. Confirm deletion of the **Feature setup** by selecting **Yes** in the dialog.

