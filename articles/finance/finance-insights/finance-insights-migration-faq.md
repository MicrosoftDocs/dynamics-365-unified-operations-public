---
title: Finance insights migration FAQ
description: This article answers frequently asked questions about migrating from Finance insights 1.0.0.x with Export to Data Lake to Finance insights 1.2.x with Business performance analytics.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 12/09/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Finance insights migration FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently asked questions about migrating from Finance insights 1.0.0.x with Export to Data Lake to Finance insights 1.2.x with Business performance analytics.


### Why is this migration happening?
Microsoft is modernizing Finance insights to use Business performance analytics as its data backend instead of Export to Data Lake. This provides better performance, reliability, and aligns with Microsoft's Power Platform strategy. Export to Data Lake is being deprecated and will be discontinued early in 2026.

### When do I need to migrate?
You must migrate before early in 2026 when Export to Data Lake is discontinued. Microsoft manages the migration process and contacts you at least 30 days before your scheduled migration window. You don't need to take immediate action.

### Do I have to migrate?
Yes, if you want to continue using Finance insights. Export to Data Lake will be discontinued early in 2026, and Finance insights 1.0.0.x will no longer function after that date. The migration to Finance insights 1.2.x with Business performance analytics is required to maintain functionality.

### Who manages the migration?
Microsoft manages the migration process. You'll receive advance notice and preparation instructions, but Microsoft performs the actual migration of your Finance insights configuration and models.

### How much does the migration cost?
There is no separate migration fee. However, Finance insights 1.2.x requires Business performance analytics, which is included with Dynamics 365 Finance licenses. You may need to purchase additional Dataverse capacity depending on your data volume.

### Can I opt out of the migration?
If you choose not to migrate, you'll lose access to Finance insights features when Export to Data Lake is discontinued. There's no option to continue using Finance insights 1.0.0.x after this is discontinued. 

If you'd like to opt out of the migration and discontinue using Finance insights entirely, uninstall Finance insights before your scheduled migration date. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md). Uninstalling Finance insights removes all Finance insights functionality, including prediction models and historical data.


### How will I know when my migration is scheduled?
Microsoft will contact you using email and LCS notifications at least 30 days before your scheduled migration. The notification includes your specific migration window and preparation checklist.

### What version of Dynamics 365 Finance do I need?
You must be on Dynamics 365 Finance version 10.0.38 or later before migration. If you're on an earlier version, you need to upgrade before Microsoft can migrate your Finance insights configuration.

### Do I need to install Business performance analytics?
No, Microsoft installs Business performance analytics version 2.3 or later as part of the migration process. 

### Will my environment be down during migration?
Your Dynamics 365 Finance environment remains available during migration. However, Finance insights features (payment predictions, cash flow forecasting) will be unavailable for 2-4 hours during the migration window. Plan the migration during a low-usage period if possible.

### How long does migration take?
The migration typically takes 2-4 hours. Microsoft provides a specific timeframe when they schedule your migration. During this time, Finance insights features are unavailable, but the rest of your Finance environment remains accessible.

### Can users still work in Dynamics 365 Finance during migration?
Yes, users can continue working in Finance during migration. Only Finance insights features (payment predictions, cash flow forecasting workspaces) are temporarily unavailable.

### What if something goes wrong during migration?
Microsoft's migration team monitors the process and resolves any issues. If migration fails, Microsoft works with you to reschedule and address any blocking issues. Your original Finance insights 1.0.0.x configuration remains intact until migration completes successfully.

### Will I lose my prediction models?
No, customer payment prediction models and cash flow forecast models are automatically migrated and preserved. 

### Will historical prediction data be preserved?
Yes, historical predictions and model training data are preserved during migration. You maintain continuity in your prediction accuracy and historical analysis.

### Do I need to reconfigure Finance insights features?
No, your Finance insights feature configurations are migrated automatically. Users can access the same workspaces and features without reconfiguration.

### How long before predictions start working again?
After migration completes, Business performance analytics performs an initial data sync. This can take several hours depending on your data volume. Predictions resume automatically after the data sync completes.

### What's the difference between Finance insights 1.0.0.x and 1.2.x?
Finance insights 1.0.0.x:
- Uses Export to Data Lake as part of the data pipeline
- Data stored in Azure Data Lake
- More complex configuration

Finance insights 1.2.x:
- Uses Business performance analytics as data backend
- Automatic data sync via Business performance analytics
- Data stored in Dataverse
- Simplified configuration
- Better performance and reliability

### How does Business performance analytics integration work?
Business performance analytics syncs data from Dynamics 365 Finance to Dataverse automatically. Finance insights 1.2.x reads from Business performance analytics's Dataverse tables instead of from Azure Data Lake. 

### What Business performance analytics components does Finance insights use?
Finance insights reads from standard Business performance analytics analytical entities for general ledger, customer transactions, and other financial data. Business performance analytics maintains these tables automatically as it syncs from Finance.

