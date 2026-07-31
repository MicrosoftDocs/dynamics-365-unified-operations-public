---
title: Personalize the supplier portal (preview)
description: Learn how to personalize the supplier portal branding, including the company logo, name, banner, and how to manage solution customizations.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Personalize the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The supplier portal is built on Microsoft Power Pages and serves as the primary interface for external supplier representatives to collaborate with your organization. Through the portal, suppliers register, complete onboarding, respond to requests for quotation, manage purchase orders, submit invoices, and handle consignment inventory.

The portal provides settings that you can use to personalize its appearance to match your organization's branding and communication style. Out of the box, the portal includes placeholder elements for the company name, company logo, and a banner image. You can replace these elements with your own branding, and you can also modify the layout, text, and images on key pages such as the landing page, registration page, and home page.

## Portal pages that support personalization

The supplier portal has several key pages that visitors and authenticated users interact with:

- **Landing page** – The default page for all visitors. It's publicly accessible (no sign-in required) and introduces the supplier portal to potential suppliers. It includes links to register as a new supplier or sign in with an existing account.
- **Registration page** – An anonymous page where potential suppliers submit their company details, contact information, capabilities, and certifications.
- **Home page** – The main page for authenticated users. It shows a personalized banner with the vendor's name and provides navigation to purchase orders, RFQs, invoices, and other collaboration features.
- **Onboarding pages** – A guided wizard where newly invited suppliers provide detailed business, contact, and compliance information.

Each of these pages includes branding elements—logos, banner images, and text—that you can personalize.

The following screenshot shows the default supplier portal home page with placeholder branding elements.

:::image type="content" source="media/portal-home-page-default.png" alt-text="Screenshot of the default supplier portal home page showing placeholder company logo, company name, and banner image." lightbox="media/portal-home-page-default.png":::

## How portal branding works

Two types of Power Pages components control portal branding:

- **Content snippets** – Use these to configure text-based elements such as the company name. Content snippets are stored in Microsoft Dataverse, so you can centrally manage text content without modifying page templates.
- **Web files** – Use these to store and display image assets such as the company logo and the home page banner image. Web files are stored as Dataverse file attachments.

The following screenshot shows the content snippet list in the Power Pages Management app, filtered to show company-related snippets.

:::image type="content" source="media/portal-content-snippets.png" alt-text="Screenshot of the Active Content Snippets list in Power Pages Management showing the Home/CompanyName snippet." lightbox="media/portal-content-snippets.png":::

The following screenshot shows the web file list in the Power Pages Management app, showing the company logo web file.

:::image type="content" source="media/portal-web-files.png" alt-text="Screenshot of the Active Web Files list in Power Pages Management showing the companylogo.png web file." lightbox="media/portal-web-files.png":::

Use the Power Pages Management app to manage both content snippets and web files.

## Personalization areas

The following table summarizes the branding elements you can personalize and where to find detailed instructions.

| Branding element | Component type | Name | Learn more |
|---|---|---|---|
| Company logo | Web file and content snippet | *companylogo.png* and *Home/CompanyLogo* | [Update the company logo](personalize-portal-logo.md) |
| Company name | Content snippet | *Home/CompanyName* | [Update the company name](personalize-portal-company-name.md) |
| Home page banner image | Web file | *homepage-banner* | [Update the home page banner](personalize-portal-banner.md) |
| Registration and onboarding page text | Content snippets | *Registration/HeaderPageTitle* and *Header/VendorOnboarding* | [Update the home page banner](personalize-portal-banner.md) |

## Advanced personalization

Beyond branding, the Power Pages platform supports deeper configuration and customization through CSS, web templates, and page layouts. You control the portal's visual styling through CSS files, such as `dom.css`. Modify these files to adjust colors, fonts, spacing, and responsive behavior. Test any advanced personalization across different screen sizes and browsers to ensure consistent rendering.

> [!IMPORTANT]
> When you modify portal components directly in an environment, you create unmanaged layers in Dataverse that can affect solution management. Learn more in [Manage unmanaged customizations](personalize-portal-manage-customizations.md).

## Related information

- [Update the company logo on the supplier portal](personalize-portal-logo.md)
- [Update the company name on the supplier portal](personalize-portal-company-name.md)
- [Update banner texts and images](personalize-portal-banner.md)
- [Manage unmanaged customizations on the supplier portal](personalize-portal-manage-customizations.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
