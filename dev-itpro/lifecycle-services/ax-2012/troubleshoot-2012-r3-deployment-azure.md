---
# required metadata

title: Troubleshoot your Dynamics AX 2012 R3 deployment on Azure | Microsoft Docs
description: This article explains how to resolve common issues and how to get assistance with your Microsoft Dynamics AX 2012 R3 environment on Azure.
author: kfend
manager: AnnBe
ms.date: 2015-12-05 18:03:33
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.suite: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18691
ms.assetid: 0d14d605-64c4-46a1-a9c4-e7e8cad84557
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Troubleshoot your Dynamics AX 2012 R3 deployment on Azure

This article explains how to resolve common issues and how to get assistance with your Microsoft Dynamics AX 2012 R3 environment on Azure.

How do I renew the Windows license on a demo virtual machine?
-------------------------------------------------------------

If you need to renew the trial license for Windows on the virtual machine in a demo environment, complete the following steps.

1.  On the **Cloud-hosted environments** page, select the demo environment.
2.  Scroll to the right side of the page to view details about the environment.
3.  Click the **DEMO-&lt;GUID&gt;** link.
4.  At the bottom of the page, click **Open** to open the .rdp file.
5.  When prompted for credentials, enter the user name and password found on the **Cloud-hosted environments** page for this environment.
6.  When the virtual machine’s desktop is displayed, go to the following location: C:\\DemoFiles\\StartupScripts
7.  Right-click **rearm.cmd**, and then click **Run as administrator**.

A command prompt window will be displayed briefly, and then the virtual machine will restart. The license is now good for 180 days. You can complete this procedure 3 times.

