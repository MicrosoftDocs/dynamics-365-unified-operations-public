---
# required metadata

title: Troubleshoot the Office integration
description: This article provides answers to questions, tips, and troubleshooting information for the Microsoft Office integration capabilities.
author: jasongre
ms.date: 04/12/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: OfficeAppParameters, SysEmailParameters
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 89588fed-b47f-4f01-9328-325518f016d6
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Troubleshoot the Office integration

[!include [applies to](../includes/applies-to-commerce-finance-hr-scm.md)]

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]


This article provides answers to questions, tips, and troubleshooting information about the capabilities of the Microsoft Office integration. The questions and issues that are discussed range across user, administration, and development scenarios.

## Frequently asked questions

### What platforms do the Office Add-ins support?

The Microsoft Excel Add-in and Microsoft Word Add-in are built by using the Office Web/JavaScript Add-in framework. This framework was originally released for Microsoft Office 2013 but received significant updates in Microsoft Office 2016. For more information, see [Office Add-in host and platform availability](/office/dev/add-ins/overview/office-add-in-availability). The Excel Add-in requires ExcelAPI 1.2. Therefore, use the [Office Add-in host and platform availability](/office/dev/add-ins/overview/office-add-in-availability) matrix to determine which platforms support the Excel Add-in. For many users, the phrase "Excel 2016 with the latest updates" is sufficient.

### Are the Office Add-ins safe?

In an age of malware, full connectivity, and compliance risks, nothing is completely secure. However, the web add-ins, like other websites, are basically a web application that interacts with the Office client products via a limited application programming interface (API). For more details, see [Office Add-ins platform overview](/office/dev/add-ins/overview/office-add-ins)

### Does the Excel Add-in support Office for Mac?

No. The Office JavaScript (JS) APIs work differently in Apple Safari and Microsoft Edge/Internet Explorer, especially in respect to authentication. For details about platform support for the Office JS APIs, see [Office Add-in host and platform availability](/office/dev/add-ins/overview/office-add-in-availability).

### What version of Office is required for the Excel Add-in to support AD FS?

For more information, see the "Troubleshooting issue" section later in this article.

### How can I force an update of Office?

If your Office build isn't updated, you might be on the deferred track ([Overview of update channels for Microsoft 365 Apps](/deployoffice/overview-update-channels)). In this case, you can [use the Office Deployment Tool to move to the Current channel](/deployoffice/overview-office-deployment-tool?f=255&MSPPError=-2147217396) or sign up for the [Office Insider program](https://products.office.com/office-insider) to help guarantee that you have the latest updates. The easiest method is to use the Office Deployment Tool to switch to the Current channel. In this case, the latest updates will be installed immediately.

### Why can't you tell me what version of Office or Excel a particular issue is fixed in?

Office has many releases. These releases receive updates at different times and have different version numbers that don't correspond. Some frequently used Office versions and update methods are Click to Run (C2R) Current channel, C2R Deferred, C2R First Update Deferred, Office Insider Fast, Office Insider Slow, and MSI/MSO (install from DVD). For more information about Office versions, see the [Release information for updates to Microsoft 365 Apps](/officeupdates/release-notes-microsoft365-apps?f=255&MSPPError=-2147217396) page.

### Why am I having trouble signing into the Excel Add-in?

The browser used to authenticate the Excel Add-in (or any Office add-in) is dependent on the Office and operation system versions. For more information about the specific browser used to sign in for your configuration, see [Browsers used by Office Add-ins](/office/dev/add-ins/concepts/browsers-used-by-office-web-add-ins). By default, the Excel Add-in picks up stored credentials from the browser, and the browser provides the current Microsoft Windows credentials if there are no stored credentials. Make sure that you're using the correct credentials to sign in. In the Excel Add-in, explicitly sign out, and then sign in to ensure that the correct credentials are used.

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

### Is Export to Excel the best way to get data out of the system?

The best way for end users to get data out of the system is to use the Excel Add-in. The add-in relies on the Open Data Protocol (OData) service to retrieve data and takes advantage of the security that data entities provide. The import and export capabilities in the Data management framework (DMF) and Data import/export framework (DIXF) can also be used. However, DMF and DIXF are often limited to administrators. Additionally, you might consider exploring the available [reporting and analytic features](../analytics/bi-reporting-home-page.md) in the product.

When the previously mentioned options can't be used, you might consider the Export to Excel functionality, which can be useful for retrieving data from calculated columns (display methods), columns that have formatted values, and data from temporary tables. Because the export process uses the data from the active form to retrieve data, Export to Excel will return the data exactly as it is shown in the grid. Additionally, it will return only the data that matches the current set of filters.

Export to Excel does have its own set of limitations. First, this mechanism takes more time to export than the options that go through the OData service, and the time to export can be significant for larger exports. Secondly, the export of data to Excel is a memory-intensive process that can cause out-of-memory errors to occur and servers to stop responding, especially if the organization increases the export row limit beyond the default value. Export to Excel isn't intended for auditing purposes. When very large datasets must be exported from the system, data management is recommended.

> [!WARNING]
> Although organizations can increase the default Export to Excel row limit (50,000 records), we **strongly recommend** that you **not** raise this limit above 100,000 records. Depending on the characteristics of the environment and the specific grid that is being exported, even that limit might be too high and might cause memory issues.

Because an export from Excel can take some time, it is recommended that the export is done with the Chrome or Edge browsers, with the automatic download option enabled. The automatic download option will ensure that the browser downloads the file as soon as the export is complete to ensure that the download link is used within the 15-minute time limit.

### Why is the Publish button in the Excel Add-in unavailable? 

