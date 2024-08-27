---
# required metadata

title: Sign up for Commerce trials
description: This article explains how to subscribe to the preview partner offer and deploy a Dynamics 365 Commerce environment.
author: ashishmsft
ms.date: 08/27/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: asharchw
ms.custom: 
  - bap-template
---

# Dynamics 365 Commerce trials 

With the new Dynamics 365 Commerce trial, you can automatically deploy a Commerce environment by completing a questionnaire that would provision Commerce headquarters and Commerce Scale Unit (CSU) and its related components as applicable. This article provides information about how to redeem your trial offer and initiate provisioning.

The following table outlines the details of the new trial offer.

| Offer item                   | Details                                                         |
|------------------------------|-----------------------------------------------------------------|
| Offer type                   | This offer type is Admin lead so a tenant administrator is required in order to redeem. |
| Offer use                    | One time per tenant                                             |
| Offer duration               | 30 calendar days                                                |
| Redemptions per tenant       | One                                                             |
| Extension                    | 1 extension, 30 calendars days                                  |
| Number of trial environments | Three                                                             |


## Prerequisites

The following prerequisites are required to deploy a trial of Dynamics 365 Project Operations.

- Sign-up for the [Dynamics 365 Commerce - Preview Trial](https://admin.microsoft.com/AdminPortal/home).
- The user who deploys the preview must have Azure tenant global administrator rights.

> [!IMPORTANT]
> Only one person in an organization, the tenant administrator, needs to perform this task. If you aren't the authorized user, wait until your organization has been signed up and you've received your user credentials.

### Dynamics 365 Commerce - Preview trial  - Redeem offer

Before you begin, sign in to a browser with the user work account in the tenant where you want the Dynamics 365 Commerce Trial preview.

1. Go to [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/home).
2. Go to **Marketplace \> All Products** and search for "Dynamics 365 Commerce Trial".
3. Select **Details**.
4. Select **Start Free Trial**.
5. On confirmation page, select **Try now** to continue.

> [!NOTE]
> If you're missing payment information on file, you must update your payment information before you can proceed to claim a free trial. You aren't charged without your consent. 
     
## Provisioning

1.	Go to the [Power Platform admin center](https://admin.powerplatform.com/) and 
2.	Review the recommended deployment type, and select **Begin Setup** to initiate provisioning.
3.	Review the terms and conditions and then select **Start**.
4.	After provisioning starts, you're redirected to the environment list in the Power Platform admin center. While provisioning is in progress, the state of your environment is **PreparingInstance**.
 
## Assign licenses to users

You need administrative access to your organization's Microsoft 365 Portal to complete the following steps.

1. Go to the [Microsoft 365 admin center](https://portal.office.com/) to assign the licenses to your users.
2. On the **Active users** page, select the users that you want to assign a license to.
3. Verify that the **Dynamics 365 Commerce Trial**  license has been selected, and then select **Save changes**.

## Provision a Dynamics 365 Commerce Trial (Preview) environment

To provision a Dynamics 365 Commerce Trial (Preview) environment, follow these steps

1. Go to the [Power Platform admin center] (https://admin.powerplatform.com/).
2. Navigate to Environments tab from top-left.
3. Select **New**, and then add your environment name (for example, "Contoso Trial 101") and other information as appropriate.
4. For **Type**, select **Trial (Subscription-based)**.
5. Select **Next**, and then confirm and update supporting details.
6. Select **Enable Dynamics 365 Apps**.
7. For **Automatically deploy these apps**, select **Commerce (Preview)**

> [!NOTE]
> Make sure you have assigned the Commerce trial license to the user account you're using to provision a trial environment. And, if you're not able to see “Commerce (Preview)” then give it some time, as you may have redeemed Trial offer very recently, and it takes a while for all systems to sync and update that your account has right licenses available.
 
## View environment details for Dynamics 365 Commerce Trial (preview) 

1. Go to the [Power Platform admin center](https://admin.powerplatform.com/).
2. Navigate to Environments tab from top-left.
3. Locate your environment, ‘Contoso Trial 101’ and confirm state shows “Ready”.
4. Select your environment to view details.
5. Under **Resources**, select **Dynamics 365 Apps**. You should see the **Dynamics 365 Commerce – Cloud Scale Unit** status as **Published**.
 
## View Cloud scale units for your Dynamics 365 Commerce Trial (preview) environment

1. Go to the [Dataverse Maker Apps portal](https://make.powerapps.com/).
2. In the top right corner, select your environment.
3. Select **Tables \> All**.
4. Search for "Commerce Scale Unit", and then select the result to view details. <!--(Check attached DataverseMakerApps-CommerceScaleUnit-TableView.png)-->.

> [!NOTE]
> If you're not able to view **Cloud Point of Sale Public Endpoint** and **Commerce Engine Public Endpoint** columns, select to add columns in table details.

## Frequently asked questions

### Can I extend my trial beyond 30 days?

Yes.

To extend your trial, follow these steps.

1. In the **Microsoft 365 Admin Center**, go to **Billing \> Your products**.
2. Select **Dynamics 365 Project Operations (CE) - Preview Trial**.
3. Under **Expiration Date**, select **Extend Date**.

### Can I upgrade from the Commerce trial deployment to a Commerce production/sandbox deployment?

Currently, there's no support to upgrade a trial environment.

### Can I access Commerce trial environments via Lifecycle Services (LCS)?

No. For these trials, deployment is handled through the Power Platform Admin Center. And these Commerce trial environments are expected to be used as-is in vanilla format that means you're not allowed to deploy any custom extensions. 


[!INCLUDE [footer-include](../../includes/footer-banner.md)]
