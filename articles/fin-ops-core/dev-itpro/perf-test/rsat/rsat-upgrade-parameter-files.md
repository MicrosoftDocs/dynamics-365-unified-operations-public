---
title: Upgrade of parameter files
description: 
author: FrankDahl
manager: tfehr
ms.date: 04/01/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.custom:
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: AX 7.0.0
---

# Upgrade of parameter files

[!include [banner](../../includes/banner.md)]

The format of parameter Excel files used with RSAT was changed with the 2.0 release, into a more intuitive format showing test steps. New cases created with version 2.0 and later automatically created parameter files in this new format, you may however have tests that were authored before that version which still use the old format. The old format parameter files remain supported by RSAT to run cases at least up to the next major release of RSAT.

RSAT has an action that upgrade old parameter files into the new format.

Parameter files can be edited freely in Excel and there are situations where upgrade cannot fully complete a new format parameter file, and in such cases that some manual work will be needed to complete the upgrade. The next section explains the mechanics of how the upgrade process is working to provide more detail of this.

## Mechanics of Parameter files upgrade

The upgrade process attempts to complete a full upgrade, but there are situations where this cannot safely be completed.

When upgrade can complete fully, then the Parameter file is simply replaced with the new one. We save a copy of the old parameter file named with _BAK at the end of the name as backup though.

When upgrade can only safely upgrade a part of your parameter file, then we leave the existing parameter file untouched without changing this. We create a new parameter file in the new format with all information that was possible to upgrade, and this file is named _PARTIAL at end of the filename. The idea is then for you to use this file and manually bring over missing parts from the old parameter file to complete this new file. Once you are done with this, then rename your old parameter file to a backup name, for instance add _BAK in the end of the filename like it is done with fully completed updates. Finally rename the new parameter file by removing the _PARTIAL in the end of the filename such this becomes the new parameter file used with the case.

Notice: You may continue to use old parameter files until you are ready with a file in the new format. RSAT will continue to support the old parameter file format at least up to the next major release.

The upgrade process should be able to complete upgrade of unedited Parameter files. It will also be able to upgrade files where only cell values changed in the file. However, when additional cells have been added and referenced then upgrade cannot automatically complete, and here the _PARTIAL file will include cells with “#MISSING” text to indicate cell references are missing. This is where you manually add in this information from the old Parameter Excel file into the new _PARTIAL excel file to complete such cases.

**Important: Going forward, place all cells you need to add into the new CustomParameters sheet like you also see added with in the _PARTIAL Excel file.**

There is a CustomParameters sheet added to the Excel Parameter file format as with RSAT 2.2 release and later. This is included to help future proof upgrade of Excel Parameter files. Place all self-added cells into this sheet, and we will target to bring forward this sheet directly as it is with any future parameter file upgrades.

Cells you added into the old Parameter files with a Name assigned to the cell, those will move into the CustomParameters sheet automatically during the upgrade, that is providing the cell value does not also reference other cells.

Once you have moved over your self-added cells and into the _PARTIAL Excel, then make sure you also change references from the TestCaseSteps sheet that had “#MISSING” in the text, and substitute with reference to match relevant cells added under CustomParameters, ideally always reference cells by an assigned name (like MyQuantity) and not by the cell identifier (like E4).

**Notice: It is good practice to assign names with any cells added into the CustomerParameters sheet and reference the cells by name from case steps.**

Always plan for completing an upgrade by running your test cases to review the new parameter file is working with expected results. This is important to ensure everything is working as it should. Do this both when upgrade completed fully and when upgrade required manual work.

When you are satisfied with that everything is working well, then consider at some point deleting backups files that was created during the process like _BAK and _PARTIAL files. These will no longer serve a purpose then.

## Running Parameter file upgrade

You upgrade parameter files by using the Parameter file Upgrade available as a action located under the New drop-down action menu. First select test cases you want to process parameter files upgrades for, and then click the arrow drop-down action “Upgrade Parameter files (will auto generate Test Execution files) as seen here below.

SCREEN - New drop down menu

The process will upgrade for all selected test cases.

The upgrade process will automatically skip test cases where the parameter Excel files already using the new format. This is determined by the existence of the CustomParameters sheet in the file, that the new standard format use.

The process complete by presenting a summary. This shows the total number of selected test cases that were marked for upgrade, along with the outcome of the upgrade. This includes the number of cases that were upgraded successfully, with a new parameter file fully completed in the new format that has replaced the old parameter file (but with a backup preserved of the old). This also includes the number of cases where upgrade failed to complete fully where the parameter file is left as it was but with a new PARTIAL file that include what could be upgraded. There is also the number of cases skipped because they were already upgraded.

This is an example of the summary dialog:

SCREEN - Upgrade summary message

The summary mentions further detail can be found clicking the triangle icon on test case where upgrade did not complete fully. This shows how that the triangle icon appear:

SCREEN - Upgrade warning triangle

This is an example message that is provide when clicking the yellow warning triangle icon:

SCREEN - Updade warning triangle message

This upgrade process can safely be run multiple times as recall that already upgraded files will be skipped. Notice however that new PARTIAL files will be saves, and this may override work in progress you have from earlier. It is advised to complete all PARTIAL files and take them into use by renaming them before running upgrade again.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
