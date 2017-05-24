---
# required metadata

title: Configure document management
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: ChrisGarty
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Enterprise edition, July 2017 update 
---

# Configure document management

[!include[banner](../includes/banner.md)]


## What is the difference between document handling and document management?

There is no difference. Both terms refer to the same functionality. Different terms were are used in different versions of the product.

## What is the difference between document management and print management?

Document management lets you add notes, documents, and other files to records.

Print management lets you control print settings for selected reports. Print settings include the number of copies, the printer destination, and the multilanguage text that can be included on the report. For more information, see Print management.

## What is the difference between document types and file types?

Document types are used to categorize the documents that you attach to records or the templates that you create. The document management system handles several types of documents. These include letters, worksheets, and notes. Before you can create templates or attach documents to records, you must configure document types in the Document types form. For more information, see Configure document management.

A file type is the extension of the document. For example, .doc, .xlsx, and .pdf are all file types.

## Can I export or import document types?

Yes. For more information, see Export and import a document type.

## Does document management integrate with Office 365?

Yes. Document attachments can be located anywhere on the Internet or on an intranet and can be attached by using the URL DocuType. For example, if you attach a Word document that is located on SharePoint Online to a record, the attachment opens in the web version of Word

## Can I store Dynamics 365 for Operations attachments in SharePoint?

Yes, but only if you’re using Microsoft Dynamics AX 2012 R2 or later. For more information, see Configure and use Microsoft Dynamics AX document management with Microsoft SharePoint document libraries.

## Can I use templates that are stored in SharePoint as Microsoft Dynamics 365 for Operations document templates?

Yes, but only if you’re using AX 2012 R2 or later. For more information, see Configure and use Microsoft Dynamics AX document management with Microsoft SharePoint document libraries.

## Can I move a document archive?

Yes. However, you must copy the documents from the old archive to the new archive before you enter the new location in the archive directory field. This precaution is necessary so that you don’t break existing document references to existing documents.

To move a document archive, follow these steps:

1.  Copy all documents from the old archive to the new archive.

2.  Click Organization administration \> Setup \> Document management \> Document management parameters.

3.  In the General area of the form, in the Archive directory field, enter the path of the new document archive.
 
## Why can’t I click the attachments icon in the Document handling form?

The attachments icon is available only if all of the following scenarios are true:

-   You have selected a record.
-   You have activated document management. For more information, see Configure document management.
-   You have permission to view attachments for the record.

## How do I lock the Document handling form?

The **Document handling** form always lists the documents that are attached to the selected record. If you leave the **Document handling** form open and you select another record, the form is updated to list the documents that are attached to the newly opened record.

To avoid updating the **Document handling** form when you select a different record, you can lock the view so that the information in the form doesn’t change.

To lock the **Document handling** form view, follow these steps:

1.  Select a record.

2.  Click **File** \> **Command** \> **Document handling** to open the **Document handling** form.

3.  Click Functions \> Lock.

4.  Select another record. The documents for the locked record are still displayed in the Document handling form.
