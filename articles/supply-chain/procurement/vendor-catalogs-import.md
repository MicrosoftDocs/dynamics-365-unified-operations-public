---
# required metadata

title: Import vendor catalogs
description: This topic describes the process to import vendor catalog data.
author: mkirknel
manager: AnnBe
ms.date: 03/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: VendProspectiveVendorRegistrationRequests  
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2018-04-20 
ms.dyn365.ops.version: 7.3
---

# Onboard vendors
[!include[banner](../includes/banner.md)]
---

Vendor catalogs import
======================

In Microsoft Dynamics AX, purchasing professionals can create and maintain
catalogs for company employees to use when they order items and services for
internal use. When you create a procurement catalog you can add the items and
services that you make available to employees, either by importing the vendor
catalog data or by adding the vendor catalog data to the product master
manually. If you use the catalog import process the vendor can send you the
product catalog data and you can upload it by using the Microsoft Dynamics AX
client.

The product data that the vendor submits to you, in the form of a catalog
maintenance request (CMR) file, must be in XML file format. The CMR file should
contain all of the details for the products that the vendor supplies to your
company.

Importing vendor catalog data
-----------------------------

To import vendor catalog data, you must complete the following tasks:

1.  Set up a project in data management workspace. Here you have to define your
    data mapping rules.

2.  Set up a procurement category hierarchy, and assign your vendors to
    procurement categories. If you use commodity codes, add the commodity codes
    to the procurement categories.

3.  Configure the vendor for catalog import.

4.  Configure workflow for catalog import.

5.  Create a CMR file template and share this with your vendor.

6.  Create a vendor catalog. The catalog maintenance request (CMR) files that
    you receive from your vendor are grouped in this catalog.

7.  Upload the CMR file.

8.  Review, approve, or reject the products in the vendor catalog. Details that
    can be reviewed include the product name, description, pricing, or order
    quantity requirements. Approved products are added to the product master and
    are released to the selected legal entities. Only approved products can be
    added to the procurement catalog. The products are now automatically mapped
    to the procurement categories in AX.

Generate a catalog import file template

The catalog import file template is an industry-standard XSD file that you use
to create a CMR file for a vendor’s products. You can use the CMR file to create
a new catalog, replace an existing catalog, or modify an existing catalog.

1.  Click **Procurement and sourcing** \> **Common** \> **Catalogs** \> **Vendor
    catalogs**.

2.  On the **Vendor catalogs** list page, double-click the catalog that you want
    to work with.

3.  To download a current catalog import template (XSD file), in the **Update
    catalog** form, on the **Action Pane**, on the **Catalogs** tab, in the
    **Related information** group, click **Generate catalog template**. The only
    available option is**:**

    -   **Procurement category** – Generate a catalog template that includes the
        procurement categories in which the vendor is authorized to provide
        products.

In the **Save as** dialog box, select the location where you want to store the
catalog file template and save the file

For more information about how to [set up system etc.] and for examples, see
[reference blog post]
