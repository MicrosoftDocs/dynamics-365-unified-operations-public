---
# required metadata

title: Authenticate with Dynamics 365 for Finance and Operations web services in on-premises
description: This topic...
author: PeterRFriis
manager: AnnBe
ms.date: 09/30/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: perahlff
ms.search.validFrom: 2020-09-30
ms.dyn365.ops.version: 10.0.15
---

# Authenticate with Dynamics 365 for Finance and Operations web services in on-premises

[!include[banner](../includes/banner.md)]

This blog explains how to take the standard examples for Dynamics 365 for
Finance and Operations integration from Github and authenticate to an
on-premises instance of Finance and Operations. At the end you'll also find some
troubleshooting tips if it doesn't work first time, which can be useful for any
scenario where something is trying to authenticate to services.

**Environment prerequisites**

There are a few items required before you start:  
- Installed Visual Studio 2017 Enterprise edition (edition appears to not be
important)  
- Downloaded the examples from
GitHub: <https://github.com/Microsoft/Dynamics-AX-Integration>  
- Open the ServicesSamples.sln solution  
- Within Visual Studio, go to Tools-\>NuGet package manager-\> manage NuGet
packages for solution, there it recognises there are some missing – click
restore in the top right and it downloads them automatically.

**ADFS Setup**

Now on ADFS server in my on-prem environment, I need to add a client
application. From “AD FS Management” I see Application Groups, open the default
application group for Dynamics 365 called “Microsoft Dynamics 365 for Operations
On-Premises”, it will look something similar to this:  


![ADFS application group](media/d0da8e0a79aa3740776b0079f5e8c0f9.jpg)

Click “Add application…” at the bottom, add a new server application:  


![Add new application](media/b717bbf99238d32d3f1dd8121fedecab.jpg)

Add the redirect URL, this should be the URL for the D365 application, take a
note of the client identifier as you’ll need to use this in your client
application later:  


![Add the redirect URL](media/bbca99e5b4261e46a7cf045a66d91ba1.jpg)

Select to generate a shared secret – you must copy this now, as it will not be
shown again – your client app needs this detail to connect to D365:  


![Generate shared secret](media/671f74727f73dd80782e8bd05b40125f.jpg)

 

![Summary](media/23252e559636e45c06f52c1d3d97e76e.jpg)

 

![Completed](media/8ce9a24c3147435108d1171cbf7e234d.jpg)

Next, back in the application group window, edit the “Microsoft Dynamics 365 for
Operations On-premises – Web API” item:  


![Edit application group](media/49abfce9ed372f37ff3a0645a6753042.jpg)

On the “Client permissions” tab add a new record for the server application
created in the previous step:  


![Add a new record for server application](media/e771ad8f461c141b169f633a944e55db.jpg)

**Code**

Within the ServicesSamples.sln solution open the ClientConfiguration.cs source
file and modify similar to below (using the values from your ADFS configuration
above):

public static ClientConfiguration OneBox = new ClientConfiguration() { UriString
= "https://ax.d365ffo.zone1.saonprem.com/namespaces/AXSF/", //the normal URL for
logging into D365 UserName = "not used", Password = "", //Note that AOS config
XML is on AOS machines in:
C:\\ProgramData\\SF\\AOS_10\\Fabric\\work\\Applications\\AXSFType_App84\\AXSF.Package.1.0.xml
ActiveDirectoryResource = "https://ax.d365ffo.zone1.saonprem.com/", //this is
the value for AADValidAudience from the AOS config xml ActiveDirectoryTenant =
"https://dax7sqlaoadfs1.saonprem.com/adfs",//this is the value for
AADIssuerNameFormat (minus the placeholder {0}, instead suffix "/adfs") from AOS
config xml ActiveDirectoryClientAppId = "6c371040-cf6b-4154-b9c4-75e613fb5104",
//client app ID is from ADFS management - configure a application group
ActiveDirectoryClientAppSecret = "MO-tVemKqAjVLj1NdcCs3mfiWw2X3ZNyjuFe0UYg",
//secret is from ADFS management - same place as the client app ID // Change TLS
version of HTTP request from the client here // Ex: TLSVersion = "1.2" // Leave
it empty if want to use the default version TLSVersion = "", };

**AX Setup**

Also need to add the application in AX application too, under System
administration \> setup \> Azure Active Directory applications, using the client
ID you put into your client code:  


![AX Setup](media/ebe391514951cc7ca85d1aff56636f8d.jpg)

**Troubleshooting:**

**ADFS group creation fails**

If ADFS group creation fails as shown below with the error MSIS7613 Each
identifier must be unique across all relying party trusts in AD FS
configuration. This means that the URL entered for Web API is already registered
in another group – probably the default D365 group. To resolve this see below.  


