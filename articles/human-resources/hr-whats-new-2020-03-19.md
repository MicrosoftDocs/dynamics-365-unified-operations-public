---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (March 19, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 3/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (March 19, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3014. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Human Resources environment limits based on updated licensing (394595)

The limit on the number of environments per project in Lifecycle Services (LCS) is changed. Previously limited to two environments, the limit on the number of production and sandbox environments that can be created for Human Resources in LCS is now based on updated licensing. You are now able to create as many environments as needed per LCS project, dependent on the number of licenses purchased. The new licensing, updated on February 1st, allows customers to purchase additional environments. See the Dynamics 365 Licensing Guide, which can be downloaded from the [Dynamics 365 Pricing](https://dynamics.microsoft.com/en-us/pricing/#HumanResources) page, for information licensing requirements for additional environments.


## Provide cross company viewing of Compensation data for Employees and Managers - (403904)

Turn this feature on in Feature Management. When turned on, managers will be able to see direct and extended reports compensation without having to log into the company of employment. Full compensation history is available from any logged in company the manager has access to. [More information related to Employee and Manager self-service can be found here](docs.microsoft.com)

## Enable Global address book "merge" functionality - (427189)

With this change, merging duplicate address book entries can be accomplished by selecting the duplicate records and choosing to "Merge" from the Global address book page.

## Unable to adjust leave balance for a plan with no accruals was created with "multiple leave type" feature on - (419635)

With this change, you will be able to adjust balances for leave plans that have been created with the Multiple leave type (Preview) feature enabled in feature management.

## Common Data Service solution is now available with the following changes:

| Description | Change |
| --- | --- |
| **Job/Position** entity changes | <ul><li>**Compensation region** added</li>|
| **Job position dimension** entity added | <ul><li>**Financial dimensions** added</li>
| **Worker** entity changes | <ul><li>**Name sequence** added</li><li>**Works from home** added</li><li>**Language** added</li><li>**Seniority date** added</li><li>**Anniversary date** added</li><li>**Original hire date** added</li></ul> |
| **Employment** entity changes | <ul><li>**Financial dimensions** added</li><li>**Termination reason** added</li><li>**Termination date** renamed from **Transition date**</li><li>**Probation date** added</li></ul> |
| **Worker address** entity changes | <ul><li>**Street address** added</li><li>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation</li></ul> |
| New variable compensation setup entities | <ul><li>**Compensation variable plan type**</li><li>**Compensation variable plan**</li><li>**Vesting rules**</li><li>**Compensation variable plan level**</li></ul> |
| New **Worker calendar employment** entity | <ul><li>**Work calendar entity** added</li></ul> |
| New **Payroll position detail** entity | <ul><li>**Payroll position detail** added</li></ul> |
| New **Title** entity | <ul><li>**Title** added</li></ul> |
*The new "Title" entity is included in the CDS but will not initially be referenced from Job Position or Job entities.

*Financial dimensions for both positions and employment provide **Single** direction updates from Human Resources to the Common data service.  

Over the course of the next few weeks the above changes will be available in all environments. If you would like to manually install the latest HR CDS Solution, follow the steps below. 

1.	Navigate to https://admin.powerplatform.microsoft.com.
2.	Select Environments.
3.	Find the environment you would like to upgrade. This should correspond to the Environment name in the Common data service information section in the About form found in D365 for Human Resources.
4.	Click on the Name of the environment to go to the environment details.
5.	In the Action bar at the top of the page, click Manage Solutions.  This will open a new browser window and navigate to Dynamics 365 Administration Center in the context of your environment.
6.	In the Solution list, find the Dynamics 365 for Talent Anchor solution and click on it.
7.	Click the Upgrade button to apply the latest Solution version.

## SharePoint preview not working in some environments

If document previewing for SharePoint stored documents does not display follow these steps to troubleshoot the issue:
 - Verify the Admin user account has an email associated with the user record. (this can be completed in the User page)
          - If not set up, the email and provider needs to be added via the OData Excel add in. By default, the email address is not present in the Excel design. So you will need to edit the excel design, add all fields, apply and refresh. Once this is done, the admin account can be updated.
 - Once the admin account has an associated email account, login to Dynamics 365 Human resources as the admin.
 - Access an attachment that has been stored in SharePoint. (This will initialize the preview)
 - Login with any other user with access to attachments and verify the preview functions properly.

## Coming Soon

### Platform update 33

- (Preview) full page apps - This preview feature, which requires the Saved views feature to be enabled, allows Power Apps and third-party apps to be added as full-page experiences via the dashboard
- (Preview) Saved views - This preview feature enables saved views, which is a significant enhancement to the personalization subsystem. This feature allows users to have multiple named sets of personalizations per page. Views can also be published to security roles.
- Optimized "is one of" filtering experience - This feature enables an optimized "is one of" filtering experience that makes it easier to enter multiple filter values, has a simpler mechanism to remove individual or all filter values, and has a more compact and intuitive visualization of filter values.
- Recommended fields - Users often need to add fields to a grid or page; however, with the large number of available fields, this can be difficult. Instead of having to search through a large list, this feature enables the system to surface a set of recommended fields based on what other users most often add in similar scenarios
- Sticky default actions in grids - This feature ensures that the default action in a grid is linked to a specific column in a grid, regardless of whether that column is moved or hidden.

## New production release cadence

Beginning in April, the release cadence for Human Resources will shift from a weekly update to a bi-weekly update. To ensure alignment with safe deployment practices, and maintain high standards of stability and reliability in the service, the process of deploying service updates to all regions will be a two-week rollout. Additional testing and monitors will be in place to verify successful deployment at each stage of the process. For more information on the release cadence, see the [Update process](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-admin-setup-update-process) documentation.
