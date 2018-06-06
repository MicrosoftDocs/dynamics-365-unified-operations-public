---
# required metadata

title: Move an LCS Implementation project to another Azure Active Directory Tenant 
description: 
author: ClaudiaBetz-Haubold 
manager: AnnBe
ms.date: 06/06/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Move an LCS Implementation project to another Azure Active Directory Tenant 
[!include [banner](../includes/banner.md)]

When necessary, you can move your subscriptions and LCS Implementation project to a different Azure Active Directory (AAD) tenant. Some scenarios where this is necessary include:

- **Subscriptions were accidentally purchased against the incorrect AAD tenant**

 > [!NOTE]
 > If you are a CSP and you sell Microsoft Dynamics 365 for Finance and Operations subscriptions to an existing Microsoft Online Services customer, you must request a **Reseller relationship** with that customer to place the subscriptions on their existing AAD tenant. If you create a new customer record for the customer in Partner Center, you create a new AAD tenant for the customer.
 
- **Customer changes AAD tenant structure after the subscription purchase**

The process to move your subscriptions and all related artifacts, involves four main steps as shown in the following graphic.
 
![move subscription process](./media/move-subscription-process.png) 
 
## Activate subscriptions on the new tenant
Working with your Cloud Service Provider (CSP) or Volume License Reseller (VLR), activate the subscriptions against the new AAD tenant. All subscriptions for users, as well as add-on environments, must be activated.

### Cloud Service Provider (CSP)
If you are licensed through a CSP agreement, purchase the necessary subscriptions against the new tenant from your CSP. If the new tenant already exists, the CSP must request a **Reseller relationship** or create a **New customer** in the Partner Center with the desired default domain name, **\*.onmicrosoft,com, e.g contoso.onmicrosoft.com**.
Ask the CSP to not suspend the existing subscriptions at this time.

### Volume licensing (VL)
If you are licensed through a VL agreement, you must call the [Volume Licensing support center](https://www.microsoft.com/Licensing/servicecenter/Help/Contact.aspx) and ask them to remap the subscriptions from the old tenant to the new tenant. You can reach Volume Licensing Support through the Microsoft Office 365 admin center. Request a grace period where the subscriptions will be active on both tenants. Because of customer privacy concerns, this request must be made by the customer. You should have the following information available: 

- Public customer number (PCN)
- Enrollment number
- Current tenant domain that \*.onmicrosoft.com the subscriptions are currently provisioned on
- Destination tenant domain that \*.onmicrosoft.com the customer wants the subscriptions provisioned under
- Detailed explanation of why the customer needs their VL subscriptions migrated to a different tenant
- Total number of paid subscriptions to be moved to the new tenant including the subscription type and seat count

 >[!IMPORTANT]
 >It is crucial that the subscriptions are active on both tenants in parallel for a period of a few weeks until you have completed decommissioning LCS on the old tenant.

## Configure LCS on the new tenant
On the new tenant, you will get a new LCS project that you must initiate and setup completely.

1. Fully configure LCS. This includes adding users, VSTS association, subscription estimates, the Asset library, BPM, etc.
2. Deploy all non-production environments in the new LCS project.
3. Apply the necessary code packages to the environments.
4. Upload data to the environments. You can move the data through data packages or by restoring the database. If you restore the database, additional steps are needed to remap some properties to the new tenant.
5. Update your user information.
  a. Remove all user accounts except for the admin user. 
  b. Fix the admin user record in USERINFO

    UPDATE USERINFO
    SET SID=’mysid’, NETWORKALIAS=’myalias/email’, NETWORKDOMAIN=’https://sts.windows.net’
    WHERE ID = ‘Admin’
    
6. Re-import all other users with the correct SID and identity provider.
7. Update the tenant ID in the following tables:

 - select VALUE from SYSSERVICECONFIGURATIONSETTING where name = 'TENANTID'
 - select TENANTID from POWERBICONFIG
 - select TENANTID from PROVISIONINGMESSAGETABLE
 - select TENANTID from B2BINVITATIONCONFIG
 - select TENANTID from RETAILSHAREDPARAMETERS
 
8.	Fully configure the environments, including the integration endpoints.
9.	Perform smoke tests on the UAT environment in the new LCS project which focus on user log on, integrations, workflows, printing, reporting, and similar processes that depend on configuration and user information.
7.	If you already had a production environment deployed, you must open a support request to have it moved to the new tenant after you have moved all of the sandbox environments and completed UAT. Moving production to a new tenant requires an extended downtime of 48-72 hours. 

Depending on your solution and scope, you might need to perform additional steps on the new AAD tenant. This could include registering applications (for recurring integrations and warehouse management), adding domains, and setting up Directory synchronization to enable single sign-on. Note that calls to web services are only allowed from the **home** tenant for the environment. For example, if the original tenant was companya.com, and integration ran as services@companya.com, when you switch tenants to companyb.com, you can't use services@companya.com anymore for web service calls, even if you update the userInfo.networkdomain to https://sts.windows.net/companyb.com.

 > [!IMPORTANT]
 > You will have two parallel LCS projects during this period. You can verify the name and ID of the AAD tenant that is associated with a LCS project on the **Subscriptions available** form in LCS. You will lose any document handling attachments if they are stored in BLOB storage. 

## Delete environments on the old tenant
After the new LCS project against the new AAD tenant is fully functional, you must stop, deallocate, and delete the environments on the old LCS project. When you have finished, the **Configure** button will become available on each environment. You should save any remaining artifacts from the Asset library that you may need in the future. Microsoft reserves the right to disable the customer’s account and delete the customer data after the service has been suspended for an extended period of time. 
 

## Suspend subscriptions on the old tenant
After all of the environments have been deleted and you have saved the LCS artifacts that you need, work with your CSP or VL support to suspend all of the licenses on the old AAD tenant. 

- CSP: Suspend the existing subscriptions against the old tenant
- VL: Call the Volume Licensing support center to confirm that you have completed the work and that the subscriptions can now be suspended against the old tenant.
- File a support ticket to have the old LCS project deleted.

