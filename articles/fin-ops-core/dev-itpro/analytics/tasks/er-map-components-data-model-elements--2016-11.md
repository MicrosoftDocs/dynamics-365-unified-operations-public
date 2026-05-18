---
title: ER Map components of the created format to data model elements (November 2016)
description: This article describes how to map data model elements to components of the created Electronic reporting (ER) configuration.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, EROperationDesigner
---

# ER map components of the created format to data model elements (November 2016)

[!include [banner](../../includes/banner.md)]

The following procedure shows how a user in either the System administrator or Electronic reporting developer role can map data model elements to components of the created Electronic reporting (ER) configuration. This configuration defines an electronic document format for the payments business domain. You use this format later to generate electronic documents for processing payments. In this example, you create a format configuration for the sample company, Litware, Inc. You can perform these steps in any company because all companies share ER configurations. To complete these steps, you must first complete the steps in the "Create a format configuration" task guide.

## Select a format configuration

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.
1. In the tree, expand **Payments (simplified model)**.
1. In the tree, select **Payments (simplified model)\BACS (UK fictitious)**.
1. Select **Designer**.

## Map format components to data model elements

1. Select **Expand/collapse**.
1. Select the **Mapping** tab.
1. In the tree, expand `model`.
1. In the tree, select `Xml\Message\ProcessingDate\DateTime`.
1. In the tree, select `model\ProcessingDateTime`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\MessageId\String`.
1. In the tree, select `model\MessageIdentification`.
1. Select **Bind**.
1. In the tree, expand `model\Payments`.
1. In the tree, select `Xml\Message\Payments\Item\Amount\String`.
1. In the tree, select `model\Payments\InstructedAmount`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\TransDate\DateTime`.
1. In the tree, select `model\Payments\TransactionDate`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Description\String`.
1. In the tree, select `model\Payments\Description`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Currency\String`.
1. In the tree, select `model\Payments\Currency`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Id`.
1. In the tree, select `model\Payments\End2EndID`.
1. Select **Bind**.
1. In the tree, expand `model\Payments\Creditor`.
1. In the tree, expand `model\Payments\Creditor\Account`.
1. In the tree, expand `model\Payments\Creditor\Agent`.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Name\String`.
1. In the tree, select `model\Payments\Creditor\Name`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Bank\RoutingNumber\String`.
1. In the tree, select `model\Payments\Creditor\Agent\RoutingNumber`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Bank\AccountNumber\String`.
1. In the tree, select `model\Payments\Creditor\Account\Number`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Payer\Name\String`.
1. In the tree, expand `model\Payments\Debtor`.
1. In the tree, expand `model\Payments\Debtor\Account`.
1. In the tree, expand `model\Payments\Debtor\Agent`.
1. In the tree, select `model\Payments\Debtor\Name`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Payer\Bank\RoutingNumber\String`.
1. In the tree, select `model\Payments\Debtor\Agent\RoutingNumber`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item\Payer\Bank\AccountNumber\String`.
1. In the tree, select `model\Payments\Debtor\Account\Number`.
1. Select **Bind**.
1. In the tree, select `Xml\Message\Payments\Item`.
1. In the tree, select `model\Payments`.
1. Select **Bind**.
1. Select **Save**.

## Validate format mapping

1. Select **Validate**.
    * Validate the new mapping to ensure that all bindings are correct.  
1. Close the page.

## Change status of the current version of format configuration

In the next steps, change the status of the format configuration from **Draft** to **Completed** to make it available for payment document generation.  

1. Select **Change status**.
1. Select **Complete**.
1. In the **Description** field, enter a value.
    * For example, 'version 1'.  
1. Select **OK**.
1. Select the completed version of the current configuration.
    * The configuration is saved as completed version 1.1: version 1 of the format based on version 1 of the data model.    

## Define effective date for completed version of format

You can configure each format version as available for usage starting from a certain date. When more than one format version is active on a certain date, the latest format (based on version number) is selected for usage. The session date value is used for proper version selection.  

## Restrict access to created format from companies

1. Expand the **ISO Country/region codes** section.
    * You can restrict each format access by identifying particular countries or regions in which a format is applicable. When the list of countries or regions for a particular format is empty, any company can use this format. When you add some ISO country or region codes to the list, companies can only use the format if the primary address is in the country or region.  

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
