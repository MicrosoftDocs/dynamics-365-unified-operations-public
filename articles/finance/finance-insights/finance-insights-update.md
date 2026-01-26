---
title: Finance insights update guide
description: This article provides guidance for updating from Finance insights 1.0.0.x with Export to Data Lake to Finance insights 1.2.x with Business performance analytics.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 12/10/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Finance insights 1.2.x update

[!include [banner](../includes/banner.md)]

This article provides comprehensive guidance for updating Finance insights from 1.0.0.x to 1.2.x.

## Overview

Finance insights is transitioning to Business performance analytics as its data backend. This update is necessary due to the deprecation of the Export to Data Lake service. Microsoft manages the update process for all customers.

> [!IMPORTANT]
> **Important dates:**
>
> - Export to Data Lake deprecated: November 2024
> - Update window: February 1, 2026 (midnight UTC) through March 31, 2026 (midnight UTC)
> - Export to Data Lake discontinuation: February 2026

For more information about the Export to Data Lake deprecation, see [Export to Data Lake in finance and operations apps](../../fin-ops-core/dev-itpro/data-entities/finance-data-azure-data-lake.md).

### Migration benefits

The Finance insights update delivers four key benefits:

1. Improved data refresh performance - Data refresh is the process of extracting transaction data from Dynamics 365 finance and operations, transforming it for analytics, and making it available in Business performance analytics for Finance insights predictions.
   Performance improvements come from:
   - Parallel processing of multiple entities simultaneously
   - Incremental extraction (only changed data, not full snapshots)
   - Optimized transformations with precomputed aggregations
   - Dataverse performance optimized for Power Platform workloads

1. Enhanced reliability and scalability:
   - Automatic retry logic for failed transformations
   - Data validation ensuring consistency between Dynamics 365 Finance and operations and Business performance analytics
   - Data pipeline health monitoring and alerting
   - Self-healing with automatic recovery from transient failures
   - Scalability improvements:
     - Elastic compute that scales automatically with data volume
     - Storage that can expand as needed
     - Optimized for enterprises with many legal entities

1. The Business performance analytics backend provides a modern, extensible platform that enables Microsoft to deliver new Finance insights features more rapidly.
   - Dimensional data model covering full Order-to-Cash value chain and beyond
   - Extensible design with new dimensions and facts added quarterly
   - Mature infrastructure using proven Business performance analytics capabilities

1. Seamless integration with Business performance analytics - If you use or plan to use Business performance analytics, Finance insights now shares the same data foundation, eliminating data inconsistencies and enabling unified analysis.
   - Finance insights predictions based on same Business performance analytics analytical models
   - Unified Order-to-Cash facts and dimensions
   - Synchronized data refresh schedules

### Migration process

Microsoft handles the update for all customers. Customers receive advance notification (at least 30 days before update), are informed of the update schedule and status, and receive support throughout the update process.

Customers don't need to manually uninstall Export to Data Lake, configure Business performance analytics for Finance insights, update machine learning models, or recreate predictions.

### Opting out of update

If you choose not to update, you will lose access to Finance insights features when Export to Data Lake is discontinued. There's no option to continue using Finance Insights 1.0.0.x.

If you want to opt out of the update and discontinue using Finance insights entirely, you must uninstall Finance insights before February 1, 2026. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).
Uninstalling Finance insights removes all Finance insights functionality, including prediction models and historical data.

### What's changed

**Storage:**  
From: Azure Data Lake  
To: Dataverse  

**Data pipeline:**  
From: Export to Data Lake  
To: Business performance analytics  

### What stays the same

**Finance insights features:**

- Customer payment predictions
- Cash flow forecasting
- Same user interface in Dynamics 365 Finance
- Same AI Builder integration

**Your models:**

- Existing prediction models
- Historical predictions retained
- No retraining required - models transfer automatically

**User experience:**

- Finance insights workspaces unchanged
- Same workflows for predictions
- Same AI Builder credit usage model

### Getting support

For questions and support on this update, contact Microsoft support and provide:

- Environment ID and name
- Migration date
- Specific error messages or issues
- Screenshots of problems
- Steps to reproduce the issue

#### Additional resources

- [Finance insights update FAQ](finance-insights-update-faq.md) - Common questions about update
- [Business performance analytics home page](../business-performance-analytics/business-performance-analytics-home-page.md)
- [Finance insights home page](finance-insights-home-page.md) - Overview of Finance Insights
- [Uninstall Finance insights](uninstall-finance-insights.md) - Opt-out instructions

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

---

**Last updated:** December 2025  
**Applies to:** Customers using Finance Insights 1.0.0.x  
**Update deadline:** March 31, 2026
