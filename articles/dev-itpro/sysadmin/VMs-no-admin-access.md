---
# required metadata

title: FAQ about virtual machines that do not allow administrator access
description: This topic provides answers to frequantly asked questions (FAQs) about virtual machiens that do not allow administrator access.
author: yukonpeegs
manager: AnnBe
ms.date: 03/22/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Platform 
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: epegors
ms.search.validFrom: 2017-11-30 
ms.dyn365.ops.version: Platform update 12 

---

# FAQ about virtual machines that do not allow administrator access

[!include[banner](../includes/banner.md)]

This topic provides answers to frequently asked questions about platform udpate 12 and later Tier 1 virutal machines (VMs) that do not allow administrator access.

## How can I install a deployable package?  
When possible, use Lifecyle Services (LCS) to install a package. You can install a deployable package using the -devinstall option. Keep in mind that this option requires a manual database sync.

For more information about how to install a deployable package, see [Install a deployable package](../deployment/install-deployable-package.md).  

## Is the Dynamics 365 for Finance and Operations web site accessible when Visual Studio (VS) is not running?  
Yes, IIS Express is an .EXE running as your user, but when you close VS the XPPC agent will start regular IIS (not IIS Express) before it shuts down. This ensures that even when you log off or the machine reboots, the AOS and Finance and Operations web site are accessible remotely. We recognize many people use these devoper machines as test machines and they expect the AOS to always be running, which can’t be done with IIS Express.  

## What about the other services?  
You can restart Windows services such as SQL Server, SQL Server Reporting Services (SSRS), SQL Server Integration Services (SSIS), SQL Server Analysis Services (SSAS), Batch, MR, and IIS (using the World Wide Web Windows service, not iisreset.exe).  

## Will I be able to clean up the service volume drive?  
Yes, you have full access to the service volume drive, so you can clean up the monitoring data, etc.

## What are the alternatives to the VM that do not allow administrator access?  
An Azure VM on a private Azure subscription and a local VHD allow administrator access. In this case you need to run VS as an administrator. This is because only the administrator has access to these things through the “administrator” group and not explicitly.  

## Can VS be run as an administrator?  
Starting with platform update 12, this is no longer required. Connecting via RDP to a VM as an administrator is no longer allowed for VMs under a Microsoft-owned Azure subscription such as the tier 1 VM included in the subscription and tier 1 add-on VMs. However, if you are connecting as an administrator to a VM not under a Microsoft-owned subscription, you must still run VS as an administrator.  

## A "get latest" in VS fails because files are blocked by the AOS. How do we start / stop IIS?  
You have to use IIS Express. See the next question for more information.  

## What are the instructions for using IIS Express?  
IIS Express, when started, shows an icon in the notification area (near the clock) where it shows all the running sites. You can stop if from that menu. A start in IIS Express will be triggered by some actions in VS, but you can also explicitly do it with the menu item in the “Dynamics 365” menu “Restart IIS Express.”  

## How to apply a partner VS license which is not tied to the VS log-in account that is likely within the customer AAD / domain?  
This is not supported.  

## Can additional development tools (e.g. Fiddler, Pepper, etc.) be installed?  
This is not supported.  

## Is there a way to run PowerShell & Command Prompt commands as an administrator?  
This is not supported.  

## Is the Trace Parser supported?  
It is currently not supported but we will support it again soon.  

## Is putting the system in maintenance mode supported?  
Putting the system in maintenance mode to change the license configuration is supported, but using the procedure described in [Maintenance mode](maintenance-mode.md) is not supported. Self-service support for maintenance mode in all environments will be added to LCS in the future. Until it is available in LCS, you can use the following steps to put a system in maintenance mode.

1.	RDP onto the developer machine.

2.	Log in to SQL Server on the developer machine using the credentials from LCS for the axdbadmin user. Then switch to the AXDB database and run the following command:

  update SQLSYSTEMVARIABLES SET VALUE = 1 where PARM = 'CONFIGURATIONMODE'
  
3.	Restart the **World Wide Web Publishing Service** service to reset IIS.

  After it is restarted, it will be in maintenance mode.
  
4.	Reverse the steps when done with maintenance mode activities. Set the value to 0 and restart the **World Wide Web Publishing Service** service.  

## Is installing a license deployable package supported?  
This should work with the -devinstall option but a problem was found with this scenario and we are working on it.  
