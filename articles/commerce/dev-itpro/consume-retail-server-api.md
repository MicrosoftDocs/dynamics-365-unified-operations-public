---
title: Consume Retail Server APIs in external applications
description: Learn how to consume the Retail Server APIs in external applications.
author: josaw1
ms.date: 02/13/2026
ms.topic: how-to
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2019-08-2019
ms.custom: 
  - bap-template
---

# Consume Retail Server APIs in external applications

[!include [banner](../includes/banner.md)]

This article describes how to consume the Retail Server APIs in external applications. Retail Server exposes the Open Data Protocol (OData) web endpoint so that external applications can consume the APIs. Retail Server also hosts the Commerce runtime (CRT) business logic and exposes it as OData endpoints. These endpoints are known as the Retail Server APIs.

External applications can consume the OData service through HTTPS. Retail Server provides multiple options for consuming the APIs:

- **Retail server proxy** – A typed way to consume the APIs. Multiple types of proxies are available for different application types:

    - **C\# proxy** – Server-side and native applications can consume the C\# binary (class library) to access the APIs and other entities.
    - **TypeScript proxy** – Client applications can consume the .ts proxy file to access the APIs and other entities.

- **OData client** – You can also consume the APIs from OData clients, or by generating an HTTPS request to the Retail Server URL.

To browse the metadata, open the Retail Server URL in the following format in a web browser. The result is a list of all the Retail Server APIs, and input and output parameters.

```rest
https://RS-URL/Commerce/$metadata
```

## Security and authentication required to consume APIs

Each API natively restricts access according to the following roles:

- **Employee** – Access to APIs that are associated with this role requires point of sale (POS) device activation (a device token) and an authenticated employee.
- **Customer** – Access to APIs that are associated with this role requires an authenticated customer. E-commerce sites generally use these APIs for operations such as retrieving order history and changing customer details.
- **Application** – Access to APIs that are associated with this role requires application-level authentication, such as Microsoft Entra service-to-service authentication.
- **Anonymous** – APIs that are associated with this role are primarily used by e-Commerce sites without user authentication.
- **Customized APIs** – Access to APIs that are associated with this role can be restricted by using methods such as POS device activation, customer authentication, and anonymous authentication.

External application integration requires only the **Application** authentication flow to access the APIs. E-commerce application integration requires **Customer** authentication.

This article focuses on setting up **Application** authentication flows and accessing the APIs by using the **Application** authentication context.

Before you access the APIs from an external application, register the external application in Azure App registration. Add the details of the registered application in the Commerce Headquarters.

For more information about authentication flows, see [Dynamics 365 Commerce authentication flows](../arch-auth-flow.md).

## Register the application in Azure App registration

### App registration for the Retail Server

When you register an application, you create a trust relationship between your app and the Microsoft identity platform. The trust is one-way: your app trusts the Microsoft identity platform, but the platform doesn't trust your app. Follow these steps to create the app registration.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. If you have access to multiple tenants, use the **Directory + subscription** filter on the top menu to select the tenant where you want to register an application.
1. Search for and select **Microsoft Entra ID**.
1. Under **Manage**, select **App registrations**, and then select **New registration**.
1. Enter a name for your application. Users of your app might see this name, and you can change it later.
1. Specify who can use this application as **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
1. In the **Redirect URI** field, don't change the default value.
1. Select **Register** to complete the initial app registration.
1. Select **Expose an API** and then select **Add a scope**. Provide the **Scope** name, under **Consent** select **Admins and users** and provide the **Admin consent display** name and description.
1. Set the **State** to **Enabled**.
1. Select **Add scope** to complete the scope registration. 
1. After the scope is created, copy the Application ID URI, which begins with "api://…" to the clipboard. This value is the Server Resource ID that you use later.

### Create the app registration for the client

1. Follow steps 2-8 from the preceding procedure, making sure to provide a different name for the app registration.
1. Select **API permission**.
1. On the **Request API permissions** page, select **APIs my organization uses** and then search for the app that you created in steps 2-8.
1. Select the API and then check the permission. In the new window that opens, select **Add permissions**


When registration is complete, the Azure portal shows the **Overview** pane for the app registration. This pane includes the **Application (client) ID** field. The value of this field is known as the *application ID* or the *client ID*. It uniquely identifies your application in the Microsoft identity platform.

### Add a client secret

The client secret is also known as an *application password*. It's a string value that your app can use instead of a certificate to identify itself.

1. In the Azure portal, in **App registrations**, select your application (App registered for the client).
1. Select **Certificates & secrets** &gt; **New client secret**.
1. Add a description for your client secret.
1. Select a duration.
1. Select **Add**.
1. Record the secret's value so that you can use it in your client application code. 

## Register the app in the finance and operations app so that Retail Server trusts it

