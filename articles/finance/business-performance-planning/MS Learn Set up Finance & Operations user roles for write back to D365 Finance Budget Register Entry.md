---
title: Set up Finance & Operations user roles for BRE write-back
description: Learn which roles and duties are required in Dynamics 365 Finance for Business Performance Planning to successfully export data to Budget Register Entry.
author: romainpham

---

# Set up Finance & Operations user roles for BRE write-back

## Overview

For Business Performance Planning (BPP) to export finalized budgets or forecasts to **Budget Register Entry (BRE)** in Dynamics 365 Finance, the user account used by the export process (the *flow installer account*) must also exist as a user in Dynamics 365 Finance and have the correct security roles.

If these roles aren’t present, the write-back operation will fail with a **“No permission to execute”** or similar authorization error.

---

## Required user configuration

### 1. Add the export user to Dynamics 365 Finance

The user who installs and runs the export (the **flow installer**) must:
- Exist as a valid user in Dynamics 365 Finance (same Azure AD identity as in Dataverse).  
- Be enabled and active.

To verify or add the user:
1. In Dynamics 365 Finance, go to **System administration > Users > Users**.  
2. Verify the user exists and is enabled.  
3. If missing, select **New**, enter the user’s Azure AD email, and assign the required roles below.

---

### 2. Assign the required roles and duties

| **Role / Duty** | **Purpose** | **Mandatory** | **Notes** |
|------------------|-------------|----------------|------------|
| **Custom role with duty:** *Inquire into dimension parameters master* | Grants permission to query and validate dimension parameters required during export. | ✔ | Currently required for dimension resolution. The team is exploring options to remove this dependency in future releases. |
| **Role:** *Data management operations user* | Allows the user to access Data Management Framework and Virtual Entities required for the export process. | ✔ | Required to create projects, load data, and validate Finance entities. |

To assign:
1. Go to **System administration > Users > Users**.  
2. Select the export user.  
3. Choose **Assign roles**.  
4. Add both the **Data management operations user** role and your **custom role** that includes the duty *Inquire into dimension parameters master*.  
5. Save the configuration.

---

### 3. Common error scenarios

| **Error message** | **Cause** | **Resolution** |
|--------------------|------------|----------------|
| *No permission to execute Finance operation* | The export user isn’t added to Finance or lacks required duties. | Add the user in F&O and assign the roles above. |
| *Access denied when reading dimension parameters* | Missing duty *Inquire into dimension parameters master*. | Create a custom role including this duty. |
| *Unable to access virtual entities or integration group* | Missing *Data management operations user* role. | Assign the Data management operations user role in Finance. |

---

## Next steps
After verifying the roles and user configuration:
- Ensure the **Finance connection variable** and **virtual entities** are correctly configured in Dataverse.  
- For detailed setup steps, see:  
  ➡️ [Configure the Finance connection and virtual entities for BRE write-back](./configure-finance-connection-virtual-entities.md)

