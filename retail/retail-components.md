---
# required metadata

title: Components of Dynamics 365 for Operations - Retail
description: This topic describes the various components that make up Microsoft Dynamics 365 for Operations - Retail.
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221954
ms.assetid: 8fe1b080-00d4-41ae-b047-10da160877ab
ms.search.region: Global
ms.search.industry: Retail
ms.author: yabinl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Components of Dynamics 365 for Operations - Retail

This topic describes the various components that make up Microsoft Dynamics 365 for Operations - Retail.

Dynamics 365 for Operations - Retail provides mid-market and large retailers with a complete head office and point of sale (POS) solution that includes support for online and brick-and-mortar stores. It can help retailers increase financial returns, improve service, manage growth, reach customers, and streamline efficiencies.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Component</strong></td>
<td><strong>Function</strong></td>
</tr>
<tr class="even">
<td>Retail headquarters</td>
<td>Retail headquarters for Dynamics 365 for Operations can be used to manage a chain of stores as one enterprise. It controls daily operations and tracks sales information for every store in the chain. Retail Scheduler coordinates communication between Dynamics 365 for Operations and the stores. Retail headquarters can be used with any POS or online store system that can receive and transmit the required data. <strong>Important:</strong> Building a custom POS or online store solution for Dynamics 365 for Operations is a complex task that requires extensive planning, development, and testing.</td>
</tr>
<tr class="odd">
<td>Retail POS</td>
<td>Dynamics 365 for Operations supports two types of POS experience:
<ul>
<li><strong>Cloud POS</strong> is a browser-based POS that can be used on mobile devices.</li>
<li><strong>Retail Modern POS</strong> (MPOS) can be used on clients such as PCs, tablets, and phones to process sales transactions, customer orders, and daily operations, and to perform inventory management.</li>
</ul></td>
</tr>
<tr class="even">
<td>Retail Server</td>
<td>Retail Server provides an OData web API that lets both employees and customers access information and perform tasks by using both Retail POS clients and the online store.</td>
</tr>
<tr class="odd">
<td>Hardware Station</td>
<td>Retail Hardware Station provides services that enable Retail POS clients, and peripherals such as printers, cash drawers, and payment devices to communicate with Retail Server.</td>
</tr>
<tr class="even">
<td>Retail Store Scale Unit</td>
<td>Retail Store Scale Unit is a set of features that supports selling products in a store that does not have constant Internet connectivity to a back office or headquarters (HQ). The Store Scale Unit is designed specifically for in-store operation, and enables cross terminal transactions and shift operations even when you are not connected to the back office.</td>
</tr>
<tr class="odd">
<td>Commerce runtime</td>
<td>Commerce runtime (CRT) serves as the core engine that supports the business logic across the various channels. Commerce runtime contains a data access layer, services layer, workflow layer, and an application programming interface (API) layer.</td>
</tr>
<tr class="even">
<td>Channel database</td>
<td>A channel database holds Retail data for one or more retail channels, such as online stores or brick-and-mortar stores.</td>
</tr>
<tr class="odd">
<td>e-Commerce platform SDK</td>
<td>The comprehensive e-Commerce platform lets you plug in a front-end online store that can take advantage of the omni-channel services of the platform. The software development kit (SDK) also consists of a sample online store that demonstrates how you can take advantage of the platform.</td>
</tr>
<tr class="even">
<td>Retail SDK</td>
<td>The Retail SDK contains sample source code and templates that you can use to customize the Retail system.</td>
</tr>
</tbody>
</table>



