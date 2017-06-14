---
# required metadata

title: Vendor invoice automation
description: This topic explains the features that are available for end-to-end automation of vendor invoices, even invoices that include attachments.
author: twheeloc
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: AX 7.0.0
---
# Vendor invoice automation

This topic explains the features that are available for end-to-end automation of vendor invoices, even invoices that include attachments.

Organizations that want to streamline their Accounts payable (AP) processes often identify invoice processing as one of the top process areas that should be more efficient. In many cases, these organizations offload the processing of paper invoices to a third-party optical character recognition (OCR) service provider. They then receive machine-readable invoice metadata together with a scanned image of each invoice. To help with automation, a “last mile” solution is then built to enable consumption of these artifacts in the invoicing system. Microsoft Dynamics 365 for Finance and Operations, Enterprise edition now enables this “last mile” automation out of the box, through an invoice automation solution.

## Solution context

The invoice automation solution enables a standard interface that can accept invoice metadata for the invoice header and invoice lines, and also attachments that are applicable to the invoice. Any external system that can generate artifacts that comply with this interface will be able to send the feed into Finance and Operations for automatic processing of invoices and attachments.

The following illustration shows a sample integration scenario where Contoso has partnered with an OCR service provider for vendor invoice processing. Contoso’s vendors send invoices to the service provider by email. Through OCR processing, the service provider generates invoice metadata (header and/or lines) and a scanned image of the invoice. An integration layer then transforms these artifacts so that Finance and Operations can consume them.

![Sample integration scenario](media/vendor_invoice_automation_01.png)

Several variations of the preceding scenario are possible if invoice integration is required. Data migration is another use case where this interface can be used to create invoices and attachments in Finance and Operations.

### Solution components

The solution footprint consists of the following components:

+ Data entities for the invoice header, invoice lines, and invoice attachments
+ Exception processing for invoices
+ A side-by-side attachment viewer in invoices

The rest of this topic provides detailed descriptions of these solution components.

## Data entities

A data package is the unit of work that must be sent to Finance and Operations, so that invoice headers, invoice lines, and invoice attachments can be created. The following data entities are used for the artifacts that make up the data package:

+ Vendor invoice header
+ Vendor invoice line
+ Vendor invoice document attachment

Vendor invoice document attachment is a new data entity that is introduced as part of this feature. The Vendor invoice header entity has been modified so that it supports attachments. The Vendor invoice line entity hasn’t been modified for this feature.

This topic doesn’t give a detailed definition of a data package. It also doesn’t explain how to create data packages. For this information, see [Data entities and packages framework](../unified-operations/dev-itpro/data-entities/data-entities-data-packages).

To quickly generate test data that includes invoices and attachments, follow these steps.

1. Sign in to your Finance and Operations instance.
1. Go to **Accounts payables** > **Invoices** > **Pending vendor invoices**.
1. Create invoices that have lines and attachments.

    > [!NOTE]
    > The attachments must be header attachments. Currently, the Vendor invoice document attachment entity doesn’t support line attachments.

1. Open the **Data management** workspace.
1. Create an export job that includes the Vendor invoice header, Vendor invoice line, and Vendor invoice document attachment entities.
1. Export the data.
1. Download the exported data as a package. You can now use the package to import data into target instances for testing purposes.

### Determining the legal entity for an invoice

Invoices that are imported via data packages can be associated with the legal entity that they belong to in two ways:

+ The import job that processes the invoice imports it into the same company in which the job was scheduled in the **Data management** workspace. In other words, the company of the job determines the company that the invoice belongs to.
+ When the data package that contains invoices is sent to Finance and Operations, the caller (that is, the integration application that runs outside of Finance and Operations) can explicitly mention the company ID in the HTTP request. In this case, the company context in which the processing job runs in Finance and Operations is overridden, and the invoices are imported into the company that was passed via the HTTP request.

> [!NOTE]
> This behavior is standard data management behavior. It’s explained here, in the context of invoices, just for the sake of completeness.

## Exception processing

In scenarios where vendor invoices come into Finance and Operations via integration, there must be an easy way for an Accounts payable team member to process exceptions or failed invoices, and to create pending invoices out of failed invoices. This exception processing for vendor invoices is now part of Finance and Operations.

### Exceptions list page

The new list page for invoice exceptions is available at **Accounts payable** > **Invoices** > **Import failures** > **Vendor invoices that failed to import**. This page shows all the vendor invoice header records from the staging table of the Vendor invoice header data entity. Note that you can view the same records from the **Data management** workspace, where you can also perform the same actions that are provided in the exception handling feature. However, the UI that the exception handling feature provides is optimized for a functional user.

![Exceptions list page](media/vendor_invoice_automation_02.png)

This list page includes the following fields that come in via the feed:

+ **Company** – The company that the invoice belongs to
+ **Error message** – The error message that the data management framework issues to explain why the invoice could not be created
+ **Number** – The invoice number
+ **Invoice account**
+ **Name** – The vendor’s name
+ **Vendor account**
+ **Purchase order** – The purchase order (PO) number for the invoice
+ **Posting date**
+ **Invoice date**
+ **Invoice description**
+ **Currency**
+ **Log**
+ **Line reference** – The identifier that comes from the external system

    > [!NOTE]
    > The line reference isn’t the invoice ID.

This list page also has a preview pane that you can used in the following ways:

+ View the whole error message, so that you don’t have to expand the **Error message** column in the grid.
+ View the whole list of attachments for the invoice, if any attachments came with the invoice.

The list page supports the following actions:

