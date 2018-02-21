---
# required metadata

title: Service endpoints
description: This topic describes the service endpoints that are available.
author: Sunil-Garg
manager: AnnBe
ms.date: 11/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Service endpoints

[!include[banner](../includes/banner.md)]

This topic describes the service endpoints that are available in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. It also provides a comparison to the endpoints that are available in Microsoft Dynamics AX 2012. 

## List of services
The following table lists all the service endpoints, and compares the endpoints available for Finance and Operations, and AX 2012.

| Service endpoint            | AX 2012 | Finance and Operations     |
|-----------------------------|------------------|--------------------------------|
| Document services (AXDs)    | Yes              | No – Replaced by data entities |
| SOAP-based metadata service | Yes              | No – Replaced by REST metadata |
| SOAP-based query service    | Yes              | No – Replaced by OData         |
| OData query service         | Yes              | No – Replaced by OData         |
| SOAP-based custom service   | Yes              | Yes                            |
| JSON-based custom service   | No               | Yes                   |
| OData Service               | No               | Yes                   |
| REST Metadata Service       | No               | Yes                   |

This topic describes authentication for services, and the REST Metadata service. The following links provide detailed documentation for: 
- [Custom services](custom-services.md)
- [OData service](odata.md)

## Authentication
OData services, JSON-based custom services, and the REST metadata service support standard OAuth 2.0 authentication. 

We currently support both [Authorization Code Grant flow](https://msdn.microsoft.com/en-us/library/azure/dn645542.aspx) and [Service to service calls using client credentials (shared secret or certificate)](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-protocols-oauth-service-to-service). 

Two kinds of application are supported in Microsoft Azure Active Directory (AAD):

-   **Native client application** – This flow uses a user name and password for authentication and authorization.
-   **Web application (Confidential client)** – A confidential client is an application that can keep a client password confidential to the world. The authorization server assigned this client password to the client application. 

For more information, see: 
- [Authorize access to web applications using OAuth 2.0 and Azure Active Directory](https://msdn.microsoft.com/en-us/library/azure/dn645545.aspx)
- [Troubleshoot service authentication](troubleshoot-service-authentication.md)

The following illustration describes how authorization must be configured for Authorization code grant flow. 

![Authorization code grant flow](./media/services-authentication.png)


And below is the illustration describes how authorization works for Service to service calls using client credentials (shared secret or certificate).

![Service to service calls using clident credentials](./media/S2SAuth.jpg)

### Register a native application with AAD

Before any clients can communicate with the services, they must be registered in AAD. These steps will help you register an application with AAD. 

> [!NOTE]
> These steps don't have to be completed by all the people in your organization. Only one Azure Service Administrator user can add the application and share the client ID with the developers. **Prerequisite:** You must have an Azure subscription and admin access to Active Directory.

1. From the appropriate project in Microsoft Dynamics Lifecycle Services (LCS), open Azure portal.

    ![Open Azure portal](./media/odata_azure1.png)

2. In Azure portal, on the **Azure Active Directory** tab, select **Properties**, and make a note of the tenant ID in the **Directory ID** field. You will require the tenant ID later to retrieve an Azure Active Directory (Azure AD) authentication token.
3. On the **Azure Active Directory** tab, select **App registrations**, and then select **New application registration**.
4. Enter a name that identifies the external application that you're registering. For an application that will authenticate by using a shared secret, select **Web app / API**. In this context, the sign-on URL doesn't matter. Therefore, use **localhost**.
5. Select the new application, and copy the application ID. You will require the application ID later to request an Azure AD authentication token. Select **Required permissions**.
6. Select **Add**, and then select **Select an API**.
7. Select **Microsoft Dynamics ERP**.
8. Under **Delegated permissions**, you must select, at a minimum, the following options:

    - Access Dynamics AX Custom Service
    - Access Dynamics AX data
    - Access Dynamics AX online as organization users

9. Select **Done**.
10. Select **Keys**. In the dialog box that appears, enter a description, set the **Expires** value to **Never expires**, and then select **Save**.

    After you've saved the new key, a value appears in the **Value** column.

    > [!IMPORTANT]
    > Make sure that you copy this value, because you won't see it again, and you will require this secret key to complete your OAuth authentication and receive an Azure AD token.

### Register your external application in Finance and Operations

1. In Finance and Operations, go to **System administration** &gt; **Setup** &gt; **Azure Active Directory applications**.
2. Select **New**.
3. Fill in the fields for the new record:

    - In the **Client Id** field, enter the application ID that you registered in Azure AD.
    - In the **Name** field, enter a name for the application.
    - In the **User ID** field, select an appropriate service account user ID. For this example, we have selected the **Admin** user. However, as a better practice, you should provision a dedicated service account that has the correct permissions for the operations that must be performed.
    
    When you've finished, select **Save**.

You've now finished setting up the prerequisites. After the external application retrieves an Azure AD authentication token, it should now be able to use the token in an authorization HTTP header to make subsequent service calls via OData or SOAP, for example.


### Client sample code

The following is C# sample code for getting a token from AAD. In this flow, the user will be presented with a consent form (for cross-tenant application) and a sign-in form.

```
 UriBuilder uri = new UriBuilder ("https://login.windows.net/contoso2ax.onmicrosoft.com");
               
    AuthenticationContext authenticationContext = new AuthenticationContext(uri.ToString());

    //request token for the resource - which is the URI for your organization. NOTE: Important do not add a trailing slash at the end of the URI
    AuthenticationResult authenticationResult = authenticationContext.AcquireToken("https://axdynamics1001aos.cloud.dynamics.com", clientId, redirectURI);
                
    //this gets the authorization token, which needs to be passed in the Header of the HTTP Requests
    string authenticationHeader = authenticationResult.CreateAuthorizationHeader();
```

To pass the user name and password without showing a pop-up, you can use the following overload of **AcquireToken**.

```
    UserCredential userCred = new UserCredential (username, password);
    authenticationContext.AcquireToken("https://axdynamics1001aos.cloud.dynamics.com", clientId, userCred);
```

## REST Metadata Service
The REST metadata service is a read-only service. In other words, users can make only GET requests. The main purpose of this endpoint is to provide metadata information for elements. It is an OData implementation. 

This endpoint is hosted at `http://\[baseURI\]/Metadata`.

Currently, this endpoint provides metadata for the following elements:

-   **Labels** – Returns labels from the system. Labels have a dual pair key of language and ID, so that you can retrieve the value of the label. 

    **Example:** `https://[baseURI\]/metadata/Labels(Id='@SVC\_ODataLabelFile:Label1',Language='en-us')`

-   **Data entities** – Returns a JSON-formatted list of all the data entities in the system. 

    **Example:** `https://[baseURI\]/Metadata/DataEntities`
