---
# required metadata

title: Preview features in Dynamics 365 for Retail version 10.0.5
description: This topic describes features that are in preview in Dynamics 365 for Retail. 
author: josaw1
manager: AnnBe
ms.date: 08/2/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope:  Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2019-08-02
ms.dyn365.ops.version: Release 10.0.5

---
# What's new or changed in Dynamics 365 for Retail version 10.0.5

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

This topic describes features that are new or changed in Microsoft Dynamics 365 for Retail in 10.0.5. 

To learn about the features in Microsoft Dynamics 365 for Finance and Operations, see [Preview features in Finance and Operations version 10.0.5 (September 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-5).

## Test recorder and Regression suite automation tool for Retail Cloud POS:

  
### Test Recorder:

Test recorder is a new feature added in POS to significantly reduces the time and cost of user acceptance testing. User acceptance testing is typically required before taking a Microsoft application update or applying custom code and configurations to your Retail POS production environments. Test recorder can record user actions in the client with exact fidelity for all the controls and DOM elements in POS, test recorder captures the event occurred and stores along all pertinent information about the corresponding user action in real time. From this information, test recorder can capture the type of user action (such as a button click, value entry, or navigation) and any data that is related to the user action (such as the input data value and type, view context, or record context etc.) expect the password information. Test recorder persists all the recorder information in memory during the recording and generate output file at the end of the recording with enough detail to help playback later using the RSAT tool exactly as the user performed them. 

Note: Test recorder is supported only in Cloud POS using Chrome browser, support for another browser and device type will be added later.

### Regression Suite Automation Tool:
The Regression Suite Automation Tool (RSAT) enables functional power users to execute the test case in Retail POS and updates the test execution result back in Azure DevOps for reporting and investigation. RSAT provides options to investigate the test failures. RSAT decouples the test parameters from test steps and stores the parameters in Microsoft Excel files for easy editing of the test parameter values. The RSAT tool is now updated with new Retail POS tab to specify the Retail specific settings to playback Retail POS recording and generation of retail parameters and variable file.



## Additional resources

### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/en-us/dynamics365-release-plan/2019wave2/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.
