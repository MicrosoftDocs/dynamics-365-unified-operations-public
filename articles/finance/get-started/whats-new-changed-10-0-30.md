---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.30 (November 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.30 preview release.
author: kfend
ms.date: 09/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30

---

# What's new or changed in Dynamics 365 Finance 10.0.30 (November 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.30. This version has a build number of 10.0.1362 and is available on the following schedule:

- **Preview of release:** September 2022
- **General availability of release (self-update):** October 2022
- **General availability of release (auto-update):** November 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|----|----|----|----|
| Accounts receivable | Free text invoice posting improvement for totals calculation | Performance improvements have been added to the free text invoice posting to enable it to run more efficiently. This enhancement works by saving calculated totals instead of recalculating the totals multiple times during the posting process. Therefore, the posting process will be shorter. | Feature management |
| General ledger | Enhanced performance for source document accounting framework | Performance improvements have been added to batch posting of source documents to enable it to run more efficiently. This feature will initially affect only batch posting of free text invoices. However, more source documents will be supported in future releases. When this feature is enabled, batch posting is split into smaller units of work to help prevent system degradation and reduce the chance of issues that are caused by database disconnections. | Feature management |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Credit and collections | Display the Known as field on the All customers page | This feature provides a way to view all fields on the **General** FastTab without having to select the **Show more fields** button. The **Known as** and **Phonetic name** fields will always be shown. These fields can now be added to the **All customers list view** page and remain in the list view. |
| Globalization | (ER) Embed images in Excel documents | [Electronic reporting (ER)](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) configurations can be designed to generate business documents in Excel format, based on an Excel template that contains an embedded image that has custom scaling and a custom aspect ratio. At runtime, this image is used as a placeholder for a picture in a generated business document. This improvement lets you [consider](../../fin-ops-core/dev-itpro/analytics/er-fillable-excel.md#cell-component) the actual scaling and aspect ratio of images that are used at runtime when they are added to generated documents. |
| Globalization | (ER) Inspect configured components | You can [validate](../../fin-ops-core/dev-itpro/analytics/er-components-inspections.md) every configured ER format and model mapping component at design time. During this validation, a consistency check runs to help prevent runtime issues that might occur. This improvement lets you detect any application artifacts (such as tables, classes, and methods) that have been marked as obsolete in the application code but are referred to in the evaluated ER component. You can use this information to revise the design of the evaluated ER component and remove references to obsolete artifacts before those artifacts are removed from the application code. In this way, the improvement helps prevent issues at runtime. |
| Globalization | (ER) Formula designer | The ER formula [editor](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting-formula-designer.md) lets you describe the data binding, control the process flow, specify the data formatting, and perform other tasks by using various data sources. This editor can use the [relative path](../../fin-ops-core/dev-itpro/analytics/er-formula-language.md#relative-path) to describe the location of any formula of a structured data source. This improvement lets you reveal the editable formula in the data source pane, among all available data sources, in one click. Therefore, you can quickly visualize the base element of the editable formula, observe its sibling elements, and use all this information in the formula as required. |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.30 includes platform updates. To learn more, see [Platform updates for version 10.0.30 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-30.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=745468).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 2 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
