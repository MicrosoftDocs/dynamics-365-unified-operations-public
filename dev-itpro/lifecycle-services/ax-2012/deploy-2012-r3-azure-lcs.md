---
# required metadata

title: Deploy Dynamics AX 2012 R3 on Azure using Lifecycle Services
description: 
author: kfend
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
ms.reviewer: kfend
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18231
ms.assetid: 18a1ba1e-5c75-4cff-95f7-ec0beef0a28e
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Deploy Dynamics AX 2012 R3 on Azure using Lifecycle Services



Azure is an open and flexible cloud platform that enables you to quickly build, deploy, and manage applications across a global network of datacenters that are managed by Microsoft. Azure enables *cloud computing*. Cloud computing is the delivery of computing capabilities as a service. Cloud computing makes it easy to access IT resources such as computers, networking, and storage. As with any utility, you generally only pay for what you use with cloud computing. By using cloud services, you can harness the power of massive datacenters without having to build, manage, or maintain costly, complex IT building blocks. With the cloud, much of the complexity of IT is abstracted away, letting you focus on the infrastructure, data, and application development that really matter to your business. You can deploy AX 2012 R3 on Azure. When you do, you may realize the following benefits:

-   **Reduce costs** Since you don’t have to build out or manage infrastructure with Azure, IT costs may be greatly reduced.
-   **Save time** An on-premises AX 2012 R3 environment may take weeks to plan, acquire necessary hardware, and deploy. By using the Cloud-hosted environments tool in Lifecycle Services, you can deploy an AX 2012 R3 environment on Azure in hours.
-   **Gain flexibility** The cloud enables you to easily scale up (or scale down) to meet the changing needs of your business.

## The Azure services model
Azure offers three types of services: Software-as-a-Service (SaaS), Platform-as-a-Service (PaaS), and Infrastructure-as-a-Service (IaaS).

|                                    |            |                                                                                                                                                                                                                            |
|------------------------------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Type of service**                | **Use to** | **Description**                                                                                                                                                                                                            |
| Software as a service (SaaS)       | Consume    | You use a web browser to use applications that are hosted in the cloud.                                                                                                                                                    |
| Platform as a service (PaaS)       | Build      | You don’t manage or control the network, servers, or operating system. PaaS is more developer-oriented. It allows you to focus on the business logic of applications and quickly move applications from concept to launch. |
| Infrastructure as a service (IaaS) | Host       | You have control over your virtual machines and the network configuration, but you don’t have to worry about hardware.                                                                                                     |

When you deploy AX 2012 R3 on Azure, you will be using the IaaS offering. This means that Azure provides the virtual machines, storage, and networking capabilities. You must manage and secure the operating systems, applications, and data installed on the virtual machines. [![DeployAXonAzureUsingLCS1](./media/deployaxonazureusinglcs1.jpg)](./media/deployaxonazureusinglcs1.jpg)

## Architecture of AX 2012 R3 on Azure
To deploy AX 2012 R3 on Azure, you can use Microsoft Dynamics Lifecycle Services. Lifecycle Services is a cloud-based collaborative workspace that customers and partners can use to manage Microsoft Dynamics AX projects. The Cloud-hosted environments tool, available on the Lifecycle Services website, helps you deploy AX 2012 R3 environments on Azure. When you use the Cloud-hosted environments tool to deploy, you’ll need to select the type of environment that you want to deploy on Azure, such as a demo or development/test environment. Based on your selection, the Cloud-hosted environments tool provisions the appropriate number of virtual machines on Azure. These virtual machines have AX 2012 R3 components—and all of their prerequisites—already installed on them. For example, if you deploy an AX 2012 R3 test environment, the architecture looks like this: 
[![DeployAXonAzureUsingLCS2](./media/deployaxonazureusinglcs2.jpg)](./media/deployaxonazureusinglcs2.jpg)   

You can deploy the following types of AX 2012 R3 environments on Azure with the Cloud-hosted environments tool:

**Demo environment**

| Environment            | Description                                                                                                                                                                                                                                                             |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AX 2012 R3 demo        | Deploy this environment to demo AX 2012 R3. This environment includes 1 virtual machine. This virtual machine has Windows Server—and the software and sample data that you’ll need to demo AX 2012 R3—already installed on it.                                          |
| AX 2012 R3 CU8 demo    | Deploy this environment to demo AX 2012 R3 Cumulative Update 8.This environment includes 1 virtual machine. This virtual machine has Windows Server—and the software and sample data that you’ll need to demo AX 2012 R3 CU8—already installed on it.                   |
| Retail essentials demo | Deploy this environment to demo Retail essentials for AX 2012 R3. This environment includes 1 virtual machine, by default. This virtual machine has Windows Server—and the software and sample data that you’ll need to demo Retail essentials—already installed on it. |

**Dev/test environment**

