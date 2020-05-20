---
# required metadata

title: Configure export to Azure Data Lake
description: This topic explains .
author: MilindaV2
manager: AnnBe
ms.date: 05/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2018-12-03
ms.dyn365.ops.version: Platform Update 23

---

# Configure export to Azure Data Lake

[!include [banner](../includes/banner.md)]


## Overview

Configuring Export to Data lake has several steps.

You must create a storage account in your own Azure subscription. This storage
account will be used to store data.

Next, you must create an Azure Active Directory (Azure AD) application ID that
grants access to the root of your storage account. The system will use the Azure
AD application to gain access to storage – and create the folder structure and
write data.

Finally, you must create a key vault in your subscription, and provide
information about your storage account and the application to the Data Lake
offer in Microsoft Dynamics Lifecycle Services (LCS).

Let's review the steps in detail

In **Azure portal**

1.  Create a Microsoft Azure Data Lake Storage Gen2 account (a storage account)
    in your subscription

2.  Create an Application in Azure Active Directory. Get the App ID and an
    generate an App secret.

3.  Create a Key vault and create 3 secrets that contain the storage account
    name as well as the application ID and App secret

4.  Authorize the Application you created earlier so that it can read the
    secrets in the key vault.

5.  Grant Access control roles so that your application can access the storage
    account

When following above process, the document will instruct you to save several
values such as Key vault details that are required for subsequent steps. Next
you are going to provide these values (via a key vault) to Finance and
Operations using the **Dynamics Life cycle services (LCS),** you will need
Administrator access to LCS in order to perform this step

1.  Install the **Export to Data Lake** add-in in **LCS**

In **Finance and Operations**,

1.  Turn on the **Export to Azure Data Lake** feature.

2.  Select data (that is, the tables and entities that should be staged in Data
    Lake).

3.  Monitor the tables in Data Lake.


Create a Data Lake Storage (Gen2) account in your subscription
--------------------------------------------------------------

The storage account will be used to store data from Finance and Operations. To
manually create a storage account, you must be a user who has administrative
rights to your organization's Azure subscription.

To create a storage account, follow the steps below.

1.  In the Azure portal, create a new storage account. (choose **Create new
    resource** and search for **Storage account – blob, file, table, queue**)

2.  In the Create storage account dialog box, provide values for the following
    parameter fields:

    -   **Location:** Select the data center where your environment is located.
        If the data center that you select is in a different Azure region, you
        may incur additional data movement costs. If your Microsoft Power BI
        and/or your data warehouse is in a different region, you can use
        replication to move storage between regions.

    -   **Performance**: We recommend that you select Standard.

    -   **Account kind**: You must **select StorageV2**. In the Advanced options
        dialog box, you will see the Data Lake storage Gen2 option.

3.  Select the **Advanced tab** and select Enabled under the option for **Data
    Lake storage Gen2 \> Hierarchical namespaces**. If you disable this option,
    you may not be able to consume data written by Finance and Operations apps
    with services such as Power BI data flows and AI builder.

4.  Select **Review and create**. When the deployment is completed, the new
    resource will be shown in the Azure portal.

5.  You will need to copy and keep the following information from the storage
    account created above

    -   In Azure portal, select the created storage account. Copy and save the
        **storage account name**. it should be shown on top left of the storage
        account page.

    -   Select **Settings \> access keys** form the navigation menu on the left.
        Copy **connection string** from either key 1 or key 2
        

Create a key vault and a secret that contains the Storage account
-----------------------------------------------------------------

A key vault is a secure way to hand over details such as storage account name to
Finance and Operations.

To create a key vault and a secret, follow the steps below

1.  In the Azure portal, create a new Key Vault. (choose **Create new resource**
    and search for **Key Vault**)

2.  In the **Create key vault** dialog box, in the **Location** field, select
    the data center where your environment is located.

3.  After Key Vault is created, select it in the list, and then
    select **Secrets**.

4.  Select **Generate/Import**.

5.  In the **Create a secret** dialog box, in the **Upload options** field,
    select **Manual**.

6.  Enter a name for the secret. Make a note of the name, because you will have
    to provide it later.

7.  In the value field, enter the **storage account name** that you obtained
    from the storage account in the previous procedure.

8.  Select **Enabled**, and then select **Create**. The secret is created and
    added to Key Vault.

Create an Application in Azure Active Directory
-----------------------------------------------

1.  In the Azure portal, select **Azure Active Directory**, and then
    select **App registrations**.

2.  Select **New registration**, and enter the following information:

    -   **Name:** Enter a name for the app

    -   Choose the appropriate option for **Supported Account types**

3.  After the application is created, select it. Copy and save the **Application
    (client) ID** that you see on the top of the page. You will need this later

4.  Next select **API permissions** option from the left navigation.

5.  Choose **+Add a permission** option. Select **Azure Key vault** from the
    **Request API permissions** dialog

6.  Select **Delegated permissions**, check **user_impersonation** and select
    **Add permissions.** The result will look like the one below

![](media/ce7b48fc554ff31d7256e20e6398fb6f.png)

1.  Select **Certificates & secrets** option on the left menu for the app.

2.  Select **+New client secret**. In the **Description** field, enter a name.
    Select an option in the **Expires** option. Then select **Add**.

3.  The system will generate a secret next. **Immediately copy the secret to the
    clipboard**, as it will disappear within one or two minutes. You will have
    to provide this secret value when setting up the key vault later.

