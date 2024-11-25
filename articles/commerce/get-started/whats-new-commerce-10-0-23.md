---
# required metadata

title: What's new or changed in Dynamics 365 Commerce 10.0.23 (January 2022)
description: This article describes features that are either new or changed in the preview release of Dynamics 365 Commerce 10.0.23. 
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
ms.search.validFrom: 2021-10-15 
ms.dyn365.ops.version: 10.0.23

---
# What's new or changed in Dynamics 365 Commerce 10.0.23 (January 2022)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.23. This version has a build number of 10.0.1037 and is available on the following schedule:

- **Preview of release:** October 2021
- **General availability of release (self-update):** December 2021


## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature. We may update this article to include features that made it into the build after this article was initially published. To determine how to turn on a feature, refer to the **Enabled by** column in the following table. For more information about how to use Feature management, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature area   | Feature                                                  | More information                                          |  Enabled by             |
|----------------|----------------------------------------------------------|-----------------------------------------------------------|-------------------------|
| Dynamics 365 Sales integration |   Leverage Dynamics 365 Sales for managing leads generated from a Commerce business-to-business (B2B) site.  | Use Sales to manage business partner approvals for Commerce B2B websites. Organizations that have already invested in the Sales solution can use its lead and opportunity concepts for the B2B e-commerce business partner approval process. See [Manage business partner users on B2B e-commerce websites using Dynamics 365 Sales](../b2b/prospect-management-sales.md) for more details. | Use the App source  |
|  Global address book| Define a default state/province for each country/region in address setup | You can now define a default state/province for each country/region in the address setup for the global address book. When a default state/province is set, it will be the default value entered in state/province fields when you create a new county or city record for that country/region. For more information, see [Address setup](../../fin-ops-core/fin-ops/organization-administration/global-address-book-address-setup.md). | Enabled by default |
|   Globalization |  [(India) GST in e-commerce](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/gst-e-commerce-india)    |  This feature enables Dynamics 365 Commerce customers in India to implement e-commerce capabilities by ensuring that Goods and Services Tax (GST) is calculated on e-commerce orders. For more information, see [Goods and Services Tax (GST) integration for e-commerce sites for India](../localizations/apac-ind-e-commerce.md).  |  Feature management  |
|   Globalization |   (Eastern Europe) Improvements in settlement of sales invoices and payments for retail statements   |  The feature ensures correct automatic settlement of sales invoices and payments that are generated from retail statements. The feature is applicable to the Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, and Russia.   |  Enabled by default  |
|   Merchandising |   [Improved pricing computation performance by using flattened discount tables](/dynamics365-release-plan/2021wave2/commerce/dynamics365-commerce/improved-pricing-computation-performance-using-flattened-discount-tables)   |   [Retail discounts](../retail-discounts-overview.md)  |  Feature management (*Improve discount computation performance by using flattened discount tables feature.*)  |
|   Office integration  |   Create email templates for transactional events  |  [Create email templates for transactional events](../email-templates-transactions.md)   | Enabled by default  |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Commerce 10.0.23 includes platform updates. To learn more, see [Platform updates for version 10.0.23 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23.md).

### Bug fixes 
For information about the bug fixes that are included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=627874).

For Commerce-specific breaking changes, view the [Dynamics 365 Commerce online SDK FAQ](../e-commerce-extensibility/sdk-faq.md).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that have been removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

