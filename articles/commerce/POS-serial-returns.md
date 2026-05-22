---
title: Return serial number-controlled products in POS
description: Learn about the capabilities for validating serialized items as part of the return process in Microsoft Dynamics 365 Commerce point of sale (POS).
author: hhainesms
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-02-11 
ms.custom: 
  - bap-template
---

# Return serial number–controlled products in POS

[!include [banner](includes/banner.md)]

This article describes the capabilities for validating serialized items as part of the return process in Microsoft Dynamics 365 Commerce point of sale (POS).

> [!NOTE]
> In Commerce version 10.0.20 and later, a feature named **Unified return processing experience in POS** is available. To use serial number validation during return order processing in POS, you must turn on this feature. For information about other capabilities that this feature provides when it's turned on, see [Create returns in POS)](POS-returns.md).
>
> After you turn on the feature, you can't turn it off.

## Options for validating serialized returns

When you turn on the **Unified return processing experience in POS** feature, your organization can validate returns of serial number–controlled items through POS. This capability warns users if the serial number that's being returned differs from the original serial number that was sold. In the Commerce version 10.0.20 release and later, the message that users receive is only a warning message. Users can continue to process a return against a serial number that differs from the serial number that was originally sold.

To configure serial number validation for an organization after you turn on the **Unified return processing experience in POS** feature, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters** in Commerce headquarters. On the **Inventory** tab, on the **Store inventory operations** FastTab, set the **Enable validation of serial numbers on POS returns** option to **Yes**.

## Process returns for serialized items in POS

If you set the **Enable validation of serial numbers on POS returns** option to **Yes**, when a serial number–controlled item is returned through POS, the user can enter the serial number for the return line in the details pane on the **Returnable products** page. If the serial number that is entered doesn't match the original serial number that was sold for the sales transaction, the user receives a warning message. However, the application doesn't prevent the user from continuing to post the return.

> [!NOTE]
> Currently, POS supports validation of serial numbers only on return lines where the original ordered quantity is no more than one. If the original sales order line is created in a non-POS channel, and if the quantity ordered for the serialized item on a given sales line is more than one, the item can't be correctly returned through POS.

## Additional resources

[Create returns in POS](POS-returns.md)
