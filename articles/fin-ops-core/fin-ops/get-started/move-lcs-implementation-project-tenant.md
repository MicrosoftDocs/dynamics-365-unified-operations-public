---
# required metadata

title: Move LCS implementation projects to different Azure AD tenants
description: This topic explains how to move your subscriptions and LCS Implementation project to a different Azure AD tenant.
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 04/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Move LCS implementation projects to different Azure AD tenants

[!include [banner](../includes/banner.md)]

You can move your subscriptions and your Microsoft Dynamics Lifecyle Services (LCS) Implementation project to a different Microsoft Azure Active Directory (Azure AD) tenant. Here are some scenarios where this move might be required:

- Subscriptions were accidentally purchased against the incorrect Azure AD tenant.

    > [!NOTE]
    > If you're a cloud service provider, and you sell subscriptions for Finance and Operations apps to an existing customer, you must request a reseller relationship with that customer to put the subscriptions on the customer's existing Azure AD tenant. If you create a new customer record for the customer in Microsoft Partner Center, you create a new Azure AD tenant for the customer.

- The customer changes the structure of the Azure AD tenant after the subscription is purchased.

The process for moving your subscriptions and all related artifacts has four main steps, as shown in the following illustration.

![Process for moving subscriptions](./media/move-subscription-process.png)

## Activate subscriptions on the new tenant

Work with your cloud service provider or volume license reseller to activate the subscriptions against the new Azure AD tenant. All subscriptions for users, and for add-on environments, must be activated.

### Cloud service provider

If you're licensed through a Microsoft Cloud Solution Provider (CSP) agreement, purchase the required subscriptions against the new tenant from your cloud service provider. If the new tenant already exists, the cloud service provider must request a reseller relationship. Alternatively, in Partner Center, the cloud service provider must create a new customer that has the desired default domain name, **\*.onmicrosoft.com** (for example, **contoso.onmicrosoft.com**).

Ask the cloud service provider not to suspend the existing subscriptions at this time.

### Volume Licensing

If you're licensed through a Microsoft Volume Licensing agreement, you must call the [Volume Licensing support center](https://www.microsoft.com/Licensing/servicecenter/Help/Contact.aspx) and ask that the subscriptions be remapped from the old tenant to the new tenant. You can contact Volume Licensing Support through Microsoft 365 Admin center. Request a grace period, when the subscriptions will be active on both tenants. Because of customer privacy concerns, this request must be made by the customer. You should have the following information available:

- Public customer number
- Enrollment number
- The current tenant domain that the subscriptions are currently provisioned on
- The destination tenant domain that the customer wants the subscriptions provisioned under
- A detailed explanation of why the customer must have its Volume Licensing subscriptions migrated to a different tenant
- The total number of paid subscriptions that must be moved to the new tenant, together with the subscription type and seat count

> [!IMPORTANT]
> It's crucial that the subscriptions be active on both tenants in parallel for a few weeks, until you've finished decommissioning LCS on the old tenant.

## Configure LCS on the new tenant

On the new tenant, you will get a new LCS project that you must initiate and set up.

1. Fully configure LCS. As part of this configuration, you must add users, a Microsoft Azure DevOps association, subscription estimates, the Asset library, Business process modeler (BPM), and so on.
2. Deploy all non-production environments in the new LCS project.
3. Apply the required code packages to the environments.
4. Upload data to the environments. You can move the data through data packages or by restoring the database. If you restore the database, additional steps are required in order to remap some properties to the new tenant.
5. Update your user information.

    1. Remove all user accounts except the admin user.
    2. Fix the admin user record in USERINFO.

        ```sql
        UPDATE USERINFO
        SET SID='mysid', NETWORKALIAS='myalias/email', NETWORKDOMAIN='https://sts.windows.net'
        WHERE ID = 'Admin'
        ```

6. Re-import all other users that have the correct security identifier (SID) and identity provider.
7. Run the following commands to update the tenant ID in the appropriate tables:


	```sql
    select VALUE from SYSSERVICECONFIGURATIONSETTING where name = 'TENANTID'
    select TENANTID from POWERBICONFIG
    select TENANTID from PROVISIONINGMESSAGETABLE
    select TENANTID from B2BINVITATIONCONFIG
    select TENANTID from RETAILSHAREDPARAMETERS
	```

8. Fully configure the environments. As part of this step, configure the integration endpoints.
9. Perform smoke tests on the user acceptance testing (UAT) environment in the new LCS project. These tests should focus on user sign-in, integrations, workflows, printing, reporting, and similar processes that depend on configuration and user information.
10. If you already had a production environment deployed, you must open a support request to move it to the new tenant after you've finished moving all the sandbox environments and completed UAT. The process of moving a production environment to a new tenant requires an extended downtime of 48 to 72 hours.

Depending on your solution and scope, you might have to perform additional steps on the new Azure AD tenant. These steps might include registering applications (for recurring integrations and warehouse management), adding domains, and setting up directory synchronization to enable single sign-on (SSO).

Note that calls to web services are allowed only from the **home** tenant for the environment. For example, the original tenant was companya.com, and integration ran as `services@companya.com`. In this case, when you switch tenants to companyb.com, you can no longer use `services@companya.com` for web service calls, even if you update **userInfo.networkdomain** to `https://sts.windows.net/companyb.com`.

> [!IMPORTANT]
> During this period, you will have two parallel LCS projects. You can verify the name and ID of the Azure AD tenant that is associated with an LCS project on the **Subscriptions available** page in LCS. You will lose any document handling attachments that are stored in Azure Blob storage.

## Delete environments on the old tenant

After the new LCS project against the new Azure AD tenant is fully functional, you must stop, deallocate, and delete the environments on the old LCS project. When you've finished, the **Configure** button becomes available for each environment. You should save any remaining artifacts from the Asset library that you might require later. Microsoft reserves the right to disable the customer's account and delete the customer data after the service has been suspended for an extended period.

## Suspend subscriptions on the old tenant

1. After all the environments have been deleted, and you've saved the LCS artifacts that you require, work with your cloud service provider or Volume Licensing Support to suspend all the licenses on the old Azure AD tenant.

    - **Cloud service provider:** Suspend the existing subscriptions against the old tenant.
    - **Volume Licensing Support:** Call the Volume Licensing support center to confirm that you've completed the work and that the subscriptions can now be suspended against the old tenant.

2. File a support ticket to delete the old LCS project.
