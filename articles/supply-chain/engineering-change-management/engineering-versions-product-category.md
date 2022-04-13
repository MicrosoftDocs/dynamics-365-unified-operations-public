---
# required metadata

title: Engineering versions and engineering product categories
description: This topic provides information about the concept of engineering versions. Engineering versions ensure that different states of a product and its data are kept current and clear, and that they can be visualized in the system.
author: t-benebo
ms.date: 04/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EngChgLookupDynastring, EngChgProductVersionNumberRule, EngChgEcmProductRoute, EngChgEcmRequestProducts, EngChgEcmProductRoute, EngChgEcmProductPreview,EngChgEcmProductBOMItemIdLookup, EngChgEcmProductBOMConsistOf, EngChgEcmProductCreate, EngChgEcmProductLookup, EngChgProductVersionPrCompany, ngChgProductTypeLookup, EngChgProductType, EngChgProductItemPart, EngChgProductItem, EngChgEcmCategory, EngChgEcmBomDesignerEditBom, EngChgEcmBomDesigner, EngChgEcmBOMCopyDialog
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: 10.0.15
---

# Engineering versions and engineering product categories

[!include [banner](../includes/banner.md)]

Engineering products evolve during their product lifecycle, for many reasons. For example, changes might be introduced to improve product serviceability, change a component because the supplier no longer offers it, respond to new insights, or fix mistakes in the initial design. There are also many reasons why these changes should be stored as part of an ongoing product, in such a way that previous data isn't overwritten. Here are some of these reasons:

- You want to keep track of the product as it was manufactured and delivered to your customers in previous lifecycle states.
- You need a lead time before you approve and apply the changes.
- You want to have a timestamp on each change, and you want to be able to deliver previously manufactured products separately from each other.

*Engineering versions* ensure that the various states of a product and its data are kept current and clear, and that they can be visualized in the system. This concept helps you maintain consistency, lock down the bill of materials (BOM) for production, eliminate variability, and easily identify changes.

Generally, the *form-fit-function* rule is applied to determine whether a change requires a new product, a new version, or an update to an existing version. Each of the three terms in the name of this rule refers to a specific aspect of a part, which helps engineers match parts to needs. The form-fit-function rule increases the flexibility of design changes, because minimal documentation and design cost are required to change a part, provided that the fit, form, and function of the product are maintained.

- **Fit** refers to the ability of the part or feature to connect to, mate with, or join to another feature or part in an assembly. The fit enables the part to meet the required assembly tolerances so that it can be useful.
- **Form** refers to characteristics of a part or assembly, such as the external dimensions, weight, size, and visual appearance. The form is the aspect that is most affected by an engineer's aesthetic choices. It includes the enclosure, chassis, and control panel, which become the outward "face" of the product.
- **Function** is a criterion that is met when the part effectively and reliably performs its stated purpose. For example, in an electronics product, function can depend on the solid-state components that are used, and the software or firmware. Often, it can also depend on the features of the selected enclosure. Two of the most common reasons that an enclosure can fail the function criterion are poorly placed or poorly sized ports, and misleading or missing labeling. 

## Engineering versions

When you use engineering products, each product has at least one engineering version. The initial engineering version is automatically created when you create an engineering product. Each engineering version stores the engineering-relevant data that is specific to that version. Here are some examples of this data:

- The version number and previous version number (if applicable)
- The effective-from and effective-to dates
- The product version active status, which indicates whether the version can be released and used in transactions (For more information, see [Product readiness](product-readiness.md).)
- The engineering company that created and owns the product (For more information, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).)
- Related engineering documents, such as an assembly manual, user instructions, pictures, and links
- The engineering attributes (For more information, see [Engineering attributes and engineering attribute search](engineering-attributes-and-search.md).)
- Bill of materials (BOM) for engineering products
- Formulas for process manufacturing products
- The engineering routes

You can update this data on an existing version, or create a new version, by using an *engineering change order*. (For more information, see [Manage changes to engineering products](engineering-change-management.md).) If you create a new version of a product, the system copies all engineering-relevant data to that new version. You can then modify the data for that new version. In this way, you can track specific data for each consecutive version. To compare the differences between consecutive engineering versions, inspect the engineering change order, which includes change types that indicate all changes.

