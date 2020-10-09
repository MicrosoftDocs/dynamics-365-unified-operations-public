---
# required metadata

title: Move LCS implementation projects to different Azure AD tenants
description: This topic explains how to move your subscriptions and LCS Implementation project to a different Azure AD tenant.
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 10/09/2020
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

You can move your subscriptions and your Microsoft Dynamics Lifecycle Services (LCS) Implementation project to a different Microsoft Azure Active Directory (Azure AD) tenant. Here are some scenarios where this move might be required:

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

1. Complete **Project Onboarding**. For more information, see [LCS project onboarding](../../dev-itpro/lifecycle-services/project-onboarding.md). When completing the onboarding wizard, you **must** indicate on the **Project Overview** page that you are **Moving existing LCS project from another tenant** and provide the source LCS project ID.
2. Fully configure LCS. As part of this configuration, you must:
	1. Upload and activate a subscription estimator. If you are already live in the source LCS project, please ensure that the estimates match.
	2. Add your deployable package to the asset library.
	3. Update your Business process modeler (BPM) library.

> [!Important]
> During this period, you will have two parallel LCS projects. You can verify the name and ID of the Azure AD tenant that is associated with an LCS project on the **Subscriptions available** page in LCS.

## Move your Sandbox environments to the new tenant
1. Deploy the non-production environments in the new LCS project.
2. Apply the required code packages to the environments. Make sure that the target is running the same application version as the source. We recommend using [All-in-one deployable packages](../../dev-itpro/dev-tools/aio-deployable-packages.md) and include any ISV licenses, if applicable.
3. Upload data to the environments. You can move the data through data packages or by restoring the database. If you restore the database, additional steps are required in order to remap some properties to the new tenant.
4. Update your user information.
	1. Remove all user accounts except the admin user.
	2. Fix the admin user record in USERINFO.
	
	```sql
        UPDATE USERINFO
        SET SID='mysid', NETWORKALIAS='myalias/email', NETWORKDOMAIN='https://sts.windows.net'
        WHERE ID = 'Admin'
        ```
5. Re-import all other users that have the correct security identifier (SID) and identity provider.
6. Run the following commands to update the tenant ID in the appropriate tables. You can verify the Azure AD tenant ID that is associated with an LCS project on the **Subscriptions available** page in LCS.
	
	```sql
	Update POWERBICONFIG set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
	Update PROVISIONINGMESSAGETABLE set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
	Update B2BINVITATIONCONFIG set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
	Update RETAILSHAREDPARAMETERS set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
	```

7. Fully configure the environments. As part of this step, configure the integration endpoints.
8. Perform smoke tests on the user acceptance testing (UAT) environment in the new LCS project. These tests should focus on user sign-in, integrations, workflows, printing, reporting, and similar processes that depend on configuration and user information.

Depending on your solution and scope, you might have to perform additional steps on the new Azure AD tenant. These steps might include registering applications (for recurring integrations and warehouse management), adding domains, and setting up directory synchronization to enable single sign-on (SSO).

Note that calls to web services are allowed only from the **home** tenant for the environment. For example, the original tenant was companya.com, and integration ran as services\@companya.com. In this case, when you switch tenants to companyb.com, you can no longer use services\@companya.com for web service calls, even if you update **userInfo.networkdomain** to <https://sts.windows.net/companyb.com>.

> [!Important]
> On your Sandbox environments, you will lose any document handling attachments that are stored in Azure Blob storage. Blob storage will be moved by Microsoft only for production environments.

## Move your production environment to the new tenant

If you do **not** have a production environment deployed already on the old tenant, you can skip this section.

If you already had a production environment deployed on the old tenant, Microsoft will move your database and Azure Blob storage from your old production environment to the new one. As a pre-requisite, you must complete the additional steps below after you've finished moving all the sandbox environments and completed UAT. The process of moving a production environment to a new tenant requires a downtime.

Before requesting the production environment ensure that all pre-requisites are completed:

