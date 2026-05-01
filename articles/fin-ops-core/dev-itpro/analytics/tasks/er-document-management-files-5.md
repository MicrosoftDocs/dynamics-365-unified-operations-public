---
title: ER Use Document Management files in format outputs (Part 5 - Modify and run format)
description: This article describes how to configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. (Part 5)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERSolutionTable, EROperationDesigner, ERComponentTypeDropDialog, ERExpressionDesignerFormula, SysQueryForm
---

# ER Use Document Management files in format outputs (Part 5 - Modify and run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. You can perform these steps in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 4: Run format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Modify the format to populate attachments into generating messages in binary format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Customer invoice model**.
1. In the tree, expand **Customer invoice model\Customer invoice model (custom)**.
1. In the tree, select **Customer invoice model\Customer invoice model (custom)\Electronic invoice sample message**.
1. Select **Designer**.
    * You populate the invoice message in the generating output as an XML file using UNICODE encoding.  
1. Select **Add root** to open the drop dialog.
1. In the tree, select **Common\File**.
1. In the **Name** field, type **Xml message**.
    * Xml message  
1. In the **Encoding** field, type **UTF-8**.
    * UTF-8  
1. Select **OK**.
    * Configure the generating output as a zipped file.  
1. Select **Add root** to open the drop dialog.
1. In the tree, select **Common\Folder**.
1. In the **Name** field, type **Zip output**.
    * Zip output  
1. Select **OK**.
1. In the tree, select **Zip output**.
    * Add attachments to the generating zipped file as files with original names and extensions.  
1. Select **Add** to open the drop dialog.
1. In the tree, select **Common\File**.
1. In the **Name** field, type **Attached file**.
    * Attached file  
1. Select **OK**.
1. In the tree, select **Zip output\Attached file**.
1. Select **Add** to open the drop dialog.
1. In the tree, select **Text\Base64**.
1. Select **OK**.

## Map new format elements to data model

1. Select the **Mapping** tab.
1. In the tree, expand `model`.
1. In the tree, expand `model\Invoice attachments`.
1. In the tree, select `Zip output\Attached file\Base64`.
1. In the tree, select `model\Invoice attachments\File content`.
1. Select **Bind**.
1. In the tree, select **Zip output\Attached file**.
1. Select **Edit filename**.
1. In the tree, expand `model`.
1. In the tree, expand `model\Invoice attachments`.
1. In the tree, select `model\Invoice attachments\File name`.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
1. In the tree, select `model\Invoice attachments`.
1. Select **Bind**.
1. Select **Save**.
1. Close the page.

## Run the designed report for the selected invoice

1. Select **Run**.
1. Expand the **Records to include ()** section.
1. Select **Filter**.
1. Select the row of the **Customer invoice journal** and the **Sales order** field.
1. In the **Criteria** field, enter the order number `000148`.
    * 000148  
1. Select **OK**.
1. Select **OK**.
    * Review the generated output. In addition to the invoice message in XML format, the process creates a single file for each attachment. The attachment files are populated with the zipped output in binary format.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
