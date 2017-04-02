---
# required metadata

title: Deploy a Dynamics AX 2012 R3 or AX 2012 R3 CU8 demo environment on Azure
description: 
author: kfend
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 15561
ms.assetid: b7f2e7b9-2627-4e8f-beab-a3cea8d79dc4
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Deploy a Dynamics AX 2012 R3 or AX 2012 R3 CU8 demo environment on Azure



Prerequisites
-------------

Before you complete the procedures in this article, make sure that the following prerequisites are in place.

|                |                                                                                                                                                                 |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Category**   | **Prerequisite**                                                                                                                                                |
| Required tasks | [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](plan-2012-r3-deployment-azure.md) |

## 1. Log on to Lifecycle Services
Microsoft Dynamics Lifecycle Services provides a cloud-based collaborative workspace that customers and partners can use to manage Microsoft Dynamics AX projects. You’ll use this website to deploy AX 2012 R3 on Azure. Lifecycle Services is available to customers and partners as part of their support plans. You can access it with your CustomerSource or PartnerSource credentials. [Log on to Lifecycle Services](https://lcs.dynamics.com/en/)

## 2. Create a project
After you log in to Lifecycle Services, open an existing project, or create a new project. Projects are the key organizer of your experience in Lifecycle Services. The methodology associated with a project determines which phases and tasks are included in the project by default.

## 3. Connect the project to your Azure subscription
Connect the Lifecycle Services project to your Azure subscription. This will enable Lifecycle Services to deploy an AX 2012 R3 environment to the subscription. To connect the project to your Azure subscription, complete the following procedure. Keep in mind that a project can be connected to only one Azure subscription. If you have multiple Azure subscriptions, be sure to identify which subscription you want to use before you complete this procedure.

1.  Click **Cloud-hosted environments**. The **Cloud-hosted environments** page is displayed.
2.  The **Microsoft Azure setup** panel is displayed on the side of the screen. If it is not displayed, click **Microsoft Azure settings**.
3.  Enter your Azure subscription ID. If you need to find your subscription ID, complete the following steps:
    1.  Open another instance of your browser.
    2.  Log on to the **Azure management portal**.
    3.  In the navigation pane on the left, click **Settings**. (You may have to scroll to the bottom of the navigation pane to see the Settings link.) The **Settings** page is displayed.
    4.  Copy your subscription ID, and then paste it into the **Azure subscription ID** field in Lifecycle Services (which is currently displayed in another browser instance).

4.  Click **Next**.
5.  Click **Download** to download a management certificate. This management certificate enables Lifecycle Services to communicate with Azure on your behalf. By default, the management certificate is saved to the Downloads folder on your computer and is named LifecycleServicesDeployment.cer.
6.  Upload the management certificate to Azure. To do so, complete the following steps:
    1.  Open another instance of your browser. (Or, go to the browser instance that you may have opened in step 3.)
    2.  Log on to the **Azure management portal**.
    3.  In the navigation pane on the left, click **Settings**. The **Settings** page is displayed.
    4.  Click **Management certificates**.
    5.  Click **Upload** at the bottom of the page.
    6.  In the **Upload a management certificate** window, browse to the management certificate that you downloaded in step 5. Then click the check mark.

7.  Go back to the browser that displays the **Microsoft Azure setup** panel in Lifecycle Services. Click **Next**.
8.  Select the region that is closest to you. The AX 2012 R3 environment will be deployed to a datacenter in this region.
9.  Click **Connect**.

The project is now connected to the Azure subscription that you specified. If you discover that you connected the project to the wrong Azure subscription (that is, assuming you have multiple Azure subscriptions), you’ll need to delete the project, create a new project, and then repeat this procedure to connect the new project to the appropriate Azure subscription.

## 4. Deploy an AX 2012 R3 or AX 2012 R3 CU8 demo environment on Azure
Complete the following procedure to deploy an AX 2012 R3 or AX 2012 R3 CU8 demo environment on Azure.

1.  On the **Cloud-hosted environments** page, click the Add (+) icon.
2.  In the **Select environment topology** panel, select **Demo**.
3.  Click D**emo AX 2012 R3** or **Demo AX 2012 R3 CU8**.
4.  In the **Environment name** field, enter a name for the environment that will be deployed.
5.  Click **Advanced settings**.
6.  To customize virtual machine names, click **Customize virtual machine names**. In order to support common IT naming guidelines, the ability to name virtual machines is provided through the **Advanced settings** option on most deployment topologies. In addition to defining the name, a starting index can be selected for each virtual machine type. The index is incremented for each instance of the virtual machine type that is deployed. Virtual machine names must be 13 characters or less. The index is separated from the machine name by a hyphen (-), followed by the index that supports a maximum of 2 digits. Example: ACustomVMName-99 When virtual machine instances are added to an environment after the initial deployment, the deployment service will start incrementing the virtual machine name where it left off. For example, if you deployed four AOS virtual machines with a starting index of 2, then the last AOS instance name will be AOS-6. If you add two more AOS instances, they will be AOS-7 and AOS-8. If one of the virtual machine types in your deployment is customized, then all of the virtual machine names must be customized. This is done to ensure that a long deployment does not occur because a virtual machine name was accidentally missed.
7.  One virtual machine will be deployed on Azure. The default size of this virtual machine is D3 (4 cores, 14 GB memory). If you want to change the size, select a different size from the **Size** list.
    -   For sizing and pricing details about virtual machines, see [Virtual machines pricing details](http://azure.microsoft.com/en-us/pricing/details/virtual-machines/).
    -   For more information about the software installed on the virtual machine, see [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](plan-2012-r3-deployment-azure.md).

8.  Click **Software License Terms** to review the licensing terms and conditions. Then select the check box to indicate that you agree to the terms.
9.  Click **Next**.
10. Click **Deploy** to confirm that you’re ready to deploy the environment. The deployment may take a few hours to complete. When the deployment is done, the **Deployment Status** column on the **Cloud-hosted environments** page will display **Deployed**. (You may need to refresh your browser to see this.) If the deployment fails, you may see an error message right away. If the error occurs later in the deployment process, error details will be displayed in the **Details** pane on the right side of the page.

## 5. Open the AX 2012 R3 client
Complete the following procedure to connect to the virtual machine where the AX 2012 R3 client is installed.

1.  On the **Cloud-hosted environments** page, select the demo environment that you just deployed.
2.  Scroll to the right side of the page to view details about the environment.
3.  Click the **DEMO-&lt;GUID&gt;** link.
4.  At the bottom of the page, click **Open** to open the .rdp file.
5.  When prompted for credentials, enter the user name and password found on the **Cloud-hosted environments** page for this environment.
6.  When the virtual machine’s desktop is displayed, click the Microsoft Dynamics AX icon to open the AX 2012 R3 client.


