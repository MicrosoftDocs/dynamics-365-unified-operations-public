---
# required metadata

title: Invoice capture solution workspace
description: This article provides information about the Invoice capture solution workspace.
author: sunfzam
ms.date: 11/01/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution workspace

[!include [banner](../includes/banner.md)]

In Invoice capture, when an invoice is successfully recognized by AI Builder and mapped to invoice fields, it can be automatically updated and validated according to rules before it's converted to a vendor invoice in Microsoft Dynamics 365 Finance. If the invoice isn't complete, or if the confidence score of the invoice recognition isn't high enough, manual intervention is required to review and correct the invoice.

## What is the side-by-side viewer?

The side-by-side viewer provides an intuitive interface for viewing raw documents and invoice forms side by side. It uses Microsoft form recognition technology to automatically extract information from the raw document and fill in the corresponding fields on the invoice page. The viewer also establishes a connection between the page fields and the original document, so that users can navigate through the document in a single tap or click. Therefore, users can review invoices more efficiently. 
When the invoice fields have a connection with the fields that are returned from AI Builder, an eyeball symbol appears on the left side of the fields. Select the eyeball symbol to automatically position and highlight the corresponding field value on the original document.

Here are some key features of the side-by-side viewer:

- Fields on the invoice page are automatically filled with information that's extracted from raw documents by using Microsoft form recognition technology.
- A connection is established between page fields and raw documents, for effortless navigation and proofreading.
- Messages help users correct errors on the invoice page, for improved accuracy and efficiency.
- The interface can be resized to accommodate different invoice formats.
- Lookup lists are retrieved from Dynamics 365 Finance at runtime, to ensure that information is up to date and accurate.
- The interface is flexible and adapts to different invoice types, for a customizable experience.

1. The document header consists of four fields:

- **Status**
- **Legal entity**
- **Vendor account**
- **Invoice type**

2. Users can update the legal entity, vendor account, and invoice type by selecting **Classify invoice**.

3. The document viewer shows the original document. Controls in the upper-right corner let users adjust the page view by changing pages, zooming in or out, fitting the document to the page, or rotating it. Users can resize the whole pane by dragging the resize line between the original document pane and the invoice pane.

4. The invoice pane contains different cards that show invoice context.
- The message card shows all errors, warnings, and informational messages. It's an expandable/collapsible section in the central part of the interface. To expand it, users select the message symbol. Users can select which types of messages are shown.
- The **Invoice header** card shows the header fields that are set as visible through configuration groups. The fields that are shown depend on the selected invoice type.
- The **Invoice lines** card shows the grid for invoice lines. The line fields are customized through configuration groups. This card is hidden if the invoice type is **Header-only**. A maximum of five invoice lines are shown per page. Users can navigate through the pages by using the left and right arrow buttons in the lower-right corner of the interface.
- The **Charges** card and **Sales tax** show the table for charges and sales tax on the document header. If there are no charges and sales tax line, both cards are not displayed. Users can click **Show more** to display the cards. Users can manually add the charges and sales tax by clicking **Add**. 

  a) The **Charges code** has to be assigned before transferring the invoice to Dynamics 365 Finance. The charges lines will be imported with the invoice header and lines by leveraging the data entity **Header vendor invoice charges**.

  b) When the value of **Total sales tax** is null or zero and multiples sales tax lines are defined, the sum of the sales tax amount will be automatically calculated and populated in the **Total sales tax** field in the invoice header. When the **Validate total sales tax amount** parameter is enabled, the consistency between the sum of sales tax amount and the total sales tax amount are validated. If no sales tax line is defined, the validation will be skipped. 

## Captured invoice statuses

| Status | Description | Action |
|---|---|---|
| In Processing | The invoice has been successfully captured and is currently in pre-processing and validation. | No action is required. |
| Captured | Exceptions occurred during the pre-processing and validation steps. Manual intervention is required to correct the invoice. | Select **Classify invoice**, **Start review**, or **Void**. |
| In Review | The invoice is being reviewed and corrected in the side-by-side viewer. | Select **Classify invoice**, **Complete review**, or **Void**. |
| Verified | The invoice has been reviewed but not transferred. | Select **Transfer**, **Classify invoice**, **Start review**, or **Void**. |
| Transferred | The invoice was successfully transferred to Dynamics 365 Finance. | Open the invoice in Dynamics 365 Finance. |
| Voided | The invoice is no longer needed and is obsolete. | <p>Select **Obsolete**.</p><p>When you select **Obsolete**, both captured invoices and received files are permanently deleted from Dataverse.</p> |

## Navigate to the side-by-side viewer

In Dynamics 365 Finance, you can open the side-by-side viewer from two places:

- In the **Captured invoices** list, double-tap (or double-click) a record, or single-tap (or single-click) the invoice number.
- On the **Received files** page, select an invoice that has been successfully captured, and then select **View capture invoices**.

## Assign a legal entity

In the **Captured invoices** list, the legal entity might be missing because it wasn't successfully derived. The legal entity must be assigned before an invoice can be processed. Users can then review the invoices and make corrections.

1. Select the invoice, and then select **Assign legal entity**.
2. Select the legal entity in the dropdown list.
3. Select **Save**.

Correct assignment of the legal entity ensures that AP clerks can view the status of the invoice that they are responsible for.

## Classify an invoice

For the vendor invoice to be successfully created in Dynamics 365 Finance, entities such as legal entity, vendor account, and item number must be determined before the transfer. Of these entities, legal entity and vendor account are the most important, because they determine whether the derived invoice type is acceptable according to the setting in the assigned configuration group.

If the legal entity and vendor account aren't determined by the derivation rule, a user must update these fields by selecting **Classify invoice**. A side pane that appears will prompt the user to provide the following information:

