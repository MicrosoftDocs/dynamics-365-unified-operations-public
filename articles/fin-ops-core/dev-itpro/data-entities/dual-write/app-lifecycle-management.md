---
title: Application lifecycle management
description: Learn about application lifecycle management and the benefits of making dual-write solutions, including how to install dual-write solutions.
author: nhelgren
ms.author: nhelgren
ms.topic: article
ms.date: 01/15/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Application lifecycle management

[!include [banner](../../includes/banner.md)]



By making dual-write solution-aware, you enable basic application lifecycle management (ALM) capabilities, such as transportation and backup/restore of dual-write table maps across environments. You also enable scenarios where you can get solutions published by Microsoft or an independent software vendor (ISV) from Marketplace.

## What is a dual-write solution?

A dual-write solution can contain one or more dual-write table maps. You can import these maps into your environment (by selecting **Solutions** in Microsoft Power Apps). You can also export them as a package to other environments. You can import Microsoft-published or ISV-published table maps from Marketplace, modify them in your test environment, test them, and then, when they're ready, export them to your production environment. Additionally, you can publish your solution through Marketplace, so that other people can use it.

There are two types of solutions: managed and unmanaged.

You can't modify a managed solution, and you can uninstall it after you import it. When you import an unmanaged solution, you add all the components of that solution into your environment. If you import an unmanaged solution that contains components you already customized, your customizations are overwritten by the customizations in the imported unmanaged solution.

For more information about solutions, see the [solutions overview](/powerapps/maker/common-data-service/solutions-overview).

## Install the dual-write core solution

You must install the dual-write core solution in your environments. The solution contains metadata for your table maps.

1. In Power Apps, select **Solutions** in the left pane.
1. Select **Open Marketplace**, and search for the solution named **Dual Write Core**.
1. Follow the prompts to import the solution.

    :::image type="content" source="media/import-solution.png" alt-text="Screenshot of the import dual-write core solution dialog in Power Apps.":::

## <a id="install-table-maps"></a>Install the dual-write table maps solution

1. In Power Apps, select **Solutions** in the left pane.
1. Select **Open Marketplace**, and search for the solution named **Dataverse Add-in for finance and operations package**.
1. Follow the prompts to import the solution.
1. In the finance and operations app, on the **Dual-write** page, select **Apply Solution** to apply the table maps that you downloaded and installed. After you apply the solution, you see that the default table maps are published.

    :::image type="content" source="media/default-entity-maps.png" alt-text="Screenshot of the dual-write table maps page showing published default table maps.":::

You successfully imported and applied a Microsoft-published dual-write table maps solution to your environment.

## Import table maps through a dual-write solution and apply them to your environment (New environments)

This section explains how to import table maps from Marketplace and apply them to your environment.

:::image type="content" source="media/import-apply-entity-maps.png" alt-text="Screenshot of the process flow for importing and applying table maps.":::

