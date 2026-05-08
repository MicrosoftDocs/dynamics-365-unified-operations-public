---
title: ER migration cleanup
description: Learn how you can use the ER migration cleanup function to resolve issues with ER templates, including an outline on applicability.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-01-01
ms.search.form: ERSolutionTable, ERWorkspace, ERParameters, ERMigrationCleanup
ms.dyn365.ops.version: AX 8.0.0
ms.assetid: 
ms.custom:
  - sfi-image-nochange
---

# ER migration cleanup

[!include[banner](../includes/banner.md)]

When you manage your Finance instances, you might decide to migrate your current instance to another location. For example, you might migrate your production instance to a new sandbox environment. If you configured the Electronic reporting (ER) framework to store templates in Microsoft Azure Blob storage, the **DocuValue** table in the new sandbox environment refers to the instance of Blob storage in the production environment. However, you can't access this instance from the sandbox environment because the migration process doesn't support the migration of artifacts in Blob storage. Instead, in the new sandbox environment, you refer to the instance of Blob storage in the sandbox environment that doesn't yet have the ER templates.

If you try to run an ER format that uses a template to generate business documents, an exception occurs, and you're notified about the missing template. You're also guided to use the ER migration cleanup option to delete and then re-import the ER format configuration that contains the template.

:::image type="content" source="./media/er-migration-cleanup-run.png" alt-text="Screenshot of running an ER format." lightbox="./media/er-migration-cleanup-run.png":::

You receive a similar error if you go to the **Configurations** page (**Organization administration** > **Electronic reporting** > **Configurations**) and in the configurations tree, try to delete an ER format configuration that uses a template.

:::image type="content" source="./media/er-migration-cleanup-delete.png" alt-text="Screenshot of deleting an ER format." lightbox="./media/er-migration-cleanup-delete.png":::

Complete the following steps to resolve issues with ER templates that you can't access.

1. Go to **Organization administration** > **Periodic** > **Migration cleanup**.
1. Select an ER format configuration that you can't execute or delete.
1. Select **Delete**.
1. Confirm the deletion of the selected ER format configuration.
1. [Import](download-electronic-reporting-configuration-lcs.md) the deleted ER format configuration to the current Finance instance.

## Applicability

> [!IMPORTANT]
> The **Migration cleanup** option is only for ER format configurations that contain non-accessible ER templates. When you use the **Migration cleanup** option to delete an ER format configuration, ER deletes the templates that are related to the configuration artifacts in the only application database. ER doesn't validate the existence of the appropriate physical files in Blob storage. Instead, ER assumes that there are none. Therefore, don't use the **Migration cleanup** option as an alternative to the ER configuration deletion option on the **Configurations** page. Use the **Migration cleanup** option only when the ER configuration deletion option on the **Configurations** page failed.
>
> If you use the **Migration cleanup** option to delete an ER format configuration when the referred template is available in the Blob storage, you only delete related configuration artifacts in the application database. The physical file of the template in the Blob storage remains. File overwriting in Blob storage is no longer allowed. For more information, see [KB4557217](https://fix.lcs.dynamics.com/Issue/Details?kb=4557217). Additionally, you can't re-import the configurations deleted by using the Migration cleanup in this environment. To resolve this issue, you need to find the corresponding file in Blob storage and manually delete it.

:::image type="content" source="./media/er-migration-cleanup-import.png" alt-text="Screenshot of importing an ER format." lightbox="./media/er-migration-cleanup-import.png":::

A similar problem can occur if you migrate your application instance to another location that you used as a migration target more than once and for which the Blob storage already contains ER template files.

Because you can have several ER format configurations, this process can be time consuming. Therefore, using the [Backup storage of ER templates](er-backup-storage-templates.md) feature to automatically recover templates with broken references is preferred.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
