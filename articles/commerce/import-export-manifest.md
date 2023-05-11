---
title: Bulk import and export of digital assets using manifests
description: This article describes how to bulk import and export digital assets using manifests in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 5/11/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: psimolin
ms.search.validFrom: 2023-03-01

---

# Bulk import and export of digital assets using manifests

[!include[banner](../includes/banner.md)]

This article describes how to bulk import and export digital assets using manifests in Microsoft Dynamics 365 Commerce.

This article provides an overview of the manifest based asset import and export operations in the Microsoft Dynamics 365 Commerce site builder, describes the schema of the manifest and provides detailed examples of both import and export operations.

Manifest based asset import and export operations are initiated from the media library of the site builder. Import operation can be started by clicking "Bulk import" from the command bar. \[LINK TO MANIFEST IMPORT\] Export operation is started by selecting one or more assets and clicking "Bulk export" from the command bar. \[LINK TO MANIFEST EXPORT\]

Manifest based operations always require (import) or produce (export) a manifest file, which is a tab limited text file listing all the assets that are part of that operation. \[LINK TO MANIFEST SCHEMA\] In the case of export operations, all the information of the assets is included in the manifest, including read-only metadata information such as when the asset was created and published. Import operations only require some of the fields to be entered for each asset and the rest are optional.

When imported, manifests documents are processed row by row and if processing of any of the rows fails for any reason, the description of the error is included in the resulting manifest which can be downloaded from the job details view. If one of multiple entries in the manifest fails, it does not prevent the rest of the manifest to be processed. If the error requires user to fix something, for example, if the http source url was incorrect in the first import and it is fixed now, the result manifest from the first run can be used to reprocess the failed assets.

Main use cases for manifest driven asset import and export operations are:

-   Uploading product media and other digital assets to the system during onboarding
-   Modifying asset metadata in bulk (e.g. adding specific keyword to large number of assets)
-   Performing search and replace operations on the metadata (e.g. rebranding)
-   Performing actions (e.g. publish, delete) in bulk

Manifests can also be used to import and export product media assignments. The schema used for product media assignments is an extended version of the plain asset management manifest schema. Product media assignments are explained in more detail in \[LINK TO NICK – PRODUCT MEDIA ASSIGNMENTS\]

More details and examples can be found from \[LINK TO MANIFEST IMPORT\] and \[LINK TO MANIFEST EXPORT\]

## Manifest schema

Manifest documents are tab delimited unicode text files. First row of the manifest is a header row and contains the column names. After the header row, each row represents a single asset and its metadata. For initial ingestion of an asset, binary files (actual assets) have to be provided along with the manifest either as a local upload or as publicly accessible http source urls.

After the manifest based import operation has completed, the imported manifest with import results and possible error information can be downloaded from "Jobs" menu and the "Past jobs" tab. Please see the four last rows in the schema description below for more information.

![A screenshot of a computer Description automatically generated with medium confidence](media/image1.png)

Schema for asset import / export

| Column name                          | Description                                                |
|--------------------------------------|------------------------------------------------------------|
| InternalMediaId                      | Commerce CMS asset identity identifier                     |
| MediaChannel                         | Name of the channel where the asset is exported from       |
| MediaLocale                          | Locale of the asset                                        |
| MediaType                            | Type of the asset                                          |
| MediaVersion                         | Version number of the asset                                |
| MediaCategory                        | Commerce media category                                    |
| MediaSourceProvider                  | External system the asset is being imported from           |
| MediaSourceId                        | Identifier in the external system                          |
| MediaReferenceUrl                    | Url to external provider (instead of MediaImportPath)      |
| MediaSourceIfExistsAction            | UseExisting, Overwrite, TakeLatest or KeepBoth             |
| MediaAction                          | PublishNow, Draft, Unpublish, UnpublishAndDelete           |
| MediaCheckedOutAction                | UseExisting, Overwrite                                     |
| MediaVersionMismatchAction           | UseExisting, Overwrite                                     |
| MediaImportPath                      | Either http source url or filename                         |
| ImageAltText                         | Alt text for an image asset                                |
| MediaSearchTags                      | Keywords describing the asset (comma separated)            |
| MediaCaption                         | Caption of the asset (video asset)                         |
| MediaDisplayName                     | Display name of the asset (unique within a site)           |
| MediaDescription                     | Description of the asset (video asset)                     |
| VideoCaptionImportPath               | Url to captions of video asset                             |
| VideoThumbnailImportPath             | Url to thumbnail of video asset (otherwise generated)      |
| VideoTranscriptImportPath            | Url to transcript of video asset                           |
| VideoAudioTrackImportPath            | Url to additional audio track for video asset              |
| VideoDescriptiveAudioTrackImportPath | Url to descriptive audio track for video asset             |
| VideoPlaytime                        | Playtime of video asset (seconds)                          |
| MediaCreatedOn                       | Date and time when the asset was created                   |
| MediaLastModifiedOn                  | Date and time when the asset was last modified             |
| MediaPublished                       | Has the asset been published (true/false)                  |
| MediaPublishedOn                     | Date and time when the asset was published                 |
| MediaPublishedURL                    | Url to published asset                                     |
| MediaPreviewURL                      | Preview url to asset (requires login)                      |
| ImageQuality                         | Quality% of the image asset                                |
| ImageWidth                           | Width of the image asset                                   |
| ImageHeight                          | Height of the image asset                                  |
| MediaChecksum                        | Hash of the image asset binary                             |
| MediaTitle                           | Title of the asset (video asset)                           |
| VideoSubtitle                        | Url to subtitles for video asset                           |
| VideoMinimumAge                      | Minimum age for video asset                                |
| DocumentForceDownload                | Force the download of file asset (instead of viewing)      |
| Result                               | Result of the import operation for this row                |
| ResultTime                           | Time when this row was processed                           |
| ErrorCode                            | Error code                                                 |
| ResultDescription                    | Detailed description of the result, e.g. error description |

