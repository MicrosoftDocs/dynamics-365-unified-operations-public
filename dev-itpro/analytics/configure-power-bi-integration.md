---
# required metadata

title: Configure Power BI integration for workspaces
description: This tutorial describes the configuration that is required for a new Microsoft Dynamics 365 for Finance and Operations environment to support integration with PowerBI.com. This configuration enables workspaces to show the Power BI control and lets users pin visualizations to a workspace.
author: MilindaV2
manager: AnnBe
ms.date: 07/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: PowerBIConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 27661
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
ms.search.region: Global
# ms.search.industry: 
ms.author: cwesene
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Power BI integration for workspaces

[!include[banner](../includes/banner.md)]

## Overview

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition enables a user to pin tiles and reports from their own PowerBI.com account directly to workspaces.

This functionality requires a one-time configuration to your environment. An administrator must do this step to enable Finance and Operations and Power BI to communicate and authenticate correctly.

Both Finance and Operations and PowerBI.com are cloud-based services. For a Finance and Operations workspace to display a Power BI tile, the Finance and Operations server must contact the Power BI service on behalf of a user and access the visualization. Then it must redraw the visual in the Finance and Operations workspace. “On behalf of a user” is important, when a user, say, <Tim@ContosoAX7.onmicrosoft.com> contacts the PowerBI.com service. Power BI should only display tiles and reports from Tim’s own PowerBI.com account.

By doing this step you are enabling Finance and Operations to contact the PowerBI.com service “on behalf of a user”. This flow between Finance and Operations and the Power BI service is based on the OAuth 2.0 Authorization Code Grant Flow, which is discussed later in this topic.

## Things you need to know before you start 

- You must be a system administrator in Finance and Operations. This option is available from the **System administration** menu.

- You need to have a PowerBI.com account. You could create a trial account if you do not have an account. (You do not need a Pro license for this step).

- You must have at least one dashboard and a report in your Power BI account. While this is not a requirement for the configuration step, you may not be able to validate the successful configuration if you do not have any content in your PowerBI.com account.

- You must be an administrator to your Azure Active directory account. If you are not the administrator, you need an administrative user to perform this operation for you.

- The Azure Active Directory domain that is configured for Finance and Operations must be the same one that you used for your PowerBI.com account. For an example, if you provisioned Finance and Operations in the Contoso.com domain, you must have Power BI accounts in that domain, such as. <Tim@ContosoAX7.onmicrosoft.com>.

## Registration process 

1.  Open a new browser session and launch the Power BI app registration at [https://dev.powerbi.com/apps ](https://dev.powerbi.com/apps). You will be shown a page like the following:

[./media/image1.png](./media/image1.png)

2.  Click the sign-in button. Make sure that your browser is signed in with same Azure Active Directory account that you use for Finance and Operations. After you sign-in, you should see the user’s name displayed in the tool.

[./media/image2.png](./media/image2.png)

3.  Enter the **App name**, such as **Contoso Dyn365**.

4.  Enter the **Redirect URL**. Find the base URL of your Finance and Operations client, and copy and paste. Then add the OAuth suffix to your own URL. For example, the URL should look like: `<http://contosoax7.cloud.dynamics.com/oauth>`.

5.  Enter the **Home page URL**, which is your URL with a mock extension, such as `https://<your own base URL>`.

This value is mandatory, but it isn't required for the workspace integration. Make sure that this App ID URI is a mock URL, since using the URL of your deployment may cause sign-in issues in other AAD applications, such as the Excel Add-in. **Example:** `http://contosoax7.cloud.dynamics.com/testenv/`

6.  Select **all check boxes** for **Choose APIs for Access**.

7.  Select the **Register App** button.

8.  You will see **Client ID** and **Client Secret** as displayed below. You will need these values in the next procedure.

[./media/image3.png](./media/image3.png)

## Specify Power BI settings in Finance and Operations

1.  Navigate to the **Power BI configuration** page in the Finance and Operations client.

   [./media/image4.png](./media/image4.png)

1.  Select **Edit**

2.  Check **Enabled** flag to Yes

3.  **Azure AD tenant** field should show your tenant (or domain name).

>   Example, if you provisioned Dynamics 365 for Operations with the tenant
>   ContosoAX7.onmicrosoft.com, you should see the field populated as shown
>   above. You can enter the correct tenant if the field is not initialized.

>   Also note that PowerBI integration feature doesn’t work on pre-produciton
>   and test AAD domains such as PPE, you would need to change to a prod AAD
>   domain by running the Admin user tool)

