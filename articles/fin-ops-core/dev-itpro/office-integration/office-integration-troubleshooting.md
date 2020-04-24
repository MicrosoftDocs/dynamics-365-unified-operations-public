---
# required metadata

title: Troubleshoot the Office integration
description: This topic provides answers to questions, tips, and troubleshooting information for the Microsoft Office integration capabilities. The questions and issues that are discussed range across user, administration, and development scenarios.
author: ChrisGarty
manager: AnnBe
ms.date: 04/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: OfficeAppParameters, SysEmailParameters
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 72263
ms.assetid: 89588fed-b47f-4f01-9328-325518f016d6
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Troubleshoot the Office integration

[!include [banner](../includes/banner.md)]


This topic provides answers to questions, tips, and troubleshooting information about the capabilities of the Microsoft Office integration. The questions and issues that are discussed range across user, administration, and development scenarios.

## Frequently asked questions

### What platforms do the Office Add-ins support?

The Microsoft Excel Add-in and Microsoft Word Add-in are built by using the Office Web/JavaScript Add-in framework. This framework was originally released for Microsoft Office 2013 but received significant updates in Microsoft Office 2016. For more information, see [Office Add-in host and platform availability](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-in-availability). The Excel Add-in requires ExcelAPI 1.2. Therefore, use the [Office Add-in host and platform availability](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-in-availability) matrix to determine which platforms support the Excel Add-in. For many users, the phrase "Excel 2016 with the latest updates" is sufficient.

### Are the Office Add-ins safe?

