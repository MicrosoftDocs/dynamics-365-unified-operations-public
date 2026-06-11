---
title: Uninstall Finance insights
description: This article explains how to uninstall Finance insights from your Dynamics 365 Finance environment.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 06/01/2026
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Uninstall Finance insights

[!include [banner](../includes/banner.md)]

This article explains how to uninstall Finance insights from your Dynamics 365 Finance environment.

## Overview

You might need to uninstall Finance insights if you:

- Want to opt out of the Finance insights 1.0.0.x -> 1.2.x update before your scheduled update date
- No longer need Finance insights capabilities
- Are troubleshooting issues and need to perform a clean reinstall

When you uninstall Finance insights, you permanently delete:

- All customer payment prediction models
- All cash flow forecast models
- Historical prediction data
- All Finance insights configurations

This action can't be undone. Make sure to back up any data you need before uninstalling.

## Prerequisites

Before uninstalling Finance insights, ensure you have:

- System administrator access to your Dynamics 365 finance and operations environment
- Access to Power Platform admin center

## Uninstall Finance insights 1.0.0.x

You can uninstall Finance insights 1.0.0.x by using either code-based uninstallation or manual uninstallation.

### Step 1: Disable Finance insights features

Before uninstalling, disable Finance insights features in your environment:

1. Go to the Finance insights set up page in the Dynamics 365 finance and operations portal. To get there:
   - Open Finance and Operations
   - Search for "Finance insights" and select one of the setup payments, such as customer payment predictions or cash flow forecast
1. In each setup page, disable the **Enable feature** switch for any active model. This step removes legacy metadata from the current version.

### Step 2: Uninstall Finance insights solutions

Choose one of the following uninstallation methods:

#### Option 1: Code-based uninstallation

