---
title: SSRS Reports/Services references configuration for Latin America
description: Learn how to configure the SSRS/Services references page, including prerequisites and process for setting up SSRS/Services references.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/02/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# SSRS Reports/Services references configuration for Latin America

[!include [banner](../../includes/banner.md)]

When you configure the **SSRS Reports/Services references** page, a relation is established between the output of a report and the specified execution format.

## Prerequisites

Before you complete the procedure in this article, import the required model mapping, model, and execution format from the Global repository. For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

## Set up SSRS/Services references

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **SSRS Reports/Services references**, and select **New** to create a configuration.
2. In the **General** section, in the **Report/Service Id** field, enter the ID that will be used to identify the report or service.
3. In the **Report/Service name** field, enter the name of the report or service.
4. In the **Settings** section, in the **Report/Service type** field, select the **ER Configuration** option for accounting reports.
5. For invoice layouts, select **Service**.
6. In the **Model mapping name** field, select the model mapping name that corresponds to the report that you want to configure.
7. In the **Data model definition** field, select the value that corresponds to the configured mapping.
8. In the **Format mapping** field, select a format.
9. Enable the **Report service type** option according to the report type.
10. In the **Parameters** section, add a name and value to identify each report, if necessary. Then save your changes.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
