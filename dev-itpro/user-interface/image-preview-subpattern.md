---
# required metadata

title: Image Preview subpattern | Microsoft Docs
description: This article provides information about the Image Preview form subpattern. This subpattern can be used for most images that appear within a form container, especially within a FastTab or Group. 
author: jasongre
manager: AnnBe
ms.date: 2015-11-04 20:50:00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 12444
ms.assetid: 809ad369-9637-4519-bf56-ba816eb2e7fa
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Image Preview subpattern

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

\[Container\] (Columns = Fixed – 1)

*Toolbar (ActionPane) \[Optional\]*

Image

### Image and fields – High-level structure

\[Container\] (Columns = Fixed – 1)

*Toolbar (ActionPane) \[Optional\]*

Image

Group

            Image

            Group - Note: uses a fields subpattern

### Core components

-   Apply the Image Preview subpattern to the container control.
-   Address BP Warnings:
    -   No additional BP checks are required beyond the AX6.3 BP checks that were carried forward.

### Related container patterns

-   [Fields and Field Groups](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fields-and-field-groups-subpattern)
-   [Fill Text](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/fill-text-subpattern)

## UX guidelines
The verification checklist shows the steps for manually verifying that the form complies with the UX guidelines. This checklist doesn't include any guidelines that will be enforced automatically through the development environment. Open the form in a browser, and walk through these steps.

-   **Image Preview guidelines:**
    -   Any fields should be placed to the right of the image.

## Examples
Form: **RetailVisualProfile** **(Login)** [![ImagePreview(2)](./media/imagepreview2.png)](./media/imagepreview2.png)

## Resources
### Typically used by patterns

-   [Details Master](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-master-form-pattern)
-   [Details Transaction](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/details-transaction-form-pattern)
-   [Simple Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-details-form-pattern)
-   [Simple List and Details](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/simple-list-and-details-form-pattern)
-   [Table of Contents](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/table-of-contents-form-pattern)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None.

### AX 2012 content

[![ImagePreview(3)](./media/imagepreview3.png)](./media/imagepreview3.png)

