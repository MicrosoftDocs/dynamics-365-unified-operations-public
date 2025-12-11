---
title: Finance Insights migration FAQ
description: This article answers frequently asked questions about migrating from Finance Insights 1.0.0.x with Export to Data Lake to Finance Insights 1.2.x with Business Performance Analytics.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: article
ms.date: 12/09/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Finance Insights migration FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently asked questions about migrating from Finance Insights 1.0.0.x with Export to Data Lake to Finance Insights 1.2.x with Business Performance Analytics (BPA).

## General Questions

### Why is this migration happening?

Microsoft is modernizing Finance Insights to use Business Performance Analytics (BPA) as its data backend instead of Export to Data Lake. This provides better performance, reliability, and aligns with Microsoft's Power Platform strategy. Export to Data Lake is being deprecated and will be discontinued in Q1 2026.

### When do I need to migrate?

You must migrate before Q1 2026 when Export to Data Lake is discontinued. Microsoft will manage the migration process and will contact you at least 30 days before your scheduled migration window. You don't need to take immediate action - wait for Microsoft's notification.

### Do I have to migrate?

Yes, if you want to continue using Finance Insights. Export to Data Lake will be discontinued in Q1 2026, and Finance Insights 1.0.0.x will no longer function after that date. The migration to Finance Insights 1.2.x with BPA is required to maintain functionality.

### Who manages the migration?

Microsoft manages the migration process. You will receive advance notice and preparation instructions, but Microsoft will perform the actual migration of your Finance Insights configuration and models.

### How much does the migration cost?

There is no separate migration fee. However, Finance Insights 1.2.x requires Business Performance Analytics, which is included with Dynamics 365 Finance licenses. You may need to purchase additional Dataverse capacity depending on your data volume.

### Can I opt out of the migration?

If you choose not to migrate, you will lose access to Finance Insights features after Q1 2026 when Export to Data Lake is discontinued. There is no option to continue using Finance Insights 1.0.0.x beyond that date.

If you'd like to opt out of the migration and discontinue using Finance Insights entirely, you must uninstall Finance Insights before your scheduled migration date. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md). Note that uninstalling Finance Insights will remove all Finance Insights functionality, including your prediction models and historical data.

## Before Migration

### How will I know when my migration is scheduled?

Microsoft will contact you via email and LCS notifications at least 30 days before your scheduled migration. The notification will include your specific migration window and preparation checklist.

### What version of Dynamics 365 Finance do I need?

You must be on Dynamics 365 Finance version 10.0.38 or later before migration. If you're on an earlier version, you'll need to upgrade before Microsoft can migrate your Finance Insights configuration.

### Do I need to install Business Performance Analytics myself?

No. Microsoft will install BPA version 2.3 or later as part of the migration process. You don't need to install or configure BPA in advance.

### Will my environment be down during migration?

Your Dynamics 365 Finance environment will remain available during migration. However, Finance Insights features (payment predictions, cash flow forecasting) will be unavailable for 2-4 hours during the migration window. Plan the migration during a low-usage period if possible.

## During Migration

### How long does migration take?

The migration typically takes 2-4 hours. Microsoft will provide a specific timeframe when they schedule your migration. During this time, Finance Insights features will be unavailable, but the rest of your Finance environment remains accessible.

### Can users still work in Dynamics 365 Finance during migration?

Yes. Users can continue working in Finance during migration. Only Finance Insights features (payment predictions, cash flow forecasting workspaces) will be temporarily unavailable.

### What if something goes wrong during migration?

Microsoft's migration team will monitor the process and resolve any issues. If migration fails, Microsoft will work with you to reschedule and address any blocking issues. Your original Finance Insights 1.0.0.x configuration will remain intact until migration completes successfully.

## After Migration

### Will I lose my prediction models?

No. Your customer payment prediction models and cash flow forecast models are automatically migrated and preserved. You don't need to retrain models after migration.

### Will historical prediction data be preserved?

Yes. Historical predictions and model training data are preserved during migration. You'll maintain continuity in your prediction accuracy and historical analysis.

### Do I need to reconfigure Finance Insights features?

No. Your Finance Insights feature configurations are migrated automatically. Users can access the same workspaces and features without reconfiguration.

### How long before predictions start working again?

After migration completes, BPA needs to perform an initial data sync. This can take several hours depending on your data volume. Predictions will resume automatically once the data sync completes.

### Can I still use Export to Data Lake for other purposes?

The migration only affects Finance Insights. If you use Export to Data Lake for other purposes (not Finance Insights), that functionality is unaffected by this migration. However, note that Export to Data Lake as a whole is being deprecated - check Microsoft's guidance for your other Export to Data Lake use cases.

## Technical Questions

### What's the difference between Finance Insights 1.0.0.x and 1.2.x?

**Finance Insights 1.0.0.x:**
- Uses Export to Data Lake as part of the data pipeline
- Data stored in Azure Data Lake
- More complex configuration

**Finance Insights 1.2.x:**
- Uses Business Performance Analytics as data backend
- Automatic data sync via BPA
- Data stored in Dataverse
- Simplified configuration
- Better performance and reliability

### How does BPA integration work?

BPA syncs data from Dynamics 365 Finance to Dataverse automatically. Finance Insights 1.2.x reads from BPA's Dataverse tables instead of from Azure Data Lake. This provides a more reliable, performant data pipeline.

### What BPA components does Finance Insights use?

