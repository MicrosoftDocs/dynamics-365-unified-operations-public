---
# required metadata

title: Import or export customized security configuration using Data management 
description: The topic provides an overview of how customized security configuration can be exported and imported across environments using the Data management framework.
author: tonyafehr
manager: Peakerbl
ms.date: 07/15/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: peakerbl
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: 10.0.12
---

# Import or export customized security configuration using Data management 

[!include[banner](../includes/banner.md)]

The topic provides an overview of how customized security configuration can be
exported and imported across environments using the [Data management
framework](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entities-data-packages).
This can for example be used when the is a need to move customized security
configuration from a test environment to a production environment.

The following entities holds the customized role-based security, i.e.
privileges, duties and roles that has been added or modified using Security
configuration:

-   **Security privilege metadata customization entity**

-   **Security duty metadata customization entity**

-   **Security role metadata customization entity**

**Export customized security configuration**
--------------------------------------------

1.  Go to **System administration \> Workspaces \> Data management**.

2.  Click the **Export** tile.

3.  Enter a **Group name** and set **Generate data package** to yes.

    ![](media/cb4da5cdf487ee4c55f931f1e220cdf9.png)

4.  Click the **Add multiple** menu action.

5.  Filter for **Entities** = ‘Security’ and **Entity category** = ‘Master’.

6.  Select ‘Excel’ as **Target data format**.

7.  Select the applicable security customization entities.

8.  Click **Add selected**.

    From version 10.012, ignore any warning messages about data length, they are
    not applicable since the included entities use containers in data package
    mode.

9.  Click **Close**.

10.  Make sure that the **Sequence** field value is set in order of the entity
    dependencies, i.e. first Privileges, then Duties and last Roles.

11.  Click **Export**.

12.  Click **Close**.

13. Wait for the job to complete, click **Refresh** to see the status.

14. Click **Download package**.

15. Save the package

**Import customized security configuration**
--------------------------------------------

1.  Go to **System administration \> Workspaces \> Data management**.

2.  Click the **Import** tile.

3.  Enter a **Group name**.

4.  Click **Add file**.

5.  Click **Upload and add**.

6.  Locate the exported package and click **Open.**

    From version 10.012, ignore any warning messages about data length, they are
    not applicable since the included entities use containers in data package
    mode.

7.  Click **Close**.

8.  Click **Import**.

9.  Click **Close**.

10. Wait for the job to complete, click **Refresh** to see the status.

**Related security configuration entities:**
--------------------------------------------

-   **SystemSecurityUserRoleOrganizationEntity**: assignment of organizations to
    security roles.

-   **Security segregation of duties rule**: segregation of duties rules.

-   **Security segregation of duties conflict**: segregation of duties
    conflicts. This entity has unresolved, but also reviewed conflicts.

**Additional resources**
------------------------

-   <https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/data-import-export-job>

-   [Move all user and security settings with data entities - By Andre Arnaud De
    Calavon
    [blog]](https://dynamicspedia.com/2020/05/move-all-user-and-security-settings-with-data-entities/)
