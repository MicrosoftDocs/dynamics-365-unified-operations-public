---
title: Transportation management number sequence
description: Learn how to set up number sequences for transportation management, including a step-by-step process for creating number sequences for pro numbers.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 10/16/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: TMSNumberSequence
---

# Transportation management number sequence

[!include [banner](../includes/banner.md)]

Use the **Number sequences** page in the transportation management module to set up various pro numbers. Carriers use pro numbers to organize and track the progress of each shipment.

## Create a number sequence for a pro number

To create a number sequence for a pro number, follow these steps:

1. Go to **Transportation management \> Setup \> Carriers \> Number sequences**.
1. Select **New** to create a new number sequence.
1. Enter a unique ID and descriptive name for the number sequence.
1. In the **Number sequence type** field, *Pro number* is the only option.
1. In the **Check digit** field, *Check digit* is the only option and is set up as a generic engine.
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

## Pro number generation mode

The pro number generation mode controls how the system allocates pro numbers.

> [!TIP]
> If your high-volume processes (such as release to warehouse) run slowly when you're using pro numbers, use the *Performance optimized* pro number generation mode to help improve throughput.

### Prerequisites

You must be running Supply Chain Management version 10.0.47 or higher to use this feature.

### Choose the pro number generation mode

To choose the pro number generation mode, follow these steps:

1. Go to **Transportation management** \> **Setup** \> **Transportation management parameters**.
1. Open the **General** tab.
1. On the **Performance settings** FastTab, set **Pro number generation mode** to one of the following values:

    - *Default* – Generate pro numbers inside the current business transaction (*transaction scoped*). The system keeps the number only if the process finishes successfully. If you cancel, or if an error stops the process, the system puts back the number and reuses it. This option enforces continuous sequencing but can increase locking under high parallel load.

    - *Performance optimized* – Generate the number on a separate connection (*isolated*). This option reduces locking and improves throughput under high load, but numbers aren't recycled if the business process later fails.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
