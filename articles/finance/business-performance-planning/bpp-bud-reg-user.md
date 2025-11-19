---
title: Set up Dynamics 365 Finance user roles for budget register entry write-back
description: Learn which roles and duties are required in Dynamics 365 Finance for Business Performance Planning to successfully export data to budget register entry.
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

# Set up Dynamics 365 Finance user roles for budget register entry write-back

## Overview

For Business performance planning to export finalized budgets or forecasts to budget register entry in Dynamics 365 Finance, the user account used by the export process (the *flow installer account*) must also exist as a user in Dynamics 365 Finance and have the correct security roles.

If these roles aren’t present, the write-back operation fails with a **No permission to execute** error.

> [!NOTE]
> The **Write back to budget register entry** feature is available as part of the Business performance planning app version 1.14 (November 2025 release).  
> This capability is accessible within the new Data model builder experience, under the **Cube (preview)** page, and is only available for cubes created using the **Cube (preview)**.


### Add the export user to Dynamics 365 Finance

The user who installs and runs the export must:
- Exist as a valid user in Dynamics 365 Finance (same Azure AD identity as in Dataverse).  
- Be enabled and active.

To verify or add the user:
1. In Dynamics 365 Finance, go to **System administration > Users > Users**.  
2. Verify the user exists and is enabled.  
3. If missing, select **New**.
4. Enter the user’s Azure AD email, and assign the required roles below.

### Assign the required roles and duties

| **Role / Duty** | **Purpose** | **Mandatory** | **Notes** |
|------------------|-------------|----------------|------------|
| **Custom role with duty** -  Inquire into dimension parameters master | Grants permission to query and validate dimension parameters required during export. | ✔ | Currently required for dimension resolution. |
| **Role** - Data management operations user | Allows the user to access Data Management Framework and virtual entities required for the export process. | ✔ | Required to create projects, load data, and validate Finance entities. |

To assign roles and duties, follow these steps:
1. Go to **System administration > Users > Users**.  
2. Select the export user.  
3. Choose **Assign roles**.  
4. Add both the **Data management operations user** role and your custom role that includes the **Inquire into dimension parameters master** dute.  
5. Save the configuration.


### Common error scenarios

| **Error message** | **Cause** | **Resolution** |
|--------------------|------------|----------------|
| No permission to execute Finance operation | The export user isn’t added to Finance or lacks required duties. | Add the user in Dynamics 365 Finance and assign the roles above. |
| Access denied when reading dimension parameters | Missing Inquire into dimension parameters master duty. | Create a custom role including this duty. |
| Unable to access virtual entities or integration group | Missing Data management operations user role. | Assign the Data management operations user role in Finance. |

After verifying the roles and user configuration, ensure the Finance connection variable and virtual entities are correctly configured in Dataverse.  
For more information, see [Configure the Finance connection and virtual entities for write-back](bpp-bud-reg-write.md).




