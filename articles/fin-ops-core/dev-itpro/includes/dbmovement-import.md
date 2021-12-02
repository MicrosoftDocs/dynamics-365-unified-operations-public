To import a database that is prepared from a developer environment to a standard user acceptance test (UAT), or a database previously exported from a UAT environment, follow the steps outlined below:

1. Go to your target sandbox **Environment Details** page, and select the **Maintain** > **Move database** menu option.
2. Select **Import database** and choose your source database backup (.bacpac format) file from the Asset Library.
3. Note the warnings. Review the list of data elements that are cleaned up from the backup file.
4. The import operation will begin immediately.

> [!NOTE]
> All users except the Admin user and other internal service user accounts will be unavailable after import. Therefore, the Admin user can delete or obfuscate data before other users are allowed back into the system.

To import a database to a developer environment after you've downloaded a database backup (.bacpac) file, you can begin the manual import operation on your Tier 1 environment. When you import the database, we recommend that you follow these guidelines:

- Keep a copy of the existing AxDB database, so that you can revert to it later if needed.
- Import the new database under a new name, such as **AxDB\_fromProd**.

To ensure the best performance, copy the \*.bacpac file to the local computer that you're importing from. Download sqlpackage .NET Core for Windows from [Get sqlpackage .NET Core for Windows](/sql/tools/sqlpackage-download#get-sqlpackage-net-core-for-windows). Open a **Command Prompt** window, and run the following commands from the sqlpackage .NET Core folder.

```

SqlPackage.exe /a:import /sf:D:\Exportedbacpac\my.bacpac /tsn:localhost /tdn:<target database name> /p:CommandTimeout=1200
```

Here is an explanation of the parameters:

- **tsn (target server name)** – The name of the Microsoft SQL Server instance to import into.
- **tdn (target database name)** – The name of the database to import into. The database should **not** already exist.
- **sf (source file)** – The path and name of the file to import from.

> [!NOTE]
> During import, the user name and password aren't required. By default, SQL Server uses Microsoft Windows authentication for the user who is currently signed in.

For information about how to complete the manual import operations into a Tier 1 environment, see [Import the database](../database/dbmovement-scenario-exportuat.md#import-the-database).
