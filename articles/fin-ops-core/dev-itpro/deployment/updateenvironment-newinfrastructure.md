---
title: Update an environment
description: Learn how to update an environment that was deployed by using the self-service deployment experience, including an overview of servicing changes.
author: laneswenka
ms.author: laswenka
ms.topic: how-to
ms.date: 04/02/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-12-31
ms.search.form: 
ms.dyn365.ops.version: 8.1.1
---

# Update an environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This article explains how to apply updates to an environment that you deployed by using the [self-service deployment](infrastructure-stack.md) experience.

> [!IMPORTANT]
> In the next-generation infrastructure, you apply updates differently than in the current flow. *The update process applies whatever is provided in the package to the environment, and it **overwrites** whatever is already present in that environment.* Therefore, you **must** create a single deployable package that contains all customizations and independent software vendor (ISV) solutions from your build environment. If the list of models in the environment differs from the list of models in the package, you receive a warning before the update is applied. For information about how to create a single package, see [Manage third-party models and runtime packages by using source control](../dev-tools/manage-runtime-packages.md).

## Apply updates to self-service environments

Self-service environments use a special approach to performing updates, because the container-based image process builds the environment's runtime. When you apply these images to a sandbox environment, you give them an **Update name** value, and they appear in the environment history. An update image consists of three parts:

- **Microsoft binaries** that Microsoft releases on a regular basis, and that include new platform and application software updates. You can get these binaries from the environment details page for your environment in Microsoft Dynamics Lifecycle Services. You see a **single tile** that shows a cumulative binary update of all the application and platform fixes. To apply this update, select the package, and then select **Save package** to save the Microsoft update to the project asset library.
- An **AOT deployable package**, which is an all-in-one package that is the sum of all the custom code that you want to apply to your environment.
- An **Update name** value that you provide in Lifecycle Services.

:::image type="content" source="media/SelfServiceUpdate.png" alt-text="Screenshot of the self-service update image conceptual model.":::

The combination of these binaries is the basis for an image that is used to create an instance of an Application Object Server (AOS). The **Update name** value lets you provide a meaningful name that indicates what the update contains.

### Update by using packages on Tier 1 sandbox/development and test/demo/build environments

To apply updates to Tier 1 sandbox/development and test/demo/build environments that you deployed through Lifecycle Services, follow the steps in [Apply updates to cloud environments](apply-deployable-package-system.md).

### Update by using packages on Tier 2 and higher Standard Acceptance Test or sandbox environments

> [!IMPORTANT]
> Applying a package causes system downtime. All relevant services stop, and you can't use your environments while the package is being applied.

At the sandbox tier, Lifecycle Services still applies updates by using the same packages that Microsoft-managed environments use before self-service. When you apply a package, it can be either a Microsoft binary or an AOT deployable package. In both cases, Microsoft takes the latest image of the environment, overwrites the binary or AOT component, and produces a new image that re-creates the runtime for the environment.

Before you begin, verify that you uploaded the deployable package to the project asset library in Lifecycle Services and that validations succeeded.

After you add the package to the project asset library, follow these steps to update your environment.

1. Open the environment details page for the environment where you want to apply the package.
1. Select **Maintain** > **Apply updates** to apply an update.
1. Enter a **unique name** for the update. Use this name to identify the update for which you want to promote the image (both the Microsoft binary and the customer AOT package) to the production environment.
1. Select the package to apply. Use the filter at the top to find your package. The list includes application and platform binary packages and application deployable packages that pass validation from the asset library.
1. Select **Apply**.

    The status in the upper-right corner of the environment details page changes from **Queued** to **Servicing** and then to **Post-servicing**. When package application completes, the status changes to **Deployed**.

1. After package application completes, the environment history updates. To view the environment history, select **History** > **Environment changes** on the environment details page.
1. You can also download the logs from the environment history page.
1. After the validations complete, you can sign off on the update from the environment history page by selecting either **Sign off** or **Sign off with issues**.

## Servicing changes

Microsoft introduced a new post-servicing step that you can use to create an index in online mode. This step helps reduce the overall servicing downtime. While the post-processing step is occurring, the Lifecycle Services dashboard shows **Post-servicing** after offline servicing is completed. During this time, the process performs some index creation and modification in online mode. Users can access the environment and perform regular activities, but performance on the package changes that are involved might be degraded. During post-servicing, users can't cancel or trigger new service requests.

:::image type="content" source="https://user-images.githubusercontent.com/90061039/164792400-d8ca418c-6a5e-468c-a965-eae597bfb737.png" alt-text="Screenshot of the Lifecycle Services dashboard showing the post-processing step in progress.":::

If a failure occurs during the post-processing step, the Lifecycle Services dashboard displays **Post-servicing failed**. Users can still access the environment and perform regular activities, but performance might be degraded. If the issue isn't resolved in 24 hours, contact Microsoft Support.

#### Uninstalling a module

AOT deployable packages consist of one or many customer modules. They might be a combination of ISV modules, partner modules, or a customer's own customization modules. To completely uninstall an AOT deployable package, use one of the following options in the sandbox environments:

- **Recommended option:** Use the `ModuleToRemove.txt` process outlined in [Uninstall a package](uninstall-deployable-package.md). This option does everything that the previous option does, but you can promote the resulting image to production environments.

