---
# required metadata

title: Consume Retail Server APIs in external applications
description: This topic describes how to consume the Retail Server APIs in external applications.
author: mugunthanm
manager: AnnBe
ms.date: 09/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2019-08-2019
ms.dyn365.ops.version: AX 10.0.12

---

# Consume Retail Server APIs in external applications

[!include [banner](../includes/banner.md)]

This topic describes how to consume the Retail Server APIs in external applications. Retail Server exposes the Open Data Protocol (OData) web endpoint so that external applications can consume the APIs. Retail Server also hosts the Commerce runtime (CRT) business logic and exposes it as OData endpoints. These endpoints are known as the Retail Server APIs.

External applications can consume the OData service through HTTPS. Retail Server provides multiple options for consuming the APIs:

- **Retail server proxy** – A strongly typed way to consume the APIs. There are multiple types of proxies that are exposed for different application types:

    - **C\# proxy** – Server-side and native applications can consume the C\# binary (class library) to access the APIs and other entities.
    - **TypeScript proxy** – Client applications can consume the .ts proxy file to access the APIs and other entities.

- **OData client** – The APIs can also be consumed from OData clients, from Postman, or by generating an HTTPS request to the Retail Server URL.

To browse the metadata, open the Retail Server URL in the following format in a web browser. The result is a list of all the Retail Server APIs, and input and output parameters.

```rest
https://RS-URL/Commerce/$metadata
```

## Security and authentication that are required to consume APIs

Access to each API is natively restricted according to the following roles:

- **Employee** – Access to APIs that are associated with this role requires point of sale (POS) device activation (a device token) and an authenticated employee.
- **Customer** – Access to APIs that are associated with this role requires an authenticated customer. E-Commerce sites generally use these APIs for operations such as retrieving order history and changing customer details.
- **Application** – Access to APIs that are associated with this role requires application-level authentication, such as Azure Active Directory (Azure AD) service-to-service authentication.
- **Anonymous** – APIs that are associated with this role are primarily used by e-Commerce sites without user authentication.
- **Customized APIs** – Access to APIs that are associated with this role can be restricted by using methods such as POS device activation, customer authentication, and anonymous authentication.

External application integration requires only the **Application** authentication flow to access the APIs. E-commerce application integration requires **Customer** authentication.

This topic is focused on setting up **Application** authentication flows and accessing the APIs by using the **Application** authentication context.

Before the APIs are accessed from an external application, the external application must be registered in Azure App registration, and details of the registered application must be added in the Commerce Headquarters.

For more information about authentication flows, see [Dynamics 365 Commerce authentication flows](../arch-auth-flow.md).

## Register the application in Azure App registration

Application registration establishes a trust relationship between your app and the Microsoft identity platform. The trust is unidirectional: your app trusts the Microsoft identity platform, not the other way around. Follow these steps to create the app registration.

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. If you have access to multiple tenants, use the **Directory + subscription** filter on the top menu to select the tenant that you want to register an application in.
3. Search for and select **Azure Active Directory**.
4. Under **Manage**, select **App registrations**, and then select **New registration**.
5. Enter a name for your application. Users of your app might see this name, and you can change it later.
6. Specify who can use this application as **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
7. In the **Redirect URI** field, leave the default value. Don't change anything.
8. Select **Register** to complete the initial app registration.

When registration is completed, the Azure portal shows the **Overview** pane for the app registration. This pane includes the **Application (client) ID** field. The value of this field is known as the *application ID* or the *client ID*. It uniquely identifies your application in the Microsoft identity platform.

### Add a client secret

The client secret is also known as an *application password*. It's a string value that your app can use instead of a certificate to identity itself.

1. In the Azure portal, in **App registrations**, select your application.
2. Select **Certificates & secrets** &gt; **New client secret**.
3. Add a description for your client secret.
4. Select a duration.
5. Select **Add**.
6. Be sure to record the secret's value so that you can use it in your client application code. **The secret's value is never displayed again after you leave this page.**

## Register the app in the Finance and Operations app so that Retail Server trusts it

