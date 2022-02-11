---
# required metadata

title: Set up a B2C tenant in Commerce
description: This topic describes how to set up your Azure Active Directory (Azure AD) business-to-consumer (B2C) tenants for user site authentication in Dynamics 365 Commerce.
author: BrianShook
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: brshoo
ms.search.validFrom: 2020-02-13
ms.dyn365.ops.version: 

---

# Set up a B2C tenant in Commerce

[!include [banner](includes/banner.md)]

This topic describes how to set up your Azure Active Directory (Azure AD) business-to-consumer (B2C) tenants for user site authentication in Dynamics 365 Commerce.

Dynamics 365 Commerce uses Azure AD B2C to support user credential and authentication flows. A user can sign up, sign in, and reset their password through these flows. Azure AD B2C stores sensitive user authentication information, such as username and password. The user record in the B2C tenant will store either a B2C local account record or a B2C social identity provider record. These B2C records will link back to the customer record in the Commerce environment.

> [!WARNING] 
> Azure AD B2C will retire old (legacy) user flows by August 1, 2021. Therefore, you should plan to migrate your user flows to the new recommended version. The new version provides feature parity and new features. The module library for Commerce version 10.0.15 or higher should be used with the recommended B2C user flows. For more information, see [User flows in Azure Active Directory B2C](/azure/active-directory-b2c/user-flow-overview).
 
 > [!NOTE]
 > Commerce evaluation environments come with a pre-loaded Azure AD B2C tenant for demonstration purposes. Loading your own Azure AD B2C tenant using the steps below is not required for evaluation environments.

> [!TIP]
> You can further protect your site users and enhance the security of your Azure AD B2C tenants with Azure AD Identity Protection and Conditional Access. To review the capabilities available to Azure AD B2C Premium P1 and Premium P2 tenants, see [Identity Protection and Conditional Access for Azure AD B2C](/azure/active-directory-b2c/conditional-access-identity-protection-overview).

## Dynamics environment prerequisites

Before you begin, ensure that your Dynamics 365 Commerce environment and e-commerce channel are configured appropriately by fulfilling the following prerequisites.

- Set the POS operations **AllowAnonymousAccess** value to "1" in Commerce headquarters:
    1. Go to **POS Operations**.
    1. In the operations grid, right-click and select **Personalize**.
    1. Select **Add a field**.
    1. In the list of available columns, select the **AllowAnonymousAccess** column to add it.
    1. Select **Update**.
    1. For the **612** "Customer add" operation, change **AllowAnonymousAccess** to "1."
    1. Run the **1090 (Registers)** job.
- Set the number sequence customer account **Manual** attribute to **No** in Commerce headquarters:
    1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Accounts receivable parameters**.
    1. Select **Number sequences**.
    1. In the **Customer account** row, double-click the **Number Sequence Code** value.
    1. On the **General** FastTab of the number sequence, set **Manual** to **No**.

After deployment of your Dynamics 365 Commerce environment, it also is recommended to [Initialize seed data](enable-configure-retail-functionality.md) in the environment.

## Create or link to an existing Azure AD B2C tenant in the Azure portal

This section covers creating or linking an Azure AD B2C tenant for use in your Commerce site. For more information, see [Tutorial: Create an Azure Active Directory B2C tenant](/azure/active-directory-b2c/tutorial-create-tenant).

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. From the Azure portal menu, select **Create a resource**. Be sure to use the subscription and directory that will be connected with your Commerce environment.

    ![Create a Resource in Azure Portal.](./media/B2CImage_1.png)

