---
# required metadata

title: Device activation of a customized Retail Modern POS
description: This topic explains how you can use self-service to do silent servicing updates and initial deployments. It also explains some aspects of special deployment. 
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

This topic explains how you can use self-service to do silent servicing updates and initial deployments. It also explains some aspects of special deployment. This topic will be updated as the feature is developed and more functionality becomes available. Currently, only the capability for silent servicing updates is available.

## Delimiters for mass deployment

The following table shows the delimiters that can currently be used in execution commands for mass deployment. These delimiters apply to the July 2017 version with Application update 3 or later.

| Delimiter                 | Description |
|---------------------------|-------------|
| -S or -Silent             | Silently run the installer. No graphical user interface (GUI) is used. The **-Q** and **-Quiet** delimiters have the same effect and can also be used. |
| -C or -Config             | Specify the location and file name of the configuration file to use as part of this installation. |
| -FilePath                 | Specify a custom installation location.<p><p>We don't recommend that you use this delimiter for a standard installation.</p> |
| -LogFile                  | Specify a custom file location for the installation logs.<p><p>We don't recommend that you use this delimiter for a standard installation.</p> |
| -SkipPrerequisiteCheck    | Skip the check for prerequisites and prerequisite installation.<p><p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipSystemInfoCollection | Skip the process of collecting system information at the beginning of the installation.<p><p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |
| -SkipMerchantInfo         | Skip the installation of merchant account information at the end of the self-service installer for Hardware station.<p><p>You should use this delimiter only for development and testing. We don't recommend that you use it for a standard installation.</p> |

## Silent servicing

### Before you begin

#### NEWNEWNENENWNWENEW
    > [!NOTE]
    > - This security and functionality enhancement was introduced in the July 2017 (7.2) release and newer and has since been ported to the previous 1611 (7.1) release.

The Retail Modern POS application is a client side component for Microsoft Dynamics 365 for Finance and Operations and Microsoft Dynamics 365 for Retail.  To utilize Retail Modern POS, it is mandatory to perform device activation.  Device activation leverages Azure Active Directory (AAD) to authenticate the user.  Enhanced functionality in this area has modified the device activation flow to better leverage the Windows Web Account Manager.  As a function of this enhancement, there is now enhanced security around the authentication approval process that requires additional configuration in headquarters when Retail Modern POS has been customized.  Specifically, the Callback (Also known as the Reply) URI now requires a very specific and unique value.  By default, the Retail Modern POS application is already registered for this Callback URI.  When customized, this URI is altered and must be configured correctly to function again.  This document will detail out the steps required to perform this configuration.  When this configuration is not followed, an error message occurs when device activation is attempted in the customized Retail Modern POS application.  The error will be similar to the following:
AADSTS50011: The reply address 'ms-appx-web://Microsoft.AAD.BrokerPlugin/...' does not match the reply addresses configured for the application

If you will try to use the customized APPS package with the First Party AAD application (means without making any below mentioned changes in AAD) you will see error similar to this one while authenticating against AAD:

AADSTS50011: The reply address 'ms-appx-web://Microsoft.AAD.BrokerPlugin/...' does not match the reply addresses configured for the application

 

Note that it complains about the reply address used for the AppId which corresponds to the MPOS First Party Application.

The list below enumerates steps needed to create 2 AAD applications: one for MPOS and one for Retail Server. Retail Server one is needed because MPOS must specify a Web Application which contains resources needed for MPOS to work, both of those applications are used by MPOS while acquiring a security token from AAD, in other words MPOS will say to AAD something like this: "I am client application MPOS who needs to access resources protected by a server application Retail Server".

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
