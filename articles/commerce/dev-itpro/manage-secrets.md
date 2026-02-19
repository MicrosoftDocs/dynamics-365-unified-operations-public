---
title: Manage secrets for retail channels
description: Learn how to manage secrets when you're using an extension with channels that require access to secrets in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 02/18/2026
ms.topic: how-to
ms.author: shajain
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2019-09-17
ms.custom: 
  - bap-template
---

# Manage secrets for retail channels

[!include [banner](../includes/banner.md)]

This article explains how to manage secrets when you're using an extension with channels that require access to secrets in Microsoft Dynamics 365 Commerce.

Extensions can't deploy custom certificates in Commerce Scale Unit (CSU) or add thumbprints or secrets in web.config files. Use Azure Key Vault to manage secrets, as noted in this article.

## Key Vault setup

1. The extension developer follows these development steps:

    1. Create a test secret in Microsoft Azure Key Vault.
    1. Configure the head-office client to connect to Key Vault.
    1. On the **Key Vault Parameters** page (**Head Office \> Key Vault Parameters**), specify an extension key name for the Key Vault secret. Use the same name in the next step.
    1. Use the **GetUserDefinedSecretStringValueServiceRequest** Commerce Runtime (CRT) application programming interface (API) to get the secret. Pass a unique secret name to identify the secret.
    1. As part of the documentation of the extension setup, state the secret name that the extension references. Use a namespace for the secret name to help prevent conflicts with other extensions.

1. The IT pro or implementation partner follows these deployment and configuration steps:

    1. Apply the extension to the customer environment. For details, see [Apply updates to cloud environments](../../fin-ops-core/dev-itpro/deployment/apply-deployable-package-system.md).
    1. Upload the desired secrets to Key Vault (or enter them). For details, see [What is Azure Key Vault?](/azure/key-vault/key-vault-overview)
    1. On the **Key Vault Parameters** page (**Head Office \> Key Vault Parameters**), configure the head-office client to connect to Key Vault.
    1. On the **Key Vault Parameters** page, specify the extension secret name for the Key Vault secret in the head-office client.

## Consume the secret in the CRT extension

To consume the secret in the extension, add the following request and response classes.

| Request or response class                      | Parameters                   | Description |
|------------------------------------------------|------------------------------|-------------|
| `GetUserDefinedSecretStringValueServiceRequest`  | string **secretName**        | The request class that gets user-defined secrets from Headquarters. |
| `GetUserDefinedSecretStringValueServiceResponse` | string **SecretStringValue** | The response class that gets user-defined secrets from Headquarters. The response returns a **SecretStringValue** value. Extensions can cast this value to **X509Certificate2** or use it as a string value. |

To read the secret in the CRT extension, follow these steps:

### Cache the key vault in memory in CRT/Retail Server

Whenever you call CRT to read the Key Vault secret value, CRT calls Headquarters in real time to get the value. Headquarters then calls the key vault to get the value. Because multiple hops are involved in reading the value, the latency for the call is increased. Therefore, cache the Key Vault secret value in memory on the CRT/Retail Server side to help improve performance. If the value often changes in Key Vault, decide the correct strategy for cache expiration, based on your scenario.

1. Create a new CRT extension project (C\# class library project type). Use the sample templates from the Retail software development kit (SDK) (**RetailSDK\\SampleExtensions\\CommerceRuntime**).
1. In the CRT extension, create a new request and response, or add a pre-trigger or post-trigger for the existing CRT request, and then call it. In the following example, add a trigger for **SaveCartRequest**. It calls **GetUserDefinedSecretStringValueServiceRequest** to read the secret by passing the secret key that is configured in Headquarters. You don't have to write custom code to read the secret from Headquarters. Use the request and response to read the value.

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
               
                string result = null;
                   
                GetUserDefinedSecretStringValueServiceRequest keyVaultRequest = new GetUserDefinedSecretStringValueServiceRequest("SecretName");
                GetUserDefinedSecretStringValueServiceResponse keyVaultResponse = request.RequestContext.Execute<GetUserDefinedSecretStringValueServiceResponse>(keyVaultRequest);
                result = keyVaultResponse.SecretStringValue;

                 GetUserDefinedSecretCertificateServiceRequest getUserDefinedSecretCertificateServiceRequest = new GetUserDefinedSecretCertificateServiceRequest(profileId: null, secretName: "SecretName", thumbprint: null, expirationInterval: null);
                 GetUserDefinedSecretCertificateServiceResponse getUserDefinedSecretCertificateServiceResponse = request.RequestContext.Execute<GetUserDefinedSecretCertificateServiceResponse>(getUserDefinedSecretCertificateServiceRequest);

                X509Certificate2 Certificate = getUserDefinedSecretCertificateServiceResponse.Certificate;
               
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

1. Build the CRT extension project.
1. Copy the output class library, and paste it into **…\\RetailServer\\webroot\\bin\\Ext** for manual testing.
1. In the **CommerceRuntime.Ext.config** file, update the extension composition section with the custom library information. Here's an example.

    ```Xml
    <add source="assembly" value="your custom library name" />
    ```

## Credential rotation

When this approach is used for credential management, credential rotation is more streamlined. To update a secret, an IT administrator just has to update the secret in Key Vault. No change is required to the extension. 

## Offline support

To support offline credentials, your extension code must handle failover to offline when it can't access Key Vault credentials.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
