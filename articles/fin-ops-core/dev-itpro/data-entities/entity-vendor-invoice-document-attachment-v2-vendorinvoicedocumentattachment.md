---
title: Vendor invoice document attachment V2 entity
description: Definition of the Vendor invoice document attachment V2 data entity in finance and operations migration projects with Dynamics 365.
ms.date: 04/28/2023
ms.topic: article
author: edupont04
ms.author: katiehav
searchScope: dynamics-365-daf
ms.service: dynamics-365
ms.subservice: guidance
ms.collection: FastTrack
---

# Vendor invoice document attachment V2 entity

The **Vendor invoice document attachment V2** entity supports creating and updating documents attached to a vendor invoice header.

## When to use this entity

Use this entity to create or update vendor invoice header document attachments.

## Summary

|Type|Name|
|----|----|
| **Data management entity name** | Vendor invoice document attachment V2 |
| **OData public entity** | VendorInvoiceDocumentAttachment |
| **OData public collection** | VendorInvoiceDocumentAttachments |
| **Related menu items** | Accounts payable / Invoices / Pending vendor invoices</br>Accounts payable / Invoices / Open vendor invoicesAccounts payable / Vendors / Invoice |
| **Related entities** | Vendor invoice header |
| **Performance pattern** | Multiple threads supported – Recommendation is to set **Import threshold record count** to 1000 and set **Import task count** to 8. For more information, see [Parallel imports](/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job#parallel-imports). |
| **Application Object Tree (AOT) name** | VendorInvoiceDocumentAttachmentV2Entity |

## Fields

| Field | Description |
|--|--|
| Headerreference | Specifies the primary key, a foreign key to a **Vendor invoice header**. |
| TypeId | Specifies the first segment of a foreign key to the document type. |
| ACTUALCOMPANYID | Specifies the second segment of a foreign key to the document type. |
| Notes | The note of the attachment. |
| FileContents | The file contents as a base64 string. |

## Issues and considerations

The **Vendor invoice document attachment V2** entity supports creating and updating vendor invoice attachment at invoice header. Use it after you have created the releavant vendor invoice headers.

The basic configuration can be done from Organization administration / Document Management / Document management parameters / General tab / Maximum file size megabytes.  

> [!NOTE]
> When SharePoint is used as the document type, users can only upload a document up to a maximum file size of 262 megabytes.

## Related resources

[Import vendor invoices in Dynamics 365 projects](/dynamics365/guidance/resources/import-vendor-invoices)  
