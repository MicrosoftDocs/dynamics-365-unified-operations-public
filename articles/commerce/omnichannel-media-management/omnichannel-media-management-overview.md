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
[todo]

#### Primary media, additional media, and product-specific swatches 
[todo]

#### Omnichannel, channel-specific, and locale-specific media assignments
[todo]

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






