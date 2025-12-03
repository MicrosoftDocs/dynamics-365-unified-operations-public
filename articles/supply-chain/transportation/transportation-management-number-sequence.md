---
title: Transportation management number sequence
description: Learn how to set up number sequences for transportation management, including a step-by-step process for creating number sequences for pro numbers.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSNumberSequence
ms.topic: how-to
ms.date: 11/19/2025
ms.custom:
  - bap-template
---

# Transportation management number sequence

[!include [banner](../includes/banner.md)]

Use the **Number sequences** page in the transportation management module to set up various pro numbers. Carriers use pro numbers to organize and track the progress of each shipment.

## Create a number sequence for a pro number

To create a number sequence for a pro number, follow these steps:

1. Go to **Transportation management \> Setup \> Carriers \> Number sequences**.
1. Select **New** to create a new number sequence.
1. Enter a unique ID and descriptive name for the number sequence.
1. In the **Number sequence type** field, select *Pro number*.
1. In the **Check digit** field, select *Check digit*, which is up as a generic engine.
1. On the **Sequence** FastTab, provide information about the sequence.
1. Close the page.

Learn more about how to work with number sequences in [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md).

## Link a number sequence to a shipping carrier

To link a number sequence to a carrier, follow these steps:

1. Go to **Transportation management \> Setup \> Carriers \> Shipping carriers**.
1. Select a shipping carrier.
1. Select **Edit**.
1. On the **Overview** FastTab, select an option in the **Pro number sequence** field.
1. Close the page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
