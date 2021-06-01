---
# required metadata

title: Upgrade from AX 2012 - Data upgrade in self-service environments
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: tonyafehr
ms.date: 06/01/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2021-06-30

---

# Upgrade from AX 2012 - Data upgrade in self-service environments

[!include[banner](../includes/banner.md)]

**Prerequisites**

1.  The DotNet core SDK should have been installed. [Click
    here](https://dotnet.microsoft.com/download/dotnet/thank-you/sdk-3.1.409-windows-x64-installer)
    and download the SDK and link to the dotnet core SDK page where you
    can find all flavors - [Download .NET Core 3.1 (Linux, macOS, and
    Windows)
    (microsoft.com)](https://dotnet.microsoft.com/download/dotnet/3.1)

2.  Create a self-service environment in LCS portal and the environment
    should be in deployed state.

3.  The source SQL Server should have the replication feature installed
    and enabled. To check whether replication is enabled, execute the
    following SQL script.

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

-- If @installed is 0, replication must be added to the SQL Server
installation.

USE master;

GO

DECLARE @installed int;

EXEC @installed = sys.sp\_MS\_replication\_installed;

SELECT @installed;

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

If the replication components are not installed, follow the steps
in [Install SQL Server
replication](https://docs.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-replication?view=sql-server-ver15).

1.  Enable and start the SQL Server Agent at source database server.

2. **SA Authentication:** A user should have DB\_Owner privilege in the
    source database and the user should have access to masterDb and
    sourceDb.

3. **Migration tool kit setup:** If you want any of the source database
    tables not to be replicated at the target database, you can specify
    those in IgnoreTables.xml file. Similarly, you can also specify any
    functions that you don't want to be replicated in
    IgnoreFunctions.xml file.

**\*** IgnoreTables.xml file path: **Data\\IgnoreTables.xml**

**\*** IgnoreFunctions.xml file path:
[**Data\\IgnoreFunctions.xml**](file:///\\Data\IgnoreFunctions.xml)

Below is an example of how to specify tables and functions in the xml
files.

![A screenshot of a computer Description automatically generated with low confidence](media/image1.png)

![Graphical user interface  text Description automatically generated](media/image2.png)

> [!WARNING]
> The table and the functions present in these files will not
> be replicated at the target database and the same format should be
> followed.


> [!NOTE]
> At any point of time, if any of the steps fail, please check
> the [Exceptions](#exceptions) section.


# **Configuring Replication**

Before starting the replication process, please note that the status of
the LCS environment will be in "Deployed" state when it is created, as
shown in below figure.

Now, run the "AX2012DataUpgradeToolKit.exe" application. It will open
the console window and re-direct us to the Microsoft login page for
authentication as shown below.

Provide the credentials that are used to login to the lcs portal. Once
the authentication is successful, it shows the below message in the
browser. You can close the tab.

After the authentication is completed, you can see that the command
window waits for the Project-Id input. Give the Project-Id and press
enter. Now, it asks for Environment-Id. Provide it and press enter.

It connects to the LCS environment and validate the connection to the
target database.

> [!NOTE]
> The Project-Id and Environment-Id can be found from the LCS URL
> of the environment as shown in below figure. Environment Id can also be
> found in the Environment Details


Once, the Project-id and Environment-Id validation is successful, it
presents us with a set of options which should be performed step by step
to complete the data replication and upgrade.

**1) Data upgrade preparation: Environment setup activity \[Adding
Source-Database details, Database Firewall IP whitelist & Distribution
database path.\]**

This step will ask for a set of inputs:

1.  Source Database Details:

-Source Server(servername\\\\serverinstance)

-Source Database name

-Username

-password

1.  Source database server IP address for whitelisting

2.  Distributor database path (eg. D:\\SQLServer\\Data)

3.  Replication snapshot path (eg. D:\\SQLServer\\Snapshot)

> [!WARNING]
> The paths specified should have enough space. The
> recommended is minimum to have the size of the source database.


This option does the following.

-   Validates Source Database Connection

-   Validates AX2012 Database version

-   Authorizes the Source IP

-   Validates the target databases.

**2) Data upgrade preparation: Prepare the target environment for the
data upgrade**

This step will change the LCS environment state from **"Deployed"** to
**"Ready for replication"**.

**3) Replication: Cleanup Target Database**

This step does the following actions.

1.  Changes the LCS environment state from **"Ready for replication"**
    to **"Replication in progress" **

2.  Deletes the dbo objects of Tables, Views, Stored Procedures and User
    defined functions at the target database.

**4) Replication: Setup Distributor**

This step will create a distribution database under System Databases at
the source server which is used for replication.

**5) Replication: Setup Publication for Primary Key (PK) Tables**

This step will create publications for Primary Key tables under
Replication folder at the source server and replicate them at the target
database. If there are any ignore-tables specified, then these tables
are exempted from replication and at the same.

Created Publishers -&gt; AXDB\_PUB\_TABLE\_Obj\_\[\*\].

> [!WARNING]
> After this process (replication configuration) is completed,
> actual data replication will happen as a SQL Job and will be running in
> the background. It will take some time to complete. You can check the
> status of the replication by giving the option **'rs**' as shown
> below.


Please refer to the below which shows that the replication is completed.

**6) Replication: Setup Publication for Other Objects (functions)**

Similar to the previous step, this step will create a publication for
Other Objects (functions) and replicate them at the target database. If
you don't want any of the functions to be replicated, you can specify
them in IgnoreFunctions.xml file.

