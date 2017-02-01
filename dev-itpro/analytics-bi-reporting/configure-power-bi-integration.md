---
# required metadata

title: Configure Power BI integration for workspaces | Microsoft Docs
description: This tutorial describes the configuration that is required for a new Microsoft Dynamics 365 for Operations environment to support integration with PowerBI.com. This configuration enables workspaces to show the Power BI control and lets users pin visualizations to a workspace.
author: clwesene
manager: AnnBe
ms.date: 2015-12-14 17:08:48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: PowerBIConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 27661
ms.assetid: eaafa101-5016-4e97-b8fc-2cf58ce37853
ms.region: Global
# ms.industry: 
ms.author: cwesene

---

# Configure Power BI integration for workspaces

This tutorial describes the configuration that is required for a new Microsoft Dynamics 365 for Operations environment to support integration with PowerBI.com. This configuration enables workspaces to show the Power BI control and lets users pin visualizations to a workspace.

Microsoft Dynamics 365 for Operations supports Power BI visualizations that are pinned directly to workspaces. This functionality requires a one-time configuration for each tenant to help guarantee that Dynamics 365 for Operations and Power BI can communicate and authenticate correctly. \[caption id="attachment\_259704" align="alignnone" width="781"\][![PowerBI control in Reservation Management Workspace](./media/fleetws-1024x578.png)](./media/fleetws.png) Power BI control in the Reservation management workspace\[/caption\] Both Dynamics 365 for Operations and PowerBI.com are cloud-based services. In order for a Dynamics 365 for Operations workspace to display a Power BI tile, the Dynamics 365 for Operations server must contact the Power BI service on behalf of a user and must have a visualization drawn in the Dynamics 365 for Operations workspace. This flow between Dynamics 365 for Operations and the Power BI service is based on the OAuth 2.0 Authorization Code Grant Flow.

## The OAuth Authorization Code Grant Flow
This section describes the authorization flow between Dynamics 365 for Operations and the PowerBI.com service during authentication and when visualizations are presented to a user. The following diagram shows the authorization flow and is based on the assumption that you've completed the configuration that this article describes. [![OAuthFlow](./media/oauthflow.png)](./media/oauthflow.png)

1.  When a user visits a workspace in Dynamics 365 for Operations for the first time, the Power BI banner prompts the user to start the first-time connection. If the user agrees to start the first-time connection, an OAuth 2.0 Authorization Code Grant Flow is started.
2.  Dynamics 365 for Operations redirects the user agent to the Microsoft Azure Active Directory (AAD) authorization endpoint. The user is authenticated and consents, if consent is required. Because the user is running Dynamics 365 for Operations, he or she is already signed in to AAD. Therefore, the user doesn't have to enter his or her credentials again.
3.  The AAD authorization endpoint redirects the AAD agent back to the client application together with an authorization code. The user agent returns the authorization code to the client application’s redirect URL. The application redirect URL is a parameter that is maintained in your Power BI configuration, as described later in this article.
4.  Now that Dynamics 365 for Operations has an authorization code on behalf of the user, it requests an access token from the AAD token issuance endpoint. Dynamics 365 for Operations presents the authorization code to prove that the user has consented.
5.  The AAD token issuance endpoint returns an access token and a refresh token. Dynamics 365 for Operations must have the access tokento request a visualization from Power BI. Access tokens expire after a short time. The refresh token can be used to request a new token.
6.  Dynamics 365 for Operations uses the access token to authenticate to the Web API that is provided by Power BI. Dynamics 365 for Operations uses the Web API to request that Power BI visualizations be displayed on behalf of the user.
7.  After the client application is authenticated, the Power BI Web API returns the requested visualization to the user. Note that Power BI returns only the data that the user is allowed to see. Because the Power BI Web API detects that the user is connecting via Dynamics 365 for Operations, it can correctly resolve the user.
8.  The user sees Power BI visualizations in the Dynamics 365 for Operations workspace.

For subsequent visits, this entire flow doesn't have to occur. Because Dynamics 365 for Operations has the access token on behalf of the user, steps 1 through 4 don't have to be repeated.

## Prerequisites
-   At least one AAD account in your tenant must be registered with PowerBI.com.
    -   Follow the instructions at <https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-sign-up-for-power-bi-service/>.
    -   After you've created your AAD account, sign in to <https://app.powerbi.com>.
    -   At least one user must sign in to PowerBI.com before the configuration can be completed.
-   You must have AAD administrator privileges.
-   You must be assigned to the System Administrator role in Dynamics 365 for Operations.
-   You must be using the same tenant for both your deployment and the user logon. For example, if the environment was deployed under the contosoax7.onmicrosoft.com tenant, the user logon for both Dynamics 365 for Operations and Power BI should be in the format myname@contosoax7.onmicrosoft.com.

## Register your Dynamics 365 for Operations deployment as a web app in the Azure portal
The Power BI application programming interface (API) is available for consumption by any client or web application that is registered with AAD. Therefore, the first step is to register your Dynamics 365 for Operations deployment as a web app. To complete this step, you must have access to an AAD account that has administrator privileges for the tenant that Dynamics 365 for Operations was deployed for. For instructions about how to register your web app, see <https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-register-a-web-app/>. **Important:** Observe the following guidelines when you register your web app:

