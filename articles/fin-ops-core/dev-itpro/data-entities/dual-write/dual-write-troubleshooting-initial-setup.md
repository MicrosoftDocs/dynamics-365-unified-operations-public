---
# required metadata

title: Troubleshoot issues during initial setup
description: This topic provides troubleshooting information that can help you fix issues that might occur during the initial setup of dual-write integration between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# Troubleshoot issues during initial setup

[!include [banner](../../includes/banner.md)]



This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service. Specifically, it provides information that can help you fix issues that might occur during the initial setup of dual-write integration.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## You can't link a Finance and Operations app to Common Data Service

**Required role to set up dual-write:** System Administrator in Finance and Operations apps and Common Data Service.

Errors on the **Setup link to Common Data Service** page are usually caused by incomplete setup or permissions issues. Make sure that the whole health check passes on the **Setup link to Common Data Service** page, as shown in the following illustration. You can't link dual-write unless the whole health check passes.

![Successful health check](media/health_check.png)

You must have Azure AD tenant admin credentials to link the Finance and Operations and Common Data Service environments. After you link the environments, users can sign in by using their account credentials and update an existing entity map.

## Error when you open the Link to Common Data Service page

**Required credentials to fix the issue:** Azure AD tenant admin

You might receive the following error message when you open the **Link to Common Data Service** page in a Finance and Operations app:

*Response status code does not indicate success: 404 (Not Found).*

This error occurs when the consent step hasn't been completed. To validate whether the consent step has been completed, sign in to portal.Azure.com by using the Azure AD tenant admin account, and see whether the third-party app that has the ID **33976c19-1db5-4c02-810e-c243db79efde** appears in the Azure AD **Enterprise applications** list. If it doesn't, you must provide app consent.

To provide app consent, follow these steps.

1. Open the following URL by using your admin credentials. You should be prompted for consent.

    <https://login.microsoftonline.com/common/oauth2/authorize?client_id=33976c19-1db5-4c02-810e-c243db79efde&response_type=code&prompt=admin_consent>

2. Select **Accept** to indicate that you're giving your consent to install the app that has the ID **33976c19-1db5-4c02-810e-c243db79efde** in your tenant.

    > [!TIP]
    > This app is required to link Common Data Service and Finance and Operations apps. If you have trouble with this step, open your browser in incognito mode (in Google Chrome) or InPrivate mode (in Microsoft Edge).

## Verify that company data and dual-write teams are set up correctly during linking

To ensure that dual-write works correctly, the companies that you select during configuration are created in the Common Data Service environment. By default, these companies are read-only, and the **IsDualWriteEnable** property is set to **True**. In addition, the default owning business unit owner and team are created and include the company name. Before you enable the maps, verify that the default team owner is specified. To find the **Companies (CDM\_Company)** entity, follow these steps.

1. In the model-driven app in Dynamics 365, select the filter in the upper-right corner.
2. In the drop-down list, select **Company**.
3. Select **Run** to see the results.
4. Select the company that was linked when you configured dual-write.
5. Verify that the **Default owning team** field has a value. In the following illustration, the **Default owning team** field is set to **USMF Dual Write**.

    ![Verifying the default owning team](media/default_owning_team.png)

## Find the limit on the number of legal entities or companies that can be linked for dual-write

You might receive the following error message when you try to enable maps:

*Dual write failure - Plugin registration failed: \[(Unable to get partition map
for project
DWM-1ae35e60-4bc2-4905-88ea-69efd3b29260-7f12cb89-1550-42e2-858e-4761fc1443ea.
Error Exceeds the maximum partitions allowed for mapping
DWM-1ae35e60-4bc2-4905-88ea-69efd3b29260-7f12cb89-1550-42e2-858e-4761fc1443ea)\],
One or more errors occurred.*

The current limit when you link the environments is approximately 40 legal entities. This error occurs if you try to enable maps, and more than 40 legal entities are linked between the environments.
