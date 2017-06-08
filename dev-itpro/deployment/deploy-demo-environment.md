---
# required metadata

title: Deploy a Microsoft Dynamics 365 for Operations demo environment
description: This topic explains how to deploy a single-box Microsoft Dynamics 365 for Operations demo environment on Microsoft Azure through Microsoft Dynamics Lifecycle Services (LCS).
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 141093
ms.assetid: dcd23629-246d-4fbc-adf5-7245bb2121e4
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---
# Deploy a Microsoft Dynamics 365 for Operations demo environment

[!include[banner](../includes/banner.md)]

This topic explains how to deploy a single-box Microsoft Dynamics 365 for Operations demo environment on Microsoft Azure through Microsoft Dynamics Lifecycle Services (LCS).

## Prerequisites
Before you begin your deployment, the following prerequisites must be in place:

- Verify that you have a Microsoft Azure subscription, and that you are a co-administrator on it.
- Verify that you have access to a Microsoft Dynamics Lifecycle Services (LCS) project and permissions to deploy an environment.
- Verify that you’ve connected your Azure subscription to your LCS project by using the information in the Azure Resource Manager onboarding topic.

## Deploy a Dynamics 365 for Operations demo environment on Azure
Use this procedure to deploy a single-box Microsoft Dynamics 365 for Operations demo environment on Azure through LCS.

1. In LCS, open your project, and then, in the **Environments** section, click the plus sign (**+**).
2. Select the Azure environment topology, and then select **Demo**.
3. Select most recent Azure Resource Manager (ARM) topology. Currently, the most recent topology is **Dynamics 365 for Operations – Demo (Release 1611 – ARM enabled)**.
4. In the **Deploy environment** dialog box, enter the name of the environment. This name should be unique in the Azure subscription. To make environments easy to identify, you might want to form an acronym from the user’s name and the topology.
5. Select the size of the virtual machine (VM). All the sizes for VMs that are enabled for ARM end with v2. You must use D* v2 sizes for Dynamics 365 for Operations workloads. We recommend D12v2.
6. Set the **Instances** field to 1.
Note: The size of the VM and the number of instances affect the cost of your subscription. For more information, see the Azure pricing page.
7. Click **Advanced settings** to add customizations to your deployment. However, for the demo environment, we recommend that you keep the default settings.
8. Agree to the licensing and pricing terms, and then click **Next**.
9. In the **Confirm** message box, click **Deploy**.
10. Open the **Cloud hosted environments** page to view the status of the deployment. After the deployment is successfully completed, the environment will be ready to demo Dynamics 365 for Operations.

## Open the Dynamics 365 for Operations client
Use this procedure to connect to the VM where the Dynamics 365 for Operations demo instance is installed. 

1. In LCS, open the **Cloud-hosted environments** page, and select the demo environment that you just deployed.
2. Scroll to the right and in the **Environment details** pane, under **Cloud services**, click **Log on to Dynamics 365 for Operations**.


