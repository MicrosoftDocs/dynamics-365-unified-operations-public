---
# required metadata

title: Electronic messaging
description: This topic provides overview and setup information for electronic messaging in Microsoft Dynamics 365 Finance.
author: ShylaThompson
ms.date: 11/16/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Electronic messaging

[!include [banner](../includes/banner.md)]

This topic provides overview information for **Electronic messages** (EM) functionality.

Recently, the governments and legislative authorities of various countries and regions around the world have implemented reporting requirements for companies that are registered in those countries or regions. The purpose of the requirements is to enable data to be obtained from those companies in electronic format, directly from the systems where it was accounted, stored, and processed.

The EM functionality in Finance supports various processes for electronic interoperation between Finance and the systems that governments and legislative authorities offer for reporting, submitting, and receiving official information.

The EM functionality is integrated with the **Electronic Reporting** (ER) module. Therefore, you can set up ER formats for electronic messages. For more information, see [Electronic reporting (ER)](/dynamics365/unified-operations/dev-itpro/analytics/general-electronic-reporting).

## Basic concept for EM functionality

EM functionality is based on the following entities:

- **Electronic message** – A report or declaration that should be reported and/or transmitted internally. An example is a report that is sent to a tax office.
- **Electronic message items** – Records that should be included in the message that is reported.
- **Electronic message processing** – A chain of actions that should be run to collect the required data, generate reports, store data in Microsoft Azure Blob storage, transmit reports outside the system, receive responses from outside the system, and, based on the information that is received, update the database. The actions in the chain can be either linked or unlinked

The following illustration shows the flow of data for EM.

![Electronic messaging data flow](media/electronic-messaging-data-flow.png)

## Scenarios supported by EM functionality

The EM functionality supports the following scenarios:

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

## Country-specific regulatory features supported with EM functionality

Find more information about some country-specific regulatory features supported by using EM functionality in the table below.

| Country     | Feature name | Feature demo recording |
|-------------|--------------|----------------|
| Spain       | [Immediate Supply of Information on VAT (Suministro Inmediato de Información del IVA, SII)](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-esp-sii) |  |
| Hungary     | [Online invoicing system](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-hun-online-invoicing) |  |
| United Kingdom | [Making Tax Digital (MTD) – VAT statement submission](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-gbr-mtd-vat-integration) | [Finance and Operations: UK Digital Tax - VAT Declaration In Dynamics 365](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-uk-digital-tax-vat-declaration-in-dynamics-365) |
| Lithuania   | [i.SAF reporting](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-ltu-isaf) |  |
| Poland      | [VAT declaration with registers (JPK_V7M, VDEK)](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-pol-vdek) | [Dynamics 365 Finance: SAF/JPK VAT Audit Registers](https://community.dynamics.com/365/b/techtalks/posts/dynamics-365-finance-saf-jpk-vat-audit-registers-june-4-2020) |
| Netherlands | [VAT declaration for Netherlands](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-nl-vat-declaration-netherlands) |  |
| Czech Republic | [VAT declaration](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-cze-vat-declaration-tax-declaration-model) |  |
| Brazil      | [SPED-Reinf](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/latam-bra-sped-reinf-overview) |  |


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


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
