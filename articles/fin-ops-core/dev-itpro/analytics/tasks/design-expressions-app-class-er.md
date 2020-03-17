--- 
# required metadata 
 
title: Design ER expressions to call application class methods
description: This guide provides information about how to reuse the existing application logic in Electronic reporting (ER) configurations by calling required methods of application classes in ER expressions. 
author: NickSelin
manager: AnnBe 
ms.date: 12/12/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---
# Design ER expressions to call application class methods

[!include [banner](../../includes/banner.md)]

This guide provides information about how to reuse the existing application logic in Electronic reporting (ER) configurations by calling required methods of application classes in ER expressions. Values of arguments for calling classes can be defined dynamically at run-time: for example, based on information in the parsing document to ensure its correctness. In this guide, you will create the required ER configurations for the sample company, Litware, Inc. This procedure is created for users with the assigned role of System administrator or Electronic reporting developer. 

These steps can be completed using any data set. You must also download and save the following file locally: (https://go.microsoft.com/fwlink/?linkid=862266): SampleIncomingMessage.txt.

To complete these steps, you must first complete the steps in the procedure, "ER Create a configuration provider and mark it as active."

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Verify that the configuration provider for sample company, Litware, Inc. is available and marked as active. If you don't see this configuration provider, you must first complete the steps in the procedure, "Create a configuration provider and mark it as active".   
    * Uou are designing a process for parsing incoming bank statements for an application data update. You will receive the incoming bank statements as TXT files that contain IBAN codes. As part of the bank statement import process, you need to validate the correctness of this IBAN codes using the logic that is already available.   

## Import a new ER model configuration
1. In the list, find and select the desired record.
    * Select the Microsoft provider tile.  
2. Click Repositories.
3. Click Show filters.
4. Add a filter field 'Type name'. In the Name field, enter the value "resources", select the "contains" filter operator, and then click Apply.
5. Click Open.
6. In the tree, select 'Payment model'.
    * If the Import button on the Versions FastTab is not enabled, you have already imported the version 1 one of the ER configuration 'Payment model'. You can skip the rest steps in this sub-task.   
7. Click Import.
8. Click Yes.
9. Close the page.
10. Close the page.

## Add a new ER format configuration
1. Click Reporting configurations.
    * Add a new ER format to parse incoming bank statements in TXT format.  
2. In the tree, select 'Payment model'.
3. Click Create configuration to open the dialog menu.
4. In the New field, enter 'Format based on data model PaymentModel'.
5. In the Name field, type 'Bank statement import format (sample)'.
    * Bank statement import format (sample)  
6. Select Yes in the Supports data import field.
7. Click Create configuration.

## Design the ER format configuration - format
1. Click Designer.
    * The designed format represents the expected structure of the external file in TXT format.  
2. Click Add root to open the dialog menu.
3. In the tree, select 'Text\Sequence'.
4. In the Name field, type 'Root'.
    * Root  
5. In the Special characters field, select 'New line - Windows (CR LF)'.
    * The option 'New line - Windows (CR LF)' has been selected in the 'Special characters' field. Based on this setting, each line in the parsing file is considered a separate record.  
6. Click OK.
7. Click Add to open the drop dialog.
8. In the tree, select 'Text\Sequence'.
9. In the Name field, type 'Rows'.
    * Rows  
10. In the Multiplicity field, select 'One many'.
    * The option 'One many' has been selected in the 'Multiplicity' field. Based on this setting, it is expected that at least one line will be presented in the parsing file.  
11. Click OK.
12. In the tree, select 'Root\Rows'.
13. Click Add Sequence.
14. In the Name field, type 'Fields'.
    * Fields  
15. In the Multiplicity field, select 'Exactly one'.
16. Click OK.
17. In the tree, select 'Root\Rows\Fields'.
18. Click Add to open the drop dialog.
19. In the tree, select 'Text\String'.
20. In the Name field, type 'IBAN'.
    * IBAN  
21. Click OK.
    * It has been configured that each line in the parsing file contains the only IBAN code.  
22. Click Save.

## Design the ER format configuration – mapping to data model
1. Click Map format to model.
2. Click New.
3. In the Definition field, type 'BankToCustomerDebitCreditNotificationInitiation'.
    * BankToCustomerDebitCreditNotificationInitiation  
4. ResolveChanges the Definition.
5. In the Name field, type 'Mapping to data model'.
    * Mapping to data model  
6. Click Save.
7. Click Designer.
8. In the tree, select 'Dynamics 365 for Operations\Class'.
9. Click Add root.
    * Add a new data source to call the existing application logic for IBAN codes validation.  
10. In the Name field, type 'check_codes'.
    * check_codes  
11. In the Class field, type 'ISO7064'.
    * ISO7064  
12. Click OK.
13. In the tree, expand 'format'.
14. In the tree, expand 'format\Root: Sequence(Root)'.
15. In the tree, select 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)'.
16. Click Bind.
17. In the tree, expand 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)'.
18. In the tree, expand 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)\Fields: Sequence 1..1 (Fields)'.
19. In the tree, select 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)\Fields: Sequence 1..1 (Fields)\IBAN: String(IBAN)'.
20. In the tree, expand 'Payments = format.Root.Rows'.
21. In the tree, expand 'Payments = format.Root.Rows\Creditor Account(CreditorAccount)'.
22. In the tree, expand 'Payments = format.Root.Rows\Creditor Account(CreditorAccount)\Identification'.
23. In the tree, select 'Payments = format.Root.Rows\Creditor Account(CreditorAccount)\Identification\IBAN'.
24. Click Bind.
25. Click the Validations tab.
26. Click New.
    * Add a new validation rule that displays an error for any line in the parsing file that contains invalid IBAN code.  
