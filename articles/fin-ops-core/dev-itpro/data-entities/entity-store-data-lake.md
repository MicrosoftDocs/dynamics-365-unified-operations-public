---
title: Make Entity store available as a Data Lake
description: Learn how to make Entity store available as a Microsoft Azure Data Lake, including learning how to create storage accounts and Key Vaults.
author: MilindaV2
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.assetid: 
ms.search.region: Global
ms.search.validFrom: 2018-12-03
ms.search.form:
ms.dyn365.ops.version: Platform Update 23
---

# Make Entity store available as a Data Lake

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This feature is currently in public preview. This feature includes the following components:
>
> - **Automated Entity store refresh** - Available in Platform update 23.
> - **Entity store data in Microsoft Azure Data Lake (full push)** - Available in Platform update 26.
> - **DataFlows for Entity store schemas on PowerBI.com** - Available in a future platform update.
> - **Entity store data in Azure Data Lake (trickle feed)** - Available in Platform update 28.
> - **Extend analytical workspaces by using PowerBI.com** - Available in a future platform update.

## Automated Entity store refresh

You need to enable automated Entity store refresh before enabling Data Lake integration.

1. Go to **System administration** > **Set up** > **Entity store**.

    On the **Entity store** page, a message indicates that you can switch to the **Automated Entity store refresh** option. This option is managed by the system. An admin doesn't have to schedule or monitor the Entity store refresh.

1. Select **Switch now**.

    > [!IMPORTANT]
    > This action isn't reversible. After you switch to the **Automated Entity store refresh** option, you can't revert to the old user interface (UI) experience.

1. Select **Yes** to continue.

You now see the new experience.

:::image type="content" source="./media/entity-store-data-lake-03.png" alt-text="Screenshot of the new Entity store user interface experience.":::

After the new experience is turned on, you can define the refresh for each aggregate measurement. The following refresh options are available:

- Every hour
- Twice a day
- Once a day
- Once a week

In addition, an admin can refresh any aggregate measurement on demand by selecting the **Refresh** button. Additional options are added in future platform updates. These options include options for real-time refresh.

> [!IMPORTANT]
> When you enable the automated refresh, the system might disable refresh of aggregate measurements in some cases. Revisit aggregate measurements and validate that the system applied appropriate refresh intervals.
>

## Entity store data in Azure Data Lake (full push and trickle feed)

> [!IMPORTANT]
> This feature is currently in public preview. Don't enable this feature in production environments.

When you turn on this feature, Entity store data isn't populated in the relational Entity store database in the Microsoft subscription. Instead, it's populated in an Azure Data Lake Storage Gen2 account in your own subscription. You can use the full capabilities of PowerBI.com and other Azure tools to work with Entity store.

Before you start, you must complete these tasks in the Azure portal.

1. **Create storage accounts.** Provision a storage account in the same data center where your environment is provisioned. Make a note of the connection string for the storage account, because you have to provide it later.
1. **Create a Key Vault and a secret.** Provision Azure Key Vault in your own subscription. You need the Domain Name System (DNS) name of the Key Vault entry that you created. Also add a secret to Key Vault. As the value, specify the connection string that you made a note of in the previous task. Make a note of the name of the secret, because you have to provide it later.
1. **Register the app.** Create a Microsoft Entra application, and grant application programming interface (API) access to Key vault. Make a note of the application ID and its application key (secret), because you have to provide them later.
1. **Add a service principal to Key Vault.** In Key Vault, use the **Access policies** option to grant the Microsoft Entra application **Get** and **List** permissions. In this way, the application have access to the secrets in Key Vault.

The following sections describe each task in more detail.

### Create storage accounts

1. In the Azure portal, create a new storage account.
1. In the **Create storage account** dialog box, provide values for the following parameter fields:

    - **Location:** Select the data center where your environment is located. If you select a data center in a different Azure region, you incur additional data movement costs. If your Microsoft Power BI and your data warehouse are in different regions, you can use replication to move storage between regions.
    - **Performance:** Select **Standard**.
    - **Account kind:** Select **StorageV2**.

1. In the **Advanced options** dialog box, you see the **Data Lake storage Gen2** option. Select **Enable** under the Hierarchical namespaces feature. If you disable this option, you can't consume data written by finance and operations apps by using services such as Power BI data flows.
1. Select **Review and create**. When the deployment is completed, the new resource is shown in the Azure portal.
1. Select the resource, and then select **Security + networking** \> **Access keys**.
1. Make a note of the connection string value, because you have to provide it later.

### Create a Key Vault and a secret

1. In the Azure portal, create a new Key Vault.
1. In the **Create key vault** dialog box, in the **Location** field, select the data center where your environment is located.
1. After Key Vault is created, select it in the list, and then select **Secrets**.
1. Select **Generate/Import**.
1. In the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
1. Enter a name for the secret. Make a note of the name, because you need to provide it later.
1. In the value field, enter the connection string that you obtained from the storage account in the previous procedure.
1. Select **Enabled**, and then select **Create**. The secret is created and added to Key Vault.

### Register the app

1. In the Azure portal, select **Microsoft Entra**, and then select **App registrations**.
1. Select **New registration** at the top of the menu, and enter the following information:

    - **Name** - Enter a friendly name for the app.
    - Select **Accounts in this Organizational directory only** unless your storage account and your Dynamics environment are in different Microsoft Entra domains.

1. After the application is created, select **API permissions**.
1. In the dialog box that appears, select **Add a permission**.
1. You see a dialog box with a list of APIs. In the list, select **Azure Key Vault**.
1. Select the **Delegated permissions** box, select **user_impersonation**, and then select **Add permissions** to save your changes.
1. Select the **Certificates & secrets** menu on the left navigation pane, and then select **New client secret**.
1. In the **Description** field, enter a name and choose an expiry period. Select **Add**.
1. A secret is generated and shown in the **Value** field.
1. Immediately copy the secret to the clipboard, because it disappears within one or two minutes. You need to provide this key to the application later.

### Add a service principal to Key Vault

1. In the Azure portal, open the Key Vault that you created earlier.
1. Select **Access policies**, and then select **Add** to create a new access policy.
1. In the **Select principal** field, select the name of the application that you previously registered.
1. In the **Key permissions** field, select **Get** and **List** permissions.
1. In the **Secret permissions** field, select **Get** and **List** permissions.

    :::image type="content" source="./media/entity-store-data-lake-05.png" alt-text="Screenshot of the Get and List permissions configuration in Key Vault access policies.":::

1. Select **Save**.

## Work in Entity store in a Data Lake

1. Go to **System administration** \> **Set up** \> **System parameters**.
1. On the **Data connections** tab, enter the following information that you made a note of earlier in this article:

    - **Application ID:** Enter the application ID of the Microsoft Entra application that you registered earlier.
    - **Application Secret:** Enter the application key (secret) for the Microsoft Entra application.
    - **DNS name:** Enter the DNS name of Key Vault.
    - **Secret name:** Enter the name of the secret that you added to Key Vault together with connection string information.

    :::image type="content" source="./media/entity-store-data-lake-04.png" alt-text="Screenshot of the Data connections tab on the System parameters page.":::

1. Select the **Test Azure Key Vault** and **Test Azure Storage** links to validate that system can access the configuration information that you provided.
1. Select the **Enable data connection** check box.

Entity store data now populates in the storage location that you provided, not in the relational Entity store database.

The aggregate measurements and refresh options that you select in the Entity store UI now apply to data that is copied to Data Lake.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
