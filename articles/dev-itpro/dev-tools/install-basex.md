---
# required metadata

title: Install BaseX for AppChecker
description: This topic explains how to install and set up BaseX in a developer environment.
author: AndreasHassing
manager: AnnBe
ms.date: 02/20/2019
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

If you are working in a developer environment without administrator privileges, please consider the additional instructions in each step for this scenario.

## Prerequisites

# [Administrator](#tab/admin)

BaseX is a Java-based XML document database. It requires a Java Runtime Environment (JRE) of version 8 or later. Before you install BaseX, [verify that a JRE is installed](https://aka.ms/getjava).

# [Low privilege](#tab/low-privilege)

Download Java **Server JRE** from the [Java download page](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

Java Server JRE is downloaded as a `.tar.gz` compressed archive that you will need to extract. You can use [7zip](https://www.7-zip.org/download.html) which can be downloaded without installation [at SourceForge](https://sourceforge.net/projects/sevenzip/files/7-Zip/9.20/7za920.zip/download).

To extract Java Server JRE binaries from the archive, run PowerShell commands like (change depending on which version of the Server JRE archive you downloaded):

```powershell
.\7za.exe x .\server-jre-8u202-windows-x64.tar.gz # decompresses to current working directory
.\7za.exe x .\server-jre-8u202-windows-x64.tar # extracts jdk1.8.0_202 to current working directory
```

Assuming `7za.exe` and the archive are located in the current working directory.

Add a pointer in the path environment variable to the Java bin path from a PowerShell prompt, this is needed for BaseX to run:

```powershell
[Environment]::SetEnvironmentVariable(
    "Path",
    # replace <path_to_jdk> below with the absolute path from the extracted jdk above
    [Environment]::GetEnvironmentVariable("Path", [EnvironmentVariableTarget]::User) + ";<path_to_jdk>\bin\",
    [EnvironmentVariableTarget]::User)
```

## Download BaseX

# [Administrator](#tab/admin)

To download BaseX, go to the [BaseX website](http://basex.org/download/), and download the latest version as a Microsoft Windows installer. Currently, the latest version is 9.1.2.

# [Low privilege](#tab/low-privilege)

To download BaseX, go to the [BaseX website](http://basex.org/download/), and download the latest version as a zip package. Currently, the latest version is 9.1.2.

## Install BaseX

Run the executable file on the developer machine where you will compile your module. For each step, accept the default settings.

> [!TIP]
> If the installation drive doesn't have enough space for your model, you can change the folder for BaseX data later. For more information, see [BaseX configuration](http://docs.basex.org/wiki/Configuration#Database_Directory).

## Configure BaseX to handle your model

Depending on the size of your model, BaseX can use a lot of memory.

By default, BaseX is configured to use a maximum of about 1.17 gigabytes (GB) of random-access memory (RAM). If you have a large model, you should consider increasing this limit by following these steps.

1. Open the batch script at **\<BaseX Install Path\>\\bin\\basex.bat** for editing.
2. Find the line that contains **set BASEX\_JVM=-Xmx1200m %BASEX\_JVM%**, and increase the value after **-Xmx** to, for example, **4g** to let it use 4 GB RAM.

    For more information, see [Non-Standard Options](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/java.html#BABHDABI). This section of the Java documentation explains how to increase the limits of the Java virtual machine (VM).

    Leave the rest of the script unchanged.

> [!NOTE]
> You do not need to start the BaseX server as AppChecker will use the standalone executable for storage and querying.