1.  Copy the **Client ID** that you got from PowerBI tool in previous step and
    paste to **Client ID** field in the form

2.  Copy the **Client Secret** you got from PowerBI tool in previous step and
    paste to **Application Key** field

3.  Make sure that **Redirect URL** is set to the correct URL. This should be
    the same Redirect URL you provided to PowerBI tool.

>   Example: find the base URL of your Dynamics 365 for Operations client and
>   copy paste. Add OAuth suffix to your own URL. Ex.
>   <http://contosoax7.cloud.dynamics.com/oauth>

1.  Enter “Company” as the value for the **Tile filter table** field. Enter “ID”
    as the value for the **Tile filter column** field

>   These two values will enable filtering PowerBI tiles when they are pinned to
>   a Dynamics 365 for Operations workspace. For an example, if the company
>   context of the workspace is USMF, PowerBI tile will show data filtered for
>   Company USMF such that you would see data corresponding to the current
>   company.

>   To apply the company filter, your PowerBI content must have a Table and a
>   column that’s called “Company” and “ID” respectively. Ready-made PowerBI
>   content shipped with Dynamics 365 for Operations has adopted this
>   convention.

>   If the PowerBI content does not have a table and a field called “Company” or
>   a field called “ID”, the filter will be ignored and you will be shown
>   unfiltered data within the tile.

![](media/1820cc9320b91814dbb7d7c90c04d49f.png)

1.  Select **Save** and close the form

2.  Launch a workspace (ex. Ledger budgets or reservation management) to
    validate the configuration. In this case we will launch the Ledger Budgets
    workspace.

    1.  You should see the PowerBI banner in the workspace – you need to scroll
        to the right.

>   [./media/image6.png](./media/image6.png)

1.  In the Power BI banner, click **Get started**. If this is the first time
    that you've started Power BI from Finance and Operations, you're prompted to
    authorize sign-in to Power BI from the Finance and Operations client. Click
    **Click here to provide authorization to Power BI**.

>   Your users will need to do this the first time they pin PowerBI content.

>   [./media/image7.png](./media/image7.png)

1.  Next you will be shown the Azure Active Directory consent form. This form
    asks for user’s consent. Ie. user consent is necessary for Dynamics 365 for
    Operations to access PowerBI.com “on behalf of the user”. Click the
    **accept** button.

    ![](media/65da7a9b5ac0a328568f76c4e7a0770c.png)

2.  Because you're already signed in to AAD in Finance and Operations, you don't
    have to enter your credentials again. A new tab appears, where you're
    prompted to authorize the connection between Finance and Operations and
    Power BI. You can now return to the original tab.

3.  Next you will be shown a list of tiles from your PowerBI.com account and you
    can select one or more tiles to be pinned to the workspace you have chosen.

Trouble-shooting common errors
==============================

It is possible that you may see an error after you select the **Accept** button in the process above. The next screen shows an error message if this process is unsuccessful. The error message is as follows. Notice that details of the error are shown on the bottom right as shown below. Additional technical information (values shown grayed out) provides you with clues so as to what may have gone wrong.

![](media/ce094da8b9e0674c5cbd75616e40d829.png)

Some common issues and the resolution steps

