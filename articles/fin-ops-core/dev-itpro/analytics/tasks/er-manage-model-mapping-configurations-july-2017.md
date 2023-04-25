---
title: Manage ER model mapping in separate ER configurations
description: This article describes how to manage Electronic reporting (ER) model mappings in separate ER configurations.
author: kfend
ms.date: 06/19/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Manage ER model mapping in separate ER configurations

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the System administrator or Electronic reporting developer role can manage Electronic reporting (ER) model mappings in separate ER configurations. In this task guide, you will create required ER configurations for the sample company, Litware, Inc. To complete this task guide, you must first complete the steps in the task guide, "ER Create a configuration provider" and mark it as active. 

Because ER configurations are shared among companies, you can complete this task guide using the company data set of your choice. The functionality for this task guide is available if you have installed one of the following hotfixes: https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012872 for the Dynamics AX 7.0 version or https://fix.lcs.dynamics.com/Issue/Resolved?kb=4012871 for the Dynamics 365 for Operations version.

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Verify that the configuration provider for the sample company Litware, Inc. is available and marked as active. If you don't see this configuration provider, you must first complete the steps in the task guide, Create a configuration provider, and mark it as active.   

## Add a new ER model configuration
1. Click Reporting configurations.
    * Add a new model configuration. The name must be unique in the configurations tree.  
2. Click Create configuration to open the drop dialog.
3. In the Name field, type 'Sample data model'.
    * Sample data model  
4. Click Create configuration.
5. Click Designer.
6. Click New to open the drop dialog.
7. In the Name field, type 'Root'.
    * Root  
8. Click Add.
9. Click New to open the drop dialog.
10. In the Name field, type 'Company'.
    * Company  
11. Click Add.
12. In the Description field, enter the text, Description of the legal entity or company in which a user logged at run-time. 
    * Description of the legal entity or company in which a user logged at run-time.  
13. Click Root reference.
14. Click OK.
15. Click Save.
16. Close the page.
17. Click Change status.
18. Click Complete.
19. Click OK.

## Add a new ER model-mapping configuration
1. Click Create configuration to open the drop dialog.
2. In the New field, enter 'Model Mapping based on data model Sample data model'.
3. In the Name field, type 'Sample mapping'.
    * Sample mapping  
4. Click Create configuration.
5. Expand the Prerequisites section.
    * The Implementations prerequisites group has been added automatically. The group contains the prerequisite component that refers to the parent data model configuration and is marked as Implementation. This means that this Sample-mapping model-mapping configuration is considered the implementation of the data model, Sample data model. Therefore, this component will force ER to download the model-mapping configuration, Sample mapping from an ER repository when the model configuration, Sample data model, is downloaded.   
6. Click Designer.
    * The created model-mapping configuration contains a new blank mapping with the same name as the created configuration. When a selected parent model configuration contains model mappings, they will be copied to a new model-mapping configuration.   
7. Click Designer.
8. In the tree, select 'Dynamics 365 for Operations\Table'.
9. Click Add root.
10. In the Name field, type 'Company'.
    * Company  
11. In the Table field, type 'CompanyInfo'.
    * CompanyInfo  
12. Click OK.
13. In the tree, expand 'Company'.
14. In the tree, expand 'Company\find()'.
15. In the tree, select 'Company\find()\Name'.
16. Click Bind.
17. Click Save.
18. Close the page.
19. Close the page.
20. On the Action Pane, click Configurations.
21. Click User parameters.
22. Select Yes in the Run settings field.
23. Click OK.
24. Click Edit.
25. Select Yes in the Run Draft field.

## Add a new ER format configuration
1. In the tree, select 'Sample data model'.
2. Click Create configuration to open the drop dialog.
3. In the New field, enter 'Format based on data model Sample data model'.
4. In the Name field, type 'Sample format'.
    * Sample format  
5. Click Create configuration.
6. Click Designer.
7. Click Add root to open the drop dialog.
8. In the tree, select 'Text\String'.
9. Click OK.
10. Click the Mapping tab.
11. In the tree, expand 'model'.
12. In the tree, select 'model\Company'.
13. Click Bind.
14. Click Save.
15. Close the page.
    * Run the draft version of the created format for testing purposes.  
16. Click Run.
    * On the Versions FastTab, click Run.  
17. Click OK.
    * Review the output that contains the name of the company in which the user who is running this format configuration is logged into. The created model-mapping configuration is used by this format configuration because there is only one configuration available that contains required model mappings.   

## Add alternative ER model-mapping configuration
1. In the tree, select 'Sample data model'.
2. Click Create configuration to open the drop dialog.
3. In the New field, enter 'Model Mapping based on data model Sample data model'.
4. In the Name field, type 'Sample mapping (alternative)'.
    * Sample mapping (alternative)  
5. Click Create configuration.
6. Click Designer.
7. Click Designer.
8. In the tree, select 'Dynamics 365 for Operations\Table'.
9. Click Add root.
10. In the Name field, type 'Company'.
    * Company  
11. In the Table field, type 'CompanyInfo'.
    * CompanyInfo  
12. Click OK.
13. Click Edit.
14. In the tree, select 'String\CONCATENATE'.
15. Click Add function.
16. In the tree, expand 'Company'.
17. In the tree, expand 'Company\find()'.
18. In the tree, select 'Company\find()\Name'.
19. Click Add data source.
20. In the Formula field, type a value.
    * CONCATENATE(Company.'find()'.Name, ";",  
21. In the tree, select 'Company\find()\Company(DataArea)'.
22. Click Add data source.
23. In the Formula field, type a value.
    * CONCATENATE(Company.'find()'.Name, ";", Company.'find()'.DataArea)  
24. Click Save.
25. Close the page.
26. Click Save.
27. Close the page.
28. Close the page.
29. Select Yes in the Run Draft field.

## Use an existing ER model-mapping configuration
1. In the tree, select 'Sample data model\Sample format'.
2. Click Run.
    * The selected draft version of the ER format configuration can't be executed because there is more than one model-mapping configuration available for the undefined data model that has been selected as the data source of the running ER format.   
    * Next, you will define the alternative model-mapping configuration as the one from which model mappings will be used as data sources for running ER format.   
3. In the tree, select 'Sample data model\Sample mapping (alternative)'.
4. Select Yes in the Default for model-mapping field.
5. In the tree, select 'Sample data model\Sample format'.
6. Click Run.
7. Click OK.
    * The default model-mapping configuration is used by this format configuration for generating the electronic document (the created output contains the company code).  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
