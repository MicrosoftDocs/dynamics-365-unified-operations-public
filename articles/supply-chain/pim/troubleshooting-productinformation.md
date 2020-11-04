---
# required metadata

title: Troubleshoot product information
description: This topic describes how to fix issues that you might encounter while working with Product Information.
author: SmithaNataraj
manager: tfehr
ms.date: 11/04/2020
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
ms.search.validFrom: 2020-11-04
ms.dyn365.ops.version: 10.0.15

---
# Troubleshoot product information

This topic describes how to fix common issues that you might encounter while working with product information.

## I can't delete a released product

### Issue description

You can only delete a released product and all its variants when the released product doesn't have any related transactions.

### Issue resolution

Do the following steps to delete a released product or product master:

1. Close all open transactions for the items.
1. Reduce inventory to 0.
1. Perform inventory closing.
1. Delete all product variants for the product master that you want to delete.

## Can I change the item number of a released product?

In most cases, you can't edit item numbers for released products because that would lead to corrupted data. You can do it if and only if you need to repair data corruption caused by a previous rename of the primary key of a released product, as mentioned in the list of [removed or deprecated features for Finance and Operations 10.0.0 with Platform update 24](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md#finance-and-operations-1000-with-platform-update-24). 

If you would like to be able to edit item numbers for released products, please [vote this idea on Ideas portal](https://experience.dynamics.com/ideas/idea/?ideaid=660fcb15-875d-ea11-b698-0003ff68bc25).

## Flushing Principle is not being defaulted from the product onto the bill of materials Line.

### Issue description

When adding an item to a bill of materials (BOM) Line, the system doesn't use the default flushing principle information set up for the item. In other words, the flushing principle from the item doesn't show up on the BOM Line form.

### Issue resolution

If you specify a flushing principle on the BOM line, then that flushing principle will apply for that BOM line. Otherwise, even though the flushing principle from the item isn't shown on a BOM Line, the flushing principle set on the item will still apply for that line if the flushing principle is blank or not set on the BOM line.

This is not the way the defaulting logic usually works for other features in Supply Chain Management. However, we can't change this design because doing so might break some existing customizations that assume the current behavior.

## The system lets me save duplicate barcodes for different items or for the same item with different dimension.

The system doesn't currently enforce unique barcodes, and adding this restriction would be a breaking change. We have evidence that some existing customer installations would indeed be broken by this change. We will consider a broader design change to enable this feature in the future.

## I get this error when editing item record templates: "The warehouse location cannot be created because the item is not stocked. To stock items, the Stocked product option on the associated item model group must be selected."

### Issue description

This error is shown if you create a template for an item that isn't stocked. You will see it when doing the following procedure:

1. Open a released product that isn't stocked.
1. On the Action Pane, open the **Options** tab and select **Record info**.
1. The **Record information** dialog box opens. 
1. Select **Company accounts template**. If your selected product isn't stocked, you will see the message, "The warehouse location cannot be created because the item is not stocked. To stock items, the Stocked product option on the associated item model group must be selected"

### Issue resolution

Creating product templates requires extra product-specific logic, so you can't use the generic **Company accounts template** button for this purpose. Instead, do the following steps:

1. Open a released product.
1. On the Action Pane, open the **Product** tab and then, from the **New** group, select **Template > Create shared template**.

## Product attribute help text is not defaulted onto the released product.

When description and help text is added in the product attributes, the description and help text aren't visible or defaulted in the released products. This is by design.

## Quantity defaulted is different when registered from a BOM than when registered from a BOM Version.

### Issue description

When adding an item to a BOM, the quantity defaults to 1 rather than the quantity defined in the **Min. order quantity** field on the **Default order settings** page for a selected product. When adding the item from the BOM version (with the item and variant selected), then the defaulted quantity does take into account the minimum set in default order settings for the specific dimensions.

### Issue resolution

This is the expected behavior, though it is a known issue that the logic is different in the BOM and the BOM version. A change of behavior could affect many different customer scenarios, so this behavior will not be changed.

## In the released product details, I can't change the attached images that were uploaded from the product document attachment data entity.

### Issue description

This issue can occur when you attach an image on and an item using the *Product document attachment* data entity. As a result, the item image is shown against the item, but when you select **Change image**, nothing is shown in the list of uploaded images, nor are any attachments shown against the item.

### Issue resolution

The `EcoResProductDocumentAttachmentEntity` entity (*Product document attachments*) imports document attachment for *products*, but not for *released products* (also known as *items*). To see the attachments on the item on the **Released product details** page, you must use the `EcoResReleasedProductDocumentAttachmentEntity` entity (*Released product document attachments*) instead.

## The Flow connector shows the error message "Update not allowed for field 'ProductNumber'"

### Issue description

The issue occurs when trying to update the **Product number** field using the *Released products* entity V2 and Microsoft Flow.

### Issue resolution

This is working as expected. The ability to edit the product number for a released product was removed (to avoid data corruption) as of Dynamics 365 Finance and Operations 10.0.0 with platform update 24. In exceptional cases (in other words, to repair data corruption caused by a previous rename of the primary key of a released product), you can ask Microsoft Support to temporarily remove this restriction.

## I can't create a released product variant in another legal entity

### Issue description

If you try to release a product master without variants, and then create the variants in each of the legal entities (companies) as needed, you won't be able to release using the "variant suggestions" option or to create the variants manually.

### Issue resolution

This is working as designed. The product master and the dimensions that the master could take are kept at a "shared" level. Because these relations are kept at a shared level, it isn't possible to create the available dimensions for a shared product master in the specific legal entity where they are released and then replicate the process in each legal entity where needed. Instead, you must change your release process to adapt to the designed process.

The process to release products is to create the shared product master and the dimensions that could be released to the legal entities and using variant suggestions or the combinations needed can be manually created and then released to the needed companies. <!-- KFM: This isn't clear. I'm not sure how to fix it. -->

Alternatively, you could directly create the released product.

## When I release a variant in another company, I get the error "Product variant with specified dimensions has already been created."

### Issue description

If a product variant has already been released in a company A, releasing the variant in company B using the **New** button on the **Released product variants** page will show the error "Product variant with specified dimensions has already been created."

### Issue resolution

The **New** button on the **Released product variants** page creates the variant and release it in the company context. If the variant has already been created, you can't use the **New** button to release it in another company.

To fix the issue, go to the **Product master** page and select **Release product** to release the existing variant in the desired company.
