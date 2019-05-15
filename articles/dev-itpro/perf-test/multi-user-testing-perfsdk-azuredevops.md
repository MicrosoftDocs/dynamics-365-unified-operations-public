---
# required metadata

title: Multi-user testing with Performance SDK and Azure DevOps
description: This topic provides information about how to complete multi-user testing by using the Performance SDK and Azure DevOps with performance test scripts generated from Task recroder. 
author: hasaid
manager: AnnBe
ms.date: 05/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 9954
ms.assetid: 7b605810-e4da-4eb8-9a26-5389f99befcf
ms.search.region: Global
# ms.search.industry: 
ms.author: jujoh
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Multi-user testing with Performance SDK and Azure DevOps
[!include [banner](../includes/banner.md)]

Prerequisites

- A Dynamics 365 for Finance and Operations development environment with Platform Update 21 or above in own your Azure subscription
- Visual Studio 2015 Enterprise edition in development environment
- A tier 2 or above sandbox with the same release (App + PU) as your development environment
- You have completed all steps in Single user testing with Task recorder and Performance SDK  and all steps in Multi-user testing with Performance SDK and local test controller  except for step “Run multi-user testing with local test controller”

## Prepare PerfSDKSample solution for multi-user testing

1. Connect Visual Studio in development environment to an Azure DevOps project
 
 [![Connect to Team Foundation Server window](./media/perfsdk-azuredevops-01.png)](./media/perfsdk-azuredevops-01.png)
 
  > [!NOTE]
  > When add Azure DevOps server, please use https://<YourAzureDevOpsAccount>.visualstudio.com

2. Go to your Azure DevOps project dashboard, click Open in Visual Studio and click on Allow in prompted window. After Visual Studio opened and if it’s not running under administrator you need to re-open it as administrator

  [![Azure Project dashboard](./media/perfsdk-azuredevops-02.png)](./media/perfsdk-azuredevops-02.png)
 
3. Change vsonline.testsettings for Azure DevOps
4. Select Run tests using Visual Studio Team Services in General tab

  [![Select Run tests using Visual Studio Team Services](./media/perfsdk-azuredevops-03.png)](./media/perfsdk-azuredevops-03.png)
  
5. Keep Deployment tab as it is in Multi-user testing with Performance SDK and local test controller 

  [![Deployment tab](./media/perfsdk-azuredevops-04.png)](./media/perfsdk-azuredevops-04.png)
  
6. Point Setup script in Setup and Cleanup Scripts tab to setup.cmd under Visual Studio Online folder

  [![Setup and Cleanup Scripts tab](./media/perfsdk-azuredevops-05.png)](./media/perfsdk-azuredevops-05.png)

7. Keep Additional Settings as it is in Multi-user testing with Performance SDK and local test controller 

  [![Additional settings tab](./media/perfsdk-azuredevops-06.png)](./media/perfsdk-azuredevops-06.png)

8. Click on Apply and Close

## Run multi-user testing with Azure DevOps

1.	Open SampleLoadTest.loadtest
2.	Click on Run Load Test
 
 [![Run Load Test menu option](./media/perfsdk-azuredevops-07.png)](./media/perfsdk-azuredevops-07.png)
 
 [![SampleLoadTestLoadTest progress chart](./media/perfsdk-azuredevops-08.png)](./media/perfsdk-azuredevops-08.png)
 
 [![SampleLoadTestLoadTest progress chart continued](./media/perfsdk-azuredevops-09.png)](./media/perfsdk-azuredevops-09.png)

3.	Review the test output

   [![Test output screen 1](./media/perfsdk-azuredevops-10.png)](./media/perfsdk-azuredevops-10.png)
   
   [![Test output screen 2](./media/perfsdk-azuredevops-11.png)](./media/perfsdk-azuredevops-11.png)
    
   [![Test output screen 3](./media/perfsdk-azuredevops-12.png)](./media/perfsdk-azuredevops-12.png)
 
 
## Tips

If you want switch multi-user testing between local test controller and Azure DevOps, you could create a copy of testsettings for each of them, select the one you want as Active Test Settings
 
## Troubleshooting
For information about single or multi-user testing with PerformanceSDK, see [Troubleshooting guide](troubleshoot-perf-sdk-user-testing.md).

