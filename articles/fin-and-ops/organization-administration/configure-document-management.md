---
# required metadata

title: Configure document management
description: This topic explains how to configure document management (document handling) so that it stores file attachments and notes for records.
author: ChrisGarty
manager: AnnBe
ms.date: 08/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, UnifiedOperations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Configure document management

[!include[banner](../includes/banner.md)]

This topic explains how to configure document management (document handling) so that it stores file attachments and notes for records. It includes information about the concepts and features that are involved in this functionality.

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
    - **Attach URL** – The user can enter a URL in the **Notes** field, such as `http://www.microsoft.com`. The **Open** button on the **Attachments** page will open the URL on a browser tab.
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

4. Optional: Click **Test SharePoint connection** to test the specified SharePoint host name.
5. Optional: Click **Open SharePoint** to open the specified SharePoint host name in a browser.

### Troubleshooting SharePoint communication
SharePoint communication works for the current user only if the following conditions are met:

- An Office 365 license is associated with the user's account.
- The user is a typical user on the tenant, not an external user (for example, a user from another tenant).
- There is a SharePoint site for the tenant (for example, Contoso.SharePoint.com).

## Configure file types

By modifying the list of file extensions that are allowed, you can control the types of files that users can attach to records.

To specify file types, follow these steps.

1. Go to the **Document management parameters** page.
2. On the **File types** tab, review the default file types. 
3. Remove any file types that users should not be able to attach to records, and add any file types that users should be able to attach to records.

## Configure document preview
The attachments preview uses the Web app Open Platform Interface (WOPI) that is provided by Microsoft Office Online Server. On the **Document management parameters** page, on the **General** tab, in the **Office Web Apps Server** field, specify the Office Online Server instance to use for attachment previews. The default value is https://onenote.officeapps.live.com. This value points to the cloud-based WOPI server.

### For an on-premises environment
When an environment is on-premises, the default cloud-based WOPI server can't read the attachment file to provide a preview. If previews are required, you must [install an on-premises Office Online Server instance](https://technet.microsoft.com/en-us/library/jj219455.aspx) and configure it inside the environment. Set the **Office Web Apps Server** field to the host name of the installed Office Online Server instance, and then click **Save**.

If previews aren't required, set the **Office Web Apps Server** field to `https://localhost`. The preview will then show the message “No preview available” instead of an error message.

## Other configuration

Here are some other configuration options to consider, although these options are rarely used:

- On the **Document management parameters** page, on the **General** tab, you can use the **Use Document Tables** option to enable the **Active document tables** allow list. If you set this option to **Yes**, you disable attachments on all other tables. Therefore, turn on this option only when it's required.
- On the **Document management parameters** page, on the **General** tab, you can use the **Maximum file size in megabytes** field to set the maximum file size for attachments. Note that the ability of users to provide files is also constrained by the file size limit that is set for the environment in configuration files. These configuration files can't be changed via a client page.
- On the **Options** page (**Settings** > **User options**), on the **Preferences** tab, you can use the **Enable document handling** option to disable document handling (document management).

## Accessing document management attachments 

Document management appears to users as the **Attach** button (keyboard shortcut: **Ctrl**+**Shift**+**A**) at the top of most forms that contain data sources. Clicking the **Attach** button will open the **Attachments** form in the context of the data source of the currently selected control on the form. 
The **Attach** button will also show a count of attachments for the currently selected record, so the user can see whether there are attachments on the current record without opening that form. The count will show 0-9, and then 9+ to limit the performance impact and visual noise of determining and showing larger counts.

## Frequently asked questions

### What is the difference between document handling and document management?

There is no difference between document handling and document management. Both terms refer to the same functionality. Different terms are used in different versions of the product.

### What is the difference between document management and print management?

Document management lets you add notes, documents, and other files to records.

Print management lets you control print settings for selected reports. Print settings include the number of copies, the printer destination, and the multilanguage text that can be included on the report. For more information, see [Document Reporting Services overview](../../dev-itpro/analytics/document-reporting-services.md).

### What is the difference between document types and file types?

Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location. The table for document types is named DocuType. 

File types include Microsoft Word documents and images. A file type is denoted by the extension of the file, such as .txt, .png, .doc, .xlsx, or .pdf.

### Does document management integrate with Office 365?

Yes. SharePoint storage is supported natively and can be selected as the storage location for a document type. In addition, any URL addressable file can be made an attachment via the **URL** document type.