Hover over the **Publish** button to get more information as to why publishing currently isn't supported. Typically when this occurs, it is because all key and required fields must be present to publish data back to the entity, in which case you should open the designer and make sure all the key fields are bound.  

### Why are the Excel Add-in, the Word Add-in, and the Open in Excel options only available when the Internet is available?

For all environments, including on-premises, the Excel and Word Add-ins, and the libraries they use, are loaded from multiple Internet locations and therefore will only run when the Internet is available. For on-premises environments, when the Internet is not available, the Open in Excel options are hidden because the Excel Add-in will not run without access to the Content Delivery Network (CDN) that houses the Excel Add-in. 

### Can the Excel Add-in and Word Add-in be made available to users using Centralized Deployment?

Yes, Centralized Deployment is supported. For more information, see [Centralized Deployment](/office/dev/add-ins/publish/centralized-deployment). 

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

### When is Skype integration supported?

Skype integration is available for environments in the public cloud. For environments outside of the public cloud, including on-premises environments, Skype integration is not currently supported. 

## Troubleshooting issues

### Issue: The Excel add-in loads, but instead of showing data, it displays "Load applets" in the task pane 

**Issue:**  The Excel add-in loads, but instead of showing data, it displays "Load applets" in the task pane. 

**Explanation:** This issue usually occurs due to one of the following reasons:

-   Incorrect sign in
-   Add-in registration data has not been initialized in the environment
-   OData issues 

**Fix:** 
-  **Incorrect sign in**: The most likely cause of this issue is that the user is signed in as the wrong user. This can happen if the user has multiple accounts and the browser uses the wrong user context. Before trying any other fix, you should sign out of the add-in using the user menu in the upper-right corner and then sign back in to the add-in. If the issue continues to persist, ensure registration data is properly initialized, as noted in the following fix. 

-  **Registration data not initialized**: If the issue wasn't addressed by signing back in to the add-in, another potential cause is that the environment doesn't yet have the add-in data initialized. To check this, the admin can navigate to the **Office app parameters** page. For each of the **App parameters**, **Registered applets**, and **Registered resources** tabs on that page, verify that there is data populated in each tab. If any tab has an empty grid, select the appropriate **Initialize** button on that tab. 

-  **OData issue**: If the issue persists after attempting the previous two fixes, then the final cause of this issue could be that the OData service, through which the add-in communicates with finance and operations, is unable to return the registration data to the add-in. Without that data, the add-in will fail to load applets. At this stage, you will need to contact Microsoft Support with information from the **Application correlation ID** from the Excel add-in with the failed session. You can find this field under **Options**.

### Issue: During sign-in to the Excel Add-in, users receive an error message saying they "cannot access the application '2bc50526-cdc3-4e36-a970-c284c34cbd6e' in that tenant"

**Issue:** During sign in to the Excel Add-in, a user receives an error similar to the following: 
-  "AADSTS50020: User account 'XXX' from identity provider 'https://sts.windows.net/XXX' does not exist in tenant 'XXX' and cannot access the application '2bc50526-cdc3-4e36-a970-c284c34cbd6e'(Microsoft Business Office Add-in) in that tenant."
-  "Selected user account does not exist in tenant 'XXX' and cannot access the application '2bc50526-cdc3-4e36-a970-c284c34cbd6e' in that tenant."

**Explanation:** This issue is caused by a change made to Azure Active Directory (Azure AD) in April 2021 in regard to external users. Because this change was not made to the finance and operations apps, it can affect customers on any version of the platform or application.  

**Fix:** All external users need to be invited to the tenant through Azure AD. For more information, see [Invite users with Azure Active Directory B2B collaboration](/power-platform/admin/invite-users-azure-active-directory-b2b-collaboration).

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

**Explanation:** You receive this error message if the client is open in Internet Explorer, and the user clicks **Open** immediately after selecting the **Open in Excel** option. The way that Internet Explorer handles temporary Internet files causes an issue in Excel. This issue, in turn, causes API calls to fail. 

**Workaround:** The recommendation is to use Microsoft Edge or another modern browser. These browsers tend to save files to a Downloads folder by default, which mitigates the issue. If you are using Internet Explorer, which is now deprecated, when you open a workbook, select **Save** first, and then select **Open**. The file will then be opened from your Downloads folder.  

**Long-term fix:** We are working with the Office team to understand this issue so that it can be fixed in Excel.

### Issue: VPN users see a blank authentication screen when trying to sign into the Excel add-in

**Issue**: Users using a virtual private network (VPN) aren't able to sign in to the add-in because the authentication dialog appears blank or is missing text.  

**Fix**: The issue must be solved from the customer side, as the VPN software or browser settings when running under VPN are preventing their machines from retrieving resources and/or interpreting those resources correctly.

Here are some common solutions to VPN issues:
-  Verify that the user has access to the locations listed in: [Issue: The Excel Add-in doesn't correctly run or enable sign-in](#fixed-issue-the-excel-add-in-doesnt-correctly-run-or-enable-sign-in).
-  Verify that your browser isn't set to "Display intranet sites in Compatibility view" for Microsoft Edge (or Internet Explorer 11). This can be configured by organization policy. 
-  Have the affected user compare their VPN and Edge/IE browser settings with other users who aren't impacted.

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


**Alternate solution:** If the user is running an older version of Windows 10 (earlier than version 1909), consider upgrading Windows 10 to version 1909 or later. Version 1909 may need KB5003635. For more information, see [May 2021 resolved issues](/windows/release-health/resolved-issues-windows-10-1909#1610msgdesc). 

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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

