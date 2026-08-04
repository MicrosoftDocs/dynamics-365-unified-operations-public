---
title: Configure the Supplier Engagement app overview (preview)
description: Set up foundational Supplier Engagement configuration data to support onboarding, vendor management, risk assessment, and collaboration.
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

# Configure the Supplier Engagement app overview (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Supplier Engagement configuration establishes the reference data that supports supplier onboarding, vendor management, risk assessment, and collaboration. When these entities are set up correctly, users can work with consistent options and complete related processes without missing required values. Planning this setup early helps the rest of the app work as intended.

## Why configuration matters

Configuration matters for the following reasons:

- Accurate setup ensures that users see only valid options during onboarding, vendor management, and risk assessment.
- If required configuration is missing, users might not be able to complete related tasks such as assigning certificates or categorizing vendors.
- Features such as onboarding questionnaires, risk management, and compliance tracking depend on these entities being available in advance.

For example, if you want vendors to provide a specific certificate during onboarding, you must first define the certificate type and certifying organization. Likewise, if you want to segment vendors by industry, you must first configure the relevant segments and product categories.

## Configuration entities and dependent features

The following table summarizes each configuration entity, its purpose, and the features that depend on it.

| Configuration entity | Purpose | Dependent features |
| --- | --- | --- |
| Certificate types | Defines standard types of certificates vendors can hold. | Vendor certification management, onboarding |
| Certifying organizations | Stores recognized bodies that issue certificates. | Vendor certification management |
| Product categories | Classifies vendor offerings and supports a hierarchical structure. | Vendor registration, product and service assignment |
| Segments | Further classifies vendors for reporting and management. | Vendor segmentation, analytics |
| Capability types | Categorizes vendor skills and capabilities. | Capability assignment, vendor qualification |
| Qualities | Defines specific attributes or standards that vendors might have. | Vendor qualification, compliance checks |
| Risk scenarios | Identifies potential risks that are associated with vendors. | Risk assessment, corrective action planning |
| Corrective action types | Defines actions to mitigate identified risks. | Risk management, compliance tracking |
| Self-assessment questions | Evaluates vendor suitability during onboarding. | Vendor onboarding, qualification |
| Global vendor types | Classifies vendors for reporting and management. | Vendor registration, reporting |
| Countries/regions | Maintains a list of countries/regions for vendor classification. | Vendor registration, compliance, reporting |
| Hold reasons | Explains why a vendor is placed on hold. | Vendor management, compliance, audit |

<!-- KFM: Add mention **Portal Management > Contacts** and **Portal Management > Portal accesses** -->

> [!NOTE]
> You can import all configuration data by using Excel. Learn more in [/power-apps/user/import-data](/power-apps/user/import-data).

## Related information

- [Configure certificate types and organizations](configure-certificate-types.md)
- [Configure capabilities](configure-capabilities.md)
- [Configure risk management elements](configure-risk-management.md)
- [Configure self-assessment questions](configure-self-assessment.md)
- [Configure Supplier Engagement app settings](configure-settings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
