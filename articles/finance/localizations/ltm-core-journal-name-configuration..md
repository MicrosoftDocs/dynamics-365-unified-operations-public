---
title: Configure journal names for Latin America
description: This article provides information about configuring journal names for Latin America. 
author: Fhernandez0088
ms.date: 06/02/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Configure journal names for Latin America

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

You can add the information needed for Latin American countries in the journal names configuration in the extended **LATAM** section.
This extended configuration affects the journal name posting.

## Prerequisites
To enable the LATAM configuration, the following prerequisites must be met:

- Enable the **LATAM globalization** feature with a valid country
- Activate the **LATAM taxes** feature in the LATAM parameters
- Create at least one journal name

## LATAM configuration of journal names

1. Go to **General ledger** > **Journal setup** > **Journal names**.
2. Select a journal name or create a new one.
3. Enter the required information in the **General** section.
4. In the **LATAM** section, select **New** and complete fields in the **Value types and actions setup** grid. For each payment method type, select the movement type and actions that can be performed in the journal name.
5. In the **Default document class for account types** field group, set the predetermined document classes for each account type.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