1. Go to **Identity \> Azure Active Directory B2C**.
1. Once on the **Create New B2C Tenant or Link to existing Tenant** page, use one of the options below that best suits your company's needs:

    - **Create a new Azure AD B2C Tenant**: Use this option to create a new Azure AD B2C tenant.
        1. Select **Create a new Azure AD B2C Tenant**.
        1. Under **Organization name**, enter the organization name.
        1. Under **Initial domain name**, enter the initial domain name.
        1. For **Country or region**, select the country or region.
        1. Select **Create** to create the tenant.

     ![Create a new Azure AD Tenant.](./media/B2CImage_2.png)

     - **Link an existing Azure AD B2C Tenant to my Azure subscription**: Use this option if you already have an Azure AD B2C tenant you want to link to.
        1. Select **Link an existing Azure AD B2C Tenant to my Azure subscription**.
        1. For **Azure AD B2C Tenant**, select the appropriate B2C tenant. If the message "No eligible B2C Tenants found" appears in the selection box, you do not have an existing eligible B2C tenant and will need to create a new one.
        1. For **Resource group**, select **Create new**. Enter a **Name** for the resource group that will contain the tenant, select the **Resource group location**, and then select **Create**.

    ![Link an existing Azure AD B2C Tenant to Azure Subscription.](./media/B2CImage_3.png)

1. Once the new Azure AD B2C directory is created (this may take a few moments), a link to the new directory will appear on the dashboard. This link will direct you to the "Welcome to Azure Active Directory B2C" page.

    ![Link to new Azure AD Directory](./media/B2CImage_4.png)

> [!NOTE]
> If you have multiple subscriptions within your Azure account or have set up the B2C tenant without linking to an active subscription, a **Troubleshoot** banner will direct you to link the tenant to a subscription. Select the troubleshooting message and follow the instructions to resolve the subscription issue.

The following image shows an example of an Azure AD B2C **Troubleshoot** banner.

![Warning showing directory has no Active Subscription.](./media/B2CImage_5.png)

## Create the B2C application

Once the B2C tenant has been created, you will create a B2C application within your new Azure AD B2C tenant to interact with Commerce.

To create the B2C application, follow these steps.

