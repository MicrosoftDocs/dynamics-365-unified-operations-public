---
title: Write back to D365 Finance Budget Register Entry
description: Learn how to export finalized budgets and forecasts from Business Performance Planning to Dynamics 365 Finance Budget Register Entry, ensuring governance and accuracy.
author: romainpham
---

# Write back to D365 Finance Budget Register Entry

## Overview

The **Write back to Budget Register Entry** feature allows organizations to seamlessly export finalized budgets and forecasts from **Business Performance Planning (BPP)** into **Dynamics 365 Finance**.

This integration ensures that budgets created in BPP are validated and recorded in the **Budget Register Entry (BRE)** tables of Dynamics 365 Finance, preserving governance and compliance while eliminating manual uploads or data transformation steps.

With this capability, finance teams can:
- Write back budgets and forecasts at the same level of detail defined in their **Budget Model** in D365 Finance.
- Maintain full schema validation, ensuring field alignment and dimensional accuracy.
- Automate data transfer between **Power BI–based planning** and **ERP governance**—providing transparency, simplicity, and speed.

> [!NOTE]
> The **Write back to Budget Register Entry** feature is available as part of the **Business Performance Planning app version 1.14 (November 2025 release)**.  
> This capability is accessible **within the new Data Model Builder experience**, under the **Cube Preview** page, and is **only available for cubes created via Cube Preview**.


---

## Prerequisites

Before using the Write back to BRE feature, ensure the following requirements are met:

- You have the **Business Performance Planning Administrator** or **Business Performance Planning Power User** security role assigned.
- Your **Business Performance Planning environment** is connected to a **Dynamics 365 Finance environment** through Dataverse (via virtual tables or Dual-write).
- At least one **Budget Model** exists in Dynamics 365 Finance under the target Legal Entity.
- The **Planning Cube** in BPP was **created through the Cube Preview page** in the **New Data Model Builder**, and contains the financial dimensions and measures required by the target Budget Model (such as Main account, Department, Cost center, Date, and Amount).
- Supported environments: both **Sandbox** and **Production** with valid D365 Finance linkage.
- At least one column in your Date dimension link to your cube you want to export, must be of Date type.

