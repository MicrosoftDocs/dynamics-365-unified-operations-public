---
title: Update banner texts and images (preview)
description: Learn how to personalize the supplier portal home page banner, including banner text, the banner image, and image requirements.
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

# Update banner texts and images (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The supplier portal home page displays a banner at the top that includes both an image and text. The registration and onboarding pages also include banner text. You can configure these elements to align the portal with your organization's branding guidelines and communication style.

## Banner text

The banner text that appears on the registration and onboarding pages is stored in content snippets. The following snippet names are used:

- *Registration/HeaderPageTitle*
- *Header/VendorOnboarding*

The following screenshot shows the banner text on the registration page.

:::image type="content" source="media/portal-banner-registration.png" alt-text="Screenshot of the supplier portal registration page showing the banner text Global Vendor registration request." lightbox="media/portal-banner-registration.png":::

### Update banner text on registration and onboarding pages

To update the banner text on registration and onboarding pages, follow these steps:

1. Open the [Power Pages Management app](/power-pages/configure/portal-management-app).
1. Go to **Content** \> **Content Snippets**.
1. Find the snippet by name (*Registration/HeaderPageTitle* or *Header/VendorOnboarding*) and open it.
1. Update the **Value** field with your desired text.
1. Select **Save**.

### Home page banner text

The home page banner doesn't use a content snippet. Instead, it displays the value from the **Global vendor name** field. <!-- KFM: Where is this field? How do we edit this? -->

The technical maximum length of this field is 850 characters. However, don't exceed 500 characters. Longer values might appear visually crowded, overflow or wrap excessively, reduce readability on smaller screens, and negatively affect the overall banner layout.

## Banner image

The banner image is stored as a web file record and rendered on the home page. The image file is saved as a standard attachment in Microsoft Dataverse and associated with the corresponding web file record.

### Prerequisites

Before you begin, make sure you have the following:

- Access to the Power Pages Management app.
- A banner image file in a supported format, such as .png, .jpg, .svg, or .webp.

### Upload a new banner image

To replace the banner image, follow these steps:

1. Open the [Power Pages Management app](/power-pages/configure/portal-management-app).
1. Go to **Content** \> **Web Files**.
1. Locate and open the web file named *homepage-banner*.

    The following screenshot shows the homepage-banner web file record.

    :::image type="content" source="media/portal-banner-web-file.png" alt-text="Screenshot of the homepage-banner web file record in Power Pages Management." lightbox="media/portal-banner-web-file.png":::

1. In the **File Content** field, select **Delete** to remove the existing image (if applicable).
1. In the **File Content** field, select **Choose File** and upload your new banner image.
1. Select **Save & Close**.

### Banner image requirements and recommendations

The following table summarizes the requirements and recommendations for the banner image.

| Property | Requirement |
|---|---|
| Aspect ratio | 12:1 (width to height). If the ratio doesn't match, the image might appear stretched or cropped. |
| Recommended render size | 3,758 × 308 pixels |
| Supported formats | .png, .jpg, .svg, .webp |
| Maximum file size | Determined by Dataverse environment attachment limit (default is 5 MB). An administrator can increase or decrease this limit. If your image exceeds the configured size limit, either optimize the image or adjust the environment setting. |

To ensure optimal quality, upload an image that matches or exceeds the recommended render size while maintaining the 12:1 ratio. Avoid significantly larger images that might affect performance. Optimize images for web use to balance quality and load time.

### CSS styling

You can further personalize the banner by using cascading style sheets (CSS). By default, `dom.css` controls the styling through the `.workspace-hero-banner` class. You can adjust properties such as height, background size, positioning, and responsiveness. Test any CSS changes across different screen sizes to ensure consistent rendering.

## Related information

- [Personalize the supplier portal](personalize-portal-overview.md)
- [Update the company logo on the supplier portal](personalize-portal-logo.md)
- [Update the company name on the supplier portal](personalize-portal-company-name.md)
- [Manage unmanaged customizations on the supplier portal](personalize-portal-manage-customizations.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
