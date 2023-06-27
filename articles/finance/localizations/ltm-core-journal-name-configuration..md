---
title: Configure journal names for Latin America
description: This article explains how to configure journal names for Latin America.
author: Fhernandez0088
ms.date: 06/02/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Configure journal names for Latin America

[!include [banner](../includes/banner.md)]

In the journal name configuration in the extended **LATAM** section, you can add the information that's required for Latin American countries. This extended configuration affects journal name posting.

## Prerequisites

Before you can enable the LATAM configuration, the following prerequisites must be met:

- Enable the **LATAM** globalization feature with a valid country/region.
- Activate the **LATAM taxes** feature in the LATAM parameters.
- Create at least one journal name.

## LATAM configuration of journal names

1. Go to **General ledger** \> **Journal setup** \> **Journal names**.
2. Select an existing journal name, or create a new one.
3. In the **General** section, enter the required information.
4. In the **LATAM** section, select **New**, and then complete the fields in the **Value types and actions setup** grid. For each payment method type, select the movement type and actions that can be performed in the journal name.
5. In the **Default document class for account types** section, set the predetermined document classes for each account type.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
