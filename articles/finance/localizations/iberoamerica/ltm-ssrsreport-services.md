---
title: SSRS Reports/Services references configuration for Latin America
description: This article explains how to configure the SSRS/Services references page. 
author: Fhernandez0088
ms.date: 10/02/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# SSRS Reports/Services references configuration for Latin America
[!include [banner](../includes/banner.md)]

When you configure the **SSRS Reports/Services references** page, a relation between the output of a report and the execution format specified is established.

## Prerequisites
Before you complete the tasks in this article, import the model mapping, model, and execution format needed to configure from the **Global** repository. For more information, see [Download ER Configuration](../../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

## Set up SSRS/Services references 
1. Go to **Organization administration** > **Setup** > **LATAM>SSRS Reports/Services references** and select **New** to create a new configuration.
2. In **General** section, in the **Report/Service Id** field, enter the ID that will be used to identify the report or service.
3. In the **Report/Service name** field, nter the name of the report or service. 
4. In **Settings** section, in the **Report/Service type** field, select the ER Configuration option for accounting reports.
5. For invoice layouts, select **Service**.
6. In the **Model mapping name** field, select the model mapping name that corresponds to the report you want to configure.
7. In the **Data model definition** field, select the value that corresponds to the configured mapping.
8. In the **Format mapping** field, select a format..
9. Move the **Report service type** slider to active according to the report type.
10. In **Parameters** section, add the name and value to identify each report if necessary and then save your changes.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
