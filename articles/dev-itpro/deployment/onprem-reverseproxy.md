---
# required metadata

title: Configure proxies for on-premises environments
description: This topic describes how you can secure the Dynamics 365 for Finance and Operations on-premises environment behind a proxy.
author: sarvanisathish
manager: AnnBe
ms.date: 04/30/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: sarvanis
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8 
---

# Configure proxies for on-premises environments

[!include [banner](../includes/banner.md)]

You may want to secure the Dynamics 365 for Finance and Operations on-premises environment behind a proxy. Proxy is a server that hides the actual servers serving traffic from the clients. The proxy server accepts requests from the clients on behalf of the Finance and Operations environment and forwards the traffic to it. The clients are not aware of the actual servers that compose the Finance and Operations environment. This adds another measure of security and enables load balancing. 

## Configure the proxy

Perform the following steps in **each** node of type **OrchestratorType** in the Microsoft Azure Service Fabric cluster.

1. Use remote access to connect to the Orchestrator virtual machine (VM).
2. Execute the following PowerShell script to retrieve the path of the ```machine.config``` file.

	```Powershell
	[System.Runtime.InteropServices.RuntimeEnvironment]::SystemConfigurationFile
	```

3. Edit the ```machine.config``` file to add the following code example.

	```XML
		<system.net>
			<defaultProxy enabled="true" >
				<proxy <<<SET YOUR PROXY SETTINGS>> />
	   	 	</defaultProxy>
    	</system.net>
	```

4. Save the file.
5. Restart the virtual machine.

The above procedure must be performed for all Orchestrator node VMs. 
