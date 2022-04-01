---
title: General troubleshooting
description: This topic provides general troubleshooting information for dual-write integration between Finance and Operations apps and Dataverse.
author: RamaKrishnamoorthy 
ms.date: 03/16/2020
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-03-16
---

# General troubleshooting

[!include [banner](../../includes/banner.md)]



This topic provides general troubleshooting information for dual-write integration between Finance and Operations apps and Dataverse.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## <a id="enable-view-trace"></a>Enable and view the plug-in trace log in Dataverse to view error details

Trace logs can be useful when troubleshooting dual write live sync issues between Finance & Operations and Dataverse. 
They can provide specific details to the teams who provide technical and engineering support for Dynamics 365. 
This article will cover how to enable trace logs, and how to view them. Trace logs are managed in the Dynamics 365 Settings 
page and require administrator level privileges to change and view. 

**Required role to turn on the trace log and view errors:** System admin

### To turn on the trace log, follow these steps.

1.	Log on to Dynamics 365 select Settings in the top navigation bar. On the Systems page, click Administration.
2.	On the Administration page, click System Settings
3.	Select the Customization tab and plug-in and in the custom work flow activity tracing section, change the dropdown to All. 
This will trace all activities and provides a comprehensive set of data for the teams who must review potential issues.

[!NOTE] Setting the dropdown to Exception will only provide trace information when exceptions (errors) occur

Once enabled, the plug-in trace logs will continue to be collected until they are manually turned off by returning to this location and selecting Off.

### To view the trace log, follow these steps.

1. On the Dynamics 365 Settings page, select Settings in the top navigation bar 
2. Select Plugin Trace Log in the Customizations section of the page
3. You can find entries in the list of trace logs, based on Type Name and/or Message Name
4. Open the desired entry to view the full log. The Message Block in the Execution section will provide available information for the plug-in. 
If available, exception details will also be provided. 

You can copy the contents of the trace logs and paste them into another application like Notepad or other tools to view logs or text files 
to more easily see all the content. 



## Enable debug mode to troubleshoot live synchronization issues in Finance and Operations apps

**Required role to view the errors:** System admin

Dual-write errors that originate in Dataverse can appear in the Finance and Operations app. To enable verbose logging for the errors, following these steps:

1. For all project configurations in Finance and Operations app there is a flag **IsDebugMode** on the **DualWriteProjectConfiguration** table.
2. Open the **DualWriteProjectConfiguration** using the Excel addin. To use the addin, enable design mode in the Finance and Operations Excel addin and add the **DualWriteProjectConfiguration** to the sheet. For more information, see [View and update entity data with Excel](../../office-integration/use-excel-add-in.md).
3. Set **IsDebugMode** to **Yes** on the project.
4. Run the scenario that is generating errors.
5. The verbose logs are stored in the **DualWriteErrorLog** table.
6. To lookup data on table browser use the following link: `https://999aos.cloudax.dynamics.com/?mi=SysTableBrowser&tableName=DualWriteErrorLog`, replacing `999` as needed.
7. Update again after [KB 4595434](https://fix.lcs.dynamics.com/Issue/Details?kb=4595434&bugId=527820&dbType=3&qc=98e5dc124ac125c57ad633d885ac612aea3ddb8f4abf9d71ab3aa354f2e06cbe), which is available for platform updates 37 and later. If you have this fix installed then the debug mode will capture more logs.  

## Check synchronization errors on the virtual machine for the Finance and Operations app

**Required role to view the errors:** System administrator

1. Sign in to Microsoft Dynamics Lifecycle Services (LCS).
2. Open the LCS project that you chose to do the dual-write testing for.
3. Select the **Cloud-hosted environments** tile.
4. Use Remote Desktop to sign in to the virtual machine (VM) for the Finance and Operations app. Use the local account that is shown in LCS.
5. Open Event viewer.
6. Select **Applications and Services Logs \> Microsoft \> Dynamics \> AX-DualWriteSync \> Operational**.
7. Review the list of recent errors.

## Dual write UI landing page showing blank
When opening the Dual-write page in Edge/Chrome, the home page doesn't load, and the user sees a blank page or an error such as "Something went wrong".
In Devtools, you will see an error in the console logs:

>bundle.eed39124e62c58ef34d2.js:37 DOMException: Failed to read the 'sessionStorage' property from 'Window': 
>Access is denied for this document. at t.storeInSessionStorage 
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:16:136860 ) at new t
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:69:20103 ) at ci
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:44115 ) at Eo
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:58728 ) at jo
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:65191 ) at Nr
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:84692 ) at Or
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:85076 ) at Ss
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:91750 ) at vs
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:91130 ) at hs
>(https://dataintegrator.trafficmanager.net/bundle.eed39124e62c58ef34d2.js:37:90151 )

The UI uses browser 'session storage' to store some property values for loading the home page. For this to work, 
third-party cookies need to be allowed in the browser for the site. The error is indicative of the UI not 
being able to access the session storage. There can be two scenarios in which this issue is encountered:

1.	The user is opening the UI in incognito mode of Edge/Chrome and third-party cookies in incognito are blocked.
2.	The user has blocked third-party cookies altogether in Edge/Chrome .

### Mitigation
Third-party cookies need to be allowed by the user in browser settings.

### Chrome
1st Option:
1.	Go to settings - chrome://settings/ -> Privacy and Security -> Cookies and other site data.
2.	Select 'Allow all cookies'. (If the user does not wish to do this, go for the second option)

2nd Option:
1.	Go to Chrome settings - chrome://settings/ -> Privacy and Security -> Cookies and other site data.
2.	If 'Block third-party cookies in Incognito' or 'Block third-party cookies' is selected, go to 'Sites that can always use cookies’ and click Add. 
3.	Add your Finance and Operations apps site name - https://<your_FinOp_instance>.cloudax.dynamics.com. Make sure you select the checkbox 
4.	for "All cookies, on this site only". 

### Edge
1.	Go to settings -> Site permissions -> Cookies and site data.
2.	Turn off 'Block third-party cookies'.  


## Unlink and link another Dataverse environment from a Finance and Operations app

**Required role to unlink the environment:** System administrator for either Finance and Operations app or Dataverse.

1. Sign in to the Finance and Operations app.
2. Go to **Workspaces \> Data management**, and select the **Dual Write** tile.
3. Select all running mappings, and then select **Stop**.
4. Select **Unlink environment**.
5. Select **Yes** to confirm the operation.

You can now link a new environment.

## Unable to view the sales order line Information form 

When you create a sales order in Dynamics 365 Sales, clicking on **+ Add products** might redirect you to the Dynamics 365 Project Operations order line form. There is no way from that form to view the sales order line **Information** form. The option for **Information** does not appear in the dropdown below **New Order Line**. This happens because Project Operations has been installed in your environment.

To re-enable the **Information** form option, follow these steps:

1. Navigate to the **Order Line** table.
2. Find the **Information** form under the forms node.
3. Select the **Information** form and click **Enable security roles**.
4. Change the security setting to **Display to everyone**.

## How to enable and save network trace so that traces can be attached to support tickets

The support team might need to review network traces to troubleshoot some issues. To create a network track, follow these steps:

### Chrome

1. In the opened tab, press **F12** or choose **Developer tools** to open the developer tools.
2. Open the **Network** tab and type **integ** in the filter text box.
3. Run your scenario and observe the requests being logged.
4. Right-click on the entries and select **Save all as a HAR with content**.

### Microsoft Edge

1. In the opened tab, press **F12** or choose **Developer tools** to open the developer tools.
2. Open the **Network** tab.
3. Run your scenario.
4. Select **save** to export the results as HAR.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
