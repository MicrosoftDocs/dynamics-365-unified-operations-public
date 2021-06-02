---
# required metadata

title: Upgrade from AX 2012 - Data upgrade in self-service environments
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: sarvanisathish
ms.date: 06/02/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2021-06-30

---

# Upgrade from AX 2012 - Data upgrade in self-service environments

[!include[banner](../includes/banner.md)]

## Prerequisites

1.  The [.NET core SDK](https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-3.1.409-windows-x64-installer) is not installed, download and install it.

2.  Create a self-service environment in Lifecycle Services (LCS). The environment should be in deployed state.

3.  The source SQL Server should have the replication feature installed and enabled. To check whether replication is enabled, execute the following SQL script.

    ```sql
    -- If @installed is 0, replication must be added to the SQL Server installation.

    USE master;

    GO

    DECLARE @installed int;

    EXEC @installed = sys.sp\_MS\_replication\_installed;

    SELECT @installed;
    ```

    If the replication components are not installed, follow the steps in [Install SQL Server replication](/sql/database-engine/install-windows/install-sql-server-replication?view=sql-server-ver15).

4.  Enable and start the SQL Server Agent at source database server.

    > [!Note]
    > A user should have DB\_Owner privilege in the source database and the user should have access to the master database and source database.

5. **Migration tool kit setup:** If you want any of the source database tables not to be replicated at the target database, you can specify those in IgnoreTables.xml file. Similarly, you can also specify any functions that you don't want to be replicated in IgnoreFunctions.xml file.

    - **IgnoreTables.xml file path**: Data\\IgnoreTables.xml

    - **IgnoreFunctions.xml file path**: Data\\IgnoreFunctions.xml

    Below is an example of how to specify tables and functions in the xml files.
    
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <IgnoreTables>
        <Name>
            <Table>USERADDHISTORYLIST</Table>
            <Table>TAXRECONCILIATIONREPORTTMP</Table>
            <Table>CASELOG</Table>
            <Table>SHAREDCATEGORYROLETYPE</Table>
            <Table>VATCSREPORTXMLATTRIBUTE_CZ</Table>
        </Name>
    </IgnoreTables>

    <?xml version="1.0" encoding="utf-8"?>
    <IgnoreFunctions>
        <Name>
            <Function>if_WHSInventReserveUnionDelta</Function>
        </Name>
    </IgnoreFunctions>  
    ```
    
> [!Warning]
> The table and the functions present in these files will not be replicated at the target database and the same format should be followed.

> [!NOTE]
> At any point of time, if any of the steps fail, please check the [Exceptions](#exceptions) section.

## Configuring replication

Before starting the replication process, note that the status of the LCS environment will be in **Deployed** state when it is created.

Run the **AX2012DataUpgradeToolKit.exe** application. It will open the console window and redirect to the Microsoft login page for authentication. Provide the credentials that are used to login to LCS. Once the authentication is successful, the following message is displayed in the broswer: *Authentication complete. You can return to the application. Feel free to close this broswer tab.* You can then close the tab.

After the authentication is completed, the command window waits for the Project-Id input. Provide the Project-Id and press enter. Then, provide the Environment-Id and press Enter.

It connects to the LCS environment and validates the connection to the target database.

> [!NOTE]
> The Project-Id and Environment-Id can be found in LCS on the **Manage enviornment** page. The Environment-Id can also be found in the **Environment details** page.

After the Project-Id and Environment-Id validation is successful, it presents a set of options which should be performed step-by-step to complete the data replication and upgrade.

1. **Data upgrade preparation: Environment setup activity** 

    This step will ask for a set of inputs:

    - Source database details:
        - Source server (servername\serverinstance)
        - Source database name
        - Username
        - Password
    - Source database server IP address for whitelisting
    - Distribution database path (eg. D:\SQLServer\Data)
    - Replication snapshot path (eg. D:\SQLServer\Snapshot)

    > [!Warning]
    > The paths specified should have enough space. The recommended is minimum to have the size of the source database.

    This option does the following.

    - Validates source database connection.
    - Validates AX 2012 database version.
    - Authorizes the Source IP.
    - Validates the target databases.

2. **Data upgrade preparation: Prepare the target environment for the data upgrade**

    This step will change the LCS environment state from **Deployed** to **Ready for replication**.

3. **Replication: Clean-up target database**

    This step does the following actions:

    1. Changes the LCS environment state from **Ready for replication** to **Replication in progress**.

    2. Deletes the dbo objects of tables, views, stored procedures, and user-defined functions at the target database.

4. **Replication: Set up distributor**

    This step will create a distribution database under System Databases at the source server which is used for replication.

5. **Replication: Set up publication for primary key tables**

    This step will create publications for primary key tables under the **Replication** folder at the source server, and replicate them at the target database. If there are any ignore-tables specified, then these tables are exempted from replication and at the same.

    Created Publishers -&gt; AXDB\_PUB\_TABLE\_Obj\_\[\*\].

    > [!WARNING]
    > After this process (replication configuration) is completed, actual data replication will happen as a SQL job and will be running in the background. It will take some time to complete. You can check the status of the replication by giving the option **'rs**'.

6. **Replication: Set up publication for other objects (functions)**

    Similar to the previous step, this step will create a publication for other objects (functions) and replicate them at the target database. If you don't want any of the functions to be replicated, you can specify them in IgnoreFunctions.xml file.

    Creates Publisher -&gt; AX\_PUB\_OtherObjects

    > [!WARNING]
    > It will take some time to complete the replication. Check the replication status by giving the option **'rs'**. Don't proceed to next step, until the "DataReplicationStatus" for this step is marked as completed.

    > [!Note]
    > If there are no functions to be replicated then publication will not be created.

7. **Cutover: Set up publication for non-primary key tables**

    This step creates two publications to replicate 1.) non-primary key tables, 2.) ;ocked tables with publication names -&gt; AX\_PUB\_NoPKTable, AX\_PUB\_TABLE\_LockedTable

    If AX Service acquire a schema lock during the primary key publication creation time, those tables will be ignored from the publication and will be added into a temporary table and will be marked for replicating during cutover publication creation.

    > [!WARNING]
    > Don't proceed to next step, until the "DataReplicationStatus" for this step is shown as completed.

8. **Cutover: Remove non-primary key publication and temporary tables**

    This step does the following actions:

    1. Cleans up the temp tables created for non-primary key tables at the source database.

    2. Deletes publication --&gt; AX\_PUB\_NoPKTable.

9. **Cutover: Create constraint for non-primary key tables**

    This step extracts constraints for the non-primary key tables from the source database and create them at the target database.

10. **Cutover: Remove replication setup**

    This step will delete all the publications created at the source database, the distribution database, and replication snapshot.

    > [!Note]
    > If you want to remove the **Snapshot** folder without exception, execute the below script in the source database, or after execution you will get an exception. This exception can be ignored.

    ```sql
    **EXEC** master.dbo.sp\_configure 'show advanced options', 1

    RECONFIGURE **WITH** OVERRIDE

    **EXEC** master.dbo.sp\_configure 'xp\_cmdshell', 1

    RECONFIGURE **WITH** OVERRIDE
    ```
    
11. **Post-replication: Update environment state to Replicated**

    This step will change the LCS environment state from **Replication in progress** to **Replication completed**.

12. **Data Upgrade: Trigger upgrade**

    This step does the following actions:

    1. During this data upgrade process, it changes the LCS environment state from **Replication completed** to **Data upgrade in progress**.

    2. After completion of data upgrade, it changes the LCS environment state from **Data upgrade in progress** to **Deployed**. This completes the data upgrade process.

The status for all the steps in the data upgrade process should be marked as completed.

If data upgrade fails, you can see that as **Failed** in LCS, and as "Resume" in menu option status of console app.

Resume the failed step. It changes the LCS environment state to **Servicing**.

## Reporting section of the application

Below are the options available to check the reports of Replication Status, Data Upgrade Status, and Replication Validation.

-   dv) Report: Validate the replication (Compares the number of records in the source database Vs target database)

-This option will compare the number of tables and records at the source and target server databases and display the report. This should be used only after completion of step 12.

- This report data will be found in the **output/PostValidationInfo.csv**

-   rs) Report: Get Replication Status

-This option will display the report of the replication process for the publications created. This should be used only after starting step 3, i.e., during the replication process of any publication.

-   ds) Report: Get DataUpgrade Status

-This option will display the report of the data upgrade process. This should be used only after starting step 12.

## Tooling section of the application

- **Reset**: This will reset the replication setup (removes all the replication configuration).

    This will remove all the replication configurations (publications and distribution database will be deleted). The menu options status will be reset from completed to reset mode which helps you to perform the replication from beginning.

- **Reset-all**: This will reset all the menu options

    **Reset** option + **Clear** option + All the options will be changed to "Not Started".

- **Clear**: Clears the environment setup activity (clearing the cache).

    This will clear all the cache like project-Id, Environment-Id, source database details. The option 1 status will be changed to "Not Started".

- **Help**: Display the data upgrade migration.

    This will display the menu option status with the updated status.

- **Exit**: Exit

## To know replication configuration and status via SQL Server Management Studio(SSMS)

- To know replication feature is available/installed in the server, the Object Explorer should have the Replication folder.

- After the completion of step 3, we should be able to see the publisher configured under Replication folder.

- To know the replication status, right-click the Replication folder and select **Launch Replication Monitor**.

- In the monitor screen we can see all the publishers that we have created for replication.

- Selecting the **Snapshot** tab, we can see the status of the snapshot.

- To view the detail log/transaction, double-click on the grid item.

- To view the data replication to the target, select the **All Subscription** tab and double-click subscription from the grid item.

## Exceptions

1.  Delete the distribution database if it already exists at the source database server by following the below steps.

    1.  Expand the **Replication** folder in the source database server. Right-click the **Local Publications** folder and select **Generate Scripts**. 
    
        This opens a tab called **Generate SQL Script**.

    2.  Select the **To drop or disable the components** option and select **Open in New Query Window** from the **Generate Script** drop-down list.

    3.  The above step will open the script in a new query window. Execute this script at the source database.

2. **Exception**: After Creating the Publication if the Snapshot creation is failing with the below error message:

    **Error Message**: Prefetch objects failed for Database 'MicrosoftDynamicsAX'.

    **Solution**: Go to Replication launch Monitor, right-click on the failed publication and select on "Generate Snapshot". Wait until it is completed. You can check the replication status with the option 'rs'.
