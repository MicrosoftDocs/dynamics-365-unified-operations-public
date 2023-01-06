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

## The audience validation failed

After you enter the valid Cloud Point of Sale (CPOS) staff id and password or enter a AAD user account, you might receive error message that resembles the following example:

> Audience validation failed. Contact your system administrator to properly configure identity providers in Commerce headquarters.

In this case, 

If you are using Personnel ID and Password logon, make sure relying parties are correctly configured.

If you are using Azure AD logon, make sure both relying parties and server resource ids are correctly configured. For more information about detailed config steps, see [Update identity providers settings in Commerce headquarters](../cpos-custom-aad.md#update-identity-providers-settings-in-commerce-headquarters).