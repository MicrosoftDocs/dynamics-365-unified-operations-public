---
# required metadata

title: Project migration manager
description: This article explains how to use the Project Migration Manager to move your project from one Lifecycle Services geography to another.
author: LaneSwenka
ms.date: 09/08/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form:
# ROBOTS:
audience: IT Pro, Developer
# ms.devlang:
ms.reviewer: sericks
# ms.tgt_pltfrm:
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry:
ms.author: laswenka
ms.search.validFrom: 2016-09-30
ms.dyn365.ops.version: AX 7.0.0

---

# Project migration manager

[!include [banner](../includes/banner.md)]

The Lifecycle Services (LCS) project migration manager utility allows customers to move their project data from one geography to another geography that LCS supports.  In this article, we will describe the terminology, the supported scenarios, and also cover some frequently asked questions around this functionality.

## Why move geographies?
First and foremost is understanding why you might want to move your LCS project from one "geo" or geography to another.  Originally, LCS only supported a single instance - https://lcs.dynamics.com/ - which was the global endpoint for all customers.  With the recent regulatory requirement trend across the industry for customers and software vendors to keep data within a geographic boundary, LCS has started to deploy geographic-specific instances of LCS so that customers can have all of their project data in a desired location.

With this capability, you can now move your project from one geographic location to another that meets your requirements.  There are some limitations in terms of all of the data that is automatically transferred which we will cover below.  

## What data is transferrable and how?
The following data is transferreable between instances, using the actions below.

|Migration method| Project types| Capabilities|
|----------------|--------------|-------------|
|Automated| Cloud implementation project, on-premise implementation project, partner projects| Business process modeler<br/>Methodologies<br/>Project onboarding<br/>Project settings<br/>Support</br>Work Items<br/>|
|Manual migration| Cloud implementation project, on-premise project, partner project| Asset library<br/>Commerce<br/>Self-service environments(support ticket)<br/>Cloud-hosted environments (CHE)<br/>|
|Not supported| All | Configuration and Data Manager (CDM)<br/>Sharepoint Online integration<br/>System diagnostics<br/>Upgrade analysis<br/>Globalization<br/>Code upgrade<br/>Translation service<br/>Non-project features|

## Start your project migration
To start your project migration, use the navigation menu and select **Project migration manager**.

1. Use the **Add** button to start a new migration request.
2. In the Schedule Migration slider, choose a **target geo** that meets your specifications.
3. Choose a **migration start time** which is in the future. This will begin the migration for your project and several aspects of the project will become read-only.
4. Click the checkbox to agree to the terms and continue.

## Frequently asked questions (FAQ)
Below are several common questions that we would like to answer.  

### Question 1
Answer 1

### Question 2
Answer 2

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
