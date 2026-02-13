---
title: Manage support experiences for finance and operations apps
description: Learn about using the Support tool to on Microsoft Dynamics Lifecycle Services to manage support incidents and support plans in Lifecycle Services.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0fa10573-8146-446e-8124-8a7af9546add
ms.custom: sfi-image-nochange
---

# Manage support experiences for finance and operations apps
[!include [banner](../includes/banner.md)]


## Open a new incident
1. In Lifecycle Services, go to the project for which you want to file a support incident. 

1. Select the **Support** tile.

   :::image type="content" source="media/CPS1.png" alt-text="Screenshot of Support menu.":::

1. On the **Submitted to Microsoft** tab, select the **Submit an incident** button.

   :::image type="content" source="media/CPS2.png" alt-text="Screenshot of Support button.":::

1. Select an issue category.

1. Select an issue area.

1. In the **Describe your issue** area, enter the following information:

   - Select **Yes** if the issue occurred in an environment. Select the environment name.  
   - Enter a short description of your issue in the **Title** field.
   - Provide details about the issue and the steps needed to reproduce the error.
   - If applicable, enter an error message. 
   - If possible, attach screenshots that illustrate the problem. To do this, select **Attach file from computer**.
 
 
   > [!NOTE]
   > When you create an incident, Issue search populates the top 10 "Possible issue solutions" search results based on your selection and input, and dynamically refreshes these results as you provide more details during support case creation. 
   > 
   > You can still access standalone Issue search by using the drop-down menu if you need to search for more solutions. 
 
1. Enter the primary contact information. The customer support team uses these contact details to contact you about the case.

1. Select the support contract and the severity level. 
    
   - Support contracts for on-premises environments have a limited incident count. 
   - Support contracts for cloud environments have an unlimited incident count. 
   - For on-premises products or cloud environments, select the support option to use if you have multiple tier support contracts. 
  
1. Select **Submit**. 

After you select **Submit**, an incident is created and added to the **Incidents** list. You receive an email message from the Microsoft Support Engineer assigned to your case. 


## Support plans in Lifecycle Services
Support plan entitlements are based on several different identifiers. Not all identifiers apply to your situation. If you're missing a support plan or entitlement in Lifecycle Services, determine which identifier you need to tie it to your project in Lifecycle Services. If there's more than one organization, note which one is current by selecting your name in the upper-right corner of Lifecycle Services. Select the organization that applies to your scenario and contains the benefits that you want to use.

### Unique contract ID/access ID
The following online support plans require a unique contract ID/access ID combination linked to your sign-in in Lifecycle Services:

-   Unified
-   Premier
-   Advanced support for partners

If you don't know your unique contract ID/access ID combination, contact your Microsoft account manager to have an ID created for you.

To link your contract ID/access ID to your account, complete the following steps:

1. From within a project, select **Support** from the main menu, then select **Manage Support plans**. 
1. Select **Add contract**.

   :::image type="content" source="media/56c7bfd469f6d850d456e9e7a89e0d8d.png" alt-text="Screenshot of Add contract.":::

1. Enter your access ID and your password or contract ID, then select **Add contract**.

   :::image type="content" source="media/4abba1127549ef484a58daf51609d924.png" alt-text="Screenshot of Add contract credentials.":::

### PartnerSource Business Center account
You can use the following support plan incidents as part of your PartnerSource Business Center (PSBC) account if they exist: 

> [!NOTE]
> You can't use online support plans through the PSBC account.

-   Advanced support for partners on-premises incidents.
-   Advantage or Advantage + on-premises incidents.
-   Other pay per incident types of plans with an existing incident count in PSBC.

If you don't find the PartnerSource Business Center account, make sure that your sign in is added as a professional in your organization in PSBC. Make sure that you're signing in with the same Microsoft or work account authentication. This account is only applicable in an on-premises project.

:::image type="content" source="media/56c7bfd469f6d850d456e9e7a89e0d8d.png" alt-text="Screenshot of Add contract.":::

### Sign-in specific options
The following incidents and support benefits appear based on your sign in, if applicable:

-   MPN gold and silver incidents.
-   Signature cloud support.
-   Individual incidents and five packs purchased on [support.microsoft.com/supportforbusiness]. 

   > [!NOTE]
   > You must purchase incidents with a Microsoft account such as \@hotmail.com or \@outlook.com. Work or Microsoft Entra accounts can't have incidents tied to them.

### Tenant subscription
The following entitlements appear based on your subscription and ProDirect
purchases within your tenant organization:

-   Subscription
-   ProDirect

### Software assurance
The following entitlements can be added by linking a subscription number and contact email:

-   Software assurance

To add these entitlements, select **Add a Software Assurance plan** when you create the support incident. Enter the subscription number and the contact email, then select **Continue**.

:::image type="content" source="media/cd8f65a32c30722ea687dfbc5cc30874.png" alt-text="Screenshot of Software Assurance plan.":::
   
## Report production outage
For a quick and effective way to escalate issues to Microsoft Support when the services in a production environment are degraded or become unavailable, see [Report a production outage](report-production-outage.md).

## Phone support
Contact Support by following the steps in [Open a new incident](cloud-powered-support-lcs.md#open-a-new-incident). If you're unable to open a new incident in Lifecycle Services, phone support is available through [Premier phone support](https://support.microsoft.com/premier/contacts).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
