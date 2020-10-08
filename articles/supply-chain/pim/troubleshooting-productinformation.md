---
# required metadata

title: Troubleshoot Product Information
description: This topic describes how to fix issues that you might encounter while working with Product Information.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Product Information
This topic describes how to fix common issues that you might encounter while working with Product Information.

## Unable to delete a released product
It is possible to delete a released product and all its variants, only if the released product does not have any related transactions.

### Resolution
Follow the steps to be able to delete a released product or product master:
1. Close all open transactions for the items
2. Reduce inventory to 0
3. Perform inventory closing
4. Delete any product variants for the product master that you want to delete. 

##  Is it possible to rename a released product? 
		
### Resolution
It is not possible to rename item numbers for released products as it would lead to corrupted data. We only allow it if and only if you need to repair data corruption caused by a previous rename of the primary key of a released product, as we indicate in https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#finance-and-operations-1000-with-platform-update-24
Please vote the idea on Ideas portal: https://experience.dynamics.com/ideas/idea/?ideaid=660fcb15-875d-ea11-b698-0003ff68bc25

## Flushing Principle is not being defaulted from the product onto the BOM Line.
When adding an item to a BOM Line, the system is not defaulting the Flushing principle information previously set up in the Item, i.e. the flushing principle from the iteam does not show up on the BOM Line form.

**Resolution**
If a Flushing Principle is specified on the BOM line, then that will be the flushing principle that would be applicable for the BOM line. Otherwise, though the Flushing principle from the item does not show up on the BOM Line, the Flushing principle that is set on the Item will be applicable for the BOM line if the Flushing principle is blank/not set on the BOM line.

This is not the way the usual defaulting logic works in the product in general. However this design cannot be changed, because it might be breaking some customizations which are assuming the current behavior.

## It is possible save duplicate barcode for different items or same item with different dimension.
Barcode uniqueness is not enforced currently. Putting this restriction on the metadata would be a breaking change - and we do have evidence that there are customers who will be broken by this change. We will consider a broader design change to enable this feature in the future.

## Error when editing Items record templates: 'The warehouse location cannot be created because the item is not stocked. To stock items, the Stocked product option on the associated item model group must be selected'
This happens when creating template for items that are not stocked, using the Options > Record info > Company accounts template button.

**Resolution**
Creating product templates require extra product-specific logic and so the generic Company accounts template button cannot be used for this purpose. One must used the following button in the Action pane: Product > New > Template > Create shared template instead.

## Product attribute help text is not defaulted onto the Released product
When description and help text is added in the product attributes, the description and help text are not visible or defaulted in the released products. This is by design. 

## Quantity defaulted is different when registered from BOM and when registered from BOM Version 
When adding an item to a BOM, the quantity defaulted is 1 and not the quantity defined in the minimum field in the default order settings. When adding the item from the BOM version (item and variant selected), then the defaulted quantity takes into account the minimum set in default order settings for the specific dimensions.

**Resolution**
This is the expected behavior and is a known issue that the logic is different in the BOM and the BOM version. A change of behavior could affect many different customer scenarios, so this behavior will not be changed.

## Unable to change the attached images that were uploaded from the Product Document Attachment data entity, in the Released product details. 
**Business Scenario**
1. Attach images on items through the Product document attachment data entity. 
2. Result: The item image is showing against the item but when they click on change image, nothing shows in the list of uploaded images. Also, no attachments are showing against the item either. 

**Resolution**
The EcoResProductDocumentAttachmentEntity entity ("Product document attachments") will import document attachment for the Products, not the Released products (aka items).
In order to see the attachments on the item in the Released product details form, the EcoResReleasedProductDocumentAttachmentEntity entity ("Released product document attachments") must be used instead.

## Flow connector getting error message  "update not allowed for field 'ProductNumber'
The issue occurs when trying to update the "Product number" field using the released products entity V2 and flow.

**Resolution**
This is working as expected. This functionality was removed (to avoid data corruption) as of Finance and Operations 10.0.0 with Platform update 24. In exceptional cases (in other words, to repair data corruption caused by a previous rename of the primary key of a released product), it is possible to request Microsoft to temporarily remove this restriction on the rename primary key operation for released products.

## Cannot create a released product variant in another legal entity
When trying to release the master without the variants and create the variants in each of the legal entities where needed, it is not possible to release via "variant suggestions" or create them manually. 

**Cause**
This is working as designed. The product master and the dimensions that the master could take are kept at a "shared" level. As these relations are kept at a shared level it is not possible to create the available dimensions for a shared product master in the specific company where they are released and then replicate the process in each legal entity where needed. The customer must change the release process to adapt to to the designed process:

**Resolution**
The process to release products is to create the shared product master and the dimensions that could be released to the legal entities and using variant suggestions or the combinations needed can be manually created and then released to the needed companies. 

An alternative approach, is to directly create the released product. 

## Releasing the variant in another company throws error 'Product variant with specified dimensions has already been created'
If a product variant has already been released in a company A, releasing the variant in another company B using the New button in the Released product variants form will throw an error "Product variant with specified dimensions has already been created.".

**Possible Cause**
The New button in the Released product variants form creates the variant and release it in the company context. If the variant has already been created, the New button cannot be used to release it in another company. 

**Resolution**
Go to the Product Master form and use the Release product button to release the existing variant in the desired company.
