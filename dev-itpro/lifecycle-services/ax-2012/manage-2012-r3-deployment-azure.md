---
# required metadata

title: Manage your Dynamics AX 2012 R3 deployment on Azure
description: 
author: annbe
manager: AnnBe
ms.date: 2015-12-05 00 - 01 - 40
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
ms.custom: 18491
ms.assetid: 0941f010-3326-4eaf-8015-5b23b1027f27
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: 
ms.dyn365.version: 2012

---

# Manage your Dynamics AX 2012 R3 deployment on Azure



How do I log on to a virtual machine?
-------------------------------------

Complete the following procedure to log on to a virtual machine in you AX 2012 R3 environment.

1.  Log on to [Lifecycle Services](https://lcs.dynamics.com/en/).
2.  Open your project.
3.  Click **Cloud-hosted environments**.
4.  Select the environment that includes the virtual machine that you want to log on to.
5.  Scroll to the right side of the page.
6.  In the **Deployment Status** section, click the link for the virtual machine that you want to log on to.
7.  At the bottom of the page, click **Open** to open the .rdp file for the virtual machine.
8.  When prompted for credentials, enter an appropriate user name and password. See the **Cloud-hosted environments** page for a list of administrative accounts for this environment.

## How do I change the size of a virtual machine?
If you want to change the size of a virtual machine, complete the following steps:

1.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
2.  In the navigation pane on the left, click **Virtual Machines**. The **Virtual machines** page is displayed.
3.  Identify the virtual machine that you want to change the size of by viewing the information in the **Location** column.
4.  Click the name of the virtual machine. The **&lt;Machine name&gt;** page is displayed.
5.  Click **Configure**.
6.  From the **Virtual machine size** list, select a size for the virtual machine.
7.  Click **Save** at the bottom of the page.

## How do I print from a virtual machine?
You can print documents to a local printer when using a virtual machine. The following procedure explains how to connect the virtual machine to your local printer.

1.  Log on to [Lifecycle Services](https://lcs.dynamics.com/en/).
2.  Open your project.
3.  Click **Cloud-hosted environments**. The **Cloud-hosted environments** page is displayed.
4.  Select an environment.
5.  Scroll to the right side of the page to view details about the environment.
6.  Click the link for the virtual machine that you want to log on to.
7.  At the bottom of the page, click **Save** &gt; **Save as** to save the .rdp file. Then, browse to the location where you want to save the .rdp file.
8.  Go to the location where you saved the .rdp file. Then, right-click the .rdp file and choose **Edit**.
9.  The **Remote Desktop Connection** window is displayed. Do the following:
    1.  Click the **Local Resources** tab.
    2.  Select the **Printers** check box.
    3.  Click **Connect**.

10. When prompted for credentials, enter the appropriate user name and password (found on the **Cloud-hosted environments** page).

When you choose to print, documents will be sent to your local printer.

## Can I add a virtual machine to an environment that’s already been deployed?
You can add (or remove) virtual machines to AX 2012 R3 environments that you’ve deployed on Azure. To add virtual machines, complete the following procedure. **Note:** The functionality described in this section does not apply to demo environments or environments that were deployed before August 2014.

1.  Log on to [Lifecycle Services](https://lcs.dynamics.com/en/).
2.  Open your project.
3.  Click **Cloud-hosted environments**. The **Cloud-hosted environments** page is displayed.
4.  Select the environment to which you want to add virtual machines.
5.  Click the Edit (pencil) icon near the top of the page.
6.  Indicate how many virtual machines you want to add to the environment. Then specify the size of those virtual machines.
    -   For information about the software installed on each virtual machine in this environment, see [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](plan-2012-r3-deployment-azure.md).
    -   For sizing and pricing details about virtual machines, see [Virtual machines pricing details](http://azure.microsoft.com/en-us/pricing/details/virtual-machines/).

7.  Click **Software License Terms** to review the licensing terms and conditions. Then select the check box to indicate that you agree to the terms.
8.  Click **Next**.
9.  Click **Deploy** to confirm that you’re ready to deploy the additional virtual machines.

The deployment may take a few hours to complete. When the deployment is done, the **Deployment Status** column on the **Cloud-hosted environments** page will display **Deployed**. You may need to refresh your browser to see this. If the deployment fails, you may see an error message right away. If the error occurs later in the deployment process, error details will be displayed in the details pane on the right-side of the page.

## How do I shut down an environment?
If you want to shut down an AX 2012 R3 environment that you’ve deployed on Azure, complete the following procedure. When you shut down an environment, the environment still exists; however, the virtual machines in the environment are not running. You won’t be charged for the virtual machines when they’re not running.

1.  Log on to [Lifecycle Services](https://lcs.dynamics.com/en/).
2.  Select your project.
3.  Click **Cloud-hosted environments**.
4.  Select the environment that you want to shut down.
5.  Click the Pause (||) icon near the top of the page.
6.  Click **Yes** to confirm that you want to shut down the environment.

When the environment has been shut down, the Deployment Status column will display **Stopped**. You may need to refresh your browser to see this. **Note: **If you stop an environment from the **Cloud-hosted environments** page—and then restart the virtual machines in that environment by using the Azure management portal—the details about that environment won’t be available on the **Cloud-hosted environments** page. For example, you won’t see links to the virtual machines in the environment, or user names and passwords for accounts used in the environment. To resolve this issue, restart the environment by completing the procedure in the following section. **Note: ** Previously, Cloud-hosted environments lacked static IP addresses. When VMs were restarted, new IP addresses were assigned, and as a result, DNS settings becoming invalid. Because of this issue, we did not shut down the SQL and RDS tiers when an environment was stopped. By setting all IP addresses to be static, we help ensure that you won’t have issues when stopping/starting environments. Stopping an environment will now shut down all tiers. We do not expect the stop/start feature to be used on high availability topologies that are actually used in production; however, we do anticipate that the feature will be used when you want to test a high availability topology prior to going live with your production deployment.

## How do I restart an environment?
If you want to restart an AX 2012 R3 environment that has been shut down, complete the following procedure.

1.  Log on to [Lifecycle Services](https://lcs.dynamics.com/en/).
2.  Select your project.
3.  Click **Cloud-hosted environments**.
4.  Select the environment that you want to restart. This environment will currently have a status of **Stopped** in the **Deployment Status** column.
5.  Click the Start (triangle) icon near the top of the page.
6.  Click **Yes** to confirm that you want to restart the environment.

When the environment has been restarted, the **Deployment Status** column will display **Deployed**. You may need to refresh your browser to see this. **Note: **Previously, Cloud-hosted environments lacked static IP addresses. When VMs were restarted, new IP addresses were assigned, and as a result, DNS settings becoming invalid. Because of this issue, we did not shut down the SQL and RDS tiers when an environment was stopped. By setting all IP addresses to be static, we help ensure that you won’t have issues when stopping/starting environments. Stopping an environment will now shut down all tiers. We do not expect the stop/start feature to be used on high availability topologies that are actually used in production; however, we do anticipate that the feature will be used when you want to test a high availability topology prior to going live with your production deployment.

## How do I delete an environment?
When you deploy an environment via the Cloud-hosted environment tool, a set of virtual machines, virtual networks, storage accounts, and databases are deployed to your Azure subscription. When you delete an environment, those resources are deleted. Data backup services are not automatically provided by Lifecycle Services at this time; therefore, you should take the proper actions to backup and secure important data before you delete your environment. To delete an environment, you must be the Project Owner (highest privileged role), or the Environment Owner.

-   **Deallocate - **This option appears on the details page for each deployed environment, and is the first step in deleting an environment. This phase stops and deallocates (so there are no usage charges) all VM resources. No other resources, such as networks, VIPS, endpoints, storage, and databases are impacted. When you click **Deallocate**, you will be asked whether you want to continue. If you continue with the process, the status of the environment will change to **Deallocating** while the VM resources are deallocated. This process will take some time, depending on the size of the environment. Once complete, the status of the environment will change to **Delete Pending**. At this point, if you mistakenly selected **Deallocate**, you can recover the environment with nothing being lost or changed. To recover the environment, click **Start** at the top of the details page.
-   **Delete - **Selecting this option will permanently delete all deployed Azure resources for the environment, and remove references to the environment from the Lifecycle Services project. When you click **Delete**, you will be asked whether you want to continue, and if so, you must enter the name of the project that you’re deleting. The exact name, with exact casing must be provided to proceed. Once entered, the status of the environment will change to **Deletin**g while all Azure resources are deleted for this environment.

Keep in mind, when you deployed the environment, you may have added it to an existing Active Director/virtual network. Deleting an environment does NOT delete any resource that the Cloud-hosted environment tool did not deploy. **Note: **When a Lifecycle Services project is connected to an Azure subscription, a storage account is created in the subscription. This storage account acts as a cache of both VHD and script artifacts associated with all environments that are deployed from that project. In some cases, the VHDs and scripts that are in the storage account are shared among environments. As a result, the Deallocate/Delete operations do not affect this shared storage account. When a deployment is performed with Azure Premium Storage, an additional storage account is created specifically for those VMs and their associated disks. When the environment is deleted, the resources that are stored in the storage account will be deleted; however, the storage account itself will not be deleted because it is a project-level resource.

## How do I delete a Lifecycle Services project and its Azure artifacts?
To delete a Lifecycle Services project, including all of the Azure artifacts that were created when you deployed AX 2012 R3 environments from the project, complete the following procedures.

### 1. Identify the storage account that is associated with the project

Complete the following procedure to identify the Azure storage account that is associated with the Lifecycle Services project that you want to delete. You won’t delete the storage account in this procedure, but you will identify the GUID of the storage account. This GUID will help you identify other, related Azure artifacts that need to be deleted.

1.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
2.  In the navigation pane on the left, click **Virtual Machines**. The **Virtual machines** page is displayed.
3.  Use the information in the **Name** and **Location** columns to identify a virtual machine that is associated with an AX 2012 R3 environment in the project. There may be multiple virtual machines associated with the project; however, you just need to select one. **Note: **To make sure that you’ve identified an appropriate virtual machine, compare the name that you see on this page with the name of the virtual machine that is listed on the **Cloud-hosted environments** page in [Lifecycle Services](https://lcs.dynamics.com/en/).
4.  Click the arrow next to the name of the virtual machine.
5.  Click **Dashboard** at the top of the page.
6.  Scroll down to the **Disks** section of the page.
7.  View the information in the **VHD** column. A URL may look similar to this: https://dyn&lt;GUID&gt;.blob.core.windows.net/dynamicsdeployments... Take note of the GUID. This GUID will help you identify other related artifacts.

### 2. Delete the environments in the project

Delete the AX 2012 R3 environments that exist in the project. For instructions, see  the section in this topic, How do I delete an environment?

### 3. Delete the image files that were used to create virtual machines

Complete the following procedure to delete image files. These image files were used to create the virtual machines for the AX 2012 R3 environments in the Lifecycle Services project. **Note: **If AX 2012 R3 demo environments were the only type of environments deployed from this project, there may be no image files to delete.

1.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
2.  In the navigation pane on the left, click **Virtual Machines**. The **Virtual machines** page is displayed.
3.  Click **Images** at the top of the page.
4.  Sort the list of images by clicking on the **Name** column.
5.  For every image file whose name starts with the GUID of the storage account you identified earlier, complete the following steps:
    1.  Select the row of the image file by clicking in the Status field of that row. **Note:** Be sure that you don’t click in the **Name** field of that row. If you do, a different page is displayed.
    2.  Click **Delete** at the bottom of the page.
    3.  Select the **Delete the associated VHD** option.

### 4. Delete VHD files from the storage account

There are several artifacts that get saved to the storage account associated with each Lifecycle Services project. The largest files are *copies* of the VHD files that were used to create the virtual machines for the AX 2012 R3 environments in the Lifecycle Services project. (These are copies of the VHD files that you deleted in the previous procedure.) You can’t delete a storage account if it contains any VHD files. Complete the following procedure to delete VHD files from the storage account.

1.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
2.  In the navigation pane on the left, click **Storage**. The **Storage** page is displayed.
3.  Identify the storage account that is associated with your project by viewing the information in the **Name** column.
4.  Click the arrow next to the name of the storage account.
5.  Click **Containers** at the top of the page.
6.  Click the arrow next to the deployment catalogs container. A list of the files in the container is displayed.
7.  For each .vhd file in the list, complete the following steps:
    1.  Select the row of the .vhd file.
    2.  Click **Delete** at the bottom of the page. **Note:** You don’t need to delete the PowerShell files in the list. They will be automatically deleted when you delete the storage account in the next procedure.

### 5. Delete the storage account

Complete the following procedure to delete the storage account that is associated with your Lifecycle Services project.

1.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
2.  In the navigation pane on the left, click **Storage**. The **Storage** page is displayed.
3.  Identify the storage account that is associated with your project by viewing the information in the **Name** column.
4.  Select the row for the storage account by clicking in the **Status** field of the row.
5.  Click **Delete** at the bottom of the page.

### 6. Delete the management certificate

Complete the following procedure to delete the management certificate that is associated with the Lifecycle Services project.

1.  Locate the management certificate that you downloaded when you initially connected the project to your Azure subscription. By default, the management certificate is saved to the Downloads folder on your computer and is named **LifecycleServicesDeployment.cer**. If you can’t locate the management certificate on your computer, you can download it again by following these steps:
    1.  Log on to Lifecycle Services.
    2.  Open your project.
    3.  Click **Cloud-hosted environments**.
    4.  Click **Microsoft Azure settings**. The Microsoft Azure setup panel is displayed on the side of the screen.
    5.  Click **Next**.
    6.  Click **Download** to download the management certificate.

2.  Double-click the management certificate (.cer) file, and then click **Open**. The **Certificate** window is displayed.
3.  On the **General** tab, note the name in the **Issued to** field. The certificate is issued to: **DynamicsDeployment\_&lt;GUID&gt;**
4.  Log on to the [Azure management portal](https://manage.windowsazure.com/).
5.  In the navigation pane on the left, click **Settings**. The **Settings** page is displayed.
6.  Click **Management Certificates** at the top of the page. A list of certificates is displayed.
7.  Identify the management certificate that you want to delete by viewing the information in the **Name** column. The name on this page will match the name you identified in step 3.
8.  Select the row for that management certificate and then click **Delete** at the bottom of the page.

### 7. Delete the project

Complete the following procedure to delete the Lifecycle Services project.

1.  Log on to [Lifecycle Services](https://lcs.dynamics.com/en/).
2.  Click **All projects**. The **Project** list page is displayed. **Note:** If you only have one project, that project opens. Click the Back icon in Lifecycle Services to display the **Project** list page.
3.  Select the row for the project that you want to delete.
4.  Click **Remove** at the bottom of the page.

## How is the Azure Internal Load Balancer used?
Test and high availability environments utilize Azure Internal Load Balancer (ILB) around RPC (2712) and WCF ports (8101, 8201) for client components. This allows for high availability in case an instance is down. Azure has a polling method that by default checks every 15 seconds—and—after 2 failures, it removes that node from the ILB. How Microsoft Dynamics AX utilizes ILB is via a Windows hosts file (C:WindowsSystem32driversetchosts). An entry is created with a virtual name (AOSLoadBalancer) and an IP address is assigned (10.1.1.4). From there, the Microsoft Dynamics AX 2012 Configuration is set to AOSLoadBalancer. With the use of Azure PowerShell scripts, ILB is set for 2712, 8101, and 8201 for each AOS instance. Keep in mind that when new AOS instances are added (by using the edit button in Lifecycle Services), these PowerShell scripts are executed to incorporate the new AOS instances being added.

## How do I set up Remote Desktop access via Corpnet connected users?
If you want users to use Remote Desktop via tunneled access to the Azure Virtual Network, you will need to configure Remote Desktop Services (RDS) in your deployment to enable it. When RDS is deployed by using Lifecycle Services, an Azure Internal Load Balancer endpoint is created for the RDS Connection Broker VMs deployed.

1.  The Azure Internal Load Balancer endpoint created by Lifecycle Services can be found in the details pane of the Cloud-Hosted Environments page in Lifecycle Services. Specifically, it is the endpoint domain specified by the link “RDS Farm Access”. It will appear like this: RDSFarm\#\#\#\#\#.domain.com
2.  Obtain the IP address created for this domain by opening [http://manage.windowsazure.com](http://manage.windowsazure.com/) in a browser and logging into your subscription. Open **Cloud Services** and click the Cloud Service name associated with the RDS machines. Locate the RDS\* VM IP that is an internal IP (eg. 10.1.3.4) with port 3389. This is the IP of the Azure Internal Load Balancer associated with the RDSFarm\#\#\#.domain.com address.
3.  Set up the appropriate routing and DNS entries for your users on the corporate network to reach that domain name/IP/load balancer. Once that is done, the users will be able to use Remote Desktop access from the corporate network.


