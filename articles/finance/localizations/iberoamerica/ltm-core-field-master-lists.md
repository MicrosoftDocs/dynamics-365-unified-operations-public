---
title: Field list configuration for Latin America
description: Learn about how to configure field lists for Latin America, including prerequisites and an outline and process for creating a field list.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Field list configuration for Latin America

[!include [banner](../../includes/banner.md)]

You can create lists that are used to provide required information that's related to Latin America (LATAM) on transactions. These lists are used in the **LATAM** section of multiple transaction posting pages, including the pages for invoices, packing slips, and journals. For every transaction, you can select an option in each list, based on the configuration of the document class that's used in the transaction.

You can create up to 10 lists.

## Prerequisites

Before you complete the procedures in this article, enable the **LATAM Globalization** feature for the country or region where the legal entity that you're working in is located.

## Create a field list 

This procedure shows how to create a custom field list.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
2. Select **New** to create a list. 
3. In the **General** section, in the **Name** field, enter a descriptive name for the list.
4. In the **Reference code** section, select **New** to add an item to the list.
5. In the **Reference code** field, enter or select the code that's provided by the fiscal authority.
6. In the **Description** field, enter a brief explanation of the item.

## Add information required by the fiscal authorities

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**.
2. Select a list, and then, on the Action Pane, select **Tax application**.
3. Select **New**.
4. On the new line, in the **Tax application Id.** field, select a value.
5. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the document class type.
6. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
