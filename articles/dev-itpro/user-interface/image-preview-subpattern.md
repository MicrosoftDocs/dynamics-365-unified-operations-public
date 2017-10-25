---
# required metadata

title: Image Preview subpattern
description: This article provides information about the Image Preview form subpattern. This subpattern can be used for most images that appear within a form container, especially within a FastTab or Group. 
author: jasongre
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 12444
ms.assetid: ac176ec7-7f14-47b8-908c-d2175a29fc5c
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Image Preview subpattern

[!include[banner](../includes/banner.md)]


This article provides information about the Image Preview form subpattern. This subpattern can be used for most images that appear within a form container, especially within a FastTab or Group. 

Usage
-----

Image Preview can be used for most images that appear within a form container, especially within a FastTab or Group. This subpattern can be used in conjunction with the FieldsAndFieldGroup and FillText subpatterns to combine images and any associated fields. This subpattern isn't used for tiles or buttons, or for field status images.

### Typical contents

-   Toolbar (ActionPane where **Style**=**Strip**)
-   Image
-   Can contain subpatterns:
    -   Fields and Field Groups
    -   Fill text

## Wireframe
[![ImagePreview(1)](./media/imagepreview1.png)](./media/imagepreview1.png)

## Pattern changes
Here are the main changes to this pattern since Microsoft Dynamics AX 2012:

-   Fields are to the right of the image, if there are any fields.
-   An ActionPane above the image can be used for associated actions (for example, Upload and Select).

## Model
### Image only – High-level structure

- \[Container\] (Columns = Fixed – 1)

    - *Toolbar (ActionPane) \[Optional\]*
    - Image

### Image and fields – High-level structure

- \[Container\] (Columns = Fixed – 1)

    - *Toolbar (ActionPane) \[Optional\]*
    - Image
    - Group

        - Image
        - Group - Note: uses a fields subpattern

### Core components

-   Apply the Image Preview subpattern to the container control.
-   Address BP Warnings:
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

### Related container patterns

-   [Fields and Field Groups](fields-field-groups-subpattern.md)
-   [Fill Text](fill-text-subpattern.md)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with the UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Image Preview guidelines:**
    -   Any fields should be placed to the right of the image.

## Examples
Form: **RetailVisualProfile** **(Login)** 

[![ImagePreview(2)](./media/imagepreview2.png)](./media/imagepreview2.png)

## Resources
### Typically used by patterns

-   [Details Master](details-master-form-pattern.md)
-   [Details Transaction](details-transaction-form-pattern.md)
-   [Simple Details](simple-details-form-pattern.md)
-   [Simple List and Details](simple-list-details-form-pattern.md)
-   [Table of Contents](table-of-contents-form-pattern.md)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None.

### AX 2012 content

[![ImagePreview(3)](./media/imagepreview3.png)](./media/imagepreview3.png)
