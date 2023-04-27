---
title: SysSetup
description: This article describes the SysSetup interface and how to onboard classes to use it.
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

# About SysSetup

SysSetup is an interface that is used to identify the X++ classes that run during Database Synchronization. The X++ classes that implement the SysSetup interface run during the **PostTableAndViewSyncActions** step during Database Synchronization. 

## Onboarding to SysSetup - 
1. From Microsoft Visual Studio, select **View** --> **Application explorer (AOT)**, and then create a new class that implements the **SysSetup** interface. 
2. Add the **loadData()** method in the class. The code in this method is executed during Database Synchronization. (It can also be a reference to another class or method.)
3. Add the [SysSetupConfig](../../dev-itpro/dev-tools/syssetupconfigattribute.md) and SysSetupTable attributes to the class. 
4. SysSetupTable attribute takes the related table as the input. 

```xpp
[
    SysSetupTable(tablestr(DemoTable)),
    SysSetupConfig(true, 300, 1.1)
]
class DemoSetup implements SysSetup
{
    public void loadData()
    {
        <your code here..>
    }
}
```

> [!Note]
> Running Database Synchronization from Visual Studio will not run the SysSetup classes. Refer the below section to run Database Synchronization from the command line. 

## Validating New Classes

1. Open the command prompt. 
2. Run the following command.</br> 
   </br>
   ``` 
   <AOSInstalledDirectory>\AosService\PackagesLocalDirectory\bin\Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "<AOSInstalledDirectory>\AosService\PackagesLocalDirectory" -metadatadir <AOSInstalledDirectory>\AosService\PackagesLocalDirectory -sqluser <sqluser> -sqlserver <sqlservername/localhost> -sqldatabase <axdbname> -setupmode sync -syncmode fullall -isazuresql false -sqlpwd <password> -logfilename "<anydirectory>\dbsync.log"
   ```
   For example.</br>
   </br>
   ```
   <AOSInstalledDirectory>\AosService\PackagesLocalDirectory\bin\Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "K:\AosService\PackagesLocalDirectory" -metadatadir K:\AosService\PackagesLocalDirectory -sqluser <sqluser> -sqlserver localhost -sqldatabase axdb -setupmode sync -syncmode fullall -isazuresql false -sqlpwd <password> -logfilename "K:\temp\dbsync.log"
   ```
3. After the command has executed, check the log file to confirm that the X++ class was picked up and executed during Database Synchronization. You'll see an entry similar to the example below.
```
04/24/2023 09:10:17: SysSetupInstaller: Running Script: DemoSetup with Timeout 300 seconds.
04/24/2023 09:10:17: SysSetupInstaller: Script: DemoSetup, Completed Successfully. Time elapsed: 0:00:00:00.0415237
```
