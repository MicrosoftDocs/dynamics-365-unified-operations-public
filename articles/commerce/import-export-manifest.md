---
title: Bulk import and export digital assets using manifests
description: This article describes how to bulk import and export digital assets using manifests in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 5/26/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: psimolin
ms.search.validFrom: 2023-03-01

---

# Bulk import and export digital assets using manifests

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This article describes how to bulk import and export digital assets using manifests in Microsoft Dynamics 365 Commerce site builder, and also describes the manifest schema and provides examples of import and export operations.

Manifest-based asset import and export operations are executed in the Commerce site builder media library. Manifest-based operations always require (for import) or produce (during export) a manifest file, which is a tab-delimited \*.tsv text file listing all the assets that are part of the operation. For export operations, all of the asset information is included in the manifest, including read-only metadata information such as when assets were created and published. Import operations only require a subset of the fields to be entered for each asset, the remaining fields are optional.

When imported, manifest documents are processed row by row. If the processing of any of the rows fails for any reason, a description of the error is included in the resulting manifest which can be downloaded from the job details view. If one of multiple entries in a manifest fails, it won't prevent the rest of the manifest from being processed. If the error requires the user to fix something in the manifest (for example, if the source URL is incorrect), the result manifest from the first run can be used to fix and reprocess the assets with errors.

The main use cases for manifest-driven asset import and export operations are:

- Uploading product media and other digital assets to the system during onboarding.
- Modifying asset metadata in bulk (for example, adding specific keywords to a large number of assets).
- Performing search and replace operations on the metadata (for example, rebranding).
- Performing actions in bulk (for example, publishing or deleting assets).

Manifests can also be used to import and export product media assignments. The schema used for product media assignments is an extended version of the plain asset management manifest schema. For information on product media assignments, see [Assign media to products and categories](assign-media-omnichannel.md).

## Manifest schema

Manifest documents are tab delimited unicode text files with \*.tsv extensions. The first row of the manifest is a header row and contains the column names. After the header row, each following row represents a single asset and its associated metadata. For the initial ingestion of an asset, binary files (in other words, actual assets) must be provided along with the manifest, either as a local upload or as publicly accessible HTTP source URLs.

After a manifest-based import operation has completed, the imported manifest with import results and possible error information can be downloaded from the **Past jobs** tab on the **Site jobs** page (**Site settings \> Jobs**). See the last four rows in the schema description below for what error information is captured and provided.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image1.png)-->

### Schema for asset import and export operations

The following table shows the schema for asset import/export operations.

| Column name                          | Description                                                |
|--------------------------------------|------------------------------------------------------------|
| InternalMediaId                      | Commerce content management system (CMS) asset identity identifier.     |
| MediaChannel                         | Name of the channel from which the asset is exported.       |
| MediaLocale                          | Locale of the asset.                                        |
| MediaType                            | Type of the asset.                                          |
| MediaVersion                         | Version number of the asset.                               |
| MediaCategory                        | Commerce media category.                                    |
| MediaSourceProvider                  | External system from which the asset is being imported.           |
| MediaSourceId                        | Identifier in the external system.                          |
| MediaReferenceUrl                    | URL to external provider (instead of MediaImportPath).      |
| MediaSourceIfExistsAction            | UseExisting, Overwrite, TakeLatest, or KeepBoth.             |
| MediaAction                          | PublishNow, Draft, Unpublish, UnpublishAndDelete.           |
| MediaCheckedOutAction                | UseExisting, Overwrite.                                    |
| MediaVersionMismatchAction           | UseExisting, Overwrite.                                     |
| MediaImportPath                      | Either HTTP source URL or filename.                         |
| ImageAltText                         | Alt text for an image asset.                                |
| MediaSearchTags                      | Keywords describing the asset (comma separated).            |
| MediaCaption                         | Caption for a video asset.                         |
| MediaDisplayName                     | Display name of the asset (unique within a site).           |
| MediaDescription                     | Description of a video asset.                     |
| VideoCaptionImportPath               | URL to the captions for a video asset.                             |
| VideoThumbnailImportPath             | URL to the thumbnail for a video asset (otherwise automatically generated).      |
| VideoTranscriptImportPath            | URL to the transcript for a video asset.                           |
| VideoAudioTrackImportPath            | URL to the additional audio track of a video asset.              |
| VideoDescriptiveAudioTrackImportPath | URL to the descriptive audio track of a video asset.             |
| VideoPlaytime                        | Playtime of a video asset (in seconds).                          |
| MediaCreatedOn                       | Date and time when the asset was created.                   |
| MediaLastModifiedOn                  | Date and time when the asset was last modified.            |
| MediaPublished                       | Has the asset been published (true/false).                  |
| MediaPublishedOn                     | Date and time when the asset was published.                 |
| MediaPublishedURL                    | URL to the published asset.                                     |
| MediaPreviewURL                      | Preview URL for the asset (requires sign-in).                      |
| ImageQuality                         | Quality of the image asset.                                |
| ImageWidth                           | Width of the image asset.                                   |
| ImageHeight                          | Height of the image asset.                                  |
| MediaChecksum                        | Hash of the image asset binary.                             |
| MediaTitle                           | Title of a video asset.                           |
| VideoSubtitle                        | URL to the subtitles of a video asset.                           |
| VideoMinimumAge                      | Minimum age for a video asset.                                |
| DocumentForceDownload                | Force the download of file asset (instead of viewing).      |
| Result                               | Result of the import operation for this row.                |
| ResultTime                           | Time when this row was processed.                           |
| ErrorCode                            | Error code.                                                 |
| ResultDescription                    | Detailed description of the result (for example, an error description). |

