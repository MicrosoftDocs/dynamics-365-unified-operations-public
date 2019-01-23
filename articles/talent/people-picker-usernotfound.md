---
# required metadata

title: User not found in People Picker in Attract or Onboard
description: This topic explains what to do when users in the company tenant isn't showing up in the people picker in Attract or Onboard applications
author: ChrisChua
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
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chrichua
ms.search.validFrom: 2019-01-22
ms.dyn365.ops.version: Talent

---

# Azure Active Directory Users not found in People Picker

[!include [banner](includes/banner.md)]

**Issue**

Certain valid users in Azure Active Directory for the tenant do not appear when searching for name in the people picker.

**Cause**

Certain user types are not supported in Attract and Onboard applications currently. Please verify that the user is not an AAD B2B Guest user. User Type information can be found in the Azure Active Directory blade on the Azure portal.

For more information about Azure B2B - https://docs.microsoft.com/en-us/azure/active-directory/b2b/what-is-b2b

For non-B2B users, there are certain users who may have incomplete User Type property on the User object. This can be verified and fixed using the AzureAD Powershell module - https://docs.microsoft.com/en-us/powershell/module/azuread/?view=azureadps-2.0

**Resolution**

To perform the following resolution steps, you will need to have Global Administrator permissions on the Azure Active Directory tenant or permissions for User.ReadWrite.All

Please verify the User Type for the affected user:

```
PS C:\>Get-AzureADUser -ObjectId "testUpn@tenant.com"
```
The command returns the following information:
```
ObjectId                             DisplayName UserPrincipalName      UserType
--------                             ----------- -----------------      --------
5e8b0f4d-2cd4-4e17-9467-b0f6a5c0c4d0 New user    testUpn@tenant.com     
```
Note the UserType property on the user. If the UserType is blank, i.e. not "Member" or "Guest", please update the UserType using the following command:

```
PS C:\>Set-AzureADUser -ObjectId "testUpn@tenant.com" -UserType Member
```

