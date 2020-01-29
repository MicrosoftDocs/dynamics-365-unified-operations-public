---
# required metadata

title: Deploy Retail essentials dev/test environments on Azure
description: This topic explains how to deploy a Retail essentials dev/test environment on Microsoft Azure. To deploy the environment, you’ll use the cloud-hosted environments tool in Microsoft Dynamics Lifecycle Services.
author: aamirallaqaband
manager: AnnBe
ms.date: 01/05/2018
ms.topic: article
ms.prod: dynamics-ax-2012 
ms.service: 
ms.technology:

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 13261
ms.assetid: 00e58780-7373-4c53-b3af-1e9d3d4eebff
ms.search.region: Global
# ms.search.industry: 
ms.author: aamiral
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Deploy Retail essentials dev/test environments on Azure

[!include [banner](../../includes/banner.md)]

This topic explains how to deploy a Retail essentials dev/test environment on Microsoft Azure. To deploy the environment, you’ll use the cloud-hosted environments tool in Microsoft Dynamics Lifecycle Services.

Prerequisites
-------------

Before you complete the procedures in this topic, make sure that the following prerequisites are in place.

| Category       | Prerequisite                                                                                                                                                    |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Required tasks | [Plan AX 2012 R3 deployments on Azure](plan-2012-r3-deployment-azure.md) |

