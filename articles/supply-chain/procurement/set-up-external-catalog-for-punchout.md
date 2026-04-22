---
title: Set up an external catalog for PunchOut e-procurement
description: Learn about the use of an  external catalog or PunchOut catalog to collect quote information from a vendor and add it to a requisition.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchVendorPortalRequests, CatExternalCatalogConfiguration, CatCXMLCartLogList
ms.topic: how-to
ms.date: 4/22/2026
ms.custom: 
  - bap-template
---

# Set up an external catalog for PunchOut e-procurement

[!include [banner](../includes/banner.md)]

By using the external catalog, you can ensure that the product and price information that you subsequently process in Supply Chain Management is accurate and up to date.

The requisition can then be approved and converted to a purchase order and an order can be placed at the vendor.

When the external catalog is set up and an employee prepares a requisition, an option is available to redirect to an external site, the external catalog, and return the shopping basket that was created at the external site.

This communication is based on the cXML protocol and it needs to be set up between the systems of the buying and the selling organization.

To set up the communication, your vendor needs to provide information for you to use in the configuration of the external catalog, such as identity, domain of the buyer's company (for example, "DUNS" and "DUNS number"), credentials, and the URL to reach the vendor's catalog.

## Set up an external catalog

Set up the external catalog so that when an employee enters a purchase requisition, they're redirected to an external site to select products.

The products that the employee selects from the external catalog are returned with up-to-date price information and from here, they can be added to the purchase requisition.

The intention isn't to enable employees to place an order on the external site.

When setting up the external catalog, make sure that the purpose of the site that the external catalog accesses is to collect quote information and not to place a real order.

To set up an external vendor catalog, complete the following tasks:

1. Set up a procurement category hierarchy. For more information, see [Set up policies for procurement category hierarchies](tasks/set-up-policies-procurement-category-hierarchies.md).
1. Register the vendor in Supply Chain Management. Before you can set up configurations to access an external vendor's catalog, set up the vendor and the vendor contact in Microsoft Dynamics 365. Add the external catalog's vendor to the selected procurement category. For more information about registering vendors, see [Manage vendor collaboration users](manage-vendor-collaboration-users.md). For information about how to assign vendors to a procurement category, see [Approve vendors for specific procurement categories](tasks/approve-vendors-specific-procurement-categories.md).
1. Make sure that the units of measure and the currency that the vendor uses are set up. For information about how to create a unit of measure, see [Manage units of measure](../pim/tasks/manage-unit-measure.md).
1. Configure the external vendor catalog by using the requirements for your vendor's external catalog site. For more details about this task, see [Configure the external vendor catalog](#configure-the-external-vendor-catalog).
1. Test the vendor's external catalog configurations to verify that the settings are valid and that you can access the vendor's external catalog. Use the **Validate settings** action to validate the request setup message that you've defined. This message should cause the vendors external catalog site to be opened in a browser window. During validation, you can't order items and services from the vendor. To order items and services, you must access the vendor's catalog from a purchase requisition.
1. Activate the external catalog by using the **Activate catalog** button on the **External catalogs** page. Activate the external catalog before employees can use it. You can deactivate the external catalog at any time.

## Configure the external vendor catalog

This section gives more details about task 4 in the preceding section.

1. Enter a name and description for the vendor's external catalog. The name that you enter will appear on the cart that represents the external catalog that is shown to employees who creates a requisition. Employees can select on the cart to open the catalog on the vendor's external catalog site.
1. Add an image by using the **External catalog image** action. The image appears on the cart that represents the external catalog. Employees who create a requisition can see the cart. The image's width and height must be equal. Otherwise, the image doesn't display correctly.
1. Select whether the vendor's external catalog website should appear in the same browser window as the one where the employee created the requisition, or if it should open in a new window.
1. Select the vendor for the catalog. In the **Legal entities** list, there's a row for each legal entity where the vendor is set up. To allow users to request products directly from the vendor's catalog in some legal entities but not others, use the **Prevent access** or **Allow access** button for each legal entity where you want the catalog to be or not to be available.
1. In the **Default expiration (Days)** field, enter the number of days that a quotation received from the external catalog is valid and can be used to purchase from the external vendor. When a quotation is created and retrieved from the vendor's external catalog site, the quotation is valid as of the current system date and remains valid for the number of days that you enter in this field.
1. Select the **Add** button to start mapping the procurement categories to the external catalog. Then, in the Category name list, select a category. The list of categories is a superset of procurement categories that the vendor is mapped to in all the legal entities set up for the vendor.

    > [!NOTE]
        > Procurement policies are used to allow or restrict access to categories for the buying legal entity or receiving operating unit. Punchout to an external catalog requires that you allow access to at least one of the procurement categories mapped to the catalog.

