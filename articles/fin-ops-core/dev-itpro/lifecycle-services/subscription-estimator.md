---
title: Subscription estimator in Lifecycle Services
description: Learn about how to use the Subscription estimator tool that's available in Lifecycle Services, including answers to frequently asked questions.
author: angelmarshall
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: Platform update 12
ms.custom:
  - sfi-image-nochange
---

# Subscription estimator in Lifecycle Services

[!include [banner](../includes/banner.md)]

Subscription estimator is a tool that's available in Microsoft Dynamics Lifecycle Services. Microsoft uses this tool to estimate the initial size of the production environment that it must provision for a customer. Before customers can request deployment of a production environment, they must estimate their peak workloads in terms of transaction counts and then upload that information to Lifecycle Services. By using the details of user licenses and transaction counts to infer subscription requirements, the Subscription estimator tool helps ensure that the provisioned environment meets the customer's business requirements.

Follow these steps to use the Subscription estimator tool.

1. In Lifecycle Services, open the project that is associated with the implementation project.
1. At the top of the page, select the hamburger icon, and then select **Subscription estimator**.

    :::image type="content" source="./media/subscription_estimator_01.png" alt-text="Screenshot of the subscription estimator option.":::

1. Download the sample usage profile.
1. Answer the required questions on each tab. If you're a Commerce customer, be sure to answer the questions on the **Retail and Commerce** tab.
1. Save the usage profile locally.
1. To upload the usage profile, select **New estimate**, name the estimate, and then upload the usage profile.
1. After the upload is completed, select **Mark as Active** to activate an estimate. You need an active estimate to configure a production deployment.

When there's a valid active estimate, the **Configure** button becomes available. You can use this button to request a production environment deployment.

## Edit the estimate for multiple implementation projects

To edit the estimate for multiple implementation projects, follow these steps:

1. Open the Subscription estimator tool for each implementation project.
1. Edit the active subscription estimate to apply the license allocation for each project. To edit a subscription estimate in the Subscription estimator tool, select it, and then select **Edit estimate**.

    :::image type="content" source="./media/SubscriptionEstimatorWithEdit.jpg" alt-text="Screenshot of active subscription estimate in the Subscription estimator tool.":::

1. In the **Edit estimate** dialog box, enter the license count for each type of finance and operations license. By default, when you create a subscription estimate, you assign the full count of all purchased licenses to it. You can't allocate more than the total number of licenses to a single estimate. Additionally, you can't reduce the allocated number so that it's less than the minimum number that the Dynamics 365 Licensing policy requires.

    :::image type="content" source="./media/SubscriptionEstimatorEditDialog.jpg" alt-text="Screenshot of the Edit estimate dialog box in the Subscription estimator tool.":::

1. Select **Save**.
1. A message box warns you that updates to an active estimate might cause the size of your production environment to change. Select **Yes** to confirm that you want to continue with the update.

    :::image type="content" source="./media/SubscriptionEstimatorEditDialogWarning.jpg" alt-text="Screenshot of the warning message about updates to an active estimate in the Subscription estimator tool.":::

> [!NOTE]
> Although you can have multiple estimates, you must mark one estimate as **Active**. After you deploy the production environment, or after deployment of the environment receives sign out, the active estimate is locked. If you make any other changes to the active estimate or mark a new estimate as **Active**, you might cause the production environment to be resized.

## Frequently asked questions

### Why isn't the Configure button available for deploying a production environment, even though there's an active estimate? Why does a warning message appear in the Action Center on the project dashboard?

If you have multiple implementation projects, the **Configure** button might not be available. A warning message in the Action center might indicate that the number of licenses is insufficient. The **Edit estimate** button in the Subscription estimator tool lets you edit an active subscription estimate and apply the desired license allocation for that project.

### Why does an error occur when I mark an estimate as Active?

When you mark an estimate as **Active**, you might receive the following error message:

*Estimate created but doesn't meet requirements*

This error occurs if transaction lines that you enter aren't within the limits of the Subscription estimation tool. To resolve this error, create a support request, and attach the usage profile. Your instance can then be manually sized.

### How can I update my subscription if my production environment is deployed?

The [Subscription estimator](subscription-estimator.md) is a required step before you request production. Although you can have multiple estimates, one estimate must be marked as **Active**. You use the active subscription estimate to size the production environment. After you deploy the production environment, or after deployment sign out, the active estimate is locked. To edit an active subscription estimate, select the **Edit estimate** button in the Subscription estimator tool to update your license allocation.

### What should I do to activate my subscription estimate if I have multiple projects in the same tenant?

When you're implementing several projects in the same tenant, a warning message in the Action center in Lifecycle Services might state, "subscription estimate isn't complete." This warning indicates that the total number of estimated users for all implementation projects shouldn't exceed the number of purchased licenses. This situation can occur if the total users in the active subscription estimates exceed the tenant license count of the same type. To edit the active subscription estimate, select the **Edit estimate** button in the Subscription estimator tool to update your license allocation.

> [!NOTE]
> FastTrack solutions architects aren't involved in uploading or updating the Subscription estimator. If you identify any warnings about the Subscription estimator in Lifecycle Services, follow the instructions in this article. If you continue to have issues, contact Microsoft Support.

If you receive any other error message or encounter other issues, create a support request, and attach your active estimate so that the Support team can address the issue.

## Additional resources

[Subscriptions, Lifecycle Services projects, and Microsoft Entra tenants FAQ](../../fin-ops/get-started/subscription-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]