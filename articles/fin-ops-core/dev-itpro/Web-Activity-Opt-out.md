---
# required metadata

title: Opt out of web activity event collection
description: This topic explains how you can let your website visitors opt out of web activity event collection in Microsoft Dynamics 365 Commerce. 
author: aamiral
manager: AnnBe
ms.date: 05/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
ms.search.industry: Retail, eCommerce
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5
---

# Opt out of web activity event collection
[!include [banner](includes/banner.md)]

This topic explains how you can let customers opt out of web activity event collection in Microsoft Dynamics 365 Commerce.

## Overview

Dynamics 365 Commerce allows site administrators to analyze web activity of users on their e-commerce sites to better understand usage of their e-commerce site and optimize the site to provide an improved user experience and to meet business objectives.


## Ways for administrators to implement an opt-out experience

Administrators have three ways to implement an opt-out experience.

### Opting out on behalf of users

In Account management in Commerce HQ, administrators can opt out on behalf of users.

1. In the HQ client, navigate to **All customers** form.
1. Search for and select a customer, and then select the **Retail** FastTab.

    ![Retail FastTab](../../../commerce/media/Disablepersonalizationpart1.png)

1. Under **Privacy**, set the **Do not track web activity** option to **Yes**.

    ![Privacy settings](../../../commerce/media/Disablepersonalizationpart2.png)

1. Select **Save**, and close the page.

### Module-based opt-out experience

Administrators can let authenticated users opt out of web activity event collection by themselves. To provide this opt-out experience, add the user opt-out module to customer account profile pages.

### Custom extensions

Administrators can create their own extensions to manage the opt-out experience for users. For more information, see [Call Retail Server APIs](e-commerce-extensibility/call-retail-server-apis.md) and [Online channel extensibility](e-commerce-extensibility/overview.md).
