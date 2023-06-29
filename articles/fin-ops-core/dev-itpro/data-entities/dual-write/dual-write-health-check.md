---
title: Dual-write health check
description: This article describes the dual-write configuration health check, including details on the error codes that can result from the health check.
author: jaredha
ms.date: 06/30/2023
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: 
ms.search.region: global
ms.author: jaredha
ms.search.validFrom: 2023-06-06
---

# Dual-write health check

[!include [banner](../../includes/banner.md)]

The dual-write health check runs validations to ensure that the environment meets system requirements, and that the required configurations for dual-write have been completed. The health check is typically done as part of the setup and configuration process for dual-write, to ensure the prerequisite configuration is completed before entity maps are set up. However, it can also be done as a troubleshooting step if issues occur after configuration is completed.

## Run the dual-write health check

To run the dual-write health check, follow these steps.

1. In the finance and operations apps environment, on the **Dual-write** page, on the Action Pane, select **Health check**.
1. Follow the steps in the dual-write health check wizard.

## Steps in the dual-write health check

There are two steps in the validation: the prerequisite health check and dependency validation.

### Prerequisite health check

The prerequisite health check verifies that the system requirements and prerequisites have been met, so that the dual-write configuration can link the finance and operations apps environment to the Microsoft Dataverse environment. This check ensures that the required solutions have been installed in the environment, and that permissions have been configured to grant access to the environments.

For more information about the validations for prerequisite configuration, see [System requirements and prerequisites](./requirements-and-prerequisites.md). This article includes information about the health check results and the requirements for fixing any issues that the health check identifies.

### Dependency validation

After the prerequisites have been met, and the finance and operations apps environment and Dataverse environment are linked, you must configure the dual-write entity maps to sync between the linked environments. The dependency validation ensures that this configuration is completed.

> [!NOTE]
> All errors in the prerequisite health check must be fixed before the dependency validation is done.

Three dependency validations are done:

- **APIHubConnection** – There must be a connection to APIHub for the finance and operations apps environment and the Dataverse environment.
- **StaleConfiguration** – Dual-write entity map configurations must match the entity in both the finance and operations apps environment and the Dataverse environment.
- **BusinessUnit** – Configuration must be completed for the default team of the root business unit of the Dataverse environment.

The following table lists the error codes that can occur during the dual-write health check.