1. In the Azure portal, select **App registrations**, and then select **New registration**.
1. Under **Name**, enter the name to give this Azure AD B2C application.
1. Under **Supported account types**, select **Accounts in any identity provider or organizational directory (for authenticating users with user flows)**.
1. For **Redirect URI**, enter your dedicated reply URLs as type **Web**. For information on reply URLs and how to format them, see [Reply URLs](#reply-urls) below. A redirect URI/reply URL must be entered to enable redirections from Azure AD B2C back to your site when a user authenticates. The reply URL can be added during the registration process, or can be added later by selecting the **Add a Redirect URI** link from the **Overview** menu in the B2C application's **Overview** section.
1. For **Permissions**, select **Grant admin consent to openid and offline_access permissions**.
1. Select **Register**.
1. Select the newly created application and navigate to the **Authentication** menu. 
1. If a reply URL is entered, under **Implicit grant and hybrid flows** select both the **Access tokens** and **ID tokens** options to enable them for the application, and then select **Save**. If a reply URL was not entered during registration, it can also be added on this page by selecting **Add a platform**, selecting **Web**, and then entering the redirect URI of the application. The **Implicit grant and hybrid flows** section will then be available to select both the **Access tokens** and **ID tokens** options.
1. Go to the **Overview** menu of the Azure portal and copy the **Application (client) ID**. Note this ID for later setup steps (referenced later as the **Client GUID**).

For additional reference on App Registrations in Azure AD B2C, please see [The new App registrations experience for Azure Active Directory B2C](/azure/active-directory-b2c/app-registrations-training-guide)

### Reply URLs

Reply URLs are important as they provide an allow list of the return domains when your site calls Azure AD B2C to authenticate a user. This permits the return of the authenticated user back to the domain from which they are signing into (your site domain). 

In the **Reply URL** box on the **Azure AD B2c - Applications \> New application** screen, you need to add separate lines for both your site domain and (once your environment is provisioned) the Commerce-generated URL. These URLs must always use a valid URL format and must be base URLs only (no trailing forward slashes or paths). The string ``/_msdyn365/authresp`` then needs to be appended to the base URLs, as in the following examples.

- ``https://www.fabrikam.com/_msdyn365/authresp`` (The domain should match the e-commerce domain completely. If you have multiple domains, you need to add this URL for each domain.)
- ``https://fabrikam-prod.commerce.dynamics.com/_msdyn365/authresp``

## Create user flow policies

User flows are the policies Azure AD B2C uses to provide secure sign in, sign up, edit profile, and forget password user experiences. Dynamics 365 Commerce uses these flows to perform the policy actions to interact with the Azure AD B2C tenant. When a user interacts with these policies, they are redirected to the Azure AD B2C tenant to perform the actions.

Azure AD B2C provides three basic user flow types:
- Sign up and sign in
- Profile editing
- Password reset

You can choose to use the default user flows provided by Azure AD, which will display a page hosted by Azure AD B2C. Alternately, you can create an HTML page to control the look and feel of these user flow experiences. 

To customize the user policy pages with pages built in Dynamics 365 Commerce, see [Set up custom pages for user logins](custom-pages-user-logins.md). For additional information, see [Customize the interface of user experiences in Azure Active Directory B2C](/azure/active-directory-b2c/tutorial-customize-ui).

### Create a sign up and sign in user flow policy

To create a sign up and sign in user flow policy, follow these steps.

1. In the Azure portal, select **User flows (policies)** in the left navigation pane.
1. On the **Azure AD B2C – User flows (policies)** page, select **New User Flow**.
1. Select the **Sign up and sign in** policy, and then select the **Recommended** version.
1. Under **Name**, enter a policy name. This name will display afterwards with a prefix the portal assigns (for example, "B2C_1_").
1. Under **Identity providers**, in the **Local accounts** section, select **Email signup**. Email authentication is used in most common scenarios for Commerce. If you are also using social identity provider authentication, these can also be selected at this time.
1. Under **Multifactor Authentication**, select the appropriate choice for your company. 
1. Under **User attributes and claims**, select options to collect attributes or return claims as appropriate. Select **Show more...** to get the full list of attributes and claims options. Commerce requires the following default options:

    | **Collect  attribute** | **Return  claim** |
    | ---------------------- | ----------------- |
    | Email Address          | Email Addresses   |
    | Given Name             | Given Name        |
    |                        | Identity Provider |
    | Surname                | Surname           |
    |                        | User’s Object ID  |

1. Select **Create**.

The following image is an example of the Azure AD B2C sign up and sign in user flow.

![Sign Up and Sign In policy settings.](./media/B2CImage_11.png)

   
### Create a profile editing user flow policy

To create a profile editing user flow policy, follow these steps.

1. In the Azure portal, select **User flows (policies)** in the left navigation pane.
1. On the **Azure AD B2C – User flows (policies)** page, select **New User Flow**.
1. Select **Profile editing**, and then select the **Recommended** version.
1. Under **Name**, enter the profile editing user flow. This name will display afterwards with a prefix the portal assigns (for example, "B2C_1_").
1. Under **Identity providers**, in the **Local accounts** section, select **Email SignIn**.
1. Under **User attributes**, select the following check boxes:
    
    | **Collect  attribute** | **Return  claim** |
    | ---------------------- | ----------------- |
    |                        | Email Addresses   |
    | Given Name             | Given Name        |
    |                        | Identity Provider |
    | Surname                | Surname           |
    |                        | User's Object ID  |
    
1. Select **Create**.

The following image shows an example of the Azure AD B2C profile editing user flow.

![Example of the Azure AD B2C profile editing user flow](./media/B2CImage_12.png)

### Create a password reset user flow policy

To create a password reset user flow policy, follow these steps.

1. In the Azure portal, select **User flows (policies)** in the left navigation pane.
1. On the **Azure AD B2C – User flows (policies)** page, select **New User Flow**.
1. Select **Password Reset**, and then select the **Recommended** version.
1. Under **Name**, enter a name for the password reset user flow.
1. Under **Identity providers**, select **Reset password using email address**.
1. Select **Create**.
1. Under **Application claims**, select the following check boxes:
    - **Email addresses**
    - **Given Name**
    - **Surname**
    - **User's Object ID**
1. Select **Create**.

The following image shows where to set **Reset Password using mail address** in the Azure AD B2C password reset user flow.

![Set "Reset Password using mail address" in Password Reset policy](./media/B2CImage_13.png)

## Add social identity providers (Optional)

Social identity providers allow users to use their social accounts for authentication. Adding social identity provider authentication is optional in Dynamics 365 Commerce. 

If social identity provider authentication is not added, the default Azure AD B2C profiles will be the main profiles for your user base. Users will select their own username (their preferred email address) and set a password. Azure AD B2C will authenticate users directly. 

If social identity provider authentication is added and a user chooses one of the social identity providers offered, an entity is still created in the Azure AD B2C tenant. Azure AD B2C will then authenticate the user's credentials with the social identity provider.

> [!NOTE]
> The identity provider sign in creates a record in the B2C tenant, but in a different format than local accounts since it will call the external social identity provider reference for authentication. The user can use the same email address across social identity providers, meaning that the email username used for authentication may not be unique to the tenant. Azure AD B2C will only enforce that users have a unique email address on local B2C accounts.

Before you can add a social identity provider for authentication, you must go to the identity provider's portal and set up an identity provider application as instructed in the Azure AD B2C documentation. A list of links to the documentation is provided below.

- [Amazon](/azure/active-directory-b2c/active-directory-b2c-setup-amzn-app)
- [Azure AD (Single Tenant)](/azure/active-directory-b2c/active-directory-b2c-setup-oidc-azure-active-directory)
- [Microsoft Account](/azure/active-directory-b2c/active-directory-b2c-setup-msa-app)
- [Facebook](/azure/active-directory-b2c/active-directory-b2c-setup-fb-app)
- [GitHub](/azure/active-directory-b2c/active-directory-b2c-setup-github-app)
- [Google](/azure/active-directory-b2c/active-directory-b2c-setup-goog-app)
- [LinkedIn](/azure/active-directory-b2c/active-directory-b2c-setup-li-app)
- [OpenID Connect](/azure/active-directory-b2c/active-directory-b2c-setup-oidc-idp)
- [Twitter](/azure/active-directory-b2c/active-directory-b2c-setup-twitter-app)

### Add and set up a social identity provider

To add and set up a social identity provider, follow these steps.  

1. In the Azure portal, navigate to **Identity Providers**.
1. Select **Add**. The **Add identity provider** screen appears.
1. Under **Name**, enter the name to be displayed to users on your sign in screen.
1. Under **Identity provider type**, select an identity provider from the list.
1. Select **OK**.
1. Select **Set up this identity provider** to access the **Set up the social identity provider** screen.
1. Under **Client ID**, enter the client ID as obtained from the identity provider application setup.
1. Under **Client secret**, enter the client secret as obtained from the identity provider application setup.
1. Attach user flow for sign in sign up policies:
1. Go to **Azure AD B2C – User flows (policies) \> {your sign-in sign-up policy} \> Identity providers**.
1. To attach the sign in/sign up user flow policy, select each identity provider you have set up for your account. To test these, select **Run user flow** for each identity provider. A new tab will display the sign-in page displaying the new identity provider selection box.

The following image shows examples of the **Add identity provider** and **Set up the social identity provider** screens in Azure AD B2C.

![Adding a Social Identity Provider to your application.](./media/B2CImage_14.png)

The following image shows an example of how to select identity providers on the Azure AD B2C **Identity Providers** page.

![Select each Social Identity Provider to enable for your policy.](./media/B2CImage_16.png)

The following image shows an example of a default sign-in screen with a social identity provider sign-in button displayed.

> [!NOTE]
> If using the custom pages built in Commerce for your user flows, the buttons for social identity providers will need to be added using the extensibility features of the Commerce module library. Additionally, when setting up your applications with a specific social identity provider, in some cases URL or configuration strings may be case sensitive. Refer to your social identity provider's connection instructions for more information.
 
![Example default login screen with Social Identity Provider sign-in button displayed.](./media/B2CImage_17.png)

## Update Commerce headquarters with the new Azure AD B2C information

Once the Azure AD B2C provisioning steps above are completed, the Azure AD B2C application must be registered in your Dynamics 365 Commerce environment.

To update headquarters with the new Azure AD B2C information, follow these steps.

1. In Commerce, go to **Commerce Shared Parameters** and select **Identity Providers** in the left menu.
1. Under **Identity Providers**, do the following:
    1. In the **Issuer** box, enter the identity provider issuer string. To find your issuer string, see [Obtain issuer string for headquarters setup](#obtain-issuer-string-for-headquarters-setup) below.
    1. In the **Name** box, enter a name for your issuer record.
    1. In the **Type** box, enter **Azure AD B2C (id_token)**.
1. Under **Relying Parties**, with the above B2C identity provider item selected, do the following:
    1. In the **ClientID** box, enter your B2C application ID. You can find this in the **Application ID** box of your B2C application's properties page.
    1. In the **Type** box, enter **Public**.
    1. In the **User Type** box, enter **Customer**.
1. On the action pane, select **Save**.
1. In the Commerce search box, search for **Distribution schedule**
1. In the left navigation menu of the **Distribution schedules** page, select job **1110 Global configuration**.
1. On the action pane, select **Run Now**.

### Obtain issuer string for headquarters setup

To obtain your identity provider issuer string, follow these steps.

1. On the Azure AD B2C page of the Azure portal, navigate to your **Sign up and sign in** user flow.
1. Select **Page layouts** in the left navigation menu, under **Layout name** select **Unified sign up or sign in page**, and then select **Run user flow**.
1. Ensure that your application is set to your intended Azure AD B2C application created above, and then select the user flow link that appears under the **Run user flow** header that includes ``.../.well-known/openid-configuration?p=<B2CSIGN-INPOLICY>``. (Do not select **Run user flow**.) A new tab will open displaying metadata for the policy to collect the issuer string.
1. On the metadata page displayed in your browser tab, copy the identity provider issuer string (the value for **issuer** starting with "https://" and ending with "/v2.0/" ) that looks similar to the following example.
   - ``https://login.fabrikam.com/011115c3-0113-4f43-b5e2-df01266e24ae/v2.0/``.
 
**OR**: To construct the same metadata URL manually, do the following steps.

1. Create a metadata address URL in the following format using your B2C tenant and policy: ``https://<B2CTENANTNAME>.b2clogin.com/<B2CTENANTNAME>.onmicrosoft.com/v2.0/.well-known/openid-configuration?p=<B2CSIGN-INPOLICY>``
    - Example: ``https://d365plc.b2clogin.com/d365plc.onmicrosoft.com/v2.0/.well-known/openid-configuration?p=B2C_1_signinup``.
1. Enter the metadata address URL into a browser address bar.
1. In the metadata, copy the identity provider issuer URL (the value for **"issuer"**).
    - Example: ``https://login.fabrikam.com/011115c3-0113-4f43-b5e2-df01266e24ae/v2.0/``.

## Configure your B2C tenant in Commerce site builder

Once setup of your Azure AD B2C tenant is completed, you must configure the B2C tenant in Commerce site builder. Configuration steps include collecting B2C application information from the Azure portal, entering that B2C application information into site builder, and then associating the B2C application with your site and channel.

### Collect the required application information

To collect the required application information, follow these steps.

1. In the Azure portal, go to **Home \> Azure AD B2C - App registrations**.
1. Select your application, and then in the left navigation pane select **Overview** to obtain the application details.
1. From the **Application (client) ID** reference, collect the application ID of the B2C application created in your B2C tenant. This will later be entered as the **Client GUID** in site builder.
1. Select **Redirect URIs** and collect the reply URL shown for your site (the reply URL entered at setup).
1. Go to **Home \> Azure AD B2C – User flows**, and then collect the full names of each user flow policy.

The following image shows an example of the **Azure AD B2C - App registrations** overview page.

![Azure AD B2C - App registrations overview page with the Application (client) ID highlighted](./media/ClientGUID_Application_AzurePortal.png)

The following image shows an example of user flow policies on the **Azure AD B2C – User flows (policies)** page.

![Collect the names of each B2C policy flow.](./media/B2CImage_22.png)

### Enter your Azure AD B2C tenant application information into Commerce

You must enter details of the Azure AD B2C tenant into Commerce site builder before associating the B2C tenant with your site(s).

To add your Azure AD B2C tenant application information to Commerce, follow these steps.

1. Sign in as an administrator to Commerce site builder for your environment.
1. In the left navigation pane, select **Tenant Settings**  to expand it.
1. Under **Tenant Settings**, select **B2C Settings**. 
1. In the main window next **B2C Applications**, select **Manage**. (If your tenant appears in the B2C Applications list, then it was already added by an administrator. Verify that the items in step 6 below match your B2C Application.)
1. Select **Add B2C Application**.
1. Enter the following required items in the form displayed, using values from your B2C tenant and application. Fields that are not required (those without an asterisk) may be left blank.

    - **Application Name**: The name for your B2C Application, for example "Fabrikam B2C".
    - **Tenant Name**: The name of your B2C tenant (for example, use "fabrikam" if the domain appears as "fabrikam.onmicrosoft.com" for the B2C tenant). 
    - **Forget Password Policy ID**: The forget password user flow policy ID, for example "B2C_1_PasswordReset".
    - **Signup Signin Policy ID**: The sign up and sign in user flow policy ID, for example "B2C_1_signup_signin".
    - **Client GUID**: The B2C application ID, for example "22290eb2-c52e-42e9-8b35-a2b0a3bcb9e6".
    - **Edit Profile Policy ID**: The profile editing user flow policy ID, for example "B2C_1A_ProfileEdit".

1. Select **OK**. You should now see the name of your B2C application appear in the list.
1. Select **Save** to save your changes.

### Associate the B2C application to your site and channel

> [!WARNING]
> If your site is already associated with a B2C application, changing to a different B2C application will remove the current references established for users already signed up in this environment. If changed, any credentials associated with the currently-assigned B2C application will not be available to users. 
> 
> Only update the B2C application if you are setting up the channel's B2C application for the first time or if you intend to have users re-sign up with new credentials to this channel with the new B2C application. Take caution when associating channels to B2C applications, and name applications clearly. If a channel is not associated to a B2C application in the steps below, users signing into that channel for your site will be entered into the B2C application showing as **default** in the **Tenant Settings \> B2C Settings** list of B2C applications.

To associate the B2C application to your site and channel, follow these steps.

1. Navigate to your site in Commerce site builder.
1. In the left navigation pane, select **Site Settings** to expand it.
1. Below **Site Settings**, select **Channels**.
1. In the main window under **Channels**, select your channel.
1. In the channel properties pane on the right, select your B2C application name from the **Select B2C Application** drop-down menu.
1. Select **Close**, and then select **Save and Publish**.

## Additional B2C information

### Customer migration

If you are considering migrating customer records from a previous identity provider platform, please work with the Dynamics 365 Commerce team to review your customer migration needs.

For additional Azure AD B2C documentation on customer migration, see [Migrate users to Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-user-migration).

### Custom policies

For additional information regarding customizing Azure AD B2C interactions and policy flows beyond what is offered by B2C standard policies, see [Custom policies in Azure Active Directory B2C](/azure/active-directory-b2c/active-directory-b2c-overview-custom). 

### Secondary admin

An optional, secondary administrator account can be added in the **Users** section of your B2C tenant. This can be a direct account or a general account. If you need to share an account across team resources, a common account can also be created. Due to the sensitivity of the data stored in Azure AD B2C, a common account should be monitored closely per your company's security practices.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
