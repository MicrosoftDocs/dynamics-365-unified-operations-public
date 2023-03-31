--- 
# required metadata 
 
title: Set up electronic signatures
description: Use this procedure to set up electronic signatures. 
author: maertenm
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysConfiguration, SIGParameters, SIGReasonCode, SIGProcSetup   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up electronic signatures

[!include [banner](../../includes/banner.md)]

Use this procedure to set up electronic signatures. An electronic signature confirms the identity of a person who is about to start or approve a computing process. The demo data company used to create this procedure is DAT.


## Enable the Electronic signature configuration key
1. Go to System administration > Setup > License configuration.
2. In the tree, expand 'Administration'.
    * Verify that the Electronic signature check box is selected.  
    * If the Electronic signature check box is not selected, you must enable maintenance mode. Maintenance mode can be enabled in this environment by running a maintenance job from Lifecycle Services, or by using the Deployment.Setup tool locally.  
3. Close the page.

## Set up electronic signature parameters
1. Go to Organization administration > Setup > Electronic signature > Electronic signature parameters.
2. Click Edit.
3. In the Notice field, type a value.
    * Enter the notice that signers will receive when a signature is requested. You can enter any text. Typically, this text tells the user what it means to sign a document electronically.  
    * If you want to enter the Notice text in additional languages, click the Translations button.  
4. Click Save.
5. Close the page.

## Set up reason codes for electronic signatures
1. Go to Organization administration > Setup > Electronic signature > Electronic signature reason codes.
2. Click New.
    * You must set up reason codes before using electronic signatures. A valid reason code is required when signing a document.     A signer selects a reason code to indicate the purpose of an electronic signature. For example, a reason code could be used to indicate legal approval.  
3. In the Reason code field, type a value.
4. In the Description field, type a value.
    * Enter additional reason codes, if needed.  
5. Click Save.
6. Close the page.

## Require electronic signatures for existing processes
1. Go to Organization administration > Setup > Electronic signature > Electronic signature requirements.
2. In the list, find and select the desired record.
    * Select a process that requires electronic signatures.  
3. Select or clear the Signature required check box.
    * Repeat these steps for each process that requires electronic signatures.  
4. Click Save.

## Create a custom requirement for electronic signatures
1. Click New.
2. Select or clear the Signature required check box.
3. In the Name field, enter a name for the process that requires electronic signatures.
4. In the Table name field, click the drop-down button to open the lookup.
5. In the list, find and select the table where the data that must be signed is stored.
6. In the list, click the link in the selected row.
7. In the Field name field, click the drop-down button to open the lookup.
8. In the list, find and select the field in the table that you want to monitor.
9. In the list, click the link in the selected row.
    * Specify when a signature is required.     Select Always if a signature is required when the data in the field changes.     Select Only if a signature is required only under certain conditions. If you select Only, you must also select one of the following options: When a record is inserted, When a record is updated, or When a record is deleted.  
10. Click Save.
11. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]