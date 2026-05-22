---
title: Opt out of web activity event collection
description: Learn how to allow visitors to your Microsoft Dynamics 365 Commerce site to opt out of web activity event collection.
author: bebeale
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: bebeale
ms.search.validFrom: 2019-10-31
ms.custom:
  - bap-template
---

# Opt out of web activity event collection

[!include [banner](includes/banner.md)]

This article explains how to allow visitors to your Microsoft Dynamics 365 Commerce site to opt out of web activity event collection.

Dynamics 365 Commerce lets site administrators analyze the web activity of users of their e-commerce sites. Administrators can use this data to better understand how their sites are used, and optimize the sites to provide an improved user experience and meet business objectives.

## Ways for administrators to implement an opt-out experience

Administrators have three ways to implement an opt-out experience.

### Opt out on behalf of users

In Account management in Commerce headquarters (HQ), administrators can opt out on behalf of users.

1. In the HQ client, on the **All customers** page, search for and select a customer.
1. On the customer details page, on the **Retail** FastTab, in the **Privacy** section, set the **Do not track web activity** option to **Yes**.

    :::image type="content" source="media/Disablepersonalizationpart2.png" alt-text="Screenshot of privacy settings.":::

1. Select **Save**, and then close the page.

### Module-based opt-out experience

Administrators can let authenticated users opt out of web activity event collection by themselves. To provide this opt-out experience, add the user opt-out module to customer account profile pages.

### Custom extensions

Administrators can create their own extensions to manage the opt-out experience for users. For more information, see [Call Retail Server APIs](e-commerce-extensibility/call-retail-server-apis.md) and [Online channel extensibility](e-commerce-extensibility/overview.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
