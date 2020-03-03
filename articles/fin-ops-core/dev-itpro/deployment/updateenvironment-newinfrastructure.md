---
# required metadata

title: Update an environment
description: This topic explains how to update an environment that was deployed by using the self-service deployment experience.
author: laneswenka
manager: AnnBe
ms.date: 09/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Update an environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This topic walks through the process of applying updates to an environment that was deployed by using the [self-service deployment](infrastructure-stack.md) experience.

> [!IMPORTANT]
> In the next-generation infrastructure, updates are applied differently than they are applied in the current flow. *Whatever is provided in the package is applied to the environment, and it **overwrites** whatever is already present in that environment.* Therefore, you **must** create a single deployable package that contains all customizations and independent software vendor (ISV) solutions from your build environment. If the list of models in the environment differs from the list of models in in the package, you receive a warning before the update is applied. For information about how to create a single package, see [Manage third-party models and runtime packages by using source control](../dev-tools/manage-runtime-packages.md).

## Supported package types

Because environments that are deployed by using the [self-service deployment](infrastructure-stack.md) experience will be running on version 8.1 (October 2018) or a later version, the following package types are supported:

- **AOT deployable package** – A deployable package that is generated from application metadata and source code. This type of deployable package is created in a **build** environment.
- **Binary update package** – A deployable package that contains dynamic-link libraries (DLLs), and other binaries and metadata that the platform and application depend on. This type of package is released by Microsoft.

## Development Application Lifecycle Management (ALM) flow

To apply code customizations to your sandbox and production environments, you must create a deployable code package from your build environment. For more information, see [Create deployable packages of models](create-apply-deployable-package.md).

## Microsoft updates

To access Microsoft updates, go to the environment details page for your environment in Microsoft Dynamics Lifecycle Services (LCS). You will see a **single tile** that shows a cumulative binary update of all the application and platform fixes. To apply this update, select the package, and then select **Save Package** to save the Microsoft update to the project asset library.

## Apply updates

### Tier 1 sandbox/develop and test/demo/build environments

To apply updates to a Tier 1 sandbox/develop and test/demo/build environment that was deployed through LCS, follow the steps in [Apply updates to cloud environments](apply-deployable-package-system.md).

### Tier 2 and above Standard Acceptance Test/sandbox environments

> [!IMPORTANT]
> Package application causes system downtime. All relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

Before you begin, verify that the deployable package has been uploaded to the project asset library in LCS, and that validations have succeeded.

After the package is in the project asset library, follow these steps to update your environment.

1. Open the environment details page for the environment where you want to apply the package.
2. Select **Maintain \> Apply updates** to apply an update.
3. Enter a **unique name** for the update. You will use this name to identify the update that you want to move to the production environment.
4. Select the package to apply. Use the filter at the top to find your package. The list will include application and platform binary packages and application deployable packages that have passed validation from the asset library.
5. Select **Apply**.

    The status in the upper-right corner of the environment details page changes from **Queued** to **Servicing**. Then, when package application is completed, the status changes to **Deployed**.

6. After package application is completed, the environment history is updated. To view the environment history, select **History \> Environment changes** on the environment details page.
7. You can also download the logs from the environment history page.
8. After the validations are completed, you can sign-off on the update from the environment history page by selecting either **Sign off** or **Sign off with issues**.

### Production environment

To improve the reliability of updates that are applied to a production environment, a specific update that is done in the sandbox environment is designated ("marked") as a **release candidate** and moved to the production environment. This update contains both the base product and the customization. Therefore, both will be moved over when the selected update is applied to the production environment. This behavior differs from the current servicing behavior. Currently, you can move only the customization, but the base product **will not** change. In the case of a self-service deployment environment, the base product version **might change**, depending on the update that is marked as a release candidate in the sandbox environment.

> [!IMPORTANT]
> Package application causes system downtime. All relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

After you've successfully applied the update in the sandbox environment and are ready to move the update over to the production environment, follow these steps to mark an update as a release candidate.

1. Open the environment history page by selecting **History \> Environment changes** on the environment details page.
2. Select the update to move over to the production environment.
3. In the details for the update, select **Mark as release candidate**.

    The **Is Release Candidate** option is set to **Yes**.

After you've marked an update as a release candidate, follow these steps to update your environment.

1. Open the environment details page for the production environment.
2. Select **Maintain \> Update environment** to apply an update.
3. In the **Available sandboxes** list, select the source sandbox environment where the update was applied, validated, and marked as a release candidate.
4. In the grid, select the update to apply to the production environment. This grid shows only updates that have been marked as release candidates.
5. In the **Downtime start** field, select a date and time. The environment will be taken down for servicing at the specified time on the specified date. The **Downtime end** field is set to through hours from the start of the downtime.

    No lead time is required for this update.

6. Select **Schedule**. LCS runs validations to make sure that the selected update is applicable to the environment. To prevent downgrade of the environment, the update isn't allowed if its application version is lower than the current environment version. Additionally, customers are asked to confirm that they want the update to proceed.

    If the update is **successfully** scheduled, an email notification is sent to all project stakeholders.

    The status in the upper-right corner of the environment details page changes from **Queued** to **Servicing**. Then, when the update is completed, the status changes to **Deployed**.

    All stakeholders are notified of the progress of the operation.

7. After the update is completed, the environment history is updated. To view the environment history, select **History \> Environment changes** on the environment details page.
8. You can also download the logs from the environment history page.
9. After the validations are completed, you can sign-off on the update from the environment history page by selecting either **Sign off** or **Sign off with issues**.

> [!NOTE]
> If there is an on-going operation in the environment, or if the environment is already running on the same version or a later version, the scheduled update is canceled. When a scheduled update is canceled, an email notification is sent to all project stakeholders. Customers can also cancel an update by selecting **Cancel** on the environment details page. If customers want to reschedule or change an update, they can cancel the current operation and schedule a new one.

> [!IMPORTANT]
> For environments that are deployed in the modern infrastructure stack, if servicing is unsuccessful, the environment is automatically rolled back. To learn why the operation was unsuccessful, you can download the logs from the environment history page.