| Error message                                            | Resolution                                                                                                                                                                                        |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Reply address did not match because of case sensitivity. | It is possible that the URL you entered in the PowerBI tool does not match with the application ID. Launch the PowerBI tool and re-run the registration process                                   |
| PowerBI service is unavailable                           | This error is unlikely to occur most of the times, but It is possible that the PowerBI service is un-reachable. You do not need to re-register. Try to pin a tile into a workspace a little later |
| You can’t access this application…                       | It is likely that you may not have selected all the checkboxes in the PowerBI registration tool Launch the PowerBI tool and re-run the registration process                                       |
| PowerBI tiles page is empty – no content is shown        | It is possible that your PowerBI.com account does not have a dashboard or any tiles. Add a dashboard (ex. sample dashboard) and try pinning a tile again                                          |
|                                                          |                                                                                                                                                                                                   |

Technical details - OAuth 2.0 Authorization Code Grant Flow
===========================================================

This section describes the authorization flow between Finance and Operations and the PowerBI.com service during authentication phase – just before the list of tiles are presented to a user. This is a flow that is executed by Azure Active Directory service to enable two services to securely communicate “on behalf of a user”.

Following diagram shows the authorization flow

![OAuthFlow](media/caaddad46d4ea9e3c7e12e896733594a.png)

1.  When a user visits a workspace in Finance and Operations for the first time,
    the Power BI banner prompts the user to start the first-time connection. If
    the user agrees to start the first-time connection, an OAuth 2.0
    Authorization Code Grant Flow is started.

2.  Finance and Operations redirects the user agent to the Microsoft Azure
    Active Directory (AAD) authorization endpoint. The user is authenticated and
    consents if consent is required. Because the user is running Finance and
    Operations, he or she is already signed in to AAD. Therefore, the user
    doesn't have to enter her or his credentials again.

3.  The AAD authorization endpoint redirects the AAD agent back to the client
    application together with an authorization code. The user agent returns the
    authorization code to the client application’s redirect URL. The application
    redirect URL is a parameter that is maintained in your Power BI
    configuration, as described later in this article.

4.  Now that Finance and Operations has an authorization code on behalf of the
    user, it requests an access token from the AAD token issuance endpoint.
    Finance and Operations presents the authorization code to prove that the
    user has consented.

5.  The AAD token issuance endpoint returns an access token and a refresh token.
    Finance and Operations must have the access tokento request a visualization
    from Power BI. Access tokens expire after a short time. The refresh token
    can be used to request a new token.

6.  Finance and Operations uses the access token to authenticate to the Web API
    that is provided by Power BI. Finance and Operations uses the Web API to
    request that Power BI visualizations be displayed on behalf of the user.

7.  After the client application is authenticated, the Power BI Web API returns
    the requested visualization to the user. Note that Power BI returns only the
    data that the user is allowed to see. Because the Power BI Web API detects
    that the user is connecting via Finance and Operations, it can correctly
    resolve the user.

8.  The user sees Power BI tiles in the Finance and Operations workspace.

For subsequent visits, this entire flow doesn't have to occur. Because Finance and Operations has the access token on behalf of the user, steps 1 through 4 don't have to be repeated.

What’s next
===========

Now that you have enabled PowerBI.com integration feature, you may consider
performing following steps

1.  If your organization is using PowerBI.com, you may invite users to pin Tiles
    and reports from their own PowerBI.com account into workspaces for ease of
    access. For more information see the link here: \<…\>

2.  If you are using Dynamics 365 for Operations spring update or later, you may
    see ready-made Analytical workspaces built into your workspaces (this
    feature is only available in multi-box environments at present). However, if
    you are using a previous version of Dynamics 365 for Operations, you can
    deploy the ready-made reports distributed in LCS into your PowerBI.com
    account. For more information see the link here \<…\>

3.  You may wish to create your own PowerBI content using data available in
    Entity store, the Operational data warehouse included with Dynamics 365 for
    Operations. For more information see the link here \<…\>

4.  You may wish to mash-up external data with ready-made PowerBI content
    provided with Dynamics 365 for Operations using PowerBI solution templates
