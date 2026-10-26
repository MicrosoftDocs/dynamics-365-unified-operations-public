---
title: Rental management setup overview (preview)
description: Overview and recommended order for configuring the rental management module in Dynamics 365 Finance and Supply Chain Management.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Rental management setup overview (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Configuring rental management starts here. The following sections list the setup articles, the order to complete them in, and what each one delivers. Complete the steps in order because later steps depend on the configuration that you create in earlier ones.

## Setup sequence

Complete the setup articles in the order shown in the following table. Each step builds on the steps before it.

| Step | Article | What you configure | Why it comes here |
|---|---|---|---|
| 1 | [Configure prerequisites for rental management](set-up-rental-prerequisites.md) | Configure standard Supply Chain Management and Finance components: item model groups, item groups and inventory posting, tracking and storage dimension groups, sites, warehouses, journal names, fixed asset setup, the fixed asset posting profiles that rental management uses, and the rental security roles. | These standard components underpin everything else. |
| 2 | [Configure inventory and location settings for rental management](configure-inventory-location-settings.md) | Configure fleet types and their value tracking methods, posting configuration for fleet types, transfer rules, warehouses, and the rental location hierarchy.<br><br>Configure released products as fleet items after step 4 in this table because a released product needs a fleet item model and a rental class. | Fleet types must exist *before* you create fleet items, and their posting configuration and transfer rules must exist *before* you run fleet transfers. |
| 3 | [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md) | Configure period codes, invoice methods, and billing scenarios. | Period codes are referenced by rates, and billing scenarios are selected on rental templates, so they come before both. |
| 4 | [Set up rental reference data](set-up-rental-reference-data.md) | Configure posting journals, movement statuses, rental categories and classes, revenue categories, fleet item models, reservations, reason codes, and purchase option interest.<br><br>Learn more about availability status combinations in [Check fleet item availability and select fleet items](check-equipment-availability.md#configure-availability-status-combinations). | Classes and models provide the structure for fleet items and rates. Revenue categories, movement reason codes, and interest calculations support template setup. |
| 5 | [Set up rental templates](set-up-rental-templates.md) | Configure document defaults for billing, charges, payment terms, financial dimensions, movement automation, and rental purchase options. Set fleet type eligibility, customer assignments, and charge exemptions. | Templates reference the billing scenarios and reference data created in earlier steps. |
| 6 | [Configure rental parameters](configure-rental-parameters.md) | Configure legal entity-wide rules for fleet items, invoicing, pricing, posting, and reservations, plus per-user defaults and number sequences. | The parameters bring together the defaults and rules that use the templates and reference data configured in the earlier steps. |
| 7 | [Set up rental rates and discounts](set-up-rental-rates-discounts.md) | Configure book rates, customer and rental rate group rates, price factors, packages, dynamic pricing, discounts, and rate overrides. | You define rates per rental class and per period code, so both must exist first. Create the price factors before step 5 in this table because the rental parameters and the rental templates take their default application, shift, and location values from them. |
| 8 | [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md) | Purchase and receive fleet items, then transfer them into the rental fleet. | You can add fleet items only after completing the previous steps of this table. |

<!--
| 9 | [Set up the Dynamics 365 Supply Chain Management mobile app](set-up-rental-mobile-app.md) | Configure the feature toggles that the app needs, mobile device menu items and menus, the workers who sign in to the app, and the settings for photos and videos. | The app works from fleet item movements, so the fleet item movement status setup and the checklists from step 4 in this table must exist first. |
-->

> [!TIP]
> As part of step 2, set up **Fleet types** before you create fleet items, and set up **Posting configuration for fleet types** and **Transfer rules** before you run fleet transfers.

## Generate demo data

The rental management feature can generate demo data that lets you try out the module without needing to set up all the data prerequisites. It includes a full set of sample rental setup and data, such as rental categories, rental classes, and fleet types. It runs only in the *USMF* legal entity. Use it only in a demo or test environment.

When you report feedback, reproduce the issue with the *USMF* demo data whenever possible.

To generate the rental management demo data, follow these steps:

1. Turn on the feature and configuration key for your environment, as described in [Turn on rental management](set-up-rental-prerequisites.md#turn-on-feature).
1. Use the legal entity selector to go to the *USMF* company.
1. Go to **Rental management (Preview)** > **Demo data** > **Generate demo data**. Data generation starts immediately, without showing a confirmation dialog. It takes several minutes.

<!-- KFM: It might be helpful to list a few key records that are added here, including specific released products and others. -->

## Import setup data with data entities

You can import setup data through data entities. To do so, prepare the data in a spreadsheet and import it by using the **Data management** workspace, or use OData to read and write the data. The following table groups the entities by setup area, under the names that the **Data management** workspace shows.

| Setup area | Data entities |
|---|---|
| Fleet item reference data | <ul><li>Fleet item features</li><li>Fleet item translations</li><li>Fleet item availability status combinations</li><li>Excluded fleet item agreement statuses</li></ul> |
| Rental classes and templates | <ul><li>Rental class definitions for released products</li><li>Rental class fleet item lines</li><li>Rental class package lines</li><li>Rental template line class rules</li><li>Fleet type and fleet item or attachment eligibility</li></ul> |
| Customers and job sites | <ul><li>Rental job sites</li><li>Rental job site customer assignments</li><li>Rental job site prospect assignments</li></ul> |
| Reservations | <ul><li>Fleet item reservation types</li><li>Fleet item reservation request setups</li><li>Fleet item reservation request setup fleet types</li><li>Fleet item reservation setups</li><li>Fleet item reservation setup fleet types</li><li>Fleet item reservation headers</li><li>Fleet item reservation lines</li></ul> |
| Billing and pricing | <ul><li>Rental billing scenario prices</li><li>Rental period hours allowances</li><li>Rental dynamic price inventory level tiers</li><li>Rental dynamic price time utilization tiers</li><li>Rental dynamic price financial utilization tiers</li><li>Rental dynamic price past contract tiers</li><li>Rental dynamic price reservation tiers</li><li>Rental dynamic price period limits</li></ul> |
| Rental purchase option | <ul><li>Rental purchase option prime interest rates</li><li>Rental template purchase option periods</li><li>Rental document purchase option periods</li></ul> |

Three more entities are available for export only:

- Rental class exceptions
- Rental customer invoice journal headers
- Rental customer invoice journal lines

Import the entities in the setup order described earlier in this article because the data that they carry has the same dependencies.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Configure prerequisites for rental management](set-up-rental-prerequisites.md)
- [Configure inventory and location settings for rental management](configure-inventory-location-settings.md)
- [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Set up rental templates](set-up-rental-templates.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
<!-- - [Set up the Dynamics 365 Supply Chain Management mobile app](set-up-rental-mobile-app.md) -->
- [Understand rental management financial integration](understand-rental-financial-integration.md)
