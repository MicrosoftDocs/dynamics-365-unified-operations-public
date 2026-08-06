---
title: Configure capabilities (preview)
description: Configure capability hierarchies for products, segments, capability types, and qualities in Supplier Engagement.
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

# Configure capabilities (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Capabilities define how vendor offerings, specializations, and standards are organized in Supplier Engagement. By using predefined values, teams can classify vendors consistently and support better sourcing, qualification, and supplier management decisions. These settings also support hierarchical structures that make complex vendor profiles easier to manage.

## Capability areas

In the Supplier Engagement app, you can configure four types of capabilities:

- **Product categories** – Classify a vendor's products using a structured list based on industry standards. This classification helps you organize and search for vendors efficiently within the system. Examples include:
    - **Automotive components** – Tires, batteries, radiators, brakes
    - **Industrial machinery** – Cranes, forklifts, pumps, compressors
    - **Food and beverage** – Frozen meals, canned goods, baked goods, dairy products
    - **Construction materials** – Doors, roofing, cement, bricks, tiles

- **Segments** – Represent the broader product or service groups a vendor operates in. This representation helps you categorize vendors by the industries they serve. Examples include:
    - **Medical equipment** – Irradiation equipment, electro-medical devices, hospital furniture
    - **Electronic and electricals** – Lighting equipment, motors, generators, switches, connectors

- **Capability types** – Describe a vendor’s technical skills, manufacturing processes, and production capacity. This information helps you determine whether a vendor can meet operational or project-specific requirements. Examples include:
    - **Metal fabrication** – Bending, punching, stamping, tool manufacturing, progressive die stamping

- **Qualities** – Define the standards, certifications, and testing processes a vendor follows. This definition ensures vendors meet industry, customer, or regulatory requirements. Examples include:
    - **Inspection and testing** – Proof load testing, impact testing
    - **Certifications** – ISO 9001, FDA approval
    - **Processes** – PPAP levels, VDA levels
    - **Additional areas** – Compliance, traceability

## Capability hierarchies

All capability entities use parent-child hierarchies. For example, a product category such as *Automotive Components* can include child categories such as *Tires* and *Brakes*, while a capability type such as *Metal Fabrication* can include sub-capabilities such as *Stamping* and *Bending*.

These hierarchies use self-referential one-to-many relationships, so each record can link to a parent record of the same type. This approach supports flexible classification and helps users navigate vendor information efficiently.

## Create, delete, and edit capabilities

Use the following procedure to manage product categories, segments, capability types, and qualities.

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, under the **Capabilities** heading, select the capability entity that you want to set up: **Product categories**, **Segments**, **Capability types**, or **Qualities**.
1. Either open an existing record to edit it or, on the command bar, select **New** to create a record. You can also select **Delete** to remove a selected record.
1. Enter the following information for the new or selected record:
    - **Name** – Enter a descriptive name.
    - **Parent** – If the record belongs under another record of the same type, select the parent record to place it in the hierarchy.
1. Select **Save**.

## Related information

- [Configure the Supplier Engagement app overview](configure-app-overview.md)
- [Configure certificate types and organizations](configure-certificate-types.md)
- [Configure risk management elements](configure-risk-management.md)
- [Configure self-assessment questions](configure-self-assessment.md)
- [Configure Supplier Engagement app settings](configure-settings.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
