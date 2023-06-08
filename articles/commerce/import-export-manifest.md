---
title: Bulk import and export digital assets using manifests
description: This article describes how to bulk import and export digital assets using manifests in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 06/08/2023
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

This article describes how to bulk import and export digital assets using manifests in Microsoft Dynamics 365 Commerce site builder, and also describes the manifest schema.

You can perform manifest-based asset import and export operations in the Commerce site builder media library. Manifest-based operations require (during import) or produce (during export) a manifest file, which is a tab-delimited \*.tsv text file that lists all assets that are part of the operation. For export operations, all asset information is included in the manifest, including read-only metadata information such as when assets were created and published. Import operations only require a subset of asset information in the manifest for each asset, the remaining fields are optional.

When imported, manifest documents are processed row by row. If the processing of any of the rows fails for any reason, a description of the error is included in the resulting manifest, which can be downloaded from the job details view. If one of multiple entries in a manifest fails, it won't prevent the rest of the manifest from being processed. If an error requires you to fix something in the manifest (for example, if the source URL is incorrect), the result manifest from the first run can be used to fix and reprocess the assets that generated errors.

The main use cases for manifest-driven asset import and export operations are:

- Uploading product media and other digital assets to the system during onboarding.
- Modifying asset metadata in bulk (for example, adding specific keywords to a large number of assets).
- Performing search and replace operations on the metadata (for example, rebranding).
- Performing actions in bulk (for example, publishing or deleting assets).

Manifests can also be used to import and export product media assignments. The schema used for product media assignments is an extended version of the plain asset management manifest schema. For information on product media assignments, see [Assign media to products and categories](assign-media-omnichannel.md).

## Manifest schema

Manifest documents are tab-delimited unicode text files with \*.tsv extensions. The first row of the manifest is a header row and contains the column names. After the header row, each following row represents a single asset and its associated metadata. For the initial ingestion of an asset, binary files (in other words, actual assets) must be provided along with the manifest, either as a local upload or as publicly accessible HTTP source URLs.

After a manifest-based import operation has completed, the imported manifest with import results and possible error information can be downloaded from the **Past jobs** tab on the **Site jobs** page (**Site settings \> Jobs**) in site builder. The last four rows in the schema description below describe what error information is captured and provided.

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

#### Mandatory fields for manifest import (for new assets)

- MediaLocale
- MediaType
- MediaImportPath
- ImageAltText (for image assets)
- MediaDisplayName
- MediaTitle (for video assets)

#### Mandatory fields for manifest import (for existing assets)

- InternalMediaId
- MediaChannel
- MediaLocale
- MediaType
- ImageAltText (for image assets)
- MediaDisplayName
- MediaTitle (for video assets)

Columns can be in any order in an import manifest. Export manifests always contain all available fields for assets (depending on the asset type).

The same manifest schema can be used for product media assignments. Product media assignment manifests must also include the mandatory fields of the base asset manifest. For information on product media assignments, see [Assign media to products and categories](assign-media-omnichannel.md).

### Schema extension for product media assignments

The following table shows the schema extension for product media assignments.

| Column name                         | Description                                                                                                                  |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| EntityType                          | Product assignment target for this row (for example, Master, Variant, DimensionMatrix, Category).                                     |
| EntityKey                           | Specifies what is used as the key for this assignment in the EntityKeyValue field (for example, ProductNumber, RecordId, CategoryID). |
| EntityKeyValue                      | The value of the key specified in EntityKey.                                                                                  |
| EntityLocale                        | Locale of the product assignment.                                                                                            |
| CatalogNumber                       | Catalog number this assignment is associated with.                                                                           |
| EntityChannel                       | Channel operating unit number (OUN) associated with the assignment.                                                                              |
| EntityAssignmentCurrentPublishState | Publish state of the assignment.                                                                                              |
| EntityAssignmentAction              | PublishNow, Draft, Unpublish, UnpublishAndDelete                                                                             |
| EntityCheckedOutAction              | UseExisting, Overwrite                                                                                                       |
| EntityVersionMismatchAction         | UseExisting, Overwrite                                                                                                       |
| MediaGroup                          | Media group of the asset (Primary/Additional).                                                                                |
| MediaPurpose                        | Purpose of the asset (free text).                                                                                             |
| MediaDisplayOrder                   | Display order.                                                                                                                |
| SwatchGroup                         | Swatch group (for example, Size or Style).                                                                                            |
| SwatchDimension                     | Swatch dimension (for example, M, XL, XXL)                                                                                           |
| SwatchValue                         | Swatch value (hexidecimal code of the color or identity identifier of an image asset).                                                |
| EntityCreatedOn                     | Date and time when the assignment was created.                                                                                |
| EntityLastModifiedOn                | Date and time when the assignment was last modified.                                                                          |
| EntityVersion                       | Assignment version number.                                                                                                    |
| EntityPublishedOn                   | Date and time when the assignment was published.                                                                              |

