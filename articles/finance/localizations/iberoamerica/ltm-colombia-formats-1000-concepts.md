---
title: Add Concepts to File Formats 1000 in Electronic Reporting for Columbia
description: Learn how to configure Electronic Reporting to add new concepts to File formats 1000 for Colombia. Follow step-by-step instructions to enhance your reports.
author: Fhernandez0088
ms.date: 12/30/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Add concepts to the lookups in File formats 1000 for Colombia in Electronic Reporting

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to add more concepts to the lookups of the File formats 1000 of Colombia in Electronic Reporting configurations.

## Prerequisites

Before you add any new concepts to the 1000 file formats for Colombia, meet these prerequisites:

- Set the legal entity address to a location in Colombia.
- Enable the country/region-specific Latin American (LATAM) globalization feature for Colombia and the general LATAM feature.
- Import these configurations from the Dataverse:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="LTM Tax Report":::                |
| Mapping | :::no-loc text="LTM Tax Report mapping ":::       |
| Format  | :::no-loc text="File Format 1001":::              |
| Format  | :::no-loc text="File Format 1003":::              |
| Format  | :::no-loc text="File Format 1007":::              |
| Format  | :::no-loc text="File Format 1008":::              |
| Format  | :::no-loc text="File Format 1009":::              |
| Format  | :::no-loc text="File Format 1012":::              |

## Add new concepts

After you meet the prerequisites, follow these steps to add new concepts:

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. Select the format to modify from the list of formats on the left.
1. Select **Create configuration** in the menu bar, and select **Derive from name**.
1. Enter a format name and a description. Select a **Data model version** (use the latest version) and select **Create configuration**.
1. Go to **Format designer** in the top menu bar, and then select **Format enumerations**. You see the enumeration containing values that are groups of concepts.
1. Select the enumeration of concepts to modify.
1. Add the required concepts in the **Format enumeration values** list.
1. Enter the name, label, and description for each new record. The label and description fields aren't mandatory, but it's recommended you complete them.
1. Select **Save** and return to the format designer.
1. Select **Ok**.
1. Save the changes in the **Format designer** and return to the **Electronic Reporting** configuration screen.
1. Change the version status to complete.
1. Go to **Configurations > Application specific parameters > Setup**.
1. Select the corresponding report version. The new concepts are available as a **Lookup result** of its corresponding **Condition**.
1. Configure the corresponding application specific parameters and change the state to Completed. Now the report is ready to use the new concepts.

> [!NOTE]
> The concepts in the Colombian file formats 1000 depend on the list of concepts for each report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