27. Click Edit condition.
28. In the tree, expand 'check_codes'.
29. In the tree, select 'check_codes\verifyMOD1271_36'.
30. Click Add data source.
31. In the Formula field, enter 'check_codes.verifyMOD1271_36('.
    * check_codes.verifyMOD1271_36(  
32. In the tree, expand 'format'.
33. In the tree, expand 'format\Root: Sequence(Root)'.
34. In the tree, expand 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)'.
35. In the tree, expand 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)\Fields: Sequence 1..1 (Fields)'.
36. In the tree, select 'format\Root: Sequence(Root)\Rows: Sequence 1..* (Rows)\Fields: Sequence 1..1 (Fields)\IBAN: String(IBAN)'.
37. Click Add data source.
38. In the Formula field, enter 'check_codes.verifyMOD1271_36(format.Root.Rows.Fields.IBAN)'.
    * check_codes.verifyMOD1271_36(format.Root.Rows.Fields.IBAN)  
39. Click Save.
40. Close the page.
    * The validation condition has been configured to return FALSE for any invalid IBAN code by calling the existing method 'verifyMOD1271_36' of the application class 'ISO7064'. Note that the value of the IBAN code is defined dynamically at run-time as the argument of the calling method based on the content of the parsing TXT file.   
41. Click Edit message.
42. In the Formula field, enter 'CONCATENATE("Invalid IBAN code has been found:  ", format.Root.Rows.Fields.IBAN)'.
    * CONCATENATE("Invalid IBAN code has been found:  ", format.Root.Rows.Fields.IBAN)  
43. Click Save.
44. Close the page.
45. Click Save.
46. Close the page.

## Run the format mapping
For testing purposes, execute the format mapping using the SampleIncomingMessage.txt file that you downloaded. The generated output includes data that will be imported from the selected TXT file and populated to the custom data model during the real import.   
1. Click Run.
    * Click Browse and navigate to the SampleIncomingMessage.txt file that you previously downloaded.  
2. Click OK.
    * Review the output in XML format that represents the data that has been imported from the selected file and ported to the data model. Note that only 3 lines of the imported TXT file were processed. The IBAN code on line 4 that is not valid was skipped and an error message is provided in the Infolog.  