Finance Insights reads from standard BPA analytical entities for general ledger, customer transactions, and other financial data. BPA maintains these tables automatically as it syncs from Finance.

### Do I need separate BPA licenses?

Business Performance Analytics is included with Dynamics 365 Finance licenses. You don't need separate BPA licenses.

### Will AI Builder credit usage change?

AI Builder credit usage remains the same. Finance Insights continues to use the same AI Builder models and credit consumption patterns. Each Finance tenant receives 20,000 AI Builder credits monthly.

### Can I test the migration in a sandbox first?

Microsoft's migration process is designed to be low-risk and is tested extensively. However, if you have multiple environments (production and sandbox both using Finance Insights), Microsoft will typically migrate sandbox environments first to allow you to validate before production migration.

### What if I have multiple environments?

If you have multiple Finance environments using Finance Insights (e.g., production and sandbox), each environment will need to be migrated separately. Microsoft will coordinate migration schedules with you.

### Do Finance Insights features work differently after migration?

The user experience remains the same. The Finance Insights workspaces, prediction workflows, and AI models function identically. Only the underlying data pipeline changes (from Export to Data Lake to BPA).

## Capacity and Licensing

### How much Dataverse capacity will I need?

Dataverse usage varies based on:
- Organization size
- Number of legal entities
- Transaction volume
- Amount of historical data

Small to medium organizations typically have sufficient capacity included with Finance licenses. Large organizations may need additional Dataverse capacity.

### Is BPA included in my Finance license?

Yes, Business Performance Analytics is included with Dynamics 365 Finance licenses. No separate BPA license is required.

### What happens if I run out of Dataverse capacity?

If you exceed your Dataverse capacity, you'll receive notifications in the Power Platform admin center. Finance Insights may experience performance issues or data sync delays. Purchase additional capacity to resolve this.

## Troubleshooting

### Finance Insights features aren't working after migration

**Check these items:**
1. Wait for initial BPA data sync to complete (can take several hours)
2. Verify BPA is syncing data from Finance successfully
3. Check AI Builder credits are available
4. Verify no errors in the BPA workspace
5. Wait 24 hours after migration for full data refresh

If issues persist after 24 hours, contact Microsoft support.

### BPA shows errors after migration

Contact Microsoft support immediately. Provide:
- Your environment ID
- Error messages from BPA workspace
- Migration completion date/time
- Screenshots of errors

## Support

### How do I get help with migration?

For questions & support on this migration, please contact Microsoft Support at https://support.microsoft.com/en-us

### What information should I provide when contacting support?

Include:
- Environment ID
- Environment name
- Migration date
- Specific error messages or issues
- Screenshots of problems
- Steps to reproduce the issue

## Planning Questions

### Should I upgrade to Finance 10.0.38 before or during migration?

Upgrade to Finance 10.0.38+ **before** your scheduled migration. The migration cannot proceed if you're on an earlier version. Plan your Finance upgrade well in advance of migration.

### Can I delay migration beyond Q1 2026?

No. Export to Data Lake will be discontinued in Q1 2026, and Finance Insights 1.0.0.x will stop functioning. All migrations must be completed before that deadline.

### What happens if I don't migrate by Q1 2026?

Finance Insights features will stop working when Export to Data Lake is discontinued. You will lose:
- Customer payment predictions
- Cash flow forecasting
- All Finance Insights functionality

If you do not want to migrate, you must uninstall Finance Insights before your scheduled migration date. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).

## Feature-Specific Questions

### Will customer payment predictions work the same way?

Yes. Customer payment predictions function identically after migration. Your trained models are preserved, and predictions continue with the same accuracy and workflow.

### Will cash flow forecasting work the same way?

Yes. Cash flow forecasting maintains the same functionality. Your forecast models and historical forecasts are preserved during migration.

### What about Budget proposals feature?

Budget proposals feature was deprecated in Finance Insights 1.2.x and is no longer available after migration. If you currently use Budget proposals, plan alternative budgeting workflows before migration.

### Can I still train new prediction models?

Yes. You can train new customer payment prediction models and cash flow forecast models after migration, just as you could before.

### Will prediction accuracy change?

No. The migration preserves your trained models and historical data. Prediction accuracy remains consistent after migration.

## Timeline and Process

### What's the overall migration timeline?

**Phase 1 - Notification:** Microsoft contacts you (30+ days before migration)
**Phase 2 - Preparation:** You prepare environment, or uninstall Finance Insights if you do not wish to be migrated
**Phase 3 - Migration:** Microsoft performs migration (2-4 hours)
**Phase 4 - Validation:** You verify functionality (5-7 days)
**Phase 5 - Decommission:** Microsoft removes old configuration

### Can I perform the migration myself?

No. This is a Microsoft-managed migration. Microsoft performs the technical migration to ensure data integrity and model preservation. You'll be responsible for validation and updating any custom integrations afterward.

### What if I need to reschedule?

Microsoft will schedule your migration with advance notice. If the scheduled date does not work for your organization, you must uninstall Finance Insights before the scheduled migration date to opt out of the migration. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).

### Is there a rollback plan if migration fails?

Yes. If migration fails, Microsoft can roll back to your original Finance Insights 1.0.0.x configuration. Your environment and data remain safe during migration attempts.

## Additional Resources

- [Business Performance Analytics home page](../business-performance-analytics/business-performance-analytics-home-page.md)
- [Finance insights home page](finance-insights-home-page.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
