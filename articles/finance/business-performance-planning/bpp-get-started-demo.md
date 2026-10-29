---
title: Get started with Business planning performance demo assets
description: Learn how to install and configure the Dynamics 365 Finance Business planning performance demo assets.
author: twheeloc
ms.author: romainpham
ms.reviewer: twheeloc
ms.topic: how-to
ms.date: 10/21/2026
ai-usage: ai-assisted
---

# Set up Business planning performance demo assets

The Dynamics 365 Finance Business planning performance demo assets provide preconfigured data, planning scenarios, automation, and Power BI experiences that you can use to explore Business planning performance. The demo assets support two scenarios: Financial Planning & Analysis and Retail Sales Planning.

In this article, you set up the Business planning performance demo assets in a Power Platform environment, install a Power BI template app, and connect the template app to the demo data. Complete the demo assets configuration before you connect a Power BI template app.

The demo has two components:

- Business planning performance demo assets are deployed to a Power Platform environment and provide the Dataverse planning model, demo data, automation, and dataflows.
- Business planning performance Power BI template apps are installed in your Power BI tenant and provide the Financial planning and analysis and Retail sales planning demo experiences.

After you install a template app, you connect its semantic model to the Power Platform environment that contains the demo assets. You can install either template app or both, and connect them to the same demo assets environment.

| Power BI template app | Scenario |
| --- | --- |
| Dynamics 365 Finance Business planning performance - Financial planning and analysis demo data | Financial planning, budgeting, forecasting, workforce planning, CAPEX planning, allocations, approvals, and Profit and loss reporting. |
| Dynamics 365 Finance Business planning performance - Retail sales planning demo | Retail sales budgeting, forecasting, store and SKU planning, inventory analysis, and price-volume-mix analysis. |

## Prerequisites

Before you begin, review the licensing, security, Power Platform, and Power BI requirements.

### Licensing

- Users who perform planning operations have a Dynamics 365 Finance Premium license.
- The user who installs a Power BI template app has a Power BI Pro license.
- Your organization allows the installation of Power BI template apps.

### Power Platform

The user who configures the demo assets has:

- Access to a supported Power Platform environment.
- Permission to install Dynamics 365 applications.
- Permission to manage solutions.
- Permission to configure Power Automate cloud flows.
- Permission to configure and publish Power Query dataflows.
- Permission to create or use connections for:
  - Microsoft Dataverse
  - Office 365 Outlook
  - Power Query Dataflows
  - Standard approvals

### Business planning performance security

Users who interact with the Power BI demo have:

- A Dynamics 365 Finance Premium license.
- An appropriate Business planning performance security role.
- Access to the required demo data through Business planning performance dimension security.

For the complete interactive demo experience, users need at least the Business planning performance contributor role. Business planning performance security roles determine which planning operations a user can perform. Dimension security determines which planning data the user can view and edit.

Demo users don't need to open the Business planning performance application to use the Power BI demo. Administrators use the application to configure dimension security. Users can open the application if they want to explore or modify the underlying planning model.

### Power BI

The user who installs and configures a Business planning performance Power BI template app needs:

- A Power BI Pro license.
- Permission to install template apps in your Power BI tenant.
- Access to the template app from Microsoft AppSource.
- An organizational account that can authenticate to the Dataverse environment.

The user installs the template app in your Power BI tenant. The Business planning performance demo assets stay in the Power Platform environment and connect after the user installs the template app.

### Install Business planning performance

Install Business planning performance in the Power Platform environment where you want to set up the demo. Don't install the Planning demo assets package until this installation finishes successfully.

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Select **Manage** > **Environments**.
1. Select the environment where you want to set up the demo.
1. Under **Resources**, select **Dynamics 365 apps**.
1. Select **Install app**.
1. Search for **planning**.
1. Select **Dynamics 365 Finance business performance planning**.
1. Start the installation.
1. Wait for the installation to complete.

