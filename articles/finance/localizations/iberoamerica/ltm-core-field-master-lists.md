---
title: Field list configuration for Latin America
description: Learn how to configure field lists for Latin America, including prerequisites and an outline and process for creating a field list.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.topic: how-to
ms.date: 11/25/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Field list configuration for Latin America

[!INCLUDE [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

Create **lists** that provide **additional information** required for **LATAM fiscal documents**.

Use these lists in the LATAM section for **invoices**, **packing slips**, and **journals**. Users select applicable values based on the configuration of the **document class**. The purpose of this feature is to assign a predefined set of extra data to each document through selectable list values. Configured lists are reusable and can be associated with multiple document classes.

You can create up to 10 lists.

## Prerequisites

Before you complete the procedures in this article, ensure you meet the following prerequisites:

- The legal entity has an address in a country/region within the LATAM localization.
- Both the region-specific LATAM feature and the general LATAM feature are enabled.

## Create a field list

This procedure shows how to create a custom field list.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
1. Select **New** to create a list.
1. In the **General** section, select an option in the **List** field.
1. Enter a descriptive name for the list in the **Name** field.
1. Select **New** in the **Reference code** section to add a record.
1. Enter or select the code that the fiscal authority provides in the **Reference code** field.
1. Enter a brief explanation of the record in the **Description** field.

## Add information required by the fiscal authorities

To add information required by the fiscal authorities, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
1. Select a list from the Navigation pane and a record from the **Reference code** section.
1. Select **Tax application** on the Action Pane.
1. Select **New**.
1. Select a value in the **Tax application Id.** field on the new line.
1. Enter the code that the fiscal authority uses to identify the record in the **Tax application code** field.
1. Select **Save**.

## Use field lists

You can use field lists to assign extra information to LATAM documents based on the document class configuration. The document class controls the availability of each field list. Follow these steps to configure and use field lists:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**.
1. Select the document class you want.
1. In the **Additional data** section, find the **Field list** area.
1. Set the status for each field list (List 1 through List 10):
   - **Disabled**: The field isn't available.
   - **Enabled**: The field is available.
   - **Required**: The field is mandatory.
1. Save your changes.

The enabled or required field lists appear in the **LATAM section** of transaction pages, where users can select the corresponding values based on the records created in [Create a field list](#create-a-field-list).

Learn more in [Document classes for Latin America](ltm-core-document-class.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