## 1. Log on to Lifecycle Services
Microsoft Dynamics Lifecycle Services (LCS) provides a cloud-based collaborative workspace that customers and partners can use to manage Dynamics AX projects. You’ll use this website to deploy Dynamics AX on Azure. Lifecycle Services is available to customers and partners as part of their support plans. You can access it with your CustomerSource or PartnerSource credentials, for details see [Log on to Lifecycle Services](https://lcs.dynamics.com/en/).

## 2. Create a project
After you log in to LCS, open an existing project, or create a new project. Projects are the key organizer of your experience in LCS. The methodology associated with a project determines which phases and tasks are included in the project by default.

## 3. Connect the project to your Azure subscription
Connect the LCS project to your Azure subscription. This will enable LCS to deploy a Dynamics AX environment to the subscription. To connect the project to your Azure subscription, complete the following procedure.

1. In your LCS project, go to the **Environments** section, click **Microsoft Azure settings**, and then click **Add** in the **Azure Connectors** area. 
   >[!Note]
   > The **Microsoft Azure settings** option is also available when you click the **Cloud-hosted environments** tile.
2. Enter a name to identify the connection to Azure.
3. Enter your Azure subscription ID. If you need to find your subscription ID, complete the following steps:
   1.  Open another instance of your browser.
   2.  Log on to the [Azure portal](https://ms.portal.azure.com/).
   3.  In the navigation pane on the left, click **Subscriptions**. 

       > [!Note]
       > You may need to click **More services** at the bottom, and then click **Subscriptions**.

   4.  Copy your subscription ID, and then paste it into the **Azure subscription ID** field in LCS (which is currently displayed in another browser instance).

4. Click **Next**.
5. Click **Download** to download a management certificate. This management certificate enables LCS to communicate with Azure on your behalf. By default, the management certificate is saved to the **Downloads** folder on your computer and is named **LifecycleServicesDeployment.cer.**
6. Upload the management certificate to Azure. To do so, see the instructions in [Upload an Azure Management API Management Certificate](https://docs.microsoft.com/azure/azure-api-management-certs).

7. Go back to the browser that displays the **Microsoft Azure setup** panel in LCS. Click **Next**.
8. Select a region. The AX 2012 R3 environment will be deployed to a datacenter in this region.
9. Click **Connect**. The project is now connected to the Azure subscription that you specified. 

>[!Note]
> If the certificate expires, you can obtain a new one. To do so:
> 1. Select the connection in the **Azure connectors** area of your project settings, and click **Edit**.
> 2. The **Microsoft Azure setup** panel is displayed on the side of the screen. Click **Download** to download a new certificate.
> 3. Repeat steps 6-9 of the above procedure.

## 4. Deploy a Retail essentials dev/test environment on Azure
Complete the following procedure to deploy a Retail essentials dev/test environment on Azure.

1. On the **Cloud-hosted environments** page, click the **Add** (**+**) icon.
2. In the **Select environment topology** panel, select **Dev/Test**.
3. Click **Retail essentials dev/test**.
4. In the **Environment name** field, enter a name for the environment that will be deployed.
5. Click **Advanced settings**.
6. To customize domain settings, click **Customize domain settings**. Use the following table to enter information.
   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <thead>
   <tr class="header">
   <th>If you want to</th>
   <th>Do this</th>
   </tr>
   </thead>
   <tbody>
   <tr class="odd">
   <td>Create a new domain in Azure for the environment</td>
   <td><ol>
   <li>Click <strong>New domain</strong>.</li>
   <li>Enter a name for the domain. By default, the domain is named <em>contoso.com</em>.</li>
   </ol></td>
   </tr>
   <tr class="even">
   <td>Add the environment to an existing domain in Azure</td>
   <td><ol>
   <li>Click <strong>Existing domain</strong>.</li>
   <li>Enter the name of the domain. For example, <em>contoso.com</em>.</li>
   </ol></td>
   </tr>
   </tbody>
   </table>

7. To customize the service accounts that will be created in the domain, click **Customize service accounts**. Service accounts and/or service account passwords can be specified through the **Advanced Settings** option for a deployment. If neither is provided, default accounts are used and random passwords are selected. Use these features when you want to maintain account naming and password rules for your corporation. Account and password rules:
   - A valid service name must be less than 20 characters with no special characters.
   - A valid password must be more than 8 characters and contain uppercase letters, lowercase letters, numbers, and at least one of the following characters: \['@', '!', '=', '\*'\] You can’t use common passwords, such as: pass@word1

8. To select the version of AX 2012 R3 that you want use, click **Supported version**. By default, the AX 2012 R3 CU8 version of this environment will be deployed. If you don’t want to use the CU8 version, select **Dynamics ERP 2012 R3 RTM** from the list.
9. To customize virtual machine names, click **Customize virtual machine names**. In order to support common IT naming guidelines, the ability to name virtual machines is provided through the **Advanced settings** option on most deployment topologies. In addition to defining the name, a starting index can be selected for each virtual machine type. The index is incremented for each instance of the virtual machine type that is deployed. Virtual machine names must be 13 characters or less. The index is separated from the machine name by a hyphen (-), followed by the index that supports a maximum of 2 digits. Example: ACustomVMName-99. When virtual machine instances are added to an environment after the initial deployment, the deployment service will start incrementing the virtual machine name where it left off. For example, if you deployed four AOS virtual machines with a starting index of 2, then the last AOS instance name will be AOS-6. If you add two more AOS instances, they will be AOS-7 and AOS-8. If one of the virtual machine types in your deployment is customized, then all of the virtual machine names must be customized. This is done to ensure that a long deployment does not occur because a virtual machine name was accidentally missed.
10. To customize virtual network settings, click <strong>Customize virtual network</strong>. Use the following table to enter information.
    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>If you want to</th>
    <th>Do this</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Create a new virtual network in Azure for the environment</td>
    <td><ol>
    <li>Click <strong>New virtual network</strong>.</li>
    <li>Enter a name for the virtual network.</li>
    </ol></td>
    </tr>
    <tr class="even">
    <td>Add the environment to an existing virtual network in Azure</td>
    <td><ol>
    <li>Click <strong>Existing virtual network</strong>.</li>
    <li>Select the name of the existing virtual network that you want to use.</li>
    <li>The <strong>Address space</strong> field will automatically display the appropriate value. Select the provided value.</li>
    <li>The <strong>Application subnet name</strong> field will display available options. If you are deploying to an AD that was previously deployed through Lifecycle Services, select the <strong>APPNET</strong> value.</li>
    <li>The Active Directory subnet must be entered and match the Active Directory subnet IP/Range found in the Azure management portal for the AD you want to target.
    <ol>
    <li>Log on to the <a href="https://ms.portal.azure.com/">Azure portal</a>.</li>
    <li>In the navigation pane on the left, click <strong>Virtual networks</strong>.</li>
    <li>Click the name of the virtual network that you’re going to use.</li>
    <li>Click <strong>Configure</strong>. Details about the virtual network are listed on the page.</li>
    </ol></li>
    </ol></td>
    </tr>
    </tbody>
    </table>

11. Click **Done**. The **Deploy** **environment** panel is redisplayed.
12. The number and size of each virtual machine that will be deployed is listed. Change the number and size of the virtual machines, as needed.
    -   For information about the software installed on each virtual machine in this environment, see [Plan AX 2012 R3 deployments on Azure](plan-2012-r3-deployment-azure.md).
    -   For sizing and pricing details about virtual machines, see [Virtual machines pricing details](https://azure.microsoft.com/pricing/details/virtual-machines/).

13. Click **Software License Terms** to review the licensing terms and conditions. Then select the check box to indicate that you agree to the terms.
14. Click **Next**.
15. Click **Deploy** to confirm that you’re ready to deploy the environment. The deployment may take a few hours to complete. When the deployment is done, the **Deployment Status** column on the **Cloud-hosted environments** page will display **Deployed**. (You may need to refresh your browser to see this.) If the deployment fails, you may see an error message right away. If the error occurs later in the deployment process, error details will be displayed in the details pane on the right-side of the page.

## 5. Prepare the environment for use
Now that the Retail essentials environment has been deployed on Azure, you must set it up and configure it for use. See the following sections for more information.

### Log on to the Retails essentials virtual machine

Log on to the ESSEN-&lt;GUID&gt; virtual machine using the &lt;DomainName&gt;DynamicsInstallUser account. For instructions, see the “How do I log on to a virtual machine?” section of the [Manage AX 2012 R3 deployments on Azure](manage-2012-r3-deployment-azure.md) topic.

### Compile Dynamics AX 2012 R3

Compile Dynamics AX 2012 R3 by using AxBuild.exe. For instructions, see [AxBuild.exe for Parallel Compile on AOS of X++ to p-code](https://technet.microsoft.com/library/dn528954.aspx).

### Initialize Dynamics AX 2012 R3

Open the Dynamics AX 2012 R3 client and complete the initialization checklists. For instructions, see [Initialization checklists](https://technet.microsoft.com/library/aa497061.aspx).

### Install sample data

If you want sample data installed in your environment, complete the following steps.

1.  Go to the following location:F:TestTransferTool
2.  Install the Test Data Tool. For instructions, see [Install the Test Data Transfer Tool (beta)](install-test-data-transfer-tool-beta.md).
3.  Open a command prompt and navigate to the following location: C:\Program Files (x86)\Microsoft Dynamics AX 2012 R3 Test Data Transfer Tool (Beta)
4.  Run the following command: dp.exe import F:DemoData MicrosoftDynamicsAx

> [!NOTE]
> The sample data includes trial license keys for Dynamics AX. If you choose not to install the sample data, you can download trial license keys—for development or testing purposes—from [CustomerSource](https://mbs.microsoft.com/downloads/customer/AX/AXDemoTools/MicrosoftDynamicsAX2012R2v4DemoLicense.zip) or [MSDN](https://msdn.microsoft.com/subscriptions/securedownloads/hh442898#FileId=57028).

### Set up Retail essentials

Open the Dynamics AX client and complete the following steps.

1.  Go to the **Retail essentials** area page.
2.  Click **Channels &gt; Setup** **&gt; Retail parameters**.
3.  In the **Retail parameters** form, complete the following steps:
    1.  Click the **Initialize** button at the top of the form.
    2.  Click **Yes** to confirm that you want to initialize the base configuration data. When the initialization process is complete, the Infolog is displayed.
    3.  Close the form.

4.  Click **Data synchronization &gt; Setup &gt; Retail scheduler parameters.**
5.  In the **Retail scheduler parameters** form, complete the following steps:
    1.  In the **Server name** field, enter the name of the virtual machine.
    2.  Click the **Sync metadata** button at the top of the form.
    3.  Click **Yes** to confirm that you want to sync the metadata. When the process is complete, the Infolog is displayed.
    4.  Close the form.

6.  Click **Data synchronization &gt; Setup &gt; Channel integration &gt; Real-time service profiles.**
7.  In the **Commerce Data Exchange: Real-time Service Profile** form, complete the following steps:
    1.  In the **Server name** field, enter the name of the virtual machine.
    2.  In the **Common name** field, enter the common name of the certificate.
    3.  Close the form.

8.  Click **Data synchronization &gt; Setup &gt; Channel integration &gt; Working folders.**
9.  In the **Working folders** form, complete the following steps.
    1.  Note the location in the **Download path** field. It is typically C:\DemoFiles\Retail\CDXDownload. Create these folders on the C drive.
    2.  Note the location in the **Upload path** field. It is typically C:\DemoFiles\Retail\CDXUpload. Create these folders on the C drive.
    3.  Close the form.

10. Click **Data synchronization &gt; Setup &gt; Channel integration &gt; Channel database.**
11. In the **Channel database** form, complete the following steps:
    1.  Select the **HoustonStore** record.
    2.  In the pane on the right side of the form, go to the **Retail Server** section. (You may have to scroll to the bottom of the pane to see it.)
    3.  In the **Server name** field, enter the name of the virtual machine.
    4.  Click the **Full data sync** button at the top of the form. Then, select the 9999 distribution schedule from the list. Click **OK**.
    5.  Close the form.

## 6. Enable users to access Dynamics AX 2012 R3 on Azure
The following sections provide information about how to configure the Azure virtual network and domain so that your corporate users can access Dynamics AX 2012 R3.

### Create a site-to-site VPN connection

To enable corporate users to access resources on the virtual machines in the Azure virtual network, you’ll need to create a site-to-site VPN connection between the Azure virtual network and your on-premises, corporate network. For information about how to do this, see:

-   [Virtual network overview](https://msdn.microsoft.com/library/windowsazure/jj156007.aspx)
-   [Virtual network configuration tasks](https://msdn.microsoft.com/library/jj156206.aspx)
-   [Site-to-site VPN in Azure virtual network using Windows Server 2012 Routing and Remote Access Service (RRAS)](https://msdn.microsoft.com/library/dn636917.aspx)
-   [Configure a virtual network gateway in the management portal](https://msdn.microsoft.com/library/azure/jj156210.aspx)

### Create a domain trust

To enable corporate users to access resources on the virtual machines in your Azure domain, you must create an Active Directory trust between the domains. For information about how to create a trust, see [Create a Forest Trust](https://technet.microsoft.com/library/cc754626.aspx). This process is the same process you would use to create a trust between two on-premises domains.

### Give users access

To enable your users to access Dynamics AX, complete the following tasks:

-   Add each user’s domain account to the Remote Desktop Users group on the CLI-&lt;GUID&gt; virtual machine.
-   Give users access to Dynamics AX. For instructions, see [Create new users in Microsoft Dynamics AX](https://technet.microsoft.com/library/aa548139.aspx).

> [!NOTE]
> If you don’t want to create a VPN connection and a domain trust, you can still give users access to Dynamics AX. To do so, you’ll need to log on to the virtual machine that serves as the domain controller, and create domain accounts for each user. Then, you’ll need to complete the two tasks mentioned above.

## 7. Learn more about the service accounts for this environment
The following sections provide information about the service accounts that were created when you deployed the environment.

### Domain accounts

The following table lists the default names of the domain accounts that were created when you deployed the environment.

| Domain account                  | Description                                                                                                           |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| <DomainName>AOSServiceUser      | The account used to run the following services: Microsoft Dynamics AX Object Server                                   |
| <DomainName>SQLServiceUser      | The account used to run the following services: SQL Server Analysis Services (MSSQLSERVER)                            |
| <DomainName>DynamicsInstallUser | The account used to install Dynamics AX.                                                                              |
| <DomainName>RetailServiceUser   | The account used to run the following services: Microsoft Dynamics AX for Retail Commerce Data Exchange Async Client. |
| <DomainName>BCProxyUser         | The account used as the Business Connector proxy.                                                                     |

> [!NOTE]
> The passwords are displayed on the **Cloud-hosted environments** page in [Lifecycle Services](https://lifecycleservices.dynamics.com/en/).

### Local administrator accounts

Each virtual machine that you deployed has a local administrator account. This account is: builtinaxlocaladmin. The passwords for the local administrator accounts are displayed on the **Cloud-hosted environments** page in [Lifecycle Services](https://lifecycleservices.dynamics.com/en/).