1. In Commerce Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
1. On the **Identity providers** FastTab, select the provider with type `Microsoft Entra ID`. The values on the **Relying parties** FastTab are set based on your selection.
1. On the **Relying parties** FastTab, select **Add**. Enter the client ID that was generated during the client app registration (not the headless Commerce app). Set the **Type** field to **Confidential** and the **UserType** field to **Application**.
1. On the action pane, select **Save**.
1. Select the new relying party, and then on the **Server resource IDs** FastTab, select **Add**. In the **Server Resource ID** column, enter the Application ID URI (which is the API URI generated during the Retail Server app registration).
1. On the action pane, select **Save**.
1. Go to **Retail and commerce** &gt; **Retail and commerce IT** &gt; **Distribution Schedule**, and run Commerce Data Exchange (CDX) job **1110**.

## Access the Retail Server APIs by using a console application

1. Use Visual Studio 2017 to create a console application.
1. In the **app.config** file, include the following configuration.

    ```xml
    <appSettings>
        <add key="aadClientId" value="client id generated during the client app registration in Azure" />
        <add key="aadClientSecret" value="client secret generated during the client app registration in Azure" />
        <add key="aadAuthority" value="https://sts.windows.net/tenant id/" />
        <add key="retailServerUrl" value="https://RetailserverURL/Commerce" /> 
        <add key="resource" value="api://2fxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" /> <!-- //Application ID URI generated during the Retail Server app registration -->
        <add key="operatingUnitNumber" value="OUN value" />
    </appSettings>
    ```

### Update the configuration settings with actual values

1. Use the NuGet package manager for the project to add the following NuGet packages:

    + Microsoft.Identity.Client
    + Microsoft.Dynamics.Commerce.RetailProxy

    Add the **Microsoft.Dynamics.Commerce.RetailProxy** NuGet package from the **RetailSDK\\pkgs** folder. In the NuGet manager, add a local repository for the **RetailSDK\\pkgs** folder.

1. Add the following variables in the **Program.cs** file.

    ```C#
    private static string clientId;
    private static string clientSecret;
    private static Uri retailServerUrl;
    private static string resource;
    private static string operatingUnitNumber;
    private static Uri authority;
    ```

1. Add the **GetConfiguration** method in the **Program.cs** file to read the app settings.

    ```C#
    private static void GetConfiguration()
    {
        clientId = ConfigurationManager.AppSettings["aadClientId"];
        clientSecret = ConfigurationManager.AppSettings["aadClientSecret"];
        authority = new Uri(ConfigurationManager.AppSettings["aadAuthority"]);
        retailServerUrl = new Uri(ConfigurationManager.AppSettings["retailServerUrl"]);
        operatingUnitNumber = ConfigurationManager.AppSettings["operatingUnitNumber"];
        resource = ConfigurationManager.AppSettings["resource"];
    }
    ```

1. Add the **CreateManagerFactory** method in the **Program.cs** file to get the access token.

    ```C#
    private static async Task<ManagerFactory> CreateManagerFactory()
    {
        Microsoft.Identity.Client.AuthenticationContext authenticationContext = new   Microsoft.Identity.Client.AuthenticationContext(authority.ToString(), false);
        AuthenticationResult authResult = null;
        authResult = await authenticationContext.AcquireTokenAsync(resource, new ClientCredential(clientId, clientSecret));

        ClientCredentialsToken clientCredentialsToken = new ClientCredentialsToken(authResult.AccessToken);
        RetailServerContext retailServerContext = RetailServerContext.Create(retailServerUrl, operatingUnitNumber, clientCredentialsToken);
        ManagerFactory factory = ManagerFactory.Create(retailServerContext);
        return  factory;
    }
    ```

1. Add the **GetOrderHistory** method to read the orders.

    ```C#
    private static async Task<Microsoft.Dynamics.Commerce.RetailProxy.PagedResult<SalesOrder>> GetOrderHistory(string customerId)
    {
        QueryResultSettings querySettings = new QueryResultSettings
        {
            Paging = new PagingInfo() { Top = 10, Skip = 10 }
        };

        ManagerFactory managerFactory = await CreateManagerFactory();
        ICustomerManager customerManage = managerFactory.GetManager<ICustomerManager>();
        return await customerManage.GetOrderHistory(customerId, querySettings);
    }
    ```

1. In the **main** method, call the **GetOrderHistory** method to read the records.

    ```C#
    static void Main(string[] args)
    {
        GetConfiguration();
        Microsoft.Dynamics.Commerce.RetailProxy.PagedResult<SalesOrder> orderHistory = Task.Run(async () => await GetOrderHistory("2001")).Result;
        Console.WriteLine(orderHistory.Results.GetEnumerator().Current.Id);
    }
    ```

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
