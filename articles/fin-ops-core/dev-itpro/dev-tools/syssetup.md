---
title: SysSetup
description: This article describes the SysSetup interface and explains how to onboard classes to use it.
author: najaidee
ms.date: 04/24/2023
ms.topic: article
audience: Developer
ms.reviewer: 
ms.search.region: Global
ms.author: najaidee
ms.search.validFrom: 2021-10-26
ms.dyn365.ops.version: AX 10.0.0
---

# SysSetup

SysSetup is an interface that's used to identify the X++ classes that run during database synchronization. The X++ classes that implement the SysSetup interface run during the **PostTableAndViewSyncActions** step of database synchronization.

## Onboard to SysSetup

1. In Microsoft Visual Studio, select **View** \> **Application explorer (AOT)**.
2. Create a new class that implements the **SysSetup** interface.
3. Add the **loadData()** method in the class. The code in this method is run during database synchronization. (The code can also be a reference to another class or method.)
4. Add the [**SysSetupConfig**](../../dev-itpro/dev-tools/syssetupconfigattribute.md) and **SysSetupTable** attributes to the class. The **SysSetupTable** attribute takes the related table as the input.

The completed class should resemble the following example.

```xpp
[
    SysSetupTable(tablestr(DemoTable)),
    SysSetupConfig(true, 300, 1.1)
]
class DemoSetup implements SysSetup
{
    public void loadData()
    {
        <your code here...>
    }
}
```

> [!NOTE]
> If you run database synchronization from Visual Studio, the SysSetup classes won't be run. For information about how to run database synchronization from the command line, see the next section.

## Validate new classes

1. Open a Command Prompt window.
2. Run the following command.

    ``` text
    <AOSInstalledDirectory>\AosService\PackagesLocalDirectory\bin\Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "<AOSInstalledDirectory>\AosService\PackagesLocalDirectory" -metadatadir <AOSInstalledDirectory>\AosService\PackagesLocalDirectory -sqluser <sqluser> -sqlserver <sqlservername/localhost> -sqldatabase <axdbname> -setupmode sync -syncmode fullall -isazuresql false -sqlpwd <password> -logfilename "<anydirectory>\dbsync.log"
    ```

    Here's an example.

    ``` text
    K:\AosService\PackagesLocalDirectory\bin\Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "K:\AosService\PackagesLocalDirectory" -metadatadir K:\AosService\PackagesLocalDirectory -sqluser <sqluser> -sqlserver localhost -sqldatabase axdb -setupmode sync -syncmode fullall -isazuresql false -sqlpwd <password> -logfilename "K:\temp\dbsync.log"
    ```

3. When the command has finished running, review the log file to confirm that the X++ class was picked up and run during database synchronization. You'll see an entry that resembles the following example.

    ``` text
    04/24/2023 09:10:17: SysSetupInstaller: Running Script: DemoSetup with Timeout 300 seconds.
    04/24/2023 09:10:17: SysSetupInstaller: Script: DemoSetup, Completed Successfully. Time elapsed: 0:00:00:00.0415237
    ```
