---
# required metadata

title: Sign up for Commerce trials
description: This article explains how to subscribe to the preview partner offer and deploy a Dynamics 365 Commerce environment.
author: ashishmsft
ms.date: 07/12/2024
ms.topic: how-to
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: asharchw
ms.custom: 
  - bap-template
---

# Dynamics 365 Commerce trials 

With the new Dynamics 365 Commerce trial, you can automatically deploy a Commerce environment by completing a questionnaire that would provision backoffice (F&O), along with Commerce scale unit and its related components as applicable. This article provides information about how to:

*   Redeem your trial offer.
*   Initiate provisioning.
*   Learn more about Dynamics 365 CO.

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
> Only one person in an organization, the tenant administrator, needs to perform this task. If you aren't the subscriber to this release, wait until your organization has been signed up and you've received your user credentials.

### Dynamics 365 Commerce - Preview trial 

Before you begin, sign in to a browser with the user work account in the tenant where you want the Dynamics 365 Commerce Trial preview.

1. Redeem the first offer code, **Dynamics 365 Commerce - Preview Trial** by pasting it into the browser URL.

    ![Redeem Offer](./media/16RedeemFirstOfferNew.png)

2. Confirm your order.

    ![Confirm the order](./media/17ConfirmOrderNew.png)

  You will see that the confirmation offer was successfully redeemed.

   ![Confirmation](./media/18OrderConfirmationNew.png)

  You will be redirected to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/projectoperationstrial).

## Questionnaire and provisioning

1.	Go to the [Power Platform admin center](https://admin.powerplatform.com/projectoperationstrial) and complete the questionnaire.  
2.	Review the recommended deployment type, and select **Begin Setup** to initiate provisioning.
3.	Review the terms and conditions and then select **Start**.

   After provisioning starts, you are redirected to the environment list in the Power Platform admin center. While provisioning is in progress, the state of your environment is **PreparingInstance**.
 
  When provisioning is complete, the state of your environment is **Ready**. Provisioning the environment includes deploying demo data.
 
4.	Select the respective Microsoft Dataverse URL and the finance and operations apps URLs to validate the deployment.


## Assign licenses

You will need administrative access to your organization's Microsoft 365 Portal to complete the following steps.

1. Go to the [Microsoft 365 admin center](https://portal.office.com/) to assign the licenses to your users.

   ![Admin center home page](./media/14AdminPortal.png)

2. On the **Active users** page, select the users that you want to assign a license to.

   ![Assign Licenses](./media/15AssignLicenses.png)

3. Verify that the **Dynamics 365 Project Operations Preview**  license has been selected, and then select **Save changes**.

## Additional resources

The following resources provide helpful guidance as you begin your journey with Project Operations:

- [Video Series -Project Operations Overview, feature deep dives and roadmap](https://youtube.com/playlist?list=PLcakwueIHoT_LJ3Fr1tHnkPk5lioqE6uH)
- [Dynamics 365 Project Operations](/training/modules/examine-dynamics-365-project-operations/)


## Frequently asked questions

### What if I require ALM or ELM for my finance and operations apps environment?

- For partners who require full environment lifecycle management capabilities, see the [Partner Sandbox License Request](https://experience.dynamics.com/requestlicense) to review the new partner offer. 
- For partners seeking more information about Internal Use Rights, see [Internal Use Rights cloud and software benefit (microsoft.com](https://partner.microsoft.com/membership/internal-use-software).

### Can I extend my trial beyond 30 days?
To extend your trial, complete the following steps.

1. In the **Microsoft 365 Admin Center**, go to **Billing** > **Your products**.
2. Select **Dynamics 365 Project Operations (CE) - Preview Trial**.
3. Under **Expiration Date**, select **Extend Date**.

### Can I upgrade from the lite deployment to the resource/non-stocked based scenario deployment?
Currently, there is no support to upgrade an environment from a lite to a non-stocked based deployment.

### Can I access Lifecycle Services (LCS) for my Finance environments?  
No. For these trials, deployment is handled through the Power Platform Admin Center. Access to the Finance environment is restricted.

### Can I install my trial on an existing environment?
If you have an existing environment, you will be allowed to install the lite deployment on an existing sales Dataverse environment from the Power Platform Admin center.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
### In this article
