---
title: SPED fiscal files
description: Learn how to set up and generate SPED fiscal export files for Brazil, including an outline and process on generating the SPED fiscal export file for a month.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# SPED fiscal files 

[!include [banner](../../includes/banner.md)]

Sistema Publico de Escrituração Digital (SPED) fiscal text files contain information about all fiscal documents that have been received and issued for a specific fiscal establishment during a month. Federal tax authorities use the SPED system to verify tax calculations for Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) and Imposto sobre Produtos Industrializados (IPI).

## Setup

Before you can generate a SPED fiscal text file and submit it to the federal tax authorities, you must specify parameters that define how the SPED fiscal text file will be saved. This section explains how to specify these parameters on the **SPED fiscal parameters** page.

1. Select **Fiscal books** \> **Setup** \> **Tax statements parameters**.
2. Select **SPED Fiscal**, and then, on the **Setup parameters** FastTab, select **Open**.
4. On the **SPED fiscal parameters** page, select the location where the SPED fiscal text file should be saved.
5. Select a profile presentation. For the current release, only profile presentation **A** is supported.
6. Select the version of the SPED fiscal text file format to generate.
7. Select the type of activity to include in the SPED fiscal text file:

    - **Industrial or equivalent** – Include information for activities that are related to industries (for example, the manufacture of goods).
    - **Others** – Include information for all other types of activities.

8. Set the **Enable block K** option to **Yes**. If you don't enable block K, only records K001 and K999 will be generated.
9. Set the **Enable production orders** option to **Yes**. This option lets you generate records K230 and K235 from the manufacturing module. 

## Generate the SPED fiscal export file for a month 

The SPED fiscal text file provides information about fiscal documents that were received and issued during a specific month. This information is used by tax authorities. The SPED fiscal text file also includes information about tax assessments and payments during the month. This section explains how to generate a SPED fiscal text file by using the **Booking period** list page.

1. Select **Fiscal books** \> **Common** \> **Booking period**.
2. Select a booking period.
3. On the Action Pane, on the **Tax statements** tab, select **SPED Fiscal**.
4. Specify the location and name of the file. The default location is specified on the **SPED fiscal parameters** page, and a default file name is automatically generated. In most cases, you should accept the default file name.
5. In the **File type** field, select either **Original** or **Substitute**.
6. Select the version. The default version is specified on the **SPED fiscal parameters** page.
7. Set the **Enable block K** option to **Yes**. The default setting is specified on the **SPED fiscal parameters** page.
8. Optional: On the **Run in the background** FastTab, specify the options for batch processing. You might use batch processing if the file should be generated later or on a server instead of on your computer.
9. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
