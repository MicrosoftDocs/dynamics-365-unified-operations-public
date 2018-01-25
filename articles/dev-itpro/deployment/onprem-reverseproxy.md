---
# required metadata

title: Configure reverse proxy for your Dynamics 365 for Finance and Operations on-premises environment
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: sarvanisathish
manager: AnnBe
ms.date: 01/25/2018
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

# Configure reverse proxy for your Dynamics 365 for Finance and Operations on-premises environment

[!include[banner](../includes/banner.md)]

Customers may want to secure the Dynamics 365 for Finance and Operations on-premises environment behind a reverse proxy. Reverse proxy is a server that hides the actual servers serving traffic from the clients. The proxy server accepts requests from the clients on behalf of the F&O environment and forwards the traffic to it. The clients are not aware of the actual servers that compose the F&O environment. This adds a measure of security and enable load balancing. 

## Steps to configure the reverse proxy

Perform the below steps in **each** node of type OrchestratorType in the Service Fabric cluster
1. Remote into the Orchestrator VM
2. Execute the below powershell script to retrive the path of the ```machine.config``` file

	```Powershell
	[System.Runtime.InteropServices.RuntimeEnvironment]::SystemConfigurationFile
	```

3. Edit the ```machine.config``` file to add the below xml snippet

	```XML
		<system.net>
			<defaultProxy enabled="true" >
				<proxy <<<SET YOUR PROXY SETTINGS>> />
	   	 	</defaultProxy>
    	</system.net>
	```

4. Save the file.
5. Restart the machine.
