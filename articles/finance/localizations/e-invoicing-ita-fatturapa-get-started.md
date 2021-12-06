---
# required metadata

title: Setup direct integration of Italian FatturaPA with SDI
description: This topic provides information that will help you get started with Electronic invoicing direct integration of Italian FatturaPA with SDI.
author: abaryshnikov
ms.date: 11/30/2021
ms.topic: article
audience: Application User, Developer
ms.reviewer: rhaertle
ms.custom: <remove if blank>
ms.search.region: Global
ms.author: abaryshnikov
ms.search.validFrom: 2021-10-18
ms.dyn365.ops.version: AX 10.0.20
---

# Get started with Electronic invoicing for Italy. FatturaPA SDI

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

1. On the **Electronic invoicing features** page, select Feature to edit.
2. On the **Versions** tab, verify that the **Draft** version is selected.
3. On the **Configurations** tab, select **Application specific parameters** for a selected configuration. 
4. In the **Lookups** section, make sure that the lookup, **List of Natura reverse charge subcategories** is selected.
5. In the **Conditions** section, select **Add**.
6. Add specific conditions for each subcategory that is defined in the system and then save your changes.  

   > [!NOTE]
   > In the **Name** column, you can select the **\*Blank\*** or **\*Not blank\*** placeholder value instead of a specific value.

### Configure a processing pipeline for export

1. On the **Electronic invoicing features** page, select Feature to edit.
2. On the **Setups** tab, select **Sales invoices** > select **Edit**.
3. In the **Processing pipeline** section, go through the actions and fill in all the required parameters:
    - For the **Sign document** action fill in the **Certificate name** parameter value (certificate for digital signature).
    - For the **Submit** action fill in **URL address** and **Certificates** parameters. **Certificates** is a chain of certificates where the first certificate is the root CA certificate (caentrate.cer), second certificate is the Clients certificate.
4. Select **Validate** to ensure all required parameters are filled in.
5. Save and close the form.
6. On the **Setups** tab, select **Project invoices** > select **Edit**.
7. Repeat steps 3-5 for **Project invoices**.

### Configure the processing pipeline for import

1. On the **Electronic invoicing features** page, select Feature to edit.
2. On the **Setups** tab, select **Import invoices** > select **Edit**.
3. In the **Data channel** section, on the **Parameters** tab, enter a string value in the **Data channel** field.
4. Fill in **Applicability rules** for the setup. You can use the default **Channel** clause by passing here the value for **Data channel** parameter value.

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
10. On the **External channels** tab, **Channels** section, select **Add** and enter values in the **Channel** field (**$Context Channel** value), **Description**, and **Company** fields.
11. In the **Document context** field, select the newly derived configuration from **Customer invoice context model**. The mapping description should be **Data channel context**.
12. On **Import sources** tab select **Add** and enter the following field information:
	
    - **Name**: OutputFile
    - **Data entity name**: Vendor invoice header (Data entity: VendorInvoiceHeaderEntity)
    - **Model mapping**: Vendor invoice import (IT)

    > [!NOTE]
    > You can create several external channels and derived context configurations with different **$Context Channel** value for import vendor invoices from different sources. For example, if you want to import vendor invoices for different legal entities.

## Proxy server setup

This topic provides information that will help you to setup and configure proxy service to communicate between Italian SDI and **Electronic invoicing service**.

### Create App registration

1. Create a self-signed certificate for service to service authentication by using a PowerShell script.
	
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
5. Create an app registration for **SDI Proxy service**.
    1. Go to **App registrations** and create a new registration with the following parameters:
	
        - **Name**: **SDI Proxy Client**
        - **Account type**: Accounts in this organizational directory only (single tenant)
		
    	![Create Azure App Registration](media/e-invoicing-ita-fatturapa-get-started-app-registration.png)

    2. Select **Register** and then select the app registration you created.
    3. Go to **API permissions** and select ***Grant admin consent***.
	
      ![Grant admin consent](media/e-invoicing-ita-fatturapa-get-started-app-registration-consent.png)
	
    4. Go to ***Certificates & secrets*** and upload the '.cer' certificate for service-to-service authentication.
	
        ![Upload certificate](media/e-invoicing-ita-fatturapa-get-started-app-upload-cert.png)

    5. Go to ***Enterprise applications*** and select the application you  created.
    6. Save the app's ***Application ID*** (Client ID) and ***Object ID***.
    7. Contact the Invoicing Service team to grant this app access to the service. by sending the folloiwng parameters to D365EInvoiceSupport@microsoft.com.
        - **AAD TenantID**  
        - **LCS Environment ID**
        - **Application ID** (Client ID)  
        - **Object ID**

