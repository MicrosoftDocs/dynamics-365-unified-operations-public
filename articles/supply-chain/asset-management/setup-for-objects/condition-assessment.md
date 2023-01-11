---
# required metadata

title: Condition assessment
description: This article explains how to create a condition assessment template and registration on an asset in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetObjectCondition, EntAssetConditionTemplate 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Condition assessment

[!include [banner](../../includes/banner.md)]

 

This article explains how to create a condition assessment template and registration on an asset in Asset Management. Condition assessment is performed at regular intervals, and the primary objective is to create and maintain condition data on assets. Seen from a preventive maintenance perspective, it is important to monitor key information such as current condition, and remaining life span. Furthermore, if you carry out condition assessment at regular intervals, you will be able to monitor and compare conditions on the machinery in your factory.

Condition assessment can be used to measure and monitor many conditions on your equipment. Example: You could measure vibrations on your machinery. After you have registered vibration measurements in Asset Management on various types of equipment, you can search for the latest registered assessment and view vibration measurements.

Condition assessment is created on assets. You set up a condition assessment template on an asset type before you carry out the condition assessment procedure. The reason for using templates for condition assessment is to avoid variation of condition data on similar assets. The sequence for setting up and using condition assessment in Asset Management is: First you set up the required condition assessment templates. Next, you associate templates with asset types in the **Asset types** form. Finally, you can create condition assessment registrations on an asset in the **Asset** form.

## Create a condition assessment template

1. Select **Asset management** > **Setup** > **Asset types** > **Condition assessment**.
2. Select **New** to create a new template.
3. Insert and ID for the template in the **Template** field.
4. Insert a name for the template in the **Name** field.
5. On the **Condition assessment lines** FastFab, add the lines required for the condition assessment, including selection of the appropriate condition type and measurement unit.
6. On the **Asset types** FastTab, add the asset types that should use the condition assessment template.
7. In the **Lines** and **Asset types** fields in the **Details** group at the top of the screen, you will see the number of assessment lines and asset types related to the selected condition assessment template.


## Create condition assessment registration on an asset

1. Select **Asset management** > **Assets** > **All Assets**.
2. In the list, select the asset for which you want to create a condition assessment registration.
3. On the **General** tab, click **Condition assessment**.
4. Click **New** to make a new registration.
5. Select the date for the condition assessment in the **Date** field.
6. Select the name of the worker who carried out the assessment registration in the **Worker** field.
7. In the **Lines** field, you see the number of assessment lines set up on the condition assessment.
8. Select a template for the condition assessment in the **Template** field. The name of the template is automatically inserted in the **Name** field, and the related registration lines are inserted on the **Condition assessment lines** FastTab.
9. You can insert notes relating to the selected condition assessment on the **Notes** FastTab.
10. For each condition assessment line, insert measurement data in the **Value** field.
11. You can insert a comment relating to the selected registration line on the **Condition assessment lines** FastTab > **Comments** field. If you add a comment on a line, the **Comment** check box is automatically selected.

After you have made a condition assessment registration on an asset, you can print a condition assessment report.

>[!NOTE]
>You can also register condition assessment on a work order (**Asset management** > **Work orders** > **All Work orders** > **Condition assessment** button.)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]