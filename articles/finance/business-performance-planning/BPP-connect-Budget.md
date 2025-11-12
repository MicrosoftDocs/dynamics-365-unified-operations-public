---
title: Configure the Finance connection and virtual entities for BRE write-back
description: Learn how to configure the Finance connection variable and enable required virtual entities for Business Performance Planning write-back to Budget Register Entry.
author: romainpham
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

# Configure the Finance connection and virtual entities for BRE write-back

## Overview

To enable Business Performance Planning (BPP) to write back budgets and forecasts to Dynamics 365 Finance, Dataverse must be connected to the corresponding Finance environment.  
This connection is defined using an **environment variable** and a set of **virtual entities** that provide access to Finance data such as ledgers, budget models, and dimension structures.

If this setup is incomplete, the export will fail with an error such as *“Finance service not reachable”* or *“No permission to execute”*.

---

## Configure the Finance connection environment variable

During package deployment, the environment variable is created automatically.  
If your Dataverse environment was already linked to Dynamics 365 Finance, the variable value is populated automatically.  
If not, it must be set manually.

| **Property** | **Value** |
|---------------|-----------|
| **Display Name** | BPP App FinOps URI |
| **Name** | msdyn_xpna_BPPAppFinOpsURI |
| **Type** | Text |
| **Purpose** | Defines the Finance environment URL for BPP Dataverse connection. |

### Steps to configure manually
1. Open the **Power Platform Maker portal** for your BPP environment.  
2. Go to **Solutions**, then locate and open the solution **Default Solution**.  
3. Select **Environment Variables**.  
4. Open **BPP App FinOps URI**.  
5. In the **Current Value** field, enter the URL of your Finance environment (for example, `https://contoso.operations.dynamics.com`).  
6. Save and publish the solution.

> [!NOTE]
> This variable is automatically created during installation. If the Finance–Dataverse link was configured later, you must update this variable manually to establish the connection.

---

## Enable virtual entities in Dataverse

Business Performance Planning relies on virtual entities to access Finance data such as ledgers, budget models, and dimension structures.  
These must be visible and accessible in the environment.

### Required virtual entities
- LedgerEntity  
- BudgetModelEntity  
- BudgetDimensionEntity  
- DimensionIntegrationFormatEntity  
- BudgetCodeEntity  
- DataManagementDefinitionGroupEntity  
- DataManagementDefinitionGroupDetailEntity  
- DimensionParametersEntity  

### Steps to enable virtual entities
1. Open **Power Platform Admin Center (PPAC)**.  
2. Select your environment and go to **Settings > Advanced settings**.  
3. Click the **Filter** icon in the top-right corner.  
4. Search for **Available Finance and Operations Entities**, and select **Continue**.  
5. For each entity listed above:  
   a. Add a filter condition matching the entity name.  
   b. Click **Apply**.  
   c. Open the entity record.  
   d. Enable the **Visible** checkbox.  
   e. Click **Save & Close**.  
6. Repeat for all required entities.

> [!TIP]
> These steps make the Finance virtual entities visible and accessible to BPP for write-back operations.  
> If any entity remains hidden, the export may fail with a message such as *“Unable to load Finance entity definitions.”*

---

## Validation

After completing setup:
- Restart your export in BPP.  
- Verify that the Finance entities are successfully loaded and the connection variable points to the correct URL.  
- If you continue to experience export failures, confirm the F&O user roles are configured as described in [Set up Finance & Operations user roles for BRE write-back](./setup-finance-roles-bre-writeback.md).

---

## Related links
- [Write back to D365 Finance Budget Register Entry](./write-back-to-bre.md)  
- [Set up Finance & Operations user roles for BRE write-back](./setup-finance-roles-bre-writeback.md)  
- [Business Performance Planning overview](https://learn.microsoft.com/en-us/dynamics365/finance/business-performance-planning/overview)

