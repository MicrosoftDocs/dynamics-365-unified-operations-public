---
title: Invoice capture solution workspace
description: Learn about the Invoice capture solution workspace, including on outline on the side-by-side viewer and captured invoice statuses.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 08/08/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture solution workspace

[!include [banner](../includes/banner.md)]

In Invoice capture, when an invoice is successfully recognized by AI Builder and mapped to invoice fields, it can be automatically updated and validated according to rules before it's converted to a vendor invoice in Microsoft Dynamics 365 Finance. If the invoice contains errors or warnings, manual intervention is required to review and correct the invoice.

## What is the side-by-side viewer?

The side-by-side viewer provides an intuitive interface for viewing raw documents and invoice forms side by side. It uses Microsoft form recognition technology to automatically extract information from the raw document and fill in the corresponding fields on the invoice page. The viewer also establishes a connection between the page fields and the original document, so that users can navigate through the document in a single tap or click. Therefore, users can review invoices more efficiently. 
When the invoice fields have a connection with the fields that are returned from AI Builder, an eyeball symbol appears on the left side of the fields. Select the eyeball symbol to automatically position and highlight the corresponding field value on the original document.

Here are some key features of the side-by-side viewer:

- Fields on the invoice page are automatically filled with information that's extracted from raw documents by using Microsoft form recognition technology.
- A connection is established between page fields and raw documents, for effortless navigation and proofreading.
- Messages help users correct errors on the invoice page, for improved accuracy and efficiency.
- The interface can be resized to accommodate different invoice formats.
- Lookup lists are retrieved from Dynamics 365 Finance at runtime, to ensure that information is up to date and accurate.
- The interface is flexible and adapts to different invoice types.

1. The document header consists of four fields:

    - **Status**
    - **Legal entity**
    - **Vendor account**
    - **Invoice type**

2. Users can update the legal entity, vendor account, and invoice type by selecting **Classify invoice**.
3. The document viewer shows the original document. Controls in the upper-right corner let users adjust the page view by changing pages, zooming in or out, fitting the document to the page, or rotating the document. Users can resize the whole pane by dragging the resize line between the original document pane and the invoice pane.
4. The invoice pane contains different cards that show the invoice context.

    - The **Message** card shows all errors, warnings, and informational messages. It's an expandable/collapsible section in the central part of the interface. To expand it, users select the message symbol. Users can select which types of messages are shown.
    - The **Invoice header** card shows the header fields that are set as visible through configuration groups. The fields that are shown depend on the selected invoice type.
    - The **Invoice lines** card shows the grid for invoice lines. The line fields are customized through configuration groups. This card is hidden if the invoice type is **Header-only**. A maximum of five invoice lines are shown per page. Users can navigate through the pages by using the left and right arrow buttons in the lower-right corner of the interface.
    - The **Charges** and **Sales tax** cards show the table for charges and sales tax on the document header. If there are no charges lines and sales tax lines, these cards are hidden. Users can select **Show more** to show the cards, and they can manually add charges and sales tax by selecting **Add**. 

        - The **Charges code** value must be assigned before the invoice can be transferred to Dynamics 365 Finance. The charges lines will be imported together with the invoice header and lines by using the **Vendor invoice charges** data entity.
        - If the value of the **Total sales tax** field is null or zero, and multiple sales tax lines are defined, the sum of the sales tax amount is automatically calculated and entered in the **Total sales tax** field on the invoice header. If the **Validate total sales tax amount** parameter at **Setup system** \> **Manage processing rule** is enabled, the consistency between the sum of the sales tax amount and the total sales tax amount is validated. If no sales tax line is defined, the validation is skipped. 

### Captured invoice statuses

| Status | Description | Action |
|---|---|---|
| In process | The invoice has been successfully captured and is currently in pre-processing and validation. | No action is required. |
| Captured | Exceptions occurred during the pre-processing and validation steps. Manual intervention is required to correct the invoice. | Select **Classify invoice**, **Start review**, or **Void**. |
| In review | The invoice is being reviewed and corrected in the side-by-side viewer. | Select **Classify invoice**, **Complete review**, or **Void**. |
| Verified | The invoice has been reviewed but not transferred. | Select **Transfer**, **Classify invoice**, **Start review**, or **Void**. |
| Transferred | The invoice was successfully transferred to Dynamics 365 Finance. | Open the invoice in Dynamics 365 Finance. |
| Voided | The invoice is no longer needed and is obsolete. | <p>Select **Obsolete**.</p><p>When you select **Obsolete**, both captured invoices and received files are permanently deleted from Dataverse.</p> |
| Awaiting | The invoice has been submitted to the waiting list so that the automation job in Dynamics 365 Finance can pick it up for further processing. | No action is required. |

### Navigate to the side-by-side viewer

You can open the side-by-side viewer from two places:

- In the **Captured invoices** list, double-tap (or double-click) a record, or single-tap (or single-click) the invoice number.
- On the **Received files** page, select an invoice that has been successfully captured, and then select **View capture invoices**.

### Classify captured invoices

#### Assign a legal entity on the list page

