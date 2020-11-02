---
# required metadata

title: E-Commerce Online SDK Frequently Asked Questions
description: This topic summarizes answers to questions that are frequently asked by users of the Dynamics 365 Commerce Online SDK.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# E-Commerce Online SDK Frequently Asked Questions

[!include [banner](../includes/banner.md)]

This topic summarizes answers to questions that are frequently asked by users of the Dynamics 365 Commerce Online SDK.

## After upgrading to module library version 10.0.14, some cloned modules that use the below list of data actions may throw an error **UserAuthorizationException. Customer account number on the request was wrong"**. 

The below list of [core data actions](core-data-actions.md) have a signature change which move the user account number parameter to the second parameter (instead of the first) and is now set an optional parameter.  In most scenarios the user account number is no longer needed, the data action will execute in the context of current signed in user. In some custom scenario where this user account number is different than the signed in user, then you can fetch the user account number using the **get-customer** data action and pass it to the data action.
 
*add-address
*get-address
*get-customer
*get-loyalty-card
*get-loyalty-transaction-estimation
*issue-loyalty

The module library modules have been updated with the correct calling pattern to the above data actions, so you won't see any errors in these modules, however if one of them was previously [cloned](clone-starter-module) with the older signature, the signatures will need to be updated accordingly. To solve this, you can temporarily clone the module libray module again with a new name, then diff the code with the previously cloned module and merge the changes. The temp module can then be deleted.