### Install the Planning demo assets package

Install the Planning demo assets package in the same environment where you installed Business planning performance. The package installs the data model and supporting components required by the Financial planning and analysis and Retail sales planning demos.

1. In the Power Platform admin center, return to **Dynamics 365 apps**.
1. Select **Install app**.
1. Search for and select the **Planning demo assets** package.
1. Start the installation.
1. Wait for the installation to complete.

#### Give demo users access

For the complete interactive demo experience, assign users at least the Business planning performance contributor role and give them dimension access to the required demo data.

If the person who configures the demo assets isn't the person who runs the demo, a Business planning performance administrator or another user with the Maintain security privilege must assign the demo user to an appropriate dimension group.

For all Business planning performance visuals except Table edit, users need access to at least one dimension value for every dimension in the cube.

#### Configure the connection references

The demo assets use four connection references. Configure all four before you run the demo assets cloud flows:

- Microsoft Dataverse demo data
- Office 365 Outlook demo data
- Power Query Dataflows demo data
- Standard approvals demo data

1. Go to the [Power Apps maker portal](https://make.powerapps.com).
1. Select the environment where you installed the demo assets.
1. Select **Solutions**.
1. Under **Unmanaged solutions**, open **Default Solution**.
1. Select **Connection references**.
1. Open a demo data connection reference.
1. Select an existing connection or create a connection.
1. Authenticate if you're prompted.
1. Select **Save**.
1. Repeat the previous steps for the remaining connection references.

#### Configure and run Financial planning and analysis demo data setup

The Financial planning and analysis demo data setup cloud flow initializes the environment-specific configuration for the demo assets. Don't continue until the flow completes successfully.

#### Configure the flow

1. In the Power Apps maker portal, select **Solutions** > **Managed**.
1. Open **Dynamics extended planning and analysis demo data**.
1. Select **Cloud flows**.
1. Open **XPnA demo data setup**.
1. Select **Edit**.
1. Locate **Refresh a dataflow**.
1. For **Group**, select the environment where you installed the Demo Assets.
1. For **Dataflow**, select a dataflow included with the Demo Assets.
1. Select **Save**.
1. Turn on the flow.

### Run the flow

1. Run **XPnA demo data setup**.
1. For **FPA approver email**, enter the email address that receives Financial planning and analysis approval notifications.
1. For **Retail approver email**, enter the email address that receives Retail sales planning approval notifications.
1. Start the flow.
1. Wait for the flow to complete.

#### Turn on the demo cloud flows

After Financial planning and analysis demo data setup completes, save and turn on the cloud flows included with the demo assets. Saving each flow applies its configured connection references and environment-specific values, so save each flow before you turn it on.

1. Open **Dynamics extended planning and analysis demo data**.
1. Select **Cloud flows**.
1. Open a demo cloud flow.
1. Select **Edit**.
1. Select **Save**, even if you don't make other changes.
1. Return to the flow details.
1. Select **Turn on**.
1. Verify that the flow status is **On**.
1. Repeat the previous steps for the remaining demo cloud flows.

#### Configure and publish the demo dataflows

Configure and publish these Financial planning and analysis dataflows. The destination mappings are preconfigured, so you shouldn't normally need to modify them.

- FPA_Dataflow_Allocation_Planning_Output_Demo
- FPA_Dataflow_CAPEX_Output_Demo
- FPA_Dataflow_Reporting_Output_Demo
- FPA_Dataflow_Workforce_Planning_Output_Demo

Complete the following procedure for each dataflow:

1. In the Power Apps maker portal, select the demo assets environment.
2. Go to **Dataflows**.
3. Find the dataflow, select the ellipsis (**...**), and then select **Edit**.
4. Locate the **OrgUrl** parameter.
5. Enter the Dataverse environment URL without the `https://` prefix.

   For example:

   `yourenvironment.crm.dynamics.com`

1. Select **Apply**.
7. If you're prompted, select **Configure connection** and authenticate with your organizational account.
8. Verify that the source data loads.
9. Select **Next**.
10. Review the preconfigured destination and column mappings.
11. Select **Publish**.
12. Wait for publication to complete.

#### Verify the demo assets configuration

Before you install a Power BI template app, verify the configuration.

For the demo assets environment, confirm that:

- Business planning performance is installed.
- The Planning demo assets package is installed.
- All four connection references are configured.
- You complete the financial planning and analysis demo data setup.
- All required demo cloud flows are saved and turned on.
- All four Financial planning and analysis dataflows are configured and published.
- The expected demo data is available.

For each user who interacts with the demo, confirm that:

- The user has a Dynamics 365 Finance Premium license.
- The user has the appropriate Business planning performance security role.
- The user has dimension security access to the required demo data.

> [!IMPORTANT]
> Power BI access, Business planning performance permissions, and Business planning performance dimension security are separate. Connecting Power BI doesn't grant planning permissions or access to all planning data.

#### Record the Power BI connection information

Before you install a Power BI template app, record the connection values required by the app. You can find the environment URL on the environment details page in the Power Platform admin center.

| Parameter | Value |
| --- | --- |
| **Server** | Dataverse organization URL without the `https://` prefix. For example, `yourenvironment.crm.dynamics.com`. |
| **Database** | The first part of the Environment URL before the first period (.). For example, `yourenvironment`. |

#### Install a Power BI template app

Choose the template app for the scenario that you want to explore. Power BI installs the template app in your Power BI tenant and creates an associated workspace that contains its semantic model and reports. Installing the template app doesn't install or move the Business planning performance demo assets. You can install both template apps and connect them to the same demo assets environment.

| Power BI template app | Install |
| --- | --- |
| Dynamics 365 Finance Business planning performance - Financial planning and analysis demo data | Microsoft AppSource |
| Dynamics 365 Finance Business planning performance - Retail sales planning demo | Microsoft AppSource |

1. Select the Microsoft AppSource link for the template app.
1. Select **Get it now**.
1. Sign in with your Power BI account if you're prompted.
1. Follow the instructions to install the template app.
1. Wait for Power BI to confirm that the app is ready.
1. Open the installed app.

#### Connect the template app to the demo assets

After you install the template app, connect its semantic model to the Dataverse environment that contains the demo assets. The template app remains in your Power BI tenant. The **Server** and **Database** parameters determine which demo assets environment provides data to the app.

1. Open the installed template app.
1. Select **Connect your data**.
1. Enter the **Server** value that you recorded earlier.
1. Enter the **Database** value.
1. Continue to authentication.
1. Select **OAuth2** if you're prompted for an authentication method.
1. Sign in with your organizational account.
1. Select **Organizational** if you're prompted for a privacy level.
1. Apply the credentials.
1. Wait for the initial semantic model refresh to complete.

#### Verify the Power BI template app

After the initial refresh, confirm that:

- The semantic model refreshes successfully.
- The reports display the expected demo data.
- The Business planning performance visuals load correctly.
- A demo user with the required security can perform the expected planning interactions.

To verify refresh:

1. Open the workspace that Power BI created for the template app.
1. Find the semantic model.
1. Select the ellipsis (**...**), and then select **Refresh now**.
1. Wait for the refresh to complete.
1. Open the template app.
1. Verify that the reports display the expected demo data.

The Business planning performance demo is ready to use.

#### Troubleshoot setup

If setup fails, identify which part of the solution is affected:

- Demo assets installation: Verify the Business planning performance and Planning demo assets installations.
- Automation: Verify the connection references, XPnA demo data setup, cloud flows, and dataflows.
- User security: Verify the Dynamics 365 Finance Premium license, Business planning performance security role, and dimension-group assignment.
- Power BI: Verify the **Server** and **Database** parameters, authentication, and semantic model refresh.
