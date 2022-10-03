---
# required metadata

title: Invoice capture solution workspace 
description: This article provides information about the invoice capture solution workspace. 
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

Entering invoices into the system has been a long process. Clerks usually need to navigate through multiple attachment files and windows to
collect the right piece of information, which can be time consuming and error prone. With the document side by side viewer, this process becomes easier. 

The document side by side viewer, allows users to have the original document and the invoice displayed side by side in the same window. The invoice page is now 
filled with information that comes from the original invoice document. The viewer builds the connection between the page fields and original invoice document. 
The viewer also helps users find possible errors that exist on the page. This viewer will improve your experience working on the invoices by introducing simplicity, 
efficiency, and accuracy. 

### How to open the side-by-side viewer 

The viewer can be accessed in Dynamics 365 Finance from the list on the summary page or from the invoice list page. It also can be accessed by double clicking a record 
or single click the invoice number. 

### Side-by-side viewer user guide 

#### When an invoice needs manual review 

An invoice document has been imported and needs manual review due to errors or warnings. In the side-by-side viewer, the document header will show a status 
of **Imported** and the current version is **Original Version**. 

To start reviewing the invoice, click **Start review**. When the review starts, all fields become editable. The **Status** and **Current version** will be updated to 
**In review** and **Modified version**. 

#### Viewing and working with messages 

Users should start the review process from the message panel. Error messages are displayed with a red X, warning messages are displayed with triangle, information 
messages are displayed with a circle. Confidence score-related messages can be either classified as warning or error. This is based on the threshold set by the 
configuration group. For more information, see Invoice capture solution configuration group.  

Warning and error messages can be ignored from the message panel, the invoice header or invoice lines. When ignored, the message will no longer be displayed as 
error or warning, and won't fail validation.  

To ignore messages from the message panel, click **Ignore**. Messages that are ignored can be reset by clicking **Ignore** and its type will be changed from error or 
warning to information. 

To ignore message from the invoice header or the invoice line, click **Ignore** on the field. The message icon will disappear after ignoring and will come back if the message is reset from the message panel. 

For messages related to invoice header fields, click the message in the message panel will move the cursor to the corresponding field in the header section. 
 
#### Proofreading and editing fields 

An icon will show on the field if the field’s content is read from the original invoice through OCR. Click the icon and the document viewer will zoom in and highlight
where the field value is taken from to help with verifying invoice data.  

To reset the document viewer to its original display ratio, you can: 
 - Click on the same icon that was previously clicked.
 - Click on the button on the upper right corner of the document viewer. 

Edit the fields as needed, the edited field will be automatically saved when the cursor leaves the field. An icon will be displayed to the right of the edited field to indicate that this field has been manually updated. When the page is refreshed, the icon will be removed.

#### Check an invoice to get up-to-date messages 

Editing a field will update the field values but won't generate new validation messages. To get the most up-to-date validation messages, click **Check**. The messages in both the message panel and the invoice header / lines will be updated. 

#### Completing review 

To complete review, click **Complete review**. 

Invoices will be validated, if errors are found, the document status will remain in **In review** and a message bar will be displayed. All messages in the message 
panel and the invoice header / lines are all automatically refreshed and will provide information about causes of the failed validation. 

When the blocking errors are fixed, the review will be able to be completed. The document status will be updated to **Reviewed** and the fields can't be edited. 
You can restart the review by clicking **Start review** again.

#### Generate a pending vendor invoice in Dynamics 365 Finance  

Click **Generate** to send the invoice document to the connected Dynamics 365 Finance environment. If the invoice generation fails, the error message will be displayed
in a message bar. 

#### Void an invoice 

To voice an invoice, click **Void**. The Voided invoices won't be able to be reviewed and won't be shown in the **Invoices need manual review** list. 

### Validation logic  

From the side-by-side viewer, there are key fields like **Legal Entity**, **Vendor Account** and **Item Number**. Sometimes those fields don't exist in the 
invoice staging data, but are mandatory to generate pending invoices in Dynamics 365 Finance. The fields are derived from the current invoice staging data 
combined with master data from Dynamics 365 Finance. 

The fields that need to be derived are **Legal Entity**, **Vendor Account** and **Item Number**. The derivation order is listed below and during each step, if the 
derivation fails, it will not go the next step. 
 1. **Legal entity** - The legal entity is derived in the first step. When an active mapping rule is found for the legal entity,  the legal entity will be derived 
based on the company name and company address.  
 2. **Vendor account** - After the legal entity is derived, a **Vendor account** will be derived using an active mapping rule and from the legal entity that was derived from the first step combined with the vendor's name and vendor address. 
 3. **Item number** -   The **Item name** will be derived from staging based on the below three types of information: 
  - A configured mapping rule 
  - The legal entity from the previous step
  - The vendor account from the previous step 

On the side-by-side viewer, click **Check** and a validation check will be ran. Currently, the validation checks for:
 - **Mandatory check** 
 - **Confidence score** 
 - **Legal entity** 

**Mandatory check** validates the mandatory fields for the side-by-side viewer. Users can select which fields need to be mandatory in the **Configuration setting**.

**Confidence score**: Users can set the warning threshold and error threshold for the confidence score. The **Confidence score** check focuses on the confidence score 
from OCR that below those thresholds. The error or warning messages will be shown based on the validation result.  

**Legal entity check**: This is a check if a legal entity is in Dynamics 365 Finance. If the legal entity doesn't exist in the Dynamics 365 Finance environment, the validation will fail. 

When the side-by-side viewer is used the first time, and the user clicks **Check**, the derivation and validation processes are ran. If the invoices are accurate, the user clicks **Complete review** and the validation process will run. When the user clicks **Generate vendor invoice**, the validation process is ran. 

The derivation process will happen before validation process and all the warnings or errors come from validation process. The warnings and errors will be logged 
into Dynamics 365 Finance.   

 



