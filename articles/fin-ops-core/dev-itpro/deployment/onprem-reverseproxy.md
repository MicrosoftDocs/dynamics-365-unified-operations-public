---
# required metadata

title: Configure proxies for on-premises environments
description: This topic describes how you can secure the on-premises environment behind a proxy.
author: faix
ms.date: 04/05/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8 
---

# Configure proxies for on-premises environments

[!include [banner](../includes/banner.md)]

You may want to secure the Dynamics 365 Finance + Operations (on-premises) environment behind a proxy. Proxy is a server that hides the actual servers that are serving traffic from the clients. The proxy server accepts requests from the clients on behalf of the environment and forwards the traffic to it. The clients are not aware of the actual servers that compose the environment. This adds another measure of security and enables load balancing. 

## Configure the proxy

Perform the following steps in **each** node of type **OrchestratorType** in the Microsoft Azure Service Fabric cluster.

1. Use remote access to connect to the Orchestrator virtual machine (VM).
2. Execute the following PowerShell script to retrieve the path of the ```machine.config``` file.

	```powershell
	[System.Runtime.InteropServices.RuntimeEnvironment]::SystemConfigurationFile
	```

3. Edit the ```machine.config``` file to add the following code example.

	```xml
	<system.net>
		<defaultProxy>
            <proxy usesystemdefault="true" proxyaddress="http://<PROXYADDRESS>:<PROXYPORT>" bypassonlocal="true" />
        </defaultProxy>
    </system.net>
	```

4. Save the file.
5. Restart the virtual machine.

The above procedure must be performed for all Orchestrator node VMs.

## Safe list URLs

The LocalAgent needs to communicate with Azure resources. As a result, the following URLs should be added to a safe list on the proxy or firewalls so that all **OrchestratorType** nodes can access them:

```Text
- lcsapi.lcs.dynamics.com
- login.windows.net
- uswelcs1lcm.queue.core.windows.net
- www.office.com
- login.microsoftonline.com
- dc.services.visualstudio.com
- uswelcs1lcm.blob.core.windows.net
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