> [!IMPORTANT]
> In **Dynamics 365 Finance**, a **default account structure** must be configured before Budget Register Entries can be created.  
> For setup guidance, see [Budget overview configuration](https://learn.microsoft.com/en-us/dynamics365/finance/budgeting/basic-budgeting-overview-configuration#configuration).

---

### Finance and Operations user and security prerequisites

To enable Business Performance Planning (BPP) to write back to Budget Register Entry (BRE) in Dynamics 365 Finance, specific user roles and connection ownerships must be configured correctly.  
The user who installs or updates the app, as well as the user designated as the **flow owner**, must have the appropriate Finance & Operations roles to allow data upload and workflow execution.

---

#### Default flow ownership behavior

By default, the **user who installs or updates the BPP app** automatically becomes the **default owner** of all Power Automate flows related to the BRE export process.  
This means that:
- Their **Dataverse connection** is used by default for all flows.  
- Their **current access level** to the **Finance virtual entities** is inherited during installation.  

If this installer user doesn’t have the correct Finance roles or connections, the export may fail.  
In such cases, ownership of the flows should be reassigned to a user with the required Finance privileges (typically the BPP Administrator or flow owner).

---

#### Required roles and duties in Finance

| **Role / Duty** | **Purpose** | **Required for** |
|------------------|-------------|------------------|
| **Custom role** including duty **Inquire into dimension parameters master** | Enables access to dimension parameters and allows the **BREExportFromDataverseToFnO** workflow to execute successfully. This duty ensures every entry created in Finance includes the correct user tag (flow owner). | Flow owner / user configuring BRE export |
| **Role:** *Data management operations user* | Grants access to all **Virtual Entities** in the environment. This is the **minimum required role** for any user who triggers the export from BPP. | Flow owner and any export-triggering user |

> [!IMPORTANT]  
> The user who installs, updates, or configures the export for the first time (the **default flow owner**) must have **both roles** listed above.  
> If either role is missing, the upload to Finance will fail.

---

#### Example: How role ownership affects export behavior

Consider the following scenario:

- **User A – IT Administrator**  
  - Installs or updates BPP in the environment.  
  - Automatically becomes the default flow owner after installation.  
  - Does **not** have any Finance security roles and doesn’t wish to be assigned them.  

- **User B – BPP Administrator**  
  - Responsible for maintaining the Power Automate workflows and managing exports.  
  - Has both **Data management operations user** and **custom role** (with duty *Inquire into dimension parameters master*).  
  - Should be reassigned as the **flow owner** for all BRE-related flows.  
  - All BRE entries created from exports will be tagged in Finance under **User B’s** name.  

- **User C – Planner or end user**  
  - Triggers the export directly from the BPP app UI.  
  - Has only the **Data management operations user** role (minimum requirement).  
  - Their export will execute under **User B’s** context (the flow owner).

In this setup:
- **User B** must open the **Power Automate solution** (*Dynamics Extended Planning and Analysis Workflows*) and reassign ownership of all BRE-related flows (**BREExportFromDataverseToFnO**, **CountTotalCubeRows**, and **BREExportFnOStatusUpdate**).  
- When taking ownership, **User B** must reconnect both **Dataverse** and **Finance & Operations** connections using their own credentials (the credentials that have the required roles).  
- Any export triggered by any user will then create **Budget Register Entry records under User B’s Finance account**, as the export runs in their context.

---

#### Summary of role and ownership requirements

| **User Type** | **Example User** | **Required Roles in Finance** | **Purpose / Responsibility** |
|----------------|------------------|--------------------------------|-------------------------------|
| IT Administrator | User A | None | Installs or updates BPP. Becomes the default flow owner by installation, but should reassign ownership if lacking Finance privileges. |
| BPP Administrator (Flow Owner) | User B | Data management operations user, and Custom role with duty *Inquire into dimension parameters master* | Maintains workflows, owns Dataverse and Finance connections, and serves as the user context for BRE entries. |
| End User (Export Trigger) | User C | Data management operations user | Initiates exports from the BPP app UI. The export runs under the flow owner’s context. |

> [!TIP]  
> If export failures occur with messages such as **“No permission to execute Finance operation”**, verify that the **flow owner** (for example, User B) has both required roles and that all Power Automate flows are owned and connected under their account.


For detailed steps, see  
➡️ [Set up Finance & Operations user roles for BRE write-back](./setup-finance-roles-bre-writeback.md)

---

### Finance connection and virtual entities

During installation, BPP automatically creates an environment variable to store the Finance connection URL.

| Property | Value |
|-----------|--------|
| **Display Name** | BPP App FinOps URI |
| **Name** | msdyn_xpna_BPPAppFinOpsURI |

If the Finance environment wasn’t linked during deployment, this variable must be configured manually.  
In addition, several **virtual entities** must be enabled in Dataverse so that BPP can access Finance data such as ledgers, budget models, and dimension parameters.

For configuration guidance, see  
➡️ [Configure the Finance connection and virtual entities for BRE write-back](./configure-finance-connection-virtual-entities.md)

---

### Power Automate workflows and connections

The **Write back to Budget Register Entry** process uses several Power Automate workflows to orchestrate the export between Dataverse and Dynamics 365 Finance.  
These workflows must be installed, connected, and activated correctly for the export to function.

#### Required Power Automate workflows

| Workflow name | Connection type | Purpose |
|----------------|------------------|----------|
| **BREExportFromDataverseToFnO** | Dataverse | Triggers the export process and calls the plug-in that sends data to Finance. |
| **CountTotalCubeRows** | Dataverse | Calculates and validates the total number of rows to be exported from the selected cube. |
| **BREExportFnOStatusUpdate** | Dataverse and Finance & Operations | Retrieves and updates the export status from the Finance pipeline once the export process is complete. |

---

#### 1. Verify or create required connections

The **BREExportFromDataverseToFnO** and **CountTotalCubeRows** workflows rely solely on the **Dataverse** connection.  
These connections are automatically created during the installation of Business Performance Planning.  
You can verify them in **Power Automate > Solutions > Dynamics Extended Planning and Analysis Workflows** — ensure they appear as active and are turned **On**.

The **BREExportFnOStatusUpdate** workflow requires **both Dataverse and Finance & Operations connections**.  
This connection must be created manually and associated with the flow owner for proper execution.

---

#### 2. Set up the Finance & Operations connection

1. Open the **Power Automate Maker portal** at [make.powerautomate.com](https://make.powerautomate.com).  
2. Go to **Connections** > **+ New connection**.  
3. In the list, search for and select **Finance & Operations (Dynamics 365)**.  
4. Under **Authentication type**, choose **OAuth**.  
5. When prompted, a Windows authentication pop-up appears.  
   - Sign in with a user profile that has access to your **Dynamics 365 Finance** environment.  
6. Once created, confirm that the connection status shows as **Connected**.

---

#### 3. Enable the BREExportFnOStatusUpdate workflow

1. In Power Automate, navigate to **Solutions**.  
2. Locate the solution named **Dynamics Extended Planning and Analysis Workflows**.  
3. Open the workflow **BREExportFnOStatusUpdate**.  
4. Verify that the **connections** are mapped correctly — one for **Dataverse**, one for **Finance & Operations**.  
5. Turn the flow **On**.

> [!TIP]
> The **BREExportFnOStatusUpdate** flow must run using the **flow owner’s context**.  
> If the owner doesn’t have a valid Finance connection or sufficient privileges, the export status update will fail.
> 
>If you're unable to **Turn On** the flow from the **Details summary** page, select **Edit**, then **Save** the flow.  
> After saving, return to the details page and you should now be able to **Turn On** the flow successfully.

---

#### 4. Summary of workflow behavior

| Workflow | Trigger | Key responsibility | Connection required |
|-----------|----------|--------------------|---------------------|
| BREExportFromDataverseToFnO | User export action in BPP | Calls the plug-in to write data from Dataverse to Finance | Dataverse |
| CountTotalCubeRows | System-triggered during export | Counts total rows to validate the dataset before export | Dataverse |
| BREExportFnOStatusUpdate | Called post-export | Retrieves export completion status from Finance | Dataverse and Finance & Operations |

---

#### 5. Date dimension requirement

At least one column in your **Date dimension** must be of **Date type**.  
This field is used in the export configuration to define the transaction date in the Budget Register Entry records.

> [!IMPORTANT]
> If the cube’s Date dimension doesn’t contain a column of data type **Date**, the export configuration cannot proceed and will fail validation.


---

## Export budgets to D365 Finance

Once your budget or forecast has been finalized and approved in BPP, follow these steps to create Budget Register Entries in Dynamics 365 Finance.

### Step 1. Open your Planning Cube
1. From your BPP workspace,, in **Cubes (Preview)** select a **Published** cube  that contains your finalized scenario.  
2. On the command ribbon, select **Export** > **Export to Budget Register Entries**.

### Step 2. Configure export settings
A sliding configuration pane opens. This pane guides you through setting up the export.

1. **Name** your export (for example, *FY26 OPEX Budget*).  
2. Select the **Legal entity** in Dynamics 365 Finance where the budget should be created.  
3. Once a legal entity is selected, BPP automatically retrieves the list of **Budget Models** available in that environment.  
4. Choose the target **Budget Model** for this export.

### Step 3. Map your fields
After selecting the Budget Model, the **Mapping parameters** section displays all mandatory fields required by D365 Finance, such as:

- Financial dimensions (e.g. Main account, Department, Cost center, Business unit)  
- Date (need to be mapped with a column Date type)
- Amount 
- Currency (optional)

Map each of these to the corresponding columns from your Planning Cube.  
Any unmapped required field will be highlighted until resolved.

> [!NOTE]
> The Planning Cube in BPP can contain data at a **different or lower granularity** than the Budget Model defined in Dynamics 365 Finance.  
> During write-back, BPP will create **one Budget Register Entry line for each record** returned by the applied filter in the cube.  
> 
> **Example:**  
> Using the HOL *ContosoFinancials* sample data, if the filter criteria are **Account = 510350** and **Business Unit = 001**, and the cube includes **12 detailed rows** that meet those conditions, the export will create **12 corresponding Budget Register Entry lines** in Dynamics 365 Finance—one for each matching record in the cube.



### Step 4. Filter your export lines
Optionally, define filters to limit which lines are included in the export.  
For example, you can filter by department, period, or scenario to focus on a specific subset of data.

>[!NOTE]
> Currently, filtering on **Linked Columns** from Column Link dimensions isn’t supported.
For example, if you want to filter scenarios where the Status is Approved, and that status value comes from a linked column, you won’t be able to use the Status linked column as a filter criterion.

### Step 5. Export to Dynamics 365 Finance
When the mapping and filters are complete, select **Export**.

BPP validates your configuration against the Budget Model schema and then creates corresponding **Budget Register Entry records** in Dynamics 365 Finance.  
A confirmation message appears when the process is complete.

---

## Review and reuse exports

You can review all previously created exports from the same Planning Cube.

1. In the ribbon, select **All BRE Exports**.  
2. The list displays every export created, including the export name, legal entity, budget model, creation date, and status.  
3. To reuse an existing configuration, open a previous export and select **Reuse configuration**.  
   The system prepopulates the name, mappings, and filters—allowing you to quickly generate a new batch of Budget Register Entries.

>[!NOTE]
> The ability to review and reuse previous BRE exports will be available starting with **Business Performance Planning version 1.15**.
> This upcoming feature will allow users to view all past exports from a Planning Cube and quickly reuse existing configurations—including mappings and filters—to generate new Budget Register Entries.


---

## Validation and troubleshooting

| Scenario | System behavior |
|-----------|----------------|
| Missing required field mapping | The system displays a validation message and prevents export until all required fields are mapped. |
| Invalid data type or value | The system highlights the affected field and prompts correction before proceeding. |
| Cube granularity lower than Budget Model | BPP automatically aggregates values to the correct Budget Model level before exporting to Finance. |
| Missing Finance connection URL variable | The export fails with *Finance service not reachable*. Verify the `msdyn_xpna_BPPAppFinOpsURI` variable and update it with your Finance URL. |
| Missing Finance user roles | The export fails with *No permission to execute Finance operation*. Ensure the export user exists in Finance and has required roles. |
| Export completed successfully | A toast notification confirms **Budget Register Entries created successfully.** |
| Export failed after multiple retries | The system retries the export five times before failing. If you see repeated integration errors, contact your administrator or Microsoft support. |

---

## Benefits

- **Accuracy:** Validations ensure exported data matches the D365 Finance Budget Model schema.  
- **Governance:** Budgets are recorded in the ERP system with the same structure and controls as native entries.  
- **Speed:** No more manual Excel uploads—exports happen directly from Power BI through BPP.  
- **Reusability:** Previous configurations can be reused for faster future exports.  
- **Flexibility:** Support for cubes at a lower granularity ensures planners can model data in more detail without losing consistency in Finance.  

---

## Related links

- [Set up Finance & Operations user roles for BRE write-back](./setup-finance-roles-bre-writeback.md)  
- [Configure the Finance connection and virtual entities for BRE write-back](./configure-finance-connection-virtual-entities.md)  
- [Set up Budget Models in Dynamics 365 Finance](https://learn.microsoft.com/en-us/dynamics365/finance/budgeting/budget-models)  
- [Basic budgeting overview configuration](https://learn.microsoft.com/en-us/dynamics365/finance/budgeting/basic-budgeting-overview-configuration#configuration)  
- [Create and configure Planning Cubes in BPP](https://learn.microsoft.com/en-us/dynamics365/finance/business-performance-planning/create-cubes)  
- [Manage security roles and privileges in BPP](https://learn.microsoft.com/en-us/dynamics365/finance/business-performance-planning/bpp-security)
