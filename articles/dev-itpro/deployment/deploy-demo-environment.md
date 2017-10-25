---
# required metadata

title: Deploy a demo environment
description: This topic explains how to deploy a demo environment on Microsoft Azure using Microsoft Dynamics Lifecycle Services (LCS). This applies to Dynamics 365 for Finance and Operations and Dynamics 365 for Retail.
author: sarvanisathish
manager: AnnBe
ms.date: 10/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Platform, UnifiedOperations, 
# ms.tgt_pltfrm: 
ms.custom: 141093
ms.assetid: dcd23629-246d-4fbc-adf5-7245bb2121e4
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2, 

---
# Deploy a demo environment

[!include[banner](../includes/banner.md)]

This topic explains how to deploy a demo environment on Microsoft Azure using Microsoft Dynamics Lifecycle Services (LCS). This topic applies to deploying a demo environment for:

- Dynamics 365 for Finance and Operations
- Dynamics 365 for Retail

## Prerequisites
Before you begin your deployment, the following prerequisites must be in place:

- Verify that you have an Azure subscription, and that you are a co-administrator on it.
- Verify that you have access to an LCS project and permissions to deploy an environment.
- Verify that you’ve connected your Azure subscription to your LCS project by using the information in the [Azure Resource Manager onboarding](arm-onboarding.md) topic.

## Deploy a demo environment
Use this procedure to deploy a demo environment on Azure using LCS. 

1. In LCS, open your project, and then, in the **Environments** section, click the plus sign (**+**).
2. Select the Azure environment topology, and then select **Demo**.
3. Select a topology.
    - For Finance and Operations, select the most recent Azure Resource Manager (ARM) topology for Finance and Operations.
    - For Retail, select **Dynamics 365 for Retail - Demo**.
4. In the **Deploy environment** dialog box, enter the name of the environment. This name should be unique in the Azure subscription. To make environments easy to identify, consider forming an acronym using the user’s name and the topology.
5. Select the size of the virtual machine (VM). All the sizes for VMs that are enabled for ARM end with v2. You must use D* v2 sizes for Finance and Operations workloads. We recommend D12v2.
6. Set the **Instances** field to 1.

      
    **Note:** The size of the VM and the number of instances affect the cost of your subscription. For more information, see [Azure pricing](https://azure.microsoft.com/en-us/pricing/).
  
7. Click **Advanced settings** to add customizations to your deployment. For the demo environment, we recommend that you keep the default settings.
8. Agree to the licensing and pricing terms, and then click **Next**.
9. In the **Confirm** message box, click **Deploy**.
10. Open the **Cloud hosted environments** page to view the status of the deployment. After the deployment is successfully completed, the environment will be ready.

## Log on to your demo environment
To log on to your demo environment, do the following.

1. In LCS, open the **Cloud-hosted environments** page, and select the demo environment that you just deployed.

2. Scroll to the right and in the **Environment details** pane, under **Cloud services**, click the appropriate link:

      - **Log on to Finance and Operations**
      - **Log on to Retail**
