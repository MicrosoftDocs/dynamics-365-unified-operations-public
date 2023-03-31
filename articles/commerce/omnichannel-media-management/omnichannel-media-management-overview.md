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

# Omnichannel media managment overview
Starting with version 10.0.35, **Dynamics 365 Commerce** introduces an integrated solution for managing merchandising media. It is now easy to assign images and other media to products, product dimensions, and variants. Media assignments are no longer based on legacy filenames, allowing for the reuse of a single media asset for multiple merchandising entities. Specific product dimensions can be assigned media while ignoring unnecessary ones (example: a shirt product with size, color, and style dimensions can assign media to color + style dimension combinations, while ignoring size dimension media assignments).  Additionally, large sets of media assignments and metadata can be managed through bulk export and import using manifest files (.TSV format). The solution integrates media management capabilities into the **Commerce headquarters (HQ)** merchandising flow, and introduces a new omnichannel content workspace within **Commerce site builder**. All omnichannel media management capabilities introduced in 10.0.35+ are opt-in through feature flags. New implementations are encouraged to use this capability by default, while existing solutions may opt-in on their own preferred timeline by following the documented migration steps. With these capabilities, **Dynamics 365 Commerce** now offers a powerful and flexible native solution for managing merchandising media.

## "Hello world" media managment tutorial

## How it works
[Describe new managment UX interfaces (HQ, Omnichannel content library)
[Diagram of dataflows between UX -> CMS -> HQ -> CSU -> Frontend/POS]

Mermaid example [to be deleted]
```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```

## Enabling omnichannel media managment features
[Tactical steps and best practices to enable this feature accross dev/uat/prod environments]

## Omnichannel media managment core topics
### Media assignment fallback hierarchies
#### Channel and locale media assignments
#### Product dimension media assignments
#### Product variant media assignments
### "Additional media" assignments
### Product-level swatch assignments


## Bulk import and export of merchandising media

## Using publish groups with merchandising media
### Publishing and unpublishing media assignments

## Migrating an existing environment [separate article?]