- **Option not supported for production:** Create a new AOT deployable package that no longer includes the module that you want to remove. When you apply this package directly to your sandbox environment, a message in Lifecycle Services warns you that a module that is included in the current image of the environment is missing from your package.

  - You can proceed in Lifecycle Services. Microsoft creates a new image that combines the Microsoft binary from the last update and the current AOT package that doesn't contain the module that you want to remove. In effect, the module is uninstalled.
  - Use this option only in situations where you don't yet have a production environment, or where you must quickly test the resulting environment but don't plan to promote this AOT package to production.
  - Promotion of the resulting image of the sandbox environment to production environments is blocked.

#### Microsoft automatic updates in sandbox environments

On a regular basis, Microsoft pushes automatic updates of new Microsoft binaries to your sandbox environments. This automatic update happens only if your sandbox environment version falls behind and is older than the supported generally available version.

This automatic update overwrites the Microsoft binary from your latest sandbox image. In effect, it creates a new update that includes the new Microsoft binary and your earlier customizations.

### Promote an update to production environments

You no longer apply packages directly to production environments. Historically, in Microsoft-managed environments, you could apply any package that was successfully applied to a sandbox environment and marked as a *Release candidate*. However, this approach posed many challenges, because there are order of operation scenarios where application of package A before package B produced a healthy environment, but a different order led to regressing functionality.

To address these challenges, Microsoft introduced the image-based update process. As discussed earlier in this article, as you apply packages to sandbox environments, Microsoft creates images that are given an **Update name** value. This value represents the whole runtime, including Microsoft code and all custom code as a single unit. When you want to promote a change to a production environment, select an update from a sandbox environment's history. The whole runtime is then moved to the production infrastructure as is and should better safeguard against regressions.

> [!IMPORTANT]
> Applying a package causes system downtime. All relevant services stop, and you can't use your environments while the package is being applied.

After you successfully apply the update in the sandbox environment and are ready to move the update over to the production environment, follow these steps to mark an update as a release candidate.

1. Open the environment history page by selecting **History \> Environment changes** on the environment details page.
1. Select the update to move over to the production environment.
1. In the details for the update, select **Mark as release candidate**.

    The **Is Release Candidate** option is set to **Yes**.

After you mark an update as a release candidate, follow these steps to update your environment.

1. Open the environment details page for the production environment.
1. Select **Maintain \> Update environment** to apply an update.
1. In the **Available sandboxes** list, select the source sandbox environment where you applied, validated, and marked the update as a release candidate.
1. In the grid, select the update to apply to the production environment. This grid shows only updates that are marked as release candidates.
1. In the **Downtime start** field, select a date and time. The environment is taken down for servicing at the specified time on the specified date. The **Downtime end** is calculated automatically based on the expected duration.

    No lead time is required for this update.

1. Select **Schedule**. Lifecycle Services runs validations to make sure that the selected update is applicable to the environment. To prevent downgrade of the environment, the update isn't allowed if its application version is lower than the current environment version. Additionally, confirm that you want the update to proceed.

    If the update is **successfully** scheduled, an email notification is sent to all project stakeholders.

    The status in the upper-right corner of the environment details page changes from **Queued** to **Servicing**. Then, when the update is completed, the status changes to **Deployed**.

    All stakeholders are notified of the progress of the operation.

1. After the update is completed, the environment history is updated. To view the environment history, select **History \> Environment changes** on the environment details page.
1. You can also download the logs from the environment history page.
1. After the validations complete, you can sign off on the update from the environment history page by selecting either **Sign off** or **Sign off with issues**.

> [!NOTE]
> If there's an ongoing operation in the environment, or if the environment is already running on the same version or a later version, the scheduled update is canceled. When a scheduled update is canceled, an email notification is sent to all project stakeholders. You can also cancel an update by selecting **Cancel** on the environment details page. If you want to reschedule or change an update, cancel the current operation and schedule a new one.

#### Things to consider about production updates

When you promote an update from sandbox to production, it includes **both the Microsoft binary and the customer AOT package**. You can't promote the Microsoft binary and the customer AOT package independently.

If you want to promote a Microsoft binary update from your sandbox environment, be aware that it includes the latest customer packages that are applied as of that same point in time from the sandbox.

If you want to promote a customer AOT package from your sandbox environment, be aware that it also includes the most recently applied Microsoft binary update.

#### Microsoft automatic updates in production environments

On a regular basis, Microsoft pushes automatic updates of new Microsoft binaries to your production environment. This automatic update always occurs a week after successful update to your sandbox environments.

In this automatic update, Microsoft doesn't promote any customer AOT packages. Instead, Microsoft takes the newer binary version and combines it with the latest customer AOT package in the target production environment to create a new image for the production runtime.

### Rollback

For environments that you deploy in the modern infrastructure stack, the system automatically rolls back the environment if servicing isn't successful. To find out why the operation wasn't successful, you can download the logs from the environment history page.

> [!NOTE]
> For a small subset of environments, rollback might cause extended downtime. This situation can happen when the database size is large. In these cases, the system leaves the environment in a failed state to check if it can take actions to avoid rollback. If the failed operation can't move forward, the system starts the normal rollback process.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
