---
# required metadata

title: Opt out of web activity event collection
description: This topic explains how you can let visitors to your website opt out of web activity event collection in Microsoft Dynamics 365 Commerce. 
author: aamiral
ms.date: 05/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
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

Dynamics 365 Commerce lets site administrators analyze the web activity of users of their e-commerce sites. In that way, they can better understand how their sites are used, and they can optimize the sites to provide an improved user experience and meet business objectives.


## Ways for administrators to implement an opt-out experience

Administrators have three ways to implement an opt-out experience.

### Opt out on behalf of users

In Account management in Commerce headquarters (HQ), administrators can opt out on behalf of users.

1. In the HQ client, on the **All customers** page, search for and select a customer.
1. On the customer details page, on the **Retail** FastTab, in the **Privacy** section, set the **Do not track web activity** option to **Yes**.

    ![Privacy settings.](media/Disablepersonalizationpart2.png)

1. Select **Save**, and then close the page.

### Module-based opt-out experience

Administrators can let authenticated users opt out of web activity event collection by themselves. To provide this opt-out experience, add the user opt-out module to customer account profile pages.

### Custom extensions

Administrators can create their own extensions to manage the opt-out experience for users. For more information, see [Call Retail Server APIs](e-commerce-extensibility/call-retail-server-apis.md) and [Online channel extensibility](e-commerce-extensibility/overview.md).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
