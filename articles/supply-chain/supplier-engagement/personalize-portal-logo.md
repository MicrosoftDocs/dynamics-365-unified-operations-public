---
title: Update the company logo on the supplier portal (preview)
description: Learn how to replace the default company logo on the supplier portal by updating a web file and activating a content snippet.
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

# Update the company logo on the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The portal logo is a web file record in Microsoft Dataverse. A content snippet reference renders the logo on the home page. Replace the default placeholder logo with your organization's logo by uploading a new image and ensuring the related content snippet is active.

## Prerequisites

To update the company logo on the supplier portal, you must have the following:

- Access to the Power Pages Management app.
- A logo file in one of the supported formats, such as .png, .jpg, .svg, or .webp.

## Upload a new logo

To replace the company logo, follow these steps:

1. Open the [Power Pages Management app](/power-pages/configure/portal-management-app).
1. Go to **Content** \> **Web Files**.
1. Locate and open the web file named *companylogo.png*.
1. Select the **Choose File** button next to the **File content** field.

    The following screenshot shows the *companylogo.png* web file record with the file upload dialog.

    :::image type="content" source="media/portal-logo-web-file-upload.png" alt-text="Screenshot of the companylogo.png web file record in Power Pages Management with the file upload dialog open." lightbox="media/portal-logo-web-file-upload.png":::

1. Select your new logo image.
1. Select **Save & Close**.

## Activate the logo snippet

After uploading the logo, verify that the content snippet that references it is active. To check the snippet, follow these steps:

1. Open the [Power Pages Management app](/power-pages/configure/portal-management-app).
1. Go to **Content** \> **Content Snippets**.
1. Set the view selector to **Active Content Snippets** and locate the snippet named *Home/CompanyLogo*. If you don't see the snippet, set the view selector to **Inactive Content Snippets** and try again.
1. Open the *Home/CompanyLogo* snippet. If the snippet is inactive, select **Activate** on the command bar.

    The following screenshot shows the *Home/CompanyLogo* content snippet with the activation confirmation dialog.

    :::image type="content" source="media/portal-logo-snippet-activate.png" alt-text="Screenshot of the Home/CompanyLogo content snippet showing the activation confirmation dialog." lightbox="media/portal-logo-snippet-activate.png":::

1. Select **Save & Close** if you made any changes.

## Verify the changes

Clear your browser cache and refresh the portal home page. The updated logo should now appear.

The following screenshot shows the portal home page with an updated company logo.

:::image type="content" source="media/portal-logo-updated.png" alt-text="Screenshot of the supplier portal home page showing the updated company logo." lightbox="media/portal-logo-updated.png":::

> [!TIP]
> Ensure uploaded logo images are optimized for web use to maintain portal performance. If the updated logo doesn't appear, verify that the *Home/CompanyLogo* content snippet is active and correctly configured.

## Related information

- [Personalize the supplier portal](personalize-portal-overview.md)
- [Update the company name on the supplier portal](personalize-portal-company-name.md)
- [Update banner texts and images](personalize-portal-banner.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
