---
# required metadata

title: Configure document management
description: This article explains how to configure document management (document handling) so that it stores file attachments and notes for records.
author: jasongre
ms.date: 03/14/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: July 2017 update 
---

# Configure document management

[!include [banner](../../../finance/includes/banner.md)]

This article explains how to configure document management (document handling) so that it stores file attachments and notes for records. It includes information about the concepts and features that are involved in this functionality.

To learn more about document management, watch the short [Document Management](https://www.youtube.com/watch?v=p4rl1CkiLN4&feature=youtu.be) video.

## Configure document types

Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location.

A default set of document types is provided. You can use these document types to categorize an attachment as a file, image, note, or URL. The **File** and **Image** default document types are configured to use **Azure storage** as the location.

To create a new document type, follow these steps.

1. Go to the **Document types** page.
2. Select **New**.
3. In the **Type** field, enter a short name for the new document type, such as **SharePoint** or **HR Docs**.
4. In the **Name** field, enter a longer name, such as **SharePoint files** or **HR Docs**.
5. In the **Class** field, specify a class to define the behavior for the document type:

    - **Attach file** – The user is prompted for a file.
    - **Attach URL** – The user can enter a URL in the **Notes** field, such as `https://www.microsoft.com`. The **Open** button on the **Attachments** page opens the URL on a browser tab.
    - **Simple note** – The user can add a note in the **Notes** field.

6. If you specified **Attach file** in the **Class** field, in the **Location** field, specify the storage mechanism to use.
7. If you specified **SharePoint** in the **Location** field, specify the Microsoft SharePoint address in the **SharePoint Address** field by selecting **Edit** (pencil symbol) and using the **Folder selection** dialog.

## Configure SharePoint storage

Microsoft SharePoint Online is one of the storage locations that is supported natively. On-premises SharePoint (a local SharePoint server) isn't currently supported. 

> [!IMPORTANT]
> -  SharePoint storage is only available in Microsoft-managed environments.
> -  SharePoint managed device policies are incompatible with an integration to finance and operations apps

To use SharePoint storage, set the **Location** field for a document type to **SharePoint**. Then, in the **SharePoint Address** field, enter a valid SharePoint address.

To configure SharePoint storage, follow these steps.

1. Go to the **Document management parameters** page.
2. On the **SharePoint** tab, in the **Default SharePoint server** field, review the host name that was automatically detected for the SharePoint site, such as contosoax7.sharepoint.com. Typically, the SharePoint host name is in the form tenantname.sharepoint.com, and accounts on that tenant are in the form `user1@tenantname.onmicrosoft.com`.

    Typically, if no default SharePoint server is specified, either there's no SharePoint site for the tenant, or a valid Microsoft 365 license isn't associated with the current user (the admin).

4. Optional: Select **Test SharePoint connection** to test the specified SharePoint host name, which verifies that the security and license are working correctly. 
5. Optional: Select **Open SharePoint** to open the specified SharePoint host name in a browser. This action doesn't verify security, it just opens the SharePoint path in a browser tab for easy exploration.
6. Optional: On the **General** tab, turn on **Open attachments in new window**. For more information, see the [Other configuration](#other-configuration) section later in this article. 

### Troubleshooting SharePoint communication

SharePoint communication works for the current user only if the following conditions are met:

- A Microsoft 365 license is associated with the user's account.
- The user is a typical user on the tenant, not an external user (for example, a user from another tenant).
- There's a SharePoint site for the tenant (for example, Contoso.SharePoint.com).
- The SharePoint site is configured to **Allow this site to appear in search results**.
- The SharePoint site doesn't use managed device policies. 
    -  If managed device policies are enabled on the SharePoint instance, the finance and operations SharePoint integration no longer works, and users aren't able to download, view, or create documents that are stored in SharePoint from finance and operations. 
- The user has access to the folder that the document is stored in.

If documents that are stored in SharePoint don't open or don't display in preview, follow these steps to troubleshoot the issue: 

1. Verify the Admin account has an associated email account. You can verify or change associated email account on the **User** page. If an associated email account isn't set up, you need to add the email and provider via the OData Excel add-in. By default, the email address isn't present in the Excel design. The user needs to edit the Excel design, add all fields, apply, and refresh. Once complete, you can update the Admin account.

2. After the Admin account has an associated email account, sign in to Dynamics as the admin.

3. Open an attachment that is stored in SharePoint.

4. Sign in with another user account with read access to the attachments page and the configured SharePoint folder. Verify that they can also open and preview the attachment.

## Configure file types

By modifying the list of file extensions that are allowed, you can control the types of files that users can attach to records.

To specify file types, follow these steps.

1. Go to the **Document management parameters** page.
2. On the **File types** tab, review the default file types.
3. Remove any file types that users shouldn't be able to attach to records, and add any file types that users should be able to attach to records.

## Configure document preview

The attachments preview uses the Web app Open Platform Interface (WOPI) that is provided by Microsoft Office Online Server. On the **Document management parameters** page, on the **General** tab, in the **Office Web Apps Server** field, specify the Office Online Server instance to use for attachment previews. The default value is `https://onenote.officeapps.live.com`, which points to the cloud-based WOPI server. 

> [!NOTE]
> For the following situations, you will need to adjust the **Office Web Apps Server** field as specified. 
> -  For environments in China, use https://onenote.partner.officewebapps.cn. 
> -  For environments in the Government Commmunity Cloud (GCC), use https://gb4-onenote.officeapps.live.com.

### For a Microsoft Dynamics 365 Finance + Operations (on-premises) environment

The default cloud-based WOPI server in Finance + Operations can't read the attachment file to provide a preview. If previews are required, you must [install an on-premises Office Online Server instance](/officeonlineserver/deploy-office-online-server) and configure it inside the environment. Set the **Office Web Apps Server** field to the host name of the installed Office Online Server instance, and then select **Save**.

If previews aren't required, set the **Office Web Apps Server** field to `https://localhost`. The preview then shows the message "No preview available" instead of an error message.

### Document preview (WOPI) doesn't work in environments with an IP safe list enabled

Document preview (WOPI) doesn't work in environments with an IP safe list enabled, because the WOPI service that provides the preview aren't able to connect back to the file service to retrieve the file for rendering.

## Other configuration

Here are some other configuration options to consider:

- On the **Document management parameters** page, on the **General** tab, you can use the **Use active document tables** option to enable the **Active document tables** allow list. If you set this option to **Yes**, you disable attachments on all other tables. Only turn on this option when required.
- On the **Document management parameters** page, on the **General** tab, you can use the **Maximum file size in megabytes** field to set the maximum file size for attachments. When SharePoint is used as a document type, users can only upload a document up to a maximum file size of 262 megabytes. 
- On the **Document management parameters** page, on the **General** tab, you can use the **Open attachments in new window** option to determine if attachments are opened in place or in a new window or tab. You should consider turning on this option especially if you're using SharePoint for storing attachments, because this option prevents the finance and operations user session from resetting when opening attachments. This option is available starting in version 10.0.23. 
- On the **Options** page (**Settings** \> **User options**), on the **Preferences** tab, you can use the **Enable document handling** option to disable document handling (document management).

## Accessing document management attachments 

Document management appears to users as the **Attach** button at the top of most pages that contain data. When you select the **Attach** button (or when you use the corresponding keyboard shortcut, **Ctrl**+**Shift**+**A**), the **Attachments** page is opened in the context of the data source of the control that is currently selected on the page. This page shows all the attachments that are related to the corresponding data source. 

The **Attach** button also shows a count of the attachments for the currently selected record. Therefore, you can determine whether there are attachments for the current record without having to open the **Attachments** page. The button shows exact counts for zero through nine attachments. If there are more than nine attachments, the button shows **9+** as the count. In this way, the performance impact and visual noise that exact larger counts might cause are reduced.

## Document attachment history

Starting in version 10.0.16/Platform update 40, a history mechanism is available for record attachments, which allows your organization to maintain an audit of actions related to individual attachments. You can see when an attachment was created, marked for pending deletion, restored, deleted, or moved, and who performed that action. Attachment history isn't maintained until 10.0.16/Platform update 40, so any actions on attachments before that version aren't available.  

### Configuration of document attachment history
Document attachment history can be enabled (or disabled) by going to **Document management parameters** > **General** > **History** > **Enable document history**. The default history retention period is 180 days, but this value can be modified as needed using the **Number of days to retain history** field. 

### Viewing an attachment's history
There are two entry points for viewing the history of a record attachment:

- When you're looking at the attachments for a specific record (see the [Accessing document management attachments](#accessing-document-management-attachments) section for more details), you can view the history for the current set of attachments on the **Attachments** page by selecting the **Document history** button in the Action pane.   
- Administrators can select the **Document history** button in the **History** section of the **Document management parameters** page. This action opens the **Document history** page, which shows a list of all attachments in the system. You can then drill into any record to see the detailed history for the selected attachment.  

## Attachment recovery

In Platform update 29, an attachment recovery feature was added that provides a recycle bin for record attachments to be recovered within a configured period of time.

### Configuration of attachment recovery

Attachment recovery can be enabled by going to **Document management parameters** > **General** >  **Deferred deletion** > **Deferred deletion enabled**. The default for **Number of days to defer deletion** is 30 days but can be changed as needed. If the **Number of days to defer deletion** value is zero, the deleted attachments are recoverable for an indefinite period. 

After attachment recovery is enabled, a batch job with this name is created, "Scans for deleted references which have reached the end of their retention period." This batch job uses the **Number of days to defer deletion** to determine how long to retain a deleted attachment based on the **Deleted data and time**.

### Deleting attachments when attachment recovery is active

When a user deletes an attachment, a notification is added to the Message Center to provide confirmation of the deletion and an option to undo to the action if the deletion was unintended.

Table extension support is built in so that any extension or custom field values on the **DocuRef** or **DocuValue** tables are retained to enable their recovery. 

### Recovering attachments

When attachment recovery is enabled, attachments can be recovered in one of three ways:
1. Immediately after deletion, the user can use the undo link in the **Attachment deleted** notification.
2. On the **Attachments** page, a **Deleted attachments** button provides access to the list of deleted attachments that can be recovered for a particular record. The deleted attachments can be opened for review, permanently deleted, or restored.
3. In **System administration** > **Inquiries**, the **Deleted attachments** page provides access to the list of deleted attachments that can be recovered for any record. The deleted attachments can be opened for review, permanently deleted, or restored.

## Scanning attachments for viruses and malicious code
When you work with attachments, you might want to scan the files for viruses and malicious code. Therefore, in version 10.0.12 and later, extension points are available so that customers can integrate with the file scanning software of their choice when they work with attachments. A similar extension point is also available for file upload. For more information, see [File upload control](../user-interface/file-upload-control.md).

> [!IMPORTANT]
> Out of the box, finance and operations apps don't scan files for viruses and malicious code, and we don't recommend specific software for file scanning. Instead, customers are responsible for choosing their own file scanning software, and for adding the appropriate code to the delegate handlers so that they can use the software or service of their choice to scan files.

The **Docu** class exposes the following two delegates. Handlers can be implemented for these delegates for document scanning purposes:

- **Docu.delegateScanDocument()** – This delegate applies the file scanning logic when a new document attachment is uploaded, or when a user tries to preview or download an existing attachment. The corresponding action fails if the scanning service determines that the file is malicious.
-  **Docu.delegateScanDeletedDocument()** – This delegate applies the file scanning logic to documents in the attachments recycle bin when a user tries to preview or download a file. The corresponding action fails if the scanning service determines that the file is malicious.

### Implementation details
The following example of the **ScanDocuments** class shows boilerplate code for the two handlers. For general information about how to implement handlers for delegates, see [EventHandlerResult classes in request or response scenarios](../dev-tools/event-handler-result-class.md).

```xpp
    public final class ScanDocuments
    {

        [SubscribesTo(classStr(Docu), staticDelegateStr(Docu, delegateScanDocument))]
        public static void Docu_delegateScanDocument(DocuRef _docuRef, EventHandlerRejectResult _validationResult)
        {
            if (!ScanDocuments::scanDocument(_docuRef))
            {
                _validationResult.reject();
            }
        }

        [SubscribesTo(classStr(Docu), staticDelegateStr(Docu, delegateScanDeletedDocument))]
        public static void Docu_delegateScanDeletedDocument(DocuDeletedRef _docuDeletedRef, EventHandlerRejectResult _validationResult)
        {
            if (!ScanDocuments::scanDeletedDocument(_docuDeletedRef))
            {
                _validationResult.reject();
            }
        }

        private static boolean scanDocument(DocuRef _docuRef)
        {
            /*
            Custom implementation required for connecting to a scanning service
            If document scanning process found an issue, return false; otherwise, return true;
            */
            return true;
        }

        private static boolean scanDeletedDocument(DocuDeletedRef _docuDeletedRef)
        {
            /*
            Custom implementation required for connecting to a scanning service
            If document scanning process found an issue, return false; otherwise, return true;
            */
            return true;
        }

    }
```

## [Developer] Specifying valid content types when attaching documents programmatically

The following APIs from the `DocumentManagement` class allow developers to specify the file content type (MIME type) of the file being attached. 
-  attachFileToCommon()
-  attachFile()
-  attachFileToDocuRef()

If this file content type isn't specified correctly, the attached document may not behave as expected. For this reason, if you use these APIs you should consider one of the following courses of action:  

-  Pass **null** for the `_fileContentType` parameter in any of the preceding APIs. Doing so allows the correct content type to be inferred from the file name. 
-  Switch to using one of the following methods that doesn't include a `_fileContentType` parameter. This action avoids the possibility of passing incorrect file content types.
    -  **attachFileForRecord()**, which replaces attachFileToCommon()
    -  **attachFileForReference()**, which replaces attachFile()
    -  **attachFileForDocuRefRecord()**, which replaces attachFileToDocuRef()

## <a id="export-attachments"></a> Export attachments

As of version 10.0.40 of Dynamics 365 Finance, the **Export attachments** feature is available in **Document management**. Use this feature to export files and metadata attached to records of tables in Finance.

To export attachments, follow these steps.

1. Go to the **Modules** \> **Organization administration** \> **Document management parameters** \> **Export attachments**.
2. On the **Export attachments** page, to add lines for each table for which you want to export attachments, select **New** on the Action Pane. The following table describes the fields available on **Export attachments** page.

| Field name           | Field description | Example |
|----------------------|-------------------|---------|
| **Table name**       | Name of a table for which you want to export attachments.  | CustInvoiceJour |
| **Table label**      | Label assigned to the selected table. | Customer invoice journal |
| **Date field name**  | The date type of the selected table. The exporting job uses this field as criteria to apply the **Date from** and **Date to** range that you specify to export attachments. | InvoiceDate |
| **Date field label** | Label assigned to the selected date field. | Date |
| **Enabled**          | When the checkbox is selected, the system includes the related table with the next exporting job. | Yes |

![Export attachments page.](../media/docu-ref-export-attachments-page.png)

3. Select **Export** on the Action Pane to open the **Export attachments** dialog. The following table describes the fields available on **Export attachments** dialog.

| Field name                         | Field description | Example |
|------------------------------------|-------------------|---------|
| **From date**<br> **To date**      | The period for which you want to export attachments. The exporting job applies this period to the **Date field name** of the selected tables for which you enabled to export attachments.  | 1/1/2023 <br> 12/31/2023 |
| **File type**                      | File type used for creating an archive of exported attachments. This file type must be set up as described in [Configure file types](#configure-file-types). | File |
| **Compression level**              | Compression level parameter of an archive that specifies how much the data within the archive is compressed. This parameter indicates whether a compression operation emphasizes speed or compression size. <ul><li>**Fastest** - The compression operation should complete as quickly as possible, even if the resulting file isn't optimally compressed.</li><li>**No compression** - No compression should be performed on the file. </li><li>**Optimal** - The compression operation should optimally balance compression speed and output size.</li></ul> | Optimal |
| **Maximum file size in megabytes** | This parameter redefines the value specified by the **Maximum file size in megabytes** parameter on the **Document management parameters** page for specific execution of the **Export attachments** job, and is applied to limit the size of archive that is created. If the size of archive exceeds the **Maximum file size in megabytes** value, multiple files are created and attached. Configuring an extensive value for **Maximum file size in megabytes**  may impact job execution performance. | 90 |
| **Include metadata**               | When the checkbox is selected, the system includes **Note** and **URL** type attachments and the metadata of **File** type attachments in the export job. Exported metadata is exported as separate JavaScript Object Notation (JSON) files. When the checkbox isn't selected, only attachments of the **File** type are exported without metadata. | Yes |

4. Expand **Run in the background** FastTab, select **Batch processing** checkbox, and then specify the necessary parameters to run the **Export attachments** job in the background. Attachments are exported for the legal entity where the job is executed.
5. Select **OK** to start executing **Export attachments** job.

![Export attachments dialog.](../media/docu-ref-export-attachments-dialog.png)

When execution of the **Export attachments** job is completed, you can find exported attachments in the archives attached for each enabled table. Depending on the volume of the exported attachments in the specified period, and value specified for the **Maximum file size in megabytes** parameter on the **Export attachments** dialog, the archive can be automatically split into several files. 

The name of each attached archive is in the format `LE_TableName_DateFieldName_Period_SeqNum.zip`, and contains the following information: 

- **LE**: The ID of the legal entity.
- **TableName**: The name of the referred table.
- **DateFieldName**: The date type field selected as criteria.
- **Period**: The values of the **Date from** and **Date to** parameters.
- **SeqNum**: The sequential number of the archive in case there are several archive files created. 

The names of the attachments included in an archive are in the format `RecID_AttachmentName_AttachmentDate_SeqNum.xxx`, and contains the following information: 

- **RecID**: The ID of the referred record in selected table. 
- **AttachmentName**: The original file name of the attachment. 
- **AttachmentDate**: The date when the attachment was attached to the referred record of the table. 
- **SeqNum**: The sequential number in case there are simultaneously duplicate attachments.
- **xxx**: The attachment file extension.

## Frequently asked questions

### What is the difference between document handling and document management?

There's no difference between document handling and document management. Both terms refer to the same functionality. Different terms are used in different versions of the product.

### What is the difference between document management and print management?

Document management lets you add notes, documents, and other files to records.

Print management lets you control print settings for selected reports. Print settings include the number of copies, the printer destination, and the multilanguage text that can be included on the report. For more information, see [Document Reporting Services](../analytics/document-reporting-services.md).

### What is the difference between document types and file types?

Document types are used to categorize the documents that you attach to records or the templates that you create. Each document type can be stored in a unique location. The table for document types is named DocuType.

File types include Microsoft Word documents and images. A file type is denoted by the extension of the file, such as .txt, .png, .doc, .xlsx, or .pdf.

### Does document management integrate with Microsoft 365?

Yes. SharePoint storage is supported natively and can be selected as the storage location for a document type. In addition, any URL addressable file can be made an attachment via the **URL** document type.

### What is the default storage location for attachments in Finance + Operations environments?

By default, attachments are saved in Azure Blob storage automatically as part of the product cloud offering.

### If I accidentally delete an attachment stored in Azure Blob storage, can it be restored?

If an attachment stored in Azure Blob storage is accidentally deleted, it can't be restored or recovered because it's permanently deleted, and the reference to the attachment is also deleted.

### Is the database information about attachments stored separately from the attachments themselves?

Record attachment information is stored in the DocuRef and DocuValue tables. The DocuRef table is the record that represents the attachment. The DocuRef record points to the record being attached to and to a DocuValue record. The DocuValue record points to the file that is the attachment. Files are stored outside the database, so any database operations such as restoring from backup only affect the database information about the attachment, not the attachment file itself.

### Can attachments be stored in the database?

No. By default, attachments are stored in Azure Blob storage.

### What are the main differences between Azure Blob storage and database storage?

Database storage is Azure SQL Database. File storage is Azure Blob storage. Azure Blob storage is simpler and much less expensive.

### How much storage do we get for Azure Blob storage?

That information is in the [licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544). Currently, you get 40 gigabytes (GB) of storage.

### What is the cost for additional storage?

The cost for additional storage varies, but it's similar to the [standard Azure costs for storage](https://azure.microsoft.com/pricing/details/storage/page-blobs/). In other words, the cost is about $0.05 per GB.

### How do we know how much storage is already used?

There are proactive communications when you're approaching your database and file storage limits. However, Microsoft Dynamics Lifecycle Services (LCS) provides some information, and you can log support requests for additional information. 

### Is there an option to export all document attachments from the system?

Although attachments can be exported, that capability isn't a standard capability, because there isn't a standard attachment entity. Entities that provide attachments for a specific business document or record must be built.

### How can attachments be extracted from the system?

To extract attachments, an Attachments entity must be built for a specific business document or record. There isn't a standard attachment entity because the identity for each record type is different. To learn how to build an Attachments entity, you can find examples in the Application explorer by searching for "Attachment" under the **AOT > Data Model > Data Entities** node.

### How does the document preview work for attachments stored in SharePoint?

The files are retrieved from SharePoint using the current user permissions by the WOPI service. Those files are then rendered in HTML to provide a document preview. The current user needs access to the files to be able to preview them or open them.

## Troubleshooting issues

### Issue: When users interact with Document management or Electronic reporting, they receive an error similar to "Invalid length for a Base-64 char array or string"

**Explanation**: Typically, this issue occurs because the token for the Office Web Apps Server is no longer valid.  

**Fix**: The admin needs to select the **Token refresh** button to the right of the **Office Web Apps Server** field on the **Document management parameters** page under the **General** tab.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

