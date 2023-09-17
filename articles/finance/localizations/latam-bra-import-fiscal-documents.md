---
title: Import fiscal documents for Brazil
description: This article describes the functionality for direct import fiscal documents that is available for the Brazilian localization.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 270204
ms.assetid: b2389297-1359-498f-b755-c20574248ae1
ms.search.form: BrazilParameters, FiscalDocument_BR, PurchImportDeclaration_BR, PurchImportDeclarationList_BR, VendEditInvoice
---

# Import fiscal documents for Brazil

[!include [banner](../includes/banner.md)]

This article describes the functionality for direct import fiscal documents that is available for the Brazilian localization.

You can issue a direct import fiscal document when you create a purchase order to import items from a foreign vendor. An import fiscal document records transit information about the items that you import. The import fiscal document is used to release items from customs and to validate the entry of the items in the warehouse of the legal entity. You must specify the import declaration information (the addition number and import declaration number) for a purchase order that is issued to import items from a foreign vendor before you post the purchase order. A direct import fiscal document includes the following information:

-   Calculation of Brazilian taxes for the direct import fiscal document
-   Introductory information about the import declaration
-   Generation of the NF-e (Brazilian electronic fiscal document model 55)
-   A printed DANFE document
-   Integration with the **Fiscal books** module

**Note:** You can also issue an import fiscal document when you create a purchase order to import services from a foreign vendor. When you import a service, it's not required that you specify the import declaration number and addition number for the vendor invoice. Before you can generate an import fiscal document, you must select the **Generate incoming fiscal document** option for the foreign vendor on the **Vendors** page. You can use **Cancel** to cancel an incorrect import fiscal document. You can use **Inquire** to load all fiscal documents, together with the related information, onto the **Fiscal document viewer** page.

## Prerequisites
Before you can create and post a direct import fiscal document, you must set the following parameters in the **Import declaration** field group on the **Fiscal document** tab of the **Brazilian parameters** page:

-   **Line amount is based on** – Select one of the following values:
    -   **FOB** – The line amount in the fiscal document is equal to the gross line amount.
    -   **CIF + II** – The **Line amount** in the fiscal document is equal to the gross line amount plus all miscellaneous charges (except SISCOMEX and customer miscellaneous charges) that are related to the setup of the import process for the vendor invoice line.
-   **Text ID** – Select the text that is used to print import declaration information as additional information in the printed fiscal document or DANFE.

## Import declaration
After you've created and confirmed the purchase order for a foreign vendor, and before the vendor invoice is posted, you can enter information about the import declaration. On the **Foreign trade** page, select the import declaration number that you previously created, or create a new import declaration number.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Import declaration number</td>
<td>The identification number of the import declaration.</td>
</tr>
<tr class="even">
<td>Date</td>
<td>The date when the import declaration is issued.</td>
</tr>
<tr class="odd">
<td>Port</td>
<td>The identification code of the port where the imported item is loaded.</td>
</tr>
<tr class="even">
<td>Description (port description)</td>
<td>The name and description of the port.</td>
</tr>
<tr class="odd">
<td>Port state</td>
<td>The state where the port is located.</td>
</tr>
<tr class="even">
<td>DI type</td>
<td>The type of import declaration:
<ul>
<li><strong>Import declaration</strong> – A detailed import declaration is generated.</li>
<li><strong>Simplified import declaration</strong> – A summarized import declaration is generated.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Nationalization date</td>
<td>The date when the item is nationalized in Brazil.</td>
</tr>
<tr class="even">
<td>Draw back number</td>
<td>The identification code of the draw-back operation.</td>
</tr>
<tr class="odd">
<td>Transport mode</td>
<td>The type of transportation.</td>
</tr>
<tr class="even">
<td>ARFMM</td>
<td>The amount of additional freight for transportation of the <strong>Marine</strong> type.</td>
</tr>
</tbody>
</table>

## Scenario overview
For this scenario, you must create and post a direct import fiscal document.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Background</td>
<td>The company imports items and must issue an entrance nota fiscal for the imported items with the correct taxes calculated for the items to be released in Customs. The following people/roles are involved:
<ul>
<li>Alicia (Purchasing agent)</li>
<li>April (Accounts payable coordinator)</li>
<li>Sammy (Shipping and receiving)</li>
</ul></td>
</tr>
<tr class="even">
<td>User goals</td>
<td><ul>
<li>Have the sales tax (II, IPI, PIS, COFINS, ICMS) correctly calculated for the import nota fiscal, according to the rules that are specified by the government.</li>
<li>Print the entrance nota fiscal.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Scenario steps</td>
<td><ol>
<li>Alicia creates a purchase order for a foreign vendor. The purchase order uses the foreign currency that the item price was negotiated in.</li>
<li>The Customs agent (despachante aduaneiro) notifies Alicia that the items arrived in the port or at the airport, and provides the estimated amount of sales taxes that must be paid before the port or airport can release the items.</li>
<li>April generates a prepayment in the company&#39;s currency to the Customs agent. April uses the estimated amount of sales tax as a reference.</li>
<li>Customs (Aduana) generates one import declaration document per vendor. This import declaration document is delivered to the Customs agent. It&#39;s based on the taxes that are presented in the import declaration, and generates and pays the tax payment documents (GARE).</li>
<li>The Customs agent sends a copy of the import declaration document to April. April then adjusts the miscellaneous charge amounts that are related to freight, insurance, and SISCOMEX in the purchase orders that are related to the import process. (The distribution of miscellaneous charges is done manually by April.)</li>
<li>April prepares the import nota fiscal by selecting the purchase orders and purchase order items, and then enters the import declaration number in the purchase order. April also enters the addition number in the posting invoice lines per purchase order item.</li>
<li>April checks the sales tax amount before posting the import nota fiscal against the import declaration. When the sales tax amounts of the import nota fiscal and import declaration match, April posts the invoice. If the amounts don&#39;t match, April adjusts the sales tax amounts of the invoice that must be posted. <strong>Note:</strong> Because the goods aren&#39;t yet in the company&#39;s possession, a different warehouse can be used on each purchase order line that is related to the import nota fiscal.</li>
<li>April sends the printed vendor invoice to the Customs agent.</li>
<li>The Customs agent joins the documents that are required in order to release the goods: the import declaration, GARE (taxes paid), and printed import nota fiscal (self-nota fiscal). The Customs agent then requests that the port or airport release the goods.</li>
<li>The goods are transported to the company’s warehouse.</li>
<li>Sammy receives the goods when they arrive at the company and transfers the items from the temporary warehouse to the effective warehouse.</li>
<li>Alicia uses the complementary invoice to add the Customs agent expenses, plus national freight or other costs that are related to the import process after nationalization of goods (entrance into the Brazilian territory) occurs, to the item costs of the original import nota fiscal.</li>
</ol></td>
</tr>
</tbody>
</table>







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