As has been stated, the initial engineering version is automatically created when you create an engineering product. The version number for this version follows the version number rule that is defined in the engineering category for the product. To transition to a subsequent version, you must add the product to an engineering change order as a line, and you must set the **Impact** field to *New version*. The engineering change order will include the details of the change from the current version to the next version.

Note that an engineering product can be in only one engineering change order at a time. This restriction ensures data accuracy, and helps avoid overlapping or contradictory changes in the product. Also note that the **Engineer** field in the **Header** view of the engineering change order shows the engineer who is responsible for the change order. If the engineer belongs to a team that is defined in the system, the **Responsible** field shows the leader of that team.

## Track versions in transactions

When you use engineering change management, your product master data always includes one or more engineering versions. In your setup of engineering products, you can choose whether the engineering version is also part of *logistical transactions*. (For more information, see the [Set up engineering product categories](#product-category) section later in this topic.) If the logistical impact is relevant, it differs per product and per company. Sometimes, only the latest version of a product is used. Therefore, when you introduce a new version, the previous version can no longer be used. In other cases, the previous version is required in logistical transactions to overcome the following challenges:

- The Logistics department must ship two pieces of a product to a customer. In this case, you must decide whether you want or will allow two different versions to be shipped.
- It's later discovered that a problem occurs, and that it's related to a specific change. In this case, it might be beneficial to determine exactly which version was shipped in each order.
- Companies typically want to ship old versions first, to phase them out of inventory. Especially for low-volume products, this approach can often be managed by determining the effectivity dates of the new version in relation to predictions about when stock of the old version will be depleted. However, sometimes you might not be able to make this comparison, or you may consider the uncertainty of stock level predictions to be too high.

The decision about whether to make versions visible in inventory depends on factors such as those that were previously mentioned, plus company practice and other considerations that are specific to each company. You can specify the behavior for the *engineering product category*. It will then apply to all products that are created from that category, for all companies that the product is released to.

For products that are set up so that they have logistical impact, the engineering version must be specified on each transaction. Although the system will propose the *latest active version*, you can select among all the active versions that are available for the company. For products that are set up so that they don't have logistical impact, the engineering version isn't specified on transactions. However, the system uses the latest active version. For example, when you add a product to a production BOM, the latest version will be used, and when you run master planning, the latest version will be assumed.

## <a name="product-category"></a>Set up engineering product categories

An engineering product category provides a basis for creating a specific engineering product. Each category establishes a set of default values and policies. Therefore, when you create an engineering product, you first select the category to create it from.

Note that a new category hierarchy type (*engineering product hierarchy*) is automatically set up for you. You can manually create the categories by going to **Engineering change management \> Setup \> Engineering product category details**.

Each engineering product category establishes the default behavior of the engineering products that are created based on that category. After you've created an engineering product, you can't change its engineering product category. However, if you select the incorrect category, you can delete the product and then re-create it.

When an engineering product category is created, you're prevented from changing the following settings:

- Engineering company
- Product type
- Product subtype
- Product dimension group
- Configuration technology
- Version number rule

Other settings might inherit default values that are set up for the engineering product category. However, according to the system rules, those values can be changed.

To work with engineering product categories, go to **Engineering change management \> Setup \> Engineering product category details**. Then follow one of these steps.

- To create a new category, select **New** on the Action Pane, and then set the fields as described in the following subsections.
- To edit an existing category, select it in the list pane, select **Edit** on the Action Pane, and then set the fields as described in the following subsections.
- To delete an existing category, select it in the list pane, and then select **Delete** on the Action Pane.

### Header

Set the following fields on the header of an engineering product category.

| Field | Description |
|---|---|
| Name | Enter a name for the engineering product category. |
| Engineering company | Select the engineering company where products in this engineering product category can be created and where they will be maintained. |

### Details FastTab

Set the following fields on the **Details** FastTab of an engineering product category.

| Field | Description |
|---|---|
| Product type | Select whether the category applies to products or services. |
| Production type | This field appears only when you've enabled [formula change management](manage-formula-changes.md) in your system. Select the type of production that this engineering product category applies to:<ul><li>**Planning item** – Use this engineering category to do formula change management for planning items. Planning items use formulas. They resemble formula items, but they are used to produce only co-products and by-products, not finished products. Formulas are used during process manufacturing.</li><li>**BOM** – Use this engineering category to manage engineering products, which don't use formulas and typically (but not necessarily) include BOMs.</li><li>**Formula** – Use this engineering category to do formula change management for finished products. These items will have a formula but not a BOM. Formulas are used during process manufacturing.</li></ul> |
| Catch weight | This option appears only when you've enabled [formula change management](manage-formula-changes.md) in your system. It's available only when the **Production type** field is set to *Planning item* or *Formula*. Set this option to *Yes* if you will use this engineering category to manage items that require catch-weight support. |
| Track versions in transactions | Select whether the version of the product should be stamped on all transactions (logistical impact). For example, if you track the version in transactions, each sales order will show which specific version of the product was sold in that sales order. If you don't track the version in transactions, sales orders won't show which specific version was sold. Instead, they always show the latest version.<ul><li>If this option is set to *Yes*, a product master is created for the product, and each version of the product will be a variant that uses the *version* product dimension. The **Product subtype** field is automatically set to *Product master*, and in the **Product dimension group** field, you must select a product dimension group where the *version* dimension is active. Only product dimension groups where *version* is an active dimension will be shown. You can create new product dimension groups by selecting the **Edit** button (pencil symbol).</li><li>If this option is set to *No*, the *version* product dimension won't be used. You can then select whether to create a product or a product master that uses the other dimensions.</li></ul><p>This option is often used for products that have a cost difference between versions, or products where different conditions apply in relation to the customer. Therefore, it's important to indicate which version was used in each transaction.</p> |
| Product subtype | Select whether the category will hold products or product masters. For product masters, product dimensions will be used.
| Product dimension group | The **Track versions in transactions** setting helps you select the product dimension group. If you specified that you want to track the version in transactions, the product dimension groups where the *version* dimension is used will be shown. Otherwise, only product dimension groups where the *version* dimension isn't used will be shown. |
| Product lifecycle state at creation | Set up the default product lifecycle state that an engineering product should have when it's first created. For more information, see [Product lifecycle states and transactions](product-lifecycle-state-transactions.md). |
| Version number rule | Select the version number rule that applies to the category:<ul><li>**Manual** – You choose the version number for each new version.</li><li>**Automatic** – The system sets the version number, based on a format that you define. When you set up the format, use a number sign (\#) to represent a digit and any other character to represent a constant value. For example, if you define the format as *V-\#\#*, the first version will be "V-01," the second version will be "V-02," and so on.</li><li>**List** – The system takes the next number from a predefined list of custom values that you define.</li></ul> |
| Enforce effectivity | Select whether the effectivity dates of engineering versions must be contiguous, or whether there can be gaps and overlaps. This setting affects the way that you can use the **Effective from** and **Effective to** fields for each engineering version where the category applies.<ul><li>If this option is set to *Yes*, an **Effective from** value must be specified for each version, and neither overlaps nor gaps are allowed between versions. The date range for each engineering version is connected directly to the previous and next engineering versions, if they exist. In this scenario, the newest version is always used, and older versions are no longer used.</li><li>If this option is set to **No**, there are no restrictions on the effectivity date fields for engineering versions, and both overlaps and gaps are allowed. In this scenario, multiple versions can be active at the same time, and you can work with any active version.</li></ul><p>This option also affects BOMs and routes that are connected to a product version. For more information, see the [Connect BOMs and routes to engineering versions](#boms-routes) section later in this topic.</p> |
| Use number rule nomenclature | Set this option to *Yes* to enable rules for defining a product number by using number sequences, engineering attribute names and values, and text constants as segments. To create or modify rules, select the **Edit** button. |
| Use name rule nomenclature | Set this option to *Yes* to enable rules for defining a name by using the engineering attribute names, engineering attribute values, and text constants as segments. To create or modify rules, select the **Edit** button. |
| Use description rule nomenclature | Set this option to *Yes* to enable rules for defining the description by using the engineering attribute names, engineering attribute values, and text constants as segments. To create or modify rules, select the **Edit** button. |

### Attributes FastTab

Use the grid on the **Attributes** FastTab to set up the engineering attributes that apply to products that belong to this category. For information about how to create engineering attributes, see [Engineering attributes and engineering attribute search](engineering-attributes-and-search.md).

Use the buttons on the **Attributes** FastTab to add, remove, and arrange attributes in the grid.

If you change the selection of attributes for an engineering category, and products already exist that are based on that category, you must decide whether to apply your changes to those products. If you want existing products to reflect the changes, select **Update existing products** on the **Attributes** FastTab.

For each row that you add to the grid, set the following fields.

| Field | Description |
|---|---|
| Name | Select the attribute to add. |
| Value | Select the default value for the attribute. |
| Mandatory | Choose whether the attribute is mandatory, which means users must specify a valid value for the attribute before they can save a product. The effect of this setting varies slightly based on the data type of the selected attribute, as defined in the following list.<ul><li>**Boolean** – Set this to *Yes* to require the attribute to have a value of *Yes* (the system will refuse to save a product where the attribute is set to *No*). Set this to *No* to accept a value of *Yes* or *No*. (Attributes of type *Boolean* can't have an empty value.)</li><li>**Integer or Decimal** – Set this to *Yes* to require users to enter a non-zero value for this attribute. Set this to *No* to allow users to save with a value of zero.  (Attributes of these types can't have an empty value.)</li><li>**List** – Lists have a data type of *Text*, but also include a predefined list of possible values. Therefore, it isn't possible to enter a blank value for attributes of this type, so this setting has no effect and is just informational.</li><li>**All other data types** – Set this to *Yes* to make the attribute mandatory. Set this to *No* to allow users to save a product without providing a value for this attribute.</li></ul> |
| Batch attribute | Select whether the attribute should be propagated through the batch functionality. |

### Readiness policy FastTab

Use the **Product readiness policy** field to select the readiness policy that should be applied to products that are created based on this engineering category. For more information, see [Product readiness](product-readiness.md).

> [!NOTE]
> The **Product readiness policy** field works slightly differently if you've turned on the *Product readiness checks* feature in your system. (That feature lets you apply readiness policies to standard \[non-engineering\] products). For more information, see [Assign readiness policies to standard and engineering products](product-readiness.md#assign-policy).

### Release policy FastTab

Use the **Product release policy** field to select the release policy that applies to products that belong to this category. For more information, see [Release product structures](release-product-structure.md).

## <a name="boms-routes"></a>Connect BOMs and routes to engineering versions

The setting of the **Enforce effectivity** option is important for the connection of BOMs and routes to each engineering version. You can activate multiple BOMs or routes per product only if there is a difference in any of the following settings:

- Product dimension
- Quantity
- Site
- Effectivity dates

Engineering BOMs and routes are created from the engineering version where they apply. They can be recognized by the check mark in the **Engineering controlled** check box. When you work with engineering BOMs and routes, you won't typically design them by using different quantities. You also won't typically design different BOMs per site. Additionally, for engineering BOMs and routes, the effectivity dates are always taken from the engineering version. Therefore, an engineering version, its BOM, and its route will all have the same effectivity dates.

For products where you're using the *version* product dimension (together with logistical impact on the transactions), the version is also added to the BOMs and routes. This behavior helps differentiate the BOMs and routes of consecutive versions, regardless of the **Enforce effectivity** setting.

For products where you aren't using the *version* product dimension (without logistical impact on the transactions), the version isn't added to the BOMs or routes. Therefore, there will be no difference between the BOMs and routes of consecutive versions. In this case, we highly recommend that you set the **Enforce effectivity** option to *Yes*. In this way, you help prevent engineering versions from overlapping, and you can also activate the BOM and route of a newer version without first having to inactivate the BOM and route of the previous version. If you do set the **Enforce effectivity** option to *Yes* in this case, you must manually inactivate the BOMs and routes of older versions before you can activate the latest version.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
