---
title: Move Lifecycle Services implementation projects to different Microsoft Entra tenants
description: Learn about how to move your subscriptions and Lifecycle Services Implementation project to a different Microsoft Entra tenant.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 03/26/2026
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.search.form: 
ms.dyn365.ops.version: AX 7.0
---

# Move Lifecycle Services implementation projects to different Microsoft Entra tenants

[!include [banner](../../../finance/includes/banner.md)]

You can move your subscriptions and your Microsoft Dynamics Lifecycle Services Implementation project to a different Microsoft Microsoft Entra tenant. Here are some scenarios where this move might be required:

- You accidentally purchase subscriptions against the wrong Microsoft Entra tenant.

    > [!NOTE]
    > If you're a cloud service provider, and you sell subscriptions for finance and operations apps to an existing customer, you must request a reseller relationship with that customer to put the subscriptions on the customer's existing Microsoft Entra tenant. If you create a new customer record for the customer in Microsoft Partner Center, you create a new Microsoft Entra tenant for the customer.

- The customer changes the structure of the Microsoft Entra tenant after the subscription is purchased.

The process for moving your subscriptions and all related artifacts has four main steps, as shown in the following illustration.

:::image type="content" source="../../fin-ops/get-started/media/move-subscription-process.png" alt-text="Screenshot of the process for moving subscriptions.":::

## Activate subscriptions on the new tenant

Work with your cloud service provider or volume license reseller to activate the subscriptions against the new Microsoft Entra tenant. Activate all subscriptions for users, and for add-on environments.

### Cloud service provider

If you're licensed through a Microsoft Cloud Solution Provider (CSP) agreement, purchase the required subscriptions against the new tenant from your cloud service provider. If the new tenant already exists, the cloud service provider must request a reseller relationship. Alternatively, in Partner Center, the cloud service provider must create a new customer that has the desired default domain name, **\*.onmicrosoft.com** (for example, **contoso.onmicrosoft.com**).

Ask the cloud service provider not to suspend the existing subscriptions at this time.

### Volume Licensing

