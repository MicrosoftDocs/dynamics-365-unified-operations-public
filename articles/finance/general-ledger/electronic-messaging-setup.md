---
title: Set up Electronic messages
description: This article provides information about how to set up Electronic messages (EM) functionality.
author: AdamTrukawka
ms.date: 11/18/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 2021-06-23
ms.dyn365.ops.version: 8.1
---

# Set up Electronic messages

[!include [banner](../includes/banner.md)]

The **Electronic messages** (EM) functionality helps you maintain different electronic reporting processes for different document types. In some complex scenarios that support [country/region-specific reporting features](electronic-messaging.md#country-specific-regulatory-features-supported-by-the-em-functionality), the EM functionality is set up so that it has a combination of many message statuses, message items statuses, actions, additional fields, and executable classes. For these scenarios, packages of data entities are available for import. If you use these data entity packages, import them into a legal entity by using the Data management tool. For more information about how to use the Data management tool, see [Data management](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

If you don't import a data entity package, you can manually set up the EM functionality. In this case, you must set up the following elements:

- [Number sequences](#sequences)
- [Message item types](#types)
- [Message item statuses](#item)
- [Message statuses](#statuses)
- [Additional fields](#additional)
- [Executable class settings](#executable)
- [Populate records actions](#populate)
- [Populate records from multiple companies](#multiple-companies-populate)
- [Web applications](#applications)
- [Web service settings](#settings)
- [Message processing actions](#actions)
- [Electronic message processing](#processing)

The following sections provide more information about each of these elements.

## <a id="sequences"></a>Number sequences

Set up number sequences for both messages and message items. The number sequences are then used to automatically number messages and message items. The numbers that are assigned are used as unique identifiers for the messages and message items in the system. You can set up number sequences for electronic messaging by going to **General ledger** \> **Ledger setup** \> **General ledger parameters**.

## <a id="types"></a>Message item types

Message item types identify the types of records that are used in electronic messages. You can set up message item types by going to **Tax** \> **Setup** \> **Electronic messages** \> **Message item types**.

## <a id="item"></a>Message item statuses

Message item statuses identify the statuses that apply to message items in the processing that you're setting up. You can set up message item statuses by going to **Tax** \> **Setup** \> **Electronic messages** \> **Message item statuses**.

The **Allow delete** parameter of a message item status defines whether you can delete message items that have this status on the **Electronic messages** page or the **Electronic message items** page.

## <a id="statuses"></a>Message statuses

Set up the message statuses that should be available in message processing. You can set up message statuses by going to **Tax** \> **Setup** \> **Electronic messages** \> **Message statuses**.

The following table describes the fields on the **Message statuses** page.

| Field name          | Description |
|---------------------|-------------|
| Message status      | Enter a unique name for the message status. Message statuses are used to characterize the state of an electronic message at every moment. The name that you enter is shown on the **Electronic messages** page and in a log that is related to electronic messages. |
| Description         | Enter a description of the message status. |
| Response type       | Select the response type for the message status. Some actions in a processing can produce more than one response type. For example, an action of the **Web service** type can produce responses of the **Successfully executed** type or the **Technical error** type, depending on the result of its execution. In this case, define message statuses for both response types. For more information about action types and the types of responses that are related to them, see the [Message processing action types](#action-types) section later in this article. |
| Message item status | Sometimes, the status of an electronic message must influence the status of related message items. Select a message item status in this field to associate it with the message status. |
| Allow delete        | Select this checkbox if users should be able to delete electronic messages that have this status on the **Electronic messages** page. |

## <a id="additional"></a>Additional fields

The EM functionality lets you collect records from transactional tables in Microsoft Dynamics 365 Finance as message items. In this way, you can prepare the records for reporting and then report them. However, transactional tables sometimes don't have enough information to fill in records in a manner that meets the reporting requirements. To fill in all the information that must be reported for a record, you can set up additional fields. Additional fields can be associated with messages and message items. You can set up additional fields by going to **Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**.

The following table describes the general fields on the **Additional fields** page.

| Field       | Description |
|-------------|-------------|
| Field name  | Enter the name of an additional field for electronic messages or message items that are related to the process. This name is shown in the user interface (UI) while you work with the process. The name can also be used in Electronic reporting (ER) configurations that are related to the process. |
| Description | Enter a description of the additional field. |
| User edit   | Set this option to **Yes** if users should be able to change the value of the additional field in the UI. |
| Counter     | Set this option to **Yes** if the additional field should contain a number sequence in an electronic message. The value of the additional field is automatically filled in when an action of the **Electronic reporting export** type is run. |
| Hidden      | Set this option to **Yes** if the additional field should be hidden in the UI on the **Electronic messages** page or the **Electronic message items** page. |

On the **Values** FastTab, you can predefine values that an additional field can have. These values are then available for users to select. Therefore, they don't have to be manually filled in during processing. The following table describes the fields.

| Field                | Description |
|----------------------|-------------|
| Field value          | Enter the field value to use for a message or message item during reporting. |
| Description          | Enter a description of the field value. |
| Account type         | Some field values might be limited to specific account types. Select one of the following values: **All**, **Customer**, or **Vendor**. |
| Account code         | If you selected **Customer** or **Vendor** in the **Account type** field, you can further limit the use of the field value to a specific group or table. |
| Account/Group number | If you selected **Customer** or **Vendor** in the **Account type** field, and if you entered a group or table in the **Account code** field, you can enter a specific group or counteragent in this field. |
| Effective            | Specify the date when the value should start to be considered. |
| Expiration           | Specify the date when the value should stop being considered. |

By default, combinations of criteria that are defined by the **Account/Group number**, **Account code**, **Effective**, and **Expiration** fields don't influence the selection of values for additional fields. However, these combinations can be used in an executable class to implement specific logic that calculates values for additional fields.

## <a id="executable"></a>Executable class settings

An executable class is an X++ method or class that the electronic message processing can call in relation to an action if some evaluation is required for the process.

You can manually set up an executable class that must be called during processing by going to **Tax** \> **Setup** \> **Electronic messages** \> **Executable class settings**. On the **Executable class settings** page, create a line, and set the following fields.

| Field                 | Description |
|-----------------------|-------------|
| Executable class      | Enter the name that will be used during the setup of a message processing action that this class is called in relation to. |
| Description           | Enter a description of the executable class. |
| Executable class name | Select an X++ executable class. |
| Execution level       | This field is automatically set, because the value is predefined for the selected executable class. This field limits the level that the related evaluation is run on. |
| Class description     | This field is automatically set, because the value is predefined for the selected executable class. |
| Action type           | This field is available when the **\[EM\] Executable class action type** feature is turned on in the **Feature management** workspace. Use this field to specify the action type for the executable class. This field gives more precise control over the next actions that are available for the electronic message on the **Electronic messages** page. |

Some executable classes might have mandatory parameters that must be defined before the executable class is run for the first time. To define these parameters, on the Action Pane, select **Parameters**. In the dialog box that appears, set the fields, and then select **OK**. It's important that you select **OK**. Otherwise, the parameters won't be saved to the database, and the executable class won't be called correctly.

## <a id="populate"></a>Populate records actions

You use populate records actions to set up actions that add records to the Message items table, so that they can be added to an electronic message. For example, if your electronic message must report customer invoices, you must set up a populate records action that is linked to the **Data source** field in the Customer invoice journal table.

You can set up populate records actions by going to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**. Create a new record for every action that should add records to the table, and set the following fields.

| Field       | Description |
|-------------|-------------|
| Name        | Enter a name for the action that fills in records in your process. |
| Description | Enter a description of the populate records action. |

On the **Datasources setup** FastTab, add a line for every data source that is used for the process, and set the following fields.

| Field                  | Description |
|------------------------|-------------|
| Name                   | Enter a name for the data source. |
| Message item type      | Select the type of message item to use when records are created for the data source. |
| Account type           | Select the type of account to associate with records from the data source. |
| Master table name      | Select the table that will be a data source. |
| Document number field  | Select the field that the document number will be taken from in the selected master table. The value of this field is used as the value of the **Document number** field for the message item. |
| Document date field    | Select the field that the document date will be taken from in the selected master table. The value of this field is used as the value of the **Message item date** field for the message item. |
| Document account field | Select the field that the document account will be taken from in the selected master table. The value of this field is used as the value of the **Account number** field for the message item. |
| Company                | This field is available when the **Cross-company queries for the populate records actions** feature is turned on in the **Feature management** workspace. Use this feature to set up cross-company data sources for the populate records actions. Data can be fetched from multiple companies. |
| User query             | <p>If you set up a query by selecting **Edit query** above the grid, and you specify the criteria that must be applied to the selected master table that data is filled in from, this checkbox is automatically selected. Otherwise, all the records are filled in from the selected master table source.</p><p>When the **Cross-company queries for the populate records actions** feature is turned on in the **Feature management** workspace, and records must be collected from several companies, add a line for each additional legal entity that must be included in reporting. For each new line, select **Edit query**, and specify a related criterion that is specific to the legal entity that is specified in the **Company** field on the line. When you've finished, the **Datasources setup** grid will contain lines for all the legal entities that must be included in reporting.</p> |

## <a id="multiple-companies-populate"></a>Populate records from multiple companies

If your company must report from multiple legal entities in the same Finance database, set up the [populate records actions](#populate) for all the legal entities from which data must be included in reporting.

To enable this capability in your Finance environment, follow these steps. 

1. Go to **Workspaces** \> **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list.
3. Select **Enable now**. 

To set up the [populate records actions](#populate) for multiple companies from which data must be included in reporting, follow these steps.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.

    When the **Cross-company queries for the populate records actions** feature is enabled, the **Datasources setup** grid on the **Populate records action** page includes a **Company** field. For existing records that were created during the general setup of the [populate records actions](#populate), this field shows the identifier of the current legal entity.

2. In the **Datasources setup** grid, add a line for each subsidiary legal entity that must be included in reporting, and set the following fields.

    | Field name             | Value |
    |------------------------|-------|
    | Name                   | Enter a text value that will help you understand where this record comes from. For example, enter **Data source name - Subsidiary 1**. |
    | Message item type      | Select the message item type that is required for your EM processing. |
    | Account type           | Specify the account type that is required for your EM processing. If your EM processing has no specific account types, select **All**. |
    | Master table name      | Specify the name of the master table that is required for your EM processing. |
    | Document number field  | Specify the field that contains the document number in records of your EM processing. |
    | Document date field    | Specify the field that contains the document date in records of your EM processing. |
    | Document account field | Specify the field that contains the document account in records of your EM processing. |
    | Company                | Select the ID of the subsidiary legal entity. |
    | User query             | This checkbox is automatically selected when you define criteria by selecting **Edit query**. |

3. For each new line, select **Edit query**, and specify related criteria for the legal entity that is specified in the **Company** field on the line.

## <a id="applications"></a>Web applications

Use web application settings to set up a web application so that it supports Open Authorization (OAuth) 2.0. OAuth is the open standard that lets users grant "secure delegated access" to the application on their behalf, without sharing their access credentials. You can also go through the authorization process by getting an authorization code and access token. You can set up web application settings by going to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**.

The following table describes the fields on the **Web applications** page.

| Field                        | Description |
|------------------------------|-------------|
| Application name             | Enter a name for the web application. |
| Description                  | Enter a description of the web application. |
| Base URL                     | Enter the base internet address of the web application. |
| Authorization URL path       | Specify the path that is used to compose the URL for authorization. |
| Token URL path               | Specify the path that is used to compose the URL for the token. |
| Redirect URL                 | Enter the redirect URL. |
| Client ID                    | Enter the client ID of the web application. |
| Client secret                | Enter the client secret of the web application. |
| Server token                 | Enter the server token of the web application. |
| Authorization format mapping | Select the ER format that is used to generate the request for authorization. |
| Import token model mapping   | Select the ER importing model mapping that is used to store the access token. |
| Granted scope                | The scope that is granted for requests to the application. This field is automatically updated. |
| Access token will expire in  | The remaining time before the access token expires. This field is automatically updated. | 
| Accept                       | Specify the **Accept** property of the web request. For example, enter **application/vnd.hmrc.1.0+json**. |
| Content type                 | Specify the content type. For example, enter **application/json**. |

In addition, the following buttons are available on the Action Pane of the **Web applications** page to support the authorization process:

- **Get authorization code** – Initialize authorization of the web application. This function uses the ER format that is specified in the **Authorization format mapping** field to generate an authorization request.
- **Obtain access token** – Initialize the process of getting an access token.
- **Refresh access token** – Refresh an access token. This function uses the ER format that is specified in the **Import token model mapping** field to import information about the received access token.

When an access token to a web application is stored in the system's database in encrypted format, it can be used for requests to a web service. For security purposes, access to the token must be limited to the security roles that are allowed to address those requests. If anyone outside the security group tries to address a request, they receive an error that states that they aren't allowed to interoperate by using the selected web application. To set up the security roles that have access to the access token, use the **Security roles** FastTab on the **Web applications** page. If security roles aren't defined for a web application, only a system admin can interoperate by using the web application.

For each action with the selected web application, the **Action log** FastTab saves information about the user, and the date and time.

Some web services might require that different headers be included in the requests. The system admin can set up additional headers and their values on the **Supplementary headers** FastTab, and then use them during request generation.

## <a id="settings"></a>Web service settings

Use web service settings to set up direct data transmission to a web service. You can set up web service settings by going to **Tax** \> **Setup** \> **Electronic messages** \> **Web service settings**.

The following table describes the fields on the **Web service settings** page.

| Field                          | Description |
|--------------------------------|-------------|
| Web service                    | Enter a name for the web service. |
| Description                    | Enter a description of the web service. |
| Internet address               | <p>Enter the internet address of the web service. If a web application is specified for the web service, and if the internet address of the web service should be the same as the internet address that is defined for that web application, select **Copy base URL**. The base URL of the web application is then copied to this field.</p><p>**Warning:** Third-party services or other services that you configure here don't require certification and might not meet Microsoft privacy standards. You should review each service's privacy documentation and work with each service provider to learn more about the level of compliance that its service provides. You're responsible for ensuring that these services meet your security, privacy, and legal standards. You bear the risk of using the services. Microsoft gives no express warranties, guarantees, or conditions. We strongly recommend that you use only services that provide secure and authorized connections, such as HTTPS.</p> |
| Certificate                    | Select an Azure Key Vault certificate that has previously been set up. |
| Web application                | Select a web application that has previously been set up. |
| The response type – XML        | Set this option to **Yes** if the response type is XML. |
| Request method                 | Specify the method of the request. HTTP defines a set of request methods that indicate the action that should be performed for a given resource. The request method can be **GET**, **POST**, or another HTTP method. |
| Request headers                | Specify request headers. A request header is an HTTP header that can be used in an HTTP request. It isn't related to the content of the message. |
| Accept                         | Specify the accept property of the web request. |
| Accept encoding                | Specify the accept-encoding value. The Accept-Encoding request HTTP header advertises the content encoding that the client can understand. This content encoding is usually a compression algorithm. |
| Content type                   | Specify the content type. The Content-Type entity HTTP header indicates the media type of the resource. |
| Successful response code       | Specify the HTTP status code that indicates that the request was successful. |
| Request headers format mapping | Select the ER format that is used to generate web request headers. |

## <a id="actions"></a>Message processing actions

You use message processing actions to create actions for your processes and set up their parameters. You can set up message processing actions by going to **Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions**.

The following tables describe the fields on the **Message processing actions** page.

### General FastTab

| Field                                     | Description |
|-------------------------------------------|-------------|
| Action type                               | Select the type of action. For information about the available options, see the [Message processing action types](#action-types) section later in this article. |
| Format mapping                            | Select the ER format that should be called for the action. This field is available only for actions of the **Electronic reporting export**, **Electronic reporting import**, and **Electronic reporting export message** types. |
| Format mapping for URL path               | Select the ER format that should be called for the action. This format is used to compose the path of the URL address that will be added to the base internet address that is specified for the selected web server. This field is available only for actions of the **Web service** type. |
| Message item type                         | Select the type of records that the action should be evaluated for. This field is available for actions of the **Message item execution level**, **Electronic reporting export**, **Electronic reporting import**, and **Web service** types, and other types. If you leave this field blank, all the message item types that are defined for the message processing are evaluated. |
| Executable class                          | Select an existing executable class setting. This field is available only for actions of the **Message item execution level** and **Message item execution level** types. |
| Populate records action                   | Select an existing populate records action. This field is available only for actions of the **Populate records** type. |
| Web service                               | Select an existing web service. This field is available only for actions of the **Web service** type. |
| File name to send                         | Enter the name of the attachment to an electronic message that must be sent by this action. If multiple attachments have the same original file name, the newest one will be sent. If no attachment is found that has the specified original file name, the request will be sent without content. This field is available only for actions of the **Web service** type. |
| File name                                 | Specify the name of the file that will be the result of the action. This file can be the response from the web server or the report that is generated. This field is available only for actions of the **Web service** and **Electronic reporting export message** types. |
| Attach files to source documents          | Select this checkbox to attach generated files to records in a referenced master table for EM items. This field is available only for actions of the **Electronic reporting export** and **Web service** types. |
| Attach files from output archive to items | Select this checkbox to extract separate XML files from the output archive file and attach them to the corresponding electronic message items. This field is available only for actions of the **Electronic reporting export** type. |
| Number of message items per export        | Specify the limit on the number of message items that must be included in one file (message). This field is available only for actions of the **Electronic reporting export** type. |
| Use ER source                             | Select this checkbox to use ER source parameters for import. Otherwise, the attachment from the electronic message is used. This field is available only for actions of the **Electronic reporting import** type. |
| Show dialog                               | Set this option to **Yes** if a dialog box must be shown to users before the report is generated. This field is available only for actions of the **Electronic reporting export message** type. |

#### <a id="action-types"></a>Message processing action types

The following options are available in the **Action type** field:

- **Create message** – Use this action type to let users manually create messages on the **Electronic message** page. An initial status can't be set up for an action of this type.
- **Populate records** – This action type must already be set up. Associate it with a populate records action to enable the action to be included in processing. It's assumed that this action type is used for the first action in message processing (when no electronic message was created in advance) or for an action that adds message items to a message that was previously created by the **Create message** action type. Therefore, for actions of this type, a result status can be set up only for message items. An initial status can be set up only for messages.
- **Message execution level** – Use this action type to set up an executable class that should be evaluated at the message level.
- **Message item execution level** – Use this action type to set up an executable class that should be evaluated at the message item level.
- **Electronic reporting export** – Use this action type for actions that should generate a report based on an exporting ER configuration at the message item level.
- **Electronic reporting export message** – Use this action type for actions that should generate a report based on an exporting ER configuration at the message level (for example, when a message doesn't have any message items).
- **Electronic reporting import** – Use this action type for actions that should generate a report based on an importing ER configuration.
- **Message level user processing** – Use this action type for actions that assume some manual action by the user at the message level. For example, the user might update the status of messages.
- **User processing** – Use this action type for actions that assume some manual action by the user at the message item level. For example, the user might update the status of messages items.
- **Web service** – Use this action type for actions that should transmit a generated report to a web service. This action type isn't used for Italian Purchase and Sales Invoices Communication reporting. For this action type, the **Message processing actions** page includes a **Miscellaneous details** FastTab where you can specify a confirmation text. This confirmation text is shown to users before requests are addressed to the selected web service.
- **Request verification** – Use this action type to request verification from a server.

### Initial statuses FastTab

> [!NOTE]
> The **Initial statuses** FastTab isn't available for actions that have an initial action type of **Create message**.

| Field               | Description |
|---------------------|-------------|
| Message item status | Select the message item status that the selected message processing action should be evaluated for. |
| Description         | A description of the selected message item status. |

### Result statuses FastTab

| Field               | Description |
|---------------------|-------------|
| Message status      | Select the message statuses that the selected message processing action should be evaluated for. This field is available only for message processing actions that are evaluated at the message level. For example, it's available for actions of the **Electronic reporting export** and **Electronic reporting import** types, but it isn't available for actions of the **User processing** and **Message item execution level** types. |
| Description         | A description of the selected message status. |
| Response type       | The response type of the selected message status. |
| Message item status | Select the resulting statuses that should be available after the selected message processing action is evaluated. This field is available only for message processing actions that are evaluated at the message item level. For example, it's available for actions of the **User processing** and **Message item execution level** types. For message processing actions that are evaluated at the message level, this field shows the message item status that was set up for the selected message status. |

The following table shows the result statuses that must be set up for different action types and response types.

| Electronic message action type/Response type | Successfully executed | Business error | Technical error | User defined | Cancel |
|----------------------------------------------|-----------------------|----------------|-----------------|--------------|--------|
| Create message                               | X                     |                |                 |              |        |
| Electronic reporting export                  | X                     |                |                 |              |        |
| Electronic reporting import                  |                       |                |                 |              |        |
| Web service                                  | X                     |                | X               |              |        |
| User processing                              |                       |                |                 |              |        |
| Message execution level                      |                       |                |                 |              |        |
| Populate records                             |                       |                |                 |              |        |
| Message item execution level                 |                       |                |                 |              |        |
| Request verification                         | X                     | X              | X               |              |        |
| Electronic reporting export message          | X                     |                |                 |              |        |
| Message level user processing                |                       |                |                 |              |        |

## <a id="processing"></a>Electronic message processing

Electronic message processing is a basic concept of the EM functionality. It aggregates actions that should be evaluated for the electronic message. The actions can be linked by using an initial status and a result status. Alternatively, actions of the **User processing** type can be started independently. To set up processing of electronic messages, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.

The **Action** FastTab lets you add predefined actions to the processing. You can specify whether an action must be run separately, or whether it can be started by the processing. To specify that an action in the processing can be initialized only by a user, set the **Run separately** field to **Yes** for that action. If an action should be started by the processing for messages or message items that are in the status that is defined as the initial status for the action, set the **Run separately** field to **No**. Actions of the **User action** type must always be run separately.

Sometimes, several actions must be aggregated into a sequence, even though the first action is set up to run separately. For example, a user must initialize report generation. However, immediately after the report is generated, it must be sent to a web service, and the response from the web service must be reflected in the system. In this case, you can create an inseparable sequence for the actions that must always run together. On the **Action** FastTab, select **Inseparable sequences** above the grid, and create a sequence. Then, for all the actions that must run together in one sequence, select the sequence in the **Inseparable sequence** field. For this example, the **Run separately** field can be set to **Yes** for the first action in the sequence and **No** for all the other actions.

Actions of the **Electronic reporting export** and **Electronic reporting export message** types run an ER format that has input parameters. If your electronic message processing includes actions of either of those types, you must specify the values for the input parameters before report generation. In this way, the system can use a batch regime to generate the report. You can select **Parameters** above the grid to set up the parameters for the selected action type (**Electronic reporting export** or **Electronic reporting export message**). Select the **Use parameters** checkbox for the action that must be run with the specified parameters in a batch regime.

Use the **Message item additional fields** FastTab to add predefined additional fields that are related to message items. You must add additional fields for each type of message item that the fields are related to. You can specify a default value that will be assigned to the additional field during processing.

Use the **Message additional fields** FastTab to add predefined additional fields that are related to messages. You can specify a default value that will be assigned to the additional field during processing.

Use the **Security roles** FastTab to set up the security roles that are predefined in the system for specific processing. Users who have a specific role will see only the processing that is defined for that role.

Use the **Batch** FastTab to set up the processing to work in a batch regime. We recommend that you set up a batch regime for your processing directly on the **Electronic messages** or **Electronic message items** page, when you select **Run processing** on the Action pane to initiate processing.
