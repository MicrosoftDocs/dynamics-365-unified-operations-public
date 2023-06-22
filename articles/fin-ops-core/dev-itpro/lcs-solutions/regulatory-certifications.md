---
title: Regulatory certification information in feature titles
description: This article describes how information about certifications is used in the title of the feature.
author: kfend
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: kfend
ms.search.region: global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d0b8286a-b2c1-4fa2-905a-3383b1d34d56
---

# Regulatory certification information in feature titles

[!include [banner](../includes/banner.md)]

As part of the requirements for LCS solutions for localization &amp; translation, localization ISV solution providers must include details about any regulatory certifications that the solution requires in order to be legally compliant for sale in the intended market. This article shows how information about certifications is used in the title of the feature.

Regulatory certification can take various forms, from data privacy to certification of compliance with specific regulations. However, one thing that all regulatory certifications have in common is that they are required by the laws and regulations of the country/region of operation. These certifications are enforced, and non-adherence can lead to severe consequences for an organization that does business in that country/region. When the business process library is constructed, regulatory certifications must be identified as regulatory requirements in the Microsoft Dynamics Lifecycle Services (LCS) Business process modeler (BPM) library through the title of the localization solution feature. The label for this title will conform to the following naming convention that indicates the country/region and certification type through prefixes, as shown in the following table.

| Feature type | Format                      | Example                                  |
|--------------|-----------------------------|------------------------------------------|
| Regulatory   | XX-REG-Certification for xx | PT-REG-Certification for Fiscal printers |

The following table explains the components of the naming convention.

| Component name      |  Format | Description                                                                                                                   | Example                           |
|---------------------|---------|-------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Country/region code | XX      | The two-letter ISO country/region code (from the [ISO 3166 standard](https://www.iso.org/iso/country_names_and_code_elements)) | PT (= Portugal)                   |
| Feature type        | REG     | The type of feature                                                                                                           | REG                               |
| Certification name  | Text    | A short title that describes the certification and its application                                                            | Certification for Fiscal printers |

In the BPM business process library, certifications should be located under **APQC level 8.0 Manage Financial Resources (10009)**. 

**Example**

-   APQC level 8.0 Manage Financial Resources (10009)
    -   PT-REG-Certification for Fiscal printers

For more information about BPM, see [Flowcharts in Business process modeler (BPM)](../lifecycle-services/flowcharts-business-process-modeler.md).





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