-   Use the following values when you create your web app:
    -   **Sign-in URL:** This URL is the same as your deployment URL, but **oauth** is added to the end. **Example:** http://contosoax7.cloud.dynamics.com/**oauth**
    -   **App ID URI:** This value is mandatory, but isn't required for the workspace integration. Make sure that this App ID URI is a mock URI like https://contosoAX, since using the URL of your deployment can cause sign-in issues in other AAD applications such as the Excel Add-in. **Example:** http://contosoax7testenv/
    -   **Reply URL:** This URL is the same as your deployment URL, but **oauth** is added to the end. **Example:** http://contosoax7.cloud.dynamics.com/**oauth**
-   If you have multiple deployments, you can use the same web app and add additional deployments. Add the URL of each deployment to the **Reply** **URL** list on the **Configuration** tab for your web app.
-   If you use the deployment URL as the **App ID URL** value, you will cause an error when authentication through Microsoft Power Query for Excel occurs.
-   Write down the **Client ID** and **Secret Key** values as they appear in the Azure portal, and keep this information in a safe place. You will have to enter these values on the Dynamics 365 for Operations **Power BI configuration** page later.
-   When you try to give permission to the Power BI service, if you don't see **Power BI Service** in the **Permissions to other applications** list, you must sign up for the Power BI service by using the account of a member of your tenant. To sign up for the Power BI service, you must have at least one organizational user in your AAD tenant. For information about how to create new AAD users, see [Create or edit users in Azure AD](https://msdn.microsoft.com/en-us/library/azure/hh967632.aspx). If you must create a new AAD user for this purpose, go to [https://powerbi.microsoft.com,](https://powerbi.microsoft.com) and sign up for a Power BI account. After your tenant has at least one account that is registered with Power BI, the Power BI service will appear as one of the options for permissions to your Dynamics 365 for Operations web application.

## Configure the environment for Power BI integration
The following procedure must be completed by a Dynamics 365 for Operations system administrator. By default, the Power BI configuration is disabled.

1.  Sign in to Dynamics 365 for Operations by using an account that has the System Administrator role.
2.  Click **System administration** &gt; **Setup** &gt; **Power BI** to open the **Power BI configuration** page. \[caption id="attachment\_260044" align="alignnone" width="640"\][![PowerBI Configuration Form](./media/powerbiconfig2-903x1024.png)](./media/powerbiconfig2.png) Power BI configuration page\[/caption\]
3.  Click the **Edit** button to make changes.
4.  Specify the following values for the fields on this page:
    -   **Enabled:** Set the option to **Yes**.
    -   **Azure AD authority URI:** The correct value, **https://login.windows.net**, should already be entered when you open the page.
    -   **Azure AD Power BI resource URI:** The correct value, **https://analysis.windows.net/powerbi/api**, should already be entered.
    -   **Azure AD Tenant:** The correct value, **contosoax7.onmicrosoft.com**, should already be entered.
    -   **Client ID:** Enter the **Client ID** value that you recorded earlier.
    -   **Application key:** Enter the **Secret Key** value that you recorded earlier.
    -   **Redirect URL:** The correct value, the root URL of your deployment plus **oauth**, should already be entered.
    -   **Power BI API Address:** The correct value, **https://api.powerbi.com/beta/myorg**, should already be entered.
    -   **Apply tile filter:** The correct value, **Yes**, should already be set.
    -   **Tile filter table:** The correct value, **Entities**, should already be entered.
    -   **Tile filter column:** The correct value, **ID**, should already be entered.

5.  Click **Save** to save your changes.

## Connect to Power BI from Dynamics AX for the first time
Users will now see the Power BI control in specific workspaces. (The control must be added as part of the development process. By default, the control isn't added to all workspaces.) The first time that users use the control, they must confirm that they authorize access to their Power BI visualizations. To test your configuration, you can use the **Reservation management** workspace.

1.  On the dashboard page, click the **Reservation management** tile. Alternatively, to use menus, click **Fleet management** &gt; **Workspaces** &gt; **Reservation management**. The Power BI banner appears, as shown in the following screen shot. \[caption id="attachment\_259704" align="alignnone" width="640"\][![PowerBI control in Reservation Management Workspace](./media/fleetws-1024x578.png)](./media/fleetws.png) Power BI control in the Reservation management workspace\[/caption\]
2.  In the Power BI banner, click **Get started**. If this is the first time that you've started Power BI from Dynamics 365 for Operations, you're prompted to authorize sign-in to Power BI from the Dynamics 365 for Operations client. Click **Click here to provide authorization to Power BI**. \[caption id="attachment\_260804" align="alignnone" width="635"\][![PowerBI Authorization](./media/authorization.png)](./media/authorization.png) Power BI authorization\[/caption\]
3.  Because you're already signed in to AAD in Dynamics 365 for Operations, you don't have to enter your credentials again. A new tab appears, where you're prompted to authorize the connection between Dynamics 365 for Operations and Power BI. You can now return to the original tab.
4.  The **Add / remove Power BI tiles** slider dialog opens. The tabs on the left show your dashboards, and the related visualizations appear on the right. You can now select visualizations to add (pin) to the workspace. \[caption id="attachment\_260924" align="alignnone" width="640"\][![Pinning Slider](./media/pinning-836x1024.png)](./media/pinning.png) Pinning slider\[/caption\]
5.  After you've finished selecting visualizations, click **OK**.


See also
--------

[Sign up for Power BI service](https://powerbi.microsoft.com/en-us/documentation/powerbi-developer-sign-up-for-power-bi-service/)

