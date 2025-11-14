---
title: Configure the Finance connection and virtual entities for Budget register entry write-back
description: Learn how to configure the Finance connection variable and enable required virtual entities for Business performance planning write-back to Budget register entry.
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

# Configure the Finance connection and virtual entities for Budget register entry write-back

## Overview

To enable Business performance planning to write back budgets and forecasts to Dynamics 365 Finance, Dataverse must be connected to the corresponding Finance environment.  
This connection is defined using an environment variable and a set of virtual entities that provide access to Finance data such as ledgers, budget models, and dimension structures.

If this setup is incomplete, the export fails with errors: 
 - Finance service not reachable
 - No permission to execute

## Configure the Finance connection environment variable

During package deployment, the environment variable is created automatically. If your Dataverse environment was already linked to Dynamics 365 Finance, the variable value is populated automatically.  
If not, it must be set manually.

| **Property** | **Value** |
|---------------|-----------|
| **Display Name** | BPP App FinOps URI |
| **Name** | msdyn_xpna_BPPAppFinOpsURI |
| **Type** | Text |
| **Purpose** | Defines the Finance environment URL for BPP Dataverse connection. |

### Steps to configure manually
1. Open the **Power Platform Maker portal** for your Business performance planning environment.  
2. Go to **Solutions** and open the solution **Default solution**.  
3. Select **Environment variables**.  
4. Open **BPP App FinOps URI**.  
5. In the **Current value** field, enter the URL of your Finance environment (for example, `https://contoso.operations.dynamics.com`).  
6. Save and publish the solution.

> [!NOTE]
> This variable is automatically created during installation. If the Finance–Dataverse link was configured later, you must update this variable manually to establish the connection.

---

## Enable virtual entities in Dataverse

Business performance planning relies on virtual entities to access Finance data such as ledgers, budget models, and dimension structures.  
These must be visible and accessible in the environment.

The following are required virtual entities:
- LedgerEntity  
- BudgetModelEntity  
- BudgetDimensionEntity  
- DimensionIntegrationFormatEntity  
- BudgetCodeEntity  
- DataManagementDefinitionGroupEntity  
- DataManagementDefinitionGroupDetailEntity  
- DimensionParametersEntity  

### Enable virtual entities

To enable virtual entities, follow these steps:
1. Open **Power Platform Admin Center (PPAC)**.  
2. Select your environment and go to **Settings > Advanced settings**.  
3. Click **Filter** icon in the top-right corner.  
4. Search for **Available Finance and Operations entities**, and select **Continue**.  
5. For each entity listed above:  
   a. Add a filter condition matching the entity name.  
   b. Click **Apply**.  
   c. Open the entity record.  
   d. Select the **Visible** checkbox.  
   e. Click **Save and close**.  
6. Repeat for all required entities.

These steps make the Finance virtual entities visible and accessible to Business performance planning for write-back operations.  
If any entity remains hidden, the export fails with the error message, Unable to load Finance entity definitions.

### Validation

After completing setup, follow these steps to validate the connection:
- Restart your export in Business performance planning.  
- Verify that the Finance entities are successfully loaded and the connection variable points to the correct URL.  
- If you continue to experience export failures, confirm the finance and operations user roles are configured correctly. For more information, see [Set up Finance and Operations user roles for budget register entry write-back](./setup-finance-roles-bre-writeback.md).

---

## Related links
- [Write back to Dynamics 365 Finance budget register entry](./write-back-to-bre.md)  
- [Set up Finance and Operations user roles for budget register entry write-back](./setup-finance-roles-bre-writeback.md)  
- [Business performance planning overview](https://learn.microsoft.com/en-us/dynamics365/finance/business-performance-planning/overview)


