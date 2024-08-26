---
# required metadata

title: Sign up for Commerce trials
description: This article explains how to subscribe to the preview partner offer and deploy a Dynamics 365 Commerce environment.
author: ashishmsft
ms.date: 08/26/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: asharchw
ms.custom: 
  - bap-template
---

# Dynamics 365 Commerce trials 

With the new Dynamics 365 Commerce trial, you can automatically deploy a Commerce environment by completing a questionnaire that would provision backoffice (F&O), along with Commerce scale unit (CSU) and its related components as applicable. This article provides information about how to:

*   Redeem your trial offer.
*   Initiate provisioning.

The following table outlines the details of the new trial offer.

| Offer item                   | Details                                                         |
|------------------------------|-----------------------------------------------------------------|
| Offer type                   | This offer type is Admin lead so a tenant admin is required in order to redeem. |
| Offer use                    | One time per tenant                                             |
| Offer duration               | 30 calendar days                                                |
| Redemptions per tenant       | 1                                                               |
| Extension                    | 1 extension, 30 calendars days                                  |
| Number of trial environments | 3                                                               |


## Prerequisites
The following prerequisites are required to deploy a trial of Dynamics 365 Project Operations.

- Sign-up for the [Dynamics 365 Commerce - Preview Trial](https://admin.microsoft.com/AdminPortal/home).
- The user who deploys the preview must have Azure tenant global administrator rights.

> [!IMPORTANT]
> Only one person in an organization, the tenant administrator, needs to perform this task. If you aren't the authorized user, wait until your organization has been signed up and you've received your user credentials.

### Dynamics 365 Commerce - Preview trial  - Redeem Offer

Before you begin, sign in to a browser with the user work account in the tenant where you want the Dynamics 365 Commerce Trial preview.

1. Go to [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/home)
2. Next, go to Marketplace > All Products, search for "Dynamics 365 Commerce Trial"
3. Click on "Details", this should load details about "Dynamics 365 Commerce Trial" and click "Start Free Trial" and then on confirmation page click "Try now" and continue.

> [!Note]
> If you maybe missing payment information on file, then you are required to update payment information before you can proceed to claim free trial. You shall not be charged without your consent. 
     
   
## Provisioning

1.	Go to the [Power Platform admin center](https://admin.powerplatform.com/) and 
2.	Review the recommended deployment type, and select **Begin Setup** to initiate provisioning.
3.	Review the terms and conditions and then select **Start**.
4.	After provisioning starts, you are redirected to the environment list in the Power Platform admin center. While provisioning is in progress, the state of your environment is **PreparingInstance**.
 
## Assign licenses to users

You will need administrative access to your organization's Microsoft 365 Portal to complete the following steps.

1. Go to the [Microsoft 365 admin center](https://portal.office.com/) to assign the licenses to your users.
2. On the **Active users** page, select the users that you want to assign a license to.
3. Verify that the **Dynamics 365 Commerce Trial**  license has been selected, and then select **Save changes**.


## Provisioning

Provision a Dynamics 365 Commerce Trial (Preview) environment

1. Go to the [Power Platform admin center] (https://admin.powerplatform.com/)
2. Navigate to Environments tab from top-left
3. Click on New, add env name e.g., ‘Contoso Trial 101’ , and other information as appropriate. Choose Type as “Trial (Subscription-based)”
4. Click on Next, confirm and update supporting details.
5. Make sure to select “Enable Dynamics 365 Apps”
6. And, then for “Automatically deploy these apps” choose “Commerce (Preview)”

> [!Note]
> Make sure you have assigned the Commerce trial license to the user account you are using to provision a trial environment. And, if you are not able to see “Commerce (Preview)” then give it some time, as you may have redeemed Trial offer very recently, and it takes a while for all systems to sync and update that your account has right licenses available.
 

## View environment details for Dynamics 365 Commerce Trial (preview) 

1. Go to the [Power Platform admin center](https://admin.powerplatform.com/)
2. Navigate to Environments tab from top-left
3. Locate your environment, ‘Contoso Trial 101’ and confirm state shows “Ready”
4. Click to view environment details
5. Click on “Dynamics 365 Apps” under resources - you should see “Dynamics 365 Commerce – Cloud Scale Unit” status as “Published”.
 

## View Cloud scale units for your Dynamics 365 Commerce Trial (preview) environment

1. Go to Dataverse Maker Apps portal (https://make.powerapps.com/)
2. Select your Environment from top-right corner
3. Select Tables > All
4. Search “Commerce Scale Unit” and click on it to view details (Check attached DataverseMakerApps-CommerceScaleUnit-TableView.png)

> [!Note]
> If you are not able to view columns for ‘Cloud Point of Sale Public Endpoint’ and ‘Commerce Engine Public Endpoint’ then simply click to add columns in table details.


## Frequently asked questions

### Can I extend my trial beyond 30 days?
To extend your trial, complete the following steps.

1. In the **Microsoft 365 Admin Center**, go to **Billing** > **Your products**.
2. Select **Dynamics 365 Project Operations (CE) - Preview Trial**.
3. Under **Expiration Date**, select **Extend Date**.

### Can I upgrade from the Commerce trial deployment to the a Commerce Production/Sandbox deployment?
Currently, there is no support to upgrade a trial environment.

### Can I access Commerce trial environments via Lifecycle Services (LCS)?  
No. For these trials, deployment is handled through the Power Platform Admin Center. And these Commerce trial environments are expected to be used as-is in vanilla format that means you are not allowed to deploy any custom extensions. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
