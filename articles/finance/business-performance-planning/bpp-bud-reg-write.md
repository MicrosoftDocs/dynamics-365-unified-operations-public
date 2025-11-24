---
title: Write back to Dynamics 365 Finance budget register entry
description: Learn how to export finalized budgets and forecasts from Business performance planning to Dynamics 365 Finance budget register entry.
author: twheeloc
ms.author: romainpham
ms.topic: install-set-up-deploy
ms.date: 11/14/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 


---

# Write back to Dynamics 365 Finance budget register entry

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

## Overview

The **Write back to budget register entry** feature allows organizations to seamlessly export finalized budgets and forecasts from Business performance planning into Dynamics 365 Finance.

This integration ensures that budgets created in Business performance planning are validated and recorded in the budget register entry tables of Dynamics 365 Finance, preserving governance and compliance while eliminating manual uploads or data transformation steps.

With this capability, finance teams can:
- Write back budgets and forecasts at the same level of detail defined in their **Budget Model** in Dynamics 365 Finance.
- Maintain full schema validation, ensuring field alignment and dimensional accuracy.
- Automate data transfer between **Power BI–based planning** and **ERP governance**.

> [!NOTE]
> The **Write back to budget register entry** feature is available as part of the **Business performance planning app version 1.14 (November 2025 release)**.  
> This capability is accessible within the new Data model builder experience, under the **Cube (preview)** page, and is only available for cubes created using the **Cube (preview)**.


## Prerequisites

Before using the Write back to budget register entry feature, ensure the following requirements are met:

- You have the **Business performance planning administrator** or **Business performance planning Power User** security role assigned.
- Your Business performance planning environment is connected to a Dynamics 365 Finance environment through Dataverse (via virtual tables or Dual-write).
- At least one **Budget model** exists in Dynamics 365 Finance under the target legal entity.
- The planning cube in Business performance planning was created through the **Cube (preview)** page in the new Data model builder, and contains the financial dimensions and measures required by the target Budget model (such as Main account, Department, Cost center, Date, and Amount).
- Supported environments: both **Sandbox** and **Production** with valid Dynamics 365 Finance linkage.
- At least one column in your Date dimension link to your cube you want to export, must be of Date type.

> [!IMPORTANT]
> In **Dynamics 365 Finance**, a default account structure must be configured before budget register entry can be created.  
> For setup guidance, see [Budget overview configuration](../budgeting/basic-budgeting-overview-configuration.md).


### Finance and operations user and security prerequisites

To enable Business performance planning to write back to budget register entry in Dynamics 365 Finance, specific user roles and connection ownerships must be configured correctly.  
The user who installs or updates the app, as well as the user designated as the flow owner, must have the appropriate Dynamics 365 Finance roles to allow data upload and workflow execution.

---

#### Default flow ownership behavior

By default, the user who installs or updates the Business performance planning app automatically becomes the default owner of all Power Automate flows related to the budget register entry export process.  
This means that:
- Their **Dataverse connection** is used by default for all flows.  
- Their current access level to the **Finance virtual entities** is inherited during installation.  

If this installer user doesn’t have the correct Finance roles or connections, the export may fail. In such cases, ownership of the flows should be reassigned to a user with the required Finance privileges (typically the Business performance planning administrator or flow owner).


#### Required roles and duties in Dynamics 365 Finance

| **Role / Duty** | **Purpose** | **Required for** |
|------------------|-------------|------------------|
| **Custom role** including duty **Inquire into dimension parameters master** | Enables access to dimension parameters and allows the **BREExportFromDataverseToFnO** workflow to execute successfully. This duty ensures every entry created in Dynamics 365 Finance includes the correct user tag (flow owner). | Flow owner / user configuring budget register entry export |
| **Role:** *Data management operations user* | Grants access to all **Virtual entities** in the environment. This is the minimum required role for any user who triggers the export from Business performance planning. | Flow owner and any export-triggering user |

> [!IMPORTANT]  
> The user who installs, updates, or configures the export for the first time must have both roles listed above.  
> If either role is missing, the upload to Dynamics 365 Finance fails.


#### Example: How role ownership affects export behavior

Consider the following scenario:

- **User A – IT Administrator**  
  - Installs or updates Business performance planning in the environment.  
  - Automatically becomes the default flow owner after installation.  
  - Doesn't have any Dynamics 365 Finance security roles and doesn’t wish to be assigned them.  

- **User B – Business performance planning Administrator**  
  - Responsible for maintaining the Power Automate workflows and managing exports.  
  - Has both Data management operations user and custom role with the Inquire into dimension parameters master duty.  
  - Should be reassigned as the flow owner for all budget register entry related flows.  
  - All budget register entry entries created from exports are tagged in Dynamics 365 Finance under User B’s name.  

- **User C – Planner or end user**  
  - Triggers the export directly from the Business performance planning app.  
  - Has only the Data management operations user role.  
  - Their export executes under **User B’s** context (the flow owner).

