---
# required metadata

title: SPED fiscal files
description: This topic provides information on how to generate SPED fiscal export files for Brazil. 
author: ShylaThompson
manager: AnnBe
ms.date: 8/27/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# SPED fiscal files 

The Sistema Publico de Escrituração Digital (SPED) fiscal text files contain information about all fiscal documents that have been received and issued in a month for a specific fiscal establishment. The SPED system is used by federal tax authorities to verify Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) and Imposto sobre Produtos Industrializados (IPI) tax calculations. Before you can generate a SPED fiscal text file to submit to the federal tax authorities, you must specify parameters that define how the SPED fiscal text file will be saved. This topic explains how to specify these parameters by using the **SPED fiscal parameters** page. 

## Setup

1. Click **Fiscal books** \> **Setup** \> **Tax statements parameters**.
2. Select **SPED Fiscal**.
3. On the **Setup parameters** FastTab, click **Open**.
4. On the **SPED fiscal parameters** page, select the location where the SPED fiscal text file will be saved.
5. Select a profile presentation. For the current release, only the **A** profile presentation is supported.
6. Select the current version of the SPED fiscal text file format to generate.
7. Select the type of activity to include in the SPED fiscal text file. The following options are available:
    
      - **Industrial or equivalent** – Select this option to include information for activities related to industries, for example manufacturing of goods.
    
      - **Others** – Select this option for all other types of activities.
      
8. Set the **Enable block K** option to be **Yes**. If you don't enable block K, only the records K001 and K999 will be generated.
9. Set the **Enable production orders** option to be **Yes**. This option allows you to generate the records K230 and K235 from the manufacturing module. 

## Generate the SPED fiscal export file for a month 

The Sistema Publico de Escrituração Digital (SPED) fiscal text file provides information about fiscal documents that were received and issued during a specific month. This information is used by tax authorities. The SPED fiscal text file also includes information about tax assessments and payments during the month. This topic explains how to generate a SPED fiscal text file by using the **Booking period** list page.

1. Click **Fiscal books** \> **Common** \> **Booking period**.
2. Select a booking period.
3. On the **Action Pane**, click the **Tax statements** tab.
4. Click **SPED Fiscal**.
5. Specify the location and name of the file. The default location is specified on the **SPED fiscal parameters** page, and the default file name is automatically generated. In most cases, you should accept the default entry.
6. Select either **Original** or **Substitute** for the file type.
7. Select the version. The default entry is specified on the **SPED fiscal parameters** page.
8. Set the **Enable block K** option to be **Yes**. The default entry is specified on the **SPED fiscal parameters** page.
9. Optional: Click the **Run in the background** FastTab and specify options for batch processing. You might use batch processing if the file should be generated later or on a server instead of on your computer.
10. Click **OK**.
