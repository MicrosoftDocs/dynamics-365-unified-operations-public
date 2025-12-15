---
title: Finance insights update FAQ
description: This article answers frequently asked questions about updating from Finance insights 1.0.0.x with Export to Data Lake to Finance insights 1.2.x with Business performance analytics.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 12/09/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Finance insights update FAQ

[!include [banner](../includes/banner.md)]

This article answers frequently asked questions about updating from Finance insights 1.0.0.x with Export to Data Lake to Finance insights 1.2.x with Business performance analytics.

## Why is this update happening?
Microsoft is modernizing Finance insights to use Business performance analytics as its data backend instead of Export to Data Lake. This change provides better performance and reliability, and it aligns with Microsoft's Power Platform strategy. Export to Data Lake is deprecated and will be discontinued in February 2026.

## When do I need to update?
Starting on February 1, 2026, Finance insights will be updated to use Business performance analytics for the data pipeline. The update period runs from February 1, 2026 (midnight UTC) through March 31, 2026 (midnight UTC).

Microsoft manages the update process and updates your environment automatically during this window. Customers with **Payment prediction** and **Cashflow forecast** that refresh periodically are considered active and are updated.

## Do I have to update?
Yes, if you want to continue using Finance insights. Export to Data Lake will be discontinued and Finance insights 1.0.0.x no longer functions after that date. The update to Finance insights 1.2.x with Business performance analytics will occur automatically during the February 1 - March 31, 2026 window.

## Who manages the update?
Microsoft manages the update process and performs the actual update of your Finance insights configuration and models automatically.

## How much does the update cost?
There's no separate update fee. However, Finance insights 1.2.x requires Business performance analytics, which is included with Dynamics 365 Finance licenses.

The installation of Business performance analytics results in additional storage consumption and your organization's storage costs may increase depending on your Dynamics 365 Finance data volume. Check your Dataverse license entitlement and usage in the [Power Platform admin center](https://aka.ms/ppac).

## Can I opt out of the update?
If you choose not to update, you lose access to Finance insights features when Export to Data Lake is discontinued. There's no option to continue using Finance insights 1.0.0.x after this date. 

If you'd like to opt out of the update and discontinue using Finance insights entirely, you must uninstall Finance insights before February 1, 2026. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md). Uninstalling Finance insights removes all Finance insights functionality, including prediction models and historical data.

## What version of Dynamics 365 Finance do I need?
You must be on Dynamics 365 Finance version 10.0.38 or later before update. If you're on an earlier version, you need to upgrade before Microsoft can update your Finance insights configuration.

## Do I need to install Business performance analytics?
No, Microsoft installs Business performance analytics version 2.3 or later as part of the update process.

## Will my environment be down during update?
Your Dynamics 365 Finance environment remains available during update. However, Finance insights features (payment predictions, cash flow forecasting) are unavailable for 2-4 hours during the update window. Plan the update during a low-usage period if possible.

## How long does update take?
The update typically takes 2-4 hours. Microsoft provides a specific timeframe when they schedule your update. During this time, Finance insights features are unavailable, but the rest of your Finance environment remains accessible.

## Can users still work in Dynamics 365 Finance during update?
Yes, users can continue working in Finance during update. Only Finance insights features (payment predictions, cash flow forecasting workspaces) are temporarily unavailable.

## What if something goes wrong during update?
Microsoft's update team monitors the process and resolves any issues. If update fails, Microsoft works with you to reschedule and address any blocking issues. Your original Finance insights 1.0.0.x configuration remains intact until update completes successfully.

## Will I lose my prediction models?
No, customer payment prediction models and cash flow forecast models are automatically updated and preserved.

## Will historical prediction data be preserved?
Yes, historical predictions and model training data are preserved during update. You maintain continuity in your prediction accuracy and historical analysis.

## Do I need to reconfigure Finance insights features?
No, your Finance insights feature configurations are updated automatically. Users can access the same workspaces and features without reconfiguration.

## How long before predictions start working again?
After update completes, Business performance analytics performs an initial data sync. This process can take several hours depending on your data volume. Predictions resume automatically after the data sync completes.

## What's the difference between Finance insights 1.0.0.x and 1.2.x?
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

## How does Business performance analytics integration work?
Business performance analytics syncs data from Dynamics 365 Finance to Dataverse automatically. Finance insights 1.2.x reads from Business performance analytics's Dataverse tables instead of from Azure Data Lake.

## What Business performance analytics components does Finance insights use?
Finance insights reads from standard Business performance analytics analytical entities for general ledger, customer transactions, and other financial data. Business performance analytics maintains these tables automatically as it syncs from Finance.

