---
# required metadata

title: Electronic messaging
description: This topic provides overview and setup information for electronic messaging in Microsoft Dynamics 365 Finance.
author: ShylaThompson
manager: AnnBe
ms.date: 11/16/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Electronic messaging

[!include [banner](../includes/banner.md)]

This topic provides overview and setup information for electronic messaging.

Recently, the governments and legislative authorities of various countries and regions around the world have implemented reporting requirements for companies that are registered in those countries or regions. The purpose of the requirements is to enable data to be obtained from those companies in electronic format, directly from the systems where it was accounted, stored, and processed.

The Electronic messages functionality in Finance supports various processes for electronic interoperation between Finance and the systems that governments and legislative authorities offer for reporting, submitting, and receiving official information.

The Electronic messages functionality is integrated with the **Electronic Reporting** (ER) module. Therefore, you can set up ER formats for electronic messages. For more information, see [Electronic reporting (ER)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/general-electronic-reporting).

Electronic messaging is based on the following entities:

- **Electronic message** – A report or declaration that should be reported and/or transmitted internally. An example is a report that is sent to a tax office.
- **Electronic message items** – Records that should be included in the message that is reported.
- **Electronic message processing** – A chain of actions that should be run to collect the required data, generate reports, store data in Microsoft Azure Blob storage, transmit reports outside the system, receive responses from outside the system, and, based on the information that is received, update the database. The actions in the chain can be either linked or unlinked

The following illustration shows the flow of data for electronic messaging.

![Electronic messaging data flow](media/electronic-messaging-data-flow.png)

The Electronic messages functionality supports the following scenarios:

- Manually create messages, and generate reports that are based on associated exporting ER formats of various types: Microsoft Excel, XML, JavaScript Object Notation (JSON), PDF, text, and Microsoft Word.
- Automatically create and process messages that are based on information that was requested and received from an authority via an associated importing ER format.
- Collect and process information from a data source as message items. The data source is a Finance table.
- Store additional information, and evaluate various values by calling specifically defined executable classes in relation to messages or message items.
- Aggregate information that is collected in message items, split that information by message, and generate reports that are in associated exporting ER formats.
- Transmit the reports that are generated to a web service by using security information that is stored in Azure Key Vault.
- Receive a response from a web service, interpret the response, and update data in Finance as appropriate.
- Store and review all the reports that are generated.
- Store and review all the log information that is related to actions that are run for a message or message item.
- Control the processing through various message statuses and message item statuses.

## Set up electronic messaging

Electronic messaging can help you maintain different electronic reporting processes for different document types. In some complex scenarios, electronic messaging is set up so that it has a combination of many message statuses, message items statuses, actions, additional fields, and executable classes. For these scenarios, packages of data entities are available for import. If you use these data entity packages, you should import them to a legal entity by using the Data management tool. For more information about how to use the Data management tool, see [Data management](../../dev-itpro/data-entities/data-entities-data-packages.md).

If you don't import a data entity package, you can manually set up the Electronic messages functionality. In this case, you must set up the following elements:

