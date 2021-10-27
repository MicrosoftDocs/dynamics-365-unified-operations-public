---
# required metadata

title: Update an environment
description: This topic explains how to update an environment that was deployed by using the self-service deployment experience.
author: laneswenka
ms.date: 10/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
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


## Applying updates to self-service environments

Self-service environments use a special approach to how updates are performed.  This is because of the usage of the container-based, image process to build the environment’s runtime.  These images are given an **Update name** by the customer when they are applied to a sandbox environment, and are shown in the environment history of the environment.  An update image is comprised of three parts:

1.	**Microsoft binaries**.  These are released by Microsoft on a regular basis and include new platform and application software updates.  These are available from the environment details page for your environment in Microsoft Dynamics Lifecycle Services (LCS). You will see a **single tile** that shows a cumulative binary update of all the application and platform fixes. To apply this update, select the package, and then select **Save package** to save the Microsoft update to the project asset library.
2.	**AOT deployable package**.  These are an all-in-one package that is the sum of all of the custom code that the customer wishes to apply to their environment.
3.	An **Update name** provided by the customer in Lifecycle Services.
 
<img src="media/SelfServiceUpdate.png" width=600px alt="Self-service update image conceptual model" />
 
The combination of these binaries is the basis for an image of which is used to create an instance of an Application Object Server (AOS).  By giving this image an **Update name** customers can provide a meaningful name for what the update contains.

### Update using packages on Tier 1 sandbox/development and test/demo/build environments

To apply updates to a Tier 1 sandbox/development and test/demo/build environments that were deployed through LCS, follow the steps in [Apply updates to cloud environments](apply-deployable-package-system.md).

### Update using packages on Tier 2 and above Standard Acceptance Test/sandbox environments

> [!IMPORTANT]
> Package application causes system downtime. All relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

At the sandbox tier, updates are still applied via Lifecycle Services using the same packages as they were with the Microsoft-managed environments prior to self-service.  
When a customer applies a package, it can be either a Microsoft binary or an AOT deployable package.  In either case, we will take the latest image of the environment, overwrite the binary or AOT component, and result in a new image that is used to re-create the runtime for the environment.

Before you begin, verify that the deployable package has been uploaded to the project asset library in LCS, and that validations have succeeded.

After the package is in the project asset library, follow these steps to update your environment.

1. Open the environment details page for the environment where you want to apply the package.
2. Select **Maintain \> Apply updates** to apply an update.
3. Enter a **unique name** for the update. You will use this name to identify the update that you want to promote the image (both Microsoft binary and the customer AOT package) to the production environment.
4. Select the package to apply. Use the filter at the top to find your package. The list will include application and platform binary packages and application deployable packages that have passed validation from the asset library.
5. Select **Apply**.

    The status in the upper-right corner of the environment details page changes from **Queued** to **Servicing**. Then, when package application is completed, the status changes to **Deployed**.

6. After package application is completed, the environment history is updated. To view the environment history, select **History \> Environment changes** on the environment details page.
7. You can also download the logs from the environment history page.
8. After the validations are completed, you can sign-off on the update from the environment history page by selecting either **Sign off** or **Sign off with issues**.

#### Uninstalling a module
AOT deployable packages are comprised of one or many customer modules.  This could be a combination of ISV modules, partner modules, or a customer’s own customization modules.  If you want to uninstall one completely, there are two paths in the sandbox environments:

- Create a new AOT deployable package that no longer includes the module you wish to remove.  Applying this package directly to your sandbox environment will result in a warning in LCS letting you know that a module is missing in your package, compared to the current image of the environment.
  -	You can proceed in LCS and we will create a new image combining the Microsoft binary from the last update, as well as the current AOT package that doesn’t contain the module you wish to remove.  This will in-effect uninstall the module.
  -	This is only advised in situations where you don’t have a production environment yet, or you quickly need to test the resulting environment, but don’t plan to promote this AOT package to production.
  -	Promoting this resulting image of the sandbox environment to production environments will be blocked.
-	Use the ModuleToRemove.txt process as outlined in [Uninstall a package](uninstall-deployable-package.md). This will do everything the same as the prior option, but will result in an image that is promotable to production environments.  *This is the recommended option*.

#### Microsoft automatic updates in sandboxe environments
On a regular basis, Microsoft will push automatic updates of new Microsoft binaries to your sandbox environments.  This will only be done in the case where your sandbox environment version has fallen behind and is older than the supported generally available version.

This will overwrite the Microsoft binary from your latest sandbox image and will, in-effect, create a new update with the new Microsoft binary plus your prior customizations.  

### Promote an update to production environments
Packages are no longer directly applied to production environments.  Historically, in Microsoft-managed environments, customers were able to apply any package that was successfully applied to a sandbox environment and marked as a *Release candidate*. 

This posed many challenges, however, as there are order of operation scenarios where applying *Package A* before *Package B* resulted in a healthy environment, but applying in a different order resulted in regressing functionality.

To solve this, Microsoft has introduced the image-based, update process.  As discussed earlier in this topic, as packages are applied to sandbox environments, we are creating images that are given an **Update name**.  This represents the entire runtime, including Microsoft code and all custom code as a single unit.  When customers want to promote a change to a production environment, they will select an update from a sandbox’s environment history.  This will move the entire runtime to the production infrastructure as-is and should better safeguard against regressions.

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
5. In the **Downtime start** field, select a date and time. The environment will be taken down for servicing at the specified time on the specified date. The **Downtime end** is calculated automatically based on the expected duration.

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

#### Things to consider on production updates
When you are promoting an update from sandbox to production, it includes **both the Microsoft binary and the customer AOT package** from that update.  It is not possible for customers to promote them independently. 

If you are seeking to promote a Microsoft binary update from your sandbox environment, be mindful that it will include the latest customer packages applied as of that same point in time from the sandbox.

If you are seeking to promote a customer AOT package from your sandbox environment, be mindful that it will include the most recently applied Microsoft binary update, as well.

#### Microsoft automatic updates in production environments
On a regular basis, Microsoft will push automatic updates of new Microsoft binaries to your production environment.  This will always happen a week after successful update to your sandbox environments.  

In this event, Microsoft will not promote any customer AOT packages with this update.  Instead, Microsoft will take the newer binary version and combine that with the latest customer AOT package in the target production environment, thereby creating a new image for the production runtime.

### Rollback
For environments that are deployed in the modern infrastructure stack, if servicing is unsuccessful, the environment is automatically rolled back in most cases. To learn why the operation was unsuccessful, you can download the logs from the environment history page.

> [!NOTE]
> For a small subset of environments where rollback may result in extended downtime, such as when the database size is large, the environment is left in a failed state to determine if actions can be taken to avoid performing the rollback. If the failed operation cannot move forward, then the normal rollback process is initiated.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