![ADFS group creation fails](media/78e28611501b16b5b5c0f26034eabff5.jpg)

Locate the standard Microsoft Dynamics 365 for Operations On-premises ADFS
application group and open it.  


![ADFS configuration](media/aa596975be552212eeff7b3a47b86b9f.jpg)

**Forbidden**

The error below occurs if the setup within AX hasn’t been completed within the
AX application under System administration \> setup \> Azure Active Directory
applications. The error below was reported back to the calling client
application.  
0:025\> !pe Exception object: 0000029e2b48e1d8 Exception type:
System.ServiceModel.Web.WebFaultException\`1[[System.ComponentModel.Win32Exception,
System]] Message: Forbidden InnerException: \<none\> StackTrace (generated):
\<none\> StackTraceString: \<none\> HResult: 80131501 0:025\> !clrstack OS
Thread Id: 0x1cb4 (25) Child SP IP Call Site 000000f0381bc3e8 00007ff86e233c58
[HelperMethodFrame: 000000f0381bc3e8] 000000f0381bc4d0 00007ff808fe8642
Microsoft.Dynamics.Ax.Services.ServicesSessionProvider.ThrowSessionCreationException(Microsoft.Dynamics.Ax.Services.ServicesSessionCreationErrorCode)
000000f0381bc520 00007ff808fe45b0
Microsoft.Dynamics.Ax.Services.ServicesSessionProvider.GetSession(Boolean,
Boolean, System.String, System.String, System.String, System.String,
System.Security.Claims.ClaimsIdentity) 000000f0381bc690 00007ff808fe4014
Microsoft.Dynamics.Ax.Services.ServicesSessionManager.InitThreadSession(Boolean,
Microsoft.Dynamics.Ax.Xpp.AxShared.SessionType, Boolean, System.String,
System.String, System.String, System.String,
System.Security.Claims.ClaimsIdentity) 000000f0381bc730 00007ff808fe3ea6
Microsoft.Dynamics.Platform.Integration.Common.SessionManagement.ServicesAosSessionManager.InitializeSession(Boolean,
System.String, System.Security.Claims.ClaimsIdentity) 000000f0381bc7a0
00007ff808fe366a
Microsoft.Dynamics.Platform.Integration.Common.SessionManagement.OwinRequestSessionProvider.CreateSession(System.Security.Claims.ClaimsIdentity)
000000f0381bc7f0 00007ff808fe34cc
Microsoft.Dynamics.Platform.Integration.Common.SessionManagement.ServicesRequestSessionHelper.EnsureRequestSession(Microsoft.Dynamics.Platform.Integration.Common.SessionManagement.IServicesRequestSessionProvider,
System.Security.Claims.ClaimsIdentity) 000000f0381bc830 00007ff808fe2a86

**Audience validation failed**

The error below occurs if the value you’re using in your client application for
ActiveDirectoryResource (from ClientConfiguration.cs in the example apps)
doesn’t match the value in the AOS configuration for AADValidAudience. The AOS
configuration is here:
C:\\ProgramData\\SF\\AOS_10\\Fabric\\work\\Applications\\AXSFType_App84\\AXSF.Package.1.0.xml  
Note that the error passed back to the client application is not as detailed as
this – this error was from catching the exception directly on the AOS machine
using WinDbg.

0:029\> !pe Exception object: 00000166f07da608 Exception type:
System.IdentityModel.Tokens.SecurityTokenInvalidAudienceException Message:
IDX10214: Audience validation failed. Audiences: 'http://tariqapp.saonprem.com'.
Did not match: validationParameters.ValidAudience: 'null' or
validationParameters.ValidAudiences: 'https://ax.d365ffo.zone1.saonprem.com,
00000015-0000-0000-c000-000000000000, https://ax.d365ffo.zone1.saonprem.com/'
InnerException: \<none\> StackTrace (generated): \<none\> StackTraceString:
\<none\> HResult: 80131501

**Strong name validation failed on first client application run**

If you tried to run OdataConsoleApplication and it failed with error: Could not
load file or assembly 'Microsoft.OData.Client, Version=6.11.0.0,
Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
Strong name validation failed. (Exception from HRESULT: 0x8013141A)

The root cause of this could be that it’s looking for 6.11 but 6.15 is the
version installed – from the NuGet package manager in VS you can change the
version, then build, success, then run, success.

**ADFS error log**

To help troubleshoot ADFS errors you can view the event viewer on the ADFS
server, as shown below, it’s under Applications and services logs \> AD FS \>
Admin.  


![ADFS error log](media/408738add91f9c313c285a4742eacb6a.jpg)
