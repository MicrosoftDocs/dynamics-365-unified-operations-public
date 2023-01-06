---
title: Troubleshoot Store Commerce logon issues
description: This article explains how to troubleshoot logon issues in the Microsoft Dynamics 365 Commerce Store Commerce app.
author: josaw1
ms.date: 01/06/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2023-01-06
---

# Troubleshoot Store Commerce logon issues

[!include [banner](../includes/banner.md)]

This article explains how to troubleshoot logon issues in the Microsoft Dynamics 365 Commerce Store Commerce app.

## Audience validation failed

After entering the employee credentials on point of sale (POS) sign-in screen, you might receive error message that resembles the following example:

> Audience validation failed. Contact your system administrator to properly configure identity providers in Commerce headquarters.

In this case, 

If the POS application is configured to use **Personal ID and Password** logon authentication method, please go to **Commerce shared parameters** > **Identity providers**, for the identity provider issuer named **Commerce Identity Provider**, make sure the **Relying parties** section has **Cloud POS** and **Modern POS** records correctly configured.

If the POS application is configured to use **Azure AD** logon authentication method, please go to **Commerce shared parameters** > **Identity providers**, for the identity provider issuers with type **Azure Active Directory**, make sure the **Relying parties** and **Server resource IDs** are correctly configured. For more information about detailed configuration steps, see [Update identity providers settings in Commerce headquarters](../cpos-custom-aad.md#update-identity-providers-settings-in-commerce-headquarters).