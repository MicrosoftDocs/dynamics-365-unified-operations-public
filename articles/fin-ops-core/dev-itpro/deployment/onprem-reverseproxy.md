---
# required metadata

title: Configure proxies for on-premises environments
description: This article describes how you can secure the on-premises environment behind a proxy.
author: faix
ms.date: 04/05/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
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
search.app:
  - financeandoperationsonprem-docs 
---

# Configure proxies for on-premises environments

[!include [banner](../includes/banner.md)]

Some organizations require that all server traffic goes through a proxy server for tracking or packet inspection. This section describes how we recommend configuring your environment in these cases.

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

The LocalAgent needs to communicate with Azure resources and Microsoft Dynamics Lifecyle Services (LCS). As a result, some URLs need to be added to a safe list on the proxy or firewalls so that all **OrchestratorType** nodes can access them. The urls will vary depending which LCS region your environment is being deployed from.

### LCS Global

```Text
- lcsapi.lcs.dynamics.com
- login.windows.net
- uswelcs1lcm.queue.core.windows.net
- www.office.com
- login.microsoftonline.com
- dc.services.visualstudio.com
- uswelcs1lcm.blob.core.windows.net
```

### LCS EU

```Text
- lcsapi.eu.lcs.dynamics.com
- login.windows.net
- euweprodlcm.queue.core.windows.net
- www.office.com
- login.microsoftonline.com
- dc.services.visualstudio.com
- euweprodlcm.blob.core.windows.net
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