If you licensed through a Microsoft Volume Licensing agreement, call the [Volume Licensing support center](https://www.microsoft.com/Licensing/servicecenter/Help/Contact.aspx) and ask them to remap the subscriptions from the old tenant to the new tenant. You can contact Volume Licensing Support through Microsoft 365 admin center. Request a grace period, when the subscriptions are active on both tenants. Because of customer privacy concerns, the customer must make this request. Have the following information available:

- Public customer number.
- Enrollment number.
- The current tenant domain that the subscriptions are currently provisioned on.
- The destination tenant domain that the customer wants the subscriptions provisioned under.
- A detailed explanation of why the customer must migrate its Volume Licensing subscriptions to a different tenant.
- The total number of paid subscriptions that must be moved to the new tenant, together with the subscription type and seat count.

> [!IMPORTANT]
> It's crucial that the subscriptions are active on both tenants in parallel for a few weeks, until you finish decommissioning Lifecycle Services on the old tenant.

## Configure Lifecycle Services on the new tenant

On the new tenant, you get a new Lifecycle Services project that you must initiate and set up.

1. Complete the Project Onboarding wizard. For more information, see [Lifecycle Services project onboarding](../lifecycle-services/project-onboarding.md). When completing the wizard, indicate on the **Project Overview** page that you're **Moving existing Lifecycle Services project from another tenant** and provide the source Lifecycle Services project ID.
1. Fully configure Lifecycle Services. As part of this configuration, you must:
1. Upload and activate a subscription estimator. If you're already live in the source Lifecycle Services project, you need to ensure that the estimates match.
1. Add your deployable package to the asset library.
1. Update your Business process modeler (BPM) library.

> [!IMPORTANT]
> During this period, you have two parallel Lifecycle Services projects. You can verify the name and ID of the Microsoft Entra tenant that is associated with an Lifecycle Services project on the **Subscriptions available** page in Lifecycle Services.

## Move your sandbox environments to the new tenant

1. Deploy the nonproduction environments in the new Lifecycle Services project.
1. Apply the required code packages to the environments. Make sure that the target is running the same application version as the source. Use [All-in-one deployable packages](../dev-tools/aio-deployable-packages.md) and include any ISV licenses, if applicable.
1. Upload data to the environments. You can move the data through data packages or by restoring the database. If you restore the database, you need to remap some properties to the new tenant.
   1. This script is only required if you are performing a database restore. Before doing the export, update the placeholders with your old and new tenant details and execute the SQL command on the source environment.
      1. This will take the backup of SYSCONFIG table and update the value of the tenant with target tenant information.
      2. Once the export is done you will need to recover this table to get back the source tenant information. The script to do this is attached below.
   ```
     -- =============================================
      -- Script: Update AAD Tenant in SYSCONFIG
      -- Purpose: Updates the AAD tenant domain and tenant ID
      --          in the SYSCONFIG table after a tenant migration.
      -- =============================================
    
      DECLARE @NewTenantDomain VARCHAR(255)
      DECLARE @NewTenantId VARCHAR(255)
      DECLARE @OldTenantDomain VARCHAR(255)
      DECLARE @OldTenantId VARCHAR(255)
    
      SET @NewTenantDomain = '<new-tenant-domain>' -- New AAD tenant domain (e.g., contoso.onmicrosoft.com)
      SET @NewTenantId = '<new-tenant-id>'         -- New AAD tenant ID (GUID)
      SET @OldTenantDomain = '<old-tenant-domain>' -- Current AAD tenant domain
      SET @OldTenantId = '<old-tenant-id>'         -- Current AAD tenant ID (GUID)
    
      -- Back up SYSCONFIG before making changes
      PRINT 'Backing up SYSCONFIG table...'
      SELECT * INTO SYSCONFIG_BKP FROM SYSCONFIG
    
      -- Update tenant domain
      IF EXISTS (SELECT VALUE FROM SYSCONFIG
                 WHERE CONFIGTYPE = 0 AND ID = 0 AND VALUE = @OldTenantDomain)
      BEGIN
          PRINT 'Updating tenant domain to: ' + @NewTenantDomain
          UPDATE SYSCONFIG
          SET VALUE = @NewTenantDomain
          WHERE CONFIGTYPE = 0
            AND ID = 0
            AND VALUE = @OldTenantDomain
      END
      ELSE
      BEGIN
          PRINT 'No tenant domain update required.'
      END
    
      -- Update tenant ID
      IF EXISTS (SELECT VALUE FROM SYSCONFIG
                 WHERE CONFIGTYPE = 1 AND ID = 0 AND VALUE = @OldTenantId)
      BEGIN
          PRINT 'Updating tenant ID to: ' + @NewTenantId
          UPDATE SYSCONFIG
          SET VALUE = @NewTenantId
          WHERE CONFIGTYPE = 1
            AND ID = 0
            AND VALUE = @OldTenantId
      END
      ELSE
      BEGIN
          PRINT 'No tenant ID update required.'
      END
   ```
   ```
     -- Restore SYSCONFIG to original values after export
      DELETE FROM SYSCONFIG
      INSERT INTO SYSCONFIG SELECT * FROM SYSCONFIG_BKP
      DROP TABLE SYSCONFIG_BKP
   ```
    
1. Update your user information.
1. Remove all user accounts except the admin user.
1. Fix the admin user record in USERINFO.

 ```sql
        UPDATE USERINFO
        SET SID='mysid', NETWORKALIAS='myalias/email', NETWORKDOMAIN='https://sts.windows.net'
        WHERE ID = 'Admin'
        ```
1. Reimport all other users that have the correct security identifier (SID) and identity provider.
1. Run the following commands to update the tenant ID in the appropriate tables. You can verify the Microsoft Entra tenant ID that is associated with an Lifecycle Services project on the **Subscriptions available** page in Lifecycle Services.
 
 ```sql
 Update POWERBICONFIG set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
 Update PROVISIONINGMESSAGETABLE set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
 Update B2BINVITATIONCONFIG set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
 Update RETAILSHAREDPARAMETERS set TENANTID = 'newtenantid' where TENANTID = 'oldtenantid'
 ```

1. Fully configure the environments. As part of this step, configure the integration endpoints.
1. Perform smoke tests on the user acceptance testing (UAT) environment in the new Lifecycle Services project. These tests should focus on user sign-in, integrations, workflows, printing, reporting, and similar processes that depend on configuration and user information.

Depending on your solution and scope, you might have to perform more steps on the new Microsoft Entra tenant. These steps might include registering applications (for recurring integrations and warehouse management), adding domains, and setting up directory synchronization to enable single sign-on (SSO).

Calls to web services are allowed only from the **home** tenant for the environment. For example, the original tenant was companya.com, and integration ran as `services\@companya.com`. In this case, when you switch tenants to companyb.com, you can't use `services\@companya.com` for web service calls, even if you update **userInfo.networkdomain** to `https://sts.windows.net/companyb.com`.

> [!IMPORTANT]
> On your sandbox environments, you lose any document handling attachments that are stored in Azure Blob storage. Microsoft moves Blob storage only for production environments.

## Move your production environment to the new tenant

If you don't already have a production environment deployed on the old tenant, you can skip this section.

> [!IMPORTANT]
> You can only perform tenant migration if the **source and target production environments are in the same region**. If the source environment is in a different region, you need to move the environment to the same region as the target. For more information about moving an environment, see [Finance and operations apps environment migration](/dynamics365/fin-ops-core/dev-itpro/deployment/environment-migration-process).

> [!IMPORTANT]
> Tenant-to-tenant migration isn't supported when Customer Lockbox is enabled. You must disable Customer Lockbox to move an environment to another tenant. You can re-enable Customer Lockbox once the migration is completed. For more information, see [Securely access customer data by using Customer Lockbox Known Issues](/power-platform/admin/about-lockbox#known-issues).  

If you already have a production environment deployed on the old tenant, Microsoft moves your database and Azure Blob storage from your old production environment to the new one. As a prerequisite, complete the following steps after you finish moving all the sandbox environments and complete UAT. The process of moving a production environment to a new tenant requires downtime of up to 48 hours.

Before requesting the production environment, ensure that you complete all prerequisites:

1. Get all required licenses that are needed to correctly license all users on the production environment.
1. When the licenses are in place, upload a subscription estimator to the new Lifecycle Services project. It should match the subscription estimator that is active in the source Lifecycle Services project, and it must correctly reflect peak transaction volumes.
1. Send an email to Dynamics 365 FO Go-Live (d365fogl\@microsoft.com) stating that your new Lifecycle Services project is ready for Microsoft to move your production database and Azure Blob Storage. To ensure that the process runs smoothly, provide the following details in the email. Copy the following list to your email, and then answer all of the information line by line.

  **Lifecycle Services**

- Provide the Lifecycle Services IDs (number in the Lifecycle Services project URL) for source and target Lifecycle Services project.
- Confirm that the go-live date is set correctly in the target Lifecycle Services project.
- Confirm that the update schedules are set in the target Lifecycle Services project (**Lifecycle Services > Menu > Project settings > Update settings**).
- Confirm if you're using Azure Blob Storage for document attachments.
- Confirm that your project is identified as a tenant move in the Project Onboarding wizard.
- Confirm that your deployable package is marked as a release candidate in the target Lifecycle Services project.
  
  **Environment region**

- Confirm that the target production environment is deployed to the same region as the source production environment.

  > [!IMPORTANT]
  > You can only perform tenant migration if the **source and target production environments are in the same region**. If the source environment is in a different region, you need to move the environment to the same region as the target. For more information about moving an environment, see [Finance and operations apps environment migration](/dynamics365/fin-ops-core/dev-itpro/deployment/environment-migration-process).

  **Testing**

- Confirm that the smoke testing is completed on the sandbox environment (Tier-2 or higher) in the target Lifecycle Services project.

  **Code Management**

- Share which environment version you plan to deploy your new production environment.
- List the ISV solutions you're using.
- Confirm which version your old production environment is running on.
- Confirm that nonstandard code to be applied in the new production environment is exactly the same as the nonstandard code present in the old production environment to prevent database copy issues.
- Confirm if there were any non-typical actions taken on your old production environment that need to be considered on the new production environment, like installation of a custom font or environment upscale.

  **Cutover and timeline**

- Describe how you'll conduct your cut over.
- Confirm the dates when the source Lifecycle Services environments and project are deallocated and deleted.

1. The Dynamics 365 FO Go-Live team replies to you within two business days and a FastTrack team works with you on the assessment of the project readiness for production deployment.
1. When the tenant move assessment is successfully completed, the FastTrack team enables production environment slot in Lifecycle Services.
1. Deploy production environment in Lifecycle Services.

- You can't select the same name for the new production environment, as it's in use for your old production environment. Choose a new environment name so that a new URL is generated.
- Make sure you select the same application version that is used by your current production environment.
- In the Production configuration wizard, select a generic user account, not a named user, as Environment Administrator.

1. After the production environment is deployed, verify that source and target environments have exactly the same code, otherwise migration fails. If necessary, install deployable packages on the target production environment.
1. Request to copy database and blob storage from the old production environment to the new production environment. Submit a **support ticket** requesting a copy of the database and blob storage, if applicable, from the old production environment to the new production environment. Be sure to include Lifecycle Services IDs and environment IDs from source and target projects in the support ticket.
  
- This process requires interaction between Microsoft and the implementing project team. Ensure that you follow the email notifications or notifications directly in the service request.
- After Microsoft completes the tenant migration activity and informs you to continue with the next steps, you need to reimport all users from the new Microsoft Entra tenant.
- You need to validate the new production environment to ensure that all business processes are successful.
- If you encounter an issue after the migration, file a support ticket.

## Tear down the Lifecycle Services project on the old tenant

After the new Lifecycle Services project on the new Microsoft Entra tenant is fully functional, you must stop, deallocate, and delete the environments on the old Lifecycle Services project. When you've finished, the **Configure** button becomes available for each environment. If you already had a production environment on the old tenant, you must file a support ticket to have it deleted.

You should save any remaining artifacts from the Asset library that you might require later.

After all environments have been deleted and all artifacts saved, an Organization Administrator on the old tenant must delete the Lifecycle Services project.
Microsoft reserves the right to disable the customer's account and delete the customer data after the service has been suspended for an extended period.

## Suspend subscriptions on the old tenant

After all the environments have been deleted, and you've saved the Lifecycle Services artifacts that you require, work with your cloud service provider or Volume Licensing Support to suspend all the licenses on the old Microsoft Entra tenant.

- **Cloud service provider** - Suspend the existing subscriptions against the old tenant.
- **Volume Licensing Support** - Call Volume Licensing Support to confirm that you've completed the work and that the subscriptions can now be suspended against the old tenant.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