Sample asset manifests (Urls redacted/removed)

Sample manifests have all been exported from an environment. They could be imported back (to that same environment) or imported to another environment after clearing the InternalMediaId, MediaChannel and MediaVersion fields.

Mandatory fields for manifest import (for new asset)

-   MediaLocale

-   MediaType

-   MediaImportPath

-   ImageAltText (for image assets)

-   MediaDisplayName

-   MediaTitle (for video assets)

Mandatory fields for manifest import (for existing asset)

-   InternalMediaId

-   MediaChannel

-   MediaLocale

-   MediaType

-   ImageAltText (for image assets)

-   MediaDisplayName

-   MediaTitle (for video assets)

Columns can be in any order in the import manifest.

Export manifests will always contain all available fields for assets (depending on the asset type).

The same manifest schema can be used for product media assignment. For more information on product media assignments in general, please see \[LINK TO NICK – PRODUCT MEDIA ASSIGNMENTS\]

Please note, that the product media assignment manifests must include the mandatory fields of the base asset manifest as well.

Schema extension for product media assignments

| Column name                         | Description                                                                                                                  |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| EntityType                          | Product assignment target for this row (e.g. Master, Variant, DimensionMatrix, Category)                                     |
| EntityKey                           | Specifies what is used as the key for this assignment in the EntityKeyValue field (e.g. ProductNumber, RecordId, CategoryID) |
| EntityKeyValue                      | The value of the key specified in EntityKey                                                                                  |
| EntityLocale                        | Locale of the product assignment                                                                                             |
| CatalogNumber                       | Catalog number this assignment is associated with                                                                            |
| EntityChannel                       | Channel OUN this assignment is associated with                                                                               |
| EntityAssignmentCurrentPublishState | Publish state of the assignment                                                                                              |
| EntityAssignmentAction              | PublishNow, Draft, Unpublish, UnpublishAndDelete                                                                             |
| EntityCheckedOutAction              | UseExisting, Overwrite                                                                                                       |
| EntityVersionMismatchAction         | UseExisting, Overwrite                                                                                                       |
| MediaGroup                          | Media group of the asset (Primary/Additional)                                                                                |
| MediaPurpose                        | Purpose of the asset (free-text)                                                                                             |
| MediaDisplayOrder                   | Display order                                                                                                                |
| SwatchGroup                         | Swatch group (e.g. Size or Style)                                                                                            |
| SwatchDimension                     | Swatch dimension (e.g. M, XL, XXL)                                                                                           |
| SwatchValue                         | Swatch value (Hex code of the color or identity identifier of an image asset)                                                |
| EntityCreatedOn                     | Date and time when the assignment was created                                                                                |
| EntityLastModifiedOn                | Date and time when the assignment was last modified                                                                          |
| EntityVersion                       | Assignment version number                                                                                                    |
| EntityPublishedOn                   | Date and time when the assignment was published                                                                              |

For more information on swatches, please see \[LINK TO NICK – PRODUCT-SPECIFIC SWATCHES\]

For more information on media groups, please see \[LINK TO NICK – ASSIGN MEDIA TO SIMPLE PRODUCTS\]

## Import assets manifests 

Manifest based asset import operation targeting regular site is started from the media library in the commerce site builder by clicking "Bulk import" from the command bar.

![A screenshot of a computer Description automatically generated with low confidence](media/image2.png)

Bulk import dialog is opened where the import job name and description can be modified. Job name is required, but the description is optional.

