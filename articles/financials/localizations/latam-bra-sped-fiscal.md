---
# required metadata

title: SPED fiscal files
description: This topic provides information on how to generate SPED fiscal export files for Brazil. 
author: ShylaThompson
manager: AnnBe
ms.date: 6/5/2018
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

# Set up parameters for SPED fiscal text files 

The Sistema Publico de Escrituração Digital (SPED) fiscal text files contain information about all fiscal documents that have been received and issued in a month for a specific fiscal establishment. The SPED system is used by federal tax authorities to verify Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) and Imposto sobre Produtos Industrializados (IPI) tax calculations. Before you can generate a SPED fiscal text file to submit to the federal tax authorities, you must specify parameters that define how the SPED fiscal text file will be saved. This topic explains how to specify these parameters by using the **SPED fiscal parameters** form. 


> [!NOTE]
> The procedure for completing this task has changed for Microsoft Dynamics AX 2012 R3. For information that is specific to Microsoft Dynamics AX 2012 R3, see the section later in this topic.



## Set up requirements for SPED fiscal text files

1.  Click **Fiscal books** \> **Setup** \> **Tax statements parameters**. Select **SPED Fiscal**, on the **Setup parameters** FastTab, click **Open**.

2.  In the **SPED fiscal parameters** form, select the location where the SPED fiscal text file will be saved.

3.  Select a profile presentation. For the current release, only the **A** profile presentation is supported.

4.  Select **1.06** or **1.07** as the version of the SPED fiscal text file format to generate.
    

    > [!NOTE]
    > To generate the SPED fiscal text file for the year 2013, select <STRONG>1.06</STRONG>. To generate the SPED fiscal text file for the year 2014, select <STRONG>1.07</STRONG>.



5.  Select the type of activity to include in the SPED fiscal text file. The following options are available:
    
      - **Industrial or equivalent** – Select this option to include information for activities related to industries, for example manufacturing of goods.
    
      - **Others** – Select this option for all other types of activities.

# Generate the SPED fiscal export file for a month 

The Sistema Publico de Escrituração Digital (SPED) fiscal text file provides information about fiscal documents that were received and issued during a specific month. This information is used by tax authorities. The SPED fiscal text file also includes information about tax assessments and payments during the month. This topic explains how to generate a SPED fiscal text file by using the **Booking period** list page.


> [!NOTE]
> The procedure for completing this task has changed for Microsoft Dynamics AX 2012 R3. For information that is specific to Microsoft Dynamics AX 2012 R3, see the section later in this topic.



## Generate the SPED fiscal text file for a month

1.  Click **Fiscal books** \> **Common** \> **Booking period**. On the **Action Pane**, click the **Tax statements** tab.

2.  Select a booking period, and then click **SPED Fiscal**.

3.  Specify the location and name of the file. The default location is specified in the **SPED fiscal parameters** form, and the default file name is automatically generated. In most cases, you should accept the default entry.

4.  Select either **Original** or **Substitute** for the file type.

5.  Select the version. The default entry is specified in the **SPED fiscal parameters** form.

6.  Optional: Click the **Batch** tab and specify options for batch processing. You might use batch processing if the file should be generated later or on a server instead of on your computer.

7.  Click **OK**.
