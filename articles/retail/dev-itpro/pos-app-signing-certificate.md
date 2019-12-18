---
# required metadata

title: Sign MPOS with a code signing certificate
description: This topic explains how to sign MPOS with a code signing certificate.
author: mugunthanm
manager: AnnBe
ms.date: 11/21/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2019-09-2019
ms.dyn365.ops.version: AX 10.0.5

---

# Sign MPOS appx with a code signing certificate

[!include [banner](../includes/banner.md)]

To install Modern POS (MPOS) you must sign the MPOS app with a signing certificate from a trusted provider. To sign the MPOS app with a certificate, use one of these options in the **Retail SDK\\Build tool\\Customization.settings** file:

- Add the Secure file task part of Azure DevOps build steps and upload the certificate to secure the file task. Use the secure file task output path variable as a parameter in the Customization.settings file.

    > [!NOTE] 
    > The Secure File task doesn’t support a password protected certificate. You must remove the password before uploading this task. Because the certificate is uploaded to the secure file system task in Azure, you can remove the password only for this step. However, you should discuss removing the password with your security experts to determine if this is the correct action for your project. Don’t remove the certificate password for other scenarios.
- Use a certificate that is in the file system. To do this, download or generate a certificate and place it in the file system where the build is running. The Visual Studio Online agent or build user should have access to this path and file.
- Use thumbprint to look up in the certificate in the store and sign in with that certificate.

## Use a Secure File task for Universal Windows Platform app signing

Using a Secure File task is the recommended approach for Universal Windows Platform (UWP) app signing. For more information about package signing, see [Configure package signing](https://docs.microsoft.com/windows/uwp/packaging/auto-build-package-uwp-apps#configure-package-signing). This process is shown in the following image.

![MPOS app signing flow](media/POSSigningFlow.png)

> [!NOTE] 
> Currently the OOB packaging supports signing only the appx file, the different self-service installers like MPOIS, RSSU, and HWS are not signed by this process. You need to manually sign it using SignTool or other signing tools.

## Steps to configure the certificate for signing

### Certificate in the file system/secure location

Download the [DownloadFile task](https://docs.microsoft.com/visualstudio/msbuild/downloadfile-task?view=vs-2019) and add it as the first step in the build process. The advantage of using the Secure File task is that the file is encrypted and placed in the disk during build no matter if the build pipeline succeeds, fails, or is canceled. The file is deleted from the download location after the build process is completed.

1. Download and add the Secure File task as the first step in the Azure DevOps build pipeline. You can download the Secure File task from [DownloadFile](https://marketplace.visualstudio.com/items?itemName=automagically.DownloadFile).
2. Upload the certificate to the Secure File task and set the Reference name under Output Variables, as shown in the following image.
    > [!div class="mx-imgBorder"]
    > ![Secure file task](media/SecureFile.png)
3. Create a new variable in the Azure DevOps pipeline by clicking **New Variable** under the **Variables** tab.
4. Provide a name for the variable in the value field **$(MySigningCert.secureFilePath)**, for example, **CertFile**.
5. Save the variable.
6. Open the **Customization.settings** file from **RetailSDK\\BuildTools** and update the **ModernPOSPackageCertificateKeyFile** with the variable name created in the Azure DevOps pipeline (step 3). For example:
    ```Xml
    <ModernPOSPackageCertificateKeyFile Condition="'$(ModernPOSPackageCertificateKeyFile)' ==''">$(CertFile</ModernPOSPackageCertificateKeyFile>
    ```

## Download or generate a certificate to sign the MPOS app

If a downloaded or generated certificate is used to sign the MPOS app, then the update the **ModernPOSPackageCertificateKeyFile** node in the **BuildTools\\Customization.settings** file to point to the pfx file location (**$(SdkReferencesPath)\\appxsignkey.pfx**). For example:

<ModernPOSPackageCertificateKeyFile Condition="'$(ModernPOSPackageCertificateKeyFile)' ==''">$(SdkReferencesPath)\\appxsignkey.pfx</ModernPOSPackageCertificateKeyFile>

In this case, the certificate file name is **appxsignkey.pfx**, located in the **Retail SDK\\Reference** folder.

## Use thumbprint to sign the MPOS app

If you use thumbprint to sign the MPOS app, then install the certificate locally. Update the thumbprint value in the **ModernPOSPackageCertificateThumbprint** node in the **BuildTools\\Customization.settings** file.

This option will work if the build user is a local user. However if you are using the Azure DevOps/Visual Studio Online agents to generate the build, then the agent may not have permission to access the cert store to use the certificate for signing or the build machine will not have the certificate installed. In this case, the workaround is to change the build user to local user and install the certificate in the box. However, this option will not work if you don’t have admin access to the box.

> [!NOTE]
> If the .pfx file or Secure File task option is used to sign the app, then leave the **ModernPOSPackageCertificateThumbprint** node in the **Customization.settings** file empty. If the thumbprint option is used, then leave **ModernPOSPackageCertificateKeyFile** empty. If both the values are updated, then the build will fail.
