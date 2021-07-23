---
# required metadata

title: Troubleshoot issues during initial setup
description: This topic provides information that can help you fix issues that occur during the initial setup of dual-write integration.
author: RamaKrishnamoorthy 
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# Troubleshoot issues during initial setup

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]



This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Dataverse. Specifically, it provides information that can help you fix issues that might occur during the initial setup of dual-write integration.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## You can't link a Finance and Operations app to Dataverse

**Required role to set up dual-write:** System administrator in Finance and Operations apps and Dataverse.

Errors on the **Setup link to Dataverse** page are usually caused by incomplete setup or permissions issues. Make sure that the whole health check passes on the **Setup link to Dataverse** page, as shown in the following illustration. You can't link dual-write unless the whole health check passes.

![Successful health check.](media/health_check.png)

You must have Azure AD tenant admin credentials to link the Finance and Operations and Dataverse environments. After you link the environments, users can sign in by using their account credentials and update an existing table map.


## Find the limit on the number of legal tables or companies that can be linked for dual-write

You might receive the following error message when you try to enable maps:

*Dual write failure - Plugin registration failed: \[(Unable to get partition map
for project
DWM-1ae35e60-4bc2-4905-88ea-69efd3b29260-7f12cb89-1550-42e2-858e-4761fc1443ea.
Error Exceeds the maximum partitions allowed for mapping
DWM-1ae35e60-4bc2-4905-88ea-69efd3b29260-7f12cb89-1550-42e2-858e-4761fc1443ea)\],
One or more errors occurred.*

The current limit when you link the environments is approximately 40 legal tables. This error occurs if you try to enable maps, and more than 40 legal tables are linked between the environments.

## Error message: Saving connection set failed! An item with the same key has already been added 

While linking the DualWrite environment, it fails with an error msg - Saving connection set failed! An item with the same key has already been added

#### Cause

DualWrite does not support multiple legal entities/companies with the same name. For example, If you have two companies with dat name in the CRM then it will show this error msg.

#### Mitigation

To unblock the customer, search for the companies then delete the redundant ones. Also, look for companies with blank spaces. For some customers, a similar error was shown for multiple companies with a blank name.

## Error when opening the 'Link to Common Data Service' page in Finance and Operations apps

If you are trying to link the Dataverse environment for dual write, and starts to experience issue with error message "Response status code does not indicate success: 404 (Not Found)", then issue is that Consent step is not completed. You can validate if consent has been provided by logging on to portal.azure.com using the tenant admin account, and check if the 3rd party app of ID 33976c19-1db5-4c02-810e-c243db79efde shows up in AAD’s Enterprise applications list. If not, the re-do the consent step as defined in playbook as well in Dual-Write setup section on wiki.

#### Providing App consent

-   Launch URL below with your admin credentials which should prompt you for consent. https://login.microsoftonline.com/common/oauth2/authorize?client_id=33976c19-1db5-4c02-810e-c243db79efde&response_type=code&prompt=admin_consent

-   Click ‘Accept’. This would mean that you are providing the consent to install the app (with id =33976c19-1db5-4c02-810e-c243db79efde) in your tenant.

-   This app is required for CDS to talk to F&O Note: If this doesn't work, open browser in incognito mode for chrome and private mode of Edge.
    
    ![Initial sync setup troubleshooting.](media/Initial-sync-setup-troubleshooting-1.png)



## Linking error with newly created FinOps - Error fetching legal entities

#### Description

[Bad Request], [<!DOCTYPE html> <html> <head> <title>Runtime Error</title> <meta name="viewport" content="width=device-width" /> <style> body {font-family:"Verdana";font-weight:normal;font-size: .7em;color:black;} p {font-family:"Verdana";font-weight:normal;color:black;margin-top: -5px} b {font-family:"Verdana";font-weight:bold;color:black;margin-top: -5px} H1 { font-family:"Verdana";font-weight:normal;font-size:18pt;color:red } H2 { font-family:"Verdana";font-weight:normal;font-size:14pt;color:maroon } pre {font-family:"Consolas","Lucida Console",Monospace;font-size:11pt;margin:0;padding:0.5em;line-height:14pt} .marker {font-weight: bold; color: black;text-decoration: none;} .version {color: gray;} .error {margin-bottom: 10px;} .expandable { text-decoration:underline; font-weight:bold; color:navy; cursor:hand; } @media screen and (max-width: 639px) { pre { width: 440px; overflow: auto; white-space: pre-wrap; word-wrap: break-word; } } @media screen and (max-width: 479px) { pre { width: 280px; } } </style> </head> <body bgcolor="white"> <span><H1>Server Error in '/' Application.<hr width=100% size=1 color=silver></H1> <h2> <i>Runtime Error</i> </h2></span> <font face="Arial, Helvetica, Geneva, SunSans-Regular, sans-serif "> <b> Description: </b>An application error occurred on the server. The current custom error settings for this application prevent the details of the application error from being viewed remotely (for security reasons). It could, however, be viewed by browsers running on the local server machine. <br><br> <b>Details:</b> To enable the details of this specific error message to be viewable on remote machines, please create a &lt;customErrors&gt; tag within a &quot;web.config&quot; configuration file located in the root directory of the current web application. This &lt;customErrors&gt; tag should then have its &quot;mode&quot; attribute set to &quot;Off&quot;.<br><br> <table width=100% bgcolor="#ffffcc"> <tr> <td> <code><pre> &lt;!-- Web.Config Configuration File --&gt; &lt;configuration&gt; &lt;system.web&gt; &lt;customErrors mode=&quot;Off&quot;/&gt; &lt;/system.web&gt; &lt;/configuration&gt;</pre></code> </td> </tr> </table> <br> <b>Notes:</b> The current error page you are seeing can be replaced by a custom error page by modifying the &quot;defaultRedirect&quot; attribute of the application&#39;s &lt;customErrors&gt; configuration tag to point to a custom error page URL.<br><br> <table width=100% bgcolor="#ffffcc"> <tr> <td> <code><pre> &lt;!-- Web.Config Configuration File --&gt; &lt;configuration&gt; &lt;system.web&gt; &lt;customErrors mode=&quot;RemoteOnly&quot; defaultRedirect=&quot;mycustompage.htm&quot;/&gt; &lt;/system.web&gt; &lt;/configuration&gt;</pre></code> </td> </tr> </table> <br> </body> </html> ], The remote server returned an error: (400) Bad Request.

#### Solution 
    
After creating Finance and Operations environment, the FinOps schema generates when you first time open the Data Management page. To solve this problem all you need to do is to open the Data Management page in Finance and Operations.


    
## Finance and Operations apps environment ***.cloudax.dynamics.com is not discoverable.

There are only two things that can cause an issue with environment not being discoverable:
    
a) The user used for login should be in the same tenant as the Finance and Operations instance.
    
b) There are some legacy Finance and Operations instances that were Microsoft-hosted that had an issue with discovery. This gets fixed if the Finance and Operations instance was updated recently as the environment becomes discoverable with any update.




[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