In this setup:
- **User B** must open Power Automate, Dynamics 365 Finance extended planning and analysis workflows, and reassign ownership of all budget register entry related flows: **BREExportFromDataverseToFnO**, **CountTotalCubeRows**, and **BREExportFnOStatusUpdate**.  
- When taking ownership, **User B** must reconnect both Dataverse and Dynamics 365 Finance connections using their own credentials (the credentials that have the required roles).  
- Any export triggered by any user creates budget register entry records under User B’s Dynamics 365 Finance account, as the export runs in their context.

---

#### Summary of role and ownership requirements

| **User type** | **Example user** | **Required roles in Dynamics 365 Finance** | **Purpose / Responsibility** |
|----------------|------------------|--------------------------------|-------------------------------|
| IT Administrator | User A | None | Installs or updates Business performance planning. Becomes the default flow owner by installation, but should reassign ownership if lacking Finance privileges. |
| BPP Administrator (Flow Owner) | User B | Data management operations user, and custom role with the Inquire into dimension parameters master duty | Maintains workflows, owns Dataverse and Finance connections, and serves as the user context for budget register entry entries. |
| End user (Export Trigger) | User C | Data management operations user | Initiates exports from the Business performance planning app. The export runs under the flow owner’s context. |

> [!TIP]  
> If export fails with the **No permission to execute Finance operation** error, verify that the flow owner (for example, User B) has both required roles and that all Power Automate flows are owned and connected under their account.


For more information, see [Set up Dynamics 365 Finance user roles for budget register entry write-back](bpp-bud-reg-user.md)

### Dynamics 365 Finance connection and virtual entities

During installation, Business performance planning automatically creates an environment variable to store the Dynamics 365 Finance connection URL.

| Property | Value |
|-----------|--------|
| **Display name** | BPP App FinOps URI |
| **Name** | msdyn_xpna_BPPAppFinOpsURI |

If the Dynamics 365 Finance environment wasn’t linked during deployment, this variable must be configured manually.  
In addition, several virtual entities must be enabled in Dataverse so that Business performance planning can access Dynamics 365 Finance data such as ledgers, budget models, and dimension parameters.

For configuration guidance, see [Configure the Dynamics 365 Finance connection and virtual entities for budget register entry write-back](BPP-connect-Budget.md)

### Power Automate workflows and connections

The write-back to budget register entry process uses several Power Automate workflows to orchestrate the export between Dataverse and Dynamics 365 Finance.  
These workflows must be installed, connected, and activated correctly for the export to function.

#### Required Power Automate workflows

| Workflow name | Connection type | Purpose |
|----------------|------------------|----------|
| **BREExportFromDataverseToFnO** | Dataverse | Triggers the export process and calls the plug-in that sends data to Dynamics 365 Finance. |
| **CountTotalCubeRows** | Dataverse | Calculates and validates the total number of rows to be exported from the selected cube. |
| **BREExportFnOStatusUpdate** | Dataverse and Dynamics 365 Finance | Retrieves and updates the export status from the Dynamics 365 Finance pipeline once the export process is complete. |


#### Verify or create required connections

The **BREExportFromDataverseToFnO** and **CountTotalCubeRows** workflows rely solely on the **Dataverse** connection. These connections are automatically created during the installation of Business performance planning. You can verify them in **Power Automate > Solutions > Dynamics Extended Planning and Analysis Workflows** and ensure they appear as active and are turned on.

The **BREExportFnOStatusUpdate** workflow requires **both Dataverse and Finance & Operations connections**. This connection must be created manually and associated with the flow owner for proper execution.


#### Set up the Dynamics 365 Finance connection

