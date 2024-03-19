---
title: Bulk import and export digital assets using manifests
description: This article describes how to bulk import and export digital assets by using manifests in Microsoft Dynamics 365 Commerce.
author: psimolin
ms.date: 03/15/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: psimolin
ms.search.validFrom: 2023-03-01

---

# Bulk import and export digital assets using manifests

[!include[banner](../../finance/includes/banner.md)]

This article describes how to bulk import and export digital assets by using manifests in Microsoft Dynamics 365 Commerce site builder. It also describes the manifest schema.

You can perform manifest-based asset import and export operations in the Commerce site builder media library. Manifest-based operations require (during import) or produce (during export) a manifest file. This file is a tab-delimited .tsv text file that lists all assets that are part of the operation. For export operations, the manifest includes all asset information, including read-only metadata that specifies details such as when assets were created and published. For import operations, the manifest has to include only a subset of asset information for each asset. The remaining fields are optional.

When manifest documents are imported, they're processed row by row. If the processing of any row fails for any reason, a description of the error is included in the resulting manifest. You can download that manifest from the job details view (**Site settings \> Jobs**) in site builder. A failure of one of multiple entries in a manifest doesn't prevent the rest of the manifest from being processed. If an error requires that you fix something in a manifest (for example, an incorrect source URL), you can use the resulting manifest from the first run to fix and reprocess the assets that generated errors.

Here are the main use cases for manifest-driven asset import and export operations:

- Uploading product media and other digital assets to the system during onboarding.
- Modifying asset metadata in bulk (for example, adding specific keywords to a large number of assets).
- Performing search and replace operations on the metadata (for example, rebranding).
- Performing actions in bulk (for example, publishing or deleting assets).

## Bulk import and export product media

Manifests can also be used to import and export product media assignments. The schema that's used for product media assignments is an extended version of the plain asset management manifest schema. For information about product media assignments, see [Assign media to products and categories](assign-media-omnichannel.md).

> [!NOTE]
> To use bulk import and export product media assignment features for **Omnichannel (Channel) - Neutral (locale)**, you must configure Commerce headquarters with site builder's application ID. This action is a temporary requirement that will be made unnecessary in a future update.

To configure Commerce headquarters with site builder's application ID, follow these steps:

