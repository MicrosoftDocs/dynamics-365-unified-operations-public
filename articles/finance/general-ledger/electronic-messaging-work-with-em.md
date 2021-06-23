---
# required metadata

title: Electronic messaging
description: This topic provides information about how to Work with the Electronic messages functionality in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.date: 06/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: liza-golub
ms.search.validFrom: 2021-06-24
ms.dyn365.ops.version: 10.0.21

---

# Work with the Electronic messages functionality

[!include [banner](../includes/banner.md)]

If you're working at the message level, the **Electronic messages** page (**Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**) is more useful. If you're operating at the data collection (message item) level, the **Electronic message items** page (**Tax** \> **Inquires and reports** \> **Electronic messages** \> **Electronic message items**) is more useful.

## Electronic messages

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

## Electronic message items

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

### Run processing

Select **Run processing** on the Action Pane to run the processing for message items. To run a specific action, in the **Run processing** dialog box, set the **Choose action** option to **Yes**, and then select an action. To run the whole processing, leave the **Choose action** option set to **No**.

### Generate report

Select **Generate report** on the Action Pane to generate a report. This button is associated with actions of the **Electronic reporting export** type.

### Update status

Select **Update status** on the Action Pane to update the status of one or more message items. In the **Update status** dialog box, use the **Records to include** FastTab to select the message items to update. Make sure that you correctly define the selection criteria, because message item statuses will be updated according to these criteria, the initial status of the selected action, and the **New status** value that you specify. After a status update is completed, it will be difficult to determine which items were updated. Therefore, it will be difficult to roll back the status update.

### Electronic messages

Select **Electronic messages** on the Action Pane to review an electronic message that is related to the selected message item.

You can also review all the files that are related to a specific message item. Select the **Message** field for the message item, or select **Electronic messages** on the Action Pane. Then, on the **Electronic message** page, select the message to review files for, and then select the **Attachment** button (the paper clip symbol) in the upper-right corner of the page.

![Attachment button](media/attachment-icon.png)

The **Attachments** page shows all the attachments that are related to the message. To view a file, select it in the list on the left, and then select **Open** on the Action Pane.

![Open button](media/open-button.png)

### Original document

Select **Original document** on the Action Pane to open the original document for the selected message item.
