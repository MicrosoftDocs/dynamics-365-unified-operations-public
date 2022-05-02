---
# required metadata

title: Transportation management number sequence
description: This topic describes how to set up number sequences for transportation management.
author: Weijiesa
ms.date: 10/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: TMSNumberSequence
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2020-10-16
ms.dyn365.ops.version: 10.0.14
---

# Transportation management number sequence

[!include [banner](../includes/banner.md)]

Use the **Number sequences** page in the transportation management module to set up various pro numbers. Pro numbers are used by carriers to organize and track the progress of each shipment.

## Create a number sequence for a pro number

To create a number sequence for a pro number, do the following:

1. Go to **Transportation management \> Setup \> Carriers \> Number sequences**.
1. Select **New** to create a new number sequence.
1. Enter a unique ID and descriptive name for the number sequence.
1. In the **Number sequence type** field, *Pro number* is the only option.
1. In the **Check digit** field, *Check digit* is the only option and is set up as a generic engine.
1. On the **Sequence** FastTab, provide information about the sequence.
1. Close the page.

## Link a number sequence to a shipping carrier

To link a number sequence to a carrier, do the following:

1. Go to **Transportation management \> Setup \> Carriers \> Shipping carriers**.
1. Select a shipping carrier.
1. Select **Edit**.
1. On the **Overview** FastTab, select an option in the **Pro number sequence** field.
1. Close the page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]