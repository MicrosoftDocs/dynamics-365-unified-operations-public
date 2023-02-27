---
# required metadata

title: Invoice capture solution workspace
description: This article provides information about the Invoice capture solution workspace.
author: sunfzam
ms.date: 09/25/2022
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

## Side-by-side viewer for the Invoice capture solution

Entering invoices into the system has typically been a time-consuming process that is prone to errors, because clerks must navigate multiple attachment files and windows to collect the correct piece of information. The side-by-side document viewer will help improve your experience when you work on invoices, by making the process easier, more efficient, and more accurate.

The side-by-side document viewer lets users have the original document and the invoice open side by side in the same window. The invoice page is filled with information that comes from the original invoice document. The viewer builds the connection between the invoice page fields and the original invoice document. The viewer also helps users find any errors that exist on the invoice page.

### Open the side-by-side viewer

In Microsoft Dynamics 365 Finance, you can open the side-by-side viewer from the list on the summary page or from the invoice list page. You can also open it by double-tapping (or double-clicking) a record or by selecting the invoice number.

### Using the side-by-side viewer

#### Manually review an invoice

An invoice document that has been imported might require manual review because of errors or warnings. In the side-by-side viewer, the document header will show a status of **Imported**, and the current version will be **Original Version**.

To start to review the invoice, select **Start review**. All fields become editable. The **Status** field is updated to **In review**, and the **Current version** field is updated to **Modified version**.

#### View and work with messages

Users should start the review process from the message pane. Error messages are indicated by a red X, warning messages are indicated by a triangle, and informational messages are indicated by a circle. Confidence score–related messages can be classified as either warnings or errors, depending on the threshold that is set by the configuration group. For more information, see [Invoice capture solution configuration groups](invoice-capture-config-group.md).

Warning and error messages can be ignored from the message pane, the invoice header, or invoice lines. After a message is ignored, it no longer appears as an error or a warning, and the invoice won't fail validation.

- To ignore messages from the message pane, select **Ignore**. To reset a message that has been ignored, select **Ignore** again. Its type is then changed from error or warning to information.
- To ignore messages from the invoice header or the invoice line, select **Ignore** on the field. The message symbol disappears. However, it will reappear if the message is reset from the message pane.

For messages that are related to invoice header fields, when you select the message in the message pane, the cursor is moved to the corresponding field in the header section.

#### Proofread and edit fields

If a field's value is read from the original invoice through optical character recognition (OCR), a symbol appears on the field. If you select the symbol, the document viewer zooms in and highlights the place that the field value is read from, to help you verify invoice data.

To reset the document viewer to its original magnification, follow one of these steps:

- Select the same symbol that you previously selected.
- Select the button in the upper-right corner of the document viewer.

Edit the fields as required. Edits are automatically saved when the cursor leaves a field. A symbol to the right of a field indicates that the field has been manually updated. When the page is refreshed, the symbol will be removed.

#### Check an invoice to get up-to-date messages

When you edit a field, the field value is updated, but new validation messages aren't generated. To get up-to-date validation messages, select **Check**. The messages in the message pane, on the invoice header, and on the invoice lines are updated.

#### Complete the review

To complete the review, select **Complete review**. The invoices are validated. If any errors are found, the document status remains **In review**, and a message bar appears. All messages in the message pane and on the invoice header and lines are automatically updated to provide information about the causes of the failed validation.

After all blocking errors are fixed, the review can be completed. The document status is updated to **Reviewed**, and the fields can no longer be edited. You can restart the review by selecting **Start review** again.

#### Generate a pending vendor invoice in Finance

To send the invoice document to the connected Finance environment, select **Generate**. If invoice generation fails, an error message appears in a message bar.

#### Void an invoice

To void an invoice, select **Void**. Voided invoices can't be reviewed and aren't shown in the **Invoices need manual review** list.

### Validation logic

Some key fields in the side-by-side viewer don't exist in the invoice staging data but are required to generate pending invoices in Finance. These fields are derived from a combination of the current invoice staging data and master data from Finance.

The fields that must be derived are **Legal Entity**, **Vendor Account**, and **Item Number**. They must be derived in the following order. If the derivation of a field fails, the process stops.

1. **Legal entity** – The legal entity is derived first. If an active mapping rule is found for the legal entity, the legal entity is derived based on the company name and company address.
2. **Vendor account** – Next, the vendor account is derived based on an active mapping rule and a combination of the derived legal entity and the vendor's name and vendor address.
3. **Item number** – Finally, the item name is derived from staging, based on the following three types of information:

    - A configured mapping rule
    - The derived legal entity
    - The derived vendor account

To run a validation, select **Check** in the side-by-side viewer. Currently, the validation performs the following checks:

- **Mandatory check** – This check validates the mandatory fields for the side-by-side viewer. Users can select which fields must be mandatory on the **Configuration setting** page.
- **Confidence score** – Users can set the warning threshold and error threshold for the confidence score. This check focuses on the confidence score from OCR that is below those thresholds. Error or warning messages will be shown based on the validation result.
- **Legal entity** – This check validates that a legal entity is in Finance. If the legal entity doesn't exist in the Finance environment, the validation fails.

When the side-by-side viewer is used for the first time, and the user selects **Check**, the derivation and validation processes are run. If the invoices are accurate, the validation process is run when the user selects **Complete review**. It's also run when the user selects **Generate vendor invoice**.

The derivation process occurs before the validation process, and all warnings or errors come from the validation process. The warnings and errors will be logged in Finance.
