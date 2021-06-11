---
# required metadata

title: Troubleshoot product information
description: This topic describes how to fix issues that you might encounter while you work with product information.
author: SmithaNataraj
ms.date: 11/04/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
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

This topic describes how to fix issues that you might encounter while you work with product information.


## The default flushing principle from the product isn't being entered on the bill of materials line.

### Symptoms

When you add an item to a bill of materials (BOM) line, the system doesn't use the default flushing principle information that is set up for the item. In other words, the flushing principle from the item doesn't appear on the **BOM line** page.

### Resolution

If you specify a flushing principle on a BOM line, it will apply to that BOM line. However, if the flushing principle is blank, or if it isn't set on a BOM line, the flushing principle that is set on the item will still apply to that BOM line, even though it isn't shown on the BOM line.

The defaulting logic for other features in Microsoft Dynamics 365 Supply Chain Management doesn't usually work in this way. However, the current behavior can't be changed. Otherwise, some existing customizations that rely on it might be broken.

## The system lets me save duplicate bar codes for different items or for the same item that has different dimensions.

The system doesn't currently enforce unique bar codes, and the addition of this restriction would be a breaking change. In fact, Microsoft has evidence that some existing customer installations would be broken by this change. However, we will consider a broader design change to enable this feature in the future.

## I receive the following error message when I edit item record templates: "The warehouse location cannot be created because the item is not stocked. To stock items, the Stocked product option on the associated item model group must be selected."

### Symptoms

This issue occurs if you follow these steps to try to create a template for an item that isn't stocked.

1. Open a released product that isn't stocked.
1. On the Action Pane, on the **Options** tab, select **Record info**.
1. In the **Record information** dialog box, select **Company accounts template**.

In this case, you receive the following error message:

> The warehouse location cannot be created because the item is not stocked. To stock items, the Stocked product option on the associated item model group must be selected.

### Resolution

The process of creating product templates requires extra product-specific logic. Therefore, you can't use the generic **Company accounts template** button for this purpose. Instead, follow these steps.

1. Open a released product.
1. On the Action Pane, on the **Product** tab, in the **New** group, select **Template \> Create shared template**.

## Default Help text that is added in product attributes isn't entered in a released product.

A description and Help text that are added in the product attributes aren't visible or entered by default in the released products. This behavior is by design.

## The default quantity that is entered differs when it's registered from a BOM and when it's registered from a BOM version.

### Symptoms

By default, when you add an item to a BOM, the quantity is set to 1 instead of the quantity that is defined in the **Min. order quantity** field on the **Default order settings** page for a selected product. However, when you add an item from a BOM version, and the item and variant are selected, the quantity that is entered by default takes into account the minimum quantity that is set in the default order settings for the specific dimensions.

### Resolution

This behavior is expected. However, the fact that the logic differs in the BOM and the BOM version is a known issue. Nevertheless, this behavior won't be changed, because a change could affect many different customer scenarios.

## In the released product details, I can't change the attached images that were uploaded from the Product document attachments data entity.

### Symptoms

This issue can occur when you attach an image to an item by using the *Product document attachments* data entity. In this case, the item image is shown for the item. However, if you select **Change image**, nothing is shown in the list of uploaded images. Additionally, no attachments are shown for the item.

### Resolution

The *EcoResProductDocumentAttachmentEntity* entity (*Product document attachments*) imports document attachments for *products* but not for *released products*. (Released products are also known as *items*.) To view the attachments for an item on the **Released product details** page, you must use the *EcoResReleasedProductDocumentAttachmentEntity* entity (*Released product document attachments*) instead.

## The Microsoft Flow connector shows the following error message: "Update not allowed for field 'ProductNumber'."

### Symptoms

This issue occurs if you try to update the **Product number** field by using the *Released products* entity V2 and Microsoft Flow.

### Resolution

This behavior is expected. The ability to edit the product number for a released product was removed in Dynamics 365 Finance and Operations 10.0.0 with platform update 24 to help prevent data corruption. In exceptional cases, where you must repair data corruption that was caused by a previous rename of the primary key of a released product, you can ask Microsoft Support to temporarily remove this restriction.

## I can't create a released product variant in another legal entity.

### Symptoms

If you try to release a product master without variants, and then create the variants in each legal entity (company) as they are required, you won't be able to release the variants by using variant suggestions. You also won't be able to manually create the variants.

### Resolution

This behavior is by design. The relations of a product master and the dimensions that the master can take are kept at a shared level. Therefore, you can't create the available dimensions for a shared product master in the specific legal entity where those dimensions are released and then replicate the process in each legal entity where the dimensions are required. Instead, you must change your release process to adapt to the designed process.

Here is the process for releasing products.

1. Create the shared product master and the dimensions that can be released to the legal entities.
1. Release the products to the legal entities either by using variant suggestions or by manually adding the combinations that should be released.

Alternatively, you can directly create the released product.

## When I release a variant in another company, I receive the following error message: "Product variant with specified dimensions has already been created."

### Symptoms

If a product variant has already been released in a company A, and you try to release it in company B by using the **New** button on the **Released product variants** page, you will receive the following error message:

> Product variant with specified dimensions has already been created.

### Resolution

The **New** button on the **Released product variants** page creates the variant and releases it in the company context. If the variant has already been created, you can't use the **New** button to release it in another company.

To fix the issue, open the **Product master** page, and select **Release product** to release the existing variant in the desired company.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]