For more information on swatches, see [Product-specific swatches](assign-media-omnichannel.md#product-specific-swatches). For more information on media groups, please see [Assign media to simple products](assign-media-omnichannel.md#assign-media-to-simple-products).

## Import asset manifests

You can import asset manifests to the site builder media library of any of e-commerce site, or to your omnichannel. Manifests with product media assignments must be imported from the **Product media** view in your omnichannel.

### Bulk import an asset manifest

Manifest-based asset import operations for e-commerce sites are initiated from the site builder media library.

To bulk import an asset manifest in site builder, follow these steps.

1. Go to the site into which you want to import the manifest.
2. Go to **Media library**.
3. Select **Bulk import**. The **Bulk import files** dialog box appears.
4. Under **Import details**, enter a name (required) and a description (optional) for the job, then select **Next**.
5. Under **Select a manifest file for import**, select **browse your computer** to select the manifest file on your your local machine, or drag and drop the manifest file onto the **Drop your file here** box.
6. If the manifest references asset binaries from the local machine, select the **Import using local files from my device** checkbox.
7. Select **Next**. 
8. If you selected the **Import using local files from my device** checkbox above, under **Select a media directory**, select **Browse**, and then select the media directory on your local machine. If you are not importing media assets, proceed to step 11.
9. After selecting the media directory to upload, you may see a confirmation dialog box appear, depending on your browser. After reviewing the message, select **Upload**, **OK**, or **Yes** (depending on your browser). The **Select a media directory** dialog box is then updated showing the folder you selected for upload.
10. Select **Next**.
11. In the **Review and finish** dialog box, review the job settings, and then select **Begin import**.

### Bulk import a product media assignment asset manifest

Manifest-based product media assignment asset import operations are initiated from the media library of your omnichannel. Manifests with product media assignments are imported from the **Product media** view in your omnichannel.

To bulk import a product media assignment asset manifest, follow these steps.

1. Go to the omnichannel for your environment.
2. Select **Product media**.
3. Select **Bulk import**.
4. Under **Import details**, enter a name (required) and a description (optional) for the job, then select **Next**.
5. Under **Select a manifest file for import**, select **browse your computer** to select the product media assignment asset manifest file on your your local machine, or drag and drop the manifest file onto the **Drop your file here** box.
6. If the manifest references asset binaries from the local machine, select the **Import using local files from my device** checkbox.
7. Select **Next**. 
8. If you selected the **Import using local files from my device** checkbox above, under **Select a media directory**, select **Browse**, and then select the media directory on your local machine. If you are not importing media assets, proceed to step 11.
9. After selecting the media directory to upload, you may see a confirmation dialog box appear, depending on your browser. After reviewing the message, select **Upload**, **OK**, or **Yes** (depending on your browser). The **Select a media directory** dialog box is then updated showing the folder you selected for upload.
10. Select **Next**.
11. In the **Review and finish** dialog box, review the job settings, and then select **Begin import**.

## Export asset manifests 

You can export asset manifests from the site builder media library of any of e-commerce site, or from your omnichannel. Manifests with product media assignments must be exported from the **Product media** view in your omnichannel.

### Bulk export an asset manifest

To bulk export an asset manifest, follow these steps.

1.  Go to the site or omnichannel from which you want to export the manifest.
2.  Go to **Media library**.
3.  Select the assets you want to export, and then select **Bulk export**. Alternatively, to export all media assets, select **Export entire library**.
4.  Enter a name and description for the export job, review the selected media, and then select **Export**.

The job status can be monitored from **Site settings \> Jobs**, or by selecting **Go to job** from the job notification.

### Bulk export a product media assignment manifest

To bulk export a product media assignment manifest, follow these steps.

1.  Go to the omnichannel of your environment.
2.  Select **Product media**.
3.  Select **Bulk export**.
4.  Select **Export media assignments for all products** or **Export media assignments for specific products**, and then select **Next**.
5.  If you selected **Export media assignments for specific products**, under **All products**, select the products from which you want to export the media assignments, and then select **Next**. If you selected **Export media assignments for all products**, proceed to step 6.
6.  If you want to export all locales and not just the currently selected locale, select the **Export all locales** checkbox.
7.  Select **Export product media**.

The job status can be monitored from **Site settings \> Jobs**, or by selecting **Go to job** from the job notification.

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Publish media assignments](publish-media-omnichannel.md)

[Copy omnichannel content between tenants](copy-content-between-tenants.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
