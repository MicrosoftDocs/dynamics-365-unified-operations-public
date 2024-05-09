---
title: Metadata Explorer
description: Learn about Metadata Explorer and to search metadata
author: pvillads
ms.author: pvillads
ms.date: 05/06/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Metadata Explorer

In this release, we have introduced a new and exciting way to search over the metadata. We have heard from our customers that it has been painful to search over metadata from the Application Explorer, and that it did not always provide the options needed. The new version is both fast and flexible, and it complements the existing search functionality in the Application Explorer.

You will find the new tool under the Metadata Search menu item in the Dynamics 365 menu. It opens a tool window, that you can position anywhere you like. This is what it looks like:

![A screenshot of a computer Description automatically generated](media/enter-query.png)

Let's give it a spin. Say that I an interested in finding out more about how the Batch jobs work. I enter BatchJob in the search field above:

![A screenshot of a computer program Description automatically generated](media/batchjob.png)

You should see a flurry of information as you enter the keystrokes making up the search item. I told you it was fast!

There are lots of things called BatchJob, obviously. Near the top of the list is the form and the table as you can see from the URL listed below the Name and model information. If you click on anything in the list it will open that artifact for perusal. You can also right-click on individual items and add the designated artifact to an existing or new project. As a bonus item, you can copy that URL into the browser, and it will open the artifact inside Visual Studio, or send it in an email to your coworker.

Let us use the dropdown arrow at the extreme right of the search field. You will see this:

![A screenshot of a computer Description automatically generated](media/filter.png)

This works in the same way as the other metadata search tool situated in the Application Explorer. Let us try to find BatchJob things that are tables in the ApplicationPlatform package:

![A screenshot of a computer program Description automatically generated](media/tables.png)

Great. But let's say that we wanted to know which tables are obsolete in all out packages. For this we need to filter on properties. The table has a property that shows whether it is obsolete or not, so we will use that property in the filter:

![A screenshot of a computer program Description automatically generated](media/property-filter.png)

You can inspect any of these in the properties window and check that they are, in fact, obsolete.

But there's more! Let's say I wanted to find a particular code snippet. I would really like to find any usage if the LeaseGroup lease details in obsolete tables:

![A screenshot of a computer Description automatically generated](media/lease.png)

We hope you will find the new tool useful. Let us know if there is anything missing that you would like us to implement.
