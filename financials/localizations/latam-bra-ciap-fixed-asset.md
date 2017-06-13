---
# required metadata

title: Acquire and dispose a CIAP fixed asset
description: Fiscal books can acquire and dispose of fixed assets that are ICMS tax long term return.
author: v-gonode
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: v-gonode
ms.search.validFrom: 2017-06-30]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# CIAP fixed asset

## Acquire a CIAP fixed asset
Use this functionality to register in Fiscal books module the acquisition of a fixed asset controlled by the ICMS tax long term return.

1.	On the **All purchase orders** page, in the **Vendor account** field, select a vendor.
2.	Click **Add line**.
 - 	Fill in the **Item number**, **CFOP**, **Quantity**, **Unit price** fields.
3.	Expand the Line details section.
4.	Click the **Fixed assets** tab.
5.	Select **Yes in the New fixed asset?** field.
6.	In the **Fixed asset group** field, select a fixed asset group.
7.	On the **Financial dimensions** tab, fill out the **CostCenter** and **Filial** fields.
8.	Click **Confirm**.
9.	On the **All purchase orders** page, click the link to select a Purchase order.
10.	On the Action Pane, click **Invoice** > **Default from: Product receipt quantity**. In the **Default quantity for lines** field, select a quantity.
11.	Click **OK**.
12.	Fill in the **Document model**, **Access key**, **Invoice date** and **Posting date** fields.
13.	Click **Post**.
14.	On the **Booking period** page, click **Create new booking period**.
15.	Fill in the **Fiscal establishment**, **Month** and **Year** fields.
16.	Click **OK**.
17.	Click **Sync** > **OK**.
18.	Click **ICMS** > **ICMS tax assessment** > **OK**.
19.	On the **All CIAP fixed assets** page, click the link to select a CIAP asset ID.
20.	Expand the Line details section.
21.	On the **CIAP Report** page,in the **Fiscal establishment** field, enter a fiscal establishment.
22.	Click **OK**.

## Dispose of a CIAP fixed asset
Use this functionality to register in Fiscal books module the disposal of a fixed asset controlled by the ICMS tax long term return.

1.	On the **All free text invoices** page, click **New**.
2.	Fill in the **Fiscal establishment ID**, **Customer account**, **Date**, **Description**, **Main account**, **CFOP**, **Sales tax group**, **Item sales tax group**, **Quantity** and **Unit price** fields.
3.  Expand the **Line details** section, > in the **Fixed asset number** field, enter a fixed asset.
4.	Click **Post**.
5.	Expand the **Bill of lading** section, fill in the **Carrier name**, **Volume type**, **Volume quantity**, **Net weight**, **Gross weight** fields.
6.	Click **OK**.
7.	On the **Export/import NF-e process** > **OK**.
8.	One the **Booking period** page > **Create new booking period**.
9.	Fill in the **Fiscal establishment**, **Month** and **Year** fields.
10.	Click **OK**.
11.	Click **Sync** > **OK**.
12.	Click **ICMS** > **ICMS tax assessment** > **OK**.
13.	On the **All CIAP fixed assets** page, click the link to select a CIAP asset ID.
14.	On the **CIAP Report**, in the **Fiscal establishment** field, select a fiscal establishment.
15.	Click **OK**.

