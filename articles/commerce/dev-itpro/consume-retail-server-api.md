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
ms.search.scope: Operations, Retail
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

This topic describes how to consume the Retail Server (RS) APIs in external application. Retail Server exposes the OData web endpoint for external application to consume the APIs. Retail Server hosts the Commerce Runtime (CRT) business logic and exposes it as OData endpoints, called the RS APIs.

External applications can consume the OData service through https. RS provides multiple options to consume the APIs:

- Retail server proxy – a strongly-typed way to consume the APIs. There are multiple types of proxies exposed for different application types:

    - C\# proxy – The C\# binary (class library) can be consumed by server-side and native applications to access the APIs and other entities.
    - TypeScript proxy - The .ts proxy file can be consumed by client applications to access the APIs and other entities.

- OData client – The APIs can be also consumed from OData clients, Postman, or by generating and HTTPS request to the Retail Server URL.

To browse the metadata, open the Retail Server URL in the following format in a web browser. The result is a list of all the RS APIs and input and output parameters.

```rest
https://RS-URL/Commerce/$metadata
```

## Security and authentication required to consume APIs

Access to each of the APIs is natively restricted according to the following roles:

- Employee – Access to APIs associated with this role requires point of sale (POS) device activation (a device token) and an authenticated employee.
- Customer – Access to APIs associated with this role requires an authenticated customer. E-Commerce sites generally use these APIs for operations such as retrieving order history and changing customer details.
- Application – Access to APIs associated with this role requires application-level authentication, such as Azure Active Directory (Azure AD) service-to-service authentication.
- Anonymous – APIs associated with this role are primarily used by e-Commerce sites without user authentication.
- Customized APIs – Access to APIs associated with this role can be restricted using methods such as POS device activation, customer authentication, and anonymous authentication.

External application integration would need only **Application** authentication flow to access the APIs. E-commerce application integration would need **Customer** authentication.

In this topic, we will focus on how to setup **Application** authentication flows and accessing the APIs with **Application** authentication context.

Before accessing the APIs from the external application, the external application must be registered in Azure App registration and registered application details must be added in the headquarters.

For more information about authentication flows, see [Dynamics 365 Commerce authentication flows](../arch-auth-flow.md).

## Register the application in Azure App registrations

Registering your application establishes a trust relationship between your app and the Microsoft identity platform. The trust is unidirectional: your app trusts the Microsoft identity platform, and not the other way around. Follow these steps to create the app registration:

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. If you have access to multiple tenants, use the **Directory + subscription** filter in the top menu to select the tenant in which you want to register an application.
3. Search for and select **Azure Active Directory**.
4. Under **Manage**, select **App registrations**, then **New registration**.
5. Enter a **Name** for your application. Users of your app might see this name, and you can change it later.
6. Specify who can use this application as **Accounts in this organizational directory only (Microsoft only - Single tenant)**.
7. In the **Redirect URI** option, leave the default value, don’t change anything.
8. Select **Register** to complete the initial app registration.

When registration completes, the Azure portal displays the app registration's **Overview** pane, which includes its **Application (client) ID**. Also referred to as just **client ID**, this value uniquely identifies your application in the Microsoft identity platform.

### Add a client secret

The client secret, known also as an *application password*, is a string value your app can use in place of a certificate to identity itself.

1. Select your application in **App registrations** in the Azure portal.
2. Select **Certificates & secrets** &gt; **New client secret**.
3. Add a description for your client secret.
4. Select a duration.
5. Select **Add**.
6. **Record the secret's value** for use in your client application code - it's *never displayed again* after you leave this page.

## Register the app in the Finance and Operations app for Retail server to trust this app

1. In Headquarters, go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce shared parameters**.
2. Select **Identity providers**.
3. On the **Identity providers** FastTab, select the provider that begins with `HTTPS://sts.windows.net/`. The values on the **Relying parties** FastTab are set, based on your selection.
4. On the **Relying parties** FastTab, select **Add**. Enter the client ID that is generated during the App registration in Azure. Set the **Type** field to **Confidential** and the **UserType** field to **Application**. Then, on the Action Pane, select **Save**.
5. Select the new relying party, and then, on the **Server resource IDs** FastTab, select **Add**. In the **Server Resource ID** column, enter Retail server URL.
6. On the Action Pane, select **Save**.
7. Navigate to **Retail and commerce** &gt; **Retail and commerce IT** &gt; **Distribution Schedule** and run CDX Job **1110**.

