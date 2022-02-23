---
# required metadata

title: Detect abandoned carts and send notifications to customers
description: This topic describes how to customize the Microsoft Dynamics 365 Commerce abandoned cart connector sample app to detect abandoned carts and send reminder email notifications to customers.
author: bicyclingfool
ms.date: 02/23/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: stuharg
ms.search.validFrom: 2017-06-20

---

# Detect abandoned carts and send notifications to customers

[!include [banner](../includes/banner.md)]

This topic describes how to customize the Microsoft Dynamics 365 Commerce abandoned cart connector sample app to detect abandoned carts and send reminder email notifications to customers.

The ability to recover revenue and retain customers through abandoned cart notifications is an important capability that Dynamics 365 Commerce supports. By customizing the Microsoft Dynamics 365 Commerce abandoned cart connector sample app, retailers can access shopping carts on Retail Server that have not been modified within a time window defined by the retailer. Those carts can then be retrieved, augmented with product and customer data, and passed on to a third-party email marketing provider where email notifications can be generated and sent to customers. 

The abandoned cart email notification that customers receive can contain the following information:

- Customer first name.
- Customer last name.
- Customer email.
- URL that returns the customer to their cart.
- Transaction currency.
- A list of products in the customer's cart. Each product includes the following information:
    - Product display name.
    - Product ID (used for assembling a URL to the product description page).
    - Product image that can be automatically resized to accommodate various viewport sizes.
    - Product image alt text.
    - Product unit price.

## Abandoned cart connector sample

