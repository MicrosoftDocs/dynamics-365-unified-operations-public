---
title: How to add concepts to the lookups in File formats 1000 for Colombia in Electronic Reporting
description: Learn how to configure Electronic Reporting to add more concepts to file formats 1000 for Colombia.
author: Fhernandez0088
ms.date: 29/12/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# How to add concepts to the lookups in File formats 1000 for Colombia in Electronic Reporting

This article explains how to add more concepts to the lookups of the File formats 1000 of Colombia in Electronic Reporting configurations.

## Prerequisites:

Before you add any new concepts 	to the 1000 file formats for Colombia follow the steps the article of the wanted format:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="LTM Tax Report":::                               |
| Mapping | :::no-loc text="LTM Tax Report mapping "::: |
| Format  | :::no-loc text="File Format 1001":::                   |
| Format  | :::no-loc text="File Format 1003":::                       |
| Format  | :::no-loc text="File Format 1007":::                        |
| Format  | :::no-loc text="File Format 1008":::                          |
| Format  | :::no-loc text="File Format 1009":::                     |
| Format  | :::no-loc text="File Format 1012":::                         |

## Add new concepts

After the prerequisites are met follow these steps:
1. Go to **Organization administration > Electronic reporting > Configurations**.
1. On the list of formats to the left select the format to modify.
1. In the menu bar select **Create configuration**, and select **Derive from name**.
1. Enter a format name and a description and select a **Data model version** (It is recommended to use the latest version) and select **Create configuration**.
1. In the top menu bar go to **Format designer** and then select **Format enumerations**. There you can see the enumeration containing values that are groups of concepts.
1. Select the enumeration of concepts to modify.
1. In the **Format enumeration values** list, add as the concepts required.
1. In each new record enter the name, label and description (the label and description fields are not mandatory, but it is recommended to complete them).
1. Select **Save** and return to the format designer.
1. Select **Ok**.
1. Save the changes in the **Format designer** and return to the **Electronic Reporting** configuration screen.
1. Change the version status to complete.
1. Go to **Configurations > Application specific parameters > Setup**.
1. Select the corresponding report version and the new concepts will be available as a **Lookup result** of its corresponding **Condition**.
1. Configure the corresponding application specific parameters and change the state to Completed. Now the report should be ready to use the new concepts.

> [!NOTE]
> The concepts in the Colombian file formats 1000 depend on the list of concepts for each report.
