---
# required metadata

title: Update an environment
description: This topic explains how to update an environment that was deployed using the self-service deployment experience.
author: manado
manager: AnnBe
ms.date: 06/07/2019
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
ms.author: manado
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Update an environment

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This topic walks through the process of applying updates to a Dynamics 365 for Finance and Operations environment that was deployed using the [self-service deployment](infrastructure-stack.md) experience.

> [!IMPORTANT]
> With the next generation infrastructure, updates are applied differently from the current flow. **Whatever is supplied in the package is applied to the environment and it OVERWRITES what is already present in the environment**. This means that you **must** create a single deployable package that contains all customizations and ISV solutions from your build environment. If there is a difference in the list of models between what is on the environment and what is in the package, you will be warned before applying the update. For details about creating a single package, see [Manage third-party models and runtime packages by using source control](../dev-tools/manage-runtime-packages.md).

## Supported package types
Because environments deployed using the [self-service deployment](infrastructure-stack.md) experience will be on 8.1 and later, we support the following package types:

- **AOT deployable package** - A deployable package that is generated from application metadata and source code. This deployable package is created in a **build** environment.
- **Binary update package** - A deployable package that contains dynamic-link libraries (DLLs) and other binaries and metadata that the platform and application depend on. This is a package released by Microsoft.

## Development Application Lifecycle Management (ALM) flow
To apply code customizations to your sandbox and production environments, you need to create a deployable code package from your build environment. For details on how to do this, see [Create deployable packages of models](create-apply-deployable-package.md).

## Microsoft updates
To get access to Microsoft updates, go to the environment details page for your environment. You will see a **single tile** that shows a cumulative, binary update of all the application and platform fixes. To apply this update, select the package and select **Save Package** to save the Microsoft update to the project asset library.

## Apply updates

### Tier 1 Sandbox/Develop and Test/Demo/Build environments

To apply updates to a Tier 1 Sandbox/Develop and Test/Demo/Build environment deployed through Lifecycle Services (LCS), follow the steps in  [Apply updates to cloud environments](apply-deployable-package-system.md).

### Tier 2 and above Standard Acceptance Test/Sandbox environments

> [!IMPORTANT]
> Applying packages causes system downtime. All relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

Before you begin, verify that the deployable package has been uploaded to the project asset library in LCS and that validations have succeeded.

After you have this package in the project asset library, use the following steps to update your environment:

1. Open the **Environment details** view for the environment where you want to apply the package.
2. Click **Maintain > Apply updates** to apply an update.
3. Enter a **unique name** for the update. This will be used to identify which update you want to move to production. 
3. Select the package to apply. Use the filter at the top to find your package. You will see application and platform binary packages and application deployable packages that have passed validation from the asset library in the list.
4. Click **Apply**.
5. The status in the upper-right corner of the **Environment details** view changes from **Queued** to **Servicing**, and then after completion it changes to **Deployed**.
6. On completion, the environment history accessible from **History > Environment changes** on the **Environment details** page is updated to show the completed package deployed.
7. You can also download the logs from the environment history page. 
8. On completing the validations, you can sign-off on the update from the environment history page by clicking on **Sign off** or **Sign off with issues**. 


### Production environment
To improve the reliability of updates being applied to a production environment, a specific update done in the sandbox, designated as a **Release candidate** can be moved to production. The update contains both the base product and the customization and so both will be moved over when the selected update is applied to production. This is different than how servicing is done tody where you can move over only the customization and the base product **will not** change. In the case self-service deployment environment, the base product version **could change** depending on the update in sandbox that is marked as a release candidate. 

> [!IMPORTANT]
> Applying packages causes system downtime. All relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

After you have successfully applied the update in the sandbox environment and are ready to move the update to production, use the following steps to mark an update as a release candidate:

1. Navigate to the **History > Environment changes** page. 
2. Select the update you want to promote to production. 
3. On the details of the update, click the **Mark as release candidate** button.
4. This will set the **Is Release Candidate** field to Yes. 

Once you have marked an update as a release candidate, use the following steps to update your environment:

1. Open the **Environment details** view for the production environment.
2. Click **Maintain > Update environment** to apply an update.
3. Select the source sandbox environment from the list of **Available sandboxes** where the update was applied, validated and marked as a release candidate.
4. Select an update from the grid. This grid only shows updates that have been marked as a release candidate. Select the specific update you want to apply to production.
5. Select a date and time in the **Downtime start** field. Starting at this date and time, the environment will be taken down for servicing. The **Downtime end** is set to 3 hours from the start of the downtime. 
6. There is no lead time necessary for this update. 
7. Click **Schedule**. Lifecycle Services will run validations to ensure that the selected update is applicable to the environment. If the selected upate has a lower application version than the current environment version, the update result in downgrade of the environment and hence it will not be allowed. In addition, customers will be asked to confirm that they want to proceed with the update. 
8. If the update is **successfully** scheduled, an email notifying that an update is scheduled is sent to all the project stakeholders. 
9. The status in the upper-right corner of the **Environment details** view changes from **Queued** to **Servicing**, and then after completion it changes to **Deployed**.
10. All stakeholders will be notified of the progress of the operation. 
11. On completion, the environment history accessible from **History > Environment** changes on the **Environment details** page is updated to show the completed package deployed.
12. You can also download the logs from the environment history page.
13. On completing the validations, you can sign-off on the update from the environment history page by clicking on **Sign off** or **Sign off with issues**.

> [!NOTE]
> If there is an on-going operation on the environment or if the environment is already on the same or higher version, the scheduled update will be cancelled. An email notification will be sent to all project stakeholders when a scheduled update is cancelled. If the customer wants to cancel the upddate, they will be able to do so by clicking on the **Cancel** button on the environment details page. If the customer wants to re-schedule or change the update, they can cancel the current operation and schedule a new one.

> [!IMPORTANT]
> For environments deployed in the modern infrastructure stack, if servicing fails, the environment is automatically rolled back. To understand why the operation failed, you can download the logs from the environment history page as mentioned in the steps above.