## How do I renew the Microsoft Dynamics AX license on a demo virtual machine?
If you need to renew the license for Microsoft Dynamics AX on the virtual machine in a demo environment, please download the trial license files from [CustomerSource](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/service-packs/AX2012DemoToolsMaterials#DemoVirtualMachineLicenses) or [MSDN](https://msdn.microsoft.com/en-us/subscriptions/securedownloads/hh442898). Then, follow the steps listed in [Provide license information](https://technet.microsoft.com/en-us/library/aa496447.aspx).

## How do I activate Windows on the virtual machines in my nondemo environment?
Windows is automatically activated on the virtual machines that are included with non-demo environments. However, the activation may take up to 4 days to complete. If you continue to see messages that prompt you to activate Windows after 4 days, contact the Azure support team. For information on how to contact the Azure support team, see the following section.

## How do I resolve the following error: ScriptId 'InstallDatabase' failed execution on VM instance
When installing a SQL Server AlwaysOn cluster, if the primary SQL Server instance fails over to the secondary instance, then the installation will fail with the above error. It is unusual for a virtual machine that has just been brought online to fail immediately. We recommend that you delete the deployed topology and redeploy.

## How do I resolve the following error: Script 'CreateAzureFailoverCluster:HASQL1' failed execution
If you have deployed to an existing network and Active Directory—while also customizing the names of the VMs in the topology—you cannot redeploy that same name customization without altering the DNS server in Azure. In this scenario, the DNS server will have the IP addresses of the previous VMs with the same names, and as a result, the deployment will fail. To resolve this issue, you must delete the DNS server entries for those VMs before redeploying.

## The Dynamics AX client crashes on first use.  How do I resolve this?
Dynamics AX clients may crash upon first login after a restart or after a period of inactivity. This is due to a RemoteApp issue that has been fixed in kernel 6.3.3000.287.  If you've deployed a high availability environment or a test environment, you may be using RemoteApp. To resolve this issue, complete one of the following procedures:

### Disable the status bar

1.  In the Dynamics AX client, open the **Options** form (**File** &gt; **Tools** &gt; **Options**)
2.  Click the **Status bar** option.
3.  In the **Show status bar** field, select **None**.

### Install kernel 6.3.3000.287 or later

Kernels are cumulative and the most recent kernel can be found here: <https://blogs.msdn.microsoft.com/axsupport/2012/03/29/overview-of-microsoft-dynamics-ax-build-numbers/>

## How do I monitor for storage account throttling?
To monitor storage account throttling, see [How to Monitor for Storage Account Throttling](https://blogs.msdn.microsoft.com/mast/2014/08/02/how-to-monitor-for-storage-account-throttling/). Alerts and notifications can be utilized to notify you when storage is being throttled. If this is happening, see the [Plan your Microsoft Dynamics AX 2012 R3 deployment on Azure](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/ax-2012/plan-your-microsoft-dynamics-ax-2012-r3-deployment-on-azure) wiki article for information about leveraging multiple Azure Connectors and/or LCS projects.

## How do I contact Support?
If you need to contact Microsoft with licensing or technical questions, you must first determine which support team to contact. Use the information below to best identify which support team to contact.

### Azure support

To obtain support for Azure, use the resources listed in the following table.

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
<td>Get assistance with billing-related questions</td>
<td>Go to the <a href="http://azure.microsoft.com/en-us/support/understand-your-bill/">Understand your bill</a> page to get an overview of the Azure billing process, links to sample invoices, and information about how to download daily usage data for the current billing period.</td>
</tr>
<tr class="odd">
<td>Ask the community</td>
<td>Go to the <a href="http://www.windowsazure.com/en-us/support/forums/">Azure forums</a> page to get help with your questions from the Azure community.</td>
</tr>
<tr class="even">
<td>Use the Azure services dashboard</td>
<td>Go to the <a href="http://www.windowsazure.com/en-us/support/service-dashboard/">Azure services dashboard</a> page to get the current status of the Azure platform and services.</td>
</tr>
<tr class="odd">
<td>Enter a support ticket with the Azure support team</td>
<td>Go to the <a href="http://www.windowsazure.com/en-us/support/options/">Azure support options</a> page, and click Get Support to open a support ticket.The Azure support team can help you resolve issues related to:
<ul>
<li>Requests to increase the size of your Azure subscription</li>
<li>Errors when using the Azure management portal</li>
<li>Issues when configuring a virtual network</li>
<li>Issues when configuring a virtual network gateway</li>
</ul></td>
</tr>
</tbody>
</table>

### 

### Microsoft Dynamics AX support

To obtain support for Microsoft Dynamics AX, use the resources listed in the following table.

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
<td>Get assistance with Microsoft Dynamics AX licensing questions</td>
<td>Contact Microsoft Dynamics Regional Operations Centers by clicking the following PartnerSource links:
<ul>
<li><a href="https://mbs.microsoft.com/partnersource/northamerica/pricing-ordering">Pricing and ordering</a></li>
<li><a href="https://mbs.microsoft.com/partnersource/northamerica/help/help/GlobalOperationsSupportPage">Operations support</a></li>
</ul></td>
</tr>
<tr class="odd">
<td>Ask the community</td>
<td>Go to the <a href="http://go.microsoft.com/fwlink/?LinkId=221068">Microsoft Dynamics AX forum</a> page to get help with your questions from the Microsoft Dynamics AX community.</td>
</tr>
<tr class="even">
<td>Use the Cloud-powered support tool</td>
<td>In <a href="https://lifecycleservices.dynamics.com/en/">Microsoft Dynamics Lifecycle Services</a>, Cloud-powered support is a tool that helps you manage support incidents. Cloud-powered support lets you create a virtual machine in Azure that has the same hotfixes installed as your local environment. You can reproduce and record the incident on the virtual machine, and then submit the virtual machine to our support team. The support team follows up by investigating the incident and testing a fix on the virtual machine. If a fix is found, they send the virtual machine and the fix back to you for verification. For more information, see <a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/cloud-powered-support-lifecycle-services-lcs">Cloud-powered support (Lifecycle Services, LCS)</a>.</td>
</tr>
<tr class="odd">
<td>Use the Issue search tool</td>
<td>In <a href="https://lifecycleservices.dynamics.com/en/">Microsoft Dynamics Lifecycle Services</a>, Issue search is a search engine that you can use to quickly search for KB articles, hotfixes, and workarounds for reported issues in Microsoft Dynamics AX. You can see which reported issues are in the process of being fixed and see notifications when a hotfix is released for a specific functional area in Microsoft Dynamics AX. You can download released hotfixes, see which code objects are affected, and see the code changes introduced by the hotfix. For more information, see <a href="https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/lifecycle-services/issue-search-lifecycle-services-lcs">Issue search (Lifecycle Services, LCS)</a>.</td>
</tr>
<tr class="even">
<td>Enter a support ticket with the Microsoft Dynamics AX support team</td>
<td>Go to the <a href="https://community.dynamics.com/ax/p/support.aspx">Support for Microsoft Dynamics AX</a> page to open a support ticket. The Microsoft Dynamics AX support team can help you resolve technical issues related to:
<ul>
<li>Errors when using Lifecycle Services</li>
<li>Errors when using Microsoft Dynamics AX</li>
</ul></td>
</tr>
</tbody>
</table>

   

