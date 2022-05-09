---
# required metadata

title: Import vendor catalogs
description: This topic describes the process to import vendor catalog data.
author: GalynaFedorova
ms.date: 03/20/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendProspectiveVendorRegistrationRequests, CatVendorCatalogDetails, CatVendorCatalogReleaseApprovedProducts, CatVendorCMRDetails, CatVendorCatalogProductPerCompanyStatus, CatVendorMaintenanceEventLog, CatVendorCatalogReviewTool, CatVendorCatalogFileUpload, CatVendorCatalogMaintenanceRequest, CatVendorCatalogFileInLegalEntity, CatVendorCatalogSchema, CatVendorCatalogFilePreviewPane, CatVendorCatalogImportParameter
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2018-04-20 
ms.dyn365.ops.version: 7.3
---

# Import vendor catalogs

[!include[banner](../includes/banner.md)]

## Vendor catalogs import

In Dynamics 365 Supply Chain Management, purchasing professionals can create and maintain
catalogs for company employees to use when they order items and services for
internal use. To create a procurement catalog, you can add the items and
services that you want to make available to employees, either by importing the product
catalog data or by manually adding the product catalog data to the product master. 

You can upload catalog data submitted by a vendor from the Microsoft Dynamics 365 client.

The product data that a vendor submits to you, in the form of a catalog
maintenance request (CMR) file, must be in XML file format. The CMR file should
contain the details for the products that the vendor supplies to your
company.

## Import vendor catalog data

To import vendor catalog data, you must complete the following tasks:

1. Set up a project in the Data management workspace where you have defined your
    data mapping rules. Select **Data management** and then select **Set up roles for data projects**.

2. Set up a procurement category hierarchy, and assign your vendors to
    procurement categories. If you use commodity codes, add the commodity codes
    to the procurement categories. For information about setting up a procurement category hierarchy, see [Set up a procurement category hierarchy](../procurement/tasks/set-up-procurement-category-hierarchy.md).

3. Configure the vendor for catalog import. Select a vendor, and then select **Procurement** > **Set up** > **Configure vendor for catalog import**.

4. Configure workflow for catalog import. Create a CMR file template and share this with your vendor.

5. Select **Procurement and sourcing** \> **Common** \> **Catalogs** \> **Vendor
    catalogs** to create a vendor catalog. The catalog maintenance request (CMR) files that
    you receive from your vendor are grouped in this catalog. 

6. Upload the CMR file.

7. Review, approve, or reject the products in the vendor catalog. The products are automatically mapped
    to the procurement categories. 

Approved products are added to the product master and are released to the selected legal entities. Only approved products can be added to the procurement catalog.

## Generate a catalog import file template

The catalog import file template is an XSD file that you use
to create a CMR file for a vendor's products. You can use the CMR file to create
a new catalog, replace an existing catalog, or modify an existing catalog.

1. Select **Procurement and sourcing** \> **Catalogs** \> **Vendor
    catalogs** and double-click the catalog that you want
    to work with.

2. Download a current catalog import template (XSD file). On the **Update
    catalog** page, on the **Action Pane**, on the **Catalogs** tab, in the
    **Related information** group, click **Generate catalog template** and select **Procurement category**.

    - With the **Procurement category** option you can generate a catalog template that includes the procurement categories in which the vendor is authorized to provide products.

3. In the **Save as** dialog box, select the location where you want to store the
catalog file template and save the file.

For more information and for examples, refer to this blog post: [Vendor catalogs in Dynamics AX](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/25/vendor-catalogs-in-dynamics-ax/).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]