---
title: Return serial number-controlled products in POS
description: This article describes the capabilities for validating serialized items as part of the return process in the Microsoft Dynamics 365 Commerce point of sale (POS) application.
author: hhainesms
ms.date: 06/01/2021
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-02-11 
ms.custom: 
  - bap-template
---

# Return serial number–controlled products in POS

[!include [banner](includes/banner.md)]

This article describes the capabilities for validating serialized items as part of the return process in the Microsoft Dynamics 365 Commerce point of sale (POS) application.

> [!NOTE]
> In the Commerce version 10.0.20 release and later, a new feature that is named **Unified return processing experience in POS** is available. To use serial number validation during return order processing in POS, you must turn on this feature. For information about others capabilities that this feature provides when it's turned on, see [Create returns in POS)](POS-returns.md).
>
> After the feature is turned on, it can't be turned off.

## Options for validating serialized returns

When the **Unified return processing experience in POS** feature is turned on, organizations can perform a validation on returns of serial number–controlled items through POS. This capability can warn users if the serial number that is being returned differs from the original serial number that was sold. In the Commerce version 10.0.20 release and later, the message that users receive is only a warning message. Users can continue to process a return against a serial number that differs from the serial number that was originally sold.

To configure serial number validation for an organization after the **Unified return processing experience in POS** feature is turned on, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters** in Commerce headquarters. On the **Inventory** tab, on the **Store inventory operations** FastTab, set the **Enable validation of serial numbers on POS returns** option to **Yes**.

## Process returns for serialized items in POS

If the **Enable validation of serial numbers on POS returns** option has been set to **Yes**, when a serial number–controlled item is returned through POS, the user can enter the serial number for the return line in the details pane on the **Returnable products** page. If the serial number that is entered doesn't match the original serial number that was sold for the sales transaction, the user receives a warning message. However, the application doesn't prevent the user from continuing to post the return.

> [!NOTE]
> Currently, POS supports validation of serial numbers only on return lines where the original ordered quantity is no more than one. If the original sales order line was created in a non-POS channel, and if the quantity that was ordered for the serialized item on a given sales line is more than one, the item can't be correctly returned through POS.

## Additional resources

[Create returns in POS](POS-returns.md)
