---
# required metadata

title: Skip "change due"
description: This topic describes how to skip the "Change due" dialog in the point of sale (POS) when a transaction is paid in full and there is no change due.
author: rubendel
manager: annbe
ms.date: 09/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Skip "change due"

[!include [banner](../includes/banner.md)]

This topic describes how to skip the **Change due** dialog in the point of sale (POS) when a transaction is paid in full and there's no change due.

For payments at the POS there is now a greater prevalence of credit usage, as most transactions don't require change to be provided to the customer. In Dynamics 365 Commerce, you can configure POS so that the  **Change due** dialog is skipped unless there's actually change due back to the customer. The **Change due** dialog will also be shown if the receipt format for gift receipts is configured to print **As required**. When gift receipts are configured to print **As required**, the option to print a gift receipt is included in the **Change due** dialog, overriding the **Skip change due** configuration.

## Configure **Change due** 

The property you need to configure to skip the **Change due** dialog is found in the **Functionality profile** level, which is a store-level setting. To configure the property, do the following.
1. Search for the **Functionality profile** for the store where the dialog should be skipped.
1. Open the functionality profile for the target store and select **Edit**. 
1. Expand the **Functions** FastTab. Under the **Terminal** subheading, in the **Change due** field, select **Skip when zero**. 
1. Select **Save** and then run the **1070** channel configuration distribution schedule.
1. After the changes are synchronized, sign out of the POS and sign back in. Make a transaction that has no change due to the customer to verify that the **Change due** dialog isn't displayed.  
