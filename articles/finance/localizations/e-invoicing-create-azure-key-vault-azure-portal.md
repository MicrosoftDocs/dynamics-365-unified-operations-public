---
# required metadata

title: Create Azure Key Vault in Azure portal
description: This topic provides overview of Azure Key Vault creation Electronic invoicing.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Create Azure Key Vault in Azure portal

[!include [banner](../includes/banner.md)]

All secrets and certificates used in Electronic invoicing service must be stored in customer's Azure Key Vault. This storage will help you to make sure that you don't operate with the secrets directly, and the secrets are stored securely. In the scenarios where you need to use digital signing, or secure connection to external Web services, you will set the reference to the Key Vault secrets and certificates, rather than use secrets and certificates directly.

  1. Create Azure Key Vault  in the tenant where RCS is installed to. You can refer to the instruction to create Azure Key Vault: https://docs.microsoft.com/en-us/azure/key-vault/general/quick-create-portal.
  2. Set up the access policy to grant Electronic invoicing the correct level of secure access to the secret you created. Go to **Settings** > **Access policies**, and select **Add Access Policy**.
  3. Set the **Secret permissions** for the **Get** and **List** operations.
  
    ![Add access policy page.](media/add-access-policy-page.png)

  4. Set the **Certificate permissions** for **Get** and **List** operations.
  5. In the **Select principal** field, select **None selected**.
  6. In the **Principal** dialog box, select the principal by adding **e-Invoicing Service**.
	
  > [!NOTE]
  > If you don't see e-Invoicing Service in the list of principals in your tenant, execute the following command in Azure portal: <p>`New-AzureADServicePrincipal -AppId "ecd93392-c922-4f48-9ddf-10741e4a9b65"`</p>


  7. Select **Add**, and then select **Save**.
  8. On the **Overview** page, copy the DNS name value for the Key Vault. This value will be used during setup of the service in RCS and will be referred as the Key Vault URI.
