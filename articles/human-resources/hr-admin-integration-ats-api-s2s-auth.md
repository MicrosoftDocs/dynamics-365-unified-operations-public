---
# required metadata

title: Server-to-server authentication for the ATS integration API
description: This article describes how to set up server-to-server authentication for integrations against the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.
author: jaredha
ms.date: 03/11/2024
ms.topic: article
# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-06-30
ms.dyn365.ops.version: Human Resources
---

# Server-to-server authentication for the ATS integration API



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes how to set up server-to-server authentication for application integrations against the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API. There are a couple of layers of security that need to be managed for the service principal to get access to the Microsoft Dataverse virtual table and associated data. The user needs to be granted access to the Dataverse virtual table in Microsoft Power Platform, and access to the data in Dynamics 365 Human Resources.

## Enable access to Dataverse virtual tables in Power Platform

The first step enables access to the Dataverse virtual tables in Power Platform is to set up your application in Power Platform for authentication against Dataverse virtual table endpoints. For more information, see [Microsoft Dataverse developer guide](/powerapps/developer/data-platform).

  - For single-tenant app registrations: [Use single-tenant server-to-server authentication](/powerapps/developer/data-platform/use-single-tenant-server-server-authentication)
  - For multitenant app registrations: [Use multitenant server-to-server authentication](/powerapps/developer/data-platform/use-multi-tenant-server-server-authentication)

### Creating a security role for ATS integrations

One of the steps after creating the application user is to assign the user to a security role that defines the access the application has to the endpoints. This is step 7 in [Application user creation](/powerapps/developer/data-platform/use-single-tenant-server-server-authentication#application-user-creation) for single-tenant app registrations, and [Create a security role for the application user](/powerapps/developer/data-platform/use-multi-tenant-server-server-authentication#create-a-security-role-for-the-application-user) for multitenant registrations. 

The role to which you assign the application user should have access to the data entities used for your ATS integration. This doesn't exist out of the box, so a new security role needs to be created. The new role can be created following the steps outlined in [Create a security role](/power-platform/admin/create-edit-security-role#create-a-security-role).

For the new role, appropriate access must be assigned to, at a minimum, the following entities on the **Custom Entities** tab of the new role. There may be additional entities you may need to add if the integration uses more extensive application data. After the new role is created, it can be assigned to the application user.

  - Base worker (mshr)
  - Candidate to hire (mshr)
  - Certificate competency (mshr)
  - Certificate type (mshr)
  - Company
  - Compensation job function (mshr)
  - Compensation job type (mshr)
  - Country/regions (mshr)
  - Department (mshr)
  - Education competency (mshr)
  - Education degree (mshr)
  - Education disciplines (mshr)
  - Educational requirements (mshr)
  - Identification (mshr)
  - Identification type (mshr)
  - Institution (mshr)
  - Issuing agency (mshr)
  - Job compensation (mshr)
  - Jobs (mshr)
  - Level of education (mshr)
  - Party contacts (mshr)
  - People (mshr)
  - Person addresses (mshr)
  - Person screening (mshr)
  - Position type (mshr)
  - Positions V2 (mshr)
  - Professional experience competency (mshr)
  - Rating level (mshr)
  - Rating models (mshr)
  - Reason codes (mshr)
  - Recruiting request (mshr)
  - Recruiting request location (mshr)
  - Recruiting request position (mshr)
  - Recruiting request skills (mshr)
  - Screening type (mshr)
  - Skill competency (mshr)
  - Skills (mshr)
  - Titles (mshr)
  - Veteran status (mshr)
  - Worker (mshr)

## Granting application permissions to Human Resources data

The second step is to grant appropriate permissions to the data in Human Resources by linking it to a user in the Human Resources application. For an application user, the server-to-server calls through Dataverse virtual tables are done in the context of the identity of the user (app) in Dataverse that is invoking the action. The virtual table adapter service then looks up the associated user in Human Resources and runs the query in the context of that user. This means users must be created in Human Resources with the correct roles assigned to provide access to the data that the integrating application needs.

The Human Resources user also needs the correct permissions assigned to the data in Human Resources. The **Recruiting Application** (HcmRecruitingIntegrator) role is available with privileges to the primary entities required for integrating with recruiting data. This role can be assigned to the application user in the **Users** page to grant appropriate access to the data. For more information about Human Resources security roles, see [Role-based security](/dynamics365/fin-ops-core/dev-itpro/sysadmin/role-based-security).

### Set up the new user with appropriate permissions

To set up the new user with appropriate permissions, follow these steps:

  1. Open the **Users** page in Human Resources and select **New**.
  2. Enter a **User ID** and **User name** for the new application user. For example, you can enter "RecruitingIntegration".

      > [!NOTE]
      > If the app doesn't have a Microsoft Microsoft Entra user account or email address, you can put something like "RecruitingApp" in the email address and provider fields for the user.

  3. On the **User's roles** Fast Tab, select the **Assign roles** action.
  4. In the **Assign roles to user** pane, select **Recruiting application**, and select **OK**.
  5. Save the new user record.

### Link the new Human Resources user to the application

After the user is created, a record must be created for the application in the **Microsoft Entra Applications** page to link the app to the Human Resources user.

  1. Open the **Microsoft Entra Applications** page, select **New**.
  2. In the **Client ID** field, enter the client ID of the application user created for the application.
  3. In the **Name** field, enter the name of the integrating application.
  4. In the **User ID** field, select the new Human Resources user created for the recruiting integration.
  5. Save the new record.

The application will then have access to Human Resources data, limited only to the data required for recruiting application integrations.

## See also

[Recruit job candidates](hr-personnel-recruit.md)<br>
[What is Microsoft Dataverse?](/powerapps/maker/data-platform/data-platform-intro)<br>
[Use the Microsoft Dataverse Web API](/powerapps/developer/data-platform/webapi/overview)<br>
[Create and update option sets using the Web API](/powerapps/developer/data-platform/webapi/create-update-optionsets)<br>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
