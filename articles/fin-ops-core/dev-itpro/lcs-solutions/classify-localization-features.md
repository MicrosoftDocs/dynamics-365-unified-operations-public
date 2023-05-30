---
title: Classification of localization features
description: This article explains the difference between regulatory and competitive feature and shows how the feature type is used in the title of the feature.
author: kfend
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: kfend
ms.search.region: global
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 7e2031b4-a092-482e-a76d-1e582edecd86
---

# Classification of localization features

[!include [banner](../includes/banner.md)]

As part of the requirements for LCS solutions for localization and translation, localization features must be classified as either regulatory or competitive in the business process modeler (BPM) library in Microsoft Dynamics Lifecycle Services (LCS). This article explains the difference between these two types of feature and shows how the feature type is used in the title of the feature.

Localization features must be classified as either regulatory or competitive in the Business process modeler (BPM) library in Microsoft Dynamics Lifecycle Services (LCS). The following definitions will help you distinguish the two types of features:

-   **Regulatory features** – Organizations that do business in a particular country/region must comply with country/region-specific laws and regulations as they handle their daily business transactions and operations, and meet their legal obligations for activities that are conducted in that country/region. These laws and regulations are enforced, and non-adherence can lead to severe consequences for an organization that does business in that country/region.
-   **Competitive features** – This category includes all other features that aren't considered regulatory features according to the preceding definition.

When the BPM library is constructed, the various feature types should be distinguished through the title of the localization solution feature. The label for this title will conform to the following naming convention that indicates the country/region and feature type through prefixes, as shown in the following table.

| Feature type | Format                | Example                             |
|--------------|-----------------------|-------------------------------------|
| Regulatory   | XX-REG-Feature title  | PT-REG-Direct sales Tax report      |
| Competitive  | XX-COMP-Feature title | PT-COMP-Country bank payment format |

The following table explains the components of the naming convention.

| Component name      | Format      | Description                                                                                                                   | Example                 |
|---------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------|-------------------------|
| Country/region code | XX          | The two-letter ISO country/region code (from the [ISO 3166 standard](https://www.iso.org/iso/country_names_and_code_elements)) | PT (= Portugal)         |
| Feature type        | REG or COMP | The type of feature                                                                                                           | REG                     |
| Feature name        | Text        | A short feature title that describes what the feature is used for                                                             | Direct sales tax report |

For more information about BPM, see [Upload custom business processes to Business process modeler (BPM)](../lifecycle-services/upload-business-processes-bpm-task-recorder.md).

## Additional resources

- [Globalization resources](country-region.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
