---
# required metadata

title: Engineering versions and engineering product category
description: The engineering version concept ensures that different states of a product and its data are kept current and clear and can be visualized in the system
author: XXXX
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Engineering versions and engineering product category

Engineering products evolve during their product lifecycle. There can be many reasons for this. For example, improve serviceability of a product, change a component because the supplier no longer supplies it, new insights and mistakes made in the initial design. There are many reasons why the changes of the product should be stored at the same product but should not override the previous data. Examples for this include:

- You want to keep track of the product as it was manufactured and delivered to your customers in previous lifecycle states
- You need a lead time before approving and applying the changes
- You want to have a timestamp on each change and be able to deliver the previous manufactured products, separately from each other

To ensure that the different states of the product and its data is kept current and clear and can be visualized in the system, the engineering version concept is introduced. This engineering version concept, allows to maintain consistency, lock down the bill of material for production, and eliminate variability. Next to that, changes to the product can easily be identified.

Generally, the **form – fit – function rule** is applied to decide if a change requires a new product or an update to a version or a new version is required. Each defines a specific aspect of the part to help engineers match parts to needs. The form – fit – function rule increases design change flexibility by allowing changes to the part with minimal documentation and design cost as long as the fit, form and function of the product are maintained.

- **Fit** refers to the ability of the part or feature to connect to, mate with, or join to another feature or part within an assembly. The &quot;fit&quot; allows the part to meet the required assembly tolerances to be useful.
- **Form** refers to such characteristics as external dimensions, weight, size, and visual appearance of a part or assembly. This is the element that is most affected by an engineer&#39;s aesthetic choices, including enclosure, chassis, and control panel, that become the outward &quot;face&quot; of the product.
- **Function** is a criterion that is met when the part performs its stated purpose effectively and reliably. In an electronics product, for example, function can depend on the solid-state components used, the software or firmware, and quite often on the features of the electronics enclosure selected. Poorly placed or sized ports and misleading or missing labeling are two of the most common ways in which an enclosure can fail the function criterion.

## Engineering versions

When you use engineering products, each product will have at least one engineering version. This engineering version is created automatically upon creating the engineering product. On this engineering version the engineering relevant data is stored specific for the version:

- **Version number** and previous version number (if applicable)
- **Effective from** and **effective to** dates.
- If the version is **active** and can be released and used in transactions. For more information see …. (readiness control)
- The **engineering organization** where the product is created, and which owns the product. For more information see …. (Engineering organization)
- The **engineering documents**
- The **engineering attributes**. For more information see …. (Engineering attributes)
- The **engineering bill of material(s)**
- The **engineering route(s)**

You can choose to update this data on an existing version or create a new version via an **engineering change order** for this. For more information, see … (engineering change management). In case a new version is created for the product, all engineering relevant data is copied to then new version and changes can be applied on the version specific data. This ensures that you can track the specific data for each consecutive version. To easily compare the difference between the consecutive engineering versions, you can see the engineering change order which has change types that will indicate all changes.

## Track version in transactions

With the engineering version concept, you will always have one or more engineering versions which are part of the product master data. You can choose in your setup of engineering products, if the engineering version is also part of **logistical transactions** or not. See below in the **engineering product category** how you can do this. If the logistical impact is relevant, differs per product and per company. Sometimes only the latest versions of a product are used and when you introduce a new version, the previous version cannot be used anymore. In other cases, the version is needed in logistical transactions to overcome the following challenges:

- Logistics needs to ship two pieces of a product to a customer. Do you allow/ desire to ship two different versions?
- If it later turns out that a problem occurs specifically related to a change, it may be beneficial to pinpoint exactly which version was shipped on which orders
- Companies typically want to make sure the old version is shipped first to make sure it is phased out of inventory. This can often be managed by determining the effectivity of the new version in relation to predictions of when stock of the old version is being depleted, especially with low-volume products. But sometimes this is not possible, or the uncertainty in stock level prediction is considered too high.

Whether it is required to make the version visible in inventory and orders or not, is dependent on such factors as mentioned above as well as company practice and needs to be determined by the company. You can make choice on the **engineering product category** and this will be applicable for all products created from the engineering product type for all companies where the product is released to.

In case the product is setup with logistical impact, the engineering version needs to be specified on each transaction. The system will propose the **latest active version**, but you can choose a different version among the different active versions for the company. In case the product is setup without logistical impact, the engineering version used is not specified on the transactions, but the latest active version is used by the system. As an example, when creating the **production bill of material ** and running **master planning**.

