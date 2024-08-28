---
title: Sales point prefixes for Latin America
description: Learn about the sales point prefix configuration for Latin America, including prerequisites and an outline on setting up sales point prefixes.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Sales point prefixes for Latin America

[!include [banner](../../includes/banner.md)]

You can configure the sales point prefixes that some fiscal authorities require for product legal documents, and that can be used to identify treasury documents and checkbooks.

## Prerequisites

Because warehouses can be added to the sales point prefix configuration, they should already be created.

## Set up a sales point prefix for Latin America

Follow these steps to set up a sales point prefix for Latin America.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales Point Prefix**.
2. On the Action Pane, select **New**.
3. In the **General** section, in the **Sales point prefix** field, enter the sales point code and a brief description of the sales point prefix.
4. Enable the **Validate CA** option to require a CA number when this sales point prefix is used in a transaction.
5. In the **Sales point type** field, enter the sales point type.
6. In the **Prefix** field, add the prefix that will be included with the document number in a transaction.
7. Select the report/service configuration.
8. In the **Warehouse** section, add the warehouses that can be selected when a packing slip that uses this sales point prefix is posted.

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add this codification.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point Prefix**.
2. On the Action Pane, select **Tax application**.
3. Select **New** to add a line to the grid.
4. In the **Tax application ID** field, select a value.
5. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the document class type.
6. Select **Save**.