- [Number sequences](#number-sequences)
- [Message item types and statuses](#message-item-types-and-statuses)
- [Message statuses](#message-statuses)
- [Additional fields](#additional-fields)
- [Executable class settings](#executable-class-settings)
- [Populate records actions](#populate-records-actions)
- [Web applications](#web-applications)
- [Web service settings](#web-service-settings)
- [Message processing actions](#message-processing-actions)
- [Electronic message processing](#electronic-message-processing)

The following sections provide more information about each of these elements.

### Number sequences

Set up number sequences for both messages and message items. The number sequences are used to automatically number the messages and the message items. The numbers that are assigned will be used as unique identifiers for the messages and message items in the system. You can set up number sequences for electronic messaging on the **General ledger parameters** page (**General ledger** \> **Ledger setup** \> **General ledger parameters**).

### Message item types and statuses

Message item types identify the types of records that will be used in electronic messages. You can set up message item types on the **Message item types** page (**Tax** \> **Setup** \> **Electronic messages** \> **Message item types**).

Message item statuses identify the statuses that will apply to message items in the processing that you're setting up. You can set up message item types on the **Message item statuses** page (**Tax** \> **Setup** \> **Electronic messages** \> **Message item statuses**).

The **Allow delete** parameter of a message item status defines whether users can delete message items that have this status on the **Electronic messages** page or the **Electronic message items** page.

### Message statuses

Set up the message statuses that should be available in message processing. You can set up message statuses on the **Message statuses** page (**Tax** \> **Setup** \> **Electronic messages** \> **Message statuses**).

The following table describes the fields on the **Message statuses** page.

| Field name          | Description |
|---------------------|-------------|
| Message status      | Enter a unique name for the message status. Message statuses are used to characterize the state of an electronic message at every moment. The name that you enter is shown on the **Electronic messages** page and in a log that is related to electronic messages. |
| Description         | Enter a description of the message status. |
| Response type       | Select the type of response for the message status. Some actions in a processing can produce more than one response type. For example, actions of the **Web service** type can produce responses of either the **Successfully executed** type or the **Technical error** type, depending on the result of its execution. In this case, you must define message statuses for both response types. For more information about action types and the types of responses that are related to them, see [Message processing action types](#message-processing-action-types). |
| Message item status | Sometimes, the status of an electronic message must influence the status of related message items. Select a message item status in this field to associate it with the message status. |
| Allow delete        | Select this check box if users should be able to delete electronic messages that have this status on the **Electronic messages** page. |

### Additional fields

The Electronic messages functionality lets you fill in records from a transactional table. In this way, you can prepare the records for reporting and then report them. However, transactional tables sometimes don't have enough information to fill in records in a manner that meets the reporting requirements. To fill in all the information that must be reported for a record, you can set up additional fields. Additional fields can be associated with both messages and message items. You can set up additional fields on the **Additional fields** page (**Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**).

The following table describes the general fields on the **Additional fields** page.

| Field       | Description |
|-------------|-------------|
| Field name  | Enter the name of an additional attribute of message items that are related to the process. This name is shown in the user interface (UI) while you work with the process. It can also be used in ER configurations that are related to the process. |
| Description | Enter a description of the additional field. |
| User edit   | Set this option to **Yes** if users should be able to change the value of the additional field from the UI. |
| Counter     | Set this option to **Yes** if the additional field should contain a number sequence in an electronic message. Value of the additional field will be filled in automatically when an action of the **Electronic reporting export** is run. |
| Hidden      | Set this option to **Yes** if the additional field should be hidden in the UI. |

Each additional field can have different values for the processing. You define these values on **Values** FastTab. The following table describes the fields.

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

### Executable class settings

An executable class is an X++ method or class that the electronic message processing can call in relation to an action if some evaluation is required for the process.

You can manually set up an executable class on the **Executable class settings** page (**Tax** \> **Setup** \> **Electronic messages** \> **Executable class settings**). Create a line, and set the following fields.

| Field                 | Description |
|-----------------------|-------------|
| Executable class      | Enter the name that will be used during the setup of a message processing action that this class is called in relation to. |
| Description           | Enter a description of the executable class. |
| Executable class name | Select an X++ executable class. |
| Execution level       | This field is set automatically, because the value should be predefined for the selected executable class. This field limits the level that related evaluation is run on. |
| Class description     | This field is set automatically, because the value should be predefined for the selected executable class. |

Some executable classes might have mandatory parameters that must be defined before the executable class is run for the first time. To define these parameters, select **Parameters** on the Action Pane, set the fields in the dialog box that appears, and then select **OK**. It's important that you select **OK**. Otherwise, the parameters won't be saved to the database, and the executable class won't be called correctly.

### Populate records actions

You use populate records actions to set up actions that add records to the Message items table so that they can be added to an electronic message. For example, if your electronic message must report customer invoices, you must set up a populate records action that is linked to the **Data source** field in the Customer invoice journal table. You can set up populate records actions on the **Populate records action** page (**Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**). Create a new record for every action that should add records to the table, and set the following fields.

| Field       | Description |
|-------------|-------------|
| Name        | Enter a name for the action that fills in records in your process. |
| Description | Enter a description of the populate records action. |

On the **Datasources setup** FastTab, add a line for every data source that is used for the process, and set the following fields.

| Field                  | Description |
|------------------------|-------------|
| Name                   | Enter a name for the data source. |
| Message item type      | Select the type of message item that should be used when records are created for the data source. |
| Account type           | Select the type of account that should be associated with records from the data source. |
| Master table name      | Select the table that should be a data source. |
| Document number field  | Select the field that the document number should be taken from in the selected table. |
| Document date field    | Select the field that the document date should be taken from in the selected table. |
| Document account field | Select the field that the document account should be taken from in the selected table. |
| User query             | If this check box is selected, you can set up a query by selecting **Edit query** above the grid. Otherwise, all the records will be filled in from the selected data source. |

### Web applications

You use web application settings to set up a web application so that it supports Open Authorization (OAuth) 2.0. OAuth is the open standard that lets users grant "secure delegated access" to the application on their behalf, without sharing their access credentials. You can also go through the authorization process by getting an authorization code and access token. You can set up web application settings on the **Web applications** page (**Tax** \> **Setup** \> **Electronic messages** \> **Web applications**).

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
| Access token will expire in  | The remaining time before the access token expires. | 
| Accept                       | Specify the **Accept** property of the web request. For example, enter **application/vnd.hmrc.1.0+json**. |
| Content type                 | Specify the content type. For example, enter **application/json**. |

In addition, the following buttons are available on the Action Pane of the **Web applications** page to support the authorization process:

- **Get authorization code** – Initialize authorization of the web application.
- **Obtain access token** – Initialize the process of getting an access token.
- **Refresh access token** – Refresh an access token.

When an access token to a web application is stored in the system's database in encrypted format, it can be used for requests to a web service. For security purposes, access to the access token must be limited to security roles that must be allowed to address those requests. If users outside the security group try to address a request, they receive an error that states that they aren't allowed to interoperate via the selected web application. To set up the security roles that must have access to the access token, use the **Security roles** FastTab on the **Web applications** page. If security roles aren't defined for a web application, only a system admin can interoperate via this web application.

### Web service settings

You use web service settings to set up direct data transmission to a web service. You can set up web service settings on the **Web service settings** page (**Tax** \> **Setup** \> **Electronic messages** \> **Web service settings**).

The following table describes the fields on the **Web service settings** page.

| Field                          | Description |
|--------------------------------|-------------|
| Web service                    | Enter a name for the web service. |
| Description                    | Enter a description of the web service. |
| Internet address               | Enter the internet address of the web service. If a web application is specified for the web service, and if the internet address of the web service should be the same as the internet address that is defined for that web application, select **Copy base URL** to copy the base URL of the web application to this field. |
| Certificate                    | Select a Key Vault certificate that has previously been set up. |
| Web application                | Select a Key Vault certificate that has previously been set up. |
| The response type – XML        | Set this option to **Yes** if the response type is XML. |
| Request method                 | Specify the method of the request. HTTP defines a set of request methods that indicate the action that should be performed for a given resource. The request method can be **GET**, **POST**, or another HTTP method. |
| Request headers                | Specify request headers. A request header is an HTTP header that can be used in an HTTP request, and that isn't related to the content of the message. |
| Accept                         | Specify the **Accept** property of the web request. |
| Accept encoding                | Specify the **Accept-Encoding** value. The Accept-Encoding request HTTP header advertises the content encoding that the client can understand. This content encoding is usually a compression algorithm. |
| Content type                   | Specify the content type. The Content-Type entity HTTP header indicates the media type of the resource. |
| Successful response code       | Specify the HTTP status code that indicates that the request was successful. |
| Request headers format mapping | Select the ER format that is used to generate web request headers. |

### Message processing actions

You use message processing actions to create actions for your processes and set up their parameters. You can set up message processing actions on the **Message processing actions** page (**Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions**).

The following tables describe the fields on the **Message processing actions** page.

#### General FastTab

| Field                       | Description |
|-----------------------------|-------------|
| Action type                 | Select the type of action. For information about the available options, see the [Message processing action types](#message-processing-action-types) section. |
| Format mapping              | Select the ER format that should be called for the action. This field is available only for actions of the **Electronic reporting export**, **Electronic reporting import**, and **Electronic reporting export message** types. |
| Format mapping for URL path | Select the ER format that should be called for the action. This field is available only for actions of the **Web service** type. It's used to compose the path of the URL address that will be added to the base internet address that is specified for the selected web server. |
| Message item type           | Select the type of records that the action should be evaluated for. This field is available for actions of the **Message item execution level**, **Electronic reporting export**, **Electronic reporting import**, and **Web service** types, and also some other types. If you leave this field blank, all the message item types that are defined for the message processing are evaluated. |
| Executable class            | Select executable class settings that were previously created. This field is available only for actions of the **Message item execution level** and **Message item execution level** types. |
| Populate records action     | Select a populate records action that was previously set up. This field is available only for actions of the **Populate records** type. |
| Web service                 | Select a web service that was previously set up. This field is available only for actions of the **Web service** type. |
| File name                   | Specify the name of the file that will be the result of the action. This file can be the response from the web server or the report that is generated. This field is available only for actions of the **Web service** and **Electronic reporting export message** types. |
| Show dialog                 | Set this option to **Yes** if a dialog box must be shown to users before report generation. This field is available only for actions of the **Electronic reporting export message** type. |

##### Message processing action types

The following options are available in the **Action type** field:

- **Create message** – Use this action type to let users manually create messages on the **Electronic message** page. An initial status can't be set up for an action of this type.
- **Populate records** – An action of the **Populate records** type must previously be set up. Associate this action type with a populate records action to enable that action to be included in processing. It's assumed that this action type is used either for the first action in message processing (when no electronic message was created in advance) or for an action that adds message items to a message that was previously created by an action of **Create message** type. Therefore, for actions of this type, a result status can be set up only for message items. An initial status can be set up only for messages.
- **Message execution level** – Use this action type to set up an executable class that should be evaluated at the message level.
- **Message item execution level** – Use this action type to set up an executable class that should be evaluated at the message item level.
- **Electronic reporting export** – Use this action type for actions that should generate a report that is based on an exporting ER configuration at the message item level.
- **Electronic reporting export message** – Use this action type for actions that should generate a report that is based on an exporting ER configuration at the message level (for example, when a message doesn't have any message items).
- **Electronic reporting import** – Use this action type for actions that should generate a report that is based on an importing ER configuration.
- **Message level user processing** – Use this action type for actions that assume some manual action by the user at the message level. For example, the user might update the status of messages.
- **User processing** – Use this action type for actions that assume some manual action by the user at the message item level. For example, the user might update the status of messages items.
- **Web service** – Use this action type for actions that should transmit a generated report to a web service. This action type isn't used for Italian Purchase and Sales Invoices Communication reporting. For actions of **Web service** type, the **Message processing actions** page includes a **Miscellaneous details** FastTab, where you can specify a confirmation text. This confirmation text will be shown to users before requests to the selected web service are addressed.
- **Request verification** – Use this action type to request verification from a server.

#### Initial statuses FastTab

> [!NOTE]
> The **Initial statuses** FastTab isn't available for actions that have an initial action type of **Create message**.

| Field               | Description |
|---------------------|-------------|
| Message item status | Select the message item status that the selected message processing action should be evaluated for. |
| Description         | A description of the selected message item status. |

#### Result statuses FastTab

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

### Electronic message processing

Electronic message processing is a basic concept of the Electronic messages functionality. It aggregates actions that should be evaluated for the electronic message. The actions can be linked via an initial status and a result status. Alternatively, actions of the **User processing** type can be started independently. On the **Electronic message processing** page (**Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**), you can also select additional fields that should be supported for the processing on either the message level or the message items level.

The **Action** FastTab lets you add predefined actions to the processing. You can specify whether an action must be run separately, or whether it can be started by the processing. To specify that an action in the processing can be initialized only by a user, set the **Run separately** field to **Yes** for that action. If an action should be started by the processing for messages or message items that are in the status that is defined as the initial status for the action, set the **Run separately** field to **No**. Actions of the **User action** type must always be run separately.

Sometimes, several actions must be aggregated into a sequence, even though the first action is set up so that it runs separately. For example, a user must initialize report generation, but immediately after the report is generated, it must be sent to a web service, and the response from the web service must be reflected in the system. In this situation, you can create an inseparable sequence for the actions that must always run together. On the **Action** FastTab, select **Inseparable sequences** above the grid, and create a sequence. Then, for all the actions that must run together, select the sequence in the **Inseparable sequence** field. In this case, the **Run separately** field can be set to **Yes** for the first action in the sequence but **No** for all the other action.

The **Message item additional fields** FastTab lets you add predefined additional fields that are related to message items. You must add additional fields for each type of message item that the fields are related to.

The **Message additional fields** FastTab lets you add predefined additional fields that are related to messages.

The **Security roles** FastTab lets you set up the security roles that are predefined in the system for specific processing. Users who have a specific role will see only processing that is defined for that role.

The **Batch** FastTab lets you set up processing to work in a batch regime.

## Work with the Electronic messages functionality

If you're working at the message level, the **Electronic messages** page (**Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**) is more useful. If you're operating at the data collection (message item) level, the **Electronic message items** page (**Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic message items**) is more useful.

### Electronic messages

The **Electronic messages** page presents the processing that is available to you, based on your role. Security roles are associated with processing in the setup of that processing. For each processing that is available to you, the page shows electronic messages and information that is related to them.

The **Messages** FastTab shows electronic messages for the selected processing. Depending on the status of the selected message and predefined processing, you can run some actions by using the buttons above the grid:

- **New** – This button is associated with actions of the **Create message** type.
- **Delete** – This button is available if the **Allow delete** check box is selected for the current status of the selected message.
- **Collect data** – This button is associated with actions of the **Populate records** type.
- **Generate report** – This button is associated with actions of the **Electronic reporting export message** type.
- **Send report** – This button is associated with actions of the **Web service** type.
- **Import response** – This button is associated with actions of the **Electronic reporting import** type.
- **Update status** – This button is associated with actions of the **Message level user processing** type.
- **Message items** – Open the **Electronic message items** page.

The **Action log** FastTab shows information about all the actions that have been run for the selected message. If an action caused an error, information about the error is attached to the related line in the grid. To review the information about the error, select the line in the grid, and then select the **Attachment** button (the paper clip symbol) in the upper-right corner on the page.

The **Message additional fields** FastTab shows all the additional fields that are defined for messages in the processing setup. It also shows the values of those additional fields.

The **Message items** FastTab shows all the message items that are related to the selected message. Depending on the status of the selected message item, you can run some actions by using the buttons above the grid:

- **Delete** – This button is available if the **Allow delete** check box is selected for the current status of the selected message item.
- **Update status** – This button is associated with actions of the **User processing** type.
- **Original document** – Open a page that shows the original document for the selected message item.

All reports that have already been generated and received for a message are attached to that message. To review the attachments that are related to a message, select the message, and then select the **Attachment** button (the paper clip symbol) in the upper-right corner of the page.

![Attachment button](media/attachment-icon.png)

The **Attachments** page shows all the attachments that are related to the selected message. To view a file, select it in the list on the left, and then select **Open** on the Action Pane.

![Open button](media/open-button.png)

You can also review attachments that are related to a specific action that was previously run for a message. On the **Electronic messages** page, select the message on the **Messages** FastTab, select the action on **Action log** FastTab, and then select the **Attachment** button in the upper-right corner of the page.

You can also run either the whole processing or just a specific action by selecting **Run processing** on the Action Pane.

### Electronic message items

The **Electronic message items** page presents all message items and a log of the actions that have been run for each message item. It also shows the additional fields that are defined for the message items, and the values of those additional fields.

The following table describes the fields on the **Message items** tab.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Processing</td>
<td>The name of the processing that was used to create the message item.</td>
</tr>
<tr>
<td>Message item</td>
<td>The ID of the message item. This ID is assigned automatically, based on the <strong>Message item</strong> number sequence that is defined on the <strong>General ledger parameters</strong> page.</td>
</tr>
<tr>
<td>Message item date</td>
<td>The date when the message item was created.</td>
</tr>
<tr>
<td>Message item type</td>
<td>The type of message item. Several types of messages items can be set up for the same processing (for example, <strong>Incoming invoices</strong> and <strong>Outgoing invoices</strong>). This field can be filled in automatically only when an invoice is added to the Message items table.</td>
</tr>
<tr>
<td>Message item status</td>
<td>The actual status of the message item. The available statuses vary, depending on the type of message item. Here are some examples:
<ul>
<li><strong>Populated</strong> – A record was added to the Message items table.</li>
<li><strong>Evaluated</strong> – Additional attributes were calculated for the message item.</li>
<li><strong>Reported</strong> – The message item was successfully added to a report.</li>
<li><strong>Excluded</strong> – This status can be useful if you must exclude some message items from a report before it's exported.</li>
</ul>
</td>
</tr>
<tr>
<td>Transmission date</td>
<td>For processing that automatically transmits a generated report outside the system, the date when the message item was transmitted.</td>
</tr>
<tr>
<td>Document number</td>
<td>This field is filled in automatically, based on the setup of the populate records action. This field can be filled in automatically only when an invoice is added to the Message items table.</td>
</tr>
<tr>
<td>Account number</td>
<td>The account number of a customer or vendor (or another field value, depending on the field that is defined on the populate records action). This field can be filled in automatically only when an invoice is added to the Message items table.</td>
</tr>
<tr>
<td>Message</td>
<td>The number of the message. This number is assigned automatically, based on the <strong>Message</strong> number sequence that is defined on the <strong>General ledger parameters</strong> page.</td>
</tr>
<tr>
<td>Message status</td>
<td>The actual status of the electronic message.</td>
</tr>
<tr>
<td>Next action</td>
<td>The next actions that can be started for the current status of the message item.</td>
</tr>
</tbody>
</table>

The **Additional fields** tab shows the additional fields for the selected message item, and their values.

#### Run processing

Select **Run processing** on the Action Pane to run the processing for message items. To run a specific action, in the **Run processing** dialog box, set the **Choose action** option to **Yes**, and then select an action. To run the whole processing, leave the **Choose action** option set to **No**.

#### Generate report

Select **Generate report** on the Action Pane to generate a report. This button is associated with actions of the **Electronic reporting export** type.

#### Update status

Select **Update status** on the Action Pane to update the status of one or more message items. In the **Update status** dialog box, use the **Records to include** FastTab to select the message items to update. Make sure that you correctly define the selection criteria, because message item statuses will be updated according to these criteria, the initial status of the selected action, and the **New status** value that you specify. After a status update is completed, it will be difficult to determine which items were updated. Therefore, it will be difficult to roll back the status update.

#### Electronic messages

Select **Electronic messages** on the Action Pane to review an electronic message that is related to the selected message item.

You can also review all the files that are related to a specific message item. Select the **Message** field for the message item, or select **Electronic messages** on the Action Pane. Then, on the **Electronic message** page, select the message to review files for, and then select the **Attachment** button (the paper clip symbol) in the upper-right corner of the page.

![Attachment button](media/attachment-icon.png)

The **Attachments** page shows all the attachments that are related to the message. To view a file, select it in the list on the left, and then select **Open** on the Action Pane.

![Open button](media/open-button.png)

#### Original document

Select **Original document** on the Action Pane to open the original document for the selected message item.

## Example: Set up and run processing to call a simple ER exporting format to generate an Excel report

After you've created your ER format, mapped it to data sources, and completed it, you can run it by using the **Electronic reporting** workspace. A report is generated, and you can save it locally.

To control the following aspects of the reporting process, you must set up electronic messaging processing:

- Log information about who generated the report.
- Log information about when the report was generated.
- Save the reports that were generated for previous periods.

This section provides an example that shows how you can set up electronic messaging to generate a report that is based on an exporting ER format for Excel. If you want to follow this example, the ER Excel exporting format must already be created, mapped to data sources, and completed. Additionally, a number sequence must already be set up for electronic messages.

When you build processing, it's helpful if you first define the processing actions and statuses that will be set up. The following illustration shows what the processing looks like for this example.

![Processing scheme](media/processing-scheme.png)

#### Create message statuses

1. Go to **Tax \> Setup \> Electronic messages \> Message statuses**.
2. Create the following message statuses:

    - New
    - Prepared
    - Generated

    ![Message statuses](media/message-statuses.png)

3. On the line for the **New** status, select the **Allow delete** check box to let users delete messages that have this status.

#### Create additional fields

1. Go to **Tax \> Setup \> Electronic messages \> Additional fields**.
2. Add an additional field and its values. Here is an example.

    ![Additional fields](media/additional-fields.png)

3. Set the **User edit** option to **Yes** to let users edit the field.

#### Create message processing actions

For this example, you will create the following actions:

- **Create message**
- **Update to Prepared**
- **Generate report**
- **Update to initial status** (optional)

1. Go to **Tax \> Setup \> Electronic messages \> Message processing actions**.
2. Create an action that is named **Create message**. On the **General** FastTab, in the **Action type** field, select **Create message**.
3. Create an action that is named **Update to Prepared**, and set the following fields:

    - On the **General** FastTab, in the **Action type** field, select **Message level user processing**.
    - On the **Initial statuses** FastTab, in the **Message status** field, select **New**.
    - On the **Result statuses** FastTab, in the **Message status** field, select **Prepared**. In the **Response type** field, enter **Successfully executed**.

4. Create an action that is named **Generate report**, and set the following fields:

    - On the **General** FastTab, in the **Action type** field, select **Electronic reporting export**. In the **Format mapping** field, select the exporting ER format. The options are **Excel**, **XML**, **JSON**, **Text**, and **Other**.
    - On the **Initial statuses** FastTab, in the **Message status** field, select **Prepared**.
    - On the **Result statuses** FastTab, in the **Message status** field, select **Generated**. In the **Response type** field, enter **Successfully executed**.

    ![Generate report action](media/generate-report-action.png)

5. Optional: To let users regenerate a report several times, you can create an **Update to initial status** action and set the following fields:

    - On the **General** FastTab, in the **Action type** field, select **Message level user processing**.
    - On the **Initial statuses** FastTab, in the **Message status** field, select **Generated**.
    - On the **Result statuses** FastTab, add a separate line for each of the two message statuses (**Prepared** and **New**). For both lines, set the **Response type** field to **Successfully executed**.

#### Electronic message processing

In this example, all the actions should be set up so that they run separately. The assumption is that the user will initialize every action.

1. Go to **Tax \> Setup \> Electronic messages \> Electronic message processing**.
2. Add a record for your processing, and add all previously defined actions and an additional field.
3. Optional: On the **Security roles** FastTab, define security roles for your processing to limit access to specific reporting.
4. Go to **Tax \> Inquires and reports \> Electronic messages \> Electronic messages**.
5. Select **New** to create a message. At this point, you can add dates and a description. You can also update the value of the additional field as you require.

    ![Create an electronic message](media/create-electronic-message.png)

The grid on the **Action log** FastTab is automatically filled in with a log of all actions that are performed on the message.

You can now either delete or update the message status. To update the message status, select **Update status**. In the **New status** field, select **Prepared**, and then select **OK**.

![Update the message status](media/update-status.png)

The message status is updated to **Prepared**, and you can now generate the report by selecting **Generate report**. The report is generated, and the message status and action log are updated. To view the generated report, select the **Attachment** button (the paper clip symbol) in the upper-right corner of the page.
