# Get started with the Electronic invoicing add-on service administration

# Prerequisites

Before you complete the steps in this topic, you must have the following
prerequisites in place:

-   Access to your LCS account.

-   An LCS project that includes Finance and Supply Chain Management:

    -   Version 10.0.13 or later

    -   Deployed in one of those Azure geographies:

        -   United states

        -   Europe

-   Access to your RCS account.

-   Turn on the Globalization feature for your RCS account through the
    Feature management module. For more information, see [Regulatory
    Configuration Services (RCS) - Globalization
    features](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rcs-globalization-feature).

-   Create a key vault resource and a storage account in Azure. For more
    information, see [Create Azure Storage Account and Key
    Vault](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-create-azure-storage-account-key-vault).

# Install the add-on for microservices in LCS

1.  Sign in to your LCS account.

2.  Select the **Preview feature management** tile.

3.  In **Public Preview Features** field group, select **e-Invoicing
    service.**

4.  Make sure the toggle **Preview feature enabled** is set to Yes.

# Set up the RCS integration parameters with Electronic invoicing add-on 

1.  Sign in to your RCS account.

2.  In the **Electronic reporting** workspace, in the **Related links**
    section, select the **Electronic reporting parameters** link.

3.  Click **e-Invoicing service** tab.

4.  In the **Service endpoint URI** field, type the service end point:

<https://electronicinvoicinglocal.wus2-il100.gateway.test.island.powerapps.com/>

1.  In the **Application Id** field, verify that it shows the ID
 **0cdb527f-a8d1-4bf8-9436-b352c68682b2**. This value is a fixed
    value.

2.  In the **LCS Environment Id** field, type the ID of your LCS
    subscription account.

3.  Click **Save**.

4.  Close the page.

# Create an Electronic invoicing add-on environment

1.  Sign in to your RCS account.

2.  In the **Globalization feature** workspace, in the **Environment**
    section, select the **e-Invoicing** tile.

## Create a service environment

1.  Click **Service environment** on the Action pane.

2.  Click **Key Vault parameters** on the Action pane.

3.  Click **New** to create a new key vault secret.

4.  In the **Name** field, type the name of the key vault secret.

5.  In the **Description** field, type the description.

6.  In the **Key Vault URI** field, paste the secret from Azure
    Keyvault.

7.  In the **Certificates** section, enter all digital certificate names
    and key vault secrets that are needed to establish trustable
    connections. Click **Add** to add a new certificate or secret.

8.  In the **Name** field, type the name of the certificate or secret.

9.  In the **Description** field, type the description.

10. In the **Type** field, select if it is a Certificate or a Secret.
    Both sets of values are configured on the key vault resource in
    Azure.

11. If your country/region-specific invoices require a chain of
    certificates to apply digital signatures, click **Chain of
    certificates** on the Action pane.

    1.  Click **New** to create a chain of certificates.

    2.  In the **Name** field, type the name of the chain of
        certificate.

    3.  In the **Description** field, type the description.

    4.  In the **Certificates** section, click **Add** to add a new
        certificate to the chain.

    5.  Use **Up** or **Down** to move the position of the certificate
        in the chain.

    6.  Click **Save.**

    7.  Close the page.

12. Close the page.

13. Click **New** to create a new e-Invoicing environment.

14. In the **Name** field, type the name of the e-Invoicing environment.

15. In the **Description** field, type the description.

16. In the **Storage SAS token secret**, select the certificate that
    must be use to authenticate the access to the storage account.

17. In the **Users** section, click **Add** to the allow a user to
    submit electronic invoices through this environment.

18. In the **User ID** field, type the alias of the user.

19. In the **Email** field, type the e-mail of the user.

20. Click **Save.**

21. Click **Publish** on the Action pane to publish the environment to
    the cloud, the **Status** field is changed to Published.

22. Close the page.

## Create a connected application

1.  Click **Connected applications** on the Action pane.

2.  Click **New** to create a new connected application.

3.  In the **Name** field, type the name of the application to connect.

4.  In the **Application** field, type the URL of the Finance and Supply
    Chain Management environment to connect.

5.  In the **Tenant** field, type the Tenant of the Finance and Supply
    Chain Management environment.

6.  Click **Save**.

7.  Click **Check connection** on the Action pane for testing the
    connection with the environment.

8.  Close the page.

## Link Connected applications to Environments

1.  Click **New** to assign a connected application to an environment.

2.  In the **Connected application** field, select a Connected
    application.

3.  In the **Service environment** field, select a Service environment.

4.  Click **Save**.

5.  Close the page.

# Set up the Electronic invoicing add-on integration in Finance and Supply Chain Management

## Turn on the Electronic invoicing add-on integration feature

1.  Sign in to Finance and Supply Chain Management.

2.  In the **Feature management** workspace, search for the new feature,
 **Electronic invoicing add-on integration**. If the
    feature is still not shown in Feature management page, run **Check
    for updates** function.

3.  Select the feature, and then select **Enable now**.

## Set up the service endpoint URL

1.  Go to **Organization administration &gt; Setup &gt; Electronic
    document parameters**.

2.  Click **Submission service** tab.

3.  In the **Service endpoint URL** field, type the service end point:

<https://electronicinvoicinglocal.wus2-il100.gateway.test.island.powerapps.com/>

1.  In the **Environment** field, type the name of the Electronic
    invoicing add-on Environment.

2.  Click **Save.**

3.  Close the page.
