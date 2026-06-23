---
title: Manage Dynamics 365 Commerce deployments in Power Platform admin center (preview)
description: Learn how to use the Dynamics 365 Commerce deployments and extension validation in Power Platform admin center (preview).
author: ashishmsft
ms.date: 06/19/2026
ms.topic: overview
ms.author: asharchw
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2026-06-19
ms.custom:
  - bap-template
---

# Manage Dynamics 365 Commerce deployments in Power Platform admin center (preview)

> [!IMPORTANT]
> This experience is currently available as part of a public preview release. Features, regions, user interface labels, and available lifecycle actions can change before general availability. The content and the functionality too are subject to change.

Dynamics 365 Commerce now provides public preview support for Commerce deployment and extensibility scenarios in [Power Platform admin center](https://admin.powerplatform.microsoft.com/). This preview release lets Commerce administrators use Power Platform admin center to manage Commerce Scale Unit (CSU) deployment and extension validation scenarios for Commerce environments.

The preview is designed for sandbox-first validation. Use it to familiarize yourself with the Power Platform admin center experience, validate Commerce extension deployment flows, and prepare for future Commerce environment management capabilities.

> [!NOTE]
> Begin with sandbox and nonproduction environments. Migration from existing Lifecycle Services (LCS) managed Commerce deployments to Power Platform admin center isn't supported during public preview.

## What is Commerce in Power Platform admin center?

Commerce in Power Platform admin center is the new administration experience for managing Commerce deployment and extension scenarios from Power Platform admin center. It brings Commerce Scale Unit (CSU) management and Commerce extension deployment into the same admin center that organizations use for Power Platform environments and Dynamics 365 apps.

For Commerce, the experience focuses on the Commerce components that run store, scale unit, and digital commerce workloads:

- **Commerce Scale Unit (CSU)** for channel runtime and channel-side services.
- **Store Commerce POS** for in-store point of sale extension scenarios.
- **E-commerce** for digital storefront extension scenarios.

Instead of managing these Commerce deployment and extension workflows through LCS, you can use Power Platform admin center as the destination for Commerce environment lifecycle management.

> [!IMPORTANT]
> You can continue using LCS to deploy new production Commerce environments during the public preview availability of Commerce in Power Platform admin center. Before Power Platform admin center becomes the required path (after general availability), sufficient time and guidance will be provided to let you plan and manage the transition from LCS to Power Platform admin center.

## Why Commerce in Power Platform admin center matters

Commerce implementations often span headquarters, scale units, stores, and e-commerce sites. Customers and partners need a consistent way to provision, manage, extend, and validate these workloads across environments. Commerce in Power Platform admin center helps organizations move toward a more consistent admin model for Dynamics 365 Commerce.

This experience helps organizations:

- **Use a single administrative surface**: Administrators can manage Commerce workloads in Power Platform admin center alongside other Dynamics 365 and Power Platform workloads.
- **Simplify onboarding**: Customers and partners can provision and validate Commerce workloads from Power Platform admin center without relying on separate admin experiences for every step.
- **Support compliance and governance**: Commerce management in Power Platform admin center aligns with Power Platform environment administration patterns, permissions, and operational controls.
- **Reduce operational overhead**: Use a consistent deployment model for CSU, POS, and e-commerce extension scenarios.
- **Prepare for future Commerce lifecycle management**: Organizations can validate the Power Platform admin center model now and prepare for broader Commerce environment management capabilities after general availability.
- **Align with extensibility standards**: Commerce extensions are built and packaged by using [Azure Pipelines](/azure/devops/pipelines/get-started/what-is-azure-pipelines) and deployed through an orchestrated Power Platform admin center flow.

## Supported features for preview

Public preview support for Commerce in Power Platform admin center focuses on Commerce Scale Unit management and Commerce extension deployment scenarios.

Depending on your environment and preview availability, use Power Platform admin center to:

- View Commerce scale units that are associated with a Commerce environment.
- Create a Commerce Scale Unit for a supported Commerce environment.
- Review scale unit details, such as region, status, and deployed version.
- Run supported lifecycle actions, such as update, retry, restart, or delete, where those actions are available.
- Deploy Commerce extensions for CSU, Store Commerce point of sale (POS), and e-commerce scenarios.
- Use Azure Pipelines to build, package, and publish Commerce extension artifacts for deployment.

Commerce management in Power Platform admin center supports CSU, POS, and e-commerce. It provides a lifecycle model that aligns with other Dynamics 365 and Power Platform workloads. Commerce extensibility is supported by using a unified extension model. Extensions are built and packaged by using Azure Pipelines, Power Platform admin center orchestrates deployment, and Commerce deployment services retrieve and install extension artifacts as part of the environment lifecycle.

## How it works

Commerce deployment through Power Platform admin center uses an orchestration model. Power Platform admin center provides the administrator experience and starts deployment operations. Commerce deployment services retrieve and install the packages in the target Commerce environment.

| Component | Responsibility |
| --------- | -------------- |
| Azure DevOps | Builds, validates, packages, and publishes Commerce extension artifacts. |
| Power Platform admin center | Provides the customer-facing deployment and management experience. |
| Retail Deployment Service (RDS) | Retrieves and installs CSU and POS extension packages. |
| E-commerce Deployment Service (EDS) | Retrieves and installs e-commerce extension packages. |
| Commerce environment | Runs the Commerce workloads and deployed extensions for validation. |

Here's the high-level flow:

1. Developers create Commerce extensions for CSU, POS, or e-commerce.
1. Azure DevOps builds and packages the extension.
1. Azure DevOps publishes the package as a pipeline artifact.
1. A release pipeline uploads or registers the package for the target Commerce environment.
1. Power Platform admin center orchestrates deployment.
1. RDS or EDS retrieves and installs the package, depending on the extension type.
1. The implementation team validates the deployed Commerce scenario in the target sandbox or nonproduction environment.

## Before you begin

Before you use the preview, confirm that your environment and deployment components are ready.

### Confirm environment readiness

- Use a sandbox or nonproduction environment for initial validation.
- Confirm that Dynamics 365 Commerce is provisioned for the environment.
- Confirm that the appropriate Commerce components are available for your scenario, such as CSU, POS, e-commerce, or a combination.
- Confirm that the environment is on a supported version for the preview.
- Confirm that you have appropriate permissions to manage the environment in Power Platform admin center.
- Confirm that the target geography is supported. For availability information, see the [Explore feature geography](https://aka.ms/FeatureGeographicAvailabilityReport) report.

### Confirm Azure DevOps readiness

Use a source repository and pipeline setup that separate extension source from generated artifacts.

- Store extension source code in Azure repositories or another repository connected to Azure DevOps.
- Use branch policies or pull requests for reviews.
- Keep pipeline YAML, package configuration, and deployment scripts versioned with the extension.
- Don't commit generated package output to source control.
- Store secrets, tokens, and connection values in secure pipeline variables or variable groups.

### Prepare extension metadata

Collect the values needed by the pipeline and deployment flow.

| Value | Description |
| ----- | ----------- |
| Extension type | CSU, POS, e-commerce, or a combined package. |
| Extension name | Customer-readable name that identifies the package. |
| Version | Package version that you can trace to source and build output. |
| Target environment | Sandbox or nonproduction environment where the package will be validated. |
| Artifact location | Azure DevOps artifact, pipeline artifact, or storage location used by the release step. |
| Deployment owner | Team or person responsible for validating the deployment. |

## Find Dynamics 365 Commerce in Power Platform admin center

In Power Platform admin center, you can find Commerce management on the **Dynamics 365 Commerce** page.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the left navigation, select **Manage**.
1. Under **Products**, select **Dynamics 365 Commerce**.
1. On the **Dynamics 365 Commerce** page, review the list of headquarters environments.
1. Select the headquarters environment that you want to manage.
1. In the environment details pane, review **Scale units (preview)**.
1. Select an existing scale unit row to view scale unit details, or select **Add** to start the scale unit creation flow.

The **Scale units (preview)** list displays Commerce scale units that are linked to the selected headquarters environment. The list includes values such as scale unit name, region, status, and type.

## Create and manage a Commerce Scale Unit

Use Power Platform admin center to create and manage scale units for supported Commerce environments.

> [!NOTE]
> The exact labels and available actions in Power Platform admin center can change during public preview.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select **Manage** > **Environments**.
1. Open the Commerce environment that you want to manage.
1. Open the Commerce scale unit experience for the environment.
1. Select the option to create or add a scale unit.
1. Select the target region and deployment options.
1. Submit the deployment.
1. Monitor the scale unit status until deployment completes.

After you create the scale unit, open the scale unit details page to review the status, region, version, and available lifecycle actions. During preview, the set of available actions can vary by environment, region, and rollout state.

## Deploy Commerce extensions

Commerce in Power Platform admin center (preview) supports extension deployment scenarios for:

- CSU extensions that extend Commerce runtime and channel-side business logic.
- POS extensions that customize Store Commerce workflows and user experience.
- E-commerce extensions that customize site experiences, modules, themes, and storefront behavior.

Use a sandbox-first sequence for extension validation:

1. Build and package the extension in Azure DevOps.
1. Upload or register the package for deployment.
1. Deploy to a sandbox or nonproduction environment through Power Platform admin center.
1. Validate deployment status from Power Platform admin center and the relevant Commerce deployment service.
1. Run scenario-specific smoke tests.
1. Collect issues and redeploy an updated package if needed.
1. Use production environments only when you understand the preview support policy and production readiness guidance.

## Set up Azure Pipelines for Commerce extensions

Commerce extension deployment uses Azure DevOps to build packages and make them available for deployment. As a best practice, use separate build and release pipelines.

### Build the CSU extension package

Use the existing Commerce build pipeline guidance to generate a CSU extension package. For more information, see [Set up a build pipeline in Azure DevOps to generate a Cloud Scale Unit extension package](build-pipeline.md#set-up-a-build-pipeline-in-azure-devops-to-generate-a-cloud-scale-unit-extension-package).

The build pipeline should:

1. Check out the extension source repository.
1. Restore dependencies.
1. Build the solution.
1. Generate the CSU deployable package.
1. Publish the package as an Azure DevOps pipeline artifact.

### Set up a release pipeline for the CSU extension package

For CSU deployment through Power Platform admin center, configure an Azure DevOps release pipeline that uploads the CSU extension package to the Dataverse environment linked to Commerce headquarters. Power Platform admin center uses the package from Dataverse during deployment orchestration.

The setup requires:

- A Microsoft Entra app registration for the release pipeline.
- A Dataverse application user for the app registration.
- The **Dynamics Commerce Deployment Service Role** security role assigned to the application user.
- An Azure DevOps variable group for app and environment values.
- A release pipeline that uses the Commerce CSU extension upload template or equivalent pipeline steps.

### Create a Microsoft Entra app registration

Create an app registration that the release pipeline uses to upload Commerce extension packages.

1. To create an app registration in the Azure portal, follow the steps in [Register an application with the Microsoft identity platform](/entra/identity-platform/quickstart-register-app).
1. In **App registrations**, use the following values:
   - **Name**: Enter a name that identifies the app as the Commerce extension package upload identity.
   - **Supported account types**: Select **Single tenant only**.
   - **Redirect URI**: Leave empty.
1. After you create the app, go to **Manage** > **Certificates & secrets**.
1. Select **Client secrets**, and then select **New client secret**.
1. Copy the secret value. Use it as the `ClientSecret` value in the Azure DevOps variable group.
1. Go to **Overview**, and copy the **Application (client) ID**. Use it as the `ClientId` value in the Azure DevOps variable group.
1. Copy the **Directory (tenant) ID**. Use it as the `TenantId` value in the Azure DevOps variable group.

### Assign Dataverse privileges to the app

Add the app registration as an application user in the Dataverse environment that's linked to Commerce headquarters.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select **Manage** > **Environments**.
1. Find and open the Power Platform environment linked to your Commerce headquarters environment.
1. Select **Settings** > **Users + permissions** > **Application users**.
1. Select **New app user**, and then select **Add an app**.
1. Find and add the app that you created in [Create a Microsoft Entra app registration](#create-a-microsoft-entra-app-registration).
1. Configure the app user:
   - **Business unit**: Select the business unit with the same name as your Power Platform environment.
   - **Email address**: Enter an email address for the app user record.
   - **Security roles**: Select **Dynamics Commerce Deployment Service Role**.
1. Select **Save**.

> [!NOTE]
>
> - If you can't find the app that you created, confirm whether the app registration and the account signed in to Power Platform admin center are in the same Microsoft Entra tenant.
> - If you can't find the **Dynamics Commerce Deployment Service Role** security role, check the installed Dynamics 365 apps in the Power Platform environment. Confirm that the Commerce preview prerequisites are installed for the environment.

### Create the Azure DevOps variable group

Create an Azure DevOps variable group that stores the app and Dataverse values used by the CSU extension package release pipeline.

1. Confirm that you completed [Create a Microsoft Entra app registration](#create-a-microsoft-entra-app-registration) and [Assign Dataverse privileges to the app](#assign-dataverse-privileges-to-the-app).
1. Sign in to your Azure DevOps organization.
1. Select **Pipelines** > **Library**.
1. Add a variable group named `Commerce-ScaleUnit-Extension-Release-Variables`.
1. Add the following variables.

| Variable | Value |
| -------- | ----- |
| `ClientId` | The application client ID from the Microsoft Entra app registration. |
| `ClientSecret` | The client secret value from the Microsoft Entra app registration. Mark this variable as secret. |
| `DataverseUrl` | The Dataverse environment URL, such as `https://myorg.crm.dynamics.com/`. |
| `TenantId` | The Microsoft Entra tenant ID for the Dataverse environment. |

### Create the release pipeline from the template

Use the Commerce CSU extension release pipeline template that's provided for the public preview, or create an equivalent release pipeline that performs the same upload steps.

1. Sign in to your Azure DevOps organization.
1. Select **Pipelines**, and then select **New pipeline**.
1. Select the source repository for your extension code or pipeline template.
1. Select **Existing Azure Pipelines YAML file**.
1. Select the CSU extension release pipeline template.
1. Select **Continue**.
1. Confirm that the pipeline references the variable group `Commerce-ScaleUnit-Extension-Release-Variables`.
1. Confirm that the pipeline consumes the CSU package artifact from the build pipeline.
1. Save the pipeline.
1. Run the release pipeline after the CSU extension build pipeline publishes the package artifact.

If the template exposes configurable values, confirm that the following values match your environment:

- Build pipeline or artifact source name
- Package file path
- Variable group name
- Dataverse URL
- Tenant ID
- App registration client ID

### Troubleshoot CSU package upload

If the package upload fails, confirm the following values:

- The pipeline variable group name is `Commerce-ScaleUnit-Extension-Release-Variables`, or the template uses the variable group name that you configured.
- The variable names and values match the values in [Create the Azure DevOps variable group](#create-the-azure-devops-variable-group).
- `ClientSecret` is marked as secret and contains the current secret value.
- `DataverseUrl` points to the Dataverse environment linked to Commerce headquarters.
- The application user has the **Dynamics Commerce Deployment Service Role** security role.
- The package path points to the CSU package artifact published by the build pipeline.
- The build pipeline name in the release template matches your existing CSU extension build pipeline.

## Set up pipelines for POS extensions

The same high-level model applies to POS extensions:

1. Build the extension from source.
1. Package it into the deployable Commerce extension format.
1. Publish the package artifact.
1. Use the release pipeline to upload or register the package.
1. Deploy through Power Platform admin center.
1. RDS retrieves and installs the POS extension package.
1. Validate the Store Commerce experience.

Validate POS deployments by confirming that Store Commerce loads successfully after deployment and that custom controls, operations, triggers, or workflows behave as expected. If the extension changes offline-supported scenarios, validate offline behavior as part of your smoke test.

## Set up pipelines for e-commerce extensions

For e-commerce extensions, use Azure DevOps to build, package, and publish the deployable package. The release pipeline then uploads or registers the package for deployment. Power Platform admin center orchestrates deployment to the target environment. EDS retrieves and installs the e-commerce package.

Validate e-commerce deployments by opening the target site and testing the pages, modules, themes, checkout flows, browse flows, and data actions that the extension changes. Confirm that unrelated storefront scenarios continue to work as expected.

## Public preview limitations and considerations

Review the following considerations before you use the preview:

- Start with sandbox and nonproduction environments.
- Migration from LCS-managed Commerce environments or CSUs to Power Platform admin center isn't supported during public preview.
- New production Commerce deployments can continue through LCS until general availability.
- Feature availability, supported regions, lifecycle actions, and user interface labels can change before general availability.
- Some lifecycle actions might be available only in selected environments or regions during preview.
- The Power Platform admin center experience doesn't replace every existing LCS Commerce capability during preview.

## Frequently asked questions

### Is migration from existing LCS-managed CSUs to Power Platform admin center supported during public preview?

No. Migration from LCS-managed CSUs to Power Platform admin center isn't supported during public preview.

### Do new production Commerce deployments need to move to Power Platform admin center during public preview?

No. New production Commerce deployments can continue to use LCS during public preview.

### Which Commerce extension types are supported?

Public preview supports CSU, POS, and e-commerce extension scenarios.

### What role does Power Platform admin center play in deployment?

Power Platform admin center orchestrates the deployment request and provides the administrative deployment experience. RDS and EDS handle package retrieval and installation for Commerce components.

### What role does Azure DevOps play?

Azure DevOps builds, validates, packages, and publishes Commerce extension artifacts. Release pipelines then upload or register those packages for deployment.

## Troubleshoot

| Issue | What to check |
| ----- | ------------- |
| Package doesn't appear for deployment | Confirm that the release pipeline uploaded or registered the correct artifact for the target environment. |
| Pipeline can't upload package | Check the app registration, application user security role, secure variables, Dataverse URL, tenant ID, and package path. |
| Deployment starts but installation fails | Review Power Platform admin center deployment status and the relevant Commerce deployment service logs. Validate the package manifest and extension type. |
| E-commerce site doesn't show changes | Confirm that the package version deployed to the target environment, and refresh site caches if required by your validation process. |
| POS extension isn't visible | Confirm that Store Commerce updated to the deployed package and validate store or register assignment. |
| CSU behavior is unchanged | Confirm that the CSU package installed successfully and that the target channel uses the updated scale unit. |

## Related information

- [Power Platform admin center](https://admin.powerplatform.microsoft.com/)
- [Azure Pipelines](/azure/devops/pipelines/)
- [Set up a build pipeline for the independent-packaging SDK](build-pipeline.md)
- [Commerce Scale Unit core](CSU-core.md)
- [Commerce Scale Unit packaging](CSU-packaging.md)
- [Commerce SDK samples](retail-sdk/sdk-github.md)
- [Commerce runtime extensibility](commerce-runtime-extensibility.md)
- [Dynamics 365 Commerce Scale Unit GitHub repository](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