| Error code | Description | How to fix the error |
|------------|-------------|----------------------|
| DWDVEV1001 | Missing Dataverse APIHub connection, without ConnectionFix support. | <p>This error indicates that the APIHub connection for Dataverse that's used in dual-write doesn't exist. It might have been deleted from the Power Apps maker portal.</p><p>To fix this error, reset dual-write by following the instructions in [Reset dual-write connections](./reset.md).</p> |
| DWFOEV1001 | Missing finance and operations apps APIHub connection without ConnectionFix support. | <p>This error indicates that the APIHub connection for finance and operations apps that's used in dual-write doesn't exist. It might have been deleted from the Power Apps maker portal.</p><p>To fix this error, reset dual-write by following the instructions in [Reset dual-write connections](./reset.md).</p> |
| DWDVEV1003 | Company mismatched between dual-write and Dataverse. | <p>This error indicates that the company (legal entity) that's linked to dual-write doesn't match the company in Dataverse. In other words, the legal entities that are configured on the **Dual-write** page in finance and operations apps don't match the legal entities that are set up in Dataverse.</p><p>To view the list of legal entities in finance and operations apps, select **Environment details** on the **Dual-write** page, and then review the list on the **Legal entities** tab. To view the list of legal entities in Dataverse, review the records in the **Company** (**cdm\_company**) table in Dataverse. The legal entities that are listed for dual-write in finance and operations apps must exist in the **Company** table in Dataverse.</p><p>There are two options for fixing this error:</p><ul><li>Get the list of mismatched companies from the error message in the health check, and remove the mismatched companies from the dual-write configuration.</li><li>Reset the dual-write connection by following the instructions in [Reset dual-write connections](./reset.md).</li></ul> |
| DWFOEV1003 | Company mismatched between dual-write and finance and operations apps. | <p>This error indicates that the company (legal entity) that's linked to dual-write doesn't match the legal entity in finance and operations apps. In other words, the legal entities that are configured on the **Dual-write** page in finance and operations apps don't match the legal entities that are set up in Dataverse.</p><p>To view the list of legal entities in finance and operations apps, select **Environment details** on the **Dual-write** page, and then review the list on the **Legal entities** tab. To view the list of legal entities in Dataverse, review the records in the **Company** (**cdm\_company**) table in Dataverse. The legal entities that are listed for dual-write in finance and operations apps must exist in the **Company** table in Dataverse.</p><p> There are two options for fixing this error:</p><ul><li>Get the list of mismatched companies from the error message in the health check, and remove the mismatched companies from the dual-write configuration.</li><li>Reset the dual-write connection by following the instructions in [Reset dual-write connections](./reset.md).</li></ul> |
| DWDVEV1004 | <p>Stale dual-write configurations are present in Dataverse. | After the dual-write link between the finance and operations apps environment and the Dataverse environment is removed, dual-write runtime configurations might remain in Dataverse. This error indicates that stale configurations exist in the Dataverse environment.</p><p>To fix this error, follow the steps for cleaning up Dataverse configurations in the [Fix synchronization issues in an environment that has recently changed Dataverse environment](./dual-write-troubleshooting-live-sync.md#fix-synchronization-issues-in-an-environment-that-has-a-recently-changed-dataverse-environment) section of the dual-write troubleshooting guide.</p> |
| DWFOEV1004 | <p>Stale dual-write configurations are present in finance and operations apps. | After the dual-write link between the finance and operations apps environment and the Dataverse environment is removed, dual-write runtime configurations might remain in the finance and operations apps environment. This error indicates that stale configurations exist in the finance and operations apps environment.</p><p>To fix this error, follow the steps for cleaning up finance and operations apps configurations in the [Fix synchronization issues in an environment that has recently changed Dataverse environment](./dual-write-troubleshooting-live-sync.md#fix-synchronization-issues-in-an-environment-that-has-a-recently-changed-dataverse-environment) section of the dual-write troubleshooting guide.</p> |
| DWFOEV1006 | Default Team name mismatch for Dataverse and dual-write. | <p>Dual-write initial synchronization uses the default team of the mapped or root business unit as the owner of the record that's imported. The name of the default team is expected to match the name of the business unit. However, if the user changes the name of the default team after the dual-write link is established, data ingestion fails, and this error occurs.</p><p>There are two options for fixing this error:</p><ul><li>Reset the dual-write connection by following the instructions in [Reset dual-write connections](./reset.md).</li><li>Open a ticket with Microsoft Support to update the details of the connection. In the ticket, you must provide the default team of the root business unit. To find this information, run the queries in the [Assign security role to the default owning team](security-roles.md#assign-security-role-to-the-default-owning-team) section of the dual-write setup guide.</li></ul> |
| DWDVEV1007 | Default owning team isn't present in company. | <p>This error indicates that no default owning team has been selected for the specified company record.</p><p>To fix this error, update the owning team directly on the company record in the Power Apps maker portal by following these steps.</p><ol><li>Open the [Power Apps maker portal](https://make.powerapps.com).</li><li>Select the environment that has the dual-write link to your finance and operations apps environment.</li><li>Open the **Tables** list.</li><li>Open the **Company** table.</li><li>If the **Default owning team** column of the table isn't already shown, select to show it.</li><li>In the **Default owning team** column, ensure that a value is selected for every company that's selected to sync with dual-write maps.</li><li>Ensure that the appropriate security roles are assigned to the selected default owning teams. For more information, see [Security roles for users and teams](security-roles.md#security-roles-for-users-and-teams).</li></ol> |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
