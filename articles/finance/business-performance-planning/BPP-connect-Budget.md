---
title: Configure the Finance connection and virtual entities for Budget register entry write-back
description: Learn how to configure the Finance connection for Business performance planning write-back to Budget register entry.
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

# Configure the Finance connection and virtual entities for Budget register entry write-back

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

## Overview

To enable Business performance planning to write back budgets and forecasts to Dynamics 365 Finance, connect Dataverse to the corresponding Finance environment. Define this connection by using an environment variable and a set of virtual entities that provide access to Finance data such as ledgers, budget models, and dimension structures.

If this setup is incomplete, the export fails with errors: 

- Finance service not reachable
- No permission to execute

> [!NOTE]
> The **Write back to budget register entry** feature is available as part of the Business performance planning app version 1.14 (November 2025 release).  
> This capability is accessible within the new Data model builder experience, under the **Cube (preview)** page, and is only available for cubes created using the **Cube (preview)**.

### Configure the Finance connection environment variable

During package deployment, the environment variable is created automatically. If you already linked your Dataverse environment to Dynamics 365 Finance, the variable value is populated automatically.  
If not, set it manually.

| **Property** | **Value** |
|---------------|-----------|
| **Display Name** | BPP App FinOps URI |
| **Name** | msdyn_xpna_BPPAppFinOpsURI |
| **Type** | Text |
| **Purpose** | Defines the Finance environment URL for BPP Dataverse connection. |

### Steps to configure manually

1. Open the **Power Platform Maker portal** for your Business performance planning environment.  
1. Go to **Solutions** and open the solution **Default solution**.  
1. Select **Environment variables**.  
1. Open **BPP App FinOps URI**.  
1. In the **Current value** field, enter the URL of your Finance environment (for example, `https://contoso.operations.dynamics.com`).  
1. Save and publish the solution.

> [!NOTE]
> This variable is automatically created during installation. If you configure the Finance–Dataverse link later, you must update this variable manually to establish the connection.

### Enable virtual entities in Dataverse

Business performance planning relies on virtual entities to access Finance data such as ledgers, budget models, and dimension structures. These virtual entities must be visible and accessible in the environment.

The following virtual entities are required:

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

1. Open **Power Platform Admin Center**.  
1. Select your environment.
1. Go to **Settings > Advanced settings**.  
1. Select **Filter** and search for **Available finance and operations entities**.
1. Select **Continue**.  
1. For each entity listed in the previous section:  
   a. Add a filter condition matching the entity name.  
   b. Select **Apply**.  
   c. Open the entity record.  
   d. Select the **Visible** checkbox.  
   e. Select **Save and close**.  
1. Repeat for all required entities.

These steps make the Finance virtual entities visible and accessible to Business performance planning for write-back operations. If you don't make an entity visible, the export fails with the **Unable to load Finance entity definitions** error.

### Validation

After completing the setup, follow these steps to validate the connection:

- Restart your export in Business performance planning.  
- Verify that the Finance entities are successfully loaded and the connection variable points to the correct URL.  
- If you continue to experience export failures, confirm the Dynamics 365 finance and operations user roles are configured correctly. For more information, see [Set up Finance and Operations user roles for budget register entry write-back](bpp-bud-reg-user.md).


## Related links

- [Write back to Dynamics 365 Finance budget register entry](bpp-bud-reg-write.md)  
- [Business performance planning overview](business-performance-planning-overview.md)






