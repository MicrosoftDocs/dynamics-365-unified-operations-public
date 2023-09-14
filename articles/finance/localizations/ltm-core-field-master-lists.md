---
title: Field list configuration for Latin America
description: This article provides information about configuring field lists for Latin America. 
author: Fhernandez0088
ms.date: 09/05/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Field list configuration for Latin America
[!include [banner](../includes/banner.md)]


You can create lists that are used to provide required information related to LATAM on transactions. These lists are used in the LATAM section of multiple transaction posting forms, including invoices, packing slips, and journals. For each transaction, you can select an option from each list based on the configuration of the document class used in the transaction. 

You can create up to 10 lists.  

## Prerequisites
Before you complete the procedures in this article, enable the **LATAM Globalization** feature for the country that the legal entity you are working in is located.

## Create a field list 

This procedure explains how to create a custom field list.

1. Go to **Organization administration** > **Setup** > **LATAM** > **Fields master List**.
2. Select **New** to create a new list. 
3. In the **General** section, in the **Name** field, provide a descriptive name for the list.
4. In the **Reference code** section select **New** to add an item to the list.
5. In the **Reference code** field, enter or select the code provided by the fiscal authority.
6. In the **Description** field, enter a brief explanation of the item.

## Add  information required by the fiscal authorities
1. Go to **Organization administration > Setup > LATAM > Fields master List**.
2. Select a list, and on the Action Pane, select **Tax application**.
3. Select **New**.
4. In the new line, in the **Tax application Id.** field, select a value.
5. In the **Tax application code field**, enter the code with which the fiscal authority identifies the document class type.
6. Select **Save**.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