In the **Captured invoices** list, the legal entity might be missing because it wasn't successfully derived. The legal entity must be assigned before an invoice can be processed. Users can then review the invoices and make corrections.

1. Select the invoice, and then select **Assign legal entity**.
2. Select the legal entity in the dropdown list.
3. Select **Save**.

Correct assignment of the legal entity ensures that Accounts payable (AP) clerks can view the status of the invoice that they are responsible for.

#### Classify an invoice on the detailed page

For the vendor invoice to be successfully created in Dynamics 365 Finance, entities such as legal entity, vendor account, and item number must be determined before the transfer. Of these entities, legal entity and vendor account are the most important, because they determine whether the derived invoice type is acceptable according to the setting in the assigned configuration group.

If the legal entity and vendor account aren't determined by the derivation rule, a user must update these fields by selecting **Classify invoice**. A side pane that appears will prompt the user to provide the following information:

- Legal entity
- Vendor account
- Invoice type

The derivation and validation logic is triggered again immediately after the user selects **Save and close**.

### Review process

An invoice document that has been captured might require manual review because of errors or warnings. In the side-by-side viewer, the document header will show a status of **Captured**, and the current version will be **Original Version**.

The invoice header information (legal entity, vendor account, and invoice type) must be complete before users can start to review the invoice.

When a user selects **Start review**, the **Status** field is updated to **In review**, and the **Current version** field is updated to **Modified version**. The invoice form is then in edit mode. 

The AP clerk can enter values for the invoice header. Alternatively, they can add, edit, or delete lines in the **Invoice lines**, **Charges**, and **Sales tax** fields. By selecting **Remove all**, they can delete all the invoice lines.

The AP clerk can select the upper-right icon in the document preview pane to put the invoice into mapping mode. The AP clerk can then correct or add the mapping by selecting the key-value pair and the **Mapped invoice** field. After the changes are saved, the value is extracted and applied to the corresponding invoice field. When the continuous learning feature is enabled, the system learns the changes and applies the same logic to invoices from the same vendor.

### Map key-value pairs with fields

Sometimes, the prebuilt model doesn't extract the value from the correct position of the document for some fields. Users want to correct the extraction and let the application constantly extract the correct value for subsequent incoming invoices that come from the same vendor and have the same pattern. If the value that must be extracted is returned as a key-value pair from the AI model, this correction is done on the key-value pair mapping page. When the continuous learning feature is enabled, the key-value pair mapping learns.

The key-value pair mapping function is applied when the prebuilt model is used. If you're using a custom invoice model, use the custom field mapping to extract additional fields. Select the icon in the upper right of the document preview pane to change invoices to mapping mode.

- Light yellow indicates that the key-value pair has already been mapped with invoice fields.
- Light blue indicates that the key-value pair hasn't yet been mapped with any invoice fields. The AP clerk can correct or add the mapping by selecting the key-value pair and the mapped invoice field. After the changes are saved, the value is extracted and applied to the corresponding invoice field. When the continuous learning feature is enabled, the system learns the changes and applies them to invoices from the same vendor.

> [!NOTE]
> The key-value pair mapping page button is available only for invoices that are received after an upgrade to version 1.1.0.32. It's unavailable for invoices that were received before the upgrade.

### Download the original invoice document

In the document preview pane, the download button can help users download the original invoice document.

### Derivation and validation

Some entity fields in the side-by-side viewer don't exist on the original invoice document but are required to generate the invoice in Dynamics 365 Finance. These entities are derived from a combination of the recognized invoice data and master data from Dynamics 365 Finance.

The entities include **Legal entity**, **Vendor account**, **Item number**, and **currency code**. If derivation of a field fails, the process stops.

1. **Legal entity** – If an active mapping rule is found for the legal entity, the legal entity is selected based on the company's name and address.
2. **Vendor account** – Next, the vendor account is selected based on an active mapping rule and a combination of the selected legal entity and the vendor's name, address, or tax number.
3. **Item number** – The item number is derived based on the following three types of information:

    1. Derived legal entity
    2. Derived vendor account
    3. Item description or external item number

4. **Currency code** – The currency code must be determined before the invoice can be transferred from Invoice capture to Dynamics 365 Finance. Different methods are implemented to derive the currency code:

    - If the currency symbol is captured and can be used to uniquely identify the currency code, the currency code is automatically derived. 
    - If an invoice is associated with a purchase order (PO invoice or header-only invoice), the invoice and the purchase order must use the same currency code. If no currency code is returned from the recognition result, the currency code from the purchase order is entered by default.
    - If you want a cost invoice to derive the currency code from the vendor master data, select the **Derive currency code for cost invoice** parameter at **Setup system** \> **Manage processing rules**.

After the fields are derived, the following additional validation checks are run:

- **Mandatory check** – This check validates the mandatory fields for the side-by-side viewer. Users can select which fields must be mandatory on the **Configuration settings** page.
- **Confidence score** – Users can set the warning and error thresholds for the confidence score. This check focuses on the confidence score from optical character recognition (OCR) that's below those thresholds. Error or warning messages will be shown based on the validation result.
- **Existing check** – This check validates the existence of entities, including legal entity, vendor account, item number, procurement category, or purchase order.
- **Advanced check** – When a stock item is used, the purchase order details must be assigned to the invoice line.

