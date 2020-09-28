---
# required metadata

title: Omni-channel Commerce order payments
description: This topic describes the omni-channel Commerce order payments feature in Microsoft Dynamics 365 Commerce.
author: rubendel
manager: annbe
ms.date: 07/28/2020
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

# Skip change due

[!include [banner](../includes/banner.md)]

This document decribes a setting which allows the point of sale to skip the 'Change due' dialog when a transaction is paid in full and there is no change due.

## Overview

With the prevalence of credit cards for payments at the point of sale, most transactions don't require change to be provided to the customer. When this property is enabled, the 'Change due' dialog will be skipped unless there is change due back to the customer. The 'Change due' dialog will also continue to be shown if the receipt format for gift receipts is set to print 'As required'. When gift receipts are set to print 'As required', the option to print a gift receipt is included in the 'Change due' dialog and supercedes the "Skip change due" setting.

## Setup 

The property to skip change due is found in the **Functionality profile** level- a store level setting. To enable, search for the **Functionality profile** for the store where the dialog should be skipped. Open the functionality profile for the target store and click **Edit**. Then expand the **Functions** fasttab. Under the "Terminal" subheading, locate the "Change due" property. By default it will be "Show always". Click the dropdown and change the setting to "Skip when zero". 

After the changes have been made, click **Save** and run the **1070** channel configuration distribution schedule. Once the changes have been sychronized, log out of the POS and log back in. Perform a transaction that has no change due to the customer and observe that the user is no longer presented with the "Change due" dialog for such transactions.  
