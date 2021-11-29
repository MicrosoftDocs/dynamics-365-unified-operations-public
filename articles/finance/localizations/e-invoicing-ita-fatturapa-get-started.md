---
# required metadata

title: Get started with Electronic invoicing for Italy
description: This topic provides information that will help you get started with Electronic invoicing for Italy.
author: abaryshnikov
ms.date: 11/29/2021
ms.topic: article
audience: Application User, Developer
ms.reviewer: rhaertle
ms.custom: <remove if blank>
ms.search.region: Global
ms.author: abaryshnikov
ms.search.validFrom: 2021-10-18
ms.dyn365.ops.version: AX 10.0.20
---

# Get started with Electronic invoicing for Italy

[!include [banner](../includes/banner.md)]


> [!IMPORTANT]
> Electronic invoicing for Italy might not currently support all the functions that are available for electronic invoices in Dynamics 365 Finance and Dynamics 365 Supply Chain Management. 

This topic provides information that will help you to get started with Electronic invoicing for Italy in Finance and Supply Chain Management. This topic guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Services (RCS). These steps complement the steps that are described in the topic, [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Prerequisites

Before you complete the steps in this topic, the following prerequisites must be met:

- Complete the steps in the topic, [Get started with Electronic invoicing](e-invoicing-get-started.md).
- Import the **Italian FatturaPA (IT)** electronic invoicing feature into RCS from the Global repository. For more information, see [Import an Electronic invoicing feature from the Microsoft configuration provider](e-invoicing-get-started.md#import-an-electronic-invoicing-feature-from-the-microsoft-configuration-provider) section in the topic, **Get started with Electronic invoicing**.
-  Add links from the required certificates to the service environment. This includes the Digital signature certificate, CA certificate, and the Clients certificate. For more information, see the section [Create a digital certificate secret](e-invoicing-get-started-service-administration.md#create-a-digital-certificate-secret) in the topic, **Get started with Electronic invoicing service administration**.

## Country-specific configuration for the Italian FatturaPA (IT) Electronic invoicing feature

Complete the following steps before you deploy the application setup to your connected Finance or Supply Chain Management application.

This section complements the section, [Country-specific configuration of application setup](e-invoicing-get-started.md#country-specific-configuration-of-application-setup) in the topic, **Get started with Electronic invoicing**.

### Create a new feature

1. Log in to the **Regulatory configuration service**.
2. In the **Electronic reporting** workspace, in the **Configuration providers** section, mark your company's **Configuration provider** as active.
3. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
4. On the **Electronic invoicing features** page, select **Add** > **Based on existing feature**.
5. Under the **Microsoft configuration provider**, select **Italian FatturaPA (IT)** as a base feature, enter a name and then select **Create feature**.

### Set up application specific parameters

1. On the **Versions** tab, verify that the **Draft** version is selected.
2. On the **Configurations** tab, select **Application specific parameters** for a selected configuration. 
3. In the **Lookups** section, make sure that the lookup, **List of Natura reverse charge subcategories** is selected.
4. In the **Conditions** section, select **Add**.
5. Add specific conditions for each subcategory that is defined in the system and then save your changes.  

   > [!NOTE]
   > In the **Name** column, you can select the **\*Blank\*** or **\*Not blank\*** placeholder value instead of a specific value.

### Configure a processing pipeline for export

1. On the **Setups** tab, select **Edit** for sales invoices.
2. In the **Processing pipeline** section, go through the actions and fill in all the required parameters.
    - **Sign document** action: Certificate name (certificate for digital signature).
    - **Submit** action: URL address, Certificates (chain of certificates where the first one is the root CA certificate (caentrate.cer), second one is the Clients certificate.
3. Select **Validate** to ensure all required parameters are filled in.
4. Repeat for **Project invoices** setup on the **Setups** tab.

### Configure the processing pipeline for import

1. On the **Setups** tab, select **Edit** for the **Import invoices**.
2. In the **Data channel** section, on the **Parameters** tab, enter a string value in the **Data channel** field.
3. Fill in **Applicability rules** for the setup. You can use the default **Channel** clause by passing here the value for **Data channel** parameter value.

    ![Setup applicability rules](media/e-invoicing-ita-fatturapa-get-started-apprules-setup.png)
	
4. Select **Validate** to ensure all required parameters are filled in.

### Deploy the feature

1. Complete, publish, and deploy the feature to the service environment. For more information, see the section, [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment) in the topic, **Get started with Electronic invoicing**.
2. Deploy the feature to the connected application. For more information, see the section [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application) in the topic, **Get started with Electronic invoicing**.

### Set up Finance

1.  Sign in to your Finance environment.
2.  In the **Electronic reporting** workspace, in the **Configuration providers** section, select the **Microsoft** tile.
3.  Select **Repositories** > **Global** > **Open**.
4.  Select and import the Customer invoice context model and the Vendor invoice import (IT).
5.  Go to **Organization administration** > **Setup** > **Electronic document parameters**.
6.  On the **Features** tab, locate and select the feature, **Italian electronic invoice** and then select the **Enable** check box.
7.  On the **Electronic document** tab, make sure that the settings for **Customer invoice journal** and **Project invoice** are filled in according to information in the topic, [Configure the application setup](e-invoicing-get-started.md#configure-the-application-setup).

### Set up vendor invoice import 

1. In Finance, go to the **Electronic reporting** workspace. 
2. In the **Configuration providers** section, mark your company's **Configuration provider** as active.
3. Select **Reporting configurations**.
4. Select **Customer invoice context model**, and then select **Create configuration** > **Derive from Name: Customer invoice context, Microsoft** to create a derived configuration.
5. On the **Draft** version, select **Designer** and in the **Data model** tree, select **Map model to datasource**.
6. In the **Definitions** tree, select **DataChannel** > **Designer**.
7. In the **Data sources** tree, expand the **$Context\_Channel** container and in the **Value** field, select **Edit**. 
8. Enter the data channel name. The name should be less than or equal 10 characters. This name should match with the **Data channel** parameter value of the data channel for the Electronic invoicing feature in RCS.
9. Save your changes, and then go to **Reporting configurations** > **Complete configuration version**.
10. On the **External channels** tab, **Channels**, select **Add** and enter values in the **Channel field** (**$Context Channel** value), **Description**, and **Company** fields.
11. In the **Document context** field, select the newly derived configuration from **Customer invoice context model**. The mapping description should be **Data channel context**.
12. On **Import sources** tab select **Add** and enter the following field information:
	
    - **Name**: OutputFile
    - **Data entity name**: Vendor invoice header (Data entity: VendorInvoiceHeaderEntity)
    - **Model mapping**: Vendor invoice import (IT)

    > [!NOTE]
    > You can create several external channels and derived context configurations with different **$Context Channel** value for import vendor invoices from different sources. For example, if you want to import vendor invoices for different legal entities.

## Proxy server setup

### Create App registration

1. Create a self-signed certificate for service to service authentication. This can be done using a PowerShell script.
	
	```powershell
	$certOutputLocation = "C:\certs\proxytest"
	$certName = "sdiProxyClientS2SCert"
	$certPassword = "123"

	$certCerFile = Join-Path $certOutputLocation "$certName.cer"
	$certPfxFile = Join-Path $certOutputLocation "$certName.pfx"

	$securePassword = ConvertTo-SecureString $certPassword -AsPlainText -Force

	$cert = New-SelfSignedCertificate -KeyLength 2048 -KeyExportPolicy Exportable -FriendlyName "CN=$certName" -CertStoreLocation Cert:\CurrentUser\My -Subject $certName -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider"

	Export-Certificate -Cert $cert -FilePath $certCerFile -type CERT | Out-Null
	Export-PfxCertificate -Cert $cert -FilePath $certPfxFile -Password $securePassword | Out-Null
	```

2. Save the pfx certificate into the Key Vault and then delete the pfx certificate.
3. Log in to the [Azure portal](https://portal.azure.com) as an administrator.
5. Create app registration for **SDI Proxy service**.
    1. Go to **App registrations** and create a new registration with the following parameters:
	
        - **Name**: **SDI Proxy Client**
        - **Account type**: Accounts in this organizational directory only (single tenant)
		
    	![Create Azure App Registration](media/e-invoicing-ita-fatturapa-get-started-app-registration.png)

    2. Select **Register**.
    3. Select the app registration you created and then go to **API permissions**.
    4. Select ***Grant admin consent***.
	
	    ![Grant admin consent](media/e-invoicing-ita-fatturapa-get-started-app-registration-consent.png)
	
    5. Go to ***Certificates & secrets*** and upload the '.cer' certificate for service-to-service authentication.
	
        ![Upload certificate](media/e-invoicing-ita-fatturapa-get-started-app-upload-cert.png)

    6.  Go to ***Enterprise applications*** and select application created.
    7.  Save ***Application ID*** (Client ID) and ***Object ID*** of the app.
    8.  Contact with the **Invoicing Service** team to grant this app access to the service.
        Send to the <D365EInvoiceSupport@microsoft.com> the following parameters:
        - **AAD TenantID**  
        - **LCS Environment ID**
        - **Application ID** (Client ID)  
        - **Object ID**

6.  Add the ***Object ID*** to the Applications list of your service environment in RCS. **Save** and **Publish** changes.
    1.  In Regulatory configuration service go to Globalization features \> Environments \> Electronic Invoicing \> Service environments
    2.  Select your environment and add application to the list:
	
        ![Add the application to the service environment](media/e-invoicing-ita-fatturapa-get-started-add-app-to-env.png)

    3.  Save \> Publish

### Create Azure Virtual Machine:

1.  Go to **Virtual machines** and select **Create new**.
2.  Select you subscription and resource group (the same where you Key Vault and Blob storage are located).
3.  Chose the same region where your F&O instance has been deployed (as well as Key Vault and Blob storage).
4.  Insert administrators user name and password (and save them into the Key Vault).
5.  Inbound ports: HTTPS(443), RPD (3389) (it\`s recommended to disable RDP (3389) when the system goes to production. You can enable it back when it is necessary to connect to the VM in case of troubleshooting).

    ![Create Azure Virtual Machine. Basics](media/e-invoicing-ita-fatturapa-get-started-create-vm-1.png)

6.  Use managed disks, Do not use Ephemeral.

    ![Create Azure Virtual Machine. Disks](media/e-invoicing-ita-fatturapa-get-started-create-vm-2.png)

7.  On the Networking tab select **Public IP** \> **Create new** \> Select **Standard** SKU, **Static** assignment.

    ![Create Azure Virtual Machine. Networking](media/e-invoicing-ita-fatturapa-get-started-create-vm-3.png)

    ![Create Azure Virtual Machine. Public IP](media/e-invoicing-ita-fatturapa-get-started-create-vm-4.png)

8.  On the **Management** tab:
    1.  DISABLE **Auto-shutdown** policy on the **Management** tab.
    2.  Set **Manual** Guest OS updates.
    3.  All other policies can be set.
9.  Review and create Virtual Machine.
10.  Go to created VM \> Identity \> System assigned \> Status \> ON.
11.  Grant access to the Key Vault for the VM:
     1.  Go to Key Vault \> **Access control (IAM)** \> Role assignments.
     2.  Select **Add role assignment** and save then
         1.  Role: **Key Vault Secrets User**
         2.  Assign access to: **Virtual machine**
         3.  Subscription: your **subscription**
         4.  Select: find your **Virtual machine**
     1.  Go to Key Vault \> **Access policies**
     2.  Select **Add Access Policy**
         1.  Select Virtual machine as Selected principal.
         2.  Select Certificate \> **List**, **Get** permissions.
12.  Enable Application Insights.
    1.  Go to created Virtual machine \> Monitoring \> Insights.
    2.  Select **Enable** and follow the Application Insights creation guide.
13.  Go to **Public IP addresses** and select IP address created within the Virtual machine.
     1.  Go to **Configuration** and set the DNS name.

### Proxy service environment preparation.

Several steps should be done on machine where proxy service supposed to be hosted:
1.  Connect to the Virtual machine via Remote Desktop Connection.
2.  Open Local Machine Certificate snap-in following this [guide](/dotnet/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in).
3.  Import certificates caentrate.cer file for production and CAEntratetest.cer for test (Root CA certificate provided by authority) to **Trusted Root Certification Authorities**.
3.  Open **Turn on/off windows features** window (OR **Server Manager \> Add Roles And Features** for server OS) and turn on IIS features as on screenshot below:

    ![Turn on Windows Features](media/e-invoicing-ita-fatturapa-get-started-turnon-features.png)
	
### Setup SDI Proxy service on IIS.

1.  Take folder with SdiProxy solution: Go to **Shared asset library** as described in article: [Asset library in Lifecycle Services (LCS)](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/asset-library).
2.  Select asset type: Data package
3.  Find and download **Electronic Invoicing Service Sdi Proxy** to the Virtual machine.
4.  Configure service:
    1.  In **src\\FattureService** folder open **appsettings.json** and enter following parameters:
        1. **KeyVaultUri** - Address of the key vault which stores client certificate for invoicing service
        2. **TenantId** - GUID of the customer's tenant
        3. **EnvironmentId** - Id of LCS environment
        4. **ClientId** - AppId of intermediate services app registration in customer\`s tenant
        5. **ClientCertificateName** - name of the S2S certificate in the Key Vault
        6.  SecurityServiceClientOptions.**Endpoint** - Url address of the security service
        7.  SecurityServiceClientOptions.**Resource** - Scope to obtain token
        8.  InvoicingServiceClientOptions.**Endpoint** - endpoint of the Invoicing service. Should be the same as for RCS and F&O setup
        9.  InvoicingServiceClientOptions.**ServiceEnvironmentId** - name of the service environment. Should be the same as for F&O setup
        10. **NotificationsFolder** - folder to save incoming notifications files.
    2.  In web.config:
        1.  Change the following line by adding **proxy server certificate** thumbprint:
            \<serviceCertificate findValue="Put your cert thumbprint here" storeLocation="LocalMachine" storeName="My" x509FindType="FindByThumbprint" \>.
        2.  When the system goes to production the following values could be changed to reduce amount of logs collected and to save a disc space: in \<system.diagnostics\>\<source\> nodes find 'switchValue' parameters and change it values to "Critical, Error". More information could be found here: [MS Service Trace Viewer](/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe).

5.  Open IIS Manager.
6.  Stay on root node of left menu and, on right side, select **Server certificates**.

    ![Install the service certificate](media/e-invoicing-ita-fatturapa-get-started-proxy-cert-1.png)

7.  Open the menu and select Import (Upper right corner).
8.  Specify path to **proxy server** certificate (should be the pfx file).

    ![Install the service certificate. Selection](media/e-invoicing-ita-fatturapa-get-started-proxy-cert-2.png)

9.  Now do right select on **Sites** \> **Add website**.
10.  Specify any reasonable **Site name**.
11.  In **Physical path** point to folder with **FattureService** service (\\src\\FattureService).
12. Select **https** as **Binding Type**.
13. Specify Host name as **DNS** configured for the Virtual machine and for **proxy server certificate**.
14. Leave **Ip Address** and **Port** as default.
15. **Require Server Name Indication** should be **disabled** (because SDI does not support that technology).
16. SSL certificate: **proxy server certificate** imported before.
17. Application pool: keep specific pool for the site and save it\`s name (SdiAppPool)

    ![Configure IIS. Add Website](media/e-invoicing-ita-fatturapa-get-started-proxy-iis-setup-1.png)
	
18. After creating web site, open **SSL Settings** menu.

    ![Configure IIS. Open SSL Settings](media/e-invoicing-ita-fatturapa-get-started-proxy-iis-setup-2.png)

19. Check **Require SSL** and select **Client certificats**: Require.

    ![Configure IIS. SSL Settings](media/e-invoicing-ita-fatturapa-get-started-proxy-iis-setup-3.png)

20. Open **Directory Browsing** and select **Enable**.
21. Open Internet Explorer browser and check address **serverDNS/TrasmissioneFatture.svc**.
22. Browser can show error that "Site is not secure" - select **More Information** and select **Go to the website.** (for test environment)
23. A standard window about service must be shown up:

    ![Open browser to check the service](media/e-invoicing-ita-fatturapa-get-started-proxy-open-browser.png)

24. Create folders to store logs and files:
    1.  C:\\logs\\ - here the log files would be placed. They can be viewed by [MS Service Trace Viewer](/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)
    2.  C:\\files\\ - here all the response files would be placed
25.  Grant access to the folders for the **NETWORK SERVICE** and **IIS AppPool\\SdiAppPool** (or **IIS AppPool\\DefaultAppPool** for default )
    1.  Open context menu on the folder \> Properties \> Security \> Edit \> Add the users if they are not here
	
        ![Add permissions to the service user](media/e-invoicing-ita-fatturapa-get-started-proxy-add-user.png)

## Privacy notice 

Enabling the **Italian electronic invoice** feature may require sending limited data, which includes the organization tax registration ID. An administrator can enable and disable the Italian electronic invoice feature. To disable the feature, complete the following steps.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**. 
2. On the **Features** tab, select the rows that contain the **Italian electronic invoice** feature and then select **Disable now**. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
