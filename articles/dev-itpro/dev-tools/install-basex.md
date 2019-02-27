---
# required metadata

title: Install BaseX for AppChecker
description: This topic explains how to install and set up BaseX in a developer environment.
author: AndreasHassing
manager: AnnBe
ms.date: 02/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anniels
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Platform update 25

---

# Install BaseX for AppChecker

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

AppChecker depends on a installation of BaseX to store and query abstract syntax trees that the X++ compiler generates. This topic explains how to install and set up BaseX in a developer environment.

The sections of this topic should be completed in the order that they appear.

If you are working in a developer environment without administrator privileges, follow the non-administrator instructions.

## Prerequisites

BaseX is a Java-based XML document database. It requires a Java Runtime Environment (JRE) of version 8 or later. Before you install BaseX, verify that a JRE is installed.

# [Admin: install Java](#tab/admin)

Download and install Java JRE from the [Java download page](https://aka.ms/getjava).

# [Non-admin: set up Java](#tab/admin)

Download Java **Server JRE** from the [Java download page](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

Java Server JRE is downloaded as a `.tar.gz` compressed archive that you will need to extract. You can use [7zip](https://www.7-zip.org/download.html) which can be downloaded without installation at [SourceForge](https://sourceforge.net/projects/sevenzip/files/7-Zip/9.20/7za920.zip/download).

To extract Java Server JRE binaries from the archive, run PowerShell commands similar to the following:

> [!NOTE]
> Change the command based on the version of the Server JRE archive you downloaded.

```powershell
.\7za.exe x .\server-jre-8u202-windows-x64.tar.gz # decompresses to current working directory
.\7za.exe x .\server-jre-8u202-windows-x64.tar # extracts jdk1.8.0_202 to current working directory
```

Assuming `7za.exe` and the archive are located in the current working directory.

After extracting Java, modify and run the following PowerShell script to add the Java bin folder to your **PATH** environment variable:

```powershell
[Environment]::SetEnvironmentVariable(
    "Path",
    # replace <path_to_jdk> below with the absolute path from the extracted jdk above
    [Environment]::GetEnvironmentVariable("Path", [EnvironmentVariableTarget]::User) + ";<path_to_jdk>\bin\",
    [EnvironmentVariableTarget]::User)
```

---

## Download BaseX

To download BaseX, go to the [BaseX website](http://basex.org/download/), and download the latest version.

### Admin: Download BaseX

Download the Microsoft Windows installer from the download page.

### Non-admin: Download BaseX 

Download the zip package from the download page.  Currently, the latest version is 9.1.2.

## Install BaseX

### Admin: Install BaseX

Run the executable file on the developer machine where you will compile your module. For each step, accept the default settings.

### Non-admin: Set up BaseX

Extract the previously downloaded BaseX zip package.

> [!TIP]
> If the installation drive doesn't have enough space for your model, you can change the folder for BaseX data later. For more information, see [BaseX configuration](http://docs.basex.org/wiki/Configuration#Database_Directory).

After installing BaseX, modify and run the following PowerShell script to add the BaseX bin folder to your **PATH** environment variable:

```powershell
[Environment]::SetEnvironmentVariable(
    "Path",
    # replace <path_to_basex> below with the absolute path from the extracted basex zip package above
    [Environment]::GetEnvironmentVariable("Path", [EnvironmentVariableTarget]::User) + ";<path_to_basex>\bin\",
    [EnvironmentVariableTarget]::User)
```

> [!IMPORTANT]
> You will need to restart Visual Studio if you had it open while setting the PATH environment variable.

## Configure BaseX to handle your model

Depending on the size of your model, BaseX can use a lot of memory.

By default, BaseX is configured to use a maximum of about 1.17 gigabytes (GB) of random-access memory (RAM). If you have a large model, you should consider increasing this limit by following these steps.

1. Open the batch script at **\<BaseX Install Path\>\\bin\\basex.bat** for editing.
2. Find the line that contains **set BASEX\_JVM=-Xmx1200m %BASEX\_JVM%**, and increase the value after **-Xmx** to, for example, **4g** to let it use 4 GB RAM.

    For more information, see [Non-Standard Options](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/java.html#BABHDABI). This section of the Java documentation explains how to increase the limits of the Java virtual machine (VM).

    Leave the rest of the script unchanged.

> [!NOTE]
> You do not need to start the BaseX server as AppChecker will use the standalone executable for storage and querying.
