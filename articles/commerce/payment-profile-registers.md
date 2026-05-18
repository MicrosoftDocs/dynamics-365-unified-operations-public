---
title: Set up payment profiles for registers
description: Learn how to create payment profiles to control which payment methods appear on a point of sale (POS) register and in what order they're displayed.
author: ShalabhjainMSFT
ms.author: shajain
ms.reviewer: mirao
ms.date: 04/24/2026
ms.topic: article
audience: IT Pro
ms.search.region: Global
---

# Set up payment profiles for registers

This article explains how to create and assign payment profiles to control which payment methods are available on a point of sale (POS) register and in what display order they appear.

## Overview

Stores often have a mix of registers that serve different purposes. A standard register at a checkout counter typically supports traditional payment methods such as cash, check, and card. However, newer form factors, such as mobile registers that use "Tap to Pay" on iPhones or self-checkout kiosks, might support only a subset of payment methods. By default, every register in a store inherits all payment methods that you configure at the store level, and the system determines the display order. This default behavior can result in payment methods appearing on registers that don't support them.

Payment profiles give you granular control over this behavior. By using a payment profile, you can:

- **Choose which payment methods appear on a specific register**: For example, you can exclude cash from a mobile register that only supports "Tap to Pay."
- **Set the display order of payment methods**: You decide the sequence in which payment methods appear on the POS, instead of relying on the system default order.
- **Hide legacy payment methods without deleting them**: If a payment method is no longer in use but has historical transactions associated with it, you can't delete it. A payment profile lets you hide it from the POS without any customization.

If you don't assign a payment profile to a register, the register falls back to the existing behavior and displays all payment methods that you configured at the store level.

## Create a payment profile

To create a payment profile, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS profiles** > **Payment profiles**.
1. Select **New**.
1. Enter a **Payment profile number** to uniquely identify the profile.
1. Enter a **Profile name** that describes the profile's purpose (for example, *Mobile registers - Tap to Pay only*).

## Add payment methods to the profile

After you create a payment profile, add the payment methods that should be available on registers that use this profile.

1. On the payment profile page, in the payment methods subgrid, select **Add**.
1. Select a payment method from the list of payment methods that are defined in Commerce headquarters.
1. Repeat these steps for each payment method that you want to include in this profile.
1. Optionally, set the **Display order** value for each payment method. Payment methods display on the POS in ascending order of this value. For example, a payment method with a display order of **1** appears before a payment method with a display order of **2**. Payment methods that don't have a display order value appear after methods that do.

> [!NOTE]
> Only payment methods that are also mapped to the store (channel) to which the register belongs appear on the POS. If you add a payment method to a payment profile but that payment method isn't configured on the corresponding store, it won't be displayed on the POS register.

## Assign the payment profile to a register

After you set up a payment profile, assign it to one or more registers:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **Registers**.
1. Select the register that you want to update.
1. On the **General** section of the register form, in the **Payment profiles** field, select the payment profile to assign.
1. Select **Save**.

Repeat these steps for each register that should use a payment profile.

## Run distribution schedule jobs

After you create a payment profile and assign it to a register, you must run the following distribution schedule jobs to sync the changes to the POS:

- **1090** (Registers)

Until you run these jobs, the changes don't take effect at the POS.

## Fallback behavior

If you don't assign a payment profile to a register, the register continues to use the existing behavior. In that case, the POS displays all payment methods that are configured at the store level, and the system determines the display order.

If you remove a payment profile previously assigned to a register, the register reverts to this same fallback behavior.

## More resources

- [Set up payment methods](payment-methods.md)