1. In Commerce Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
2. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/`. The values on the **Relying parties** FastTab are set based on your selection.
3. On the **Relying parties** FastTab, select **Add**. Enter the client ID that was generated during the app registration in Azure. Set the **Type** field to **Confidential** and the **UserType** field to **Application**.
4. On the Action Pane, select **Save**.
5. Select the new relying party, and then, on the **Server resource IDs** FastTab, select **Add**. In the **Server Resource ID** column, enter the Retail Server URL.
6. On the Action Pane, select **Save**.
7. Go to **Retail and commerce** &gt; **Retail and commerce IT** &gt; **Distribution Schedule**, and run Commerce Data Exchange (CDX) job **1110**.

## Access the APIs by using Postman

Several third-party tools let you authenticate with Azure services, compose and send Web API requests, and view responses. Postman is one of the most popular tools. [Download and install the Postman client tool](https://www.postman.com/).

For this example, you will access the **GetOrderHistory** API. This API retrieves the order history for a specific customer. It can be accessed only by using the **Employee**, **Customer** or **Application** authorization context. Because your application has the **Application** authorization context, it can access the **GetOrderHistory** API and get the customer order history.

To access the API, you first generate the authorization token. You then use that authorization token to access the API.

For the full list of APIs, see [Commerce Scale Unit customer and consumer APIs](retail-server-customer-consumer-api.md).

### Generate an authorization token by using Postman

1. In Postman, create a GET request that has the following request URL and body parameters.

    **Request URL**

    ```rest
    https://login.microsoftonline.com/{tenant-id}/oauth2/token
    ```

    > [!NOTE]
    > You can get the tenant ID from the **Overview** pane for your Azure app registration. It's shown next to the client ID.

    **Body parameters**

    | Key            | Value                                                              |
    |----------------|--------------------------------------------------------------------|
    | grant\_type    | **client\_credentials**                                            |
    | client\_id     | The client ID that was generated during Azure app registration     |
    | client\_secret | The client secret that was generated during Azure app registration |
    | resource       | The Retail Server URL                                              |

2. After the request has finished running, the **access\_token** value will be generated in the response body. Copy this token value. You will use it to connect to the Retail Server.

### Get order history by using Postman

- In Postman, create a POST request that has the following request URL, parameters, and header parameters.

    **Request URL**

    ```rest
    <https://Retail>serverurl/Commerce/Customers('2001')/GetOrderHistory
    ```

    > [!NOTE]
    > Replace **2001** with your own customer ID.

    **Parameters**

    | Key         | Value |
    |-------------|-------|
    | $top        | 10    |
    | api-version | 7.3   |

    **Header parameters**

    | Key           | Value                                            |
    |---------------|--------------------------------------------------|
    | OUN           | The operating unit number of this retail channel |
    | authorization | **id\_token { access\_token }**                  |

    > [!NOTE]
    > For **access_token**, copy and paste the **access_token** value that was generated in the authorization request. Then prefix it with **id_token**.

After the request has finished running, the response body will contain the customer order history.

## Access the Retail Server APIs by using a console application

1. Use Visual Studio 2017 to create a console application.
2. In the **app.config** file, include the following configuration.

    ```xml
    <appSettings>
        <add key="aadClientId" value="client id generated during app registration in Azure" />
        <add key="aadClientSecret" value="client secret generated during app registration in Azure" />
        <add key="aadAuthority" value="https://sts.windows.net/tenant id/" />
        <add key="retailServerUrl" value="https://RetailserverURL/Commerce" />
        <add key="resource" value="https://REtailServerURL" />
        <add key="operatingUnitNumber" value="OUN value" />
    </appSettings>
    ```

### Update the configuration settings with actual values

1. Use the NuGet package manager for the project to add the following NuGet packages.

    + Microsoft.IdentityModel.Clients.ActiveDirectory
    + Microsoft.Dynamics.Commerce.RetailProxy

    The **Microsoft.Dynamics.Commerce.RetailProxy** NuGet package can be added from the **RetailSDK\\pkgs** folder. In the NuGet manager, add a local repository for the **RetailSDK\\pkgs** folder.

2. In the **Program.cs** file, add the following variables.

    ```C#
    private static string clientId;
    private static string clientSecret;
    private static Uri retailServerUrl;
    private static string resource;
    private static string operatingUnitNumber;
    private static Uri authority;
    ```

3. In the **Program.cs** file, add the **GetConfiguration** method to read the app settings.

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

4. In the **Program.cs** file, add the **CreateManagerFactory** method to get the access token.

    ```C#
    private static async Task<ManagerFactory> CreateManagerFactory()
    {
        Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext authenticationContext = new   Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext(authority.ToString(), false);
        AuthenticationResult authResult = null;
        authResult = await authenticationContext.AcquireTokenAsync(resource, new ClientCredential(clientId, clientSecret));

        ClientCredentialsToken clientCredentialsToken = new ClientCredentialsToken(authResult.AccessToken);
        RetailServerContext retailServerContext = RetailServerContext.Create(retailServerUrl, operatingUnitNumber, clientCredentialsToken);
        ManagerFactory factory = ManagerFactory.Create(retailServerContext);
        return factory;
    }
    ```

5. Add the **GetOrderHistory** method to read the orders.

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

6. In the **main** method, call the **GetOrderHistory** method to read the records.

    ```C#
    static void Main(string[] args)
    {
        GetConfiguration();
        Microsoft.Dynamics.Commerce.RetailProxy.PagedResult<SalesOrder> orderHistory = Task.Run(async () => await GetOrderHistory("2001")).Result;
        Console.WriteLine(orderHistory.FirstOrDefault<SalesOrder>().Id);
    }
    ```