Retrieving and sending abandoned cart information to a third-party email marketing provider is enabled through a connector model that Microsoft provides through the Retail software development kit (SDK). The connector handles communication with Retail Server, uses Azure KeyVault for security, handles scheduling of cart retrieval for a specified time window, and retrieves order and product data. The connector also provides a sample implementation for an integration with a third-party email marketing provider. The connector is built to communicate with [Emarsys](https://emarsys.com) out of the box, and can be easily customized to integrate with other solutions such as ConstantContact, MailChimp, and SendGrid. 

The following illustration shows a component diagram of the abandoned cart connector sample app.

![Component diagram of abandoned cart connector sample app](media/AbandonedCartConnector.png)

> [!NOTE]
> Microsoft does not provide an affordance for customers who wish to opt out of having their cart data passed to an email marketing provider, or who wish to have their data removed. If you plan to do business in regions that mandate these options for customers, you will need to provide the necessary infrastructure and customizations to collect and track this customer preference and suppress the passing of customer data to your email platform based on that preference. Additionally, you will need to define a process for purging customer data from your email marketing provider if requested by a customer. 

## Obtain the code sample

The abandoned cart connector sample app is included in the Retail SDK as of version 10.0.16. The code can be found under `\RetailSDK\Code\SampleExtensions\RetailServer\Extensions.AbandonedCartSample`. For more infomation about the Retail SDK and where to obtain it, see [Retail software development kit (SDK)](retail-sdk/retail-sdk-overview.md).  

> [!NOTE] 
> Although the sample code was first made available in version 10.0.16 builds, it is compatible with Retail Server builds starting with version 10.0.13. 

## Prerequisites and dependencies

Before you can deploy and configure the abandoned cart connector sample code, the following prerequisites must be met.

### Dynamics 365 Commerce access

In order to configure and deploy the abandoned cart connector app, you will need access to the following Dynamics 365 Commerce resources:

- Administrator access to Dynamics 365 Commerce headquarters for your environment.
- Access to the Microsoft LifeCycle Services (LCS) project for your environment.

### Azure Cosmos DB

The abandoned cart connector app uses Azure Cosmos DB to track the IDs and timestamps of carts that have previously been retrieved. You may choose to use Azure Cosmos DB to persist these data, or you can customize the code sample to integrate with another data storage option. For more information about Azure Cosmos DB, see [Welcome to Azure Cosmos DB](/azure/cosmos-db/introduction).

If you use Azure Cosmos DB, the following prerequisites must be met before you can run this sample. 

- You must have an active Azure Cosmos DB account. If you don't have an account, see [Create a database account](/azure/cosmos-db/create-sql-api-dotnet#create-a-database-account).
- You need the **URI** and **PRIMARY KEY** (or **SECONDARY KEY**) values retrieved from the **Keys** blade of your Azure Cosmos DB account in the Azure portal. For more information on obtaining endpoint and key information for your Azure Cosmos DB account, see [View, copy, and regenerate access keys and passwords](/azure/cosmos-db/manage-account#keys).

### Azure Key Vault

The abandoned cart connector app uses Azure Key Vault to store the names and secrets of various components that require secure access.

To set up an Azure Key Vault, follow these steps.

1. Follow the instructions in [Manage Key Vault in Azure Stack Hub using the portal](/azure-stack/user/azure-stack-key-vault-manage-portal?view=azs-2002&preserve-view=true).
2. Create secrets for:
   1. Emarsys API user name and API secret.
   2. Abandoned cart application ID and secret. 

The abandoned cart connector sample code uses Azure default credentials to access Azure Key Vault. You must provide "List" and "Read" permissions to the identity you plan to use for accessing Key Vault. 

For more information about Azure default credentials, see [DefaultAzureCredential Class]([/dotnet/api/azure.identity.defaultazurecredential?view=azure-dotnet](/dotnet/api/azure.identity.defaultazurecredential).

## Create an abandoned cart connector sample app application ID for the Azure AD tenant

You must create an abandoned cart connector sample app application ID for the Azure AD tenant. For instructions on creating an application ID for the abandoned cart connector sample app, see [Use the portal to create an Azure AD application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal).

## Add the abandoned cart connector sample app application ID to the allow list for the Retail Server API

Next you must add the abandoned cart connector sample app application ID to the allow list for the Retail Server API. For instructions on adding an application ID to the allow list in Azure, see [Support for Service to Service authentication in Retail Server](https://community.dynamics.com/ax/b/axforretail/posts/support-for-service-to-service-authentication-in-retail-server). 

## Configure the abandoned cart connector sample app

To configure the abandoned cart connector sample app you modify the **appSettings.json** configuration file located at the root of the **AbandonedCartDetectionSample** directory. The following tables contain the configuration file properties and their descriptions.

### KeyVaultOptions

| **Property** | **Description**                                                  |
| ------------ | ------------------------------------------------------------ |
| KeyVaultURI  | The DNS Name of the key vault you're using on https://portal.azure.com. |

### RetailServerClientOptions

| **Property**                                  | **Description**                                                  |
| --------------------------------------------- | ------------------------------------------------------------ |
| TenantId                                      | The Azure AD tenant ID for your Azure tenant.      |
| RetailServerAudienceId                        | The Retail Server audience ID, which can be left as is.                                            |
| AppIdKeyVaultSecretName                       | Name of the secret you created for the abandoned cart connector sample app application ID. |
| AppSecretKeyVaultSecretName                   | Name of the secret that stores the app secret for the abandoned cart connector sample app application ID. |
| RetailServerUrl                               | URL of your Retail Server instance, which is found in LCS.   |
| OperatingUnitNumber                           | Operating Unit Number (OUN), which is found in Commerce headquarters. |
| IncludeAbandonedCartsModifiedSinceLastMinutes | Defines the beginning of the time window in minutes for the abandoned carts you want to retrieve. For example, setting the value to 120 will retrieve all carts that were last modified within 120 minutes of the current time, but not after the end of the time window defined in ExcludeAbandonedCartsModifiedSinceLastMinutes. |
| ExcludeAbandonedCartsModifiedSinceLastMinutes | Defines the end of the time window in minutes for the abandoned carts you want to retrieve. For example, setting this value to 30 will retrieve all carts that were modified between 120 minutes ago and 30 minutes ago (when 120 is used as the value for the **IncludeAbandonedCartsModifiedSinceLastMinutes** property.) In practice, this property defines the length of time you want to wait before declaring a cart to be abandoned. |
| ReturnToCartUrl                               | The URL of the cart on your e-commerce site in the format used in the app.config file. |

### AzureCosmosOptions

The abandoned cart retrieval job status, cart IDs, and modified timestamps are stored in Azure Cosmos DB. By default, the configuration file is configured to point to the local emulator instance of Azure Cosmos DB. When deploying the connector to production, you will need to configure these settings to interact with the Azure Cosmos DB instance in your Azure subscription. For local or sandbox testing, you can use the [Azure Cosmos Emulator](/azure/cosmos-db/local-emulator).

| **Property** | **Description**                              |
| ------------ | ---------------------------------------- |
| EndPointUri  | End point URI provided by Azure or emulator.           |
| PrimaryKey   | Primary key provided by Azure or emulator.           |
| DatabaseId   | Database ID (Leave default value, or provide your own). |
| ContainerId  | Container ID (Leave default value, or provide your own). |

### EmarsysClientOptions

> [!NOTE] 
> If you are integrating with an email marketing provider other than Emarsys, you will extend the IEmailProvider interface as appropriate to communicate with that provider.

| **Property**                  | **Description**                                                  |
| ----------------------------- | ------------------------------------------------------------ |
| ApiUrl                        | https://api.emarsys.net/api/v2/event/{0}/trigger             |
| ExternalEventId               | The ID of the external event record that is created in Emarsys, which is located under **Trigger settings** in the campaign you created for sending abandoned cart mails. |
| ApiUserNameKeyVaultSecretName | Name of the key where the Emarsys API user name is stored.  |
| ApiSecretKeyVaultSecretName   | Name of the key for where the Emarsys API secret is stored.       |
| EmarsysContactKeyId           | The ID of the email column in the Emarsys contact DB. The default value is "3" and should not need to be changed. |

### MediaOptions

If you are using the e-commerce capabilities in Dynamics 365 Commerce, you have the option to use Commerce digital asset management to retrieve product images. To learn more about the image resizer capabilities in digital asset management, see the [ImageSettings viewport configuration](../e-commerce-extensibility/image-component.md#imagesettings-viewport-configuration) section of the [Image component](../e-commerce-extensibility/image-component.md) help topic. 


| **Property**                        | **Description**                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| ImageServerUrl                      | The root URL of your site's digital asset manager. This property value can be found in the **Media Server Base URL** property key in headquarters at **Retail and Commerce \> Channel setup \> Channel profiles**. |
| ImageViewPorts                      | Container node for individual viewport configurations. |
| ImageViewPorts/viewport             | Viewport definition. Use this property to specify the width ranges in pixels for this viewport. See the appSettings.json for example usage. |
| ImageViewPorts/imageWidth           | Image width in pixels for this viewport. |
| imageViewPorts/imageHeight           | Image height in pixels for this viewport. |
| imageViewPorts/useForDefaultImageTag | (true/false) Use the image dimensions defined by this viewport when the <picture /> HTML tag isn't supported for a web browser or email client |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
