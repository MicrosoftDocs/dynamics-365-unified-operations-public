---
# required metadata

title: What's new or changed in Dynamics 365 Talent (October 23, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 10/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
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
ms.author: dkrame
ms.search.validFrom: 2019-10-23
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 Talent (October 23, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2569.

### Platform 30 Update

See more information about platform update [HERE](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/whats-new-platform-update-30).

### Remove benefits open enrollment preview feature

The preview option for benefits open enrollment has been removed. In conjunction with our strategic investment announcement [here](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/10/02/strategic-investments-in-core-hr-drive-operational-excellence/) in core HR we have removed the benefits open enrollment feature in its current state and how it evolves going forward. We will look to launch a new open enrollment experience as part of the recently announced Advanced Benefits functionality.

### While selecting the country/region on the worker form for the second time, System throws error message (350294)

With this weeks release, The issue has been corrected when selecting a country/region on the Worker form.

### Financial dimension values default to the Combination display field when "Do not allow manual entry" is set to true (340097)

With this change, when setting up financial dimensions and using the option to not allow manual entry, the system will correctly default the dimension value into the "Combination display" field.

### New relationship types should be added to Relationship lookup in the personal contacts form (347691)

This release includes new capabilities to add new relationship types in the relationship types table and reflect those changes in the relationship lookup for personal contacts.

### When adding additional list values to custom fields they are not reflected in CDS (379599)

With this week's release, adding a new list values to an existing custom fields already sync'ed with CDS, the new pick list values will now appear after applying changes to the entity.

### From Terms of employment page when selecting ‘Open in excel’ user all employees terms are displayed (348073)

With this release, only the selected employees terms of employment will open in excel. All company security is also honored.

### Association between work calendar holiday entity and work calendar entity is missing in CDS - (324178)

This relationship has been added with the release. This change will enable working days of an employee to display in PowerApps. 

### Employee self-service Workflows with configurable hierarchy stops with Error (370132)

In this release, better messaging is available on how to configure workflows using configurable hierarchies. 

### System allows creation of new positions that have available for assignment date earlier than the activation date (340103)

This change will display a warning when the available for assignment date is set to a value that is prior to the positions activation date.

## Coming soon

### Print performance reviews

With this new functionality: Employees, managers, and HR will be able to print an employee's performance review. Performance reviews will be available using a "Print review" option that will launch Microsoft Word to view and print the performance review.

### Feature management workspace

Features are added and updated in every release. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them

To learn more about the changes coming with feature management view the article posted [HERE](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