## Do I need separate Business performance analytics licenses?
Business performance analytics is included with Dynamics 365 Finance licenses. You don't need separate Business performance analytics licenses.

## Will AI Builder credit usage change?
AI Builder credit usage remains the same. Finance insights continues to use the same AI Builder models and credit consumption patterns. Each Finance tenant receives 20,000 AI Builder credits monthly.


## What if I have multiple environments?
If you have multiple Finance environments using Finance insights (for example, production and sandbox), each environment needs to be updated separately. Microsoft coordinates update schedules with you.

## Do Finance insights features work differently after update?
The user experience stays the same. The Finance insights workspaces, prediction workflows, and AI models function identically. Only the underlying data pipeline changes from Export to Data Lake to Business performance analytics.

## How much Dataverse capacity do I need?
Dataverse usage varies based on:
- Organization size
- Number of legal entities
- Transaction volume
- Amount of historical data

Small to medium organizations typically have sufficient capacity included with Finance licenses. Large organizations might need extra Dataverse capacity.

## Is Business performance analytics included in my Finance license?
Yes, Business performance analytics is included with Dynamics 365 Finance licenses. You don't need a separate Business performance analytics license.

## What happens if I run out of Dataverse capacity?
If you exceed your Dataverse capacity, you receive notifications in the Power Platform admin center. Finance insights might experience performance problems or data sync delays. Purchase extra capacity to resolve this problem.

## Troubleshooting

> [!NOTE]
> - Finance insights features don't work after update  
>  1. Wait for the initial Business performance analytics data sync to complete. It can take several hours.  
>  1. Verify that Business performance analytics is syncing data from Finance successfully.  
>  1. Check that AI Builder credits are available.  
>  1. Verify that there are no errors in the Business performance analytics workspace.  
>  1. Wait 24 hours after update for full data refresh.  

If problems persist after 24 hours, contact Microsoft support.

If Business performance analytics shows errors after update, contact Microsoft support immediately and provide:
- Your environment ID
- Error messages from Business performance analytics workspace
- Migration completion date and time
- Screenshots of errors

## Should I upgrade to Finance 10.0.38 before or during update?
Upgrade to Finance 10.0.38 and later before the update window begins on February 1, 2026. The update can't proceed if you're on an earlier version.

## Can I opt out of the update?
If you don't want to proceed with the update, you must uninstall Finance insights from your environment before February 1, 2026. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md). Uninstalling Finance insights removes all Finance insights functionality, including prediction models and historical data.

## What happens if I don't update?
Finance insights features stop working when Export to Data Lake is discontinued. You lose:
- Customer payment predictions
- Cash flow forecasting
- All Finance insights functionality

If you don't want to update, you must uninstall Finance insights before February 1, 2026. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).

## Will customer payment predictions work the same way?
Yes, customer payment predictions function identically after update. Your trained models are preserved, and predictions continue with the same accuracy and workflow.

## Will cash flow forecasting work the same way?
Yes, cash flow forecasting maintains the same functionality. Your forecast models and historical forecasts are preserved during update.

## What about Budget proposals feature?
The Budget proposals feature was deprecated in Finance insights 1.2.x and is no longer available after update. If you currently use Budget proposals, plan alternative budgeting workflows before update.

## Can I still train new prediction models?
Yes, you can train new customer payment prediction models and cash flow forecast models after update.

## Will prediction accuracy change?
No, the update preserves your trained models and historical data. Prediction accuracy remains consistent after update.

## What's the overall update timeline?
1. Preparation (before February 1, 2026): You prepare your environment, or uninstall Finance insights if you don't wish to be updated.
1. Update window (February 1 - March 31, 2026): Microsoft performs the update automatically.  
1. Validation: You verify functionality after the update completes.
1. Decommission: Microsoft removes old configuration.

## Can I perform the update myself?
No, this update is managed by Microsoft. Microsoft handles the technical update to ensure data integrity and model preservation. You're responsible for validating the update and updating any custom integrations afterward.

## What if I need to reschedule?
Microsoft manages the update automatically during the February 1 - March 31, 2026 window. If you don't want to proceed with the update, you must uninstall Finance insights before February 1, 2026. For uninstallation instructions, see [Uninstall Finance insights](uninstall-finance-insights.md).

## Is there a rollback plan if update fails?
Yes, if the update fails, Microsoft rolls back to your original Finance insights 1.0.0.x configuration. Your environment and data remain safe during update attempts.

### Additional resources

- [Business performance analytics home page](../business-performance-analytics/business-performance-analytics-home-page.md)
- [Finance insights home page](finance-insights-home-page.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
