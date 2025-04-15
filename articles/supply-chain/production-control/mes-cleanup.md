---
title: Cleanup functionality third-party manufacturing execution systems
description: Learn how you can set up cleanup job for message processor
author: juhnkim
ms.author: juhnkim
ms.topic: how-to
ms.date: 04/16/2025
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form: SysMessageQueueSetup, DiagnosticsValidationRule, ProcessScheduleSeries
---

# Cleanup functionality third-party manufacturing execution systems

## Functionality Description

### Optimization Advisor

A new diagnostic rule has been added to [Optimization Advisor](../../fin-ops-core/fin-ops/sysadmin/optimization-advisor-overview.md) called '***Check for aged processed or cancelled messages***'. 

By default, this rule runs on a monthly basis, detecting processed or cancelled messages older than a specified number of days. When the system identifies an old message, it creates a new opportunity with details about the number of processed or cancelled messages found. By clicking '***Take action***', users are redirected to the message queue setup form.

### Process Automation
In [Process Automation](../../fin-ops-core/fin-ops/sysadmin/process-automation.md), a background task named '***Cleanup job for the message processor***'.  By default, this task runs daily but can be modified according to user preferences. A batch job is created to execute the cleanup, deleting messages based on the setup in the message queue setup form.


## Setup message cleanup
To get started a setup in the message queue setup form needs to be created. Specifying the details for each queue that needs to be cleaned up.

There are two new fields that are added to this form:
* Days before processed message deletion - Number of days before processed messages will be deleted.
* Days before cancelled message deletion - Number of days before cancelled messages will be deleted. 

These fields have a default value of '0', meaning no cleanup will occur if the default value is set.

Once the setup is complete for a message queue, a background task can be initialized in Process Automation. Click on **Initialize process automation** to initialize a background task. 

When the background task is created, the system automatically creates a batch job to start processing the cleanup functionality for messages.



