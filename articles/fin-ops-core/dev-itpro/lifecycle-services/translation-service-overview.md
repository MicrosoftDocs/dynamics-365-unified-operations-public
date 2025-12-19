---
title: Dynamics 365 Translation Service overview
description: Learn about the Microsoft Dynamics 365 Translation Service (DTS), including a table that outlines various supported projects.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 12/19/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.collection: get-started 
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ejchoGIT
---

# Dynamics 365 Translation Service overview

[!include [banner](../includes/banner.md)]
[!INCLUDE[dts-deprecation](../../fin-ops/includes/dts-deprecation.md)]

The Microsoft Dynamics 365 Translation Service (DTS) is hosted in Microsoft Dynamics Lifecycle Services. It enhances the experience for partners and independent software vendors (ISVs) when they translate their solutions or add a new language for [supported Dynamics products](./translation-service-overview.md#supported-products).

If you want to learn the basics and best practices of DTS, consider completing the [Translate Dynamics 365 apps and documentation with Dynamics 365 Translation Service](/training/modules/dynamics-translation-service/) module.

DTS uses product-specific machine translation (MT) models that are custom-trained for [Microsoft General Availability (GA) languages](./translation-service-overview.md#glossary) to maximize the quality of the translation output. DTS also supports translation recycling from the linguistic assets of Microsoft Dynamics and partners/ISVs. Therefore, identical strings are translated one time and then consistently reused.

The following illustration shows, at a high level, how the service works.

:::image type="content" source="./media/dts-overview.png" alt-text="Screenshot of How DTS works.":::

> [!NOTE]
> To use this feature, you need a license for finance and operations apps, Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, or Dynamics 365 Project Operations.

## Custom-trained MT model

DTS uses a Microsoft Translator service and a custom translator to customize Microsoft Translator's advanced neural machine translation for Microsoft Dynamics products. You can use the custom-trained MT model for requests if the source or target language is English and partners upload XLIFF TM files that contain more than 10,000 translation units (TUs). (A TU typically contains a source string, translation, state, state qualifier, and note.) In those cases, DTS creates a custom-trained MT model that's specific to the translation request that the XLIFF TM files are submitted for.

## Supported products

DTS currently supports the following product versions.

| Product name | Versions | Supported format for user interface files | Supported format for documentation files | Notes |
|--------------|----------|-------------------------------------------|------------------------------------------|-------|
| Microsoft Dynamics AX 2012 | All versions | .ktd, .ald | .docx | Alignment is the only supported functionality for this product. |
| Dynamics 365 finance and operations apps | All versions | .label.txt | .docx, .html | .txt is the specific label format and .html is the custom help solution format. |
| Microsoft Dynamics 365 Commerce | All versions | .label.txt | .docx | |
| Microsoft Dynamics CRM | All versions | .resx | .docx | |
| Microsoft Dynamics NAV | All versions | .etx, .stx, .resx, .txt, .xml, .xlf | .docx | .txt and .xml are the NAV specific format, and .xlf is the Business Central extension resource format. |

## Accessing DTS

You can access DTS in two places in Lifecycle Services:

- From the Lifecycle Services home page
- From within a Lifecycle Services project

### Accessing DTS from the Lifecycle Services home page

Sign in to Lifecycle Services, and scroll to the right side of the page. Expand the tiles waffle, and then select the **Translation service** tile to open the dashboard view for DTS.

### Accessing DTS from within a Lifecycle Services project

Create a new project, or open an existing project. On the project dashboard, in the **More tools** section, select the **Translation service** tile. Alternatively, on the project dashboard, select the **Menu** button, then select **Translation service**.

### Accessing DTS from the Lifecycle Services home page vs. accessing it from within a Lifecycle Services project

When you access DTS from the Lifecycle Services home page and create a translation request, you can select the product that you want to use for the request. To add more requests that use different products, you can just change the product selection. You don't have to close the service and open a different translation project. This option is convenient when you work on multiple product translation projects.

The following illustration shows an example of the DTS dashboard that you open from the Lifecycle Services home page. This dashboard shows all requests that users from your organization made from the home page (outside a Lifecycle Services project).

:::image type="content" source="./media/dts-home-dashboard.png" alt-text="Screenshot of DTS dashboard that is opened from the Lifecycle Services home page.":::

Because a Lifecycle Services project is always tied to a product, any translation request that you submit from a project automatically carries the product type and version information from the project. You can't select a different product for the request.

The following illustration shows an example of the DTS dashboard that you open from within a Lifecycle Services project. Only the project owner and users who have access to the project can see these requests. Therefore, this option is useful when you work with a group of people on one product translation project in Lifecycle Services.

:::image type="content" source="./media/dts-project-dashboard.png" alt-text="Screenshot of DTS dashboard that is opened from within a project.":::

In both situations, users who can view the request have read access. However, to regenerate the request, they must take ownership of it in the dashboard.

## Glossary

| Term | Description |
|------|-------------|
| XLIFF | XML Localization Interchange File Format. XLIFF is an XML-based format. It standardizes the way tools pass localizable data during a localization process. It also serves as a common format for files that computer-aided translation (CAT) tools use. |
| Microsoft GA languages | General availability of the Microsoft-produced languages. The list varies, depending on the product. |
| TU | Translation unit. A TU typically contains a source string, translation, state, state qualifier, and note. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
