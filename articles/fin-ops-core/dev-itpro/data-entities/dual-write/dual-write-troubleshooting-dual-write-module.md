---
# required metadata

title: Troubleshoot issues with the dual-write module in Finance and Operations apps
description: This topic provides troubleshooting information that can help you fix issues with the Dual-write module in Finance and Operations apps.
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

# Troubleshoot issues with the dual-write module in Finance and Operations apps

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service. Specifically, it provides information that can help you fix issues with the **Dual-write** module in Finance and Operations apps.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## You can't load the dual-write module in a Finance and Operations app

If you can't open the **Dual-write** page by selecting the **Dual Write** tile in the **Data management** workspace, the data integration service is probably down. Create a support ticket to request a restart of the data integration service.

## Error when you try to create a new entity map

**Required credentials to fix the issue:** The same user that setup dual-write.

You might receive the following error message when you try to configure a new entity for dual-write. The only user that can create a map is the user who setup the dual-write connection.

*Response status code does not indicate success: 401 (Unauthorized)*


## Error when you open the dual-write user interface

You might receive the following error message when you try to access dual-write from the **Data management** workspace:

*login.microsoftonline.com refused to connect.*

To fix the issue, sign in by using an InPrivate window in Microsoft Edge, an incognito window in Chromium, or an incognito window in Google Chrome. You must also unblock or clear third-party cookies.

## Error when you link the environment for dual-write or add a new entity mapping

**Required role to fix the issue:** System administrator in both Finance and Operations apps and Common Data Service.

You might encounter the following error when linking or creating maps:

*Response status code does not indicate success: 403 (tokenexchange).<br>
Session ID: \<your session id\><br>
Root activity ID: \<your root activity id\>*

This error can occur if you don't have sufficient permissions to link dual-write or create maps. This error can also occur if the Common Data Service environment was reset without unlinking dual-write. Any user with system administrator role in both Finance and Operations apps and Common Data Service can link the environments. Only the user who setup the dual-write connection can add new entity maps. After setup, any user with system administrator role can monitor the status and edit the mappings.

## Error when you stop the entity mapping

You might receive the following error message when you try to stop the entity mappings:

*\[Forbidden\], \[{"status":403,"source":"","message":"Error from token exchange:
User is not allowed to access connection
dynamicscrmonline/xxxxxx-xxxx-xxxx-xxxxxxxx"}\], The remote server returned an
error: (403) Forbidden.*

This error occurs when the linked Common Data Service environment isn't available.

To fix the issue, create a ticket for the Data Integration team. Attach the network trace so that the Data Integration team can mark the maps as **Not running** in the back end.

> [!Note] 
> You will not run into this error once we enable force unlinking which should be available soon.

## Error while trying to start an entity mapping

You might receive an error like the following when you try to set that state of a mapping to **Running**:

*Unable to complete initial data sync. Error: dual-write failure - plugin registration failed: Unable to build dual-write lookup metadata. Error object reference not set to an instance of an object.*

The fix for this error depends on the cause of the error:

+ If the mapping has dependent mappings, then make sure to enable the dependent mappings of this entity mapping.
+ The mapping might be missing source or destination fields. If a field in the Finance and Operations app is missing, then follow the steps in the section [Missing entity fields issue on maps](dual-write-troubleshooting-finops-upgrades#missing-entity-fields-issue-on-maps). If a field in Common Data Service is missing, then click **Refresh entities** button on the mapping so that the fields are automatically populated back into the mapping.