1. Set up the cXML setup request message that is sent to the vendor. The automatically generated message format is the minimal template that is required in order to start a session. Fill in values for the tags.

At any time, you can reload the system-generated message template by selecting **Restore message format**.

If you restore the message format, the current message is replaced by the automatically generated message format, which has empty tags.

### cXML setup message

The following table describes the tags included in the template:

| Field | Description |
|--|--|
| &lt; Header &gt;&lt; From &gt;&lt; Credential domain="" &gt; | The domain of the buyer's company. |
| &lt; Header &gt;&lt; From &gt;&lt; Credential&gt;&lt; Identity &gt;&lt; /Identity &gt; | The identity of the buyer's company. |
| &lt; Header &gt;&lt; To &gt;&lt; Credential domain="" &gt; | The domain of the vendor's company. |
| &lt; Header &gt;&lt; To &gt;&lt; Credential&gt;&lt; Identity &gt;&lt; /Identity&gt; | The identity of the vendor's company. |
| &lt; Header &gt;&lt; Sender &gt;&lt; Credential domain="" &gt; | The domain of the buyer's company. |
| &lt; Header &gt;&lt; Sender &gt;&lt; Credential &gt;&lt; Identity &gt;&lt; /Identity&gt; | The identity of the buyer's company. |
| &lt; Header &gt;&lt; Sender &gt;&lt; Credential &gt;&lt; SharedSecret &gt;&lt; /SharedSecret &gt; | The shared secret for the buyer's company. |
| &lt; Request deploymentMode="" &gt; | The test or production deployment. |
| &lt; Request &gt;&lt; PunchOutSetupRequest &gt;&lt; SupplierSetup &gt;&lt; URL &gt;&lt; /URL&gt; | The URL of the vendor's PunchOut endpoint. |

### Extrinsic elements

An extrinsic element is additional information, such as a user name that is based on a user that punches out. The extrinsic element is set when the PunchOut occurs and it can be sent in the request setup message.

Your vendor might require an extrinsic element in the setup request. In that case, add the extrinsic element to the list of extrinsic elements in the **Message format** section of the **External catalog** page.

Specify a name for the extrinsic element that the vendor can recognize and map it to a value. The options for values are: User name, User email, or Random value.
For more information about the cXML protocol, see the [cXML.org website](http://cxml.org/).

## Post back message

The post back message is the message that is received from the vendor when the user checks out from the external site and returns to Supply Chain Management. Post back messages can't be configured. The messages are based on the cXML protocol definition. Here's the information that can be part of the post back message that is received on a requisition line.

| Message received from vendor | Copied to requisition line |
|--|--|
| &lt; ItemIn quantity="" &gt; | Quantity |
| &lt; ItemIn&gt;&lt; ItemID &gt;&lt; SupplierPartID &gt;&lt; /SupplierPartID &gt; | External item ID |
| &lt; ItemDetail&gt;&lt; UnitPrice &gt;&lt; Money currency="" &gt; | Currency |
| &lt; ItemDetail &gt;&lt; UnitPrice &gt;&lt; Money &gt;&lt; /Money &gt; | Unit price |
| &lt; ItemDetail &gt;&lt; Description ShortName="" &gt; | Product name |
| &lt; ItemDetail &gt;&lt; Description &gt;&lt; /Description &gt; | Included in item description; Product name if ShortName isn't specified. |
| &lt; ItemDetail &gt;&lt; UnitOfMeasure &gt;&lt; /UnitOfMeasure &gt; | Unit |
| &lt; ItemDetail &gt;&lt; Classification &gt;&lt; /Classification &gt; | Included in item description |
| &lt; ItemDetail &gt;&lt; Classification domain="" &gt; | Included in item description |

## Delete an external catalog

Delete an external catalog by using the **Delete** action on the page.

If a product is requested from the external vendor catalog, the external vendor catalog can't be deleted. Instead, the status of the external vendor catalog is set to inactive. If you want to remove access to the external vendor's catalog site, but not delete it, change the external catalog status to **Inactive**.

## Related information

- [Purchasing cXML enhancements](purchasing-cxml-enhancements.md)
- [Use external catalogs for PunchOut e-procurement](use-external-catalogs-for-punchout.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
