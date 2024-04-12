---
# required metadata

title: What's new or changed in Dynamics 365 Commerce 10.0.27 (July 2022)
description: This article describes features that are either new or changed in Dynamics 365 Commerce 10.0.27. 
author: josaw1
ms.date: 04/12/2024
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.custom:
  - bap-template
  - evergreen
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-04-30 
ms.dyn365.ops.version: 10.0.27

---

# What's new or changed in Dynamics 365 Commerce 10.0.27 (July 2022)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.27. This version has a build number of 10.0.1227 and is available on the following schedule:

- **Preview of release:** April 2022
- **General availability of release (self-update):** June 2022
- **General availability of release (auto-update):** July 2022


## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area   | Feature                                                  | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
|B2B   | Enable customer-specific catalogs    |   This feature enables customers to create Commerce product catalogs for Commerce business-to-business (B2B) sites. Creating catalogs allows customers to identify online stores that products are offered in, add products they want to include, and enhance product offerings by adding merchandising details. Customers can create multiple catalogs for each B2B online store.</br></br>For more information, see [Create Commerce catalogs for B2B sites](../catalogs-b2b-sites.md).   | Feature management<p>*Enable use of multiple catalogs on retail channels*   |
|E-commerce    |   Web API authentication transfer to e-commerce using Microsoft Entra ID B2C (Microsoft Entra B2C) | This feature enables customers to pass a valid Microsoft Entra B2C token into an e-commerce site from an external service. Users authenticated against the Microsoft Entra B2C tenant from a separate application or service can be sent to the e-commerce site to continue browsing as a signed-in authenticated user. | Developer opt-in |
| Globalization  |  Support of Global CFDI version 4.0 in electronic invoices for Mexico |   The Electronic Invoicing functionality for Mexico (Comprobante Fiscal Digital por Internet - CFDI) has been extended to meet the regulatory requirement for the version 4.0 of the Global CFDI format. The feature adds required changes to the layout including the following main changes:<p><p>- New retail-specific element "InformacionGlobal". <p>- Aggregation of all receipts that were issued to final consumers during a given period. <p>For more information, see [Global CFDI electronic invoices for Mexico](/dynamics365/finance/localizations/latam-mex-global-cfdi-3-3).     | CFDI version in Electronic invoice parameters. For more information, see [Electronic invoices (CFDI)](/dynamics365/finance/localizations/latam-mex-CFDI-electronic-invoices). |
| Globalization  | Display fiscal registration process details in POS             |      The feature provides a possibility to review the fiscal integration state, queue of audit events, connection parameters, and other related information on the **Settings** page of Commerce POS.<p><p>For more information, see [Set up the fiscal integration for Commerce channels](../localizations/setting-up-fiscal-integration-for-retail-channel.md)             |   Feature management<p>*Fiscal integration technical profiles overrides*             |
| Globalization  |    NF525 certification update for France           |    This update includes new capabilities according to the NF525 certification requirements for France:<p><p>-	Register the Void item audit event in the POS audit event log, and digitally sign it.<p>-	Export the Z-Report for a closed shift from Commerce HQ to an XML file.<p>The new *(France) Enable additional audit events in POS* feature provides the possibility to enable the registration and digital signing of all audit events for France without the need to explicitly enable corresponding extensions of Commerce runtime (CRT) and Commerce POS.<p>For more information, see [Cash register functionality for France.](../localizations/emea-fra-cash-registers.md).          | Feature management<p>*(France) Enable additional audit events in POS*<p>*(France) Enable exporting Z-Report to file*|     
| Payments  |  Enable Google Pay with Dynamics 365 Payment Connector for Adyen | E-commerce customers can use Google Pay on cart and checkout pages that are configured with the express checkout module. | Developer opt-in   |
|Sales tax   | [Show or hide tax breakdown in e-commerce when prices include sales tax](/dynamics365-release-plan/2022wave1/commerce/dynamics365-commerce/show-or-hide-tax-breakdown-e-commerce-when-prices-include-sales-tax)  |  Commerce shows tax breakup information in order summaries on cart, checkout, order confirmation, and order details pages. As of Commerce version 10.0.2, Commerce site builder includes an option that lets you hide the tax breakup information in order summaries. For more information, see [Hide tax breakup information in order summaries](../hide-taxes-breakup.md).   |  Site builder  |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Commerce 10.0.27 includes platform updates. To learn more, see [Platform updates for version 10.0.27 of finance and operations apps (July 2022)](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-27.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=673271).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
