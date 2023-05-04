---
title: Troubleshoot Store Commerce sign-in issues
description: This article explains how to troubleshoot sign-in issues in the Microsoft Dynamics 365 Commerce Store Commerce app.
author: josaw1
ms.date: 01/31/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2023-01-06
---

# Troubleshoot Store Commerce sign-in issues

[!include [banner](../includes/banner.md)]

This article explains how to troubleshoot sign-in issues in the Microsoft Dynamics 365 Commerce Store Commerce app.

## Description

After you enter employee credentials on a point of sale (POS) sign-in screen, you might receive an error message that resembles the following example:

> Audience validation failed. Contact your system administrator to properly configure identity providers in Commerce headquarters.

## Resolutions

### POS application is configured to use the personal ID and password sign-in authentication method

If the POS application is configured to use the personal ID and password sign-in authentication method, follow these steps.

1. In Commerce headquarters, go to **Commerce shared parameters \> Identity Providers**. 
1. For the **Commerce Identity Provider** identity provider issuer, in the **Relying parties** section, ensure that the **Cloud POS** and **Modern POS** records are correctly configured.

### POS application is configured to use the Azure Active Directory sign-in authentication method

If the POS application is configured to use the Azure Active Directory (Azure AD) sign-in authentication method, follow these steps.

1. In Commerce headquarters, go to **Commerce shared parameters \> Identity Providers**.
1. For identity provider issuers of the **Azure Active Directory** type, in the **Relying parties** and **Server resource IDs** sections, ensure that the records are correctly configured.

For detailed configuration steps, see [Update identity providers settings in Commerce headquarters](../cpos-custom-aad.md#update-identity-providers-settings-in-commerce-headquarters).