- Legal entity
- Vendor account
- Invoice type

The derivation and validation logic is triggered again immediately after the user selects **Save and close**.

## Manual review process

An invoice document that has been captured might require manual review because of errors or warnings. In the side-by-side viewer, the document header will show a status of **Captured**, and the current version will be **Original Version**.

The invoice header information (legal entity, vendor account, invoice type) must be complete before users can start to review the invoice.

When a user selects **Start review**, the **Status** field is updated to **In review**, and the **Current version** field is updated to **Modified version**. The invoice form is then in edit mode. 

AP clerk can enter values for invoice header or add/edit/delete lines in the **Invoice lines**, **Charges**, and **Sales tax** fields. Clicking **Remove all** will delete all the invoice lines.

By clicking the top-right icon in the document preview pane, the invoice will be in mapping mode. AP clerk can then correct/add the mapping by selecting the key-value pair and the **Mapped invoice** field. After saving the changes, it will extract the value and apply to the corresponding invoice field. When the continuous learning feature is enabled, the system learns the changes and applies the same logic from invoices from the same vendor.

## Derivation and validation logic

Some entity fields in the side-by-side viewer don't exist immediately after the invoice is recognized but are required to generate the invoice in Dynamics 365 Finance. These entities are derived from a combination of the recognized invoice data and master data from Dynamics 365 Finance.

The entities include legal entity, vendor account, and item number. If derivation of a field fails, the process stops.

1. **Legal entity** – If an active mapping rule is found for the legal entity, the legal entity is selected based on the company's name and address.
2. **Vendor account** – Next, the vendor account is selected based on an active mapping rule and a combination of the selected legal entity and the vendor's name, address, or tax number.
3. **Item number** – The item name is derived from staging, based on the following three types of information:

    1. Derived legal entity
    2. Derived vendor account
    3. Item description or external item number

4. **Currency code** – The currency code has to be determined before transferring the invoice from invoice capture to Dynamics 365 Finance.
   
    1. When an invoice associated with purchase order (PO invoice or Header-only invoice), the currency code between invoice and purchase order must be the same. When no currency code returned from the recognition result, the currency code will default from the purchase order. 
    2. A cost invoice can select to derive the currency code from the vendor master data by selecting the **Derive currency code for cost invoice** parameter.

After the fields are derived, the following additional validation checks are run:

- **Mandatory check** – This check validates the mandatory fields for the side-by-side viewer. Users can select which fields must be mandatory on the **Configuration settings** page.
- **Confidence score** – Users can set the warning and error thresholds for the confidence score. This check focuses on the confidence score from optical character recognition (OCR) that's below those thresholds. Error or warning messages will be shown based on the validation result.
- **Existing check** – This check validates the existence of entities, including legal entity, vendor account, item number, procurement category, or purchase order.
- **Advanced check** – When a stock item is used, the purchase order details must be assigned to the invoice line.

When the user selects **Derive and check**, the derivation and validation processes are run. If there are no errors in the invoices, the validation logic is called only when the user selects **Complete review** or **Transfer**.

The derivation process occurs before the validation process, and all warnings or errors come from the validation process. The warnings and errors will be logged in the history log. Users can select **View history** to review the errors.

> [!NOTE]
> The current derivation and validation logic includes the most common scenarios. More specific validations can be implemented through customer extension.

## Continuous learning

To help increase the touchless rate of invoice processing in Invoice capture, **Continuous learning** can derive entities (legal entity, vendor account, and item numbers) based on the mapping from the last transferred invoice. Manual intervention is required.

## Void and delete an invoice

If the invoice contains errors, users can void it by selecting **Void**. After an invoice is voided, it appears on the **Capture invoices (Voided)** page and can't be reviewed and included again unless the status is changed from **Void** to **Capture from Dataverse**.

Users can delete the invoice by selecting **Delete**. The invoice is permanently deleted from Dataverse and can't be recovered. When an invoice is deleted, the linked entry on the **Received files** page is also deleted.

## Transfer an invoice

When users complete their review, if the invoice contains no errors, they can select  **Transfer** to send the invoice to the connected Dynamics 365 Finance environment.

- If invoice generation fails, an error message is shown.
- If the invoice is successfully generated, the status of captured invoice is **Complete**.

There are two ways to transfer the complete invoice:
- If invoice transfer is triggered manually, it will use the synchronous mode. 
- If the invoice transfer is triggered automatically through the touchless process, it will be submitted into the awaiting list and the **Transfer invoices from invoice capture** will process these invoices.

## Status
1. **In Processing** - The invoice has been successfully captured and is currently being processed for creation in the captured invoices section. It's not allowed to update the invoices with this status.
   
2. **Captured** - The invoice is ready for further action. Account payable (AP) clerk can use the classify invoice function to determine the legal entity, vendor account, and invoice type if needed. 
   
3. **In Review** - The invoice is being reviewed in a modified mode. The Accounts Payable (AP) clerk has the following options:
    1. Assign correct values for entity details such as items, and procurement categories.
    2. Choose the correct purchase order number.
    3. Disregard any confidence score warnings or errors.
    4. Correct the invoice context.

4. **Verified** - The invoice has been reviewed, doesn't contain any errors and is ready for transfer. Click **Transfer** to move the invoice from invoice capture to Dynamics 365 Finance.
5. **Transferred** - The invoice has been successfully transferred to Dynamics 365 Finance. Click **Dynamics 365 Finance** to navigate to either the pending vendor invoice section or the invoice journal based on the Invoice capture settings to check the transferred result.
6. **Voided** - The invoice is no longer needed and is obsolete. All the records and attached invoice files will be permanently deleted.
7. **Awaiting** - The invoice is submitted to the waiting list to be picked up by the automation job in Dynamics 365 Finance for further processing. 