+ **Edit** – Open the exception record in edit mode, so that you can fix the issues.
+ **Options** – Access the standard options that are available on list pages. You can use the **Add to workspace** option to pin the exceptions list page to your workspace as a list or tile.

### Exception details page

When you start edit mode, the exception details page for the invoice that has issues appears. If there are any attachments, the invoice and the default attachment appear side by side on the exception details page.

![Exception details page](media/vendor_invoice_automation_03.png)

In the preceding illustration, there weren’t any lines for the vendor invoice header that came in. Therefore, the lines section is empty.

The exception details page supports the following operation:

+ **Create pending invoice** – After you’ve fixed the issues on the invoice as part of exception processing, you can click this button to create the pending invoice. The creation of pending invoices occurs in the background (as an asynchronous operation).

### Shared service vs. organization-based exception processing

The exceptions list page supports the standard security constructs that the **Data management** workspace supports for the processing of staging records. The invoice import job can be secured in the following ways:

+ By user role
+ By user
+ By legal entity

![Import job that is secured by user role and legal entity](media/vendor_invoice_automation_04.png)

If security is configured for the invoice import job, the exceptions list page honors those settings. Users will be able to see only the invoice exception records that this setup allows them to see.

For example, Contoso has decided to process invoice exceptions by legal entity. Therefore, security is configured on the invoice import job in such a way that a user in legal entity A can see only invoice exceptions in legal entity A, whereas a user in legal entity B can see only invoice exceptions in legal entity B. This setup enables segregation of duties for the management of invoice exceptions.

Contoso could also decide not to enforce any security, so that the same users can process invoice exceptions for all legal entities. This setup enables a shared services scenario for the management of invoice exceptions.

## Side-by-side attachment viewer

To help you easily view the attachments for vendor invoices, the following pages that are used in the invoicing process now provide an attachment viewer:

+ **Exception handling**
+ **Pending vendor invoices** page (also available in the invoice review process)
+ **Invoice journal** inquiry page (for posted invoices)

Here is the main functionality that the attachment viewer provides:

+ View all attachment types that Document management supports (files, images, URLs, and notes).
+ View multi-page TIFF files.
+ Perform the following actions on image files:
  + Highlight parts of the image.
  + Block parts of the image.
  + Add annotations to the image.
  + Zoom in and out on the image.
  + Pan the image.
  + Undo and redo actions.
  + Fit the image to size.

> [!NOTE]
> These actions are available only for image files (JPEG, TIFF, PNG, and so on). Any changes that you make to an image by using these actions are saved to the image file. Currently, the attachment viewer doesn’t include versioning or auditing capabilities.

### Default attachment

If a vendor invoice has more than one attachment, you can set one of the documents as the default attachment on the **Attachments** page. The **Is default attachment** option is a new option that was added as part of this feature. This option is also exposed in the Vendor invoice document attachment data entity. Therefore, the default attachment can be set through integrations.

Only one document can be set as the default attachment. After you set a document as the default attachment, it’s automatically shown in the attachment viewer when the invoice is opened. If you don’t set any document as the default attachment, the viewer doesn’t automatically show any attachment when the invoice is opened.

### Show/hide invoice attachments

A new button that is available on the **Exception processing**, **Pending invoice**, and **Invoice journal** inquiry pages lets you show or hide the attachment viewer.

### Security

The following actions in the attachment viewer are controlled via role-based security:

+ Highlighting
+ Block
+ Annotation

### Pending vendor invoices page

The following privileges provide ready-only access or read/write access to the attachment viewer for the highlighting, block, and annotation actions:

+ **Maintain vendor invoice image** – This privilege provides read/write access.
+ **View vendor invoice image** – This privilege provides read-only access.

The following duties provide read-only access or read/write access to the attachment viewer for those actions:

+ **Maintain vendor invoices** – The Maintain vendor invoice image privilege is assigned to this duty.
+ **Inquire into vendor invoice status** – The View vendor invoice image privilege is assigned to this duty.

The following roles provide read-only access or read/write access to the attachment viewer for those actions:

+ **Accounts payable clerk** and **Accounts payable manager** – The Maintain vendor invoices duty is assigned to these roles.
+ **Accounts payable clerk**, **Accounts payable manager**, **Accounts payable centralized payments clerk**, and **Accounts payable payments clerk** – The Inquire into vendor invoice status duty is assigned to these roles.

### Invoice exception details page

The following privileges provide ready-only access or read/write access to the attachment viewer for the highlighting, block, and annotation actions.

> [!NOTE]
> Out of the box, the roles that are mentioned in this section provide read-only access to the invoice images in the attachment viewer. If a role must also have write access to the images, you can grant write access to that role by using the privilege and duty that are described here.

+ **Maintain vendor invoice header entity image** – This privilege provides read/write access to the invoice images in the attachment viewer.
+ **View vendor invoice header entity image** – This privilege provides read-only view to the invoice image in the attachment viewer.

The following duties provide read-only access to the attachment viewer for those actions:

+ **Maintain vendor invoices** – The Maintain vendor invoice header entity image privilege is assigned to this duty.

The following roles provide read-only access to the attachment viewer for those actions:

+ **Accounts payable clerk** and **Accounts payable manager** – The Maintain vendor invoices duty is assigned to these roles.

By default, if the user role provides edit rights on any page, the user will also have edit rights on the attachments viewer for the highlighting, block, and annotation actions. However, if there are scenarios where a specific role should have edit rights on the page but not on the attachment viewer, the appropriate privileges from the preceding list can be used to satisfy the use case.
