---
# required metadata

title: Deploy a Retail essentials demo environment on Azure (AX 2012)
description: 
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 13352
ms.assetid: be08d43a-f05e-4580-ac75-52710d06a1d7
ms.search.region: Global
# ms.search.industry: 
ms.author: aamiral
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Deploy a Retail essentials demo environment on Azure (AX 2012)

[!include[banner](../../includes/banner.md)]




This article explains how to deploy a Retail essentials demo environment on Microsoft Azure. To deploy the environment, you’ll use the Cloud-hosted environments tool in Microsoft Dynamics Lifecycle Services.

## Prerequisites
Before you complete the procedures in this article, make sure that the following prerequisites are in place.

| Category       | Prerequisite                                                                                                                                            |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Required tasks | [Plan your Microsoft Dynamics AX deployment on Azure](plan-2012-r3-deployment-azure.md) |

## 1. Log on to Lifecycle Services
Microsoft Dynamics Lifecycle Services provides a cloud-based collaborative workspace that customers and partners can use to manage Microsoft Dynamics AX projects. You’ll use this website to deploy Dynamics AX on Azure. Lifecycle Services is available to customers and partners as part of their support plans. You can access it with your CustomerSource or PartnerSource credentials. [Log on to Lifecycle Services](https://lcs.dynamics.com/)

## 2. Create a project
After you log in to Lifecycle Services, open an existing project, or create a new project. Projects are the key organizer of your experience in Lifecycle Services. The methodology associated with a project determines which phases and tasks are included in the project by default.

## 3. Connect the project to your Azure subscription
Connect the Lifecycle Services project to your Azure subscription. This will enable Lifecycle Services to deploy a Dynamics AX environment to the subscription. To connect the project to your Azure subscription, complete the following procedure. Keep in mind that a project can be connected to only one Azure subscription. If you have multiple Azure subscriptions, be sure to identify which subscription you want to use before you complete this procedure.
1.  Click **Cloud-hosted environments**. The **Cloud-hosted environments** page is displayed.
2.  The **Microsoft Azure setup** panel is displayed on the side of the screen. If it is not displayed, click **Microsoft Azure settings**.
3.  Enter your Azure subscription ID. If you need to find your subscription ID, complete the following steps:
    1.  Open another instance of your browser.
    2.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
    3.  In the navigation pane on the left, click **Settings.** (You may have to scroll to the bottom of the navigation pane to see the **Settings** link.) The **Settings** page is displayed.
    4.  Copy your subscription ID, and then paste it into the **Azure subscription ID** field in Lifecycle Services (which is currently displayed in another browser instance).

4.  Click **Next**.
5.  Click **Download** to download a management certificate. This management certificate enables Lifecycle Services to communicate with Azure on your behalf. By default, the management certificate is saved to the **Downloads** folder on your computer and is named **LifecycleServicesDeployment.cer.**
6.  Upload the management certificate to Azure. To do so, complete the following steps:
    1.  Open another instance of your browser. (Or, go to the browser instance that you may have opened in step 3.)
    2.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
    3.  In the navigation pane on the left, click **Settings**. The **Settings** page is displayed.
    4.  Click **Management certificates**.
    5.  Click **Upload** at the bottom of the page.
    6.  In the **Upload a management certificate** window, browse to the management certificate that you downloaded in step 5. Then click the check mark.

7.  Go back to the browser that displays the **Microsoft Azure setup** panel in Lifecycle Services. Click **Next**.
8.  Select the region that is closest to you. The AX 2012 R3 environment will be deployed to a datacenter in this region.
9.  Click **Connect**. The project is now connected to the Azure subscription that you specified. If you discover that you connected the project to the wrong Azure subscription (that is, assuming you have multiple Azure subscriptions), you’ll need to delete the project, create a new project, and then repeat this procedure to connect the new project to the appropriate Azure subscription.

## 4. Deploy a Retail essentials demo environment on Azure
Complete the following procedure to deploy a Retail essentials demo environment on Azure.

1.  On the **Cloud-hosted environments** page, click the **Add** (+) icon.
2.  In the **Select environment topology** panel, select **Demo**.
3.  Click **Retail essentials demo.**
4.  In the **Environment name** field, enter a name for the environment that will be deployed.
5.  Click **Advanced settings**.
6.  To customize virtual machine names, click **Customize virtual machine names**. In order to support common IT naming guidelines, the ability to name virtual machines is provided through the **Advanced settings** option on most deployment topologies. In addition to defining the name, a starting index can be selected for each virtual machine type. The index is incremented for each instance of the virtual machine type that is deployed.Virtual machine names must be 13 characters or less. The index is separated from the machine name by a hyphen (-), followed by the index that supports a maximum of 2 digits. Example: ACustomVMName-99. When virtual machine instances are added to an environment after the initial deployment, the deployment service will start incrementing the virtual machine name where it left off. For example, if you deployed four AOS virtual machines with a starting index of 2, then the last AOS instance name will be AOS-6. If you add two more AOS instances, they will be AOS-7 and AOS-8.If one of the virtual machine types in your deployment is customized, then all of the virtual machine names must be customized. This is done to ensure that a long deployment does not occur because a virtual machine name was accidentally missed.
7.  To customize virtual network settings, click **Customize virtual network** settings. Then use the following table to enter information.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>If you want to:</th>
    <th>Do this:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Create a new virtual network in Azure for the environment</td>
    <td><ol>
    <li>Click <strong><span class="label">New virtual network</span></strong>.</li>
    <li>Enter a name for the virtual network.</li>
    </ol></td>
    </tr>
    <tr class="even">
    <td>Add the environment to an existing virtual network in Azure</td>
    <td><ol>
    <li>Click <strong><span class="label">Existing virtual network</span></strong>.</li>
    <li>Select the name of the existing virtual network that you want to use. The <span class="label"><strong>Application subnet</strong> <strong>name</strong></span> and <strong><span class="label">Address space</span></strong> fields will automatically display the appropriate information based on the virtual network that you selected. If you want to verify the information in these fields, do this:
    <ol>
    <li>Log on to the <a href="https://manage.windowsazure.com/">Azure management portal</a>.</li>
    <li>In the navigation pane on the left, click <strong><span class="label">Networks</span></strong>.</li>
    <li>Click the name of the virtual network that you’re going to use.</li>
    <li>Click <strong><span class="label">Configure</span></strong>. Details about the virtual network are listed on the page.</li>
    <li>Click <strong><span class="label">Done</span></strong>. The <strong><span class="label">Deploy environment</span></strong> panel is redisplayed.</li>
    <li>The number and size of each virtual machine that will be deployed is listed. Change the number and size of the virtual machines, as needed.</li>
    </ol></li>
    </ol></td>
    </tr>
    </tbody>
    </table>

    -   For information about the software installed on each virtual machine in this environment, see [Plan your Microsoft Dynamics AX deployment on Azure](plan-2012-r3-deployment-azure.md).
    -   For sizing and pricing details about virtual machines, see [Virtual machines pricing details](http://azure.microsoft.com/en-us/pricing/details/virtual-machines/).

8.  Click **Software License Terms** to review the licensing terms and conditions. Then select the check box to indicate that you agree to the terms.
9.  Click **Next**.
10. Click **Deploy** to confirm that you’re ready to deploy the environment. The deployment may take a few hours to complete. When the deployment is done, the Deployment Status column on the **Cloud-hosted environments** page will display **Deployed**. (You may need to refresh your browser to see this.)If the deployment fails, you may see an error message right away. If the error occurs later in the deployment process, error details will be displayed in the details pane on the right-side of the page.

## 5. Open the Dynamics AX client
Complete the following procedure to connect to the virtual machine where the Dynamics AX client is installed.

1.  On the **Cloud-hosted environments page**, select the Retail essentials environment that you just deployed.
2.  Scroll to the right side of the page to view the properties of the environment.
3.  Click the **DEMO-&lt;GUID&gt;** link.
4.  At the bottom of the page, click **Open** to open the .rdp file.
5.  When prompted for credentials, enter the user name and password for the &lt;DomainName&gt;Administrator account. You can find the password for this account on the **Cloud-hosted environments** page for this environment.
6.  When the virtual machine’s desktop is displayed, click the **Microsoft Dynamics AX** icon to open the Microsoft Dynamics AX client.





