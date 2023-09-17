---
title: What's new or changed in Dynamics AX application version 7.0.1 (May 2016)
description: This article describes features that are either new or changed in Microsoft Dynamics AX application version 7.0.1. This version was released in May 2016 and has a build number of 7.0.1265.23014.
author: sericks007
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f0bbc78f-87fc-40e9-b46a-6655893f69be
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics AX application version 7.0.1 (May 2016)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics AX application version 7.0.1. This version was released in May 2016 and has a build number of 7.0.1265.23014.

## Electronic reporting (ER)

| What can you do? | Why is this important? |
|------------------|------------------------|
| Configure a run-time dialog box for designing Electronic reporting (ER) reports, so that users can select the financial dimensions that they want. | At run time, in the dialog box for running an ER report, users can select multiple financial dimensions. The details of the selected financial dimensions will be displayed in the electronic document that is generated. |
| Configure access to multiple financial dimensions during the design of an ER report, via a single mapping to the desired data source. | The same ER report configuration can be used to generate electronic documents that present transactional data together with details of financial dimensions, regardless of the number of financial dimensions that are either selected by the user or configured for the current legal entity or instance. |
| Configure an ER report to enter data in dynamically generated columns of an electronic document that is created in OPENXML worksheet format. | An ER report can enter data in an OPENXML worksheet that is generated, via horizontally replicating columns. Therefore, the same ER report configuration can be reused to generate electronic documents that have a different number of dynamically generated columns. |
| Configure ER destinations so that the output result of a format is directed to specific destination: file, email, or archive (Microsoft SharePoint folder or Microsoft Azure Storage). | Previously, when you ran an ER configuration, a message box appeared that required user action to save or open a file. You can now pre-configure a destination for each format configuration and for each output component (a folder or a file) separately. Users who have appropriate access rights can also modify destination settings at run time. |

## POS – Microsoft Dynamics AX Retail

| What can you do? | Why is this important? |
|------------------|------------------------|
| Use the Google Chrome browser. | Retailers can now start Cloud POS from the Chrome browser, and can experience all the functionality that is available in the Microsoft Edge and Internet Explorer version of Cloud POS. |

## Financial reporting

| What can you do? | Why is this important? |
|------------------|------------------------|
| Rebuild the Financial reporting data mart. | When you move Dynamics AX databases between environments or make other invasive changes to the environment, the Financial reporting database might have to be rebuilt. A Windows PowerShell script is now provided to rebuild the database for you. |
| You can no longer select report designer options that aren't valid. | Several report designer options that were used in the in-market versions of Management reporter don't apply to this version of Dynamics AX. These options were related to financial report design, output, and linking. These options have been removed from the financial report designer to prevent user errors. |

## Financial management

| What can you do? | Why is this important? |
|------------------|------------------------|
| Generate positive pay files for accounts payable payments. | Positive pay files can be generated to help prevent check fraud. |

## Warehouse and production

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Define a warehouse work policy that controls the creation of work for a set of products at specific locations.</td>
<td>Warehouse processes don't always include work. By using the new warehouse work policy, you can prevent work from being created for raw material picking and put-away of finished goods for a set of products at specific locations.</td>
</tr>
<tr>
<td>Specify that a production output location isn't license plate–controlled.</td>
<td>You can now specify that a product output location isn't license plate–controlled. For example, this feature is useful when an upstream production order reports items as finished directly to a location that acts as production input location for a downstream production order.</td>
</tr>
<tr>
<td>Support BOMs that include items with different product dimensions of the same item.</td>
<td>When using one or multiple of the product dimensions in production, you can have situations where you would like to produce an item, based on a different variant of the same item. For more information, see <a href="/archive/blogs/axmfg/support-for-boms-that-includes-items-with-different-product-dimensions-of-the-same-item">this blog</a>.</td>
</tr>
<tr>
<td>Production orders with circular structures at the first level of their BOMs are excluded from BOM level calculation for material resource planning.</td>
<td>It is not possible to assign correct BOM levels to product variants for production orders that cause circularity in the BOM hierarchy.</td>
</tr>
<tr>
<td>Calculate separate BOM levels for material resource planning and cost calculation:
<ul>
<li>For material resource planning, BOM levels are calculated in the new <strong>ReqItemLevel</strong> table. Ended production orders are ignored in the calculation.</li>
<li>For production cost calculation, BOM levels are calculated in the <strong>InventTable</strong>. Ended production orders are included in the calculation.</li>
</ul>
</td>
<td>
<ul>
<li>When running material resource planning, for example, master planning plan scheduling and explosion, only BOM levels used for material resource planning need to be recalculated. In other words, there is no need to calculate BOM levels used for production costing calculation.</li>
<li>When running costing operations, for example, inventory closing, only BOM levels used for production costing calculation need to be recalculated.</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Additional resources

[What's new or changed in finance and operations home page](whats-new-changed.md)

[New or updated task guides (May 2016)](new-updated-task-guides-available-may-2016.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
