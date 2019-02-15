---
# required metadata

title: Install BaseX for AppChecker
description: This topic explains how to install and set up BaseX in a developer environment.
author: AndreasHassing
manager: AnnBe
ms.date: 02/13/2019
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

## Prerequisites

BaseX is a Java-based XML document database. It requires a Java Runtime Environment (JRE) of version 8 or later. Before you install BaseX, [verify that a JRE is installed](https://aka.ms/getjava).

## Download BaseX

To download BaseX, go to the [BaseX website](http://basex.org/download/), and download the latest version of the Microsoft Windows installer. Currently, the latest version is 9.1.2.

## Install BaseX

Run the executable file on the developer machine where you will compile your module. For each step, accept the default settings.

> [!TIP]
> If the installation drive doesn't have enough space for your model, you can change the folder for BaseX data later. For more information, see the [BaseX configuration page](http://docs.basex.org/wiki/Configuration#Database_Directory).

## Configure BaseX to handle your model

Depending on the size of your model, BaseX can spend a lot of memory.

By default, BaseX is configured to use a maximum of about 1.17 gigabytes (GB) of random-access memory (RAM). If you have a large model, you should consider increasing this limit by following these steps.

1. Open the batch script at **\<BaseX Install Path\>\\bin\\basex.bat** for editing.
2. Find the line that contains **set BASEX\_JVM=-Xmx1200m %BASEX\_JVM%**, and increase the value after **-Xmx** to, for example, **4g** to let it use 4GB RAM.

    For more information, see [Non-Standard Options](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/java.html#BABHDABI). This section of the Java documentation explains how increase the limits of the Java virtual machine (VM).

    Leave the rest of the script unchanged.

> [!NOTE]
> You do not need to start the BaseX server as AppChecker will use the standalone executable for storage and querying.
