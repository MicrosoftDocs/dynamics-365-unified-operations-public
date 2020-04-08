---
# required metadata

title:Replace User IDs of tracked content changes
description: This topic reviews the the ability to replace the email address User IDs in the change tracking logs within site builder. 
author: BrianShook
manager: BrendanSullivanMSFT
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Replace User IDs of tracked content changes

This topic describes the process of updating the user IDs within the site builder change tracking logs. 

## Overview
In Dynamics 365 Commerce, the site builder authoring tools track changes made to items within the Content Management System (CMS). This allows for display of history of changes made to documents which helps teams track their efforts when collaborating on content. The system utilizes the User IDs within the underlying Identity management system, Azure Active Directory (AAD). These user IDs are also the issued email addresses within the Active Directory. A Commerce System Administrator can replace the ID reference within the history logs by using a feature within the site builder tool.

## Replacing the User ID in Site Builder
To replace a specific user's User ID, or issued email address:

- Navigate to **Home** in site builder.
- Open the **Tenant Settings** menu and select **Tracking Content Changes**

![Tracking Content Changes menu](./media/TrackingContentChanges.png)

- Select the **Manage** button to manage the user IDs
- Enter the User ID/email address that is intended to be removed from tracking logs. Select "Replace" once entered. Multiple entries can be entered to be replaced.

![Interface with examples to replace an email address](./media/ReplaceEmailAddress.png)

- Select "OK" and then select the "Save" button in the **Tracking Content Changes** window.

A dialogue should appear to indicate the records for the email provided have been updated. Note: the system replaces the email address with a randomly generated string to remove all CMS references of the email address that was entered. This action only affects the history logs referenced within the specific Commerce > e-Commerce environment (tenant) which the site builder instance is associated.
