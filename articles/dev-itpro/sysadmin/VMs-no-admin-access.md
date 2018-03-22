---
# required metadata

title: Virtual machines that do not allow administrator access
description: This topic provides answers to frequantly asked questions about virtual machiens that do not allow administrator access.
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

# Virtual machines that do not allow administrator access

[!include[banner](../includes/banner.md)]

This topic provides answers to frequently asked questions about platform udpate 12 and later Tier 1 virutal machines (VMs) that do not allow administrator access.

## How can I install a deployable package?  
When possible, use LCS to install a package. You can install a deployable package using the -devinstall option. Keep in mind that this option requires a manual DB sync.
See also [Install a deployable package](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/install-deployable-package)  

## Is the AX web site accessible when Visual Studio (VS) is not running?  
Yes, IIS Express is an EXE running as your user, but when you close VS the XPPC agent will start regular IIS (not IIS Express) before it shuts down. This ensures that even when you log off or the machine reboots, the AOS and AX web site are accessible remotely. We recognize many people use these dev boxes as test machines and they expect the AOS to always be running, which can’t be done with IIS Express.  

## What about the other services?  
You can restart Windows® services such as SQL Server, SSRS, SSIS, SSAS, Batch, MR, and IIS (using the World Wide Web Windows® service, not iisreset.exe).  

## Will I be able to clean up the service volume drive?  
Yes, you have full access to the service volume drive, so you can clean up the monitoring data, etc.

## What are the alternatives to the VM that do not allow administrator access?  
An Azure VM on a private Azure subscription and a local VHD still allow administrator access. In this case you still need to run VS as an “administrator.” This is because the administrator only has access to these things through the “administrator” group and not explicitly.  

## Can VS be run as an administrator?  
Starting with PU12 this is no longer required. Connecting via RDP to a VM as an administrator is no longer allowed for VMs under a Microsoft-owned Azure subscription such as the tier 1 VM included in the subscription and tier 1 add-on VMs. However, if you are connecting as an administrator to a VM not under a Microsoft-owned subscription, you must still run VS as an administrator.  

## A "get latest" in VS fails because files are blocked by the AOS. How do we start / stop IIS?  
You have to use IIS Express. See the next question for more information.  

## What are the instruction for using IIS Express?  
IIS Express, when started, shows an icon in the notification area (near the clock) where it shows all the running sites. You can stop if from that menu. A start in IIS Express will be triggered by some actions in VS, but you can also explicitly do it with the menu item in the “Dynamics 365” menu “Restart IIS Express.”  

## How to apply a partner Visual Studio (VS) license which is not tied to the VS log-in account that is likely within the customer AAD / domain?  
This is not supported.  

## Can additional development tools (e.g. Fiddler, Pepper, etc.) be installed?  
This is not supported.  

## Is there a way to run PowerShell & Command Prompt commands as an administrator?  
This is not supported.  

## Is the Trace Parser supported?  
It is currently not supported but we will support it again soon.  

## Is putting the system in maintenance mode supported?  
Putting the system in maintenance mode to change the license configuration is supported, but using the procedure described in the maintenance mode [help topic](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/sysadmin/maintenance-mode) is not supported. Self-service support for maintenance mode in all environments will be added to LCS in the future. Until it is available in LCS, you can use the following steps to put a system in maintenance mode.
1.	RDP onto the dev machine
2.	Login to SQL Server on the dev machine using the credentials from LCS for the axdbadmin user - then switch to the AXDB database and run the following command:
update SQLSYSTEMVARIABLES SET VALUE = 1 where PARM = 'CONFIGURATIONMODE'
3.	Restart the “World Wide Web Publishing Service” service to reset IIS
4.	After it is restarted, it will be in maintenance mode
5.	Reverse the steps when done with maintenance mode activities - set the value to 0 and restart the “World Wide Web Publishing Service” service  

## Is installing a license deployable package supported?  
This should work with the -devinstall option but a problem was found with this scenario and we are working on it.  
