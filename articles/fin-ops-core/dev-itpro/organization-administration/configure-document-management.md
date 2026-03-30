---
title: Configure document management
description: Learn about how to configure document management (document handling) so that it stores file attachments and notes for records.
author: jasongre
ms.author: jasongre
ms.date: 03/17/2026
ms.topic: how-to
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update 
---

# Configure document management

[!include [banner](../../../finance/includes/banner.md)]

This article explains how to configure document management (document handling) so that it stores file attachments and notes for records. It includes information about the concepts and features that are involved in this functionality.

To learn more about document management, watch the short [Document Management](https://www.youtube.com/watch?v=p4rl1CkiLN4&feature=youtu.be) video.

## Configure document types

Use document types to categorize the documents that you attach to records or the templates that you create. You can store each document type in a unique location.

The system provides a default set of document types. Use these document types to categorize an attachment as a file, image, note, or URL. The **File** and **Image** default document types are configured to use **Azure storage** as the location.

To create a new document type, follow these steps:

1. Go to the **Document types** page.
1. Select **New**.
1. In the **Type** field, enter a short name for the new document type, such as **SharePoint** or **HR Docs**.
1. In the **Name** field, enter a longer name, such as **SharePoint files** or **HR Docs**.
1. In the **Class** field, specify a class to define the behavior for the document type:

    - **Attach file** – The user is prompted for a file.
    - **Attach URL** – The user can enter a URL in the **Notes** field, such as `https://www.microsoft.com`. The **Open** button on the **Attachments** page opens the URL on a browser tab.
    - **Simple note** – The user can add a note in the **Notes** field.

1. If you specify **Attach file** in the **Class** field, use the **Location** field to specify the storage mechanism.
1. If you specify **SharePoint** in the **Location** field, select the **Edit** button (pencil symbol) and use the **Folder selection** dialog box to specify the Microsoft SharePoint address in the **SharePoint Address** field.

## Configure SharePoint storage

SharePoint Online is a supported storage location for attachments. 

> [!IMPORTANT]
> - SharePoint storage is only available in Microsoft-managed environments.
> - On-premises SharePoint (a local SharePoint server) isn't currently supported.
> - SharePoint managed device policies aren't compatible with an integration to finance and operations apps.

### One-time registration process 
In Dynamics 365 finance and operations version 10.0.40 and later, when you enable the **SharePoint user authentication** feature, your organization needs to perform a one-time setup to use the SharePoint integration for non-interactive batch scenarios. This setup is necessary because Microsoft deprecated the Microsoft-managed high-trust connection between the finance and operations environment and SharePoint. 

With this updated SharePoint authentication mechanism, batch connections use application access. As this access isn't granted by default for tenants, an Entra ID tenant administrator needs to grant access manually one time for the tenant. To provide the required application consent for finance and operations batch scenarios to connect to SharePoint, run the following PowerShell commands.  

``` powershell

Import-Module Microsoft.Graph.Applications
   
# The parameter for TenantId needs to be changed
Connect-MgGraph -TenantId microsoft.onmicrosoft.com -Scopes 'Application.ReadWrite.All'
    
# These AppIds do not change as they are the first party application IDs
$erpServicePrincipal = Get-MgServicePrincipal -Filter "AppId eq '00000015-0000-0000-c000-000000000000'"
$sharePointServicePrincipal = Get-MgServicePrincipal -Filter "AppId eq '00000003-0000-0ff1-ce00-000000000000'"
$spAppRole = $sharePointServicePrincipal.AppRoles | where {$_.Value -eq 'Sites.ReadWrite.All'}
    
# Assign the SharePoint 'Sites.ReadWrite.All' permission to the Microsoft Dynamics 365 finance and operations application
New-MgServicePrincipalAppRoleAssignedTo -ServicePrincipalId $erpServicePrincipal.Id -PrincipalId $erpServicePrincipal.Id -ResourceId $sharePointServicePrincipal.Id -AppRoleId $spAppRole.Id
```
> [!IMPORTANT]
> Interactive connections use the logged-in user's context.
> -  As conditional access can pass through the finance and operations sign-in to SharePoint, ensure that conditional access settings for SharePoint are applied to finance and operations.
> -  Calling SharePoint as a user that isn't the currently authenticated user is no longer supported.

### Setting up SharePoint inside your finance and operations environment

To configure SharePoint storage, follow these steps:

1. Go to the **Document management parameters** page.
1. On the **SharePoint** tab, in the **Default SharePoint server** field, review the host name that the system automatically detects for the SharePoint site, such as contosoax7.sharepoint.com. Typically, the SharePoint host name is in the form `tenantname.sharepoint.com`, and accounts on that tenant are in the form `user1@tenantname.onmicrosoft.com`.

    Typically, if you don't specify a default SharePoint server, either there's no SharePoint site for the tenant, or a valid Microsoft 365 license isn't associated with the current user (the admin).

1. Optional: Test the SharePoint connection
    -  If you disable the **SharePoint user authentication** feature, select **Test SharePoint connection** to test the specified SharePoint host name. This action verifies that the security and license are working correctly.
    -  If you enable the **SharePoint user authentication** feature, there are two SharePoint connection types to test. Use the **Test interactive SharePoint connection** action to test interactive scenarios by using the logged-in user's context. Use the **Test batch SharePoint connection** action to test batch scenarios by using the granted application access.  
1. Optional: Select **Open SharePoint** to open the specified SharePoint host name in a browser. This action doesn't verify security. It just opens the SharePoint path on a browser tab for easy exploration.
1. Optional: On the **General** tab, turn on **Open attachments in new window**. For more information, see the [Other configuration](#other-configuration) section later in this article.

To use SharePoint storage, set the **Location** field for a document type to **SharePoint**. Then, in the **SharePoint Address** field, enter a valid SharePoint address.

### Troubleshooting SharePoint communication

SharePoint communication works for the current user only if the following conditions are met:

- A Microsoft 365 license is associated with the user's account.
- The user is a typical user on the tenant, not an external user (for example, a user from another tenant).
- There's a SharePoint site for the tenant (for example, Contoso.SharePoint.com).
- The SharePoint site is configured to **Allow this site to appear in search results**.
- The SharePoint site doesn't use managed device policies.

    If you enable managed device policies on the SharePoint instance, the finance and operations SharePoint integration stops working. Therefore, users can't download, view, or create documents that are stored in SharePoint from finance and operations apps.

- The user has access to the folder that the document is stored in.

If you can't open documents stored in SharePoint or they don't appear in preview, follow these steps to troubleshoot the issue.

1. Verify that the admin account has an associated email account. You can verify or change the associated email account on the **User** page. If you don't set up an associated email account, you must add the email account and provider via the OData Excel add-in. By default, the email address isn't present in the Excel design. You must edit the Excel design, add all fields, apply the change, and refresh. You can then update the admin account.
1. After the admin account has an associated email account, sign in to Dynamics 365 as the admin.
1. Open an attachment that's stored in SharePoint.
1. Sign in by using a different user account that has read access to the attachments page and the configured SharePoint folder. Verify that this user account can open and preview the attachment.

## Configure file types

By modifying the list of allowed file extensions, you can control the types of files that users can attach to records.

To specify file types, follow these steps:

1. Go to the **Document management parameters** page.
1. On the **File types** tab, review the default file types.
1. Remove any file types that users shouldn't attach to records. Add any file types that users should attach to records.

## Configure document preview

The attachments preview uses the Web app Open Platform Interface (WOPI) that Office Online Server provides. On the **Document management parameters** page, on the **General** tab, in the **Office Web Apps Server** field, specify the Office Online Server instance to use for attachment previews. The default value is `https://onenote.officeapps.live.com`, which points to the cloud-based WOPI server.

> [!NOTE]
> For the following situations, you must adjust the **Office Web Apps Server** value:
>
> - For environments in China, use `https://onenote.partner.officewebapps.cn`. 
> - For environments in the Government Community Cloud (GCC), use `https://gb4-onenote.officeapps.live.com`.

### For a Dynamics 365 Finance + Operations (on-premises) environment

The default cloud-based WOPI server in Finance + Operations (on-premises) can't read the attachment file to provide a preview. If you need previews, you must [install an on-premises Office Online Server instance](/officeonlineserver/deploy-office-online-server) and configure it inside the environment. Set the **Office Web Apps Server** field to the host name of the installed Office Online Server instance, and then select **Save**.

If you don't need previews, set the **Office Web Apps Server** field to `https://localhost`. The preview then shows the message "No preview available" instead of an error message.

### Document preview (WOPI) doesn't work in environments where an IP allow list is enabled

Document preview (WOPI) doesn't work in environments where an IP allow list is enabled, because the WOPI service that provides the preview can't connect back to the file service to retrieve the file for rendering.

## Other configuration

Consider these configuration options:

- On the **Document management parameters** page, on the **General** tab, use the **Use active document tables** option to enable the **Active document tables** allow list. If you set this option to **Yes**, you disable attachments on all other tables. Turn on this option only when it's required.
- On the **Document management parameters** page, on the **General** tab, use the **Maximum file size in megabytes** field to set the maximum file size for attachments. When you use SharePoint as a document type, users can upload only documents that have a maximum file size of 262 megabytes (MB).
- On the **Document management parameters** page, on the **General** tab, use the **Open attachments in new window** option to determine whether attachments are opened in place, or in a new window or on a new tab. Consider turning on this option especially if you use SharePoint to store attachments, because this option prevents the finance and operations user session from being reset when attachments are opened. This option is available as of version 10.0.23.
- On the **Options** page (**Settings** > **User options**), on the **Preferences** tab, use the **Enable document handling** option to disable document handling (document management).

## Accessing document management attachments

Document management appears to users as the **Attach** button at the top of most pages that contain data. When you select the **Attach** button (or when you use the corresponding keyboard shortcut, **Ctrl**+**Shift**+**A**), you open the **Attachments** page in the context of the data source of the control that's currently selected on the page. This page shows all the attachments that are related to the corresponding data source.

The **Attach** button also shows a count of the attachments for the currently selected record. Therefore, you can determine whether there are attachments for the current record without having to open the **Attachments** page. The button shows exact counts for zero through nine attachments. If there are more than nine attachments, the button shows **9+** as the count. In this way, the performance impact and visual noise that exact larger counts might cause are reduced.

## Document attachment history

As of version 10.0.16/Platform update 40, a history mechanism is available for record attachments. Therefore, your organization can maintain an audit of actions that are related to individual attachments. You can see when an attachment was created, marked for pending deletion, restored, deleted, or moved. You can also see who performed the action. Attachment history isn't maintained before version 10.0.16/Platform update 40. Therefore, any actions that were performed on attachments in earlier versions aren't available.

### Configuration of document attachment history

To enable or disable document attachment history, go to **Document management parameters** > **General** > **History** > **Enable document history**. The default setting of the **Number of days to retain history** field is 180 days, but you can change it as you require.

### Viewing an attachment's history

There are two entry points for viewing the history of a record attachment:

- When you're looking at the attachments for a specific record (see the [Accessing document management attachments](#accessing-document-management-attachments) section), you can view the history for the current set of attachments on the **Attachments** page by selecting **Document history** on the Action Pane.
- Administrators can select the **Document history** button in the **History** section of the **Document management parameters** page. This action opens the **Document history** page, which shows a list of all attachments in the system. You can then drill into any record to view the detailed history for the selected attachment.

## Attachment recovery

Platform update 29 introduced an attachment recovery feature. This feature provides a recycle bin for record attachments, so you can recover them within a configured period.

### Configuration of attachment recovery

To enable attachment recovery, go to **Document management parameters** > **General** > **Deferred deletion** > **Deferred deletion enabled**. The default setting for the **Number of days to defer deletion** field is 30 days, but you can change it as you require. If you set the **Number of days to defer deletion** value to **0** (zero), deleted attachments are recoverable for an indefinite period.

After you enable attachment recovery, you create a batch job named **Scans for deleted references which have reached the end of their retention period**. This batch job uses the **Number of days to defer deletion** value to determine how long a deleted attachment should be retained, based on the **Deleted date and time** value.

### Deleting attachments when attachment recovery is active

When you delete an attachment, the system adds a notification to the Message Center to confirm the deletion. The notification also provides an option that lets you undo the deletion if it was unintended.

Table extension support is built in. Therefore, the system retains any extension or custom field values on the DocuRef or DocuValue table to enable their recovery.

### Recovering attachments

When you enable attachment recovery, you can recover attachments in one of three ways:

- Immediately after deletion, use the undo link in the **Attachment deleted** notification.
- On the **Attachments** page, use the **Deleted attachments** button to access the list of deleted attachments that you can recover for a particular record. You can open the deleted attachments for review, permanently delete them, or restore them.
- At **System administration** > **Inquiries**, use the **Deleted attachments** page to access the list of deleted attachments that you can recover for any record. You can open the deleted attachments for review, permanently delete them, or restore them.

## Scanning attachments for viruses and malicious code

When you work with attachments, you might want to scan the files for viruses and malicious code. Therefore, in version 10.0.12 and later, extension points are available so that you can integrate with the file scanning software of your choice when you work with attachments. A similar extension point is also available for file upload. For more information, see [File upload control](../user-interface/file-upload-control.md).

> [!IMPORTANT]
> Out of the box, finance and operations apps don't scan files for viruses and malicious code, and they don't recommend specific software for file scanning. Instead, you're responsible for choosing your own file scanning software, and for adding the appropriate code to the delegate handlers so that you can use the software or service of your choice to scan files.

The **Docu** class exposes the following two delegates. You can implement handlers for these delegates for document scanning purposes:

- **Docu.delegateScanDocument()** – This delegate applies the file scanning logic when you upload a new document attachment, or when a user tries to preview or download an existing attachment. The corresponding action fails if the scanning service determines that the file is malicious.
- **Docu.delegateScanDeletedDocument()** – This delegate applies the file scanning logic to documents in the attachment recycle bin when a user tries to preview or download a file. The corresponding action fails if the scanning service determines that the file is malicious.

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

The following APIs from the `DocumentManagement` class let you specify the file content type (MIME type) of the file you're attaching:

- `attachFileToCommon()`
- `attachFile()`
- `attachFileToDocuRef()`

If you don't specify the file content type correctly, the attached document might not behave as expected. Therefore, if you use these APIs, consider one of the following actions:

- Pass **null** for the `_fileContentType` parameter in any of the preceding APIs. This action enables the correct content type to be inferred from the file name.
- Switch to using one of the following methods that don't include a `_fileContentType` parameter. This action helps prevent the possibility that incorrect file content types are passed.

    - **attachFileForRecord()**, which replaces **attachFileToCommon()**
    - **attachFileForReference()**, which replaces **attachFile()**
    - **attachFileForDocuRefRecord()**, which replaces **attachFileToDocuRef()**

## <a id="export-attachments"></a>Export attachments

In version 10.0.40 and later, Document management includes the **Export attachments** feature. Use this feature to export files and metadata that are attached to records of tables in finance and operations apps.

To export attachments, follow these steps:

1. Go to **Organization administration** > **Document management parameters** > **Export attachments**.
1. On the **Export attachments** page, on the Action Pane, select **New** to add a row for the first table that you want to export attachments for. Repeat this step until all the tables that you need attachments for are listed. The following table describes the fields that are available on the **Export attachments** page.

    | Field name       | Description | Example value |
    |------------------|-------------|---------------|
    | Table name       | The name of the table that you want to export attachments for. | CustInvoiceJour |
    | Table label      | The label that's assigned to the selected table. Note that multiple tables can share the same label. | Customer invoice journal |
    | Date field name  | A date field of the selected table. The export job uses this field as a criterion to apply the **Date from** and **Date to** range that you specify to export attachments. | InvoiceDate |
    | Date field label | The label that's assigned to the selected date field. | Date |
    | Enabled          | When this checkbox is selected, the system includes the selected table with the next export job. | Selected |

    :::image type="content" source="../media/docu-ref-export-attachments-page.png" alt-text="Screenshot of the Export attachments page.":::

1. On the Action Pane, select **Export** to open the **Export attachments** dialog box. The following table describes the fields that are available in the **Export attachments** dialog box.

    | Field name                     | Description | Example value |
    |--------------------------------|-------------|---------------|
    | From date                      | Specify the first date of the period that you want to export attachments for. The export job applies this period to the **Date field name** value of the selected tables that are configured to export attachments. | 1/1/2023 |
    | To date                        | Specify the last date of the period that you want to export attachments for. The export job applies this period to the **Date field name** value of the selected tables that are configured to export attachments. | 12/31/2023 |
    | File type                      | Specify the file type that's used to create an archive of exported attachments. Set up this file type as described in the [Configure file types](#configure-file-types) section. Select **File** in the list of file types. Alternatively, use a similar custom file type that you set up with an **Attach file** value in the **Class** property of the document type. | File |
    | Compression level              | <p>This parameter determines how much the data in an archive is compressed. Specifically, it defines whether a compression operation emphasizes speed or compression size. Select one of the following options:</p><ul><li>**Fastest** – The compression operation should be completed as quickly as possible, even if the resulting file isn't optimally compressed.</li><li>**No compression** – No compression should be done on the file.</li><li>**Optimal** (default) – The compression operation should optimally balance compression speed and output size.</li></ul> | Optimal |
    | Maximum file size in megabytes | Use this parameter to limit the size of the created archive. The value redefines the value that's set for the **Maximum file size in megabytes** parameter on the **Document management parameters** page for a specific execution of the **Export attachments** job. If the size of the archive file exceeds the value that you set here, the process creates and attaches multiple files. A large **Maximum file size in megabytes** value might affect the performance of job execution. | 90 |
    | Include metadata               | If you set this option to **Yes**, the system includes **Note** and **URL** type attachments and the metadata of **File** type attachments in the export job. Exported metadata is exported as separate JavaScript Object Notation (JSON) files. If you leave this option set to **No** (the default value), only attachments of the **File** type are exported without metadata. | Yes |

1. On the **Run in the background** FastTab, set the **Batch processing** option to **Yes**, and then specify the necessary parameters to run the **Export attachments** job in the background. The job exports attachments for the legal entity where you run the job.
1. Select **OK** to start running the **Export attachments** job.

    :::image type="content" source="../media/docu-ref-export-attachments-dialog.png" alt-text="Screenshot of the Export attachments dialog box.":::

When the **Export attachments** job finishes, you can find the exported attachments in the archives that are attached for each enabled table. Depending on the volume of the exported attachments in the specified period, and the value of the **Maximum file size in megabytes** parameter in the **Export attachments** dialog box, the process might automatically split the archive into several files.

The name of each attached archive is in the format *LE\_TableName\_DateFieldName\_Period_SeqNum.zip* and contains the following information:

- **LE** – The ID of the legal entity.
- **TableName** – The name of the referenced table.
- **DateFieldName** – The date field that's selected as a criterion.
- **Period** – The values of the **Date from** and **Date to** parameters.
- **SeqNum** – The sequential number of the archive, in case the process creates several archive files.

The name of each attachment that's included in an archive is in the format *RecID\_AttachmentName\_AttachmentDate\_SeqNum.xxx* and contains the following information:

- **RecID** – The ID of the referenced record in the selected table.
- **AttachmentName** – The original file name of the attachment.
- **AttachmentDate** – The date when the attachment was attached to the referenced record of the table.
- **SeqNum** – The sequential number, in case there are simultaneous duplicate attachments.
- **xxx** – The attachment file extension.

## Frequently asked questions

### What is the difference between document handling and document management?

There's no difference between document handling and document management. Both terms refer to the same functionality. Different terms are used in different versions of the product.

### What is the difference between document management and print management?

Document management lets you add notes, documents, and other files to records.

Print management lets you control print settings for selected reports. Print settings include the number of copies, the printer destination, and the multilanguage text that can be included on the report. For more information, see [Document Reporting Services](../analytics/document-reporting-services.md).

### What is the difference between document types and file types?

Use document types to categorize the documents that you attach to records or the templates that you create. You can store each document type in a unique location. The table for document types is named DocuType.

File types include Word documents and images. A file type is denoted by the extension of the file, such as .txt, .png, .doc, .xlsx, or .pdf.

### Does document management integrate with Microsoft 365?

Yes. The system supports SharePoint storage natively, and you can select it as the storage location for a document type. In addition, you can make any URL addressable file an attachment by using the **URL** document type.

### What is the default storage location for attachments in Finance + Operations environments?

By default, the system saves attachments in Azure Blob storage automatically as part of the product cloud offering.

### If I accidentally delete an attachment stored in Azure Blob Storage, can I restore it?

When you delete attachments that are stored in Azure Blob Storage, you permanently delete them. The system also deletes the references to those attachments. Therefore, if you accidentally delete an attachment, you can't restore or recover it.

### Is the database information about attachments stored separately from the attachments themselves?

The system stores record attachment information in the **DocuRef** and **DocuValue** tables. The **DocuRef** table contains the record that represents the attachment. Each **DocuRef** record points to both the record it's attaching to and a **DocuValue** record. Each **DocuValue** record points to the file for the attachment. The system stores files outside the database. Therefore, database operations, such as restorations from a backup, affect only the database information about the attachment, not the attachment file itself.

### Can the system store attachments in the database?

No. By default, the system stores attachments in Azure Blob storage.

### What are the main differences between Azure Blob storage and database storage?

Database storage uses Azure SQL Database. File storage uses Azure Blob storage. Azure Blob storage is simpler and much less expensive.

### How much storage do I get for Azure Blob storage?

See the [licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544). Currently, you get 40 gigabytes (GB) of storage.

### What is the cost for additional storage?

The cost for additional storage varies, but it's similar to the [standard Azure costs for storage](https://azure.microsoft.com/pricing/details/storage/page-blobs/). In other words, the cost is about $0.05 per GB.

### How do I know how much storage is already used?

The system provides proactive communication when you're approaching your database and file storage limits. However, Microsoft Dynamics Lifecycle Services provides some information, and you can log support requests for additional information.

### Is there an option to export all document attachments from the system?

Although you can export attachments, this capability isn't a standard capability because the system doesn't include a standard attachment entity. You must build entities that provide attachments for a specific business document or record.

### How can you extract attachments from the system?

To extract attachments, you must build an Attachments entity for a specific business document or record. There's no standard attachment entity because the identity for each record type differs. To learn how to build an Attachments entity, review the examples in Application explorer. To find these examples, search for "Attachment" under the **AOT** \> **Data Model** \> **Data Entities** node.

### How does the document preview work for attachments stored in SharePoint?

The WOPI service retrieves the files from SharePoint by using the current user permissions. The service then renders the files in HTML to provide a document preview. The current user must have access to the files to preview or open them.

## Troubleshooting problems

### Problem: When users interact with Document management or Electronic reporting, they receive an error similar to "Invalid length for a Base-64 char array or string."

**Explanation:** Typically, this problem occurs because the token for the Office Web Apps Server is no longer valid.

**Fix:** The admin needs to select the **Token refresh** button to the right of the **Office Web Apps Server** field on the **Document management parameters** page under the **General** tab.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
