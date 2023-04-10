---
title: Omnichannel media managment overview
description: This article covers omnichannel media managment topics for Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 2/1/2023
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: 
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 
ms.dyn365.ops.version: Release 10.0.34
ms.search.industry: 
ms.search.form: 
---

# Omnichannel media management overview
Starting with version 10.0.35, **Dynamics 365 Commerce** introduces an integrated solution for managing merchandising media. It is now easy to assign images and other media to products, product dimensions, and variants. Media assignments are no longer based on legacy filenames, allowing for the reuse of a single media asset for multiple merchandising entities. Specific product dimensions can be assigned media while ignoring unnecessary ones (example: a shirt product with size, color, and style dimensions can assign media to color + style dimension combinations, while ignoring size dimension media assignments).  Additionally, large sets of media assignments and metadata can be managed through bulk export and import using manifest files (.TSV format). The solution integrates media management capabilities into the **Commerce headquarters (HQ)** merchandising flow, and introduces a new omnichannel content workspace within **Commerce site builder**. All omnichannel media management capabilities introduced in 10.0.35+ are currently opt-in through feature flags. New implementations are encouraged to use this capability by default, while existing solutions may opt-in on their own preferred timeline by following the documented migration steps. With these capabilities, **Dynamics 365 Commerce** now offers a more flexible native solution for managing merchandising media.

# Omnichannel media management quick links
[todo]

# Omnichannel media management how-to guides
## Product media assignments
The following topics cover the steps to author and assign media to products.  
> [!NOTE]
> The following how-to guide assumes that the [**Omnichannel media management prerequisites and configuration**](#omnichannel-media-management-prerequisites-and-configuration) steps have already been followed to enable this feature for your environment.

### Assign media to simple products
For simple products, there are three media assignment scopes available: **Primary media**, **Additional media**, and product-specific **Swatches**.

### Primary media
**Primary media** is used for media assignments that should always display in a product's media gallery UX (examples: Point of Sale media gallery, e-Commerce PDP media gallery, etc.).  Media items in **Primary media** have a specific display order, and can be re-arranged using the **Up** or **Down** arrow buttons on each media item or by dragging and dropping them to the correct position.  The highest ordered image in the **Primary media** assignments is treated as the product's default image for scenarios where the entire media gallery experience is not needed.
> [!NOTE]
> The default image returned by core data-action APIs (example: get-simple-products) for UX scenarios like category pages, search results, or any other list view, will be the highest ordered media item in the **Primary media** assignments that is an image (example: any media item that is not an image will be skipped over, and the first image found in the **Primary media** ordered assignments will be returned as the default image for the product).

To assign media to a product's **Primary media**, follow these steps:
1. Navigate to the **Product media** assignments view in either **site builder's** **Omnichannel content** workspace, or to the same view in **Commerce Headquarters (HQ)** via the **Product media assignments** button in the released products by category view.
2. Search for a product using its name or product ID in the search view on the left, and select it.
3. Click the **Edit product media** button in the upper right.
4. Click the **Add media** button in the Master > **Primary media** section.  
5. Select one or more media items from the media library picker (you can also upload new images here with the **Upload** button in the upper left of the media picker), then click **Apply**.
6. Use the up and down arrows, or drag and drop, to reorder the media in the **Primary media** assignments.
7. Click **Finish editing** in the upper right to check in your changes (this will not publish your edits, but will allow others within your organization to see staged changes and make additional edits prior to publish). 

### Additional media
**Additional media** is used for media assignments that have other purposes outside of a standard product media gallery.  **Additional media** items have a property named **Purpose** that indicates its inteded use.  Typical **Additional media** purposes include product manuals, spec sheets, media kits, or any other custom media assignment purpose needed outside of the primary media gallery.  The list of media purposes is extensible and can be defined and expanded using the Commerce SDKs.

### Product-specific swatches
[Todo]

### Omnichannel, channel-specific, and locale-specific media assignments
Media can be assigned in a hierarchical fallback manner accross channels and locales.  The default assignment for any product should use Omnichannel (channel) and Neutral (locale).  These assignments will be returned by default anywhere a more specific channel+local combination is not available.  For channel+locale combinations that require different product media assignments than the default Omnichannel+Neutral assignments, specific channel+locale media assignments can be configured to override the default.  After a specific channel+locale media assignment for a product is created and published, the inheritance to the omnichannel combination is severed and all media assignments are controlled by the specific channel+locale media assignments.

Here is the basic fallback for channel and locale media assignments:
```mermaid
  flowchart LR;
      A[fa:fa-globe Client UX channel+locale]-->|request| B("Specific channel+locale (exact match)")
      B-->|if not found| C("Omnichannel+language_id (language-only match)")
      C-->|if not found| D("Omnichannel+Neutral (default)");
```

### Assign media to master products
[todo]

#### Assign media to product dimensions
[todo]

#### Assign media to product variants
[todo]

### Previewing media assignments
[todo]

### Publishing media assignments
[todo]

#### Using publish groups for media assignments
[todo]

## Category media assignments
[todo]

## Bulk import and export of media assignments
[todo: Link to Petri's documentation]

## Omnichannel content copy between tenants
[todo]

# Omnichannel media management prerequisites and configuration
[todo]

# Omnichannel media management concepts and data model
[todo]

## Overview of media assignment hierarchy
[todo]

## Omnichannel media architecture and dataflow
[Describe new management UX interfaces (HQ, Omnichannel content library)
[Diagram of dataflows between UX -> CMS -> HQ -> CSU -> Frontend/POS]

Mermaid example [to be deleted]
```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```
[todo]

# Omnichannel media management prerequisites and configuration
[todo]

# Migrating legacy product media libraries to 10.0.35+ omnichannel media management data model
[todo]

# Omnichannel merchandising media extensibility
[todo]

## e-Commerce merchandising media modules
[todo]

### e-Commerce module scenarios for primary media
[todo]

### e-Commerce module scenarios for additional media
[todo]

## Omnichannel media data actions and APIs
[todo]






