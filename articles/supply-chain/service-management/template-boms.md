---
title: Template BOMs  
description: A template bill of materials (BOM) provides a standardized list of components for service objects that are serviced regularly. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMATemplateBOMTable
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Template BOMs

[!include [banner](../includes/banner.md)]

A template bill of materials (BOM) provides you with a standardized list of components for service objects that are serviced regularly. The components that are listed in the template BOM represent the individual subcomponents of the service object. By applying a template BOM to a service object, you can keep a record of the subcomponents that were replaced on the service object.

To apply a template BOM to a service agreement or a service order, you attach it to a service object relation.

> [!NOTE]
> You can apply only one template BOM to a service object.

## Create a template BOM

The following table contains information about the various methods that you can use to create a template BOM.

| Method | Description |
|--|--|
| Production | The template BOM is based on a production order. This option is applicable only if you operate in a production environment. The benefit is that you have a current, detailed listing of the components that make up an item. |
| Item BOM | The template BOM is based on an item BOM. The item BOM, unlike the production BOM, is a static list of the components that make up an item. |
| Existing template | The template is based on an existing template BOM. |
| Manual | If you know what spare parts are typically replaced on a service object, you can create your template BOM manually. This method helps make sure that the components that are included in the template reflect the actual requirements of your workplace. |

## Apply the template BOM to a service agreement or service order

You can apply a template BOM to a service agreement, a service order, or both. The service agreement usually covers a long-term relationship with a customer. The history of replacements that is recorded in the service BOM is useful data to have for the service agreement.

You can also apply a template BOM to a service order to record the history of the service that was performed on a service object.

## Copy the history of a service BOM

You can copy the history of a service BOM line from one service agreement to another service agreement. By copying the service history between service agreements, you can preserve the record of replacements for an item.

### Example

You set up a three-year service agreement for a customer's car. During that period, the customer becomes accustomed to the good service that the company provides. Therefore, after the agreement expires, the customer wants to set up a new one. You're now able to negotiate a more favorable agreement for the company. Because the record of replaced components might be useful in the future, you copy the history of the service BOM to the new agreement.

## Modify the template BOM

If a template BOM hasn't been attached to a service object, you can modify or delete lines in it. After the template BOM is attached to a service object, you can modify only the local version of the BOM. If you want to duplicate the setup of a local version of a template BOM, you can create a new template BOM based on the local version. Learn more in [Modify a Service BOM](modify-service-bom.md).

If you replace an item in the BOM, you can register the replacement on the BOM line in the BOM designer. Optionally, you can create a service order line for the replacement object. If you create a service order line, you can invoice the replacement item. If you don't create a service order line for a replacement, the replacement registration is kept to track the history of the service object.

## Change how information on the BOM line is displayed

You can change the way that information on the BOM line is displayed for all template and service BOMs. The changes are applied to all template BOMs and service BOMs.

## Set up number sequences for template BOMs

To use template BOMs, you must set up two number sequences. Set up one number sequence for the template BOM and one for the BOM history line number.

> [!NOTE]
> Number sequences are used to allocate identifiers to records that require them. Before you can assign a number sequence to a template BOM or a BOM history line number, you must set up number sequences codes.

## Set up number sequences

1. On the **Number sequences** list page, create number sequences for template BOMs and the BOM history line number.
1. Go to **Service management** \> **Setup** \> **Service management parameters**.
1. Select **Number sequences**, and then select a number sequence code for the number sequence references that you created on the **Number sequences** page.
1. Close the page to save your changes.

> [!NOTE]
> The BOM history line number is used by the system to associate the transactions in the BOM history with a service agreement or service order. The number is not displayed in the user interface.

## Related information

- [Create a template BOM](create-template-bom.md)
- [Manage template BOMs on object relations](manage-template-boms-on-object-relations.md)
- [Modify a Service BOM](modify-service-bom.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