1. Open the **Power Automate Maker portal** at [make.powerautomate.com](https://make.powerautomate.com).  
2. Go to **Connections** > **+ New connection**.  
3. In the list, search for and select **Dynamics 365 Finance (Dynamics 365)**.  
4. Under **Authentication type**, choose **OAuth**.  
5. When prompted, a Windows authentication pop-up appears.  
   - Sign in with a user profile that has access to your **Dynamics 365 Finance** environment.  
6. Once created, confirm that the connection status shows as **Connected**.

#### Enable the BREExportFnOStatusUpdate workflow

1. In Power Automate, navigate to **Solutions**.  
2. Locate the solution named **Dynamics Extended Planning and Analysis Workflows**.  
3. Open the workflow **BREExportFnOStatusUpdate**.  
4. Verify that the connections are mapped correctly. One for Dataverse and one for Dynamics 365 Finance.  
5. Turn the flow on.

> [!TIP]
> The **BREExportFnOStatusUpdate** flow must run using the flow owner’s context. If the owner doesn’t have a valid Dynamics 365 Finance connection or sufficient privileges, the export status update fails.
> If you're unable to turn on the flow from the **Details summary** page, select **Edit**, then **Save** the flow.  
> After saving, return to the details page and you should now be able to turn on the flow successfully.

#### Summary of workflow behavior

| Workflow | Trigger | Key responsibility | Connection required |
|-----------|----------|--------------------|---------------------|
| BREExportFromDataverseToFnO | User export action in Business performance planning | Calls the plug-in to write data from Dataverse to Dynamics 365 Finance | Dataverse |
| CountTotalCubeRows | System-triggered during export | Counts total rows to validate the dataset before export | Dataverse |
| BREExportFnOStatusUpdate | Called post-export | Retrieves export completion status from Finance | Dataverse and Dynamics 365 Finance |

---

#### Date dimension requirement

At least one column in your Date dimension must be of Date type. This field is used in the export configuration to define the transaction date in the budget register entry records.

> [!IMPORTANT]
> If the cube’s Date dimension doesn’t contain a column of data type **Date**, the export configuration can't proceed and faila validation.


## Export budgets to Dynamics 365 Finance

Once your budget or forecast has been finalized and approved in Business performance planning, follow these steps to create budget register entry in Dynamics 365 Finance.

### Open your planning cube
1. From your Business performance planning workspace,, in **Cubes (preview)** select a **Published** cube  that contains your finalized scenario.  
2. On the command ribbon, select **Export** > **Export to budget register entry**.

### Configure export settings
A sliding configuration pane opens. This pane guides you through setting up the export.

1. **Name** your export (for example, *FY26 OPEX Budget*).  
2. Select the **Legal entity** in Dynamics 365 Finance where the budget should be created.  
3. Once a legal entity is selected, Business performance planning automatically retrieves the list of Budget models available in that environment.  
4. Choose the target Budget model for this export.

### Map your fields
After selecting the Budget model, the **Mapping parameters** section displays all mandatory fields required by Dynamics 365 Finance, such as:

- Financial dimensions (e.g. Main account, Department, Cost center, Business unit)  
- Date (need to be mapped with a column Date type)
- Amount 
- Currency (optional)

Map each of these to the corresponding columns from your planning cube. Any unmapped required field will be highlighted until resolved.

> [!NOTE]
> The planning cube in Business performance planning can contain data at a different or lower granularity than the budget model defined in Dynamics 365 Finance.  
> During write-back, Business performance planning creates one budget register entry line for each record returned by the applied filter in the cube.  

### Filter your export lines
Optionally, define filters to limit which lines are included in the export. For example, you can filter by department, period, or scenario to focus on a specific subset of data.

>[!NOTE]
> Currently, filtering on Linked columns from Column link dimensions isn’t supported. For example, if you want to filter scenarios where the status is approved, and that status value comes from a linked column, you won’t be able to use the Status linked column as a filter criterion.

### Export to Dynamics 365 Finance
When the mapping and filters are complete, select **Export**.

Business performance planning validates your configuration against the budget model schema and then creates corresponding budget register entry records in Dynamics 365 Finance.  
A confirmation message appears when the process is complete.

### Review and reuse exports

To review all previously created exports from the same planning cube, follow these steps:
1. In the ribbon, select **All budget register entry exports**.  
2. The list displays every export created, including the export name, legal entity, budget model, creation date, and status.  
3. To reuse an existing configuration, open a previous export and select **Reuse configuration**.  
   The system prepopulates the name, mappings, and filters. This allows you to quickly generate a new batch of budget register entries.

>[!NOTE]
> The ability to review and reuse previous budget register entry exports will be available starting with **Business performance planning version 1.15**.
> This upcoming feature will allow users to view all past exports from a planning cube and quickly reuse existing configurations, including mappings and filters, to generate new budget register entries.


### Validation and troubleshooting

| Scenario | System behavior |
|-----------|----------------|
| Missing required field mapping | The system displays a validation message and prevents export until all required fields are mapped. |
| Invalid data type or value | The system highlights the affected field and prompts correction before proceeding. |
| Cube granularity lower than Budget model | Business performance planning automatically aggregates values to the correct Budget Model level before exporting to Dynamics 365 Finance. |
| Missing Finance connection URL variable | The export fails with *Finance service not reachable*. Verify the `msdyn_xpna_BPPAppFinOpsURI` variable and update it with your Dynamics 365 Finance URL. |
| Missing Finance user roles | The export fails with *No permission to execute Finance operation*. Ensure the export user exists in Finance and has required roles. |
| Export completed successfully | A toast notification confirms budget register entries created successfully. |
| Export failed after multiple retries | The system retries the export five times before failing. If you see repeated integration errors, contact your administrator or Microsoft support. |

### Benefits

- **Accuracy:** Validations ensure exported data matches the Dynamics 365 Finance budget model schema.  
- **Governance:** Budgets are recorded in Dynamics 365 Finance with the same structure and controls as native entries.  
- **Speed:** No more manual Excel uploads. Exports happen directly from Power BI through Business performance planning.  
- **Reusability:** Previous configurations can be reused for faster future exports.  
- **Flexibility:** Support for cubes at a lower granularity ensures planners can model data in more detail without losing consistency in Dynamics 365 Finance.  

### Related links

- [Set up Dynamics 365 Finance user roles for budget register entry write-back](bpp-bud-reg-user.md)  
- [Configure the Dynamics 365 Finance connection and virtual entities for budget register entry write-back](BPP-connect-Budget.md)  
- [Basic budgeting overview configuration](../budgeting/basic-budgeting-overview-configuration.md)  
- [Create and configure cubes in Business performance planning](create-cubes.md)  
- [Manage security roles and privileges in Business performance planning](bpp-security.md)







