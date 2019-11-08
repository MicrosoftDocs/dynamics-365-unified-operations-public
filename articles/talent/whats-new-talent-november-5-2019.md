---
# required metadata

title: What's new or changed in Dynamics 365 Talent (November 5, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 11/5/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-11-05
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (November 5, 2019)

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2598.

### Copy a Core HR instance

In this week's release, you can use Microsoft Dynamics Lifecycle Services (LCS) to copy a Microsoft Dynamics 365 Talent: Core HR database to a sandbox environment. If you have another sandbox environment, you can also copy the database from that environment to a targeted sandbox environment. #

### CDS Integration batch jobs are not created when CDS integration is enabled.

This change will create batch jobs for when CDS integration is enabled.

### HcmPersonImageEntity do not resize the person image when uploaded - (369469)

This week's release, changes how Images, when imported through data management are resized for better performance.

### Positions available for assignment date can be earlier than its activation date - (340103)

With this change a warning will be presented if you select an available for assignment date that precedes the the positions activation date.

### Can't create a compensation change request in ESS for Step Based plans - (376872)

This release corrects and issue when requesting compensation changes through Employee Self-Service for step based plans. 

### Reason Code does not sync to CDS if description is longer than 30 characters, CoreHR allows 60 - (352682)

with this change, reason codes with more than 30 characters will be updated in CDS. Changes made in CDS will also be reflected back in Talent.

### Address Integration from Talent to F&O - (351961)

This release fixes an issue where addresses updated in Talent were not updating in Finance and Operations. Changes to address blocks will now update.

## Coming soon

### Print performance reviews

With this new functionality: Employees, managers, and HR will be able to print an employee's performance review. Performance reviews will be available using a "Print review" option that will launch Microsoft Word to view and print the performance review.

### Feature management workspace

Features are added and updated in every release. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them

To learn more about the changes coming with feature management view the article posted [HERE](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
