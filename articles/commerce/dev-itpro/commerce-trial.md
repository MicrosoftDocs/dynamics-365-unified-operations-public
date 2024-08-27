---
title: Subscribe to and deploy a Commerce preview trial environment
description: This article explains how to subscribe to a partner offer to deploy a Microsoft Dynamics 365 Commerce preview trial environment.
author: ashishmsft
ms.date: 08/27/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.custom: 
  - bap-template
---

# Subscribe to and deploy a Commerce preview trial environment

[!include [banner](../includes/banner.md)]

This article explains how to subscribe to a partner offer to deploy a Microsoft Dynamics 365 Commerce preview trial environment.

By subscribing to a Dynamics 365 Commerce trial, you can automatically deploy a trial Commerce environment by completing a questionnaire that provisions Commerce headquarters and Commerce Scale Unit (CSU) and its related components as applicable. 

The following table outlines the details of the new trial offer.

| Offer item                   | Details                                                         |
|------------------------------|-----------------------------------------------------------------|
| Offer type                   | This offer type is for administrator leads, so a tenant administrator is required in order to redeem it. |
| Offer use                    | One time per tenant                                             |
| Offer duration               | 30 calendar days                                                |
| Redemptions per tenant       | One                                                             |
| Extension                    | One extension, 30 calendars days                                  |
| Number of trial environments | Three                                                             |

## Prerequisites

The following prerequisites are required to deploy a trial of Dynamics 365 Project Operations.

- You must sign up for the [Dynamics 365 Commerce - Preview Trial](https://admin.microsoft.com/AdminPortal/home).
- The user who deploys the Commerce trial must have Azure tenant administrator rights.

> [!IMPORTANT]
> Only the tenant administrator of an organization can deploy the Commerce trial. If you aren't the tenant administrator, wait until your organization has been signed up and you've received your user credentials to proceed.

### Sign up for the Dynamics 365 Commerce preview trial

To sign up for the Dynamics 365 Commerce preview trial, follow these steps.

1. Sign in to a browser with the user work account of the tenant where you want the Dynamics 365 Commerce Trial preview.
1. Go to [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/home).
2. Go to **Marketplace \> All Products** and search for "Dynamics 365 Commerce Trial".
3. Select **Details**.
4. Select **Start Free Trial**.
5. On confirmation page, select **Try now**.

> [!NOTE]
> If your payment information isn't on file, you must update your payment information before you can proceed to claim the free trial. You aren't charged without your consent. 
     
## Provision a Dynamics 365 Commerce trial preview environment

To provision a Dynamics 365 Commerce Trial preview environment, follow these steps.

1.	Go to the [Power Platform admin center](https://admin.powerplatform.com/).
2.	Review the recommended deployment type, and select **Begin Setup** to initiate provisioning.
3.	Review the terms and conditions, and then select **Start**.
4.	After provisioning starts, you're redirected to the environment list in the Power Platform Admin Center (PPAC). While provisioning is in progress, the state of your environment is **PreparingInstance**.
 
### Assign licenses to users

> [!NOTE]
> You need administrative access to your organization's Microsoft 365 Portal to assign licenses to users.

To assign licenses to users, follow these steps.

1. Go to the [Microsoft 365 admin center](https://portal.office.com/).
2. On the **Active users** page, select the users to whom you want to assign a license.
3. Confirm that the **Dynamics 365 Commerce Trial** license has been selected, and then select **Save changes**.

### Continue provisioning the Dynamics 365 Commerce trial preview environment

To continue provisioning a Dynamics 365 Commerce trial preview environment, follow these steps.

1. Go to the [Power Platform admin center] (https://admin.powerplatform.com/).
2. At the top left, select the **Environments** tab.
3. Select **New**, and then enter your environment name (for example, "Contoso Trial 101") and other information as appropriate.
4. For **Type**, select **Trial (Subscription-based)**.
5. Select **Next**, and then confirm and update the supporting details.
6. Select **Enable Dynamics 365 Apps**.
7. For **Automatically deploy these apps**, select **Commerce (Preview)**

> [!NOTE]
> - Ensure that you have assigned the Commerce trial license to the user account you're using to provision a trial environment.
> - If you're not able to see **Commerce (Preview)**, try again later. It may take a while for all systems to sync and update that your account has the right licenses available.
 
## View environment details for Dynamics 365 Commerce trial (preview) 

To view environment details for Dynamics 365 Commerce trial preview, follow these steps.

1. Go to the [Power Platform admin center](https://admin.powerplatform.com/).
2. At the top left, select the **Environments** tab.
3. Locate your environment (for example, "Contoso Trial 101") and confirm that the status shows as **Ready**.
4. Select your environment to view details.
5. Under **Resources**, select **Dynamics 365 Apps**. You should see the **Dynamics 365 Commerce – Cloud Scale Unit** status as **Published**.
 
## View Cloud Scale Units for your Dynamics 365 Commerce Trial preview environment

To view Cloud Scale Units (CSUs) for your Dynamics 365 Commerce trial preview environment, follow these steps.

1. Go to the [Dataverse Maker Apps portal](https://make.powerapps.com/).
2. At the top right, select your environment.
3. Select **Tables \> All**.
4. Search for "Commerce Scale Unit", and then select the search result to view details.

> [!NOTE]
> If you're not able to view **Cloud Point of Sale Public Endpoint** and **Commerce Engine Public Endpoint** columns, select to add columns in table details.

## Frequently asked questions

### Can I extend my trial beyond 30 days?

Yes. To extend your trial, follow these steps.

1. Sign in to the [Microsoft 365 Admin Center](https://admin.cloud.microsoft).
2. Go to **Billing \> Your products**.
3. Select **Dynamics 365 Project Operations (CE) - Preview Trial**.
4. Under **Expiration Date**, select **Extend Date**.

### Can I upgrade from the Commerce trial deployment to a Commerce production/sandbox deployment?

Currently there's no support to upgrade a trial environment.

### Can I access the Commerce trial environment via Microsoft Lifecycle Services?

No. For this trial, deployment is handled through the Power Platform Admin Center. Also, Commerce trial environments are expected to be used as-is. You're not allowed to deploy any custom extensions. 

### Can I deploy custom extensions to the Commerce trial environment?

No. Commerce trial environments are expected to be used as-is, so you're not allowed to deploy any custom extensions.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
