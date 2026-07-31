---
title: Update the company name on the supplier portal (preview)
description: Learn how to update the company name displayed on the supplier portal home page by editing a content snippet.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Update the company name on the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

A content snippet in Microsoft Dataverse controls the company name displayed on the supplier portal home page. You can update this value at any time to reflect your organization's name.

## Update the company name

To update the company name shown on the portal, follow these steps:

1. Open the [Power Pages Management app](/power-pages/configure/portal-management-app).
1. Go to **Content** \> **Content Snippets**.
1. Locate and open the snippet named *Home/CompanyName*.
1. In the **Value** field, enter your company's name.

    The following screenshot shows the *Home/CompanyName* content snippet with text in the default company name in the **Value** field.

    :::image type="content" source="media/portal-company-name-snippet.png" alt-text="Screenshot of the Home/CompanyName content snippet in Power Pages Management showing the Value field." lightbox="media/portal-company-name-snippet.png":::

1. Select **Save & Close**.

## Verify the changes

Clear your browser cache and refresh the portal. The updated company name is now visible on the home page.

The following screenshot shows the portal home page with an updated company name.

:::image type="content" source="media/portal-company-name-updated.png" alt-text="Screenshot of the supplier portal home page displaying the updated company name Brand New Company." lightbox="media/portal-company-name-updated.png":::

> [!TIP]
> If the updated company name doesn't appear immediately, verify that the content snippet is active and that your browser cache is cleared.

## Related information

- [Personalize the supplier portal](personalize-portal-overview.md)
- [Update the company logo on the supplier portal](personalize-portal-logo.md)
- [Update banner texts and images](personalize-portal-banner.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
