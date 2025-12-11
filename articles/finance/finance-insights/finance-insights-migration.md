---
title: Finance Insights migration guide
description: This article provides comprehensive guidance for migrating from Finance Insights 1.0.0.x with Export to Data Lake to Finance Insights 1.2.x with Business Performance Analytics.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 12/10/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Finance Insights 1.2.x Migration

[!include [banner](../includes/banner.md)]

This article provides comprehensive guidance for migrating Finance Insights from 1.0.0.x to 1.2.x.

## Overview

Finance Insights is transitioning to Business Performance Analytics (BPA) as its data backend. This migration is necessary due to the Export to Data Lake service deprecation (November 2024, shutdown Q1 2026). Microsoft will manage the migration process for all customers.

**Important dates:**
- Export to Data Lake deprecated: November 2024
- Migration window: Now through Q1 2026
- Export to Data Lake discontinuation: Q1 2026

For more information about the Export to Data Lake deprecation, see [Export to Data Lake in finance and operations apps](../../fin-ops-core/dev-itpro/data-entities/finance-data-azure-data-lake.md).

## Migration benefits

The Finance Insights migration delivers four key benefits:

### 1. Improved data refresh performance

Data refresh is the process of extracting transaction data from Dynamics 365 Finance and Operations, transforming it for analytics, and making it available in BPA for Finance Insights predictions.

**Performance improvements come from:**
- Parallel processing of multiple entities simultaneously
- Incremental extraction (only changed data, not full snapshots)
- Optimized transformations with pre-computed aggregations
- Dataverse performance optimized for Power Platform workloads

### 2. Enhanced reliability and scalability

**Built-in reliability features:**
- Automatic retry logic for failed transformations
- Data validation ensuring consistency between Finance & Operations and BPA
- Data pipeline health monitoring and alerting
- Self-healing with automatic recovery from transient failures

**Scalability improvements:**
- Elastic compute that scales automatically with data volume
- Storage that can expand as needed
- Optimized for enterprises with many legal entities

**Proven track record:**
- BPA is generally available for Dynamics 365 customers
- 99% installation success rate
- 99% successful data flow rate
- Mature monitoring and diagnostics

### 3. Foundation for future capabilities

The BPA backend provides a modern, extensible platform that enables Microsoft to deliver new Finance Insights features more rapidly.

**Modern platform architecture:**
- Dimensional data model covering full Order-to-Cash value chain and beyond
- Extensible design with new dimensions and facts added quarterly
- Mature infrastructure leveraging proven BPA capabilities

**Potential future capabilities:**

While specific features and dates have not been committed, the BPA backend enables possibilities such as:
- Enhanced forecasting and prediction scenarios
- Expanded integrations with other Microsoft products
- Advanced analytics and customizable dashboards

### 4. Seamless integration with BPA analytics

If you use or plan to use Business Performance Analytics, Finance Insights now shares the same data foundation, eliminating data inconsistencies and enabling unified analysis.

**Single source of truth:**
- Finance Insights predictions based on same BPA analytical models
- Unified Order-to-Cash facts and dimensions
- Synchronized data refresh schedules

## Migration process

### Microsoft-managed process

Microsoft will handle the migration for all customers. You will:
1. Receive advance notification (minimum 30 days before migration)
2. Be informed of your migration schedule & status
3. Receive support throughout the migration process

You do **not** need to:
- Manually uninstall Export to Data Lake
- Manually configure BPA for Finance Insights
- Migrate your machine learning models (Microsoft handles this)
- Recreate your predictions

### Opting out of migration

If you choose not to migrate, you will lose access to Finance Insights features after Q1 2026 when Export to Data Lake is discontinued. There is no option to continue using Finance Insights 1.0.0.x beyond that date.

If you'd like to opt out of the migration and discontinue using Finance Insights entirely, you must uninstall Finance Insights before your scheduled migration date. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md). Note that uninstalling Finance Insights will remove all Finance Insights functionality, including your prediction models and historical data.

### What's changed

**Storage:**
- From: Azure Data Lake
- To: Dataverse

**Data pipeline:**
* From: Export to Data Lake
* To: Business Performance Analytics

### What stays the same

**Finance Insights features:**
- Customer payment predictions
- Cash flow forecasting
- Same user interface in Dynamics 365 Finance
- Same AI Builder integration

**Your models:**
- Existing prediction models preserved
- Historical predictions retained
- No retraining required (models transfer automatically)

**User experience:**
- Finance Insights workspaces unchanged
- Same workflows for predictions
- Same AI Builder credit usage model

## Getting support

For questions and support on this migration, contact Microsoft Support at https://support.microsoft.com/en-us

When contacting support, provide:
- Environment ID and name
- Migration date
- Specific error messages or issues
- Screenshots of problems
- Steps to reproduce the issue

## Additional resources

- [Finance Insights migration FAQ](finance-insights-migration-faq.md) - Common questions about migration
- [Business Performance Analytics home page](../business-performance-analytics/business-performance-analytics-home-page.md) - Understanding BPA
- [Finance insights home page](finance-insights-home-page.md) - Overview of Finance Insights
- [Uninstall Finance insights](uninstall-finance-insights.md) - Opt-out instructions

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

---

**Last updated:** December 2025
**Applies to:** Customers using Finance Insights 1.0.0.x
**Migration deadline:** Q1 2026
