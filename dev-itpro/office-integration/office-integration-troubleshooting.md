---
# required metadata

title: Office integration troubleshooting
description: This topic provides answers to questions, tips, and troubleshooting information for the Office integration capabilities. The questions and issues discussed range across user, administration, and development scenarios.
author: ChrisGarty
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: OfficeAppParameters
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 72263
ms.assetid: 89588fed-b47f-4f01-9328-325518f016d6
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Office integration troubleshooting

[!include[banner](../includes/banner.md)]


This topic provides answers to questions, tips, and troubleshooting information about the Office integration capabilities. The questions and issues discussed range across user, administration, and development scenarios.

Frequently asked questions
--------------------------

### What platforms are supported for the Office Add-ins?

The Excel Add-in and Word Add-in are built using the Office Web/JavaScript Add-in framework that was initially released for Office 2013, but received significant updates in Office 2016. For more information, see [Office Add-in host and platform availability](http://dev.office.com/add-in-availability). The Excel Add-in requires the ExcelAPI 1.2, so use the [Office Add-in host and platform availability](http://dev.office.com/add-in-availability) matrix to determine which platforms it is supported on. For many users, the phrase "Excel 2016 with the latest updates" is sufficient.

### Are the Office Add-ins safe?

In the age of malware, full connectivity, and compliance risks, nothing is completely secure. However, the web add-ins, like other websites, are essentially a web application that interacts with the Office Client products via a limited API. For more details, read [What can an Office Add-in do?](https://dev.office.com/docs/add-ins/overview/office-add-ins#what-can-an-office-add-in-do)

### Is Office for Mac supported for the Excel Add-in?

No. Mac and iOS support is currently under development. There are authentication differences in how the Office JS APIs function in Safari versus Internet Explorer, particularly in the authentication space. See [Office Add-in host and platform availability](http://dev.office.com/add-in-availability) for details about Office JS API platform support.

### What version of Office is needed to allow the Excel Add-in to support ADFS?

Read more about that in the troubleshooting section below.

### How can Office be forced into updating?

If your Office build does not update then it might be because you are on the deferred track (["Microsoft Office 365 ProPlus" update channel option](https://technet.microsoft.com/en-us/library/mt455210.aspx)), in which case you could [use the "Office Deployment Tool" to move to the Current channel ](https://technet.microsoft.com/en-us/library/jj219422.aspx?f=255&MSPPError=-2147217396)or sign up for the [Office Insider program](https://products.office.com/en-us/office-insider) to ensure that you have the latest updates. The easiest path is to use the Office Deployment Tool to switch to the Current channel, which will cause the latest updates to install immediately.

### Why can't you tell me what version of Office/Excel a particular issue is fixed in?

Office has many different releases, which receive updates at different times and have different version numbers that don't correspond. Some of the more common Office versions and update methods are Click to Run (C2R) Current channel, C2R Deferred, C2R First Update Deferred, Office Insider Fast, Office Insider Slow, and MSI/MSO (install from DVD). The [Office 365 client update channel releases](https://technet.microsoft.com/en-us/office/mt465751?f=255&MSPPError=-2147217396) page has more information about Office versions.

### Why am I having trouble signing into the Excel Add-in?

The Excel Add-in runs inside an Internet Explorer (IE) window. The Excel Add-in will pick up stored credentials from IE by default, and IE will provide the current Windows credentials if there are no stored credentials. Ensure that you are trying to sign in with the correct credentials. In the Excel Add-in, explicitly sign out and then sign in to ensure that the desired credentials are in use.

### The Excel Add-in seems to be slow when publishing records, how can I understand more about what is happening?

There is a certain amount of work that the Excel Add-in is doing. The majority of the work should be on the server.
For more details about where the time is being spent, you can use [Fiddler (a free download)](http://www.telerik.com/fiddler) to help ensure that the Excel Add-in is working as expected. The Excel Add-in sends out the published records as a request. When those records are processed, the response is sent back from the server. The Excel Add-in should then create another message containing the next set of records to publish and send that request. The time lapse between the previous response from the server and the next request to the server should be 5-10 seconds of Excel Add-in processing time.

To check processing time in the Excel Add-in versus the server/service:
- Open [Fiddler](http://www.telerik.com/fiddler). 
- Test the process of publishing a few records.
- Ensure that you can view that request and response in Fiddler ([ensure that HTTPS traffic is being decrypted](http://docs.telerik.com/fiddler/Configure-Fiddler/Tasks/DecryptHTTPS)).
- Publish a larger number of records. 
- In Fiddler, watch the timing from a request to its response and the timing from a response to the next request.
- If the request to response time is large, then the bottleneck is the server/service.
- If the response to next request time is large, then the bottleneck is the Excel Add-in (the client).

## Troubleshooting issues
### \[Fixed\] Issue: During Excel Add-in sign-in, an error appears "AADSTS65001: The user or administrator has not consented to use the application with ID XYZ"

**Issue:** During Excel Add-in sign-in, an error appears "AADSTS65001: The user or administrator has not consented to use the application with ID XYZ". 

**Explanation:** This is usually caused when Microsoft Azure Active Directory (AAD) cannot find the AAD application representing the Excel Add-in because during [Power BI configuration](..\analytics\configure-power-bi-integration.md) an AAD application was added that has the App ID URI set to the environment URL. 

**Fix:** Ensure that there are no AAD App ID URI's set to the environment URI. App ID URI's should be a fabricated, unique URI like `https://contosoAXPowerBI`.

### \[Fixed\] Issue: During Excel Add-in sign-in, an error appears "AADSTS50001: The application named ABC was not found in the tenant named XYZ"

**Issue:** During Excel Add-in sign-in, an error appears "AADSTS50001: The application named ABC was not found in the tenant named XYZ". 

**Explanation:** This is likely a failure in the deployment system that caused the environment to get a URL that was not added in the configured list of service principals for the tenant. 

**Fix:** File a support issue for your environment so that the problem can be investigated and the configuration can be adjusted.

### \[Fixed\] Issue: After the Excel Add-in opens and refreshes data, an error appears, "An error occurred while writing to the data cache"

**Issue:** After the Excel Add-in opens and refreshes data, an error appears, "An error occurred while writing to the data cache." Details of the error state, "The argument is invalid or missing or has an incorrect format." 

**Explanation:** This error will appear if the client is open in Internet Explorer (IE) and after using the **Open in Excel** option, the user clicks **Open** immediately. The way IE handles temporary Internet files causes an issue inside Excel, which causes API calls to fail. 

**Workaround:** For IE, when opening a workbook, click **Save** first, and then click **Open**. The file will open from your Downloads folder. Alternately, Edge and Chrome will both not showcase this problem since they save files to a Downloads folder automatically. 

**Long term fix:** We are working with the Office team to understand this issue so that it can be fixed in Excel.

### Issue: The server response was: 5.7.60 SMTP; Client does not have permissions to send as this sender

**Issue:** When sending email using SMTP, you may see the error: The server response was: "5.7.60 SMTP; Client does not have permissions to send as this sender" or "Something went wrong while generating the report."

**Explanation:** This is usually caused by incorrect setup of the Send As permissions setup for the email account. 

**Fix:** Send As permissions can be configured on the Office 365 admin center (portal.office.com/Admin) > **Users** > **Active users** > **User** > **Edit mailbox permissions** > **Send email from this mailbox** [Office 365 Help on Send email from another user’s mailbox](https://support.office.com/en-us/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E)). 

The following SMTP setup example shows the **Email parameters** page, where you need to provide the outgoing mail server, port, user name, password, and SSL requirements. 

[![smtp](./media/smtp.png)](./media/smtp.png)   

The permissions SMTP User account is `serviceacct@d365forops.onmicrosoft.com`. 

**Important:** All users, like the example Test User below, will need to allow the SMTP account to have **Send As** permissions on their email setup in Office 365. This is done in the Mailbox permissions in Exchange or in the Office 365 Admin portal. The following screenshot shows the setup for the test user account with the STMP service account added in the **Send As** section. 

[![o365](./media/o365.png)](./media/o365.png)  

### \[Fixed\] Issue: The Office Add-ins don't yet support ADFS

**Affected versions:** CTP8 and the February 2016 releases 

**Issue:** When users from a Microsoft Azure Active Directory (Azure AD) tenant that uses Active Directory Federation Services (AD FS) try to sign in to Office Add-ins (that is, when the users enter their account, and then press tab or click to enter their password), a separate browser window opens. This browser window usually has a URL that starts with `https://az689774.vo.msecnd.net/dynamicsofficeapp/v1.2.1.0/App/DynamicsApp.html\#id\_token=`. The user is not able to sign in. 

**Explanation:** The issue that the Microsoft Office add-ins (both Microsoft Excel and Microsoft Word) have with ADFS is that a redirect to the ADFS site for the tenant occurs during sign-in. However, that site is an unknown (and therefore disallowed) application domain (AppDomain). 

**Long-term fix:** The long-term fix for this issue was put in place May 10, 2016. The long-term fix was for the Office Add-ins to use a new dialog API that the Office team added. 

**To take advantage of the Add-in updates that support ADFS:** All Office installations should be updated via **File** > **Account** > **Updates** (for click to run installations) or via Windows Update (for MSI installations). The ADFS Dialog API was in the May Update [16.0.6868.2060](http://answers.microsoft.com/en-us/office/forum/office_2016-office_install/may-update-16068682060-for-office-2016-on-windows/ea082237-7ec3-4b06-895b-83490980e6d2?auth=1). The [Office 365 client update channel releases](https://technet.microsoft.com/en-us/office/mt465751?f=255&MSPPError=-2147217396) page provides information about updates. 

If your Office build does not update then it might be because you are on the deferred track (["Microsoft Office 365 ProPlus" update channel option](https://technet.microsoft.com/en-us/library/mt455210.aspx)), in which case you could [use the "Office Deployment Tool" to move to the Current channel ](https://technet.microsoft.com/en-us/library/jj219422.aspx?f=255&MSPPError=-2147217396)or sign up for the [Office Insider program](https://products.office.com/en-us/office-insider) to ensure you have the latest updates. Also refer to [Install the latest version of Office 2016](https://dev.office.com/docs/add-ins/develop/install-latest-office-version) and [Office 2016 Deployment Guides for Admins](https://technet.microsoft.com/en-us/library/cc303401(v=office.16).aspx). 

If Office updates cannot be installed, then the following workaround that can unblock users.

#### Workaround: Use Internet Explorer to sign in to the client before you use the Office Add-ins

This workaround requires user knowledge and extra steps. After users have been educated about this workaround, it should be straightforward for them. 

**User steps:** Before users open Excel (or Word), they should first sign in to the client by using Internet Explorer. 

**Explanation:** The sign-in context will be used by the Excel (or Word) Add-in, and no redirect will be required. The earlier sign-in must occur in Internet Explorer because the Office Add-ins run inside an Internet Explorer window in Excel and Word. The sign-in context lasts 6 to 24 hours, depending on policies. Therefore, a new sign-in through Internet Explorer is required only occasionally.

1.  Close Internet Explorer and Excel.
2.  Open Internet Explorer and sign in to the client.
3.  Test the Excel add-in using an Open in Excel experience. (For example, click **Fleet Management** &gt; **Customers** &gt; **Customer** &gt; **Open in Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers**.)

### \[Fixed\] Issue: The Excel Add-in doesn't run or facilitate sign-in correctly

**Issue:** When users try to sign into the Excel Add-in, a blank authentication dialog is shown or an error is shown in place of the authentication page. The user is not able to sign in. 

**Explanation:** The Excel Add-in relies on the Office Web JS Add-in platform and uses Azure Active Directory for authentication. If a proxy is being used, then there are a number of URLs that need to be accessible to facilitate running and signing into the Excel Add-in. In addition, if ADFS is being used, that ADFS URL must be HTTPS. 

**Solution:** This is a customer-specific network issue, so it requires a customer-specific resolution. If ADFS is being used, then ensure the ADFS URL is using HTTPS. Also, ensure all the following URLs are accessible from the user's machine:
URLs accessed for Excel Add-in loading and authentication
- Load Excel Add-in 
  - Excel Add-in CDN
    - http://az689774.vo.msecnd.net:443
    - https://az689774.vo.msecnd.net
  - Excel Web JS Add-in platform
    - http://appsforoffice.microsoft.com:443
    - https://appsforoffice.microsoft.com
    - http://secure.aadcdn.microsoftonline-p.com:443
    - https://secure.aadcdn.microsoftonline-p.com
    - http://az416426.vo.msecnd.net:443
    - https://az416426.vo.msecnd.net
    - http://telemetryservice.firstpartyapps.oaspapps.com:443
    - https://telemetryservice.firstpartyapps.oaspapps.com
    - http://nexus.officeapps.live.com:443
    - https://nexus.officeapps.live.com
    - http://browser.pipe.aria.microsoft.com:443
    - https://browser.pipe.aria.microsoft.com
    - http://schemas.microsoft.com
- Authentication in Excel Add-in
  - http://login.windows.net:443
  - https://login.windows.net
  - http://login.microsoftonline.com:443
  - https://login.microsoftonline.com


See also
--------

[Office integration](office-integration.md)

[Office integration tutorial](office-integration-tutorial.md)

[Configuring Power BI integration](..\analytics\configure-power-bi-integration.md)