### Do I need separate Business performance analytics licenses?
Business performance analytics is included with Dynamics 365 Finance licenses. You don't need separate Business performance analytics licenses.

### Will AI Builder credit usage change?
AI Builder credit usage remains the same. Finance insights continues to use the same AI Builder models and credit consumption patterns. Each Finance tenant receives 20,000 AI Builder credits monthly.

### Can I test the migration in a sandbox first?
Microsoft's migration process is designed to be low-risk and is tested extensively. However, if you have multiple environments (production and sandbox both using Finance insights), Microsoft will typically migrate sandbox environments first to allow you to validate before production migration.

### What if I have multiple environments?
If you have multiple Finance environments using Finance insights (for example, production and sandbox), each environment needs to be migrated separately. Microsoft coordinates migration schedules with you.

### Do Finance insights features work differently after migration?
The user experience remains the same. The Finance insights workspaces, prediction workflows, and AI models function identically. Only the underlying data pipeline changes from Export to Data Lake to Business performance analytics.

### How much Dataverse capacity will I need?
Dataverse usage varies based on:
- Organization size
- Number of legal entities
- Transaction volume
- Amount of historical data

Small to medium organizations typically have sufficient capacity included with Finance licenses. Large organizations may need additional Dataverse capacity.

### Is Business performance analytics included in my Finance license?
Yes, Business performance analytics is included with Dynamics 365 Finance licenses. No separate Business performance analytics license is required.

### What happens if I run out of Dataverse capacity?
If you exceed your Dataverse capacity, you'll receive notifications in the Power Platform admin center. Finance insights may experience performance issues or data sync delays. Purchase additional capacity to resolve this.

## Troubleshooting

 - Finance insights features aren't working after migration
1. Wait for initial Business performance analytics data sync to complete (can take several hours)
2. Verify Business performance analytics is syncing data from Finance successfully
3. Check AI Builder credits are available
4. Verify no errors in the Business performance analytics workspace
5. Wait 24 hours after migration for full data refresh

If issues persist after 24 hours, contact Microsoft support.

If Business performance analytics shows errors after migration, contact Microsoft support immediately and provide:
- Your environment ID
- Error messages from Business performance analytics workspace
- Migration completion date/time
- Screenshots of errors


### Should I upgrade to Finance 10.0.38 before or during migration?
Upgrade to Finance 10.0.38 and later before your scheduled migration. The migration can't proceed if you're on an earlier version. Plan your Finance upgrade well in advance of migration.

### Can I delay migration beyond Q1 2026?
No, Export to Data Lake will be discontinued early 2026, and Finance insights 1.0.0.x will stop functioning. All migrations must be completed before that deadline.

### What happens if I don't migrate by early 2026?
Finance insights features stop working when Export to Data Lake is discontinued. You lose:
- Customer payment predictions
- Cash flow forecasting
- All Finance insights functionality

If you don't want to migrate, uninstall Finance insights before your scheduled migration date. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).

### Will customer payment predictions work the same way?
Yes, customer payment predictions function identically after migration. Your trained models are preserved, and predictions continue with the same accuracy and workflow.

### Will cash flow forecasting work the same way?
Yes, cash flow forecasting maintains the same functionality. Your forecast models and historical forecasts are preserved during migration.

### What about Budget proposals feature?
Budget proposals feature was deprecated in Finance insights 1.2.x and is no longer available after migration. If you currently use Budget proposals, plan alternative budgeting workflows before migration.

### Can I still train new prediction models?
Yes, you can train new customer payment prediction models and cash flow forecast models after migration.

### Will prediction accuracy change?
No, the migration preserves your trained models and historical data. Prediction accuracy remains consistent after migration.


### What's the overall migration timeline?
Phase 1 - Notification: Microsoft contacts you at least 30 days before migration.
Phase 2 - Preparation: You prepare environment, or uninstall Finance insights if you don't wish to be migrated.
Phase 3 - Migration: Microsoft performs migration.
Phase 4 - Validation: You verify functionality. 
Phase 5 - Decommission: Microsoft removes old configuration.

### Can I perform the migration myself?
No, this is a Microsoft-managed migration. Microsoft performs the technical migration to ensure data integrity and model preservation. You're responsible for validation and updating any custom integrations afterward.

### What if I need to reschedule?
Microsoft schedules your migration with advance notice. If the scheduled date doesn't work for your organization, you must uninstall Finance insights before the scheduled migration date to opt out of the migration. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).

### Is there a rollback plan if migration fails?
Yes, if the migration fails, Microsoft rolls back to your original Finance insights 1.0.0.x configuration. Your environment and data remain safe during migration attempts.

#### Additional resources

- [Business performance analytics home page](../business-performance-analytics/business-performance-analytics-home-page.md)
- [Finance insights home page](finance-insights-home-page.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
