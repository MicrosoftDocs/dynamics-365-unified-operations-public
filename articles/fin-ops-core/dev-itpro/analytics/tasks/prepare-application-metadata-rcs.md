---
title: Prepare application metadata to be used in RCS
description: This article describes how to create a new reporting configuration that contains application metadata.
author: kfend
ms.date: 04/09/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---

# Prepare application metadata to use in RCS

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains application metadata for designing ER model mapping configurations in Regulatory configuration service (RCS). Use this configuration to design a sample ER model mapping configuration to access foreign trade transactions. In this example, you create a configuration for sample company, Litware, Inc. You can perform these steps in any company. To complete these steps, you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).

## Prerequisites

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).
1. Select **Metadata configurations**.
1. Assume that RCS is used to design an ER solution for a Finance and Operation application that generates electronic documents that contain information from the foreign trade business domain. To specify the mapping between the ER data model and sources of required data, RCS needs access to metadata of the Finance and Operation application. Therefore, as part of designing the ER solution, you configure a new ER metadata configuration containing all metadata that is currently required for generating ER reports for the selected business domain.

## Add metadata configuration

1. Select **Create configuration** to open the form.
1. In the **Name** field, enter *Foreign trade metadata*.
1. Select **Create configuration**.
1. Select **Designer**.
1. Select **Add**.
  
> [!NOTE]
> You can select all metadata for the entire application or selected models or selected modules. When you choose this option, the following metadata is automatically added: tables of records, enumerations, and extended data types. If you need other types of metadata, add them manually.

You can add foreign trade transaction-related metadata by selecting metadata items manually.
  
1. Select **Add data source**.
1. Select **Table records**.
1. Use the Quick Filter to filter on the **Name** field with a value of *Intrastat*.
1. Select the **Intrastat** table record.
1. Select **OK**.
  
You added metadata information about the Intrastat table of records.
  
1. In the tree, expand **Table records Intrastat** > **Relations**.
1. In the tree, select **Table records Intrastat** > **Relations** > **IntrastatCommodity (Table records EcoResCategory)**.
1. Select **Add metadata**.
  
> [!NOTE]
> You must add metadata about required relations for selected table of records manually.
  
1. Select **Add data source**.
1. Select **Enumeration**.
1. Use the Quick Filter to filter on the **Name** field with a value of *IntrastatDirection*.
1. Select the **IntrastatDirection enumeration** record.
1. Select **OK**.
1. Select **Save**.  
1. Close the page.
  
## Complete the draft version of metadata configuration

1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.
1. Select version **1**.
  
## Export the completed version of metadata configuration from application as XML file

1. Select **Exchange**.
1. Select **Export as XML file**.
1. Select **OK**.

The created ER metadata configuration is saved as an XML file. You can import this file to RCS and use it as the source of information about metadata for the foreign trade business domain. Based on this information, you can specify the mapping between application metadata and ER data model.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
