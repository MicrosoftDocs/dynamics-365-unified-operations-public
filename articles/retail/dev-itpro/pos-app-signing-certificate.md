---
# required metadata

title: Sign MPOS with a code signing certificate
description: This topic explains how to sign MPOS with code signing certificate.
author: mugunthanm
manager: AnnBe
ms.date: 09/26/2019
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

# Sign MPOS with a code signing certificate

[!include [banner](../includes/banner.md)]

To install Modern POS (MPOS) in Windows you must sign the MPOS app with a signing certificate from a trusted provider. To sign the MPOS app with a certificate, there are these options in the **Retail SDK\\Build tool\\Customization.settings** file:

- Add the Secure file task part of Azure DevOps build steps and upload the certificate to secure the file task and use the secure file task output path variable as parameter in the Customization.settings file.
    > [!NOTE] 
    > The Secure file task doesn’t support password protected certificate. You must remove the password before uploading to this task. Because the certificate is uploaded to the secure file system task in Microsoft Azure, it's okay to remove the password only for this step. You must discuss removing the password with your security experts to determine if this is the correct action for your project. The certificate uploaded to the build task can be accessed only by the build pipeline during the build flow and no other process can access it. With secure file task, the additional layer of password security is not required during the build signing process. Do not remove the certificate password for other scenarios.
- Use a certificate placed in the file system: You download or generate a certificate and place it in the file system where the build is running. The VSO agent or build user should have access to this path and file.
- Use thumbprint to look up in the certificate in the store and sign with that certificate.

## Using a Secure File task is the recommended approach for UWP app signing

For information on package signing, see [Configure package signing](https://docs.microsoft.com/en-us/windows/uwp/packaging/auto-build-package-uwp-apps#configure-package-signing). The process is shown in the following image:

![MPOS app signing flow](media/POSSigningFlow.png)

## Steps to configure the certificate for signing

### Certificate in the file system/secure location:

Download the [Download File task](https://docs.microsoft.com/en-us/visualstudio/msbuild/downloadfile-task?view=vs-2019) and add it as first step in the build process. The advantage of using the Secure File task is the file is encrypted and placed in the disk during build and no matter whether the build pipelines succeeds, fails, or canceled, the file is deleted from its download location after the build process is completed.

1. Download and add the Secure File task as first step in the Azure DevOps build pipeline. You can download the secure file task from [DownloadFile](https://marketplace.visualstudio.com/items?itemName=automagically.DownloadFile).
2. Upload the certificate to the Secure File task and set the Reference name under Output Variables, as shown in the following image.
    > [!div class="mx-imgBorder"]
    > ![Secure file task](media/SecureFile.png)
3. Create a new variable in the Azure DevOps pipeline by clicking the **New Variable** button under the **Variables** tab.
4. Provide a name for the variable, for example, **CertFile**, in the value field **$(MySigningCert.secureFilePath)**.
5. Save the variable.
6. Open the **Customization.settings** file from the **RetailSDK\\BuildTools** and update the **ModernPOSPackageCertificateKeyFile** with variable name created in the Azure DevOps pipeline (Step 3). For example:
    ```Xml
    <ModernPOSPackageCertificateKeyFile Condition="'$(ModernPOSPackageCertificateKeyFile)' ==''">$(CertFile</ModernPOSPackageCertificateKeyFile>
    ```

## Downloaded or generated certificate to sign the MPOS app

If a downloaded or generated certificate is used to sign the MPOS app then the update the **ModernPOSPackageCertificateKeyFile** node in the **BuildTools\\Customization.settings** file to point to the pfx file location (**$(SdkReferencesPath)\\appxsignkey.pfx**). For example:

<ModernPOSPackageCertificateKeyFile Condition="'$(ModernPOSPackageCertificateKeyFile)' ==''">$(SdkReferencesPath)\\appxsignkey.pfx</ModernPOSPackageCertificateKeyFile>

In this case the certificate file name is **appxsignkey.pfx** and it's placed in the **Retail SDK\\Reference** folder.

## Thumbprint to sign the MPOS app

If you use a thumbprint to sign the MPOS app then install the certificate locally and then update the thumbprint value in the **ModernPOSPackageCertificateThumbprint** node in the **BuildTools\\Customization.settings** file.

This option will work fine if the build user is a local user but if you are using the Azure DevOps/VSO agents to generate the build then the agent may not have permission to access the cert store to use the certificate for signing or the build machine will not have the certificate installed. The workaround in this case is change the build user to local user and install the certificate in the box but this option will not work well if you don’t have admin access to the box.

> [!NOTE]
> If the .pfx file or Secure File task option is used to sign the app then leave the **ModernPOSPackageCertificateThumbprint** node in the **Customization.settings** file empty and if thumbprint option is used then leave the **ModernPOSPackageCertificateKeyFile** empty. If both the values are updated, then the build will fail.