Creates Publisher -&gt; AX\_PUB\_OtherObjects

> [!WARNING]
> It will take some time to complete the replication. Check the
> replication status by giving the option 'rs'. Don't proceed to next
> step, until the "DataReplicationStatus" for this step is marked as
> completed as shown in below figure.


**Note:** If there are no functions to be replicated then publication
will not be created.

**7) Cutover: Setup Publication for Non PK Tables **

This step creates two publications to replicate 1) Non-Primary Key
tables, 2) Locked tables with publication names
-&gt; AX\_PUB\_NoPKTable, AX\_PUB\_TABLE\_LockedTable

- **Locked Tables**: If AX Service acquire a schema lock during the PK
    Publication creation time, those tables will be ignored from the
    publication and will be added into a temporary table and will be
    marked for replicating during cutover publication creation.

> [!WARNING]
> Don't proceed to next step, until the "DataReplicationStatus"
> for this step is shown as completed as shown in below figure.


**8) Cutover: Remove Non PK Publication and Temporary Tables**

This step does the following actions:

1.  Cleans up the temp tables created for no Primary Key tables at the
    source database.

2.  Deletes Publication --&gt; AX\_PUB\_NoPKTable.

**9) Cutover: Create constraint for Non PK tables**

This step extracts constraints for the non PK tables from the source
database and create them at the target database.

**10) Cutover: Remove Replication Setup**

This step will delete all the publications created at the source
database, the distribution database and replication snapshot.

**Note**: If you want to remove the Snapshot folder without exception,
execute the below script in the source database (or) After execution you
will get an exception. This exception can be ignored.

**EXEC** master.dbo.sp\_configure 'show advanced options', 1

RECONFIGURE **WITH** OVERRIDE

**EXEC** master.dbo.sp\_configure 'xp\_cmdshell', 1

RECONFIGURE **WITH** OVERRIDE

**11) Post Replication: Update environment state to replicated. **

This step will change the LCS environment state from **"Replication in
progress"** to **"Replication completed"**.

**12) Data Upgrade: Trigger Upgrade **

This step does the following actions:

1.  During this data upgrade process, it changes the LCS environment
    state from **"Replication completed"** to **"Data upgrade in
    progress"**.

2.  After completion of data upgrade, it changes the LCS environment
    state from **"Data upgrade in progress"** to **"Deployed"**. This
    completes the Data upgrade process.

The status for all the steps in the Data Upgrade process should be
marked as Completed as shown in below figure.

If Data Upgrade fails, you can see that as "**Failed**" in LCS portal
and as "Resume" in menu option status of console app.

Resume the failed step. It changes the LCS environment state to
"**Servicing**"

# **Reporting Section of the Application**

Below are the options available to check the reports of Replication
Status, Data Upgrade Status and Replication Validation.

-   dv) Report: Validate the replication (Compares the number of records
    in the source database Vs target database)

-This option will compare the number of tables and records at the
source and target server databases and display the report. This should
be used only after completion of step 12.

- This report data will be found in the
**output/PostValidationInfo.csv**

-   rs) Report: Get Replication Status

-This option will display the report of the replication process for
the publications created. This should be used only after starting step
3, i.e., during the replication process of any publication.

-   ds) Report: Get DataUpgrade Status

-This option will display the report of the data upgrade process. This
should be used only after starting step 12.

# **Tooling Section of the Application**

-   reset) This will reset the replication setup (removes all the
    replication configuration)

-This will remove all the replication configurations (publications and
distribution database will be deleted.) The menu options status will
be reset from completed to reset mode which helps you to perform the
replication from beginning.

-   reset-all) This will reset all the menu options

-reset option + clear option + All the options will be changed to "Not
Started"

-   clear) Clears the environment setup activity (clearing the cache)

-This will clear all the cache like project-Id, Environment-Id, source
database details. The option 1 status will be changed to "Not Started"

-   help) Display the data upgrade migration

-This will display the menu option status with the updated status.

-   Exit) Exit

# **To Know Replication Configuration & Status (via) SSMS - SQL Server Management Studio** 

-   To know replication feature is available/installed in the server,
    the Object Explorer should have the replication folder as in the
    below screen shot.

-   After the completion of step 3, we should be able to see the
    publisher configured under replication folder.

-   To know the replication status right click on the replication
    folder, and select the Launch Replication Monitor

-   In the monitor screen we can see all the publishers that we have
    created for replication.

-   Selecting the snapshot tab, we can see the status of the snapshot.

-   To view the detail log/transaction double click on the grid item.

-   To view the data replication to the target, select the All
    Subscription tab and double click subscription from the grid item.
    Like in the above screen shot can view the detail logs.

# **Exceptions**

1.  Delete the distribution database if it already exists at the source
    database server by following the below steps.

    1.  Expand the Replications folder in the source database server.
        Right click on the "Local Publications" folder and click on
        Generate Scripts as shown in below figure. This opens a tab
        "Generate SQL Script".

    2.  Select the radio button "To drop or disable the components" and
        select "Open in New Query Window" in the dropdown of Generate
        Script as shown in below figure.

    3.  The above step will open the script in a new query window.
        Execute this script at the source database.

2. **Exception**: After Creating the Publication if the Snapshot
    creation is failing with the below error message:

**Error Message**: Prefetch objects failed for Database
'MicrosoftDynamicsAX'.

**Solution**: Go to Replication launch Monitor, right click on the
failed publication and select on "Generate Snapshot". Wait until it is
completed. You can check the replication status with the option 'rs'.
Please refer below screenshot for reference.