## Engineering product category

To ensure the engineering products will behave as required, you can setup engineering product categories in the Engineering product hierarchy. The engineering product category will help you by having the (default) behavior of the engineering products that are created out of them. Once an engineering product is created, you cannot change the engineering product category of the product anymore. When the engineering product category is created, there are also other settings that cannot be changed anymore:

- Engineering company
- Product type
- Product subtype
- Product dimension group
- Configuration technology
- Version number rule

The other fields will be defaulted from the (set up on the) engineering product type but can be changed according to the system rules.

You can make (among other things) the following settings on the engineering product type:

| **Fields / fast tab** | **Description** |
| --- | --- |
| **Engineering&nbsp;organization** | The engineering organization where products of this engineering product type can be created and will be maintained. |
| **Product subtype** and **Product dimension group** | Here you can setup if the engineering versions will have impact on logistical transactions: with product subtype **Product** (and **no** product dimension group), there is no logistical impact. With product subtype **Product master** and a product dimension group **without the version dimension active** , there is no logistical impact (each individual variant will have an engineering version, but no impact on transactions). With product subtype **Product master** and a product dimension group **with the version dimension active** , there will be logistical impact on each engineering version. |
| **Product lifecycle state at creation** | Here you can setup the default product lifecycle state at creation of a new engineering product. For more information see …. (Product lifecycle state) |
| **Version number rule** | With the version number rule, you choose the setup for the version number rule. The rules can be setup as:<ul><li>Manual: you choose the version number on each new version</li><li>Automatic: the system defines the version number based on the predefined format. In this format, you can use # to represent a number and you can also add a constant value. As an example, if you choose the setup as &#39;V-##&#39;, the 1st version will be &#39;V-01&#39;, the 2nd version &#39;V-02&#39;, etc.</li><li>List: the system takes the next number based on the predefined list</li><ul> |
| **Enforce effectivity** | You choose how to use effectivity dates. See below for more information |
| **Naming rules** | You can setup rules for the system to define the product number, name and/ or description using the engineering attributes |
| **Engineering attributes** | You can define the engineering attributes that are part of the product definition. For more information see …. (Engineering attributes) |
| **Release policy** | For more information on this, see …(release policy) |
| **Readiness policy** | For information on this, see … (product readiness) |

## Enforce effectivity

The enforce effectivity setting will determine how the effective from and the effective to date fields on the engineering version will need to be set. There are two options, which in principle differ between: **are overlap or gaps between the time frame of engineering versions possible?** When you select **No** on the enforce effectivity, there are no restrictions on the effectivity date fields and overlap and gaps are allowed. In this scenario, multiple versions can be active at the same time and you can choose to select a different active version to be worked with. When you select **Yes** on the enforce effectivity, the effectivity date from field is mandatory and overlap and gaps are not allowed: each engineering version must directly be connected to (if existing) the previous and next engineering versions. In this scenario, the latest version is expected to be worked with and older versions are not used anymore.

### Connection of bill of materials and routes to the engineering version

The choice you make on the enforce effectivity setting is important with regards to the connection of bill of materials and routes to the engineering versions. In the system it is only allowed to activate multiple bill of materials or routes per product if there is a difference in:

- Product dimension
- Quantity
- Site
- Effectivity dates

Engineering bill of materials and routes are created from the engineering version and can be recognized by the **engineering controlled** checkmark. When working with engineering bill of materials and routes, you will normally not design them using different quantities and the bill of material will not be designed per site. Also for engineering bill of materials and routes, the effectivity dates are always synchronized from the engineering versions, so for a single engineering version, they are equal on the bill of material and route.

When the product dimension **version is used** on the products (with logistical impact on the transactions), the version is also added to the bill of material and routes. This will make sure that there is a difference between the bill of materials and routes of the consecutive versions, so you can use both enforce effectivity &#39;Yes&#39; and &#39;No&#39;. You can make the decision based on if you want to allow overlap and gaps between the engineering versions.

When the product dimension **version is not used** on the products (no logistical impact on the transactions), the version is not added to the bill of material and routes. This will result in that there is no difference between the bill of materials and routes of the consecutive versions. In this case it is highly recommended to use enforce effectivity &#39;Yes&#39;: there is no overlap of engineering versions and it is possible to activate the bill of material and route of a newer version, without needing to deactivate the bill of material and route of the previous version first. In case you would choose to use enforce effectivity &#39;No&#39;, you will manually need to deactivate bill of materials and routes of older versions, before you can activate the latest version.