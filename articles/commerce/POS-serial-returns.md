---
# required metadata

title: Return serial number-controlled products in point of sale (POS)
description: This topic describes capabilities available in the Microsoft Dynamics 365 Commerce point of sale (POS) application for validating serialized items as part of the returns process.
author: hhainesms
ms.date: 05/28/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: hhaines
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.20
---

# Return serial number-controlled products in point of sale (POS)

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic explains describes capabilities available in the Microsoft Dynamics 365 Commerce point of sale (POS) application for validating serialized items as part of the returns process.

> [!NOTE]
> Starting in the Commerce version 10.0.20 release, the **Unified return processing experience in POS** feature can be enabled. In order to use serial number validation during return order processing in POS, this feature must be enabled. Once this feature has been enabled, it cannot be disabled. For information on additional capabilities of this feature once enabled, see [Create returns in point of sale](POS-returns.md).

## Options for validating serialized returns

When the **Unified return processing experience in POS** feature is enabled, organizations have the option of performing a validation on serial number-controlled item returns through the POS application. This capability can warn users if the serial number being returned differs from the original serial number sold. As of the Commerce version 10.0.20 release, users only receive a warning and can still process a return against a serial number that differs from the serial number originally sold.

After the **Unified return processing experience in POS** feature has been enabled, organizations can configure serial number validation by going to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters** in Commerce headquarters. On the **Inventory** tab, the **Enable validation of serial numbers on POS returns** parameter found under the **Store inventory operations** FastTab should be set to **Yes**.

## Process returns for serialized items in POS

When returning a serial number-controlled item through the POS application, if the parameter to support serial number validation has been enabled, users will be able to input the serial number for the return line through the details panel on the **returnable products** form. If the data entered does not match the original serial number sold for the sales transaction, the user will see a warning. This warning will not prevent the user from continuing to post the return.  

> [!NOTE]
> Currently the POS application can only support validation of serial numbers on return lines where the original ordered quantity is no greater than one. If the original sales order line was created in a non-POS channel and the quantity ordered for the serialized item is greater than one on a given sales line, it cannot be properly returned through the POS application. 

## Additional resources

[Create returns in point of sale (POS)](POS-returns.md)