When the user selects **Derive and check**, the derivation and validation processes are run. If there are no errors in the invoices, the validation logic is called only when the user selects **Complete review** or **Transfer**.

The derivation process occurs before the validation process, and all warnings or errors come from the validation process. The warnings and errors will be logged in the history log. Users can select **View history** to review the errors.

> [!NOTE]
> The current derivation and validation logic includes the most common scenarios. More specific validations can be implemented through customer extension.

### Continuous learning

To help increase the touchless rate of invoice processing in Invoice capture, the **Continuous learning** feature can derive entities (legal entity, vendor account, and item numbers) based on the mapping from the last transferred invoice. It also supports automatic extraction of a value from a key-value pair and assignment of that value to the corresponding invoice fields. When there's an entry on the **Charges** card, continuous learning derives the **Charges code** value based on the last matched record. The feature can be turned on and off at **Setup system** \> **System preferences**.

#### Difference between continuous learning and mapping rules

The **Continuous learning** feature tries to record patterns between the invoice context and manually selected entities immediately after the invoice is successfully transferred. The affected entities include legal entity, vendor account, item number, expense type, charge code, and key-value pair mapping. Currently, continuous learning checks all the header information, such as the company name, company address, vendor name, address, and vendor tax registration number, to determine the value of the legal entity and vendor account. When the first invoice arrives, users must manually specify the legal entity and vendor account if they can't be successfully derived from other mapping rules. After the invoices are reviewed and transferred to Dynamics 365 Finance, the relationship is recorded. When any invoice that has the same context arrives, continuous learning tries to find the same pattern and to derive the legal entity and vendor account automatically.

Mapping rules are in some ways an optional approach to derive the value of entities. They can derive entity values when the conditions are fulfilled for all the fields. Because the maintenance load is quite high, we don't recommend that customers use this approach. The only exception is the expense type. For the expense type, we recommend that customers use the pending vendor invoice framework for non-PO invoices. For this approach, you can define a default expense type (procurement category) that is applied to all the lines for invoices from a specific vendor. This assigned procurement category is used to derive the expense accounting during accounting distribution on the finance and operations apps side. It can increase the touchless rate for the processing of non-PO invoices.

From a logic sequence perspective, continuous learning is applied before mapping rules.

### Link purchase orders

#### Header-only invoice

When the invoice type is **Header-only**, users can select one or multiple purchase orders in the lookup list by selecting **Purchase order** on the invoice header. The list shows all purchase orders from the same vendor account that have an **Open order** or **Received** status. Any recognized purchase orders that aren't valid appear in red. Users must remove these purchase orders by selecting **X** before they select purchase orders in the lookup list.

#### Purchase-order invoice

When the invoice type is **Purchase-order invoice**, the relationship between the invoice line and the purchase line must be established correctly in Invoice capture. If the purchase line can't be automatically derived, the AP clerk can manually establish the relationship on the **Link purchase line with invoice line** page. To open this page, select the purchase order field on the invoice header or the purchase order number (or purchase order line number) on the invoice line.

On the **Link purchase line with invoice line** page, the following sections are available:

- The first section shows the currently selected invoice line.
- The **Available purchase lines** section shows all the purchase line candidates that match the item (or expense type) on the invoice line, based on specific criteria. These criteria include purchase order, item number, expense type, and item description. The available purchase lines have the same quantity sign as the invoice line.
- When an invoice line is linked to a purchase line, an option button (also known as a radio button) is enabled for the corresponding record, and the icon in the upper right of the invoice line pane changes to a green check mark. If there is no associated purchase line, a red cross icon is shown.
- After you confirm the association, the linked purchase line and item number (or expense type) are written back to the invoice line. Additionally, the purchase order on the invoice header is updated based on the associated purchase orders.

### Void and delete an invoice

If the invoice contains errors, users can void it by selecting **Void**. After an invoice is voided, it appears on the **Capture invoices (Voided)** page and can't be reviewed and included again unless the status is changed from **Void** to **Capture from Dataverse**.

Users can delete the invoice by selecting **Delete**. The invoice is permanently deleted from Dataverse and can't be recovered. When an invoice is deleted, the linked entry on the **Received files** page is also deleted.

## Transfer an invoice

When users complete their review, if the invoice contains no errors, they can select **Transfer** to send the invoice to the connected Dynamics 365 Finance environment.

- If invoice generation fails, an error message is shown.
- If the invoice is successfully generated, the status of captured invoice is **Complete**.

There are two ways to transfer the complete invoice:

- If invoice transfer is manually triggered, it uses the synchronous mode.
- If the invoice transfer is automatically triggered through the touchless process, it's submitted to the awaiting list, and **Transfer invoices from invoice capture** will process the invoices.

> [!NOTE]
> The process automation task is named **Transfer invoices from Invoice capture**. The default repeat interval of the task is one hour. To modify this internal, Admins can go to **System administration** \> **Setup** \> **Process automation** \> **Background processes**.