1. Get all required licenses that are needed to correctly license all users on the  production environment.
2. Once the licenses are in place, upload a subscription estimator to the new LCS project. It should match the subscription estimator that is active in the source LCS project, and it must correctly reflect peak transaction volumes.
3. Send an email to Dynamics 365 FO Go-Live **d365fogl\@microsoft.com** stating that your new LCS project is ready for Microsoft to move your production database and Azure Blob Storage. To ensure that the process will run smoothly, please provide the following details in the e-mail (you can copy all these topics, paste it on the e-mail and answer each one in line):

	**LCS**
	- Please provide the LCS IDs (number in the LCS project URL) for source and target LCS project.
	- Please confirm that the go-live date is set correctly in the target LCS project.
	- Please confirm that the update schedules are set in the target LCS project (LCS > Menu > Project settings > Update settings).
	- Please confirm if you are using Azure Blob Storage for document attachments.
	- Please confirm that your project is identified as a tenant move in Project Onboarding wizard.
	
	**Testing**
	- Please confirm that the smoke testing is completed on the sandbox environment (Tier-2 or higher) in the target LCS project.
	
	**Code Management**
	- Please confirm that your deployable package is marked as a release candidate in the target LCS project.
	- Please list the ISV solutions you are using.
	- Please confirm which version your old production environment is running on.
	- Please confirm that non-standard code to be applied in the new production environment will be exactly the same as the non-standard code present in the old production environment in order to prevent database copy issues.
	- Please confirm if there were any untypical actions taken on your old production environment which needs to be considered on the new production environment, like installation of a custom font, environment upscale, etc.
	
	**Environment**
	- Please share on which environment version you plan to deploy your new production environment.
	- Please describe how you will conduct your cut-over.
	- Please confirm the dates when the source LCS environments and project will be deallocated and deleted.
	
4. **Dynamics 365 FO Go-Live** team will reply to you within 2 business days and a FastTrack Solution Architect will work with you on the assessment of the project readiness for production deployment.
5. When the tenant move assessment is successfully completed, the FastTrack Solution Architect will approve your production request for deployment.
6. Create the production deployment request on the new LCS project.

	- It is not possible to select the same name for the new production environment, as it is in use for your old production environment. You will need to choose a new environment name and hence a new URL will be generated.
	- Make sure you select the same application version as is used by your current production environment.
	- In the production configuration wizard, select a generic user account, not a named user, as Environment Administrator.

7. Once production environment has been deployed, verify that source and target environments have exactly the same code, otherwise migration will fail. If necessary, deployable packages must be installed on the target production environment.
8. Request to copy database and blob storage from old production environment to the new production environment.
	1. Raise a [service request](../../dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team.md) of type **Other** to request Microsoft Service Engineering team to copy the database and blob storage from the old production environment to the new production environment.
	2. This process will require interaction between Microsoft and the implementing project team. Ensure that you follow the e-mail notifications or notifications directly in the service request. 
	3. After Microsoft has completed the activity and informed you about it, you will need to validate the new production environment. 
	4. If you face an issue after the migration, please raise a support ticket.

## Tear down the LCS project on the old tenant

After the new LCS project against the new Azure AD tenant is fully functional, you must stop, deallocate, and delete the environments on the old LCS project. When you've finished, the **Configure** button becomes available for each environment. If you already had a production environment on the old tenant, you must file a support ticket to have it deleted.

You should save any remaining artifacts from the Asset library that you might require later.

Once all environments have been deleted and all artifacts saved, an Organization Administrator on the old tenant must delete the LCS project itself.
Microsoft reserves the right to disable the customer's account and delete the customer data after the service has been suspended for an extended period.

## Suspend subscriptions on the old tenant

After all the environments have been deleted, and you've saved the LCS artifacts that you require, work with your cloud service provider or Volume Licensing Support to suspend all the licenses on the old Azure AD tenant.

- **Cloud service provider**: Suspend the existing subscriptions against the old tenant.
- **Volume Licensing Support**: Call the Volume Licensing support center to confirm that you've completed the work and that the subscriptions can now be suspended against the old tenant.
