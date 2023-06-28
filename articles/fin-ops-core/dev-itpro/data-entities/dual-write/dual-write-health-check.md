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

The dual-write health check runs validations to ensure the environment meets system requirements and has the needed configurations completed for dual-write. The health check is typically done as part of the setup and configuration process for dual-write to ensure the prerequisite configuration is completed before setting up entity maps. The health check can also be done as a troubleshooting step if issues arise after configuration is complete.

## Running the dual-write health check

To run the dual-write health check, follow these following steps.

1. In the finance and operations apps environment, open the **Dual-write** page.
1. On the action ribbon, select the **Health check** action.
1. Follow the steps in the dual-write health check wizard.

## Steps in the dual-write health check

There are two steps in the validation: perquisite health check and dependency validation.

### Prerequisite health check
The prerequisite health check verifies the system requirements and prerequisites have been met for the dual-write configuration to link the finance and operations apps environment to the Dataverse environment. This check ensures the required solutions have been installed in the environment, and permissions have been configured to grant access to the environments. 

For more information on the validations for prerequisite configuration, see [System requirements and prerequisites](./requirements-and-prerequisites.md). This article includes information on the health check results and the requirements to resolve any issues that are identified by the health check.

### Dependency validation
When the prerequisites have been completed and the finance and operations apps environment and Dataverse environment are linked, you need to configure the dual-write entity maps to sync between the linked environments. The dependency validation ensures this configuration is complete.

> [!NOTE]
> Any errors resulting in the prerequisite health check must be resolved before performing the dependency validation.

There are three dependency validations completed.

1. **APIHubConnection**: There must be a connection to APIHub for the finance and operations apps environment and Dataverse environment.
2. **StaleConfiguration**: There may be dual-write entity map configurations that don't match the entity in either the finance and operations apps environment or Dataverse environment.
3. **BusinessUnit**: Configuration must be completed for the default team of the root business unit of the Dataverse environment.

The following table lists potential error codes that can result from the dual-write health check. 

| Error code | Description | How to fix |
| ---------- | ----------- | ---------- |
| DWDVEV1001 | Missing Dataverse APIHub connection, without ConnectionFix support. | This error indicates the APIHub connection for Dataverse that is used by dual-write doesn't exist. The connection may have been deleted from the Power Apps maker portal. To fix this issue, reset dual-write following the instructions in the [Reset dual-write connections](../reset.md) article. |
| DWFOEV1001 | Missing finance and operations apps APIHub connection without ConnectionFix support. | This error indicates the APIHub connection for finance and operations apps is getting used in dual-write doesn't exist. It may have been deleted from the Power Apps maker portal. To fix this issue, reset dual-write following the instructions in the [Reset dual-write connections](./reset.md) article. |
| DWDVEV1003 | Company mismatched between dual-write and Dataverse. | The company (legal entity) linked to dual-write doesn't match the Dataverse company. The legal entities configured in the **Dual-write** page in finance and operations apps don't match the legal entities set up in Dataverse.<br><br>You can view the list of legal entities in finance and operations apps by selecting the **Environment details** action on the **Dual-write** page, and reviewing the list on the **Legal entities** tab. You can review the list of legal entities in Dataverse by reviewing the records in the **Company** (cdm_company) table in Dataverse. The legal entities listed for dual-write in finance and operations apps must exist in the **Company** table in Dataverse.<br><br> There are two options for correcting this issue: <br><ol><li>Get the list of mismatched companies from the error message in the health check and remove the mismatched companies from the dual-write configuration.</li><li>Reset the dual-write connection following the instructions in the [Reset dual-write connections](../reset.md) article. </li></ol>|
| DWFOEV1003 | Company mismatched between dual-write and finance and operations apps. | The company (legal entity) linked to dual-write doesn't match the legal entity in finance and operations apps. This means the legal entities configured in the **Dual-write** page in finance and operations apps don't match the legal entities set up in Dataverse.<br><br>You can view the list of legal entities in finance and operations apps by selecting the **Environment details** action on the **Dual-write** page, and reviewing the list on the **Legal entities** tab. You can review the list of legal entities in Dataverse by reviewing the records in the **Company** (cdm_company) table in Dataverse. The legal entities listed for dual-write in finance and operations apps must exist in the **Company** table in Dataverse.<br><br>  There are two options for correcting this issue: <br><ol><li>Get the list of mismatched companies from the error message in the health check and remove the mismatched companies from the dual-write configuration, or</li><li>Reset the dual-write connection following the instructions in the [Reset dual-write connections](../reset.md) article. </li></ol>|
| DWDVEV1004 | Stale dual-write configuration present in Dataverse. | When the dual-write link is removed between the finance and operations environment and Dataverse environment, there may be dual-write runtime configurations remaining in Dataverse. This error indicates that the stale configurations exist in the Dataverse environment.<br><br> To resolve this error, follow the steps for cleaning up Dataverse configurations in the [Fix synchronization issues in an environment that has recently changed Dataverse environment](./dual-write-troubleshooting-live-sync.md#fix-synchronization-issues-in-an-environment-that-has-a-recently-changed-dataverse-environment) section of the dual-write troubleshooting guide. |
| DWFOEV1004 | Stale dual-write configuration present in finance and operations apps. | When the dual-write link is removed between the finance and operations environment and Dataverse environment, there may be dual-write runtime configurations remaining in the finance and operations environment. This error indicates that the stale configurations exist in the finance and operations environment.<br><br> To resolve this error, follow the steps for cleaning up finance and operations apps configurations in the [Fix synchronization issues in an environment that has recently changed Dataverse environment](./dual-write-troubleshooting-live-sync.md#fix-synchronization-issues-in-an-environment-that-has-a-recently-changed-dataverse-environment) section of the dual-write troubleshooting guide. |
| DWFOEV1006 | Default Team name mismatch for Dataverse and dual-write. | Dual-write initial sync uses the default team of the mapped or root business unit as the owner of the record to be imported. The expectation is that the name of the default team should be the same as that of the business unit. However, if the user changes the name of the default team after the dual-write link has been established, the data ingestion will fail with this error message. There are two options to resolve this error: <br><ol><li>Reset the dual-write connection following the instructions in the [Reset dual-write connections](./reset.md) article, or</li><li>Open a ticket with Microsoft Support to update the detail of the connection. In the ticket you need to provide the **default team of the root business unit**, which you can find by running the queries in the [Assign security role to the default owning team](../security-roles#assign-security-role-to-the-default-owning-team) section of the dual-write setup guide. |
| DWDVEV1007 | Default owning team isn't present in company. | This error indicates that a default owning team hasn't been selected for the specified company record. The owning team can be updated directly on the company record in the Power Apps maker portal with the following steps: <br><ol><li>Open the [Power Apps maker portal](https://make.powerapps.com), and select the environment with the dual-write link to your finance and operations environment. </li><li>Open the **Tables** list. </li><li>Open the **Company** table. </li><li>If it isn't already displayed, select to show the **Default owning team** column of the table. </li><li>Ensure a value has been selected in the **Default owning team** column for all companies that are selected to sync with dual-write maps.</li><li>When a default owning team has been set for all companies that are selected to sync for dual-write, ensure that the selected default owning teams have the appropriate security roles assigned. For more information, see [Security roles for users and teams](security-roles#security-roles-for-users-and-teams).</li></ol> |


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
