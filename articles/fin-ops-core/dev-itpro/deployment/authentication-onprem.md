---
# required metadata

title: How authentication works in Dynamics 365 Finance + Operations (on-premises)
description: This topic...
author: faix
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
ms.author: osfaixat
ms.search.validFrom: 2020-09-30
ms.dyn365.ops.version: 10.0.15
---

# How authentication works in Dynamics 365 Finance + Operations (on-premises)

[!include[banner](../includes/banner.md)]

In this article we are going to explain authentication in Dynamics 365 Finance + Operations (on-premises). The intention of this article is to provide some background information on how the process works so that if you have issues you can work to resolve them.

First off, there's one option you provide during environment deployment: the URL for Active Directory Federation Services (AD FS). The URL will look similar to this: `https://adfs.contoso.com/adfs/.well-known/openid-configuration` 

You'll find the URL mentioned in the deployment instructions [here](./setup-deploy-on-premises-pu12.md#configureadfs)

During deployment this is going to be used to set various options in the AOS startup variables of each AOS instance. These startup variables reside in an xml config file located in a Service Fabric directory. This directory will vary from machine to machine but should look similar to: C:\\ProgramData\\SF\\AOS_10\\Fabric\\work\\Applications\\AXSFType_App218\\AXSF.Package.1.0.xml

Note that there is also a file called AXSF.Package.Current.xml. This file will be a copy of the AXSF.Package.1.0.xml in Finance and Operations deployments. The AXSF.Package.Current.xml represents the variable that have been used to initialize the currently running AOS instance (AxService.exe).

Within this configuration file (which is on each AOS machine) you'll find a few sections which are set from the LCS deployment setting for AD FS, this bit:

```xml
<Section Name="Aad">
    <Parameter Name="AADIssuerNameFormat" Value="http://ADFS.contoso.com/{0}/services/trust" />
    <Parameter Name="AADLoginWsfedEndpointFormat" Value="https://ADFS.contoso.com/{0}/wsfed" />
    <Parameter Name="AADMetadataLocationFormat" Value="https://ADFS.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml" />
    <Parameter Name="AADTenantId" Value="adfs" />
    <Parameter Name="AADValidAudience" Value="https://ax.contoso.com/" />
    <Parameter Name="ACSServiceEndpoint" Value="https://accounts.accesscontrol.windows-ppe.net/tokens/OAuth/2" />
    <Parameter Name="ACSServicePrincipal" Value="00000001-0001-0000-c000-000000000000" />
    <Parameter Name="ADFSEndpoint" Value="https://ADFS.contoso.com/adfs" />
    <Parameter Name="ADFSIdentifier" Value="http://ADFS.contoso.com/adfs/services/trust" />
    <Parameter Name="FederationMetadataLocation" Value="https://ADFS.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml" />
    <Parameter Name="Realm" Value="spn:00000015-0000-0000-c000-000000000000" />
    <Parameter Name="TenantDomainGUID" Value="adfs" />
    <Parameter Name="TrustedServiceAppIds" Value="913c6de4-2a4a-4a61-a9ce-945d2b2ce2e0" />
</Section>
```

Also these sections:

```xml
<Section Name="OfficeApps">
    <Parameter Name="AppInsightsKey" Value="" />
    <Parameter Name="AuthClientId" Value="d8230a86-015d-4c14-bcd6-c7fb65176b16" />
</Section>
<Section Name="OpenIDConnect">
    <Parameter Name="ClientID" Value="d8230a86-015d-4c14-bcd6-c7fb65176b16" />
    <Parameter Name="Metadata" Value="https://ADFS.contoso.com/adfs/.well-known/openid-configuration" />
</Section>
<Section Name="Provisioning">
    <Parameter Name="AdminIdentityProvider" Value="http://ADFS.contoso.com/adfs/services/trust" />
    <Parameter Name="AdminPrincipalName" Value="axserviceuser@contoso.com" />
</Section>
```

[!NOTE]
> The settings above represent a deployment configured with Microsoft 365 compatibility. You can find more information [here](./onprem-adfscompatibility.md)

The AOS is using these configuration values to know where to redirect an unathenticated request when a user hits the application URL:
    1. Request is sent by the browser to the application URL (https://ax.contoso.com/namespaces/AXSF/).
    2. The request is processed by the Gateway and gets forwarded to an AOS node accepting interactive sessions.
    3. The request reaches an AOS server and checks for the authentication cookies.
    4. No authentication is present so the AOS server returns a redirect request for the user to authenticate with AD FS. At this point the AOS also sets an affinity cookie to bind the user session to that AOS.
    5. The gateway returns this response to the Gateway and it in turn forwards it back to the browser.
    6. The browser receives the redirect request and brings up the AD FS authentication page so the user logs in.
    7. Once successfully authenticated against AD FS, then the AD FS redirects you back to the application URL and provides the authentication cookies.
    8. The Gateway receives this response and forwards the affinitized request to the appropriate AOS node.
    9. The AOS checks the authentication information provided and checks against the UserInfo table whether the user is allowed to access the application and which permissions it has.
    
If values in the AOS config file are incorrect, then that typically means the value provided for the AD FS endpoint during environment deployment was wrong. The easiest thing is
to delete and redeploy the environment from LCS with the right value. It is possible to manually edit the configuration files, but to be safe, do a redeploy. Otherwise you will need to manually change the values after each servicing operation on each AOS node. If you do edit the config files then you need to restart the AOS services for it to take effect. You can do that from the Service Fabric explorer (right click the AOS node under Nodes, choose restart, then wait for a minute or so for it's status to go back to green) or by rebooting the machine.

Receiving a 500 error when accessing the application URL is a symptom of having specified an invalid URL for ADFS. This is because the AOS on startup will reach to that url to obtain information from the AD FS server. If the URL is wrong or inaccessible the AOS will be unable to startup. 

The second piece to the authentication process is ADFS itself. On the ADFS server if you open "AD FS Management" (from Control Panel\\System and Security\\Administrative Tools), and look under "Application groups", you'll
find a group called "Microsoft Dynamics 365 for Operations On-premises". Within this group the settings for AD FS for your Dynamics application are kept.

![AD FS application group setup](media/ADFS.png)

AD FS uses the Client ID and the URLs to decide whether the request for access should be honored. You will notice that the Client ID from the screenshot above matches the IDs specified in the OfficeApps and OpenIDConnect sections from earlier. If both the client ID and the redirect URL don't match what the AOS is requesting, then AD FS will deny the request to authenticate. If that happens you'll find an error in the Event Log on the ADFS server. There's a special event log for AD FS under "Application and Services logs\\AD FS\\Admin"

![AD FS event log error](media/ADFSredirectwrong.png)

In the case that any of the AD FS application group setup is wrong, you're likely to see an error in it's event log which explains the value it was looking for, so you can figure out what is set incorrectly.
