---
title: SPED fiscal files
description: Learn how to set up and generate SPED fiscal export files for Brazil, including an outline and process on generating the SPED fiscal export file for a month.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
---

# SPED fiscal files

[!include [banner](../../includes/banner.md)]

The Sistema Publico de Escrituração Digital (SPED) fiscal text files contain information about all fiscal documents that a specific fiscal establishment receives and issues during a month. Federal tax authorities use the SPED system to verify tax calculations for Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) and Imposto sobre Produtos Industrializados (IPI).

## Setup

Before you can generate a SPED fiscal text file and submit it to the federal tax authorities, you must specify parameters that define how the system saves the SPED fiscal text file. This section explains how to specify these parameters on the **SPED fiscal parameters** page.

1. Select **Fiscal books** > **Setup** > **Tax statements parameters**.
1. Select **SPED Fiscal**, and then, on the **Setup parameters** FastTab, select **Open**.
1. On the **SPED fiscal parameters** page, select the location where you want to save the SPED fiscal text file.
1. Select a profile presentation. For the current release, only profile presentation **A** is supported.
1. Select the version of the SPED fiscal text file format to generate.
1. Select the type of activity to include in the SPED fiscal text file:

    - **Industrial or equivalent** – Include information for activities that are related to industries (for example, the manufacture of goods).
    - **Others** – Include information for all other types of activities.

1. Set the **Enable block K** option to **Yes**. If you don't enable block K, the system generates only records K001 and K999.
1. Set the **Enable production orders** option to **Yes**. This option lets you generate records K230 and K235 from the manufacturing module.

## Generate the SPED fiscal export file for a month

The SPED fiscal text file provides information about fiscal documents that you received and issued during a specific month. Tax authorities use this information. The SPED fiscal text file also includes information about tax assessments and payments during the month. This section explains how to generate a SPED fiscal text file by using the **Booking period** list page.

1. Select **Fiscal books** > **Common** > **Booking period**.
1. Select a booking period.
1. On the Action Pane, on the **Tax statements** tab, select **SPED Fiscal**.
1. Specify the location and name of the file. The default location appears on the **SPED fiscal parameters** page, and a default file name is automatically generated. In most cases, accept the default file name.
1. In the **File type** field, select either **Original** or **Substitute**.
1. Select the version. The default version appears on the **SPED fiscal parameters** page.
1. Set the **Enable block K** option to **Yes**. The default setting appears on the **SPED fiscal parameters** page.
1. (Optional) On the **Run in the background** FastTab, specify the options for batch processing. Use batch processing if you want to generate the file later or on a server instead of on your computer.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