1. Create a new user account in headquarters by following the instructions in [Manually add a new user](/dynamics365/fin-ops-core/fin-ops/sysadmin/create-new-users#manually-add-a-new-user). The new user account is used by the bulk CMS service to access headquarters product data. The account name can be anything (for example, "Bulk operations user").
1. To assign the quality control manager role to the new user account, follow the instructions in [Manually assign users to roles](/dynamics365/fin-ops-core/fin-ops/sysadmin/assign-users-security-roles#manually-assign-users-to-roles) .

    > [!NOTE]
    > The bulk CMS service only requires read-only privileges to access headquarters product data.

1. In headquarters, search for "entra" and select **Microsoft Entra ID applications** from the search results.
1. On the Action Pane, select **New**.
1. Copy and paste the following site builder application ID GUID into the new record's **Client Id** field: `3530b95b-aca8-4164-b78e-0c07cbfd0681`.
1. For **Name**, enter a friendly name (for example, "CMS Bulk Operations").
1. In the **User Id** field, select the new user.
1. On the Action Pane, select **Save**.

## Manifest schema

Manifest documents are tab-delimited Unicode text files that have a .tsv extension. The first row of the manifest is a header row and contains the column names. Each subsequent row represents a single asset and its associated metadata. For the initial ingestion of an asset, binary files (in other words, actual assets) must be provided along with the manifest. They can be provided either as a local upload or as publicly accessible HTTP source URLs.

After a manifest-based import operation is completed, the imported manifest that includes import results and possible error information can be downloaded from the **Past jobs** tab on the **Site jobs** page (**Site settings \> Jobs**) in site builder. In the schema description that follows, the last four rows describe the error information that's captured and provided.

### Schema for asset import and export operations

The following table shows the schema for asset import and export operations.

| Column name                          | Description |
|--------------------------------------|-------------|
| InternalMediaId                      | The identifier of the asset in the Commerce content management system (CMS). This field must be empty when importing new assets. |
| MediaChannel                         | The name of the e-commerce channel from which the asset is exported, or to which the asset is imported. |
| MediaLocale                          | The locale of the asset. |
| MediaType                            | The type of the asset. Allowed field values are *Image*, *Video*, or *File*. |
| MediaVersion                         | The version number of the asset. In combination with the `MediaVersionMismatchAction` field, you can control import behavior in case the media asset was modified between export and import. |
| MediaCategory                        | The Commerce media category. Allowed field values are *None* (default), *Products*, *Categories*, *Customers*, *Workers*, *Catalogs*, *Size*, *Color*, or *Style*. |
| MediaSourceProvider                  | The external system from which the asset is imported. In combination with the `MediaSourceId` field, this field is used to determine if the asset already exists in the system and if it should be updated. If `MediaSourceProvider` and `MediaSourceId` fields aren't populated, `InternalMediaId`, `MediaChannel`, and `MediaLocale` values are used instead. |
| MediaSourceId                        | The identifier in the external system. |
| MediaReferenceUrl                    | The URL of the external provider (instead of `MediaImportPath`). |
| MediaSourceIfExistsAction            | Import behavior if the media asset already exists in the system. Allowed field values are *UseExisting*, *Overwrite*, *TakeLatest*, or *KeepBoth*. |
| MediaAction                          | Action that should be applied to the asset during manifest import. Allowed field values are *PublishNow*, *Draft*, *Unpublish*, or *UnpublishAndDelete*. |
| MediaCheckedOutAction                | Import behavior if the existing media in the system is checked out for editing. Allowed field values are *UseExisting* or *Overwrite*. |
| MediaVersionMismatchAction           | Import behavior if the existing media in the system has been updated (version differs) between the export and import of the manifest. Allowed field values are *UseExisting* or *Overwrite*. |
| MediaImportPath                      | Either the HTTP source URL or the file name. Media assets are imported from this location, either via local file upload or the system fetching the media asset binary from a publicly accessible external web location). |
| ImageAltText                         | Alt text for an image asset. |
| MediaSearchTags                      | Keywords that describe the asset (comma separated). |
| MediaCaption                         | The caption for a video asset. |
| MediaDisplayName                     | The display name of the asset. The value must be unique within a site. |
| MediaDescription                     | A description of a video asset. |
| VideoCaptionImportPath               | Publicly accessible HTTP source URL of the captions for a video asset. |
| VideoThumbnailImportPath             | Publicly accessible HTTP source URL of the thumbnail for a video asset. If none is specified, the source URL is generated automatically. |
| VideoTranscriptImportPath            | Publicly accessible HTTP source URL of the transcript for a video asset. |
| VideoAudioTrackImportPath            | Publicly accessible HTTP source URL of the additional audio track for a video asset. |
| VideoDescriptiveAudioTrackImportPath | Publicly accessible HTTP source URL of the descriptive audio track for a video asset. |
| VideoPlaytime                        | The playtime of a video asset (in seconds). |
| MediaCreatedOn                       | The date and time when the asset was created. |
| MediaLastModifiedOn                  | The date and time when the asset was last modified. |
| MediaPublished                       | A *true*/*false* value that specifies whether the asset is published. |
| MediaPublishedOn                     | The date and time when the asset was published. |
| MediaPublishedURL                    | The URL of the published asset. |
| MediaPreviewURL                      | The preview URL for the asset (requires sign-in). |
| ImageQuality                         | Estimated quality of an image asset. |
| ImageWidth                           | The width of an image asset. |
| ImageHeight                          | The height of an image asset. |
| MediaChecksum                        | The hash (checksum) of an image asset binary. |
| MediaTitle                           | The title of a video asset. |
| VideoSubtitle                        | The URL of the subtitles for a video asset. |
| VideoMinimumAge                      | The minimum age for a video asset. |
| DocumentForceDownload                | A value that specifies whether a file asset should be downloaded instead of viewed. |
| Result                               | The result of the import operation for the current row. |
| ResultTime                           | The time when the current row was processed. |
| ErrorCode                            | An error code. |
| ResultDescription                    | A detailed description of the result (for example, an error description). |

You can use the `MediaSourceProvider` and `MediaSourceId` fields to indicate the external source and ID of the media asset (for example, an external CMS). If `MediaSourceProvider` and `MediaSourceId` values are provided, they're used to determine if the same assets were imported earlier and should be updated. If `MediaSourceProvider` and `MediaSourceId` values aren't available, `InternalMediaId`, `MediaChannel`, and `MediaLocale` values are used to match media assets being imported to media assets already present in the system.

Most of the fields described above are optional in the manifest and can be left out completely, including from the header.

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

The columns in an import manifest can be in any order, as long as data is aligned with the header. Export manifests always contain all available fields for assets. The available fields depend on the asset type.

The same manifest schema can be used for product media assignments. Product media assignment manifests must also include the mandatory fields of the base asset manifest. For information about product media assignments, see [Assign media to products and categories](assign-media-omnichannel.md).

### Schema extension for product media assignments

The following table shows the schema extension for product media assignments.

| Column name                         | Description |
|-------------------------------------|-------------|
| EntityType                          | The product assignment target for the current row. Supported values are `Product\|Master`, `Product\|Variant`, `Product\|DimensionMatrix`, and `Product\|Master\|Swatch`. |
| EntityKey                           | A value that specifies what's used as the key for the assignment in the `EntityKeyValue` field. Supported values are `EntityId`, and `EntityId\|DimensionMatrix`, `EntityId\|SwatchType\|SwatchId`. |
| EntityKeyValue                      | The value of the key that's specified in `EntityKey`. For `DimensionMatrix`, the dimensions are pipe delimited and the keys are separated from the values using colons. |
| EntityLocale                        | The locale of the product assignment (for example, "en-us", "de-de", or "system_neutral" for locale agnostic). |
| CatalogNumber                       | The catalog number that the assignment is associated with. |
| EntityChannel                       | The channel operating unit number (OUN) that's associated with the assignment. Must be prefixed with "OUN" (for example, OUN007, OUN116, etc.) |
| EntityAssignmentCurrentPublishState | The publish state of the assignment. |
| EntityAssignmentAction              | Action that should be applied on the product media assignment during manifest import. Allowed field values are *PublishNow*, *Draft*, *Unpublish*, or *UnpublishAndDelete*. |
| EntityCheckedOutAction              | Import behavior if the product media assignment is checked out for editing. Allowed field values are *UseExisting* or *Overwrite*. |
| EntityVersionMismatchAction         | Import behavior if the existing product media assignment in the system was updated (version differs) between the export and import of the manifest. Allowed field values are *UseExisting* or *Overwrite*. |
| MediaGroup                          | The media group of the asset. Allowed field values are *Primary* or *Additional*. |
| MediaPurpose                        | The purpose of the asset (free text). |
| MediaDisplayOrder                   | The display order. |
| SwatchGroup                         | The swatch group (for example, *Size* or *Style*). |
| SwatchDimension                     | The swatch dimension (for example, *M*, *XL*, or *XXL*). |
| SwatchValue                         | The swatch value (the hexadecimal code of the color or the identity identifier of an image asset). |
| EntityCreatedOn                     | The date and time when the assignment was created. |
| EntityLastModifiedOn                | The date and time when the assignment was last modified. |
| EntityVersion                       | The assignment version number. |
| EntityPublishedOn                   | The date and time when the assignment was published. |

For more information about swatches, see [Product-specific swatches](assign-media-omnichannel.md#product-specific-swatches). For more information about media groups, see [Assign media to simple products](assign-media-omnichannel.md#assign-media-to-simple-products).

## Import asset manifests

You can import asset manifests into the site builder media library of your e-commerce site or omnichannel. Manifests that include product media assignments must be imported from the **Product media** view in your omnichannel.

### Bulk import an asset manifest

Manifest-based asset import operations for e-commerce sites are initiated from the site builder media library.

To bulk import an asset manifest into site builder, follow these steps.

1. In site builder, go to the site that you want to import the manifest into.
1. Go to **Media library**.
1. Select **Bulk import**. The **Bulk import files** dialog box appears.
1. Under **Import details**, enter a name (required) and a description (optional) for the job, and then select **Next**.
1. Under **Select a manifest file for import**, select **browse your computer** to select the manifest file on your local machine, or drag the manifest file onto the **Drop your file here** box.
1. If the manifest references asset binaries from your local machine, select the **Import using local files from my device** checkbox.
1. Select **Next**. 
1. If you selected the **Import using local files from my device** checkbox earlier, under **Select a media directory**, select **Browse**, and then select the media directory on your local machine. If you aren't importing media assets, skip ahead to step 11.
1. After you select the media directory to upload, a confirmation message box might appear, depending on your browser. Review the message, and then select **Upload**, **OK**, or **Yes** (depending on your browser). The **Select a media directory** dialog box is then updated and shows the folder that you selected for upload.
1. Select **Next**.
1. In the **Review and finish** dialog box, review the job settings, and then select **Begin import**.

### Bulk import a product media assignment asset manifest

Manifest-based product media assignment asset import operations are initiated from the media library of your omnichannel. Manifests that include product media assignments are imported from the **Product media** view in your omnichannel.

To bulk import a product media assignment asset manifest, follow these steps.

1. In site builder, go to the omnichannel for your environment.
1. Select **Product media**.
1. Select **Bulk import**.
1. Under **Import details**, enter a name (required) and a description (optional) for the job, and then select **Next**.
1. Under **Select a manifest file for import**, select **browse your computer** to select the product media assignment asset manifest file on your local machine, or drag the manifest file onto the **Drop your file here** box.
1. If the manifest references asset binaries from your local machine, select the **Import using local files from my device** checkbox.
1. Select **Next**. 
1. If you selected the **Import using local files from my device** checkbox earlier, under **Select a media directory**, select **Browse**, and then select the media directory on your local machine. If you aren't importing media assets, skip ahead to step 11.
1. After you select the media directory to upload, a confirmation message box might appear, depending on your browser. Review the message, and then select **Upload**, **OK**, or **Yes** (depending on your browser). The **Select a media directory** dialog box is then updated and shows the folder that you selected for upload.
1. Select **Next**.
1. In the **Review and finish** dialog box, review the job settings, and then select **Begin import**.

## Export asset manifests 

You can export asset manifests from the site builder media library of your e-commerce site or omnichannel. Manifests that include product media assignments must be exported from the **Product media** view in your omnichannel.

### Bulk export an asset manifest

To bulk export an asset manifest, follow these steps.

1. In site builder, go to the site or omnichannel that you want to export the manifest from.
1. Go to **Media library**.
1. Select the assets that you want to export, and then select **Bulk export**. Alternatively, to export all media assets, select **Export entire library**.
1. Enter a name and description for the export job, review the selected media, and then select **Export**.

You can monitor the job status at **Site settings \> Jobs** or by selecting **Go to job** in the job notification.

### Bulk export a product media assignment manifest

To bulk export a product media assignment manifest, follow these steps.

1. In site builder, go to the omnichannel of your environment.
1. Select **Product media**.
1. Select **Bulk export**.
1. Select **Export media assignments for all products** or **Export media assignments for specific products**, and then select **Next**.
1. If you selected **Export media assignments for specific products**, under **All products**, select the products that you want to export the media assignments from, and then select **Next**. If you selected **Export media assignments for all products**, skip ahead to step 6.
1. If you want to export all locales, not just the currently selected locale, select the **Export all locales** checkbox.
1. Select **Export product media**.

You can monitor the job status at **Site settings \> Jobs** or by selecting **Go to job** in the job notification.

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Publish media assignments](publish-media-omnichannel.md)

[Copy omnichannel content between tenants](copy-content-between-tenants.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