<!-- Sample asset manifests (Urls redacted/removed)-->

<!--Sample manifests have all been exported from an environment. They could be imported back (to that same environment) or imported to another environment after clearing the InternalMediaId, MediaChannel and MediaVersion fields.-->

Mandatory fields for manifest import (for new assets):

- MediaLocale
- MediaType
- MediaImportPath
- ImageAltText (for image assets)
- MediaDisplayName
- MediaTitle (for video assets)

Mandatory fields for manifest import (for existing assets):

- InternalMediaId
- MediaChannel
- MediaLocale
- MediaType
- ImageAltText (for image assets)
- MediaDisplayName
- MediaTitle (for video assets)

Columns can be in any order in the import manifest. Export manifests always contain all available fields for assets (depending on the asset type).

The same manifest schema can be used for product media assignments. Product media assignment manifests must include the mandatory fields of the base asset manifest as well. For information on product media assignments, see [Assign media to products and categories](assign-media-omnichannel.md).

### Schema extension for product media assignments

The following table shows the schema extension for product media assignments.

| Column name                         | Description                                                                                                                  |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| EntityType                          | Product assignment target for this row (for example, Master, Variant, DimensionMatrix, Category).                                     |
| EntityKey                           | Specifies what is used as the key for this assignment in the EntityKeyValue field (for example, ProductNumber, RecordId, CategoryID). |
| EntityKeyValue                      | The value of the key specified in EntityKey.                                                                                  |
| EntityLocale                        | Locale of the product assignment.                                                                                            |
| CatalogNumber                       | Catalog number this assignment is associated with.                                                                           |
| EntityChannel                       | Channel operating unit number (OUN) this assignment is associated with.                                                                              |
| EntityAssignmentCurrentPublishState | Publish state of the assignment.                                                                                              |
| EntityAssignmentAction              | PublishNow, Draft, Unpublish, UnpublishAndDelete                                                                             |
| EntityCheckedOutAction              | UseExisting, Overwrite                                                                                                       |
| EntityVersionMismatchAction         | UseExisting, Overwrite                                                                                                       |
| MediaGroup                          | Media group of the asset (Primary/Additional).                                                                                |
| MediaPurpose                        | Purpose of the asset (free-text).                                                                                             |
| MediaDisplayOrder                   | Display order.                                                                                                                |
| SwatchGroup                         | Swatch group (for example, Size or Style).                                                                                            |
| SwatchDimension                     | Swatch dimension (e.g. M, XL, XXL)                                                                                           |
| SwatchValue                         | Swatch value (Hexidecimal code of the color or identity identifier of an image asset).                                                |
| EntityCreatedOn                     | Date and time when the assignment was created.                                                                                |
| EntityLastModifiedOn                | Date and time when the assignment was last modified.                                                                          |
| EntityVersion                       | Assignment version number.                                                                                                    |
| EntityPublishedOn                   | Date and time when the assignment was published.                                                                              |

For more information on swatches, see \[LINK TO NICK – PRODUCT-SPECIFIC SWATCHES\]. For more information on media groups, please see \[LINK TO NICK – ASSIGN MEDIA TO SIMPLE PRODUCTS\].

## Import asset manifests 

Import operation can be started by clicking "Bulk import" from the command bar.

Manifest based asset import operation targeting regular site is started from the media library in the commerce site builder by clicking "Bulk import" from the command bar.

<!--![A screenshot of a computer Description automatically generated with low confidence](media/image2.png)-->

Bulk import dialog is opened where the import job name and description can be modified. Job name is required, but the description is optional.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image3.png)-->

