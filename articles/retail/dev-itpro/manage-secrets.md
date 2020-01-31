---
# required metadata

title: Manage secrets for retail channels
description: This topic explains how to extend the channel database.
author: AamirAllaq
manager: AnnBe
ms.date: 09/17/2019
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
ms.custom: 83892
ms.search.region: Global
# ms.search.industry:
ms.author: aamiral
ms.search.validFrom: 2019-09-17
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Manage secrets for retail channels

[!include [banner](../includes/banner.md)]

This topic explains how to manage secrets when you're using an extension with channels that require access to secrets.

## Key Vault setup

1. The extension developer follows these development steps:

    1. Create a test secret in Microsoft Azure Key Vault.
    2. Configure the head-office client to connect to Key Vault.
    3. On the **Key Vault Parameters** page (**Head Office \> Key Vault Parameters**), specify an extension key name for the Key Vault secret. The same name must be used in the next step.
    4. Use the **GetUserDefinedSecretStringValueServiceRequest** Commerce Runtime (CRT) application programming interface (API) to get the secret. Pass a unique secret name to identify the secret.
    5. As part of the documentation of the extension setup, state the secret name that is referenced in the extension. We recommend that the extension developer use a namespace for the secret name, because this approach helps prevent conflicts with other extensions.

2. The IT pro or implementation partner follows these deployment and configuration steps:

    1. Apply the extension to the customer environment. For details, see [Apply updates to cloud environments](../../dev-itpro/deployment/apply-deployable-package-system.md).
    2. Upload the desired secrets to Key Vault (or enter them). For details, see [What is Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-overview)
    3. On the **Key Vault Parameters** page (**Head Office \> Key Vault Parameters**), configure the head-office client to connect to Key Vault.
    4. On the **Key Vault Parameters** page, specify the extension secret name for the Key Vault secret in the head-office client.

## Consume the secret in the CRT extension

To consume the secret in the extension, add the following request and response.

| Request/response                               | Parameters                   | Description |
|------------------------------------------------|------------------------------|-------------|
| GetUserDefinedSecretStringValueServiceRequest  | string **secretName**        | The request class that is used to get user-defined secrets from Headquarters. |
| GetUserDefinedSecretStringValueServiceResponse | string **SecretStringValue** | The response class that is used to get user-defined secrets from Headquarters. The response returns a **SecretStringValue** value, and extensions can type-cast this value to **X509Certificate2** or use it as string value. |

To read the secret in the CRT extension, follow these steps.

1. Create a new CRT extension project (C\# class library project type). Use the sample templates from the Retail software development kit (SDK) (**RetailSDK\\SampleExtensions\\CommerceRuntime**).
2. In the CRT extension, you can create a new request/response, or you can add a pre-trigger or post-trigger for the existing CRT request, and then call it. In the following example, a trigger was added for **SaveCartRequest**. It calls **GetUserDefinedSecretStringValueServiceRequest** to read the secret by passing the secret key that is configured in Headquarters. You don't have to write custom code to read the secret from Headquarters. You can use the request and response to read the value.

    ```csharp
    public class CustomSaveCartTrigger : IRequestTrigger
    {
        /// <summary>
        /// Gets the list of supported request types.
        /// </summary>
        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                return new[]{ typeof(SaveCartRequest) };
            }
        }

        /// <summary>
        /// Pre trigger code.
        /// </summary>
        /// <param name="request">The request.</param>
        public void OnExecuting(Request request)
        {
            ThrowIf.Null(request, "request");
            Type requestedType = request.GetType();
            if (requestedType == typeof(SaveCartRequest))
            {
                // Sample code to get the secret in string format.
                var request = new GetUserDefinedSecretStringValueServiceRequest("SecretName");
                string response = request.RequestContext.Execute<GetUserDefinedSecretStringValueServiceResponse>(request).SecretStringValue;
                // Sample code to get the secret in X509Certificate2 format.
                var request = new GetUserDefinedSecretStringValueServiceRequest ();
                X509Certificate2 response = request.RequestContext.Execute<GetUserDefinedSecretStringValueServiceRequest>(request).Certificate;
                // custom code to additional processing with secrets.
            }
        }

        /// <summary>
        /// Post trigger code.
        /// </summary>
        /// <param name="request">The request.</param>
        /// <param name="response">The response.</param>

        public void OnExecuted(Request request, Response response)
        {
        }
    }
    ```

3. Build the CRT extension project.
4. Copy the output class library, and paste it into **…\\RetailServer\\webroot\\bin\\Ext** for manual testing.
5. In the **CommerceRuntime.Ext.config** file, update the extension composition section with the custom library information. Here is an example.

    ```Xml
    <add source="assembly" value="your custom library name" />
    ```

## Credential rotation

When this approach is used for credential management, credential rotation is more streamlined. To update a secret, an IT admin just has to update the secret in Key Vault. No change is required to the extension. After a secret is updated, the new value starts to be used when the cache expires.

## Offline support

Offline support for credentials requires that the extension code handle failover to offline when Key Vault credentials aren't available or accessible.
