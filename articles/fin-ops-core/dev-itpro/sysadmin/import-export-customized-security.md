---
title: Import or export a customized security configuration by using Data management
description: Learn about how a customized security configuration can be exported and imported across environments by using the Data management framework.
author: pnghub
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: 10.0.12
---

# Import or export a customized security configuration by using Data management 

[!include[banner](../includes/banner.md)]

This article explains how to export and import a customized security configuration across environments by using the [Data management framework](../data-entities/data-entities-data-packages.md). Use this functionality when you need to move a customized security configuration from a test environment to a production environment.

The following entities hold the customized, role-based security (that is, privileges, duties, and roles) that you add or modify by using security configuration:

- Security privilege metadata customization entity
- Security duty metadata customization entity
- Security role metadata customization entity

## Export customized security configuration

1. Go to **System administration \> Workspaces \> Data management**.
1. Select the **Export** tile.
1. In the **Group name** field, enter a name for the group.
1. Set the **Generate data package** option to **Yes**.

    :::image type="content" source="media/cb4da5cdf487ee4c55f931f1e220cdf9.png" alt-text="Screenshot of Setting the Generate data package option.":::

1. Select **Add multiple** to open the drop-down dialog box.
1. Filter the entities by setting the following fields:

    - In the **Entities** field, enter **Security**.
    - In the **Entity category** field, select **Master**.

1. In the **Target data format** field, select **Excel**.
1. Select the applicable security customization entities.
1. Select **Add selected**.

    > [!NOTE]
    > Ignore any warning messages that have the following format: "The data entity \<Entity name\> has public field XmlObjectFileName that isn't defined on the staging table." These messages don't apply, because the security entities use containers in the data package to store the security XML object.
    >
    > :::image type="content" source="https://user-images.githubusercontent.com/28597769/190197998-3f22ad9b-8dc7-47f9-9882-86f775616035.png" alt-text="Screenshot of Warning messages about an undefined XmlObjectFileName public field.":::

1. Select **Close**.
1. Make sure that the **Sequence** field is set in the order of the entity dependencies. Privileges should be first, then duties, and finally roles.
1. Select **Export**.
1. Select **Close**.
1. Wait for the job to complete. Select **Refresh** to view the status.
1. Select **Download package**.
1. Save the package.

## Import customized security configuration

1. Go to **System administration \> Workspaces \> Data management**.
1. Select the **Import** tile.
1. In the **Group name** field, enter a name for the group.
1. Select **Add file**.
1. Select **Upload and add**.
1. Find the exported package, and then select **Open**.

    > [!NOTE]
    > Ignore any warning messages that have the following format: "The data entity \<Entity name\> has public field XmlObjectFileName that isn't defined on the staging table." These messages don't apply, because the security entities use containers in the data package to store the security XML object.

1. Select **Close**.
1. Select **Import**.
1. Select **Close**.
1. Wait for the job to complete. Select **Refresh** to view the status.

## Related security configuration entities

- **SystemSecurityUserRoleOrganizationEntity** – Assignment of organizations to security roles.
- **Security segregation of duties rule** – Segregation of duties rules.
- **Security segregation of duties conflict** – Segregation of duties conflicts. This entity has unresolved conflicts but also reviewed conflicts.

## Additional resources

- [Data import and export jobs overview](../data-entities/data-import-export-job.md)
- [Move all user and security settings with data entities (blog post)](https://dynamicspedia.com/2020/05/move-all-user-and-security-settings-with-data-entities/), by André Arnaud de Calavon


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