6.  Add the ***Object ID*** to the applications list of your service environment in RCS, select **Save** and then select **Publish**.
    1. In RCS go to **Globalization features** > **Environments** > **Electronic Invoicing** > **Service environments**.
    2. Select your environment and add the application to the list.
	
        ![Add the application to the service environment](media/e-invoicing-ita-fatturapa-get-started-add-app-to-env.png)

    3. Select **Save** > **Publish**.

### Create an Azure virtual machine

1. In the [Azure portal](https://portal.azure.com), go to **Virtual machines** and select **Create new**.
2. Select your subscription and resource group. These are the same as where your Key Vault and Blob storage are located.
3. Select the region. Select the same region where your Finance environment is deployed.
4. Add the administrators user name and password and save them to the Key Vault.
5. Select Inbound ports: HTTPS (443), RPD (3389) (it\`s recommended to disable RDP (3389) when the system goes to production. You can enable it back when it is necessary to connect to the VM in case of troubleshooting).

  ![Create Azure Virtual Machine. Basics](media/e-invoicing-ita-fatturapa-get-started-create-vm-1.png)

6. In the **Disks** tab, select **Use managed disks**. Do not select **Ephemeral OS disk**.

    ![Create Azure Virtual Machine. Disks](media/e-invoicing-ita-fatturapa-get-started-create-vm-2.png)

7. On the **Networking** tab, select **Public IP** > **Create new**.

    ![Create Azure Virtual Machine. Networking](media/e-invoicing-ita-fatturapa-get-started-create-vm-3.png)
	
8. Select the **Standard** SKU and **Static** assignment.

    ![Create Azure Virtual Machine. Public IP](media/e-invoicing-ita-fatturapa-get-started-create-vm-4.png)

9. On the **Management** tab:	
    1. Unselect **Auto-shutdown** to disable it.
    2. Set **Manual** Guest OS updates and then set any other policies.
	
10. Review and create a Virtual machine.
11. In the new Virtual machine, go to **Identity** > **System assigned** > **Status** > **ON**.
12. Grant access to the Key Vault for the Virtual machine.
     1. In the Key Vault, go to **Access control (IAM)** > **Role assignments**.
     2.  Select **Add role assignment** and enter following parameters:
         1. Role: **Key Vault Secrets User**
         2. Assign access to: **Virtual machine**
         3. Subscription: your **Subscription**
         4. Select: your **Virtual machine**
     3. In the Key Vault, go to **Access policies** and select **Add Access Policy**.
         1. In the **Selected principal** field, select your **Virtual machine** .
         2. In the **Certificate** section, select **List** and **Get** permissions.
13. In the Virtual machine, go to **Monitoring** > **Insights**.
14. Select **Enable** and follow the Application Insights creation guide.
15. In the [Azure portal](https://portal.azure.com), go to **Public IP addresses** and select the IP address created in the Virtual machine.
16. Go to **Configuration** and set the DNS name.

### Proxy service environment preparation

Complete the following steps on the machine where the proxy service is hosted.
	
1. Connect to the Virtual machine by using Remote Desktop Connection.
2. Open the Local Machine Certificate snap-in. For information, see this [guide](/dotnet/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in).
3. Import the certificates, **caentrate.cer** for production and **CAEntratetest.cer** for test (Root CA certificate provided by authority) to [Trusted Root Certification Authorities] (/dotnet/framework/wcf/feature-details/working-with-certificates#certificate-stores). 
4. Open the **Turn on/off windows features** window, or go to **Server Manager** > **Add Roles and Features** for server OS, and turn on IIS features.

    ![Turn on Windows Features](media/e-invoicing-ita-fatturapa-get-started-turnon-features.png)
	
### Setup SDI Proxy service on IIS

1. In Dynamics Lifecycle Services (LCS), go to the **Shared asset library** and select **Data package** asset type.
2. Find and download **Electronic Invoicing Service Sdi Proxy** to the Virtual machine.
3.  Configure the service.
    2. Unzip downloaded **Electronic Invoicing Service Sdi Proxy** archive folder.
    2. In the **src\\FattureService** folder open **appsettings.json** and enter following parameters:
        - **KeyVaultUri**: The address of the key vault which stores the client certificate for invoicing service.
        - **TenantId**: The GUID of the customer's tenant.
        - **EnvironmentId**: The ID of the LCS environment.
        - **ClientId**: The AppId of intermediate services app registration in the customer`s tenant.
        - **ClientCertificateName**: The name of the S2S certificate in the Key Vault.
        - SecurityServiceClientOptions.**Endpoint**: The Url address of the security service.
        - SecurityServiceClientOptions.**Resource**: The scope to obtain the token.
        - InvoicingServiceClientOptions.**Endpoint**: The endpoint of the invoicing service. This should be the same as for RCS and Finance.
        - InvoicingServiceClientOptions.**ServiceEnvironmentId**: The name of the service environment. This should be the same as your Finance environment.
        - **NotificationsFolder**: Folder to save incoming notifications files.
    3.  In web.config:
        1. Change the following line by adding **proxy server certificate** thumbprint:
            \<serviceCertificate findValue="Put your cert thumbprint here" storeLocation="LocalMachine" storeName="My" x509FindType="FindByThumbprint" >.
        2. When the system goes to production the following values could be changed to reduce amount of logs collected and to save a disc space. In \<system.diagnostics>\<source> nodes, find the 'switchValue' parameter and change it to "Critical, Error". For more information, see [MS Service Trace Viewer](/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe).

4. Open IIS Manager, stay on the root node of left menu, and on right side, select **Server certificates**.

    ![Install the service certificate](media/e-invoicing-ita-fatturapa-get-started-proxy-cert-1.png)
,
5.  Open the menu and select **Import**.
6.  Specify path to the **proxy server** certificate. Rhis should be the pfx file.

    ![Install the service certificate. Selection](media/e-invoicing-ita-fatturapa-get-started-proxy-cert-2.png)

7. Right-click **Sites** > **Add website** and enter a site name.
8. In the **Physical path** field, point to the folder **src\\FattureService**.
9. In the **Binding type** field, select **https**.
10. Specify the **Host name**. Leave the default values in the **Ip Address** and **Port** fields.
11. Make sure that the **Require Server Name Indication** field isn't enabled because SDI doesn't support the technology.
12. In the **SSL certificate** field, select the proxy server certificate that you imported.
13. In the **Application pool** field, specify a pool for the site and remember it`s name (i.e. SdiAppPool).

    ![Configure IIS. Add Website](media/e-invoicing-ita-fatturapa-get-started-proxy-iis-setup-1.png)
	
14. After you create the web site, open **SSL Settings** menu.

    ![Configure IIS. Open SSL Settings](media/e-invoicing-ita-fatturapa-get-started-proxy-iis-setup-2.png)

15. Check **Require SSL** and select **Client certificates**: Require.

    ![Configure IIS. SSL Settings](media/e-invoicing-ita-fatturapa-get-started-proxy-iis-setup-3.png)

16. Open **Directory Browsing** and select **Enable**.
17. Open any internet browser and navigate to **serverDNS/TrasmissioneFatture.svc**. A standard window about service must be shown up:

    ![Open browser to check the service](media/e-invoicing-ita-fatturapa-get-started-proxy-open-browser.png)

18. Create folders to store logs and files in the following locations:
    - C:\\Logs\\: Store log files here. The files can be viewed by [MS Service Trace Viewer](/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe).
    - C:\\Files\\: Store all of the response files here.
19. In the **File explorer**, grant access to the **Logs** and **Files** folders for the **NETWORK SERVICE** and **IIS AppPool\\SdiAppPool** (or **IIS AppPool\\DefaultAppPool** for default).
    1. Open context menu on the folder and select **Properties** > **Security** > **Edit**.
    2. Add the users if they are not here
	
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
