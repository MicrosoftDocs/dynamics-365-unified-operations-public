---
title: ER Create required configurations to import data from an external file
description: This article describes how to design Electronic reporting configurations to import data in to the Microsoft Dynamics 365 Finance app from an external file.
author: kfend
ms.date: 03/24/2021
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: DefaultDashboard, ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERSolutionCreateDropDialog, EROperationDesigner, ERModelMappingTable, ERModelMappingDesigner, ERExpressionDesignerFormula, Tax1099Summary, VendSettlementTax1099
---
# ER Create required configurations to import data from an external file

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System administrator or Electronic reporting developer role can design Electronic reporting (ER) configurations to import data in to the application from an external file. In this example, you will create the required ER configurations for the sample company, Litware, Inc. To complete these steps, you must first complete the steps in the Task guide, "ER Create a configuration provider and mark it as active." These steps can be completed using the USMF data set. You must also download and save the following files locally: 

| Content description                       | File name                                     |
|-------------------------------------------|-----------------------------------------------|
| ER data model configuration - 1099 | [1099model,xml](https://download.microsoft.com/download/b/d/9/bd9e8373-d558-4ab8-aa9b-31981adc97ea/1099model.xml)                  |
| ER format configuration - 1099    | [1099format.xml](https://download.microsoft.com/download/e/8/7/e87154b0-b53f-431f-8e1e-0b7f7c9805a9/1099format.xml)                  |
| Sample of the incoming document in XML format                          | [1099entries.xml](https://download.microsoft.com/download/4/0/3/403a4958-df24-476a-b8b0-6843a9fa7f89/1099entries.xml)        |
| Sample of the workbook to manage data of incoming document                          | [1099entries.xlsx](https://download.microsoft.com/download/6/0/0/6001abab-a331-48db-a939-41851fb0f5d0/1099entries.xlsx) |

ER offers business users the ability to configure the process of importing external data files to tables in either .XML or .TXT format. First, an abstract data model and an ER data model configuration must be designed to represent the data that you are importing. Next, you need to define the structure of the file that you are importing and the method that you will use to port the data from the file to the abstract data model. The ER format configuration that maps to the designed data model must be created for that abstract data model. Then, the data model configuration must be extended with a mapping that describes how the imported data is persisted as abstract data model data and how it is used to update tables.  The ER data model configuration must be appended with a new model mapping that describes the binding of the data model to the application's destinations.  

The following scenario shows the ER data import capabilities. This includes vendor transactions that are tracked externally and then imported to be reported later in Vendor's settlement for 1099's.   

## Add a new ER model configuration
1. Go to Organization administration > Workspaces > Electronic reporting.

    Verify that the configuration provider for sample company 'Litware, Inc.' is available and marked as active. If you don't see this configuration provider, you must first complete the steps in the procedure, "Create a configuration provider and mark it as active."   

2. Click Reporting configurations.

    Instead of creating of a new model to support data import, load the file, 1099model.xml, that you previously downloaded. This file contains the custom data model of vendors' transactions. This data model is mapped to the data components that are in the AOT data entity.   

3. Click Exchange.
4. Click Load from XML file.

    Click Browse and navigate to the 1099model.xml file that you previously downloaded.  

5. Click OK.
6. In the tree, select '1099 Payments model'.

## Review data model settings
1. Click Designer.

    This model is designed to represent vendors' transactions from the business standpoint and are separate from the implementation.   

2. In the tree, expand '1099-MISC'.
3. In the tree, select '1099-MISC\Transactions'.
4. In the tree, expand '1099-MISC\Transactions'.

    The Transactions element of this model represents individual transactions. The child elements are used to specify required details, such as vendor account and transaction date, for each transaction.   

5. Close the page.

## Add a new ER format configuration that supports data import
The steps in this subtask show you how a new format configuration can be created to manage data import from external files.   
1. Click Create configuration to open the drop dialog.
2. In the New field, enter 'Format based on data model 1099 Payments model'.
3. Select Yes in the Supports data import field.
4. Press ESC key to close this page.

    Instead of creating a new format to support data import, load the 1099format.xml file that you previously downloaded. This file contains the defined structure of the file you are importing and the mapping of the structure to the custom data model of vendors' transactions.   
5. Click Exchange.
6. Click Load from XML file.
    Click Browse and navigate to the 1099format.xml file that you previously downloaded.  
7. Click OK.
8. In the tree, expand '1099 Payments model'.
9. In the tree, select '1099 Payments model\Format for importing vendors' transactions'.

## Review format settings
1. Click Designer.
2. Toggle 'Show details' on.
3. Click Expand/collapse.
4. Click Expand/collapse.

    The designed format represents the expected structure of the external file. This file must be in XML format and have the settlement root element. Each vendor's transaction is represented by the transaction element that is defined as having zero-to-many multiplicity. This means that the incoming file may contain anywhere from zero to multiple transactions. Nested elements of the 'transaction' element represent a single transaction's attributes. Note that all attributes, except country/region, are marked as mandatory, meaning that it is required to have them in the importing file.   

## Review the settings of the format mapping to the data model
1. Click Map format to model.

    The mapping 'For importing vendors' transactions' contains the data transfer rules from the incoming XML file to the selected part of the custom data model, which is defined by selecting the1099-MISC definition.  

2. Click Designer.
3. Toggle 'Show details' on.
4. In the tree, expand 'format: Record'.
5. In the tree, select 'format: Record'.

    Note that the designed format is presented here as a data source component.  

6. In the tree, expand `format: Record\*settlement: XML Element 1..1 (settlement): Record`.
7. In the tree, expand `format: Record\*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list`.
8. In the tree, expand `format: Record\*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list\*vendor: XML Element 1..1 (vendor): Record`.
9. In the tree, expand `format: Record\*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list\country: XML Element 0..1 (country): Record`.
10. In the tree, select `format: Record\*settlement: XML Element 1..1 (settlement): Record\transaction: XML Element 0..* (transaction): Record list\*vendor: XML Element 1..1 (vendor): Record`.

    Note that the presentation of mandatory and optional format elements is different in the predefined 'format' data source component.  
11. In the tree, expand 'Transactions: Record list= format.settlement.'$enumerated''.

    Note that the elements of the format that defines the structure of the imported file are bound to the elements of the custom data model. Based on these bindings, the content of the imported XML file will be stored at run-time in the existing data model. Pay attention to the binding of the country element. For any transaction element in the incoming file that has no such element, the default country code 'USA' will be populated in the data model.  

12. Click the Validations tab.

    This format mapping may contain user-defined logic to validate the accuracy of the imported data from a business standpoint. For example, based on the setting, for any transaction in the importing file without a defined country code, a warning message will be generated in the Infolog informing the user about the case and indicating the transaction's sequence number.  

13. Close the page.

## Run the format mapping to the data model
Execute this format mapping for testing purposes. Use the file 1099entries.xml that you previously downloaded. You can export this file from the 1099entries.xlsx workbook that is used to manage vendor transactions. The generated output will be imported from the selected XML file and populate the custom data model at real import.  

1. Click Run.

    Click Browse and navigate to the 1099entries.xml file that you previously downloaded.  

2. Click OK.

    Note the warning message about a missing country code for a transaction in the imported file.  
    
    Review the output in XML format, which represents the data that has been imported from the selected file and ported to the data model.   

3. Close the page.
4. Close the page.

## Review the settings for the model mapping to the destinations
1. In the tree, select '1099 Payments model'.
2. Click Designer.
3. Click Map model to datasource.

    The mapping For 1099 manual transactions import has been defined with the To destination direction type. This means that it has been entered to support data import and contains the setting of rules defining how the imported external file and persisted as abstract data model data is used to update tables in the application.  

4. Click Designer.
5. In the tree, expand 'model: Data model 1099 Payments model'.
6. In the tree, expand 'model: Data model 1099 Payments model\Transactions: Record list'.

    Note that the designed model is presented here as a data source element. At runtime, it will contain the data that is imported from the external file. Several tables were added as data source elements to ensure that the imported data is compliant with the data of the current application, including whether the importing transaction vendor account is available in the system, whether the combination of the importing country/region and state codes exists, etc.  

7. In the tree, select 'model: Data model 1099 Payments model\Transactions: Record list\$failed: Calculated field = IF(OR(ISEMPTY(model.Transactions.'$refs'.vendor), ISEMPTY(model.Transactions.'$refs'.vendor1099), ISEMPTY(model.Transactions.'$refs'.box1099), ISEMPTY(model.Transactions.'$refs'.country), ISEMPTY(model.Transactions.'$refs'.state), ISEMPTY(model.Transactions.'$refs'.location)), true, false): Boolean'.
8. Click Edit.
9. Click Edit formula.

    When at least one validation fails for a single imported transaction, this transaction will be marked as failed by the data source attribute '$failed'.  

10. Close the page.
11. Click Cancel.
12. In the tree, select 'tax1099trans: Table 'VendSettlementTax1099' records= model.Validated'.
13. Click Edit destination.

    This ER destination was added to specify how the imported data will update the application tables. In this case, the data table VendSettlementTax1099 has been selected. Because the record action Insert has been selected, the imported transactions will be inserted in the table VendSettlementTax1099. Note that a single model mapping may contain several destinations. This means that the imported data can be used to update multiple application's tables at once. Tables, views, and data entities can be used as ER destinations.   

    If the mapping will be called from a point in the application (such as button or menu item) that was specifically designed for this action, the ER destination should be marked as the integration point. In this example this is the ERTableDestination#VendSettlementTax1099 point.  

14. Click Cancel.
15. Click Show all.
16. Click Show mapped only.
17. In the tree, expand 'tax1099trans: Table 'VendSettlementTax1099' records= model.Validated'.

    Note that the data source element that contains the only validated transactions is bound to the created destination. You can filter the imported transactions to skip the ones that are incompatible with the applications' data.  

18. In the tree, select 'failed: Table 'VendSettlementTax1099Entity' records= model.Failed'.
19. Click the Validations tab.

    This model mapping may contain user-defined logic to validate the correctness of the imported data from the existing application data. For example, based on the present setting, for any transaction in the imported file with a vendor account that is not in the system, a warning message will be generated informing the user and indicating the incorrect vendor account code.  

    Note that the Post validation action option can be used for each validation, to specify whether the import process must be continued or stopped, as well as if the already performed inserts/updates can be kept or rolled back.  

20. Click Show mapped only.
21. Click Show all.
22. Close the page.

    Execute this model mapping to test the designed format and model mappings. Use the file 1099entries.xml. The data from the selected file will be imported in to the system.  

23. Click Run.

    Note that the dialog box contains no additional questions about the format mapping that must be used to parse the imported file and then port the data to the data model. This is because there is currently only one format that uses this model, which is marked as designed to support data import.  
    
    Define the voucher ID to differentiate the imported transactions from other transactions that may already have been entered manually or imported.  

24. In the Enter voucher id field, type 'IMPORT-001'.

    Browse to get the '1099entries.xml' file.  

25. Click OK.

    The list of generated warnings provides information about incorrect vendor accounts, an incorrect tax 1099 box code, missing country codes, etc. Compare this list of warnings to the content that is included in the execution XML file.  

26. Close the page.
27. Close the page.
28. Close the page.
29. Close the page.
30. Go to Accounts payable > Periodic tasks > Tax 1099 > Vendor settlement for 1099s.

    This form shows the cumulative transactions in the Tax1099Summary table that have been created based on imported transactions.  

31. In the From date field, set the date to '2000-01-01'.
32. Click Manual 1099 transactions.

    This form contains the list of transactions that were added manually and those that we just imported.  

33. Open Voucher column filter.
34. Enter a filter value of "IMPORT-001" on the "Voucher" field using the "begins with" filter operator.

## Review the relationship between model and format mappings
1. Close the page.
2. Close the page.
3. Go to Organization administration > Workspaces > Electronic reporting.
4. Click Reporting configurations.
5. In the tree, select '1099 Payments model'.

    Assume that you want to support importing the same data but from a .TXT file format.   

6. Click Create configuration to open the dialog box. 
7. In the New field, enter 'Format based on data model 1099 Payments model'.
8. In the Name field, type 'Import data from TXT file'.
9. Select Yes in the Supports data import field.
10. Click Create configuration.
11. Click Designer.
12. Click Map format to model.
13. Click New.
14. In the Definition field, enter or select a value.

    Select '1099-MISC' option.  

15. In the Name field, type 'Import data from TXT file'.
16. In the Description field, type 'Import data from TXT file'.
17. Click Save.
18. Close the page.
19. Close the page.
20. Click Edit.

    If you installed the hotfix "KB 4012871 Support of GER model mappings in separated configurations with an ability to specify different kinds of prerequisites for deploying them on different versions of Dynamics 365 Finance" ([KB 4012871](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012871)), execute the next step "Turn the flag 'Default for model mapping' on" for the entered format configuration. Skip the next step otherwise.  

21. Select Yes in the Default for model-mapping field.
22. In the tree, select '1099 Payments model'.
23. Click Designer.
24. Click Map model to datasource.
25. Click Run.

    If you installed the hotfix, KB 4012871 Support of GER model mappings in separated configurations with an ability to specify different kinds of prerequisites for deploying them on different versions ([KB 4012871](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012871)), select the preferred model mapping in the lookup field. If you haven't installed the hotfix yet, skip to the next step as the mapping has already been selected by the definition of the default format configuration.  
    
    If you have not installed the hotfix, KB 4012871, notice that the dialog box contains an additional model-mapping question that is used to parse the file that you are importing. The data is then ported from the dialog box to the data model. Currently, you can choose which format mapping must be used depending on the type of file that you plan to import.  
    
    If you plan to call this model mapping from a point in the application that is specifically designed for the action, the ER destination and the format mapping must be marked as part of the integration.  

26. Click Cancel.
27. Close the page.
28. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
