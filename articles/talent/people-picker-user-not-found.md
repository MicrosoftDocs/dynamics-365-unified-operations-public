---
# required metadata

title: User not found in People Picker in Attract or Onboard
description: This topic explains what to do when users in the company tenant aren't showing up in the People Picker in Dynamics 365 Talent - Attract or Onboard.
author: andreabichsel
manager: AnnBe
ms.date: 01/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-01-22
ms.dyn365.ops.version: Talent

---

# User not found in People Picker in Attract or Onboard

[!include [banner](includes/banner.md)]

## Issue

Certain valid users in Microsoft Azure Active Directory (Azure AD) for the tenant do not appear when searching for the name in the People Picker in Dynamics 365 Talent: Attract or Dynamics 365 Talent: Onboard.

## Cause

Certain user types are not currently supported in Attract and Onboard. Verify that the user is not an Azure AD Business to Business (B2B) guest user. "User Type" information can be found in the Azure Active Directory blade on the Azure portal.

For more information about Azure B2B, see [What is guest user access in Azure Active Directory B2B](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b).

For non-B2B users, there are certain users who may have an incomplete "User Type" property on the **User** object. This can be verified and fixed using the Azure AD Powershell module. For more information, see [Azure AD](https://docs.microsoft.com/powershell/module/azuread/?view=azureadps-2.0).

## Resolution

To complete the following steps to resolve the issue, you will need to have "Global Administrator" permissions on the Azure Active Directory tenant or permissions for **User.ReadWrite.All**.

To verify the "User Type" for the affected user.

```
PS C:\>Get-AzureADUser -ObjectId "testUpn@tenant.com"
```
The command returns the following information.
```
ObjectId                             DisplayName UserPrincipalName      UserType
--------                             ----------- -----------------      --------
5e8b0f4d-2cd4-4e17-9467-b0f6a5c0c4d0 New user    testUpn@tenant.com     
```
Note the **UserType** property on the user. If the **UserType** is blank, for example not "Member" or "Guest", update the **UserType** using the following command.

```
PS C:\>Set-AzureADUser -ObjectId "testUpn@tenant.com" -UserType Member
```
