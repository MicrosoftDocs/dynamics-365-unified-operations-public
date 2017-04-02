---
# required metadata

title: Plan your Dynamics AX 2012 R3 deployment on Azure
description: Before you can deploy Microsoft Dynamics AX 2012 R3 on Microsoft Azure, there are several things you must consider and decisions you must make. This article guides you through the planning process. 
author: kfend
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18591
ms.assetid: 84e597d7-6ad3-4322-8ac3-6b6151dd24f6
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Plan your Dynamics AX 2012 R3 deployment on Azure

Before you can deploy Microsoft Dynamics AX 2012 R3 on Microsoft Azure, there are several things you must consider and decisions you must make. This article guides you through the planning process. 

Verify that you can log on to Lifecycle Services
------------------------------------------------

Microsoft Dynamics Lifecycle Services is a cloud-based collaborative workspace that customers and partners can use to manage Microsoft Dynamics AX projects. You’ll use the Cloud-hosted environments tool, available on the Lifecycle Services website, to deploy AX 2012 R3 on Azure. Lifecycle Services is available to customers and partners as part of their support plans. You can access it with your CustomerSource or PartnerSource credentials. **Note:** Microsoft Dynamics AX 2012 R3 is officially supported on Microsoft Azure when deployments are performed through Lifecycle Services. Deployments of Dynamics AX 2012 R3 are not supported on Azure when performed outside of Microsoft Dynamics Lifecycle Services. [Verify that you can log on to Lifecycle Services](https://lcs.dynamics.com/)

## Purchase an Azure subscription
To use Azure, you must purchase a subscription. For information about subscription plans and pricing details, see the [Azure pricing](https://azure.microsoft.com/en-us/pricing/) page. Then follow the instructions on that page to purchase a subscription. The subscription must be large enough to support the AX 2012 R3 environment that you want to deploy on Azure. The following table lists the types of AX 2012 R3 environments that you can deploy on Azure, and the number of cores required to deploy each environment in its default configuration. **Note:** Keep in mind that when you deploy an environment, you can change the number and size of the virtual machines that are deployed. However, this table lists the number of cores required to deploy each environment in its *default* configuration.

**Environment type:** - Demo


| Environment name       | Number of cores to deploy the environment in its default configuration |
|------------------------|------------------------------------------------------------------------|
| AX 2012 R3 demo        | 8 cores                                                                |
| AX 2012 R3 CU8 demo    | 8 cores                                                                |
| Retail essentials demo | 8 cores                                                                |


**Environment type:** - Dev/test


| Environment name                   | Number of cores to deploy the environment in its default configuration |
|------------------------------------|------------------------------------------------------------------------|
| Development                        | 9 cores                                                                |
| Development with shared SQL Server | 14 cores                                                               |
| Test                               | 13 cores                                                               |
| Retail essentials dev/test         | 4 cores                                                                |
| Retail e-commerce dev/test         | 4 cores                                                                |
| Retail mobility dev/test           | 4 cores                                                                |


**Environment type:** - High availability


| Environment name              | Number of cores to deploy the environment in its default configuration |
|-------------------------------|------------------------------------------------------------------------|
| High availability environment | 45 cores                                                               |


If you already have an Azure subscription, note the following:

-   **To view the size of your subscription:** You can view the size of your subscription in the Azure management portal. To do so, log on to the [Azure management portal](https://manage.windowsazure.com/), and then click **Settings** &gt; **Usage**.
-   **To increase the size of your subscription:** To increase the size of your subscription, you’ll need to create a support ticket with the Azure support team. To do so, go to the [Azure support options](http://azure.microsoft.com/en-us/support/options/) page, and then click **Get Support** to create the support ticket. When creating the support ticket, be sure to indicate that the ticket is for billing support.

**Note:** The Cloud Solution Provider (CSP) program is currently not supported with Lifecycle Services due to the Azure Resource Manager (ARM) requirement.

## Purchase and Azure support plan
Azure support plans provide technical and billing support for Azure. The Azure support plans offer flexible support options that will allow you to select the right level of support for your Azure deployment. The support options range from support services included with your Azure subscription at no charge to premier support services. To learn about the available support plans and to purchase a plan, see the [Azure support plans](http://www.windowsazure.com/en-us/support/plans/) page.

## Become familiar with the Azure management portal
The Azure management portal provides developers and IT professionals the ability to provision, configure, monitor, and manage their Azure components. It’s important to become familiar with the management portal because you’ll use it to:

-   Upload a management certificate. (The management certificate enables Lifecycle Services to deploy AX 2012 R3 environments on Azure on your behalf.)
-   Connect to virtual machines.
-   Monitor the health and status of your AX 2012 R3 environment.

After you purchase an Azure subscription, you can access the management portal by clicking [here.](https://manage.windowsazure.com/?whr=live.com) The following image shows the management portal. [![PlanYouAXR3DeploymentonAzure1](./media/planyouaxr3deploymentonazure1.jpg)](./media/planyouaxr3deploymentonazure1.jpg)  

## Become familiar with the Azure VM agent
The Azure VM Agent is now automatically deployed with every VM deployed via Lifecycle Services. The Azure VM Agent is used to install, configure, manage and run Azure Virtual Machine Extensions (VM Extensions). VM extensions can help you monitor and manage your VMs.

## Consider Cloud Services resource requirements
When a topology is deployed, the deployment system will inspect the virtual machine (VM) SKUs that were selected. In order to ensure that Azure deploys these VMs to the proper clusters where the VMs are available, each level of VM SKU must have its own Azure Cloud Service. The VM SKU breakdown is as follows:

|         |                                 |
|---------|---------------------------------|
| **SKU** | **Size**                        |
| A       | Standard A’s \[A0-A4\]          |
| AM      | Standard A's \[A5-A7\]          |
| AL      | Standard A’s (large) \[A8-A11\] |
| D       | Standard D’s \[all D series\]   |
| DS      | Standard DS’s \[all DS series\] |
| G       | Standard G’s \[all G series\]   |

A Cloud Service will be created with the following naming scheme: Version-Topology-EnvironmentName-SKU-GUID Please consider the Cloud Services resource requirements for you deployments and request additional Cloud Services capacity in your Azure Subscription from Azure Support if necessary.

## Plan for storage accounts
For each project created in Lifecycle Services, one or more distinct storage accounts will be created in the Azure subscription. A storage account is created when you connect your project to your Azure subscription. This storage account is a Locally Redundant Storage (LRS) account, and is used to house scripts and VHDs which are required for deployments. An additional Premium storage account is created for each project when the first Premium storage-enabled topology is deployed from the project. Storage accounts are not shared across Lifecycle Services projects, even if the deployments are to the same Azure subscription. When a Premium storage account is created, it too is created as LRS. For more information about storage, click [here](http://azure.microsoft.com/en-us/pricing/details/storage). Consider which topologies and the number of environments that will be deployed into the same Lifecycle Services (LCS) project and Azure Connector. Premium storage account aside, by default there is 1 storage account for each LCS project and Azure Connector. Be aware that Azure storage has [limits](https://azure.microsoft.com/en-us/documentation/articles/azure-subscription-service-limits/#storage-limits), specifically 20,000 IOPS (input/output operations per second) per standard storage account. Combined with 500 IOPS per VHD, that leaves roughly 40 ***highly utilized*** VHDs before throttling occurs. To mitigate this, we recommend that you leverage multiple Azure Connectors and/or multiple LCS projects. For example, consider having production environments in one LCS project, and Dev/Test environments in another. Note: Not all VHDs that LCS deploys will be highly utilized, such as the installation VHD.

## Plan your SQL Server configuration
Azure Premium Storage delivers high-performance, low-latency disk support for I/O intensive workloads running on Azure virtual machines (VMs). With Premium Storage, your applications can have up to 32 TB of storage per VM, achieve 50,000 IOPS per VM, and have extremely low latencies for read operations. Premium Storage is required for AX 2012 R3 deployments that will be used in a production capacity. Premium Storage is enabled by default for High Availability deployments when Azure DS-series VMs are selected. Premium Storage is only offered on DS-series VMs at this time. Premium Storage is enabled exclusively for the SQL Server AlwaysOn database servers, while non-Premium storage is used for all other storage needs. When a SQL Server AlwaysOn availability set is created, Lifecycle Services will attach a disk for every disk slot supported by the DS-series VM selected. For more information about VM disk capacity, click [here](https://msdn.microsoft.com/en-us/library/azure/dn197896.aspx). Different VM sizes will come with varying maximums for throughput and IOPS. As a result, when you are planning your SQL Server configuration, please be familiar with these limitations to ensure that you are deploying the most efficient and cost effective solution for your business. Please follow the guidance found in [Premium Storage: High-Performance Storage for Azure Virtual Machine Workloads](https://azure.microsoft.com/en-us/documentation/articles/storage-premium-storage-preview-portal/), particularly the section, **Throttling when using Premium Storage**. The SQL Server AlwaysOn availability set is created automatically through Lifecycle Services. It is important to consider your data and performance needs before deploying a High Availability topology for use with a production system. Please refer to Azure Premium Storage information [here](http://azure.microsoft.com/en-us/documentation/articles/storage-premium-storage-preview-portal/). Once you have planned your deployment with Premium Storage, the High Availability topology provides configuration options to help you achieve your cost and performance objectives. Under Advanced Settings for the High Availability topology, the following SQL Server configuration options appear:

-   **Customize the SQL Server image configuration** – This option allows the use of a custom SQL Server Enterprise image or an Azure Gallery SQL Server Enterprise image.
    -   Custom SQL Server image (default) – This image contains a trial edition of SQL Server Enterprise 2014. The trial license is enabled for 3-6 months. Use this option if you want to use an existing EA/etc. license.
    -   Gallery SQL Server image – This image contains SQL Server Enterprise 2014 and uses consumption-based Azure pricing. More information can be found on the [Azure Virtual Machines Pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/#sql-server) page and the [SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/azure/jj823132.aspx)
-   **Customize the SQL Server storage space configuration** – You can specify the number and size of the disks that will be attached to the SQL Server VMs.

Keep the following points in mind when specifying the number of disks that should be used to create the storage space within SQL Server:

-   The VM size that is selected for the database server dictates how many disks are supported by that VM SKU. Information about the number of disks that are supported by each VM can be found [here](https://msdn.microsoft.com/en-us/library/azure/dn197896.aspx).
-   One of the available disk slots on the VM will be used by the Lifecycle Services deployment service. This means the VM’s maximum number of disks—minus 1—equals the available slots to fill.
-   Leaving this setting blank will allow the deployment service to attach disks up to the maximum supported by the VM. It is recommended for production deployments that the maximum disks be used.

Keep the following points in mind when specifying the size (in GB) of each disk attached to the VM:

-   Allowed values are 100 GB – 1024 GB.
-   Default is 128 GB.
-   The size of the disk used dictates the Premium Storage tier used.
-   The Premium Storage tier dictates cost, IOPS per disk, and throughput of the system being deployed. For more information, click [here](http://azure.microsoft.com/en-us/pricing/details/storage/).
-   All disks are formatted to 64k cluster size. This results in up to a 20% increase in performance. For more information, click [here](http://tk.azurewebsites.net/2012/08/).

TempDB and logs are deployed onto storage spaces as to benefit from the performance gains. One virtual disk is created over the number of disks configured for the storage space. The virtual disk is then partitioned as follows:

-   SQL data = 1/2 of the total size of pool
-   SQL logs = 1/4 of the total size
-   SQL Temp db = 1/8 of the total size
-   SQL backup = remaining 1/8 of the total size

Other considerations to keep in mind:

-   When planning your deployment, ensure that Premium Storage is available in the Azure region you are targeting. For more information, click [here](http://azure.microsoft.com/en-us/services/preview/).
-   If you have a VPN/Express Route connection (or plan to) between your corporate network and Azure, please ensure this is done for an Azure region that supports Premium Storage.
-   Consult the [Azure Premium Storage documentation](http://azure.microsoft.com/en-us/documentation/services/storage/) to understand limitations of use.
-   If non-Premium Storage VMs are deployed with the High Availability topologies, all of the above SQL Server configuration settings are applicable; however, Premium Storage benefits will not apply.
-   When setting up your Lifecycle Services project for deployment, you must select a region that supports Premium Storage.

SQL Server best practices implemented by the deployment service include those recommended by the SQL Server team. For more information, click [here](http://blogs.technet.com/b/dataplatforminsider/archive/2014/09/12/new-vm-images-optimized-for-transactional-and-dw-workloads-in-azure-vm-gallery.aspx). In addition, the following items are done:

-   Multiple temp files (one per CPU core).
-   Set max memory for SQL Server to 90% of available machine RAM.
-   Set max degree of parallelism.
-   Enabled trace flags  -T1204, -T1222.

## Estimate costs and understand the Azure billing process
To help estimate the cost of your AX 2012 R3 deployment on Azure, use the [Azure pricing calculator](http://azure.microsoft.com/en-us/pricing/calculator/). It’s also important to understand the Azure billing process before you deploy AX 2012 R3 on Azure. For an overview of the Azure billing process, links to sample invoices, and information about how to download daily usage data for the current billing period, see [Understand your bill](http://azure.microsoft.com/en-us/support/understand-your-bill/). **Note: **Keep in mind, you can shut down an AX 2012 R3 environment that has been deployed on Azure when it’s not in use. For example, you may want to shut down an environment on the weekends to reduce costs. When you shut down an environment, the environment still exists; however, the virtual machines in the environment are shut down. You won’t be charged for the virtual machines when they’re not running. For more information, see “How do I shut down an environment?” in the [Manage your Microsoft Dynamics AX 2012 R3 deployment on Azure](manage-2012-r3-deployment-azure.md) article.

## Consider legal and regulatory requirements
Microsoft runs Azure services with common operational practices and features across multiple geographies and jurisdictions. However, it is ultimately up to you to determine if Microsoft services satisfy your regulatory needs. To help provide you with up-to-date information, the [Azure trust center](http://azure.microsoft.com/en-us/support/trust-center/) provides the following information about security, privacy, and compliance.

-   **Security** The [Azure security page](http://www.windowsazure.com/en-us/support/trust-center/security/) provides an overview of the provisions Microsoft is taking to provide a secure environment within geographically dispersed datacenters. Among the extensive list of security-related resources, the [Standard Response to Request for Information: Security and Privacy](https://www.microsoft.com/en-us/download/details.aspx?id=26647) white paper outlines how Azure meets the suggested principals and mapped them to the International Standards Organization (ISO) 27001:2005 and ISO 27002.
-   **Privacy** The [Azure privacy page](http://www.windowsazure.com/en-us/support/trust-center/privacy/) includes links to multiple resources that describe privacy practices of the Azure environment. It includes a link to the [Azure privacy statement](http://www.windowsazure.com/en-us/support/legal/privacy-statement/).
-   **Compliance** The [Azure compliance page](http://www.windowsazure.com/en-us/support/trust-center/compliance/) provides resources to help you comply with the specific laws and regulations applicable to your unique industry and use scenario.

## Consider licensing requirements
Licensing the various components of the AX 2012 R3 virtual machine environment is an important consideration. For deployments on Azure, you will want to evaluate the special licensing terms specific to Azure and the impact that these terms have on the overall suitability of the solution. Licensing requirements vary based on the type of AX 2012 R3 virtual machine environment that you deploy on Azure. The following table provides more information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Type of environment</strong></td>
<td><strong>Licensing requirements</strong></td>
</tr>
<tr class="even">
<td>Demo</td>
<td>The software that is included in the virtual machine environment is time-bound and licensed according to the terms in the Software License Terms.
<ul>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397371">Software License Terms for the AX 2013 R3 demo environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397371">Software License Terms for the AX 2013 R3 CU8 demo environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397371">Software License Terms for the Retail essentials demo environment</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>Dev/test and high availability</td>
<td>All software included in the virtual machine environment must be properly licensed. Please investigate your licensing needs thoroughly with your partner and your Microsoft representative. You will need to investigate the terms for each piece of software that is included in the virtual machine environment. For the complete list of software that is included in the virtual machine environment, review the Software License Terms.
<ul>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397363">Software License Terms for the development environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397363">Software License Terms for the development with shared SQL Server environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397363">Software License Terms for the test environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkID=507496&amp;amp;clcid=0x409">Software License Terms for the Retail essentials dev/test environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkID=507494">Software License Terms for the Retail e-commerce dev/test environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkID=507496">Software License Terms for the Retail mobility dev/test environment</a></li>
<li><a href="http://go.microsoft.com/fwlink/?LinkId=397363">Software License Terms for the high availability environment</a> When reviewing the licensing terms and requirements, you need to pay special attention to any terms that apply specifically to deploying on Azure, as well as terms that apply to your intended use. For example, Microsoft Office has terms that are specific to Azure; but those terms vary depending on whether you deploy Office for development or test purposes, or whether you deploy Office for production purposes.</li>
</ul>
Some resources to help you get started are linked to below. Most of the resources that are linked to below contain links to in-depth information for several products and scenarios; however, you may need to review additional information, as well. This information is provided to help guide your authorized use of products you license; it is not your agreement. Your use of products licensed under your volume license agreement is governed by the terms and conditions of that agreement. In the case of any conflict between information linked here and your agreement, the terms and conditions of your agreement control.
<ul>
<li><strong>Virtual machines licensing FAQ</strong> Common questions regarding licensing on Azure virtual machines are answered on <a href="http://www.windowsazure.com/en-us/pricing/licensing-faq/">this page</a>.</li>
<li><strong>Microsoft Product Use Rights and Product List</strong> Learn more about Microsoft Volume Licensing product licensing models, programs, scenarios, and terms and conditions to help you make effective business decisions and maximize the value of your IT purchases on <a href="https://www.microsoft.com/licensing/about-licensing/product-licensing.aspx">this page</a>.</li>
</ul>
<ul>
<li><strong>License Mobility through Software Assurance on Azure program</strong> License Mobility through Software Assurance gives Microsoft volume licensing customers the flexibility to deploy eligible server applications with active Software Assurance on Azure. With this Software Assurance benefit, there is no need to purchase new licenses and no associated mobility fees. This enables you to easily deploy existing licenses on the Azure cloud platform. For more information, see <a href="http://www.windowsazure.com/en-us/pricing/license-mobility/">this page</a>. For Development, Test, and High Availability topologies trial versions of Sharepoint, Visual Studio, SQL Server, and Office are provided. The trials range from 30-180 days. Please apply licenses accordingly.</li>
<li><strong>Microsoft Dynamics AX volume licensing buyer’s guide</strong> For an overview of key licensing options with Microsoft Dynamics AX, see <a href="https://www.microsoft.com/licensing/about-licensing/dynamicsax.aspx#tab=1">this page</a>.</li>
<li><strong>Shared computer activation for Office 365 ProPlus</strong> Shared computer activation lets you to deploy Office 365 ProPlus to a computer in your organization that is accessed by multiple users. For more information, see <a href="https://technet.microsoft.com/en-us/library/dn782860(v=office.15).aspx">this page</a>.</li>
</ul></td>
</tr>
</tbody>
</table>

## Select the AX 2012 R3 environment that you want to deploy
You’ll use the Cloud-hosted environments tool in Lifecycle Services to deploy AX 2012 R3 environments on Azure. When you use the Cloud-hosted environments tool to deploy, you’ll need to select the type of environment that you want to deploy on Azure, such as a demo or development/test environment. Based on your selection, the Cloud-hosted environments tool provisions the appropriate number of virtual machines on Azure. These virtual machines have AX 2012 R3 components—and all of their prerequisites—already installed on them. The following sections describe the AX 2012 R3 environments that you can deploy on Azure.

-   AX 2012 R3 and AX 2012 R3 CU8 demo environments
-   Retail essentials demo environment
-   Development environments
-   Test environment
-   Retail essentials dev/test environment
-   Retail e-commerce dev/test environment
-   Retail mobility dev/test environment
-   High availability environment

**Note: **In these environments, SQL Server is configured to use the SQL\_Latin1\_General\_CP1\_CI\_AS collation.

## AX 2012 R3 and AX 2012 R3 CU8 demo environments
There are two AX 2012 R3 demo environments: one environment includes Cumulative Update 8, and the other does not. The following table lists details about each environment. **Note: **The virtual machine included in each environment is a single-instance virtual machine. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/).

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Demo machine</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> DEMO-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Active Directory</li>
<li>Domain Name Services (DNS)</li>
<li>Internet Information Services (IIS)</li>
<li>Remote Desktop Services</li>
</ul></li>
<li>Microsoft Visual Studio 2013</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Database Engine Services</li>
<li>Reporting Services</li>
<li>Analysis Services</li>
<li>Management Studio</li>
<li>Developer tools</li>
</ul></li>
<li>Microsoft SharePoint Server 2013</li>
<li>Microsoft Office 2013</li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Databases</li>
<li>Server components:
<ul>
<li>Application Object Server (AOS)</li>
<li>Web server components:
<ul>
<li>Enterprise Portal (EP)</li>
<li>Enterprise Search</li>
<li>Help Server</li>
</ul></li>
</ul></li>
<li>Business intelligence components:
<ul>
<li>Reporting Services extensions</li>
<li>Analysis Services configuration</li>
</ul></li>
<li>Management Reporter components:
<ul>
<li>Management Reporter server components</li>
<li>Management Reporter Report Designer</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
<li>Office add-ins</li>
<li>Remote Desktop Services integration</li>
</ul></li>
<li>Developer tools:
<ul>
<li>Debugger</li>
<li>Visual Studio Tools</li>
<li>Trace Parser</li>
</ul></li>
<li>Integration components:
<ul>
<li>Web services on IIS</li>
<li>.NET Business Connector</li>
</ul></li>
<li>Management utilities</li>
<li>Retail components:
<ul>
<li>Retail POS</li>
<li>Retail Headquarters</li>
<li>Commerce Data Exchange components:
<ul>
<li>Synch Service</li>
<li>Real-time Service</li>
<li>Async Server</li>
<li>Async Client</li>
</ul></li>
<li>Retail Channel Configuration Utility</li>
<li>Retail SDK</li>
<li>Retail online channel</li>
<li>Retail Server</li>
<li>Retail Mass Deployment Toolkit</li>
<li>Retail channel database</li>
</ul></li>
<li>RapidStart Connector</li>
<li>Data Import/Export Framework components:
<ul>
<li>Data Import/Export Framework (DIXF) service</li>
<li>AOS component</li>
<li>Client component</li>
</ul></li>
<li>Warehouse Mobile Devices Portal</li>
<li>Connector for Microsoft Dynamics</li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

 

## Retail Essentials demo environment
Deploy this environment to demo Retail essentials. Retail essentials is a retail-centric configuration option for Microsoft Dynamics AX. This environment includes one virtual machine, by default. This virtual machine has Windows Server—and the software and sample data that you’ll need to demo Retail essentials—already installed on it. The following table lists details about the default Retail essentials demo environment. When you deploy the environment, you can add additional virtual machines to the environment, or change the size of the virtual machines. **Note: **The virtual machines in this environment are single-instance virtual machines. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/).

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Retail essentials demo machine</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> DEMO-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Database Engine Services</li>
<li>Management Studio</li>
<li>Developer tools</li>
</ul></li>
<li>AX 2012 R3 components:
<ul>
<li>Databases</li>
<li>Server components:
<ul>
<li>Application Object Server (AOS)</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
</ul></li>
<li>Integration components:
<ul>
<li>.NET Business Connector</li>
</ul></li>
<li>Retail components:
<ul>
<li>Retail Headquarters</li>
<li>Commerce Data Exchange components:
<ul>
<li>Real-time Service</li>
<li>Async Server</li>
<li>Async Client</li>
</ul></li>
<li>Retail channel database</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

 

## Development environments
Deploy these development environments when you need to quickly jumpstart a development effort for one to many developers. Deploy a development virtual machine (VM) for each of your developers in a matter of hours instead of days. With a development environment, you have all the same domain and virtual network customizations that you have with the Test environment. Two topology options are provided for developer scenarios:

-   Development: Includes all-in-one VMs deployed with Active Directory.
-   Development with shared SQL Server: Includes all-in-one VMs deployed with Active Directory. The database for each development VM instance will be deployed to a shared SQL Server instance.

For those doing BI development you can deploy one instance for the purpose. All other instances will not deploy with BI. The development VMs provided have all the AX 2012 R3 components installed with Visual Studio 2013 and AX 2012 R3 development tools. The VMs are joined to the Active Directory domain at deployment time. If you provided an Active Directory domain as a customization option, then the VMs will join to that domain. Development VMs will be deployed up to the point of the AX 2012 R3 checklist, and have all the software installed that is listed in the Test environment. **Note: **The virtual machines in this environment are single-instance virtual machines. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/).

## Test environment
This environment includes several virtual machines, by default. These virtual machines have Windows Server—and the software that you’ll need for AX 2012 R3 testing purposes—already installed on them. The following table lists details about the default test environment. When you deploy the environment, you can add additional virtual machines to the environment, or change the size of the virtual machines. **Note: **The virtual machines in this environment are single-instance virtual machines. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/). **Note: **Data Import/Export Framework (DIXF) components are not installed by default. If you want to use DIXF, you must use your own SQL Server installation media to install SQL Server Integration Services (SSIS) on the SQL Server machine. After you install SSIS, you can use the Dynamics AX CD (available on a connected drive within the VMs) to install the DIXF components on the AOS and then client machines.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Domain controller</td>
<td><strong>Size:</strong> D1: Basic compute tier (1 core, 3.5 GB memory)<strong>Default name:</strong> AD-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Active Directory</li>
<li>Domain Name Services (DNS)</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>1</td>
<td>AOS server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> AOS-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Internet Information Services (IIS)</li>
</ul></li>
<li>Microsoft Visual Studio 2013</li>
<li>Microsoft Project Server</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Management Studio</li>
<li>Native Client</li>
</ul></li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Server components:
<ul>
<li>Application Object Server (AOS)</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
<li>Office add-ins</li>
<li>Remote Desktop Services integration</li>
</ul></li>
<li>Integration components:
<ul>
<li>Web services on IIS</li>
<li>.NET Business Connector</li>
</ul></li>
<li>Management utilities</li>
<li>Retail components:
<ul>
<li>Retail Headquarters</li>
<li>Commerce Data Exchange components:
<ul>
<li>Synch Service</li>
<li>Real-time Service</li>
<li>Async Server</li>
</ul></li>
</ul></li>
<li>RapidStart Connector</li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>1</td>
<td>Database server/BI server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> SQL-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Database Engine Services</li>
<li>Reporting Services</li>
<li>Analysis Services</li>
<li>Management Studio</li>
</ul></li>
</ul>
<strong>Note:</strong> Reporting Services is configured to run in Native mode. To use Power View, you’ll need to complete additional configuration steps. For more information, see the prerequisites listed in <a href="https://technet.microsoft.com/en-us/library/jj933492.aspx">Create a report by using Power View to connect to a cube</a>.
<ul>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Databases</li>
<li>Business intelligence components:
<ul>
<li>Reporting Services extensions</li>
<li>Analysis Services configuration</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>0</td>
<td>Enterprise Portal server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> EP-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Internet Information Services (IIS)</li>
</ul></li>
<li>Microsoft SQL Server 2012 components:
<ul>
<li>Full-text Search</li>
</ul></li>
<li>Microsoft SharePoint Server 2013</li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Server components:
<ul>
<li>Web server components:
<ul>
<li>Enterprise Portal (EP)</li>
<li>Enterprise Search</li>
<li>Help Server</li>
</ul></li>
</ul></li>
<li>Management Reporter components:
<ul>
<li>Management Reporter server components</li>
</ul></li>
<li>Retail components:
<ul>
<li>Commerce Data Exchange components:
<ul>
<li>Async Client</li>
</ul></li>
<li>Retail Server</li>
<li>Retail Online Channel</li>
<li>Retail Channel Database</li>
<li>Retail Channel Configuration Utility</li>
<li>Retail Hardware Station</li>
</ul></li>
<li>Warehouse Mobile Devices Portal</li>
<li>Connector for Microsoft Dynamics</li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>1</td>
<td>Client computer</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> CLI-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft Visual Studio 2013</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Developer tools</li>
</ul></li>
<li>Microsoft SharePoint Server 2013 Client Components SDK</li>
<li>Microsoft Office 365 ProPlus</li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Management Reporter components:
<ul>
<li>Management Reporter Report Designer</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
<li>Office add-ins</li>
<li>Remote Desktop Services integration</li>
</ul></li>
<li>Developer tools:
<ul>
<li>Debugger</li>
<li>Visual Studio Tools</li>
<li>Trace Parser</li>
</ul></li>
<li>Management utilities</li>
<li>Retail components:
<ul>
<li>Retail POS</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>0</td>
<td>Remote Desktop Services server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> RDS-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Internet Information Services (IIS)</li>
<li>Remote Desktop Services</li>
</ul></li>
<li>Microsoft SQL Server 2012 Native Client</li>
</ul></td>
</tr>
</tbody>
</table>

 

## Retail Essentials dev/test environment
Deploy this environment to develop or test features for Retail essentials. This environment includes one virtual machine, by default. This virtual machine has Windows Server—and the software that you’ll need for Retail essentials development and testing purposes—already installed on it. The following table lists details about the default Retail essentials dev/test environment. When you deploy the environment, you can add additional virtual machines to the environment, or change the size of the virtual machines. **Note: **The virtual machines in this environment are single-instance virtual machines. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/).

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Retail essentials server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> ESSEN-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Database Engine Services</li>
<li>Management Studio</li>
<li>Developer tools</li>
</ul></li>
<li>AX 2012 R3 components:
<ul>
<li>Databases</li>
<li>Server components:
<ul>
<li>Application Object Server (AOS)</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
</ul></li>
<li>Integration components:
<ul>
<li>.NET Business Connector</li>
</ul></li>
<li>Retail components:
<ul>
<li>Retail Headquarters</li>
<li>Commerce Data Exchange components:
<ul>
<li>Real-time Service</li>
<li>Async Server</li>
<li>Async Client</li>
</ul></li>
<li>Retail channel database</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

 

## Retail ecommerce dev/test environment
Deploy this environment to create and test an online sales channel that is fully integrated with AX 2012 R3. This environment includes one virtual machine, by default. This virtual machine has Windows Server—and the software that you’ll need for Retail e-commerce—already installed on it. The following table lists details about the default Retail e-commerce dev/test environment. When you deploy the environment, you can add additional virtual machines to the environment, or change the size of the virtual machines. **Note: **The virtual machines in this environment are single-instance virtual machines. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/).

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Retail e-commerce server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> E-COM-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft SharePoint Server 2013</li>
<li>AX 2012 R3 components:
<ul>
<li>Retail components:
<ul>
<li>Commerce Data Exchange components:
<ul>
<li>Async Client</li>
</ul></li>
<li>Retail online channel</li>
<li>Retail channel database</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

 

## Retail mobility dev/test environment
Deploy this environment to enable your sales staff to process sales transactions, enter customer orders, and perform daily operations and inventory management with mobile devices anywhere in a store. This environment includes one virtual machine, by default. This virtual machine has Windows Server—and the software that you’ll need for Retail mobility—already installed on it. The following table lists details about the default Retail mobility dev/test environment. When you deploy the environment, you can add additional virtual machines to the environment, or change the size of the virtual machines. **Note: **The virtual machines in this environment are single-instance virtual machines. Single-instance virtual machines are not covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/).

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>1</td>
<td>Retail server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> MOBIL-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>AX 2012 R3 components:
<ul>
<li>Retail components:
<ul>
<li>Commerce Data Exchange components:
<ul>
<li>Async Client</li>
</ul></li>
<li>Retail Server</li>
<li>Retail channel database</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

 

## High availability environment
Deploy this environment to use AX 2012 R3 in an environment that can be configured for high availability. This environment includes several virtual machines. These virtual machines have Windows Server—and the software that you’ll need to use AX 2012 R3—already installed on them. The following table lists details about the default high availability environment. When you deploy the environment, you can add additional virtual machines to the environment, or change the size of the virtual machines. **Note: **Azure Premium Storage is required for high availability environments. For more information, see [Deploy a high availability environment on Azure](deploy-high-availability-environment-azure.md). **Note:** The virtual machines in this environment are covered by an Azure [Service Level Agreement](http://azure.microsoft.com/en-us/support/legal/sla/). **Note: **Data Import/Export Framework (DIXF) components are not installed by default. If you want to use DIXF, you must use your own SQL Server installation media to install SQL Server Integration Services (SSIS) on the SQL Server machine. After you install SSIS, you can use the Dynamics AX CD (available on a connected drive within the VMs) to install the DIXF components on the AOS and then client machines.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Number of virtual machines deployed by default</strong></td>
<td><strong>Description</strong></td>
<td><strong>Size and name</strong></td>
<td><strong>Software installed</strong></td>
</tr>
<tr class="even">
<td>3<strong>Note: </strong>Three domain controllers are deployed in this environment. If one domain controller fails, you must be left with two, online domain controllers in order to meet Azure’s <a href="http://azure.microsoft.com/en-us/support/legal/sla/">Service Level Agreement</a>.</td>
<td>Domain controller</td>
<td><strong>Size:</strong> D1: Basic compute tier (1 core, 3.5 GB memory)<strong>Default name:</strong> AD-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Active Directory</li>
<li>Domain Name Services (DNS)</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>2</td>
<td>AOS server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> AOS-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Internet Information Services (IIS)</li>
</ul></li>
<li>Microsoft Visual Studio 2013</li>
<li>Microsoft Project Server</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Management Studio</li>
<li>Native Client</li>
</ul></li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Server components:
<ul>
<li>Application Object Server (AOS)</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
<li>Office add-ins</li>
<li>Remote Desktop Services integration</li>
</ul></li>
<li>Integration components:
<ul>
<li>Web services on IIS</li>
<li>.NET Business Connector</li>
</ul></li>
<li>Management utilities</li>
<li>Retail components:
<ul>
<li>Retail Headquarters</li>
<li>Commerce Data Exchange components:
<ul>
<li>Synch Service</li>
<li>Real-time Service</li>
<li>Async Server</li>
</ul></li>
</ul></li>
<li>RapidStart Connector</li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>2</td>
<td>Database server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> SQL-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Database Engine Services</li>
<li>Management Studio</li>
</ul></li>
</ul>
<table>
<tbody>
<tr class="odd">
<td><strong>Note</strong></td>
</tr>
<tr class="even">
<td>A Quorum server is also deployed. This virtual machine is a listener for the AlwaysOn availability group. This virtual machine:o    Is not represented in the High Availability VM list, but it is deployed with High Availability environments.o    Is named QRM-&lt;GUID&gt;. This name can’t be customized.o    Is an A2 virtual machine.o    Runs a gallery image of Windows Server 2012 R2.o    Post deployment, this VM appears as a “Database Server” when adding VMs to the High Availability environment. The 3rd VM referenced here is the A2 Quorum Server which is explicitly not a SQL Server.</td>
</tr>
<tr class="odd">
<td><strong>Note</strong></td>
</tr>
<tr class="even">
<td>Reporting Services is configured to run in Native mode. To use Power View, you’ll need to complete additional configuration steps. For more information, see the prerequisites listed in <a href="https://technet.microsoft.com/en-us/library/jj933492.aspx">Create a report by using Power View to connect to a cube</a>.</td>
</tr>
</tbody>
</table>
<ul>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Databases</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>2</td>
<td>Business intelligence (BI) server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> BI-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Database Engine Services</li>
<li>Reporting Services</li>
<li>Analysis Services</li>
<li>Management Studio</li>
</ul></li>
</ul>
<table>
<tbody>
<tr class="odd">
<td><strong>Note</strong></td>
</tr>
<tr class="even">
<td>Reporting Services is configured to run in Native mode. To use Power View, you’ll need to complete additional configuration steps. For more information, see the prerequisites listed in <a href="https://technet.microsoft.com/en-us/library/jj933492.aspx">Create a report by using Power View to connect to a cube</a>.</td>
</tr>
</tbody>
</table>
<ul>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Business intelligence components:
<ul>
<li>Reporting Services extensions</li>
<li>Analysis Services configuration</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>0</td>
<td>Enterprise Portal server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> EP-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Internet Information Services (IIS)</li>
</ul></li>
<li>Microsoft SQL Server 2012 components:
<ul>
<li>Full-text Search</li>
</ul></li>
<li>Microsoft SharePoint Server 2013</li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Server components:
<ul>
<li>Web server components:
<ul>
<li>Enterprise Portal (EP)</li>
<li>Enterprise Search</li>
<li>Help Server</li>
</ul></li>
</ul></li>
<li>Management Reporter components:
<ul>
<li>Management Reporter server components</li>
</ul></li>
<li>Retail components:
<ul>
<li>Commerce Data Exchange components:
<ul>
<li>Async Client</li>
</ul></li>
<li>Retail Server</li>
<li>Retail Online Channel</li>
<li>Retail Channel Database</li>
<li>Retail Channel Configuration Utility</li>
<li>Retail Hardware Station</li>
</ul></li>
<li>Warehouse Mobile Devices Portal</li>
<li>Connector for Microsoft Dynamics</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>2</td>
<td>Client computer</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> CLI-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2</li>
<li>Microsoft Visual Studio 2013</li>
<li>Microsoft SQL Server 2014 components:
<ul>
<li>Developer tools</li>
</ul></li>
<li>Microsoft SharePoint Server 2013 Client Components SDK</li>
<li>Microsoft Office 365 ProPlus</li>
<li>AX 2012 R3 or AX 2012 R3 CU8 components:
<ul>
<li>Management Reporter components:
<ul>
<li>Management Reporter Report Designer</li>
</ul></li>
<li>Client components:
<ul>
<li>Client</li>
<li>Office add-ins</li>
<li>Remote Desktop Services integration</li>
</ul></li>
<li>Developer tools:
<ul>
<li>Debugger</li>
<li>Visual Studio Tools</li>
<li>Trace Parser</li>
</ul></li>
<li>Management utilities</li>
<li>Retail components:
<ul>
<li>Retail POS</li>
</ul></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td>2</td>
<td>Remote Desktop Services server</td>
<td><strong>Size:</strong> D3: Standard compute tier (4 cores, 14 GB memory)<strong>Default name:</strong> RDS-&lt;GUID&gt;</td>
<td><ul>
<li>Windows Server 2012 R2, including:
<ul>
<li>Internet Information Services (IIS)</li>
<li>Remote Desktop Services</li>
</ul></li>
<li>Microsoft SQL Server 2012 Native Client</li>
</ul></td>
</tr>
</tbody>
</table>

 

## Next steps
- [Deploy an AX 2012 R3 or AX 2012 R3 CU8 demo environment on Azure](deploy-ax-2012-r3-ax-2012-r3-cu8-demo-environment-azure.md) 
- [Deploy a Retail essentials demo environment on Azure](deploy-retail-essentials-demo-environment-azure.md) 
- [Deploy a development environment on Azure](deploy-development-environment-azure.md) 
- [Deploy a test environment on Azure](deploy-test-environment-azure.md) 
- [Deploy a Retail essentials dev/test environment on Azure](deploy-retail-essentials-devtest-environment-azure.md) 
- [Deploy a Retail e-commerce dev/test environment on Azure](deploy-retail-ecommerce-devtest-environment-azure.md) 
- [Deploy a Retail mobility dev/test environment on Azure](deploy-retail-mobility-devtest-environment-azure.md) 
- [Deploy a high availability environment on Azure](deploy-high-availability-environment-azure.md)

