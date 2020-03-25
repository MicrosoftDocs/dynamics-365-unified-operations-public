---
# required metadata

title: Configure document management
description: This topic explains how to configure document management (document handling) so that it stores file attachments and notes for records.
author: ChrisGarty
manager: AnnBe
ms.date: 12/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Configure document management

[!include [banner](../includes/banner.md)]


This topic explains how to configure document management (document handling) so that it stores file attachments and notes for records. It includes information about the concepts and features that are involved in this functionality.

To learn more about document management, watch the short [Document Management](https://www.youtube.com/watch?v=p4rl1CkiLN4&feature=youtu.be) video.

## Configure document types

Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location.

A default set of document types is provided. You can use these document types to categorize an attachment as a file, image, note, or URL. The **File** and **Image** default document types are configured to use **Azure storage** as the location.

To create a new document type, follow these steps.

1. Go to the **Document types** page.
2. Click **New**.
3. In the **Type** field, enter a short name for the new document type, such as **SharePoint** or **HR Docs**.
4. In the **Name** field, enter a longer name, such as **SharePoint files** or **HR Docs**.
5. In the **Class** field, specify a class to define the behavior for the document type:

    - **Attach file** – The user is prompted for a file.
    - **Attach URL** – The user can enter a URL in the **Notes** field, such as `https://www.microsoft.com`. The **Open** button on the **Attachments** page will open the URL on a browser tab.
    - **Simple note** – The user can add a simple note in the **Notes** field.

6. If you specified **Attach file** in the **Class** field, in the **Location** field, specify the storage mechanism to use.
7. If you specified **SharePoint** in the **Location** field, specify the Microsoft SharePoint address in the **SharePoint Address** field. To do this, click the **Edit** button (pencil symbol) and use the **Folder selection** dialog box.

## Configure SharePoint storage

Microsoft SharePoint Online is one of the storage locations that are supported natively. Currently, only SharePoint Online is supported. Support for on-premises SharePoint (a local SharePoint server) may be added in the future.

To use SharePoint storage, set the **Location** field for a document type to **SharePoint**. Then, in the **SharePoint Address** field, enter a valid SharePoint address.

To configure SharePoint storage, follow these steps.

1. Go to the **Document management parameters** page.
2. On the **SharePoint** tab, in the **Default SharePoint server** field, review the host name that was automatically detected for the SharePoint site, such as contosoax7.sharepoint.com. Typically, the SharePoint host name is in the form tenantname.sharepoint.com, and accounts on that tenant are in the form `user1@tenantname.onmicrosoft.com`.

    Typically, if no default SharePoint server is specified, either there is no SharePoint site for the tenant, or a valid Microsoft Office 365 license isn't associated with the current user (the admin).

4. Optional: Click **Test SharePoint connection** to test the specified SharePoint host name. This verifies that the security and license are working correctly. 
5. Optional: Click **Open SharePoint** to open the specified SharePoint host name in a browser. Note that this does not verify security, it just opens the SharePoint path in a browser tab for easy exploration.

### Troubleshooting SharePoint communication

SharePoint communication works for the current user only if the following conditions are met:

- An Office 365 license is associated with the user's account.
- The user is a typical user on the tenant, not an external user (for example, a user from another tenant).
- There is a SharePoint site for the tenant (for example, Contoso.SharePoint.com).

If documents stored in SharePoint don't display in preview, follow these steps to troubleshoot the issue: 

1. Verify the Admin account has an associated email account (verify or change this in the **User** page). If this isn't set up, you need to add the email and provider  via the OData Excel add-in. By default, the email address isn't present in the Excel design. The user needs to edit the Excel design, add all fields, apply and refresh. Once complete, you can update the Admin account.

2. After the Admin account has an associated email account, sign in to Dynamics 365 Human Resources as the admin.

3. Open an attachment that is stored in SharePoint to initiate the preview.

4. Sign in with any other user account that has access to attachments and verify that preview works.

## Configure file types

By modifying the list of file extensions that are allowed, you can control the types of files that users can attach to records.

To specify file types, follow these steps.

1. Go to the **Document management parameters** page.
2. On the **File types** tab, review the default file types.
3. Remove any file types that users should not be able to attach to records, and add any file types that users should be able to attach to records.

## Configure document preview

The attachments preview uses the Web app Open Platform Interface (WOPI) that is provided by Microsoft Office Online Server. On the **Document management parameters** page, on the **General** tab, in the **Office Web Apps Server** field, specify the Office Online Server instance to use for attachment previews. The default value is `https://onenote.officeapps.live.com`. This value points to the cloud-based WOPI server.

### For a Microsoft Dynamics 365 Finance + Operations (on-premises) environment

The default cloud-based WOPI server in Finance + Operations can't read the attachment file to provide a preview. If previews are required, you must [install an on-premises Office Online Server instance](https://technet.microsoft.com/library/jj219455.aspx) and configure it inside the environment. Set the **Office Web Apps Server** field to the host name of the installed Office Online Server instance, and then click **Save**.

If previews aren't required, set the **Office Web Apps Server** field to `https://localhost`. The preview will then show the message "No preview available" instead of an error message.

### Document preview (WOPI) will not work in environments with IP whitelisting enabled

Document preview (WOPI) will not work in environments with IP whitelisting enabled, because the WOPI service that provides the preview will not be able to connect back to the file service to retrieve the file for rendering.

## Other configuration

Here are some other configuration options to consider, although these options are rarely used:

- On the **Document management parameters** page, on the **General** tab, you can use the **Use Document Tables** option to enable the **Active document tables** allow list. If you set this option to **Yes**, you disable attachments on all other tables. Therefore, turn on this option only when it's required.
- On the **Document management parameters** page, on the **General** tab, you can use the **Maximum file size in megabytes** field to set the maximum file size for attachments. Note that the ability of users to provide files is also constrained by the file size limit that is set for the environment in configuration files. These configuration files can't be changed via a client page.
- On the **Options** page (**Settings** \> **User options**), on the **Preferences** tab, you can use the **Enable document handling** option to disable document handling (document management).

## Accessing document management attachments 

Document management appears to users as the **Attach** button (keyboard shortcut: **Ctrl**+**Shift**+**A**) at the top of most forms that contain data sources. Clicking the **Attach** button will open the **Attachments** form in the context of the data source of the currently selected control on the form.

The **Attach** button will also show a count of attachments for the currently selected record, so the user can see whether there are attachments on the current record without opening that form. The count will show 0-9, and then 9+ to limit the performance impact and visual noise of determining and showing larger counts.

## Attachment recovery

In Platform update 29, an attachment recovery feature has been added that provides a recycle bin for record attachments to be recovered within a configured period of time.

### Configuration of attachment recovery

Attachment recovery can be enabled by going to **Document management parameters** > **General** >  **Deferred deletion** > **Deferred deletion enabled**. The default for **Number of days to defer deletion** is 30 days, but can be changed as needed. If the **Number of days to defer deletion** value is zero this means that the deleted attachments will be recoverable for an indefinite period. 

After attachment recovery is enabled, a batch job with this name will be created, "Scans for deleted references which have reached the end of their retention period". This batch job will use the **Number of days to defer deletion** to determine how long to retain a deleted attachment based on the **Deleted data and time**.

### Deleting attachments when attachment recovery is active

When a user deletes an attachment, a notification will be added to the Message Center to provide confirmation of the deletion and an option to undo to the action if the deletion was unintended.

Table extension support has been built-in, so that any extension or custom field values on the **DocuRef** or **DocuValue** tables will be retained to enable their recovery. 

### Recovering attachments

When attachment recovery is enabled, attachments can be recovered in one of three ways:
1. Immediately after deletion, the user can use the undo link in the **Attachment deleted** notification.
2. On the **Attachments** page, a **Deleted attachments** button provides access to the list of deleted attachments that can be recovered for a particular record. The deleted attachments can be opened for review, permanently deleted, or restored.
3. In **System administration** > **Inquiries**, the **Deleted attachments** page provides access to the list of deleted attachments that can be recovered for any record. The deleted attachments can be opened for review, permanently deleted, or restored.

## Frequently asked questions

### What is the difference between document handling and document management?

There is no difference between document handling and document management. Both terms refer to the same functionality. Different terms are used in different versions of the product.

### What is the difference between document management and print management?

Document management lets you add notes, documents, and other files to records.

Print management lets you control print settings for selected reports. Print settings include the number of copies, the printer destination, and the multilanguage text that can be included on the report. For more information, see [Document Reporting Services](../../dev-itpro/analytics/document-reporting-services.md).

### What is the difference between document types and file types?

Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location. The table for document types is named DocuType.

File types include Microsoft Word documents and images. A file type is denoted by the extension of the file, such as .txt, .png, .doc, .xlsx, or .pdf.

### Does document management integrate with Office 365?

Yes. SharePoint storage is supported natively and can be selected as the storage location for a document type. In addition, any URL addressable file can be made an attachment via the **URL** document type.

### How does the default storage location for Document Management change in Finance + Operations environments?

For Finance + Operations, the Azure Blob storage provider for attachments is replaced by a file folder storage provider so that attachments are kept on-premise instead of being stored in the cloud. Therefore, the default storage location for attachments is a file folder.

### If I accidentally delete an attachment stored in Azure Blob storage, can it be restored?

If an attachment stored in Azure Blob storage is accidentally deleted, it cannot be restored or recovered because it has been permanently deleted and the reference to it has also been deleted.

### Is the database information about attachments stored separately from the attachments themselves?

Record attachment information is stored in the DocuRef and DocuView tables. The DocuRef table is the record that represents the attachment. The DocuRef record points to the record being attached to and to a DocuView record. The DocuView record points to the file that is the attachment. Files are stored outside the database, therefore any database operations, like restoring from backup, will only affect the database information about the attachment, not the attachment file itself.

### Can attachments be stored in the database?

No. By default, attachments are stored in Azure Blob storage.

### What are the main differences between Azure Blob storage and database storage?

Database storage is Azure SQL Database. File storage is Azure Blob storage. Azure Blob storage is simpler and much less expensive.

### How much storage do we get for Azure Blob storage?

That information is in the [licensing guide](https://mbs.microsoft.com/Files/public/365/Dynamics365LicensingGuide.pdf). Currently, you get 40 gigabytes (GB) of storage.

### What is the cost for additional storage?

The cost for additional storage varies, but it's similar to the [standard Azure costs for storage](https://azure.microsoft.com/pricing/details/storage/page-blobs/). In other words, the cost is about $0.05 per GB.

### How can we learn how much storage we've already used?

There will be proactive communications when you're approaching your database and file storage limits. However, Microsoft Dynamics Lifecycle Services (LCS) provides some information, and you can log support requests for additional information. 

### Is there an option to export all document attachments from the system?

Although attachments can be exported, that capability isn't a standard capability, because there isn't a standard attachment entity. Entities that provide attachments for a specific business document or record must be built.

### How can attachments be extracted from the system?

To extract attachments, an Attachments entity must be built for a specific business document or record. There isn't a standard attachment entity because the identity for each record type is different. To learn how to build an Attachments entity, you can find examples in the Application explorer by searching for "Attachment" under the **AOT > Data Model > Data Entities** node.

