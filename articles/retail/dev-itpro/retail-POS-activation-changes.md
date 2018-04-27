---
# required metadata

title: Device activation of a customized Retail Modern POS
description: This topic explains how to configure headquarters to allow device activation to function properly when a customized Retail Modern POS application is used. 
author: jashanno
manager: AnnBe
ms.date: 04/25/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jashanno
ms.search.validFrom: 2017-09-31
ms.dyn365.ops.version: Application update 3
---

# Device activation of a customized Retail Modern POS

[!INCLUDE [banner](../includes/banner.md)]

This topic explains how to configure headquarters to allow device activation to function properly when a customized Retail Modern POS application is used. It details the steps necessary to pull the customized reply address and enter this value into headquarters.

    > [!NOTE]
    > - This security and functionality enhancement was introduced in the July 2017 (7.2) release and newer and has since been ported to the previous 1611 (7.1) release.

The Retail Modern POS application is a client side component for Microsoft Dynamics 365 for Finance and Operations and Microsoft Dynamics 365 for Retail.  To utilize Retail Modern POS, it is mandatory to perform device activation.  Device activation leverages Azure Active Directory (AAD) to authenticate the user.  Enhanced functionality in this area has modified the device activation flow to better leverage the Windows Web Account Manager.  As a function of this enhancement, there is now enhanced security around the authentication approval process that requires additional configuration in headquarters when Retail Modern POS has been customized.  Specifically, the Callback (Also known as the Reply) URI now requires a very specific and unique value.  By default, the Retail Modern POS application is already registered for this Callback URI.  When customized, this URI is altered and must be configured correctly to function again.  This document will detail out the steps required to perform this configuration.  When this configuration is not followed, an error message occurs when device activation is attempted in the customized Retail Modern POS application.  The error will be similar to the following:
```
AADSTS50011: The reply address 'ms-appx-web://Microsoft.AAD.BrokerPlugin/[...]' does not match the reply addresses configured for the application
```

    > [!NOTE]
    > - It is recommended to attempt to use the customized Retail Modern POS application without configuring headquarters once to see what the error looks like and to more easily pull the custom reply address.
    > - Take note that the error showcases the reply address used for the Application ID, which corresponds to the Retail Modern POS application.

## Setup
The steps that follow are required to allow device activation to function correctly when the customized Retail Modern POS application is used.  There will be two Azure Active Directory (AAD) applications generated, one for Retail Modern POS and one for Retail Server.  The Retail Server AAD application is required because Retail Modern POS utilizes resources through Retail Server, so both AAD applications are utilized through Retail Modern POS usage.  Retail Server, in this scenario, functions as the endpoint for protected resources that get requested by the Retail Modern POS application.

1. Navigate to https://portal.azure.com/
2. Go to Azure Active Directory->App registrations
3. Create AAD Retail Server application by clicking New application registration and provide the following values for the 3 fields:
  a) "Name" - Customized Retail Server (you can put here any name you want)
  b) "Application type" - Web app / API
  c) "Sign-on URL" - specify here any uri which doesn't have to point to any real physical location, for instance: https://YourCustomizedRetailServer
4. Press [TAB] button and then Click Create button and wait until the operation completes successfully, if it fails address the errors and try again.

5. Find the application by using its name - Customized Retail Server and then click it.

6. While at the application's settings page go to Properties, copy the value from the field App ID URI and paste it into the attribute value corresponding to the key AADRetailServerResourceId in the file DLLHost.exe.config
7. Create AAD MPOS application by repeating steps 3-4, provide the following values:
  a) Name - specify Customized MPOS (again, you can put here any name you want)
  b) Application type - specify Native
  c) Redirect URI - specify the reply address corresponding to the error seen at the above screenshot, the reply address starts with ms-appx-web://Microsoft.AAD.BrokerPlugin/

That callback can also be seen in the Event Viewer (Microsoft-Dynamics-Commerce-ModernPos/Operational) in one of the first events once MPOS is started. The event's ID is 40619, it is logged with the text which starts with:
```
This UWP application was assigned the following callback Uri to be used while interacting with AAD: ms-appx-web://Microsoft.AAD.BrokerPlugIn/S-1-15-2-[...]
```
The new URI for the customized application is the value partially showcased above when device activation is attempted (and can also be seen in Event Viewer after device activation is attempted).  It will be in the form 



Note that once you created the AAD Application you can specify as many callback URLs as you want which means that, if, by any reason, while developing or for Production, you have multiple packages with different Callback Urls, you then could just keep this one single AAD Application and maintain all your CallbackUrls in this single application.

8. Press [TAB] button and then Click Create button and wait until the operation completes successfully, if it fails address the errors and try again.
9. Find the application by using its name - Customized MPOS and then click it.
10. Copy the Application ID and paste it into the attribute value corresponding to the key AADClientId in the file DLLHost.exe.config
11. While in AAD Portal's page displaying the MPOS details click "Required permission" at "Settings" pane and then "Add"->Select an API
Type Customized Retail Server in the search box and then click the same name in the search results' list and then "Select" button
 
Check the line "Access Customized Retail Server" and then click the Select button
 
12. click "Done" button and then "Grant Permissions" -> "Yes".

This completes setup on MPOS side, next set of steps is to whitelist newly created AAD applications on AX side so AAD issued security token would be accepted.

13. In AX go to Retail Shared Parameters->Identity Providers

14. In the grid "Identity Providers" select a row corresponding to your Azure Active Directory tenant, once you select it the 2 below grids will be refreshed with the applications setup for that tenant

15. In the grid "Relying Parties" click "Add" and add new row with the following parameters:

  a) ClientID - specify the one you used in the step #10 above

  b) Type - Public

  c) UserType - Worker

  d) Name - type anything you want there

16. Click button "Save"

17. Keep newly added into Relying Party grid record selected and click "Add" in the Server Resource IDs, specify:

  a) Server Resource ID - specify the value you used in step #6 above.

  b) Name - anything

18. Click Save button. Make sure all your newly created records are stored as expected - to check that you can navigate between different rows in those grids.

19. Execute the job 1110 and wait until it is completed

20. At this time the data will be synced to the channel DB but CRT/RS employs a cache which is few minutes, if you don't want to wait until the cache expires and your are not dealing with PROD environment you can consider recycling app pool of the Retail Server.

21. Close MPOS and kill, by using a Task Manager for instance, all instances of the process DllHost.exe

Now try to activate device in MPOS again, if you will still experience issues look into Windows Event Viewer logs corresponding to MPOS and Retail Server for warnings/errors which would be helpful in the investigation.
#### NEWNEWNENENWNWENEW
To use this functionality, you must be using the July 2017 version with Application update 3 or later. Note that silent servicing maintains all components that are currently installed. If any configuration is still required, complete it before you begin to follow the instructions in this topic.

### Examples of commands for silent servicing
