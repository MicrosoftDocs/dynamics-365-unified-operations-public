---
title: Define the dependency of ER configurations on other components
description: This article describes how to design an Electronic reporting (ER) configuration and specify its dependency from other software components.
author: kfend
ms.date: 07/23/2021
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
# Define the dependency of ER configurations on other components

[!include [banner](../../includes/banner.md)]

To complete these steps, you must first complete the steps in the task guide, ER Manage model mapping configurations, and you must have access to Microsoft Dynamics Lifecycle Services (LCS).

This procedure shows how to design an Electronic reporting (ER) configuration and specify its dependency from other software components, so that you can help guarantee that the configuration is correctly downloaded to a specific version of finance and operations. In this example, you will create required ER configurations for the sample company Litware, Inc. 

This procedure is intended for users who have the System administrator or Electronic reporting developer role assigned to them. The steps can be performed in any company, because ER configurations are shared among companies. 

1. Go to Organization administration > Electronic reporting > Configurations.
    * Make sure that the configurations tree contains the 'Sample data model' configuration and subordinate items. Otherwise, complete the steps in the task guide, ER Manage model mapping configurations, and then start this guide again.   

## Define the dependency of ER configurations from other components
1. In the tree, expand 'Sample data model'.
2. In the tree, select 'Sample data model\Sample mapping'.
    * We selected the draft version of the 'Sample mapping' model mapping configuration. We will now define its dependency from other software components. This step is considered a prerequisite for controlling the download of this configuration's version from an ER repository and any further use of this version.   
3. Expand the Prerequisites section.
    * Note that the 'Implementations' prerequisites group has been added automatically at this stage. This group contains the prerequisite component that refers to the data model configuration and has the Implementation flag turned on. This flag indicates that the 'Sample mapping' mapping configuration is considered the implementation of the 'Sample data model' data model. This component will force ER to download the 'Sample mapping' mapping configuration from an ER repository whenever the 'Sample data model' model configuration is downloaded.   
4. Click Edit.
    * A single dependency of the current version of a configuration from a software component can be specified by using the definition of the component's type, and either the component version or a range of component versions.  
    * Desired dependencies can be grouped together. When the 'All of' grouping type is selected, the dependency condition of this group is considered satisfied when each dependency condition from this group and subordinate group is satisfied. When the 'One of' grouping type is selected, the dependency condition of this group is considered satisfied when at least one dependency condition from this group is satisfied.   
5. Click New.
6. Select Product prerequisite component.
7. Select Microsoft Dynamics 365 for Operations (1611).
8. In the Version field, type '[7.1.1541.3036,8)'.
    * [7.1.1541.3036,8)  
    * Dependencies that you enter will be evaluated when this configuration is downloaded from any ER repository. This configuration version will be downloaded from the ER repository when version 1 of the 'Sample data model' configuration is either already in place or downloaded in advance. If it's downloaded in advance, it must be completed in finance and operations version 7.1.1541.3036 or later, but must not exceed major version 8.   
9. Click Save.
10. Close the page.
11. Click Change status.
12. Click Complete.
13. Click OK.
14. In the tree, select 'Sample data model\Sample mapping (alternative)'.
15. Click Edit.
16. Click New.
17. Select Product prerequisite component.
18. Select Microsoft Dynamics AX 7.0 RTW.
19. In the Version field, type '[7.0.1265.3015,7.1)'.
    * [7.0.1265.3015,7.1)  
    * Dependencies will be evaluated when the configuration is downloaded from any ER repository. This configuration version will be downloaded from the ER repository when version 1 of the 'Sample data model' configuration is either already in place or downloaded in advance. If it's downloaded in advance, it must be completed in Microsoft Dynamics 365 Finance, Enterprise edition, the version of which must be 7.0.1265.3015 or later, but must not exceed minor version 1.   
20. Click Save.
21. Close the page.
22. Click Change status.
23. Click Complete.
24. Click OK.

## Configure the ER repository
1. Close the page.
2. Go to Organization administration > Workspaces > Electronic reporting.
    * Open the list of ER repositories for the current ER provider, Litware, Inc.  
3. In the list, mark the selected row.
4. Click Repositories.
5. Click Show filters.
6. Enter a filter value of "LCS" on the "Type name" field using the "contains" filter operator.
    * If the LCS repository is already registered for the current ER provider, you can skip the remaining steps in this sub-task. If the LCS repository isn't already registered, complete the remaining steps.   
7. Click Add to open the drop dialog.
8. In the Configuration repository type field, enter 'LCS'.
9. Click Create repository.
10. In the Project field, enter or select a value.
    * Select the desired LCS project from the lookup of the 'Project' field.  
11. Click OK.
12. Close the page.

## Upload configurations to LCS
1. Click Reporting configurations.
2. In the tree, select 'Sample data model'.
3. Select the completed version of this configuration.
4. Click Change status.
5. Click Share.
6. Click OK.
    * Version 1 of this model configuration has been uploaded to LCS by using the LCS project for the ER repository that was previously configured.   
7. In the tree, expand 'Sample data model'.
8. In the tree, select 'Sample data model\Sample mapping'.
9. Select the completed version of this configuration.
10. Click Change status.
11. Click Share.
12. Click OK.
    * Version 1.1 of this model mapping configuration has been uploaded to LCS by using the LCS project for the ER repository that was previously configured.   
13. In the tree, select 'Sample data model\Sample mapping (alternative)'.
14. Select the completed version of this configuration.
15. Click Change status.
16. Click Share.
17. Click OK.
    * Version 1.1 of this model mapping configuration has been uploaded to LCS by using the LCS project for the ER repository that was previously configured.   

## Evaluate ER configuration dependencies
We will delete created configurations from the system and download them back from the LCS repository.  
1. In the tree, select 'Sample data model\Sample mapping'.
2. Click Delete.
3. Click Yes.
4. In the tree, select 'Sample data model\Sample mapping (alternative)'.
5. Click Delete.
6. Click Yes.
7. In the tree, select 'Sample data model\Sample format'.
8. Click Delete.
9. Click Yes.
10. In the tree, select 'Sample data model'.
11. Click Delete.
12. Click Yes.
13. Close the page.
    * Open the list of ER repositories for the current ER provider, Litware, Inc.  
14. Click Repositories.
15. Click Show filters.
16. Enter a filter value of "LCS" on the "Type name" field using the "contains" filter operator.
17. Click Open.
18. In the tree, select 'Sample data model'.
    * Note that you can view an evaluation of whether prerequisite conditions have been satisfied for each version of the ER configurations for the current repository. To view this evaluation, click Check prerequisites.   
19. Click Check prerequisites.
20. Click Import.
21. Click Yes.
22. Close the page.
23. Close the page.
24. Close the page.
25. Go to Organization administration > Electronic reporting > Configurations.
26. In the tree, expand 'Sample data model'.
    * Note that the model 'Sample mapping' mapping configuration has been downloaded together with the selected data model configuration. The two files are downloaded together because 'Sample mapping' has been defined as implementing the selected data model, and because it's applicable for the application. The 'Sample mapping (alternative)' configuration hasn't been downloaded because the condition for the required application version isn't satisfied.   
    * If you sign in to finance and operations, register the same provider, access the same LCS project, and download the same data model configuration, the 'Sample mapping (alternative)' configuration will download, whereas the 'Sample mapping' configuration will be skipped.  

## Additional resources

[Manage the Electronic reporting (ER) configuration lifecycle](../general-electronic-reporting-manage-configuration-lifecycle.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

