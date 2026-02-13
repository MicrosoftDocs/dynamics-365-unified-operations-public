---
title: Deploy a Commerce trial (Preview) environment
description: Learn how to subscribe to a partner offer to deploy a Microsoft Dynamics 365 Commerce trial (Preview) environment.
author: ashishmsft
ms.date: 02/13/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.custom: 
  - bap-template
---

# Deploy a Commerce trial (Preview) environment

[!include [banner](../includes/banner.md)]

This article explains how to subscribe to a partner offer to deploy a Microsoft Dynamics 365 Commerce trial (Preview) environment.

When you subscribe to a Dynamics 365 Commerce trial (Preview), you can automatically deploy a trial Commerce environment by completing a questionnaire that provisions Commerce headquarters and Commerce Scale Unit (CSU) and its related components, as applicable. 

The following table outlines the details of the new trial offer.

| Offer item                   | Details |
|------------------------------|---------|
| Offer type                   | This offer type is for administrator leads. Therefore, a tenant administrator is required to redeem it. |
| Offer use                    | One time per tenant |
| Offer duration               | 30 calendar days |
| Redemptions per tenant       | One |
| Extension                    | One extension, for 30 calendars days |
| Number of trial environments | Three |

## Prerequisites

To deploy a Dynamics 365 Commerce trial (Preview) environment, you need the following prerequisites:

- You must first sign up for the Dynamics 365 Commerce trial (Preview) offer.
- The user who deploys the Commerce trial (Preview) environment must have Azure tenant administrator rights.

> [!IMPORTANT]
> Only the tenant administrator of an organization can deploy the Commerce trial. If you're not the tenant administrator, don't proceed until your organization is signed up and you receive your user credentials.

## Sign up for the Dynamics 365 Commerce trial (Preview)

To sign up for the Dynamics 365 Commerce trial (Preview), follow these steps:

1. Sign in to a browser by using the user work account of the tenant where you want to host the Commerce trial (Preview) environment.
1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/home/).
1. Go to **Marketplace** \> **All Products**, and search for "Dynamics 365 Commerce Trial".
1. Select **Details**.
1. Select **Start Free Trial**.
1. On the confirmation page, select **Try now**.

> [!NOTE]
> If your payment information isn't on file, you must update it before you can proceed to claim the free trial. You aren't charged without your consent. 

## Assign licenses to users

> [!NOTE]
> To assign licenses to users, you need administrative access to your organization's Microsoft 365 portal.

To assign licenses to users, follow these steps:

1. Go to the [Microsoft 365 admin center](https://portal.office.com/).
1. On the **Active users** page, select the users that you want to assign a license to.
1. Confirm that the **Dynamics 365 Commerce Trial** license is selected, and then select **Save changes**.

## Provision your Commerce trial (Preview) environment

To provision your Commerce trial (Preview) environment, follow these steps:

1. Go to the [Power Platform admin center](https://admin.powerplatform.com/).
1. In the upper left, select the **Environments** tab.
1. Select **New**, and then enter the name of your environment (for example, "Contoso Trial 101") and other information, as appropriate.
1. For **Type**, select **Trial (Subscription-based)**.
1. Select **Next**, and then confirm and update the supporting details.
1. Select **Enable Dynamics 365 Apps**.
1. For **Automatically deploy these apps**, select **Commerce (Preview)**.

> [!NOTE]
> - Make sure you assign the Commerce trial license to the user account that you're using to provision the Commerce preview trial environment.
> - If **Commerce (Preview)** doesn't appear right away, try again later. The system might take a while to sync and update the fact that your account has the correct licenses available.
 
## View environment details for your Commerce trial (Preview) 

To view environment details for your Commerce trial (Preview), follow these steps:

1. Go to the [Power Platform admin center](https://admin.powerplatform.com/).
1. In the upper left, select the **Environments** tab.
1. Find your environment (for example, "Contoso Trial 101"), and confirm that the state shows as **Ready**.
1. To view environment details, select your environment.
1. Under **Resources**, select **Dynamics 365 Apps**. The status of **Dynamics 365 Commerce – Cloud Scale Unit** should show as **Published**.
 
## View Cloud Scale Units for your Commerce trial (Preview) environment

To view the Cloud Scale Units (CSUs) that are used for your Commerce trial (Preview) environment, follow these steps:

1. Go to the [Dataverse Maker Apps portal](https://make.powerapps.com/).
1. In the upper right, select your environment.
1. Select **Tables** \> **All**.
1. Search for "Commerce Scale Unit," and then select the search result to view details.

> [!NOTE]
> If the **Cloud Point of Sale Public Endpoint** and **Commerce Engine Public Endpoint** columns aren't shown, in the table details, select the missing columns to add them.

## Frequently asked questions

### Can I extend my trial beyond 30 days?

Yes. To extend your trial, follow these steps:

1. Sign in to the [Microsoft 365 admin center](https://admin.cloud.microsoft/).
1. Go to **Billing** \> **Your products**.
1. Select **Dynamics 365 Commerce trial (Preview)**.
1. Under **Expiration Date**, select **Extend Date**.

### Can I upgrade from the Commerce trial (Preview) deployment to a Commerce production/sandbox deployment?

Currently, there's no support for upgrading a trial environment.

### Can I access the Commerce trial (Preview) environment through Microsoft Dynamics Lifecycle Services?

No. You deploy this trial through the Power Platform admin center.

### Can I deploy custom extensions to the Commerce trial (Preview) environment?

No. Use Commerce trial (Preview) environments as is. You can't deploy custom extensions.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
