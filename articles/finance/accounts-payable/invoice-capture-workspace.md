---
# required metadata

title: Invoice capture solution workspace
description: This article provides information about the Invoice capture solution workspace.
author: sunfzam
ms.date: 04/04/2023
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
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution workspace

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

In Invoice capture, when an invoice is successfully recognized by AI Builder and mapped to invoice fields, it can be automatically updated and validated according to rules before it's converted to a vendor invoice in Microsoft Dynamics 365 Finance. If the invoice isn't complete, or if the confidence score of the invoice recognition isn't high enough, manual intervention is required to review and correct the invoice.

## Side-by-side viewer for the Invoice capture solution

The side-by-side viewer provides an intuitive interface for viewing raw documents and invoice forms side by side. It uses Microsoft form recognition technology to automatically extract information from the raw document and fill in the corresponding fields on the invoice page. The viewer also establishes a connection between the page fields and the original document, so that users can navigate through the document in a single tap or click.

### Open the side-by-side viewer

In Dynamics 365 Finance, you can open the side-by-side viewer from two places:

- In the **Captured invoices** list, double-tap (or double-click) a record, or single-tap (or single-click) the invoice number.
- On the **Received files** page, select an invoice that has been successfully captured, and then select **View capture invoices**.

Here are the key features of the side-by-side viewer:

- Fields on the invoice page are automatically filled with information that's extracted from raw documents by using Microsoft form recognition technology.
- A connection is established between page fields and raw documents, for effortless navigation and proofreading.
- Messages are shown to help users correct errors on the invoice page, for improved accuracy and efficiency.
- The interface can be resized to accommodate different invoice formats.
- Lookup lists are fetched from Finance at runtime, to ensure that information is up to date and accurate.
- The interface is flexible and adapts to different invoice types, for a customizable experience.

### Use the side-by-side viewer

The document header consists of four fields: **Status**, **Legal entity**, **Vendor account**, and **Invoice type**. You can update these fields by selecting **Classify invoice**.

On the left side pane of the interface, the document viewer shows the original document. The controls in the upper-right corner let users adjust the page view by changing pages, zooming in or out, fitting the document to the page, or rotating it.

The message pane shows all errors, warnings, and informational messages. It's an expandable/collapsible section in the central part of the interface. To expand it, users select the message symbol. Users can select which types of messages are shown.

The invoice header fields can be customized through configuration groups and depend on the selected invoice type.

The invoice lines section can also be customized through configuration groups. It isn't visible if the invoice type is **Header-only**. A maximum of five invoice lines are shown per page. Users can navigate through the pages by using the left and right arrow buttons in the lower-right corner of the interface.

#### Manually review an invoice

An invoice document that has been captured might require manual review because of errors or warnings. In the side-by-side viewer, the document header will show a status of **Captured**, and the current version will be **Original Version**.

To start to review the invoice, select **Start review**. The **Status** field is updated to **In review**, and the **Current version** field is updated to **Modified version**.

### Assign a legal entity

In the **Captured invoices** list, the legal entity might be missing because it wasn't successfully derived. The legal entity must be assigned before an invoice can be processed. Users can then review the invoices and make the corrections.

1. Select the invoice, and then select **Assign legal entity**.
2. Select the legal entity in the drop-down list.
3. Select **Save**.

### Classify an invoice

In the side-by-side viewer, if the legal entity and vendor account aren't derived, the **Classify invoice** button is shown. The user must complete the following information:

- Legal entity
- Vendor account
- Invoice type

The derivation and validation logic will start after this information is completed.

### Validation logic

Some key fields in the side-by-side viewer don't exist in the invoice staging data but are required to generate pending invoices in Finance. These fields are derived from a combination of the current invoice staging data and master data from Finance.

The fields that must be derived are **Legal entity**, **Vendor account**, and **Item number**. They must be derived in that order. If derivation of a field fails, the process stops.

1. **Legal entity** – If an active mapping rule is found for the legal entity, the legal entity is derived based on the company's name and address.
2. **Vendor account** – Next, the vendor account is derived based on an active mapping rule and a combination of the derived legal entity and the vendor's name, address, or tax number.
3. **Item number** – Finally, the item name is derived from staging, based on the following three types of information:

    - Derived legal entity
    - Derived vendor account
    - Item description or external item number

After the fields are derived, the following additional validation checks are run:

- **Mandatory check** – This check validates the mandatory fields for the side-by-side viewer. Users can select which fields must be mandatory on the **Configuration setting** page.
- **Confidence score** – Users can set the warning and error thresholds for the confidence score. This check focuses on the confidence score from optical character recognition (OCR) that's below those thresholds. Error or warning messages will be shown based on the validation result.
- **Existing check** – This check validates the existence of entities, including legal entity, vendor account, item number, procurement category, or purchase order.
- **Advanced check** – When a stock item is used, the purchase order details must be assigned to the invoice line.

When the user selects **Derive and check**, the derivation and validation processes are run. If there are no errors in the invoices, the validation logic is called only when the user selects **Complete review** or **Transfer**.

The derivation process occurs before the validation process, and all warnings or errors come from the validation process. The warnings and errors will be logged in the history log. Users can select **View history** to review the errors.

> [!NOTE]
> The current derivation and validation logic includes the most common scenarios. More specific validations can be implemented through customer extension.

### Continuous learning

To help increase the touchless rate of invoice processing in Invoice capture, **Continuous learning** can derive entities (legal entity, vendor account, and item numbers) based on the mapping from the last transferred invoice. Manual intervention is required.

### Void and delete an invoice

If the invoice contains errors, users can void it by selecting **Void**. After an invoice is voided, it can't be reviewed and included again. Alternatively, users can delete the invoice by selecting **Delete**. When an invoice is deleted, the linked entry on the **Received files** page is also deleted.

### Transfer an invoice

When users complete their review, if the invoice contains no errors, they select **Transfer** to send the invoice to the connected Finance environment.

- If invoice generation fails, an error message is shown.
- If the pending invoice is successfully generated, the status of captured invoice is **Complete**.

> [!NOTE]
> After the invoice is successfully transferred, the original document is automatically imported from invoice capture to Finance.