1. Import the dual-write core solution.

    1. Create a new dual-write environment (a finance and operations app environment and a Dataverse environment).
    1. Follow the instructions in the [Install the dual-write core solution](#install-the-dual-write-core-solution) section earlier in this article to install the dual-write core solution from Marketplace in Power Apps.
    1. Verify that the dual-write core solution is listed under **Solutions** in Power Apps.

1. Import the Microsoft-published or ISV-published table maps solution.

    1. Follow the instructions in the [Install the dual-write table maps solution](#install-table-maps) section to download and install the Microsoft-published or ISV-published table maps from Marketplace in Power Apps.
    1. Verify that the table maps solution is listed under **Solutions** in Power Apps.

1. Apply the dual-write table maps solution to your finance and operations app environment.

    Apply the solution that you downloaded by selecting **Apply Solutions** on the **Dual-write** page in the finance and operations app, as described in the [Install the dual-write table maps solution](#install-table-maps) section.

## <a id="update-table-maps"></a>Update table maps and export them to other environments as a solution

This section explains how to export your customized table maps as a solution, use it as a backup, and move the artifacts across environments or publish them to Marketplace.

:::image type="content" source="media/export-maps-solution.png" alt-text="Screenshot of the process flow for exporting customized maps as a solution.":::

### Customize your table maps

First, customize your table maps by modifying existing table maps and adding a new table map.

1. In the finance and operations app, on the **Table mappings** tab, customize the mappings for the default table map that you installed by using a solution. To add a new table map, select **Add Table**. In both cases, when you save the table map, specify the publisher and the version number.

    The following figure shows how to add a new column named **birthday** to the contacts - CDS Contacts V2 table map and select the default publisher.

    :::image type="content" source="media/add-new-birthday-field.png" alt-text="Screenshot of adding a new birthday column to the contacts table map.":::

    > [!NOTE]
    > When you [create a new solution](#create-new-solution) by using these modified table maps, you must specify the same publisher.

    The following figure shows how to add a new table map named **Address books**.

    :::image type="content" source="media/add-address-book.png" alt-text="Screenshot of adding a new Address books table map.":::

1. Confirm the table maps that you modified and added. Be sure to enable and test them, to ensure that they work as you expect.

    :::image type="content" source="media/confirm-new-entity-maps.png" alt-text="Screenshot of the confirmation page showing new and modified table maps.":::

### <a id="create-new-solution"></a>Create a new dual-write solution and add your components (customized table maps)

After you customize your mappings and add new mappings, create a new dual-write solution and add the table maps to it.

1. In Power Apps, select **Solutions** in the left pane, and then select **New solution** to create a solution. For this example, name the solution **MyCustomTableMaps**. Select the same publisher that you selected in previous steps.

    :::image type="content" source="media/add-map-to-solution.png" alt-text="Screenshot of creating a new solution and adding table maps in Power Apps.":::

1. Select **Create**. The new solution appears on the **Solutions** list page.

    :::image type="content" source="media/show-new-solution.png" alt-text="Screenshot of the Solutions list page showing the new solution.":::

1. Select the **MyCustomTableMaps** solution that you created. Select **Add existing**, point to **Other**, and then select **Dual Write table map**.

    :::image type="content" source="media/add-customized-maps.png" alt-text="Screenshot of adding customized table maps to the solution.":::

1. In the list, select the customized table maps, and add them to the solution. The solution should now contain your customized tables.

    :::image type="content" source="media/entities-new-solution.png" alt-text="Screenshot of the solution showing customized tables added.":::

You customized your tables and put them into a solution.

### Export and publish your solution

After you run the solution checker and make sure that there are no problems, export the solution that you created and publish the changes.

1. In the list of solutions, select your solution, and then select **Export**.
1. Update the version number, and select whether you want to export the solution as a managed or unmanaged solution. Export it as a managed solution. Then select **Export**.

    :::image type="content" source="media/update-version-number.png" alt-text="Screenshot of updating the version number and exporting the solution.":::

1. Before you export, select **Publish all changes**, and then select **Check for issues**. When you finish, select **Next** to publish all your changes.

    :::image type="content" source="media/export-and-publish.png" alt-text="Screenshot of publishing changes before exporting the solution.":::

    The solution, together with all its components, is exported to a zip file.

    :::image type="content" source="media/components-to-zip.png" alt-text="Screenshot of the solution exported to a zip file with all components.":::

You customized your tables, added them to a new solution, and created a solution file that you can import and apply to other environments. This capability can be useful if you want to move table maps between test and production environments. In a similar way, you can create a backup of all your table maps by adding them to a solution and exporting the solution as a package. You can then import that package into any environment to restore the table maps.

For information about how to publish the package to the Marketplace, see [Publish your app on Marketplace](/powerapps/developer/common-data-service/publish-app-appsource).

### Test your exported solution package

Test your exported solution package by importing and applying it to another environment.

1. In Power Apps, select **Import** to import the package into a new environment.

    :::image type="content" source="media/import-package.png" alt-text="Screenshot of importing the package into a new environment in Power Apps.":::

1. Apply the solution that you imported to the environment.

    :::image type="content" source="media/apply-solution-to-environment.png" alt-text="Screenshot of applying the imported solution to the environment.":::

1. Verify that the two customized table maps appear on the dual-write table maps list page.

    :::image type="content" source="media/entity-maps-in-list.png" alt-text="Screenshot of the dual-write table maps list showing two customized table maps.":::

1. Make sure that the customizations from previous steps are preserved.

    :::image type="content" source="media/check-customizations.png" alt-text="Screenshot of verifying that customizations are preserved in the table maps.":::

### Use the table map version

Sometimes, a solution might contain different implementations of a table map. For example, the version of the contacts - CDS Contacts V2 table map might have a different publisher or a newer version number. In these cases, use the **Table Map version** button to select which table map you want to use in your environment.

:::image type="content" source="media/select-entity-map.png" alt-text="Screenshot of selecting the table map version to use in an environment.":::

## Upgrade existing dual-write environments for solution awareness (Existing environments)

1. Import the dual-write core solution.

    1. Follow the instructions in the [Install the dual-write core solution](#install-the-dual-write-core-solution) section earlier in this article to import the dual-write core solution from Marketplace into Power Apps.
    1. Verify that the dual-write core solution is listed under **Solutions** in Power Apps.

1. Upgrade the table maps.

    You see a notification prompting you to upgrade.

    :::image type="content" source="media/upgrade-prompt.png" alt-text="Screenshot of the notification prompt to upgrade table maps.":::

    Select **Upgrade table maps** at the top of the page.

    :::image type="content" source="media/upgrade-entity-maps.png" alt-text="Screenshot of the upgrade table maps option in the dual-write interface.":::

The upgrade takes a few minutes. When it's completed, you receive a notification.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
