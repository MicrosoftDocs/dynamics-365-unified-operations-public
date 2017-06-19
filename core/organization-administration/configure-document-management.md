---
# required metadata

title: Configure document management
description: [Configure document management (document handling) to store file attachments and notes for records]
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

This topic covers the concepts and features involved in configuring document management (document handling) to store file attachments and notes for records.

## Configure document types
Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location.

A set of document types is provided by default that can be used for categorizing attachments as file, image, note, or URL. The *File* and *Image* default document types are configured to use the **Location** of *Azure storage*.

To create a new document type:
1. Open **Organization administration > Setup > Document management > Document types**
2. Click **New**
3. Provide a short **Type** name e.g. *"SharePoint"* or *"HR Docs"*
4. Provide a longer **Name** e.g. *"SharePoint files"* or *"HR Docs"*
5. Provide a **Class** to define the document type behavior:
    1. **Attach file** - prompts the user for a file.
    2. **Attach URL** - enables the user to provide a URL in the **Notes** field e.g. *"http://www.microsoft.com"*. The **Open** button on the Attachments form will then open the URL in a browser tab.
    3. **Simple note** - allows the user to add a simple note using the **Notes** field.
6. If the **Class** was **Attach file** then provide a **Location** indicating what storage mechanism to use
7. If the **Location** was **SharePoint** then provide a **SharePoint Address** by clicking the edit button (pencil) and using the **Folder selection** dialog

## Configure SharePoint storage

SharePoint Online is one of the natively supported storage locations. At this time, only SharePoint Online is supported. SharePoint on-premises (local SharePoint server) support may be added in the future. 

To use SharePoint storage, on a document type set the *Location* field to *SharePoint* and supply a valid *SharePoint Address*

To configure SharePoint storage:
1. Open **Organization administration > Setup > Document management > Document management parameters**
2. On the SharePoint tab, review the *Default SharePoint server* field for the SharePoint site hostname that was automatically detected e.g. "contosoax7.sharepoint.com". The SharePoint hostname will usually be of the form "tenantname.sharepoint.com" where accounts on that tenant would look like user1@tenantname.onmicrosoft.com.
3. If no SharePoint server is populated by default, that likely means that either there is no SharePoint site for the tenant or the current user (the admin) does not have a valid Office 365 license associated with them.
4. If desired, click the *Test SharePoint connection* button to test the SharePoint hostname provided.
5. If desired, click the *Open SharePoint* button to open the SharePoint hostname in a browser.

### Troubleshooting SharePoint communication
SharePoint communication will only work for the current user if:
1. The user has an Office 365 license associated with their account
2. The user is a normal user on the tenant and is not an external user e.g. a user from another tenant
3. There is a SharePoint site for the tenant e.g. Contoso.SharePoint.com.

## Configure file types

You can control which types of files that users can attach to records by editing the list of allowable file extensions.

To specify file types, follow these steps:
1. Open **Organization administration > Setup > Document management > Document management parameters**
2. On the File types tab, review the default file types. 
3. Remove the file types that users should not be able to attach to records, and add any additional file types that users should be able to attach to records.

## Configure document preview
The attachments preview uses the Web Application Open Platform Interface (WOPI) provided by an Office Web Apps Server. **Document management parameters > General > Office Web Apps Server** sets the Office Online server to use for attachment previews. The default value for the **Office Web Apps Server** field is https://onenote.officeapps.live.com which points at the cloud WOPI server.

When an environment is on-premises, then the default cloud-based WOPI server cannot read the attachment file to provide a preview. If previews are needed on-premise, then an Office Online Server needs to be installed on-premise and configured inside the environment. Set the **Office Web Apps Server** field to the host name of the installed Office Online Server and click Save. If previews are not needed, then set the Office Web Apps Server field to https://localhost and the preview will indicate that there is “No preview available” rather presenting an error.

## Other configuration

There are a number of other configuration options that are seldom used:
- **Document management parameters > General > Use Document Tables** enables the use of the *Active document tables* whitelist. If turned on, this will disable attachments on all other tables, so only use this when necessary.
- **Document management parameters > General > Maximum file size in megabytes** sets the maximum file size for attachments. Note that the ability for users to provide files is also constrained by the file size limit set for the environment in configuration files that are not changable via a client form.
- **Settings > User options > Preferences > Enabling document handling** allows a user to disable document handling (document management) if desired.

## Frequently Asked Questions

### What is the difference between document handling and document management?

There is no difference. Both terms refer to the same functionality. Different terms were are used in different versions of the product.

### What is the difference between document management and print management?

Document management lets you add notes, documents, and other files to records.

Print management lets you control print settings for selected reports. Print settings include the number of copies, the printer destination, and the multilanguage text that can be included on the report. For more information, see Print management.

### What is the difference between document types and file types?

Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location. The table for document types is DocuType. 

File types include word documents, images, etc. A file type is denoted by the extension of the file. For example, .txt, .png, .doc, .xlsx, and .pdf are all file types.

### Does document management integrate with Office 365?

Yes. SharePoint storage is supported natively and can be selected as the storage location for a document type. In addition, any URL addressable file can be made an attachment via the URL document type.