![A screenshot of a computer Description automatically generated with medium confidence](media/image3.png)These values don't have an impact on the actual import process, but they help users locate their job from the list of jobs. After entering name and description, clicking "Next" brings up the manifest selection view. Manifest file needs to be tab delimited text file, with a header row with specific column names and one or more rows of assets. \[LINK TO MANIFEST SCHEMA\] Manifest file will be uploaded from the local machine either by selecting "browse your computer" or dragging the file into the view from file explorer of the operating system.

![A screenshot of a computer Description automatically generated with medium confidence](media/image4.png)

After selecting the manifest file, you need to specify if you need to upload local binaries with the manifest. This is not required if all of the assets in the manifest have source http url or they are existing assets and are updating metadata only.

![A screenshot of a computer Description automatically generated with medium confidence](media/image5.png)

If you have new assets that you will be uploading from your local machine, tick the "Import using local files from my device"-box. Proceed to the next step with "Next".

![A screenshot of a computer Description automatically generated with medium confidence](media/image6.png)

This step is shown only if you indicated that you will be importing assets from local machine. Click "Browse" and select the folder that contains the assets that are associated with the manifest.

![A screenshot of a computer Description automatically generated with medium confidence](media/image7.png)

After selecting the folder, you might see a confirmation dialogue that varies depending on the browser you are using. After reviewing the message, confirm by clicking "Upload" (could be "OK", "Yes" or something similar on depending on your browser).

![A screenshot of a computer Description automatically generated with low confidence](media/image8.png)

The view is updated with the folder that you selected. Clicking "Next" takes you to the next step of the process.

![A screenshot of a computer Description automatically generated with medium confidence](media/image9.png)

In the "Review and finish" step, you have all the information for the new bulk import job in the single view you to review. If you need to change any of the parameters, clicking "Edit" next to the information allows you to do that. Clicking "Begin import" will first upload the local files to the service (if selected) and then create a job for the bulk import.

![A screenshot of a computer Description automatically generated with medium confidence](media/image10.png)

The local file upload may take time, depending on the amount and the file size of the asset and your network connection.

![A screenshot of a computer Description automatically generated with medium confidence](media/image11.png)

After the local file upload is completed, manifest import job is created on your site. You can view your job and its progress by clicking "Go to job" from the notification, "-&gt; Go to job" from the view or by navigating to "Site settings" and "Jobs".

![A screenshot of a computer Description automatically generated with medium confidence](media/image12.png)

By locating and selecting your job from the list of current jobs, you can view details for the job in the inspector pane to the right. After the job has been processed it will be moved to "Past jobs" and the result manifest will become available for download.

![A screenshot of a computer Description automatically generated with medium confidence](media/image13.png)

Manifest based asset import operation targeting omnichannel should be started from the media library of the omnichannel. Otherwise the steps are the same.

Manifests with product media assignments should be imported from the "Product media" view in your omnichannel.

To bulk import an asset manifest, follow these steps.

1.  Navigate to the Omnichannel of your environment.
2.  Click "Product media"
3.  Click "Bulk import"
4.  Enter name and description for the job, then click "Next"
5.  Select the manifest file either by browsing your computer or dragging the manifest file to the view
6.  If the manifest references asset binaries from the local machine, check the box "Import using local files from my device"
7.  Click "Next". Select media directory from your computer and proceed to next step (this applies only if you checked the box in previous step)
8.  Review the job settings and click "Begin import"

## Export assets manifests 

Asset manifests can be exported from the media library of any of the sites or the omnichannel. Manifest with product media assignments must be exported from the "Product media" view in your omnichannel.

To bulk export an asset manifest, follow these steps.

1.  Navigate to the site or omnichannel you want to export the manifest from
2.  Go to "Media library"
3.  Select the assets you would like to export and click "Bulk export" (or "Export entire library")
4.  Enter name and description for the export job, review the selected media and click "Export"

The job status can be monitored from "Site settings" -&gt; "Jobs" or by clicking "Go to job" from the notification.

To bulk export a product assignment manifest, follow these steps.

1.  Navigate to the omnichannel of your environment
2.  Click "Product media"
3.  Click "Bulk export"
4.  Select if you like to export media assignments "for all products" or "for specific products", click "Next"
5.  If you selected "specific products" you will be presented with a view where you can select the products you want to export the media assignments for. After selecting the products, click "Next"
6.  If you wish to export all locales and not just the currently selected locale, check the box "Export all locales"
7.  Click "Export product media"

The job status can be monitored from "Site settings" -&gt; "Jobs" or by clicking "Go to job" from the notification.


### Sample product media assignment manifests (Urls redacted/removed)

Links to download center URLs TBD
