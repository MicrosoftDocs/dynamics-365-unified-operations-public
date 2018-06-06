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

Sometimes it becomes necessary to move the subscriptions and the LCS implementation project to a different Azure Active Directory (AAD) tenant. Some scenarios where this is necessary include:
•	The subscriptions were accidentally purchased against the incorrect AAD tenant 
Note: If you are a CSP and you sell Dynamics 365 for Finance and Operations subscriptions to an existing Microsoft Online Services customer, you must request a ‘Reseller relationship’ with that customer to place the subscriptions on their existing AAD tenant. If you create a new customer record for the customer in Partner Center, you create a new AAD tenant for the customer.
•	The customer changes his AAD tenant structure after they have purchased the subscriptions
The process to “move” your subscriptions and all related artifacts involves 4 main steps.
 
![move subscription process](./media/move-subscription-process.png) 
 
Activate subscriptions on the new tenant
Work with your Cloud Service Provider (CSP) or Volume License Reseller (VLR) to activate subscriptions against the new AAD tenant. All subscriptions for users as well as add-on environments must be activated.
Cloud Service Provider (CSP)
If you are licensed through a CSP agreement, purchase the necessary subscriptions against the new tenant from your CSP. If that new tenant already exists, the CSP must request a “Reseller relationship”; otherwise, they must create a “New customer” in Partner Center with the desired default domain name *.onmicrosoft,com, e.g contoso.onmicrosoft.com.
Ask the CSP to not suspend the existing subscriptions yet.
Volume licensing (VL)
If you are licensed through a VL agreement, you must call the Volume Licensing support center and ask them to remap the subscriptions from the old tenant to the new tenant. You can reach Volume Licensing Support through the Microsoft Office 365 admin center. Please ask them for a grace period where the subscriptions will be active on both tenants. Because of customer privacy concerns, this request must be made by the customer. You should have the following information available: 
•	Public Customer Number (PCN)
•	Enrollment Number
•	Incorrect/Current tenant domain *.onmicrosoft.com the subscription(s) is/are currently provisioned on
•	Correct/Destination tenant domain *.onmicrosoft.com the customer wants the subscription(s) provisioned under
•	Detailed Explanation of why the customer needs their VL subscription(s) migrated to a different tenant
•	Total number of paid subscriptions to be moved to the new tenant with subscription type and seat count
Important: it is crucial that the subscriptions are active on both tenants in parallel for a period of a few weeks until you have completed step Decommission LCS on the old tenant!
Configure LCS on the new tenant
On the new tenant, you will get a brand new LCS project that you must initiate and setup again, just like you did during the initial LCS setup process.
1.	Fully configure LCS – add users, VSTS association, subscription estimate, Asset library, BPM, etc.
2.	Deploy all non-production environments in the new LCS project
3.	Apply the necessary code packages to the environments
4.	Upload data to the environments. You can move the data through data packages or by restoring the database. If restoring the database, additional steps are needed to remap some properties to the new tenant.
i.	Update user information
i.	Remove all user accounts except for the admin user. 
ii.	Fix the admin user record in USERINFO
UPDATE USERINFO
SET SID=’mysid’, NETWORKALIAS=’myalias/email’, NETWORKDOMAIN=’https://sts.windows.net’
WHERE ID = ‘Admin’
iii.	Re-import all other users with the correct SID, identity provider, etc.
ii.	Update tenant ID in the following tables:
a.	select VALUE from SYSSERVICECONFIGURATIONSETTING where name = 'TENANTID'
b.	select TENANTID from POWERBICONFIG
c.	select TENANTID from PROVISIONINGMESSAGETABLE
d.	select TENANTID from B2BINVITATIONCONFIG
e.	select TENANTID from RETAILSHAREDPARAMETERS
5.	Fully configure the environments (e.g. integration endpoints)
6.	Perform smoke testing on the UAT environment in the new LCS project, focusing on user log on, integrations, workflows, printing, reporting, and similar processes that depend on configuration and user information
7.	If you already had Production deployed, you must open a support request to have it moved to the new tenant after you have moved all sandbox environments and completed UAT. Moving Production to a new tenant requires an extended downtime of 48-72 hours. 
Depending on your solution and scope, you might need to perform additional steps on the new AAD tenant, such as registering applications (e.g. for recurring integrations and warehouse management), adding domains, setting up Directory synchronization to enable single sign-on, etc. Please note that calls to web services are only allowed from the “home” tenant for the environment . E.g., if the original tenant was companya.com, and integration ran as services@companya.com, when you switch tenants to companyb.com, you cannot use services@companya.com anymore for web service calls, even if you update the userInfo.networkdomain to https://sts.windows.net/companyb.com.
Important: 
•	You will have two LCS projects in parallel during this period. You can verify Tenant name and Tenant ID of the AAD tenant associated with a LCS project on the Subscriptions available form.
•	You will lose document handling attachments if those are stored in BLOB storage. 
Delete environments on the old tenant
Once the new LCS project against the new AAD tenant is fully functional, you must stop, deallocate and delete the environments on the old LCS project (when done, you see the Configure button active on each environment). You should save any remaining artifacts from the Asset Library that you might still need in the future. Microsoft reserves the right to disable the Customer’s account and delete the Customer data after the service has been suspended for an extended period do time. Please see Service Description whitepaper for details. 
 

Suspend subscriptions on the old tenant
Once all environments have been deleted and you have saved any other LCS artifacts that you need, please work with your CSP or VL Support to suspend all the licenses on the old AAD tenant. 
•	CSP: suspend the existing subscriptions against the old tenant
•	VL: call the Volume Licensing support center. Confirm that you have completed the work and that the subscriptions can now be suspended against the old tenant.
Please also file a support ticket to have the old LCS project deleted.