1. Sign in to the [Microsoft Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Dataverse admin credentials.
1. Select the environment where you want to uninstall Finance insights.
1. Select the Environment URL that is provided in the details. You're redirected to the sign-in page for the Dataverse environment.
1. Open your browser's developer tools by selecting **Ctrl**+**Shift**+**I** or going to **More tools** > **Developer tools**. Then select the **Console** tab to open the developer console.
1. Copy the following JavaScript code, and paste it into the developer console to start the uninstallation process. The process takes about 30 minutes.

    ```javascript
    // Get the current org URL
    const ORG = window.location.hostname;
    const WEB_API = `https://${ORG}/api/data/v9.2`;
    const SOLUTIONS = [
       "msdyn_FinanceInsightsServiceAnchor",
       "msdyn_FinanceInsightsSolutionAnchor",
       "msdyn_FinanceInsightsIdentities_PROD",
       "msdyn_FinanceInsightsAISolution",
       "msdyn_D365FNOIntegrationAnchor",
       "msdyn_D365FNOIntegration",
       "msdyn_FinanceInsightsServicePermissions_PROD",
       "msdyn_FinanceInsightsService",
       "msdyn_FnoMDLFolderProd"
    ];
    
    // Get all solutions
    let _getSolutions = () => {
        var requestOptions = {
            method: "GET",
        };
        return fetch(
            `${WEB_API}/solutions?$filter=(isvisible%20eq%20true)&$select=solutionid,friendlyname,uniquename`,
            requestOptions
        ).then((response) => response.json());
    };
    
    // Delete the solution by solution ID
    let _deleteSolution = (solutionid) => {
        var requestOptions = {
            method: "DELETE",
        };
        return fetch(`${WEB_API}/solutions(${solutionid})`, requestOptions);
    };
    let start = async () => {
        console.info("Uninstalling Finance Insights solutions");
        let installedSolutions = (await _getSolutions()).value;
    
        // Sort the installed Finance Insights solutions 
         let installedFinanceInsightsSolutions = installedSolutions
            .filter((i) => SOLUTIONS.indexOf(i.uniquename) > -1)
            .sort(
                (i, j) =>
                    SOLUTIONS.indexOf(i.uniquename) - SOLUTIONS.indexOf(j.uniquename)
            );
        for (let solution of installedFinanceInsightsSolutions) {
            console.info(`Removing solution ${solution.friendlyname}`);
            await _deleteSolution(solution.solutionid);
        }
        console.info("Finance Insights Solutions removed successfully");
    };
    
    start();
    ```

1. If the operation is successful, you receive the following message: "Finance insights solutions removed successfully."

#### Option 2: Manual uninstallation

You can manually uninstall Finance insights through the Power Platform admin center. You must manually delete the solutions in the following order:

1. Finance insights service anchor
1. Finance insights solution anchor
1. Finance insights identities PROD
1. Finance insights AI solution
1. Dynamics 365 finance and operations insights anchor
1. Dynamics 365 finance and operations insights
1. Finance insights service permissions PROD
1. Finance insights service
1. Dynamics 365 finance and operations MDL folder prod

To delete each of the solutions, follow these steps:

1. In [Power Apps](https://make.preview.powerapps.com/), on the left navigation pane, select **Solutions**.
1. Select the solution to delete, and then select **Delete**.
1. Select **Delete** again to confirm the operation.
1. Wait for the **Deleting** message box to disappear.

Deleting all of the solutions takes about 30 minutes. If the operation is successful, you receive the following message: "Successfully deleted solution."

### Step 3: Uninstall Business performance analytics (optional, Finance insights 1.2.x only)

> [!IMPORTANT]
> Only uninstall Business performance analytics if you're not using it. If you're unsure, keep Business performance analytics installed.

If you're using Finance insights 1.2.x and you're not using Business performance analytics for other purposes, you can optionally uninstall Business performance analytics to free up Dataverse storage.

For more information about uninstalling Business performance analytics, see [Uninstall Business performance analytics](../business-performance-analytics/uninstall-bpa.md).

### Verification

After uninstalling, verify that Finance insights are removed:

1. In Dynamics 365 Finance, go to the **Credit and collections** workspace.
1. Verify that payment prediction tiles are no longer visible.
1. Go to the **Cash and bank management** workspace.
1. Verify that cash flow forecast tiles are no longer visible.
1. In LCS, verify that Finance insights add-in is no longer listed under environment add-ins.

### Reenabling Finance insights

To reinstall Finance insights after uninstalling it:

For Finance insights 1.2.x:

- Follow the installation instructions in [Configuration for Finance insights](configure-for-fin-insites.md).
- You'll need to retrain all prediction models.
- Historical prediction data won't be recoverable.

For Finance insights 1.0.0.x:

- Finance insights 1.0.0.x is deprecated and won't be available after the Export to Data Lake service is discontinued.

### Impact of uninstalling

Uninstalling Finance insights permanently deletes:

- All trained prediction models, such as customer payment predictions and cash flow forecasts.
- Historical prediction results.
- Model training history.
- AI Builder credit usage history specific to Finance insights.
- Finance insights configuration settings.

After uninstalling, you lose access to:

- Customer payment prediction capabilities.
- Cash flow forecasting with AI predictions.
- Finance insights workspaces and tiles.
- Integration with Business performance analytics for Finance insights scenarios.

- AI Builder credits allocated to Finance insights are available for other AI Builder scenarios.
- Dynamics 365 Finance license is unaffected.

### Troubleshooting

If the uninstallation fails:

- Check that you have the necessary permissions.
- Verify that no active jobs or processes are using Finance insights.
- Try the uninstallation again.
- Contact Microsoft support if problems persist.

If Finance insights features remain visible after uninstalling:

- Wait up to one hour for cleanup to complete.
- Clear your browser cache and restart your browser.
- Verify that you completed all steps.
- Contact Microsoft support if problems persist.

For assistance with uninstalling Finance insights, contact Microsoft support and provide:

- Environment ID and name
- Finance insights version (1.0.0.x or 1.2.x).
- Steps you completed before encountering problems.
- Error messages or screenshots.
- Reason for uninstalling (optional).

#### Additional resources

- [Finance insights home page](finance-insights-home-page.md)
- [Finance insights update guide](finance-insights-update.md)
- [Finance insights update FAQ](finance-insights-update-faq.md)
- [Configuration for Finance insights](configure-for-fin-insites.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
