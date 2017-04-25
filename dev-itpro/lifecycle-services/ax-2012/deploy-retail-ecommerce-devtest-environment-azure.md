---
# required metadata

title: Deploy a Retail e-commerce dev/test environment on Azure (AX 2012)
description: This article explains how to deploy a Retail e-commerce dev/test environment on Microsoft Azure. To deploy the environment, you’ll use the Cloud-hosted environments tool in Microsoft Dynamics Lifecycle Services. 
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
ms.custom: 13241
ms.assetid: c69e8d08-b4f8-4660-b19f-53638170b13f
ms.search.region: Global
# ms.search.industry: 
ms.author: aamiral
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Deploy a Retail e-commerce dev/test environment on Azure (AX 2012)

[!include[banner](../includes/banner.md)]


This article explains how to deploy a Retail e-commerce dev/test environment on Microsoft Azure. To deploy the environment, you’ll use the Cloud-hosted environments tool in Microsoft Dynamics Lifecycle Services. 

## Prerequisites
-------------

Before you can complete the procedures in this article, make sure that the following prerequisites are in place.

| Category       | Prerequisite                                                                                                                                                    |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Required tasks | [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](plan-2012-r3-deployment-azure.md) |

## 1. Log on to Lifecycle Services

Microsoft Dynamics Lifecycle Services provides a cloud-based collaborative workspace that customers and partners can use to manage Microsoft Dynamics AX projects. You’ll use this website to deploy Dynamics AX 2012 R3 on Azure. Lifecycle Services is available to customers and partners as part of their support plans. You can access it with your CustomerSource or PartnerSource credentials. [Log on to Lifecycle Services](https://lcs.dynamics.com/en/)

## 2. Create a project

After you log in to Lifecycle Services, open an existing project, or create a new project. Projects are the key organizer of your experience in Lifecycle Services. The methodology associated with a project determines which phases and tasks are included in the project by default.
## 3. Connect the project to your Azure subscription

Connect the Lifecycle Services project to your Azure subscription. This will enable Lifecycle Services to deploy a Dynamics AX 2012 R3 environment to the subscription. To connect the project to your Azure subscription, complete the following procedure.Keep in mind that a project can be connected to only one Azure subscription. If you have multiple Azure subscriptions, be sure to identify which subscription you want to use before you complete this procedure.
1.  Click **Cloud-hosted environments**. The **Cloud-hosted environments** page is displayed.
2.  The **Microsoft Azure setup** panel is displayed on the side of the screen. If it is not displayed, click **Microsoft Azure settings**.
3.  Enter your **Azure subscription ID**.If you need to find your subscription ID, complete the following steps:
    1.  Open another instance of your browser.
    2.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
    3.  In the navigation pane on the left, click **Settings**. (You may have to scroll to the bottom of the navigation pane to see the **Settings** link.) The **Settings** page is displayed.
    4.  Copy your subscription ID, and then paste it into the **Azure subscription ID** field in Lifecycle Services (which is currently displayed in another browser instance).

4.  Click **Next**.
5.  Click **Download** to download a management certificate. This management certificate enables Lifecycle Services to communicate with Azure on your behalf. By default, the management certificate is saved to the **Downloads** folder on your computer and is named **LifecycleServicesDeployment**.**cer**.
6.  Upload the management certificate to Azure. To do so, complete the following steps:
    1.  Open another instance of your browser. (Or, go to the browser instance that you may have opened in step 3.)
    2.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
    3.  In the navigation pane on the left, click **Settings**. The **Settings** page is displayed.
    4.  Click **Management certificates**.
    5.  Click **Upload** at the bottom of the page.
    6.  In the **Upload a management certificate** window, browse to the management certificate that you downloaded in step 5. Then click the check mark.

7.  Go back to the browser that displays the **Microsoft Azure setup** panel in Lifecycle Services. Click **Next**.
8.  Select the region that is closest to you. The Dynamics AX  environment will be deployed to a datacenter in this region.
9.  Click **Connect**.The project is now connected to the Azure subscription that you specified. If you discover that you connected the project to the wrong Azure subscription (that is, assuming you have multiple Azure subscriptions), you’ll need to delete the project, create a new project, and then repeat this procedure to connect the new project to the appropriate Azure subscription.

## 4. Deploy a Retail ecommerce dev/test environment on Azure
Complete the following procedure to deploy a Retail e-commerce dev/test environment on Azure.
1.  On the **Cloud-hosted environments** page, click the **Add** (**+**) icon.
2.  In the **Select environment topology** panel, select **Dev/test**.
3.  Click **Retail e-commerce dev/test**.
4.  In the **Environment name** field, enter a name for the environment that will be deployed.
5.  Click **Customize deployment settings**.
6.  To customize domain settings, click **Customize domain settings**. Then use the following table to enter information.
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
    <td>Create a new domain in Azure for the environment</td>
    <td><ol>
    <li>Click <strong><span class="label">New domain</span></strong>.</li>
    <li>Enter a name for the domain. By default, the domain is named <em>contoso.com</em>.</li>
    </ol></td>
    </tr>
    <tr class="even">
    <td>Add the environment to an existing domain in Azure</td>
    <td><ol>
    <li>Click <strong><span class="label">Existing domain</span></strong>.</li>
    <li>Enter the name of the domain. For example, <em>contoso.com</em>.</li>
    </ol></td>
    </tr>
    </tbody>
    </table>

7.  To customize the service accounts that will be created in the domain, click **Customize service accounts**. Service accounts and/or service account passwords may be specified through the Advanced Settings option for a deployment. If neither is provided, default accounts are used and random passwords are selected. Use these features when you want to maintain account naming and password rules for your corporation.Account and password rules:
    -   A valid service name must be less than 20 characters with no special characters.
    -   A valid password must be more than 8 characters and contain uppercase letters, lowercase letters, numbers, and at least one of the following characters: \['@', '!', '=', '\*'\]You can’t use common passwords, such as: pass@word1

8.  To select the version of AX 2012 R3 that you want use, click **Supported version**. By default, the AX 2012 R3 CU8 version of this environment will be deployed. If you don’t want to use the CU8 version, select **Dynamics ERP 2012 R3 RTM** from the list.
9.  To customize virtual machine names, click **Customize virtual machine names**.In order to support common IT naming guidelines, the ability to name virtual machines is provided through the Advanced settings option on most deployment topologies. In addition to defining the name, a starting index can be selected for each virtual machine type. The index is incremented for each instance of the virtual machine type that is deployed.Virtual machine names must be 13 characters or less. The index is separated from the machine name by a hyphen (-), followed by the index that supports a maximum of 2 digits. Example: ACustomVMName-99. When virtual machine instances are added to an environment after the initial deployment, the deployment service will start incrementing the virtual machine name where it left off. For example, if you deployed four AOS virtual machines with a starting index of 2, then the last AOS instance name will be AOS-6. If you add two more AOS instances, they will be AOS-7 and AOS-8.If one of the virtual machine types in your deployment is customized, then all of the virtual machine names must be customized. This is done to ensure that a long deployment does not occur because a virtual machine name was accidentally missed.
10. To customize virtual network settings, click **Customize virtual network**. Then use the following table to enter information.
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
    <li>Select the name of the existing virtual network that you want to use.</li>
    <li>The <strong><span class="label">Address space</span></strong> field will automatically display the appropriate value. Select the provided value.</li>
    <li>The <strong><span class="label">Application subnet name</span></strong> field will display available options. If you are deploying to an AD that was previously deployed through Lifecycle Services, select the <strong><span class="label">*APPNET*</span></strong> value.</li>
    <li>The <strong>Active Directory subnet</strong> must be entered and match the Active Directory subnet IP/Range found in the Azure management portal for the AD you desire to target.
    <ol>
    <li>Log on to the <a href="https://manage.windowsazure.com/">Azure management portal</a>.</li>
    <li>In the navigation pane on the left, click <strong><span class="label">Networks</span></strong>.</li>
    <li>Click the name of the virtual network that you’re going to use.</li>
    <li>Click <strong><span class="label">Configure</span></strong>.Details about the virtual network are listed on the page.</li>
    </ol></li>
    </ol></td>
    </tr>
    </tbody>
    </table>

11. Click **Done**. The **Deploy environment** panel is redisplayed.
12. The number and size of each virtual machine that will be deployed is listed. Change the number and size of the virtual machines, as needed.
    -   For information about the software installed on each virtual machine in this environment, see [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](plan-2012-r3-deployment-azure.md).
    -   For sizing and pricing details about virtual machines, see [Virtual machines pricing details](http://azure.microsoft.com/en-us/pricing/details/virtual-machines/).

13. Click **Software License Terms** to review the licensing terms and conditions. Then select the check box to indicate that you agree to the terms.
14. Click **Next**.
15. Click **Deploy** to confirm that you’re ready to deploy the environment.The deployment may take a few hours to complete. When the deployment is done, the **Deployment** **Status** column on the **Cloud-hosted environments** page will display **Deployed**. (You may need to refresh your browser to see this.)If the deployment fails, you may see an error message right away. If the error occurs later in the deployment process, error details will be displayed in the details pane on the right-side of the page.

## 5. Prepare the Retail ecommerce dev/test environment for use
Now that the Retail e-commerce dev/test environment has been deployed on Azure, you can connect it to your Dynamics AX environment that exists on-premises, or on Azure. See the following sections for more information.
### Prerequisites

Before you complete the following procedures, make sure that the following prerequisites are in place.

| Prerequisite                                                                                                                                                    | More information                                                                                                                                                                                                                                                                                                            |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set up and configure the Dynamics AX  application object server (AOS), database, and client.As mentioned, AX 2012 R3 may be installed on-premises, or on Azure. | [System setup for Microsoft Dynamics AX](http://technet.microsoft.com/library/e9256fe4-888c-413e-aa35-53e1a6de5806(AX.60).aspx)                                                                                                                                                                                             |
| Import data into Dynamics AX.                                                                                                                                   | If you want sample data installed in your Dynamics AX  environment, use the Test Data Transfer tool to install the sample data. For instructions, see [Test Data Transfer Tool (beta) for Microsoft Dynamics AX 2012 R3](test-data-transfer-tool-beta-2012.md). |
| Set up and configure Async Server.                                                                                                                              | [Commerce Data Exchange: Async Server](http://technet.microsoft.com/library/8f802c2f-37bc-4a5c-805e-bece3640245f(AX.60).aspx)                                                                                                                                                                                               |
| Set up and configure Real-time Service.                                                                                                                         | [Commerce Data Exchange: Real-time Service](http://technet.microsoft.com/library/7dc09b26-47ba-403e-9b69-a61601d46bae(AX.60).aspx)                                                                                                                                                                                          |
| Sync metadata for Commerce Data Exchange.                                                                                                                       | [Enter parameters for Retail Scheduler](http://technet.microsoft.com/library/bfe69872-8fb9-41d9-8f61-d206055dbd87(AX.60).aspx)                                                                                                                                                                                              |
| Create a new, or update an existing online store channel.                                                                                                       | [Set up an online store](https://technet.microsoft.com/EN-US/library/jj682095.aspx)                                                                                                                                                                                                                                         |


### Complete configuration tasks on the AOS server/virtual machine

Log on to the server or virtual machine where the AOS is installed and complete the following steps.
1.  Set up endpoints for the server or virtual machine. For instructions on how to set up endpoints for a virtual machine, see the “Getting Started” section of this [blog post](http://blogs.msdn.com/b/axsupport/archive/2014/06/27/connecting-retail-components-on-an-external-computer-to-the-microsoft-dynamics-ax-r3-azure-lifecycle-services-demo-virtual-machine.aspx).
2.  Configure the Real-time service and update the profile. For instructions, see the “Configure Real-time Service” section of this [blog post](http://blogs.msdn.com/b/axsupport/archive/2014/06/27/connecting-retail-components-on-an-external-computer-to-the-microsoft-dynamics-ax-r3-azure-lifecycle-services-demo-virtual-machine.aspx).
3.  Run the scheduler jobs to populate the channel database. For instructions, see the “Run Scheduler Jobs to Populate Channel Database” section of this [blog post](http://blogs.msdn.com/b/axsupport/archive/2014/06/27/connecting-retail-components-on-an-external-computer-to-the-microsoft-dynamics-ax-r3-azure-lifecycle-services-demo-virtual-machine.aspx).

### Complete configuration tasks on the E-COM virtual machine

From the **Cloud-hosted environments** page, select your Retail e-commerce dev/test environment. Then scroll to the right and click the **E-COM-&lt;GUID&gt;** link to log on to the virtual machine. After you have logged on to the machine, complete the following steps:
1.  If using a self-signed certificate, install the certificate on the E-COM-&lt;GUID&gt; virtual machine. For instructions, see the “Install the Cert on the External Machine” section of this [blog post](http://blogs.msdn.com/b/axsupport/archive/2014/06/27/connecting-retail-components-on-an-external-computer-to-the-microsoft-dynamics-ax-r3-azure-lifecycle-services-demo-virtual-machine.aspx).
2.  Update Async Client to use the URL of the Async Server. For instructions, see the “Install CDX Async Client” section of this [blog post](http://blogs.msdn.com/b/axsupport/archive/2014/06/27/connecting-retail-components-on-an-external-computer-to-the-microsoft-dynamics-ax-r3-azure-lifecycle-services-demo-virtual-machine.aspx).

### Access the e-commerce site

After you have completed the configuration procedures described above, you can access the e-commerce website at: http://:40002/sites/retailpublishingportal

## 6. Learn more about the service accounts for this environment

The following sections provide information about the service accounts that were created when you deployed the environment.
### Domain accounts

The following table lists the default names of the domain accounts that were created when you deployed the environment.

| Domain account                  | Description                                                                                                                                                                                         |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|SQLServiceUser      | The account used to run the following services: SQL Server Analysis Services (MSSQLSERVER)                                                                                                          |
| DynamicsInstallUser | The account used to install Dynamics AX.                                                                                                                                                            |
| ContosoSPServiceUser            | The account used to run the following services: AppFabric Caching Service, SharePoint Search Host Controller, SharePoint Server Search 15, SharePoint Timer Service, and SharePoint User Code Host. |
|RetailServiceUser   | The account used to run the following services: Microsoft Dynamics AX for Retail Commerce Data Exchange Async Client.                                                                               |
| BCProxyUser         | The account used as the Business Connector proxy.                                                                                                                                                   |

Note: The passwords are displayed on the Cloud-hosted environments page in [Lifecycle Services](https://lifecycleservices.dynamics.com/en/).

### Local administrator accounts

Each virtual machine that you deployed has a local administrator account. This account is: builtinaxlocaladmin. The passwords for the local administrator accounts are displayed on the **Cloud-hosted environments** page in [Lifecycle Services](https://lifecycleservices.dynamics.com/en/).

See also
--------

[Online Store (TechNet)](http://technet.microsoft.com/library/56364854-9730-4afa-8cf7-ae337ce2257a(AX.60).aspx)



