---
title: Uninstall Finance insights
description: This article explains how to uninstall Finance Insights from your Dynamics 365 Finance environment.
author: wei-msft
ms.author: zhuw
ms.topic: article
ms.date: 12/10/2025
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.38
---

# Uninstall Finance insights

[!include [banner](../includes/banner.md)]

This article explains how to uninstall Finance Insights from your Dynamics 365 Finance environment.

## Overview

You may need to uninstall Finance Insights if you:
- Want to opt out of the Finance Insights 1.0.0.x -> 1.2.x migration before your scheduled migration date
- No longer need Finance Insights capabilities
- Are troubleshooting issues and need to perform a clean reinstall

> [!WARNING]
> Uninstalling Finance Insights will permanently delete:
> - All customer payment prediction models
> - All cash flow forecast models
> - Historical prediction data
> - All Finance Insights configurations
> 
> This action cannot be undone. Make sure to back up any data you need before uninstalling.

## Prerequisites

Before uninstalling Finance Insights, ensure you have:
- System administrator access to your Dynamics 365 Finance & Operations environment
- Access to Power Platform admin center

## Uninstall Finance Insights 1.0.0.x

Two options are available for uninstalling Finance Insights 1.0.0.x: code-based uninstallation and manual uninstallation.

### Step 1: Disable Finance Insights features

Before uninstalling, disable Finance Insights features in your environment:

1. Start by navigating to the Finance Insights setup page within the Dynamics 365 Finance and Operations portal. Do this by:
   - Opening Finance and Operations
   - Searching for "Finance Insights" and selecting one of the setup payments such as customer payment predictions or cash flow forecast
2. In each setup page, disable "Enable feature" switch for any active model. Doing so will help to clean up any legacy metadata from the current version

### Step 2: Uninstall Finance Insights solutions

Choose one of the following uninstallation methods:

#### Option 1: Code-based uninstallation

1. Sign in to the [Microsoft Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Dataverse admin credentials
2. Select the environment where you want to uninstall Finance Insights
3. Select the Environment URL that is provided in the details. You're redirected to the sign-in page for the Dataverse environment
4. Open your browser's developer tools by selecting **Ctrl**+**Shift**+**I** or going to **More tools** > **Developer tools**. Then select the **Console** tab to open the developer console
5. Copy the following JavaScript code, and paste it into the developer console to start the uninstallation process. The process takes 30 minutes approximately

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

2. If the operation is successful, you receive the following message: "Finance Insights Solutions removed successfully."

#### Option 2: Manual uninstallation

You can manually uninstall Finance Insights through the Power Platform admin center. The solutions must be manually deleted in the following order:

1. Finance Insights Service Anchor
2. Finance Insights Solution Anchor
3. Finance Insights Identities PROD
4. Finance Insights AI Solution
5. D365 FNO Integration Anchor
6. D365 FNO Integration
7. Finance Insights Service Permissions PROD
8. Finance Insights Service
9. FNO MDL Folder Prod

To delete each of the solutions, follow these steps:

1. In [Power Apps](https://make.preview.powerapps.com/), on the left navigation pane, select **Solutions**
2. Select the solution to delete, and then select **Delete**
3. Select **Delete** again to confirm the operation
4. Wait for the **Deleting** message box to disappear

Deletion of all solutions requires approximately 30 minutes. If the operation is successful, you receive the following message: "Successfully deleted solution."

### Step 3: Uninstall Business Performance Analytics (optional, Finance Insights 1.2.x only)

If you're using Finance Insights 1.2.x and you're not using Business Performance Analytics (BPA) for other purposes, you can optionally uninstall BPA to free up Dataverse storage.

> [!IMPORTANT]
> Only uninstall BPA if you're not using it otherwise. If you're unsure, keep BPA installed.

For instructions on uninstalling BPA, see [Uninstall Business performance analytics](../business-performance-analytics/uninstall-bpa.md).

## Verification

After uninstalling, verify that Finance Insights has been removed:

1. In Dynamics 365 Finance, navigate to **Credit and collections** workspace
2. Verify that payment prediction tiles are no longer visible
3. Navigate to **Cash and bank management** workspace
4. Verify that cash flow forecast tiles are no longer visible
5. In LCS, verify that Finance Insights add-in is no longer listed under environment add-ins

## Re-enabling Finance Insights

If you need to reinstall Finance Insights after uninstalling:

**For Finance Insights 1.2.x:**
- Follow the installation instructions in [Configuration for Finance insights](configure-for-fin-insites.md)
- Note that you will need to retrain all prediction models
- Historical prediction data will not be recoverable

**For Finance Insights 1.0.0.x:**
- Finance Insights 1.0.0.x is deprecated and will not be available after Q1 2026

## Impact of uninstalling

### Data loss

Uninstalling Finance Insights results in permanent deletion of:
- All trained prediction models (customer payment predictions, cash flow forecasts)
- Historical prediction results
- Model training history
- AI Builder credit usage history specific to Finance Insights
- Finance Insights configuration settings

### Feature availability

After uninstalling, you will lose access to:
- Customer payment prediction capabilities
- Cash flow forecasting with AI predictions
- Finance Insights workspaces and tiles
- Integration with BPA for Finance Insights scenarios

### Licensing

- AI Builder credits allocated to Finance Insights will remain available for other AI Builder scenarios
- Dynamics 365 Finance license is unaffected

## Troubleshooting

### Uninstall fails or times out

If the uninstallation fails:
1. Check that you have necessary permissions
2. Verify no active jobs or processes are using Finance Insights
3. Try the uninstallation again
4. Contact Microsoft support if issues persist

### Finance Insights features still visible after uninstall

If Finance Insights features remain visible:
1. Wait up to 1 hour for cleanup to complete
2. Clear browser cache and restart browser
3. Verify all steps were completed
4. Contact Microsoft support if issues persist

## Getting support

For assistance with uninstalling Finance Insights, contact Microsoft Support at https://support.microsoft.com/en-us

When contacting support, provide:
- Environment ID and name
- Finance Insights version (1.0.0.x or 1.2.x)
- Steps completed before encountering issues
- Error messages or screenshots
- Reason for uninstalling (optional)

## Additional resources

- [Finance insights home page](finance-insights-home-page.md)
- [Finance Insights migration guide](finance-insights-migration.md)
- [Finance Insights migration FAQ](finance-insights-migration-faq.md)
- [Configuration for Finance insights](configure-for-fin-insites.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