In an age of malware, full connectivity, and compliance risks, nothing is completely secure. However, the web add-ins, like other websites, are basically a web application that interacts with the Office client products via a limited application programming interface (API). For more details, see [Office Add-ins platform overview](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

### Does the Excel Add-in support Office for Mac?

No. Support for Apple Mac and iOS is currently under development. The Office JavaScript (JS) APIs work differently in Apple Safari and Internet Explorer, especially in respect to authentication. For details about platform support for the Office JS APIs, see [Office Add-in host and platform availability](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-in-availability).

### What version of Office is required for the Excel Add-in to support AD FS?

For more information, see the "Troubleshooting issue" section later in this topic.

### How can I force an update of Office?

If your Office build isn't updated, you might be on the deferred track ([Overview of update channels for Microsoft 365 Apps](https://technet.microsoft.com/library/mt455210.aspx)). In this case, you can [use the Office Deployment Tool to move to the Current channel](https://technet.microsoft.com/library/jj219422.aspx?f=255&MSPPError=-2147217396) or sign up for the [Office Insider program](https://products.office.com/office-insider) to help guarantee that you have the latest updates. The easiest method is to use the Office Deployment Tool to switch to the Current channel. In this case, the latest updates will be installed immediately.

### Why can't you tell me what version of Office or Excel a particular issue is fixed in?

Office has many releases. These releases receive updates at different times and have different version numbers that don't correspond. Some frequently used Office versions and update methods are Click to Run (C2R) Current channel, C2R Deferred, C2R First Update Deferred, Office Insider Fast, Office Insider Slow, and MSI/MSO (install from DVD). For more information about Office versions, see the [Release information for updates to Microsoft 365 Apps](https://technet.microsoft.com/office/mt465751?f=255&MSPPError=-2147217396) page.

### Why am I having trouble signing into the Excel Add-in?

The Excel Add-in runs inside an Internet Explorer window. By default, the Excel Add-in picks up stored credentials from Internet Explorer, and Internet Explorer provides the current Microsoft Windows credentials if there are no stored credentials. Make sure that you're using the correct credentials to sign in. In the Excel Add-in, explicitly sign out, and then sign in to help guarantee that the correct credentials are used.

### The Excel Add-in seems to be slow when it publishes records. How can I learn more about what is occurring?

Most of the work that the Excel Add-in does should occur on the server. To learn where the time is being spent, you can use [Fiddler (a free download)](https://www.telerik.com/fiddler) to make sure that the Excel Add-in works as you expect.

The Excel Add-in sends the published records as a request. When those records are processed, the response is sent back from the server. The Excel Add-in then creates another message that contains the next set of records to publish, and sends that request. Five to ten seconds of processing time in the Excel Add-in should be required between the previous response from the server and the next request to the server.

To check processing time in the Excel Add-in versus the server/service, follow these steps.

1. Start [Fiddler](https://www.telerik.com/fiddler). 
2. Publish a few records to test the process.
3. Make sure that you can view that request and response in Fiddler ([make sure that HTTPS traffic is being decrypted](https://docs.telerik.com/fiddler/Configure-Fiddler/Tasks/DecryptHTTPS)).
4. Publish a larger number of records. 
5. In Fiddler, watch the time that is required from a request to its response, and from a response to the next request.

    - If the time from a request to its response is large, the bottleneck is the server/service.
    - If the time from a response to the next request is large, the bottleneck is the Excel Add-in (that is, the client).

### Why is the Export to Excel functionality limited to 10,000 records (prior to Platform update 22)?

Prior to Platform update 22, the Export to Excel functionality is limited to 10,000 records. This limitation is in place because the export process uses the form from which data is being exported to provide the following records with fields and data that can't be obtained otherwise: formatted values, calculated values, and temporary table data. Because the form is used during the export, it occurs inside the client process that is shared by all the users on a given computer. During the export, those other users are blocked from interacting with the client.

With Platform update 22 and later, Export to Excel has a progress dialog box and is no longer a blocking process for other users, so larger datasets can be exported. Exporting data via Export to Excel will be slower than using the Excel Add-in or the Data Management framework, but it will return exactly the data shown in the grid. This is useful for filtered datasets. The user is presented with a dialog box that allows them to stop at any point. Because the export can take some time, it is recommended that the export is done with the Chrome or Edge browsers, with the automatic download option enabled. The automatic download option will ensure that the browser downloads the file as soon as the export is complete to ensure that the download link is used within the 15-minute time limit.

The ideal alternative to Export to Excel is to use Open in Excel and the Excel Add-in. The Excel Add-in retrieves data by using the OData service, and takes advantage of the security that the entities provide. The import and export capabilities in the Data management framework (DMF) and Data import/export framework (DIXF) can also be used. However, DMF/DIXF is often limited to administrators.

If you have concerns about giving users access to the data via the Excel Add-in, because they should not be able to update records, consider the following points:

- The entities should have all the validation and logic that the forms have. If they don't, it's a bug. 
- The way that entities are secured resembles the way that forms are secured. Therefore, if a user should not have permission to update or write data by using a form that exposes that data, the user should not have permission to update or write data by using an entity that exposes that data. 

### Why is the Publish button in the Excel Add-in unavailable? 

All key and mandatory fields must be present to publish data back to the entity. Try to edit the design to add more fields to the binding. 

### Why are the Excel Add-in, the Word Add-in, and the Open in Excel options only available when the Internet is available?

For all environments, including on-premises, the Excel and Word Add-ins, and the libraries they use, are loaded from multiple Internet locations and therefore will only run when the Internet is available. For on-premises environments, when the Internet is not available, the Open in Excel options are hidden because the Excel Add-in will not run without access to the Content Delivery Network (CDN) that houses the Excel Add-in. 

### Can the Excel Add-in and Word Add-in be made available to users using Centralized Deployment?

Yes, Centralized Deployment is supported. For more information, see [Centralized Deployment](https://docs.microsoft.com/office/dev/add-ins/publish/centralized-deployment). 

To use Centralized Deployment, on the **App parameters** tab on the **Office App Parameters** page change the **App ID**, **Store**, and **Store Type**:

- **App ID**: 61bcc63f-b860-4280-8280-3e4fb5ea7726
- **Store**: EXCatalog
- **Store Type**: Centralized Deployment

In case a change back to Office Store is needed, the standard values are:
- **App ID**: WA104379629
- **Store**: en-US
- **Store Type**: Office Store

> [!NOTE]
>- **Name**, **Version**, and **Notes** are values that provide information but they are not needed to run the Excel Add-in.
>- These same values are also used for the Word Add-in when it is run from the Document Templates form.

If you encounter issues with Centralized Deployment for some users, it could be one of these problems:
-	One or more users are members in a group that is more restrictive than others
-	The user referenced is on a different Microsoft 365 account (such as a personal account)

### What is the cell limit for the Excel Add-in?

The default Excel Add-in cell limit is about half the limit of what the Excel Add-in can handle on a reasonably fast machine. The speed of the machine is the limitation. If problems are encountered, then the cell limit should be reduced and/or the filter should be adjusted to reduce the data set. A common workaround is to use a filter to manage the data in smaller pieces instead of all at once.

### How do I make an entity available in the Excel Add-in and/or as an Open in Excel option?

If the entity is marked as “IsPublic=Yes” and has unique PublicEntityName and PublicCollectionName values, then it will be available via the OData service. Check that there aren’t any existing entities with the same PublicEntityName and PublicCollectionName values by looking at the $metadata feed for the environment (preferably in Google Chrome): https://*SomeFullEnvironmentURL*.dynamics.com/data/$metadata

### Why are date and time values in UTC in the Excel Add-in?

The Excel Add-In, Data Management Framework, and Power BI reporting are all designed to interact with data directly on the database level. Because there is no client to adjust Date and Time data to the time zone of the user, all Date and Time values are in UTC.

## Troubleshooting issues

### \[Fixed\] Issue: During sign-in to the Excel Add-in, I receive the following error message: "AADSTS65001: The user or administrator has not consented to use the application with ID XYZ"

**Issue:** During sign in to the Excel Add-in, you receive the following error message: "AADSTS65001: The user or administrator has not consented to use the application with ID XYZ."

**Explanation:** Typically, this issue occurs because Microsoft Azure Active Directory (Azure AD) can't find the Azure AD application that represents the Excel Add-in. That issue occurs because, during the [configuration of Microsoft Power BI](../analytics/configure-power-bi-integration.md), an Azure AD application was added that has the App ID URI set to the environment URL. 

**Fix:** Make sure that no Azure AD apps have the App ID URI set to the environment URL. App ID URIs should be fabricated, unique URIs, such as `https://contosoAXPowerBI`.

### \[Fixed\] Issue: During sign-in to the Excel Add-in, I receive the following error message: "AADSTS50001: The application named ABC was not found in the tenant named XYZ"

**Issue:** During sign-in to the Excel Add-in, you receive the following error message: "AADSTS50001: The application named ABC was not found in the tenant named XYZ."

**Explanation:** This issue probably occurs because an error in the deployment system caused the environment to get a URL that wasn't added to the configured list of service principals for the tenant. 

**Fix:** File a support issue for your environment, so that the problem can be investigated and the configuration can be adjusted.

### \[Fixed\] Issue: After the Excel Add-in starts and updates data, I receive the following error message: "An error occurred while writing to the data cache"

**Issue:** After the Excel Add-in starts and updates data, you receive the following error message: "An error occurred while writing to the data cache." The details of the error state, "The argument is invalid or missing or has an incorrect format." 

**Explanation:** You receive this error message if the client is open in Internet Explorer, and the user clicks **Open** immediately after he or she selects the **Open in Excel** option. The way that Internet Explorer handles temporary Internet files causes an issue in Excel. This issue, in turn, causes API calls to fail. 

**Workaround:** In Internet Explorer, when you open a workbook, click **Save** first, and then click **Open**. The file will then be opened from your Downloads folder. Alternately, use the Edge or Google Chrome browser. By default, both these browsers save files to a Downloads folder. Therefore, the issue doesn't occur. 

**Long-term fix:** We are working with the Office team to understand this issue so that it can be fixed in Excel.

### Issue: When I send email by using SMTP, the server response is "5.7.60 SMTP; Client does not have permissions to send as this sender"

**Issue:** When you send email by using Simple Mail Transfer Protocol (SMTP), you might receive an error message that states that the server response was "5.7.60 SMTP; Client does not have permissions to send as this sender." Alternatively, the error message might state, "Something went wrong while generating the report."

**Explanation:** This issue is usually caused by incorrect setup of the Send As permissions for the email account. 

**Fix:** You can configure Send As permissions in the Microsoft 365 admin center (portal.office.com/Admin). Click **Users** > **Active users** > **User** > **Edit mailbox permissions** > **Send email from this mailbox**. For more information, see [Give mailbox permissions to another user in Microsoft 365 - Admin Help](https://support.office.com/article/Enable-sending-email-from-another-user-s-mailbox-in-Office-365-2B828C5F-41AB-4904-97B9-3B63D8129C4E). 

The following illustration shows the setup of SMTP on the **Email parameters** page. Here, you must provide the outgoing mail server, port, user name, password, and Secure Sockets Layer (SSL) requirements. 

[![SMTP settings tab on the Email parameters page](./media/smtp.png)](./media/smtp.png)

> [!IMPORTANT]
> All users must give the SMTP account Send As permissions on their email setup in Microsoft 365. This configuration is done in the mailbox permissions in Microsoft Exchange or in the Microsoft 365 Admin portal. The following illustration shows the setup for the Test User account, where the STMP service account is added in the **Send As** section. 

[![SMTP account that is granted Send As permissions in Microsoft 365](./media/o365.png)](./media/o365.png)

### \[Fixed\] Issue: The Office Add-ins don't yet support AD FS

**Affected versions:** CTP8 and the February 2016 releases 

**Issue:** When users from an Azure AD tenant that uses Active Directory Federation Services (AD FS) try to sign in to the Office Add-ins (in other words, when the users enter their account, and then press Tab or click in the field to enter their password), a separate browser window opens. This browser window usually has a URL that starts with `https://az689774.vo.msecnd.net/dynamicsofficeapp/v1.2.1.0/App/DynamicsApp.html\#id\_token=`. The user can't sign in. 

**Explanation:** During sign-in to the Office add-ins (both the Excel Add-in and the Word Add-in), a redirect to the AD FS site for the tenant occurs. However, that site is an unknown and therefore disallowed application domain (AppDomain). 

**Long-term fix:** The long-term fix for this issue was put in place on May 10, 2016. The Office Add-ins now use a new Dialog API that the Office team added. 

**Taking advantage of the add-in updates that support AD FS:** All Office installations should be updated via **File** > **Account** > **Updates** (for click-to-run installations) or via Windows Update (for MSI installations). The AD FS Dialog API was included in the May update ([16.0.6868.2060](https://answers.microsoft.com/msoffice/forum/all/may-update-16068682060-for-office-2016-on-windows/ea082237-7ec3-4b06-895b-83490980e6d2)). For information about updates, see the [Microsoft 365 client update channel releases](https://technet.microsoft.com/office/mt465751?f=255&MSPPError=-2147217396) page. 

If your Office build isn't updated, you might be on the deferred track ([Overview of update channels for Microsoft 365 Apps](https://technet.microsoft.com/library/mt455210.aspx)). In this case, you can [use the Office Deployment Tool to move to the Current channel](https://technet.microsoft.com/library/jj219422.aspx?f=255&MSPPError=-2147217396) or sign up for the [Office Insider program](https://products.office.com/office-insider) to help guarantee that you have the latest updates. Additionally, see [Install the latest version of Office](https://docs.microsoft.com/office/dev/add-ins/develop/install-latest-office-version) and [Office 2016 Deployment Guides for Admins](https://technet.microsoft.com/library/cc303401(v=office.16).aspx). 

If Office updates can't be installed, the following workaround can unblock users.

#### Workaround: Use Internet Explorer to sign in to the client before you use the Office Add-ins

This workaround requires user knowledge and extra steps. After users have been educated about this workaround, it should be straightforward for them. 

**User steps:** Before users open Excel (or Word), they should sign in to the client by using Internet Explorer. 

**Explanation:** The Excel or Word Add-in will use the sign-in context, and no redirect will be required. The earlier sign-in must occur in Internet Explorer, because the Office Add-ins run inside an Internet Explorer window in Excel and Word. The sign-in context lasts 6 to 24 hours, depending on policies. Therefore, a new sign-in through Internet Explorer is required only occasionally.

1.  Exit Internet Explorer and Excel.
2.  Start Internet Explorer, and sign in to the client.
3.  Test the Excel Add-in by using an Open in Excel experience. (For example, click **Fleet Management** &gt; **Customers** &gt; **Customer** &gt; **Open in Microsoft Office** &gt; **Open in Excel** &gt; **Fleet Management Customers**.)

### \[Fixed\] Issue: The Excel Add-in doesn't correctly run or enable sign-in

**Issue:** When users try to sign into the Excel Add-in, a blank authentication dialog box appears, or an error message is shown instead of the authentication page. The user can't sign in. 

**Explanation:** The Excel Add-in relies on the Office Web JS Add-in platform and uses Azure AD for authentication. If a proxy is used, several URLs must be accessible for users to run and sign in to the Excel Add-in. Additionally, if AD FS is used, the AD FS URL must use HTTPS. 

**Solution:** Because this issue is a customer-specific network issue, it requires a customer-specific resolution. If AD FS is used, make sure that the AD FS URL uses HTTPS. Additionally, make sure that all the following URLs are accessible from the user's computer.

The following URLs are accessed for loading.

- `https://az689774.vo.msecnd.net:443`
- `https://az689774.vo.msecnd.net`
- `https://appsforoffice.microsoft.com:443`
- `https://appsforoffice.microsoft.com`
- `https://secure.aadcdn.microsoftonline-p.com:443`
- `https://secure.aadcdn.microsoftonline-p.com`
- `https://az416426.vo.msecnd.net:443`
- `https://az416426.vo.msecnd.net`
- `https://telemetryservice.firstpartyapps.oaspapps.com:443`
- `https://telemetryservice.firstpartyapps.oaspapps.com`
- `https://nexus.officeapps.live.com:443`
- `https://nexus.officeapps.live.com`
- `https://browser.pipe.aria.microsoft.com:443`
- `https://browser.pipe.aria.microsoft.com`
- `http://schemas.microsoft.com`

The following URLs are accessed for authentication.

- `https://login.windows.net:443`
- `https://login.windows.net`
- `https://login.microsoftonline.com:443`
- `https://login.microsoftonline.com`

### Issue: The Excel Add-in needs an explicit sign out after encountering an AADSTS50058 "silent sign in failed" error

**Issue:** When users try to sign in to the Excel Add-in after some period of inactivity, the user encounters the AADSTS50058 "silent sign in failed" error and is forced to sign out before signing back in.

**Explanation:** The Excel Add-in uses Azure AD for authentication. When authentication occurs, a token is created for the user. That token has an expiration period. After the token has expired, an AADSTS50058 error will occur indicating that "silent sign in failed".

**Solution:** The user needs to sign out and sign back in. We will improve this behavior in the future by automatically signing the user out to enable faster sign in.

### Issue: When trying to use a document template with Open in Excel a "Record for id GUID not found" error displays

**Issue:** The "Record for id GUID not found" error can display when copying a database from one environment to another. 

**Explanation:** Copying the database is problematic for document templates, record attachments, and other files that are stored in Azure blob storage. When the database is copied from one environment to another, the files are not copied along with the records, so the files that the application tries to access are not found. 

**Solution:** For document templates, the solution is to identify the templates that are needed and load a copy of those template files into the target environment.

## Additional resources

[Office integration](office-integration.md)

[Office integration tutorial](office-integration-tutorial.md)

[Configuring Power BI integration](../analytics/configure-power-bi-integration.md)
