---
title: Dual-write health check
description: This article describes the dual-write configuration health check, including details on the error codes that can result from the health check
author: jaredha
ms.date: 06/06/2023
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: 
ms.search.region: global
ms.author: jaredha
ms.search.validFrom: 2023-06-06
---

# Dual-write health check

[!include [banner](../../includes/banner.md)]

The dual-write health check runs validations to ensure the environment meets system requirements and has the the needed configurations completed for dual-write. This is typically done as part of the setup and configuration process for dual-write to ensure the prerequisite configuration is completed before setting up entity maps. The health check can also be done as a troubleshooting step if issues arise after configuration has been completed.

## Running the dual-write health check
Run the dual-write health check with the following steps:
1. In the finance and operations apps environment, open the **Dual-write** page.
2. Select the **Health check** action on the action ribbon.
3. Follow the steps in the dual-write health check wizard.

## Steps in the dual-write health check

There are two steps in the validation: prequisite health check and dependency validation.

### Prerequisite health check
The prerequisite health check verifies the system requirements and prerequisites have been met for dual-write configuration to link the finance and operations apps environment to the Dataverse environment. This includes ensuring the required solutions have been installed in the environment and permission have been configured to grant access to the environments. 

See [System requirements and prerequisites](./requirements-and-prerequisites.md) for more information on the validations done for prerequisite configuration. This includes information on the health check results and requirements to resolve issues identified by the health check.

### Dependency validation
When prerequisites have been completed and a link is established between the finance and operations apps environment and Dataverse environment, there is additional required configuration needed for dual-write entity maps to sync between the linked environments. The dependency validation ensures this configuration has been completed.

> [!NOTE]
> Any errors resulting in the prerequisite health check must be resolved before performing the dependency validation.

There are three primary dependency validations completed:
1. **APIHubConnection**: There must be a connection to APIHub for the finance and operations apps environment and Dataverse environment.
2. **StaleConfiguration**: There may be dual-write entity map configurations that don't match the entity in either the finance and operations apps environment or Dataverse environment.
3. **BusinessUnit**: Configuration must be done for the default team of the root business unit of the Dataverse environment.

The following are potential error codes that can result from the configuration health check, indentifying issues in your dual-write configuration, and how to fix the resulting errors.

| Error code | Description | How to fix |
| ---------- | ----------- | ---------- |
| DWDVEV1001 | Missing Dataverse APIHub connection, without ConnectionFix support | This error in indicating that the APIHub connection for Dataverse used by dual-write doesn't exist. The connection may have been deleted from the Power Apps maker portal. To fix this issue, reset dual-write following the instructions in the [Reset dual-write connections](./reset.md) documentation. |
| DWFOEV1001 | Missing finance and operations apps APIHub connection without ConnectionFix support | This error in indicating that the APIHub connection for finance and operations apps that is getting used in dual-write doesn't exist. It may have been deleted from the Power Apps maker portal. To fix this issue, reset dual-write folliwng the instructions in the [Reset dual-write connections](./reset.md) documentation. |
| DWDVEV1003 | Company mismatched between dual-write and Dataverse | The company (legal entity) linked to dual-write doesn't match the Dataverse company. This means the legal entities configured in the **Dual-write** page in finance and operations apps do not match the legal entities set up in Dataverse.<br><br>You can view the list of legal entities in finance and operations apps by selecting the **Environment details** action on the **Dual-write** page, and reviewing the list on the **Legal entities** tab. You can review the list of legal entities in Dataverse by reviewing the records in the **Company** (cdm_company) table in Dataverse. The legal entities listed for dual-write in finance and operations apps must exist in the **Company** table in Dataverse.<br><br> There are two options for correcting this issue: <br><ol><li>Get the list of mismatched companies from the error message in the health check and remove the mismatched companies from the dual-write configuration, or</li><li>Reset the dual-write connection following the instructions in the [Reset dual-write connections](./reset.md) documentation. </li></ol>|
| DWFOEV1003 | Company mismatched between dual-write and finance and operations apps | The company (legal entity) linked to dual-write doesn't match the legal entity in finance and operations apps. This means the legal entities configured in the **Dual-write** page in finance and operations apps do not match the legal entities set up in Dataverse.<br><br>You can view the list of legal entities in finance and operations apps by selecting the **Environment details** action on the **Dual-write** page, and reviewing the list on the **Legal entities** tab. You can review the list of legal entities in Dataverse by reviewing the records in the **Company** (cdm_company) table in Dataverse. The legal entities listed for dual-write in finance and operations apps must exist in the **Company** table in Dataverse.<br><br>  There are two options for correcting this issue: <br><ol><li>Get the list of mismatched companies from the error message in the health check and remove the mismatched companies from the dual-write configuration, or</li><li>Reset the dual-write connection following the instructions in the [Reset dual-write connections](./reset.md) documentation. </li></ol>|
| DWDVEV1004 | Stale dual-write configuration present in Dataverse | When the dual-write link is removed between the finance and operations environment and Dataverse environment, there may be dual-write runtime configurations remaining in Dataverse. This error indicates that the stale configurations exist in the Dataverse environment.<br><br> To resolve this error, follow the steps for cleaning up Dataverse configurations in the [Fix synchronization issues in an environment that has recently changed Dataverse environment](./dual-write-troubleshooting-live-sync.md#fix-synchronization-issues-in-an-environment-that-has-a-recently-changed-dataverse-environment) section of the dual-write troubleshooting guide. |
| DWFOEV1004 | Stale dual-write configuration present in finance and operations apps | When the dual-write link is removed between the finance and operations environment and Dataverse environment, there may be dual-write runtime configurations remaining in the finance and operations environment. This error indicates that teh stale configurations exist in the finance and operations environment.<br><br> To resolve this error, follow the steps for cleaning up finance and operations apps configurations in the [Fix synchronization issues in an environment that has recently changed Dataverse environment](./dual-write-troubleshooting-live-sync.md#fix-synchronization-issues-in-an-environment-that-has-a-recently-changed-dataverse-environment) section of the dual-write troubleshooting guide. |
| DWFOEV1006 | Default Team name mismatch for Dataverse and dual-write | Dual-write initial sync uses the default team of the mapped or root business unit as the owner of the record to be imported. The expectation is that the name of the default team should be the same as that of the business unit. However, if the user changes the name of the default team after the dual-write link has been established, the data ingestion will fail with this error message. There are two options to resolve this error: <br><ol><li>Reset the dual-write connection following the instructions in the [Reset dual-write connections](./reset.md) documentation, or</li><li>Open a ticket with Microsoft Support to update the detail of the connection. In the ticket you will need to provide the **default team of the root business unit**, which you can find by running the queries in the [Assign security role to the default owning team](./security-roles#assign-security-role-to-the-default-owning-team) section of the dual-write setup guide. |
| DWDVEV1007 | Default owning team is not present in company | This error indicates that a default owning team has not been selected for the specified company record. This can be updated directly on the company record in the Power Apps maker portal with the following steps: <br><ol><li>Open the [Power Apps maker portal](https://make.powerapps.com), and select the environment with the dual-write link to your finance and operations environment. </li><li>Open the **Tables** list. </li><li>Open the **Company** table. </li><li>If it is not already displayed, select to show the **Default owning team** column of the table. </li><li>Ensure a value has been selected in the **Default owning team** column for all companies that are selected to sync with dual-write maps.</li><li>When a default owning team has been set for all companies that are selected to sync for dual-write, ensure that the selected default owning teams have the appropriate security roles assigned. See [Security roles for users and teams](./security-roles#security-roles-for-users-and-teams) for more information.</li></ol> |


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
