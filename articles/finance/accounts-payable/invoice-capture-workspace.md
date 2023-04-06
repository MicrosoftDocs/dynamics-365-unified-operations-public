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

In Invoice capture, when an invoice is successfully recognized by AI Builder and mapped to invoice fields, the invoice can be updated and validated automatically according to rules before being converted to a vendor invoice in Dynamics 365 Finance. If the invoice isn't complete or the recognitive result isn't confident enough, it requires intervention to review and correct the invoice. 
 
## Side-by-side viewer for the Invoice capture solution

The side-by-side viewer provides an intuitive interface for viewing raw documents and invoice forms side by side. It leverages Microsoft's form recognition technology to automatically extract information from the raw document and populate the corresponding fields in the invoice page. Additionally, the viewer establishes a connection between the page fields and the original document, allowing users to navigate through the document with a single click. 

### Open the side-by-side viewer

In Microsoft Dynamics 365 Finance, you can open the side-by-side viewer from:
 - The **Captured invoices** list, by double clicking a record or single click the invoice number. 
 - **Received files**, selecting an invoice that has been successfully captured and click **View capture invoices**.

The key features of the side-by-side viewer are: 
 - Auto-population of fields on the invoice page with information extracted from raw documents, utilizing Microsoft's form recognition technology. 
 - Establishment of a connection between page fields and raw documents for effortless navigation and proofreading. 
 - Display of messages to help users correct errors on the invoice page, improving accuracy and efficiency. 
 - Resizable interface, accommodating various invoice formats. 
 - Runtime fetching of lookup lists from Dynamics 365 Finance, ensuring up-to-date and accurate information. 
 - Flexible interface that adapts to different invoice types, providing a customizable experience. 

### Using the side-by-side viewer

The document header is composed of four fields: **Status**, **Legal entity**, **Vendor account**, and **Invoice type**. These fields can be modified by clicking **Classify invoice**. 

On the left side pane of the interface, the document viewer displays the original document. The upper right corner allows users to adjust the page view by changing pages, zooming in or out, fitting the document to the page, or rotating it. 

The message panel is a collapsible section that contains all errors, warnings, and information messages. It is located in the central area of the interface and can be expanded by clicking the message icon. Users can choose which types of messages to display. 

The invoice header fields can be customized through configuration groups and depend on the selected invoice type. 

The invoice lines section can also be customized through configuration groups, and it isn't visible if the invoice type is header-only. A maximum of five invoice lines are displayed per page. Users can navigate through the pages using the left and right arrow buttons located at the bottom right corner of the interface. 

#### Manually review an invoice

An invoice document that has been captured might require manual review because of errors or warnings. In the side-by-side viewer, the document header will show a status of **Captured**, and the current version will be **Original Version**.

To start to review the invoice, select **Start review**. The **Status** field is updated to **In review**, and the **Current version** field is updated to **Modified version**.


### Assign legal entity 

In the **Captured invoices** list, the legal entity might be missing as it isn't successfully derived. To not interrupt the invoice processing, the legal entity has to be assigned first and then users can review the invoices and make the corrections. 

1. Select the invoice and click **Assign legal entity**.
2. Select the legal entity in the drop-down list. 
3. Click **Save**. 

### Classify invoice

In the side-by-side viewer, if legal entity and vendor account aren't derived, **Classify invoice** is displayed and the user must complete the following information: 
 - Legal entity 
 - Vendor account 
 - Invoice type 

The derivation and validation logic will start after this information is complete.  


### Validation logic

Some key fields in the side-by-side viewer don't exist in the invoice staging data but are required to generate pending invoices in Finance. These fields are derived from a combination of the current invoice staging data and master data from Finance.

The fields that must be derived are **Legal Entity**, **Vendor Account**, and **Item Number** and in the following order. If the derivation of a field fails, the process stops.

1. **Legal entity** – If an active mapping rule is found for the legal entity, the legal entity is derived based on the company name and company address.
2. **Vendor account** – Next, the vendor account is derived based on an active mapping rule and a combination of the derived legal entity and the vendor's name, vendor address or tax number
3. **Item number** – Finally, the item name is derived from staging, based on the following three types of information:

    - Derived legal entity
    - Derived vendor account
    - Item description or external item number

After the fields are derived, the following additional validation checks:

- **Mandatory check** – This check validates the mandatory fields for the side-by-side viewer. Users can select which fields must be mandatory on the **Configuration setting** page.
- **Confidence score** – Users can set the warning and error thresholds for the confidence score. This check focuses on the confidence score from OCR that is below those thresholds. Error or warning messages will be shown based on the validation result.
- **Existing check** – This check validates the existence of entities, including legal entity, vendor account, item number, procurement category, or purchase order.
- **Advanced check** – When a stock-item is used, the purchase order details have to be assigned to the invoice line.  


When clicking **Derive and check**, the derivation and validation processes are ran. If there are no errors in the invoices, it only calls the validation logic when clicking **Complete review** or **Transfer**. 

The derivation process occurs before the validation process, and all warnings or errors come from the validation process. The warnings and errors will be logged in the history log. Users can select **View history** to review the errors.  

>[!Note]
>The current derivation and validation includes the most common scenarios and more specific validations can be implemented by customer extension. 


### Continuous learning 
To increase the touchless rate of invoice processing in Invoice capture, **Continuous learning** is enabled to derive the entities based on the mapping from the last transferred invoice with manual intervention. **Continuous learning** is applied to derive the legal entity, vendor account and item numbers. 

### Void and delete 
If the invoice contains errors, invoices can be voided by clicking **Void**. The invoices can't be reviewed and included again. Instead, users can delete it by clicking **Delete**. Once it is deleted, the linked entry in the **Received file** will be deleted as well.  

### Transfer 
When a user completes the review and there's no error on the invoice, click **Transfer** to send the invoice to the connected Dynamics 365 Finance environment. 
 - If the invoice generation fails, an error message will be displayed.
 - If the pending invoice is successfully generated, the status of captured invoice will be **Complete**. 

>[!Note]
>After the invoice is successfully transferred, the original document is automatically imported from invoice capture to Dynamics 365 Finance. 




