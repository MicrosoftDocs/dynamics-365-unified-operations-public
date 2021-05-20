---
# required metadata

title: Returning serial number controlled products in point of sale
description: This topic explains capabilities available in the point of sale application for validating serialized items as part of the returns process.
author: hhainesms
ms.date: 05/20/2021
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

# Returning serial number controlled products in point of sale (POS)

> [!NOTE]
In order to used serial number validation during return order processing in POS, the **Unified return processing experience** feature must enabled. It’s important to note that once this feature has been enabled, it cannot be disabled.  This feature also enables additional capabilities which you can learn about in the [create returns in point of sale](POS-returns.md)documentation.

## Options for validating serialized returns:
When the **Unified return processing experience** feature is enabled, organizations will now also have the option of performing a validation on serial number controlled item returns through the POS application.  This capability can warn users if the serial number being returned differs from the original serial number sold.   In the current release, users receive a warning only and can still process a return against a serial number that differs from the serial number originally sold.

After the **unified return processing experience** feature has been enabled, organizations can configure the serial number validation by going to the **Commerce parameters** form in Commerce Headquarters (HQ).  On the **Inventory** tab, the **enable validation of serial numbers on POS returns** parameter found under the **Store inventory operations** fasttab should be set to Yes

## Processing returns for seralized items in POS
When returning a serial controlled item through the Point of Sale (POS) application, if the parameter to support serial number validation has been enabled, the users will be able to input the serial number for the return line.  If the data they enter does not match with the original serial number sold for the sales transaction, the user will see a warning.   This will not prevent the user from continuing to post the return and is a warning message only.  

If the order being returned has a seralized item on the transaction that has a quantity greater than 1, this will display in the returnable products list as multiple lines, one return line for each quantity on the original transaction.  This is due to the requirement that we can only support the registration of one serial number per sales line in POS, therefore each quantity of seralized item being return will have to be processed as a separate return line.