| Environment                        | Description                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Development                        | Deploy this environment to develop features for AX 2012 R3.This environment includes 2 virtual machines, by default. These virtual machines have Windows Server—and the software that you’ll need for AX 2012 R3 development purposes—already installed on them.                                                                                                                       |
| Development with shared SQL Server | Deploy this environment to develop features for AX 2012 R3. The database for each development VM instance will be deployed to a shared SQL Server instance.This environment includes 3 virtual machines, by default. These virtual machines have Windows Server—and the software that you’ll need for AX 2012 R3 development purposes—already installed on them.                       |
| Test                               | Deploy this environment to test features for AX 2012 R3.This environment includes 4 virtual machines, by default. These virtual machines have Windows Server—and the software that you’ll need for AX 2012 R3 testing purposes—already installed on them.                                                                                                                              |
| Retail essentials dev/test         | Deploy this environment to develop or test features for Retail essentials for AX 2012 R3.This environment includes 1 virtual machine, by default. This virtual machine has Windows Server—and the software that you’ll need for Retail essentials development and testing purposes—already installed on it.                                                                            |
| Retail e-commerce dev/test         | Deploy this environment to create and test an online sales channel that is fully integrated with AX 2012 R3.This environment includes 1 virtual machine, by default. This virtual machine has Windows Server—and the software that you’ll need for Retail e-commerce—already installed on it.                                                                                          |
| Retail mobility dev/test           | Deploy this environment to enable your sales staff to process sales transactions, enter customer orders, and perform daily operations and inventory management with mobile devices anywhere in a store.This environment includes 1 virtual machine, by default. This virtual machine has Windows Server—and the software that you’ll need for Retail mobility—already installed on it. |

**High availability environment**

| Environment       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| High availability | Deploy this environment to use AX 2012 R3 in an environment that can be configured for high availability. This environment includes 14 virtual machines, by default. These virtual machines have Windows Server—and the software that you’ll need to use AX 2012 R3 — already installed on them. Note: When you deploy this environment, the AX 2012 R3 CU8 version of this environment is deployed by default. If you want to deploy the AX 2012 R3 RTM version, you can select that version during deployment. |

For more information about the virtual machines, and the software installed on each virtual machine in these environments, see [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](plan-2012-r3-deployment-azure.md).

## The process for deploying AX 2012 R3 on Azure
The process for deploying AX 2012 R3 on Azure is complex and should be completed by system implementers who have experience with:

-   **Licensing requirements** You’ll need to provide license information for the software included in the AX 2012 R3 environment. This documentation will point you to resources to help you complete this task, but will not provide a step-by-step procedure for completing this task.
-   **Networks and domains** To enable users in your corporate network to easily access the virtual machines on Azure, you’ll need to create a site-to-site VPN connection. This documentation will point you to resources to help you create the VPN connection, but will not provide a step-by-step procedure for completing this task.

To deploy AX 2012 R3 on Azure, see the articles that are listed in the following table.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Task</strong></td>
<td><strong>More information</strong></td>
</tr>
<tr class="even">
<td>Plan your deployment</td>
<td>Before you can deploy AX 2012 R3 on Azure, there are several things you must consider and decisions you must make. For example, you must consider licensing requirements, purchase an Azure subscription, and select the type of AX 2012 R3 environment that you will deploy on Azure.For more information, see <a href="plan-2012-r3-deployment-azure.md">Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure</a>.</td>
</tr>
<tr class="odd">
<td>Deploy AX 2012 R3 on Azure</td>
<td>Microsoft Dynamics Lifecycle Services is a cloud-based collaborative workspace that customers and partners can use to manage Microsoft Dynamics AX projects. You’ll use the Cloud-hosted environments tool in Lifecycle Services to deploy AX 2012 R3 on Azure.To deploy a demo environment, see:
<ul>
<li><a href="deploy-ax-2012-r3-ax-2012-r3-cu8-demo-environment-azure.md">Deploy an AX 2012 R3 or AX 2012 R3 CU8 demo environment on Azure</a></li>
<li><a href="deploy-retail-essentials-demo-environment-azure.md">Deploy a Retail essentials demo environment on Azure</a></li>
</ul>
To deploy a dev/test environment, see:
<ul>
<li><a href="deploy-development-environment-azure.md">Deploy a development environment on Azure</a></li>
<li><a href="deploy-test-environment-azure.md">Deploy a test environment on Azure</a></li>
<li><a href="deploy-retail-essentials-devtest-environment-azure.md">Deploy a Retail essentials dev/test environment on Azure</a></li>
<li><a href="deploy-retail-ecommerce-devtest-environment-azure.md">Deploy a Retail e-commerce dev/test environment on Azure</a></li>
<li><a href="deploy-retail-mobility-devtest-environment-azure.md">Deploy a Retail mobility dev/test environment on Azure</a></li>
</ul>
To deploy an environment that can be configured for high availability, see:
<ul>
<li><a href="deploy-high-availability-environment-azure.md">Deploy a high availability environment on Azure</a></li>
</ul></td>
</tr>
<tr class="even">
<td>Manage your AX 2012 R3 environment on Azure</td>
<td>To help you manage your AX 2012 R3 environment on Azure, see the tips and tricks in <a href="manage-2012-r3-deployment-azure.md">Manage your Microsoft Dynamics AX 2012 R3 deployment on Azure</a>.</td>
</tr>
<tr class="odd">
<td>Troubleshoot issues that may occur</td>
<td>If you need to contact Microsoft with licensing questions or technical issues, you must first determine which support team to contact: the Azure support team or the Microsoft Dynamics AX support team. For information about when and how to contact each support team, see <a href="troubleshoot-2012-r3-deployment-azure.md">Troubleshoot your Microsoft Dynamics AX 2012 R3 deployment on Azure</a>.</td>
</tr>
</tbody>
</table>