## Access the APIs using Postman

There are several third-party tools that allow you to authenticate to Azure Service and compose and send Web API requests and view responses. Postman is one of the most popular. [Download and install the postman client tool.](https://www.postman.com/)

For this sample, let's access the **GetOrderHistory** API. This API retrieves the order history for a particular customer. The **GetOrderHistory** API can be accessed only with the **Employee**, **Customer** or **Application** authorization context. Since our application will have the **Application** authorization context, it will be able to access the **GetOrderHistory** API and get the customer order history.

To access the API, first generate the authorization token and then access the API with that authorization token.

For the full list of APIS, check this doc: [Commerce Scale Unit customer and consumer APIs](retail-server-customer-consumer-api.md)

### Generate authorization token with Postman

1. Create a new Get request in postman with the below Request URL and Body parameters:

    ```rest
    https://login.microsoftonline.com/{tenant-id}/oauth2/token
    ```

    The **tenant-id** can be obtained from your Azure app registration overview page. The **tenant-id** is next to the client ID.

    Body parameters

    | Key            | Value                                                         |
    |----------------|---------------------------------------------------------------|
    | grant\_type    | client\_credentials                                           |
    | client\_id     | The client ID generated during the Azure app registration     |
    | client\_secret | The client secret generated during the Azure app registration |
    | resource       | Retail server URL                                             |

2. After the request runs, the **access\_token** will be generated in the response body. Copy this token value. You will use the token to connect to the retail server.

### GetOrderHistory using the Postman

1. Create a new POST request in Postman with this request URL, parameters, and headers:

    ```rest
    <https://Retail>serverurl/Commerce/Customers('2001')/GetOrderHistory
    ```

    Replace **2001** with your customer ID.

    Parameters

    | Key         | Value |
    |-------------|-------|
    | $top        | 10    |
    | api-version | 7.3   |

    Headers parameters**

    | Key           | Value                                                             |
    |---------------|-------------------------------------------------------------------|
    | OUN           | Operating unit number (This retail channel operating unit number) |
    | authorization | id\_token { access\_token }                                       |

    For the **access_token**, copy and paste the **access_token** generated in the authorization request. Prefix it with **id_token**.

2. After this request runs, the response body will contain the customer order history.

## Access the RS APIs using a console application

1. Create a new Console application using Visual Studio 2017.

2. In the **app.config** file, include the below configuration:

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

### Update the configuration settings with actual vales

1. Add the following NuGet packages using the NuGet package manager for the project.

    + Microsoft.IdentityModel.Clients.ActiveDirectory**
    + **Microsoft.Dynamics.Commerce.RetailProxy**.

    The **Microsoft.Dynamics.Commerce.RetailProxy** NuGet package can be added from the **RetailSDK\\pkgs** folder. In the NuGet manager, add a local repository for the **RetailSDK\\pkgs** folder.

2. Add the following variables to the **Program.cs** file:

    ```C#
    private static string clientId;
    private static string clientSecret;
    private static Uri retailServerUrl;
    private static string resource;
    private static string operatingUnitNumber;
    private static Uri authority;
    ```

3. In the **Program.cs** file, add **GetConfiguration** method to read the app settings.

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

4. In the **Program.cs** file, add the **CreateManagerFactory** method to get the access token:

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

6. In the **main** method call the **GetOrderHistory** method to read the records.

    ```C#
    static void Main(string[] args)
    {
        GetConfiguration();
        Microsoft.Dynamics.Commerce.RetailProxy.PagedResult<SalesOrder> orderHistory = Task.Run(async () => await GetOrderHistory("2001")).Result;
        Console.WriteLine(orderHistory.FirstOrDefault<SalesOrder>().Id);
    }
    ```
