---
title: Order lookup module
description: Learn about the order lookup module and how to configure it in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-08-15
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Order lookup module

[!include [banner](includes/banner.md)]

This article describes the order lookup module and explains how to configure it in Microsoft Dynamics 365 Commerce.

The order lookup module provides a form that customers can use to look up orders they placed on an e-commerce site. Use it as part of the [Enable order lookup for guest checkouts](order-lookup-guest.md) feature. The order lookup module can look up orders that users submitted through an e-commerce site, the retail point of sale (POS), or a call center. The form can retrieve orders that both guest users and registered users submitted.

The following illustration shows an example of the form that the order lookup module renders. When customers fill out the form and select **Find your order**, they go to the order details page.

:::image type="content" source="./media/OrderLookup_module.PNG" alt-text="Screenshot of the form for the order lookup module on a page.":::

## Order lookup module properties

| Property name     | Value     | Description |
|-------------------|-----------|-------------|
| Heading           | Text      | The heading that appears at the top of the form (for example, "Find your order"). |
| Rich text         | Rich text | Optional explanatory text that appears below the heading. |
| Order status type | Enum      | <p>Select the type of information that the form requests from the customer in addition to the order confirmation ID. The following values are currently supported:</p><ul><li><b>Email</b> – The form includes a field where customers can enter the email address that they used when they placed the order.</li><li><b>None</b> – The form requests no information besides the order confirmation ID.</li></ul> |

## Add an order lookup module to a page

Add the order lookup module to the body of any page of your e-commerce site. If you want to use the order lookup module to enable order lookup for guest checkouts, add it to a page that doesn't require the user to be signed in. To find a page's **Requires sign in?** setting in the Commerce site builder tree view, select the **Default page (Required)** slot, and look at the bottom of the right pane.

> [!NOTE]
> To enable the order lookup feature, ensure that the **Quotations** key is enabled under **License configuration** > **Configuration keys**.
>
> :::image type="content" source="./media/Quotations_License_Key_Configuration.png" alt-text="Screenshot of the Quotations license key configuration that must be enabled.":::

## Additional resources

[Enable order lookup for guest checkouts](order-lookup-guest.md)

[Module library overview](starter-kit-overview.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
