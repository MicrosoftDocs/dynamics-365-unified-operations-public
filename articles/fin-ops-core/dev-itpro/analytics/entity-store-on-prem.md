---
title: PowerBI.com integration with on-premises environments
description: This article provides information about how to enable Entity Store for on-premises deployments.
author: MilindaV
ms.date: 05/27/2021
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: milindav
ms.search.validFrom: 2019-06-17
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
ms.search.form: EntityStoreOnPrem
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# PowerBI.com integration with on-premises environments

[!include [banner](../includes/banner.md)]

The cloud version provides several features that allow for deeper integration with Microsoft Power BI. Some of these features haven't yet been implemented for on-premises deployments. However, the availability of Entity Store in on-premises deployments lets customers use PowerBI.com to report on and analyze data. 

This article outlines the analytical capabilities that are available in on-premises deployments that run Microsoft Dynamics 365 Finance platform update 26 (May 2019) and later.

| Feature/capability                                                           | Cloud     | On-premises (Platform update 26 or later) |
|------------------------------------------------------------------------------|-----------|-------------------------------------------|
| Analytical workspaces                                                        | Available | **Not yet implemented**<p>Customers can use the reports that are built on Entity Store together with PowerBI.com.</p> |
| Pin reports, tiles, and dashboards from PowerBI.com into the client.         | Available | **Not yet implemented** |
| Author and distribute Power BI reports that use application data. | Available | **Available**<p>Customers can modify ready-made reports and create new reports by using Entity Store on-premises.</p> |
| Extract application data into data warehouses.                    | Available | **Available** |

## Enable Entity Store on-premises

This article supplements the [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-latest.md) article. The section numbers that follow correspond to the section numbers in that article.

### [3. Plan your users and service accounts](../deployment/setup-deploy-on-premises-latest.md#plansvcacct)

| User account               | Type     | Purpose | User name |
|----------------------------|----------|---------|-----------|
| AOS SQL AXDW DB Admin user | SQL user | The application uses this user to enter information in the AXDW database. This user is optional and must be created only if you want Entity Store support. | axdwadmin |
| AOS SQL AXDW FB Admin user | SQL user | The application uses this user to enter information in the AXDW database. This user is optional and must be created only if you want Entity Store support. | axdwruntimeuser |

### [14. Configure the databases](../deployment/setup-deploy-on-premises-latest.md#configuredb)

The steps in this section are optional.

If you want to create a database that can be used for Entity Store, you must first modify the ConfigTemplate.xml file.

1. Under **DbServer – Security**, set the **generateUser** flags for **axdwadmin** and **axdwruntimeuser** to **True**. The scripts that you run in the next step will then create those two users. You will be prompted to set passwords for the users.
2. Run the following scripts.

    ```powershell
    .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName EntityStore
    .\Configure-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName EntityStore
    ```

    The Initialize-Database.ps1 script performs the following actions:

    - Create an empty database that is named **AXDW**. This database is used for Entity Store.
    - Create a new user that is named **axdwadmin** and that has SQL authentication enabled, and prompt you for the user's password.
    - Create a new user that is named **axdwruntimeuser** and that has SQL authentication enabled, and prompt you for the user's password.
    - Grant the axdwadmin and axdwruntimeuser users **db\_owner** permissions on the database.

    The Configure-Database.ps1 script performs the following actions:

    - Set the specified database file and log settings.
    - GRANT VIEW SERVER STATE TO axdwadmin.
    - GRANT VIEW SERVER STATE TO axdwruntimeuser.

### [15. Encrypt credentials](../deployment/setup-deploy-on-premises-latest.md#encryptcred)

Create a Credentials.json file as shown here. The **AosDWAuth** category is optional and is used only if Entity Store is enabled.

```json
{
    "AosPrincipal": {
        "AccountPassword": "<encryptedDomainUserPassword>"
    },
    "AosSqlAuth": {
        "SqlUser": "<encryptedSqlUser>",
        "SqlPwd": "<encryptedSqlPassword>"
    },
    "AosDWAuth": {
        "DWUser": "<encryptedDWUser>",
        "DWPwd": "<encryptedDWPassword>",
        "DWRuntimeUser": "<encryptedDWRuntimeUser>",
        "DWRuntimePwd": "<encryptedDWRuntimePassword>"
    }
}
```

Here is an explanation of the preceding code lines:

- **AccountPassword** is the encrypted domain user password for the Application Object Server (AOS) domain user (contoso\\axserviceuser).
- **SqlUser** is the encrypted SQL user (axdbadmin) that has access to the application database (AXDB). **SqlPwd** is the encrypted SQL password.
- **DWUser** is the encrypted SQL user (axdwadmin) that has access to the Entity Store database (AXDW). **DWPwd** is the encrypted SQL password that is entered when the Initialize-Database.ps1 script is run.
- **DWRuntimeUser** is the encrypted SQL user (axdwruntimeuser) that has access to the Entity Store database (AXDW). **DWRuntimePwd** is the encrypted SQL password that is entered when the Initialize-Database.ps1 script is run.

## More information

Entity Store was enabled in Platform update 26.

Creation of the Entity Store database and users is optional. When you configure a deployment in Microsoft Dynamics Lifecycle Services (LCS), you can leave the Entity Store customizations blank.

If Entity Store should be enabled in an environment, the following tasks must be completed:

- Create an **AXDW** database by using the scripts that are described in step 14.
- Create **axdwadmin** and **axdwruntimeuser** users that have appropriate privileges, by using the scripts in that are described step 14. Users are defined in the following files: ConfigTemplate.xml and DatabaseTopologyDefinition.xml.
- Create a **Credentials.json** file as described in step 15. User names and passwords should be defined for axdwadmin and axdwruntimeuser as described in step 14, and they should be encrypted.
- The Entity Store SQL Server name and Entity Store database name must be filled in during deployment in LCS.

    - The database name is created in step 14 and is defined in the DatabaseTopologyDefinition.xml file. The default name is **AXDW**.
    - The SQL Server name is the fully qualified domain name (FQDN) of the Microsoft SQL Server or Always on listener. An example of this FQDN is **sqlinstance.onprem.contoso.com**. It's the server that the AXDW database is created on.

To enable Entity Store in an environment that has already been deployed, you can use the **Update Settings** action under the **Maintain** button in LCS. This will open a dialog that will allow you to specify the Entity Store configuration. 

## Authoring and distributing reports by using Entity Store on-premises

Entity Store is an operational data warehouse that is included. It lets power users and business analysts author reports that use simplified and enriched data. Entity Store contains aggregate measurements, which are simplified star schemas. For more information about how to author reports by using Entity Store, see [Create analytical reports by using Power BI Desktop](author-distribute-power-bi-reports.md).

Note the following additional steps that are specific to on-premises deployments:

- For on-premises environments, you don't have to use LCS to deploy Power BI reports to production or sandbox environments. Because admins can point PowerBI.com datasets to specific Entity Store databases in on-premises environments, you don't have to use the functionality that LCS offers. However, you might have to configure the on-premises gateway to enable PowerBI.com to access data on-premises. For more information about the gateway, see [Power BI gateway documentation](https://powerbi.microsoft.com/gateway/).
- Although cloud-based application environments support only reports that are authored by using the DirectQuery option, on-premises Entity Store supports both DirectQuery reports and Import mode reports.
- Analytical workspaces aren't yet implemented in on-premises deployments. Instead of viewing reports in analytical workspaces, you can deploy them to PowerBI.com environments. The reports can then be used by users who have access to PowerBI.com. Your users might require appropriate licenses to access reports on PowerBI.com.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

