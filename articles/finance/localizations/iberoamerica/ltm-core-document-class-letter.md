---
title: Document class letter for Latin America
description: Learn about the document class letter configuration for Latin America, including prerequisites and outline for setting up a document class letter.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak 
---

# Document class letter for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

Create the letter codes that are part of the fiscal documents configuration. Use these codes in transactions with third parties.

The system supports document classes without a letter configuration. If a document class doesn't have a letter configuration, leave the **Prefix** field blank.

## Prerequisites

Before you set up a document class letter record, make sure the following prerequisites are met:

- The legal entity has an address in a country/region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature are enabled.
- The maximum length of the document class letter prefix is configured on the **LATAM Parameters** page.

## Set up a document class letter

1. Go to **Organization administration** > **Setup** > **LATAM** > **Document class letter**. On the Action Pane, select **New**.
1. In the **Document class letter Id** field, enter a code to identify the record.
1. In the **Description** field, enter a brief description of the document class letter.

    > [!NOTE]
    > The **Document class letter Id** and **Description** fields are mandatory.

1. Complete the **Prefix** field by specifying the letter or letters that identify the document class in transactions.

    > [!NOTE]
    > You can leave this field blank if no prefix is needed.

1. On the Action Pane, select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