These values don't have an impact on the actual import process, but they help users locate their job from the list of jobs. After entering name and description, clicking "Next" brings up the manifest selection view. Manifest file needs to be tab delimited text file, with a header row with specific column names and one or more rows of assets. \[LINK TO MANIFEST SCHEMA\] Manifest file will be uploaded from the local machine either by selecting "browse your computer" or dragging the file into the view from file explorer of the operating system.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image4.png)-->

After selecting the manifest file, you need to specify if you need to upload local binaries with the manifest. This is not required if all of the assets in the manifest have source http url or they are existing assets and are updating metadata only.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image5.png)-->

If you have new assets that you will be uploading from your local machine, tick the "Import using local files from my device"-box. Proceed to the next step with "Next".

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image6.png)-->

This step is shown only if you indicated that you will be importing assets from local machine. Click "Browse" and select the folder that contains the assets that are associated with the manifest.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image7.png)-->

After selecting the folder, you might see a confirmation dialogue that varies depending on the browser you are using. After reviewing the message, confirm by clicking "Upload" (could be "OK", "Yes" or something similar on depending on your browser).

<!--![A screenshot of a computer Description automatically generated with low confidence](media/image8.png)-->

The view is updated with the folder that you selected. Clicking "Next" takes you to the next step of the process.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image9.png)-->

In the "Review and finish" step, you have all the information for the new bulk import job in the single view you to review. If you need to change any of the parameters, clicking "Edit" next to the information allows you to do that. Clicking "Begin import" will first upload the local files to the service (if selected) and then create a job for the bulk import.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image10.png)-->

The local file upload may take time, depending on the amount and the file size of the asset and your network connection.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image11.png)-->

After the local file upload is completed, manifest import job is created on your site. You can view your job and its progress by clicking "Go to job" from the notification, "-&gt; Go to job" from the view or by navigating to "Site settings" and "Jobs".

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image12.png)-->

By locating and selecting your job from the list of current jobs, you can view details for the job in the inspector pane to the right. After the job has been processed it will be moved to "Past jobs" and the result manifest will become available for download.

<!--![A screenshot of a computer Description automatically generated with medium confidence](media/image13.png)-->

Manifest based asset import operation targeting omnichannel should be started from the media library of the omnichannel. Otherwise the steps are the same.

Manifests with product media assignments should be imported from the **Product media** view in your omnichannel.

### Bulk import an asset manifest

To bulk import an asset manifest, follow these steps.

1.  Go to the omnichannel for your environment.
2.  Select **Product media**.
3.  Select **Bulk import**.
4.  Enter name and description for the job, then select **Next**.
5.  Select the manifest file by browsing your local machine, or by dragging and dropping it onto the view.
6.  If the manifest references asset binaries from the local machine, select the **Import using local files from my device** checkbox.
7.  Select **Next**. 
8.  If you selected the **Import using local files from my device** checkbox above, select the media directory on your local machine, and then proceed to the next step..
9.  Review the job settings, and then slect **Begin import**.

## Export asset manifests 

You can export asset manifests from the site builder media library of any of e-commerce site, or from your omnichannel. Manifests with product media assignments must be exported from the **Product media** view in your omnichannel.

<!--Export operation is started by selecting one or more assets and clicking "Bulk export" from the command bar.-->

### Bulk export an asset manifest

To bulk export an asset manifest, follow these steps.

1.  Go to the site or omnichannel from which you want to export the manifest.
2.  Go to **Media library**.
3.  Select the assets you want to export, and then select **Bulk export** (or **Export entire library**).
4.  Enter a name and description for the export job, review the selected media, and then select **Export**.

The job status can be monitored from **Site settings \> Jobs**, or by selecting **Go to job** from the job notification.

### Bulk export a product assignment manifest

To bulk export a product assignment manifest, follow these steps.

1.  Go to the omnichannel of your environment.
2.  Select **Product media**.
3.  Select **Bulk export**.
4.  Select **Export media assignments for all products** or **Export media assignments for specific products**, and then select **Next**.
5.  If you selected **Export media assignments for specific products**, under **All products**, select the products from which you want to export the media assignments, and then select **Next**.
6.  If you want to export all locales and not just the currently selected locale, select the **Export all locales** checkbox.
7.  Select **Export product media**.

The job status can be monitored from **Site settings \> Jobs**, or by selecting **Go to job** from the job notification.

<!--### Sample product media assignment manifests (Urls redacted/removed)-->

<!--Links to download center URLs TBD-->

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Publish media assignments](publish-media-omnichannel.md)

[Copy omnichannel content between tenants](copy-content-between-tenants.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