![](media/5062180174bd6ba94b22f29b43e8aacd.png)

Add secrets to the Key vault
----------------------------

You are going to create 3 secrets in the key vault and add the values saved from
previous steps. For each of the secrets, you will need to provide a secret name
and provide the value you saved from earlier steps.

| **Suggested secret Name** | **Secret value (what you saved earlier…)**                                |
|---------------------------|---------------------------------------------------------------------------|
| app-id                    | The ID of the application created in step (c)                             |
| app-secret                | The client secret specified in step (c)                                   |
| storage-account-name      | The name of the storage account created in step (a). E.g. storageaccount1 |

You will need to perform the following steps 3 times, once for each secret

1.  In the Azure portal, go to the Key vault you created earlier. Select
    **Secrets** in the left navigation menu

2.  Select **+Generate/Import**.

3.  In the **Create a secret** dialog box, in the **Upload options** field,
    select **Manual**.

4.  Provide a **name** for the secret – see the suggested names above.

5.  Copy and paste the corresponding secret value in the **value** field

6.  Select **enabled** and then select **create**.

7.  You will notice the secret created in the list of secrets

Authorize the Application so that it can read the secrets in the Key vault
--------------------------------------------------------------------------

1.  In **Azure Portal**, open the Key Vault that you created earlier.

2.  Select **Access policies** in the left navigation menu and then select
    **+Add Access Policy** to create a new policy. **Add access policy** dialog
    will be shown

3.  In the **Select principal** field, search for the name of the application
    you created earlier.

4.  When you find your application in the list of principals, **click** on the
    application, and click the **select** button at the bottom of the dialog.

5.  Select **Add** in the Add access policy dialog

6.  Select **Save**

7.  Open issue: why do we add the microservices app ID?

| Application                                                   | Permissions |
|---------------------------------------------------------------|-------------|
| Display name of the new application you created from step (c) | Get, List   |
| Microsoft Dynamics ERP Microservices                          | Get, List   |


Grant Access control roles to applications 
-------------------------------------------

Next, you need to grant your application with permissions to read and write to
the storage account. These permissions are granted via Roles in Active
directory.

1.  In **Azure Portal**, open the storage account created you created earlier

2.  Select **Access Control (IAM)** in the left navigation. You will see the
    Access control page.

3.  Select the **Role assignments** tab in the page

4.  Click on **+ Add**, at the top of the page and choose **Add role
    assignment**

5.  In the **Add role assignment** dialog, select the **Role** field and select
    **Owner**.

6.  Keep field **Assign access to**” unchanged as “**Azure AD user, group, or
    service principal**”

7.  In the **Select** field, choose the application you registered earlier.

8.  Select **Save**

9.  You need to add all the roles shown in the following table by following
    similar steps (you already added the owner role. You need to add the rest.

| **Application to be selected**   | **Role to be assigned**     |
|----------------------------------|-----------------------------|
| Your application from step 2 (b) | Owner                       |
| Your application from step 2 (b) | Contributor                 |
| Your application from step 2 (b) | Storage Account Contributor |
| Your application from step 2 (b) | Storage Blob Data Owner     |
| AI Builder Authorization Service | Storage Blob Data Reader    |

Install the Export to Data Lake add-in in LCS 
----------------------------------------------

Before you can export data to your Data lake from Finance and Operations, you
must install the **Export to Data Lake** add-in in LCS. To complete this task,
you must be an environment administrator in LCS for the environment that you
want to use.

You need the following information before you start. Keep the information handy
before you begin.

| **Information you need for Export to Data lake add-in**   | **Where can you find it**                                                                                                                                                                                                |
|-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Your environment AAD Tenant ID                            | You can find your Azure AD tenant ID in the Azure portal. Sign into the **Azure portal** and open the **Azure Active Directory** service. Open the **Properties** page and copy the value in the **Directory ID** field. |
| DNS name of your Key vault                                | You should have created a key vault by following the steps \<here\> You need the DNS name of your Key vault                                                                                                              |
| The secret that contains the name of your storage account |                                                                                                                                                                                                                          |
| Secret that contains the Application ID                   |                                                                                                                                                                                                                          |
| Secret that contains the Application secret               |                                                                                                                                                                                                                          |

1.  Sign in to [LCS](https://lcs.dynamics.com). Navigate to your environment.

2.  On the **Environment** page, select the **Environment add-ins** Tab. If
    **Export Data Lake** appears in the list, the Data Lake add-in is already
    installed, and you can skip the rest of this procedure. Otherwise, follow
    the remaining steps to install the Data Lake add-in.

-   to do: picture the Data Lake add-in is installed

1.  Select **Install a new add-in**.

2.  In the **Select an add-in to install** dialog box, select **Export to Data
    lake** in the list. If it isn't listed, the feature might not yet be
    available for your environment.

-   Selecting the Azure Data lake option

    Selecting the Azure Data lake option

1.  In the **Setup add-in** dialog box, provide the required information. To
    answer the questions, you must already have a storage account. If you don't
    already have a storage account, create one, or ask your admin to create one
    on your behalf.

-   Entering details for the Data Lake add-in

    Entering details for the Data Lake add-in

1.  Accept the terms of the offer by selecting the check box, and then select
    **Install**.

The system installs and configures the data lake for the environment. After
installation and configuration are completed, you should see **Azure Data Lake**
listed on the **Environment** page.

