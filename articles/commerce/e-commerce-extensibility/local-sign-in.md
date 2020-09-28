---
# required metadata

title: Mocking signed in state during local development
description: 
author: samjarawan
manager: annbe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Mocking signed in state during local development

[!include [banner](../includes/banner.md)]

This topic describes how to

## Overview

Over the course of developing your e-Commerce online site, it may become necessary to develop and test scenarios for signed in users. Rather then publishing these pages and testing against live pages you can instead mock the signed in state when running in developer mode.
 
To take advantage of this feature, you will need to perform a one time setup in your Azure AD B2C tenant to allow you to mock the signed in user status.

## Configuring your Azure B2C Tenant
 
The first step is to create a new ROPC (resource owner password credentials) flow in your Azure AD B2C tenant. To proceed with the following steps you will need to be signed in with user that has global administrator privileges.
 
1.	Sign in to the [Azure portal](https://ms.portal.azure.com/) as the global administrator of your Azure AD B2C tenant.
1.	Click **User flows**, and select **New user flow**.
1.	Click the **All** tab and select **Sign in using ROPC**.
1.	Provide a name for the user flow, such as ROPC_Auth. Copy the full name and save it, as this information as it will later be used as `ropcUserFlowName`  in your credentials.json file.
1.	Under **Application claims**, click **Show more**.
1.	Select the application **"Display Name"**, **"Email Addresses"**,**"Given Name"**, **"Identity provider"**, **"SurName"**, **"User’s object ID"** claims.
1.	Select **OK**, and then select **Create**.
1.	Select **Run user flow**.


You will then see an endpoint such as this example: ```https://<b2cTenant>.b2clogin.com/<loginDomain>/v2.0/.well-known/openid-configuration?p=B2C_1_ROPC_Auth```


