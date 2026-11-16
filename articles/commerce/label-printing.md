---
title: Label printing in Store Commerce (preview)
description: Learn how to configure product label types, formats, and network printers, send label requests from Commerce headquarters, and print labels in Store Commerce.
ms.topic: how-to
ms.date: 11/16/2026
author: ritakimani1
ms.author: ritakimani
ms.reviewer: mirao
ms.custom:
  - bap-template
ai-usage: ai-generated
---

# Label printing in Store Commerce (preview)

[!INCLUDE [banner](includes/banner.md)]

> [!IMPORTANT]
> Label printing is currently available as part of a public preview release. Features, regions, user interface labels, and available lifecycle actions can change before general availability. Both the documentation and the functionality are subject to change.

Label printing lets you send product lists from Microsoft Dynamics 365 Commerce headquarters to stores, where associates select and print labels in Store Commerce. Associates can also print a label for a selected product from modern product details without a headquarters request.

Administrators configure label types, label formats, and printers in headquarters. Pricing and merchandising users create and release requests for specific products and stores. Printing takes place in Store Commerce through Hardware Station, not in headquarters.

## Prerequisites

- Store Commerce app version 10.0.50 or later and compatible headquarters, Commerce Scale Unit, and Hardware Station versions.
- A network-connected Zebra printer that supports ZPL, with suitable label media.
- To print labels directly from product details, enable **Enable modernized product details page** in headquarters. For more information, see [Enable the modernized product details page](pos-modern-product-details.md#enable-the-modernized-product-details-page).

For general peripheral and Hardware Station setup, see [Retail peripherals overview](retail-peripherals-overview.md) and [Support for network peripherals](dev-itpro/network-peripherals.md).

> [!IMPORTANT]
> Label printing supports Zebra printers over network connections only, not Windows printer drivers, print queues, or OPOS. Support for other printer models and label-printer extensibility might be made available in future releases.

## Set up label printing in headquarters

Administrators should complete the following setup before stores print labels. Configure request numbering only if you use headquarters label requests.

### Enable label printing in Store Commerce

1. In Commerce headquarters, go to the **Feature management** workspace (**System administration** > **Workspaces** > **Feature management**).
1. Search for **Enable label printing in Store Commerce** and select **Enable now**.
1. Run the **Registers (1090)** distribution schedule job to push changes to channels.
1. Restart the Store Commerce app.

### Configure label types and formats

A *label type* identifies a business purpose, such as a shelf label, product tag, or promotional label. You create these types to match your business. These examples aren't a required set of built-in types.

A *label format* contains the ZPL that defines the label layout and content. A *label profile* maps each label type to a format. You assign the profile to a label printer. Store associates select a printer and label type; they don't choose a format directly.

#### Create label types

To define your label types, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Label types**.
1. Create a type with a unique identifier, a name, and a description.
1. Repeat these steps for each business purpose that needs a different label type.

Choose the identifier carefully. You can update the name and description, but you can't rename the identifier. You can't delete a type while label formats, profiles, or requests reference it.

#### Create label formats

To create a format, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Label formats**.
1. Create a format with a unique identifier and a name, and select its label type.
1. Enter or paste your ZPL into the format body.
1. Use the supported variable fields displayed beside the format body to include product information in the label.
1. Save the format.

The format must contain one complete ZPL label definition, starting with `^XA` and ending with `^XZ`. Variable fields use the `${FieldName}` syntax shown in the field list. The ZPL defines the physical layout. Commerce doesn't provide a visual label designer or a rendered label preview for this workflow.

> [!NOTE]
> Saving a format doesn't validate its ZPL or guarantee that it can be printed. Test the format with your printer and label stock before using it for store work. Check the layout, barcode readability, price, and other product information on the physical label.

#### Create label profiles

To map types to formats, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **Label profiles**.
1. Create a profile.
1. Add a line for each label type that the printer should support, and select a format of that same type.
1. Save the profile.

A profile can map a label type to only one format. Different printers can use different profiles, so the same business type can produce different layouts on different printers.

If you later change a format's label type, review the profiles that use it. A profile line and its format must have matching types for printing to work.

### Configure label printers

#### Add printers to the hardware profile

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS profiles** > **Hardware profiles**, and select the profile used by the register or store hardware station for label printing.
1. Expand **Label printers** and select **New**.
1. Enter a **Label printer** name, set **Connection type** to **Network**, and set **Device name** to **Zebra**.
1. Select the **Label profile** to use for this printer.
1. Repeat for any additional printers, and then select **Save**.

#### Set printer IP addresses on the register or store hardware station

Configure the addresses for the register or the store hardware station used for label printing.

To configure addresses on a register:

1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **Registers**, and select the register.
1. On the **Register** tab, select **Configure IP addresses**.
1. Expand **Label printers**.
1. For each printer, enter its **IP address** and **Port**. Use the TCP port configured on the printer.
1. Select **Save**.
1. Run the **Registers (1090)** distribution schedule job and restart Store Commerce.

To configure addresses at the store level:

1. In headquarters, search for **All stores** and open the store.
1. On the **Hardware stations** FastTab, select the hardware station used for label printing.
1. Select **Configure IP addresses**, and expand **Label printers**.
1. For each printer, enter its **IP address** and **Port**, and select **Save**.
1. Run the **Channel configuration (1070)** and **Registers (1090)** distribution schedule jobs and restart Store Commerce.

You can configure multiple label printers, each with its own profile and network connection. Associates select the printer in Store Commerce. If a printer has no label profile, or its profile has no format for the selected type, correct the configuration or select another printer.

### Add the POS operation

Before you add the button to a button grid, configure the operation in headquarters.

1. Go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **POS operations**.
1. Select **New**, and create an operation with **Operation ID** = **1600**.
1. Configure the appropriate permissions for your organization.
1. Select **Save**.

### Add the label printing button

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Screen layouts**.
1. Select the screen layout used by the store and the appropriate layout size.
1. On the **Button grids** FastTab, select the grid where you want the button, and then select **Designer**.
1. In the button grid designer, right-click an empty area and select **New button**.
1. In **Configure button**, set **Action** to **Print labels** (operation **1600**) and **Button text** to **Label printing**. Select **OK** and save the grid.
1. Run the **Registers (1090)** distribution schedule job.
1. Restart Store Commerce and verify that the **Label printing** button appears.

If you enable **Check user access** for the operation, configure the required permissions for the workers who print labels.

For more information about creating and configuring button grids, see [Button grids and the button grid designer](pos-screen-layouts.md#button-grids).

### Configure the label print request number sequence

Before you create label print requests in headquarters, configure the number sequence that generates request identifiers. This setup isn't required when associates print labels directly from product details in Store Commerce.

1. In headquarters, switch to the legal entity where you create label print requests.
1. Go to **Organization administration** > **Number sequences** > **Number sequences**.
1. Select **Number sequence** to create a sequence, or open an existing sequence intended for label print requests.
1. Enter a number sequence code and name, define the number format, and configure the scope for the legal entity.
1. Configure the sequence to be **Automatic**, **Noncontinuous**, and **Noncyclic**.
1. Save the sequence.
1. Open **Commerce parameters** > **Number sequences**, and assign the sequence to the **Label print request** reference.
1. Save your changes.

> [!NOTE]
> Gaps in request numbers are allowed. Don't reset or reuse previously issued numbers.

### Distribute label configuration

After you finish configuring labels and printers, run or schedule the applicable distribution jobs.

| Data | Distribution job |
| ---- | ---------------- |
| Label types, formats, profiles, profile mappings, and hardware-profile label printers | **1090 - Registers** |
| Label-printer IP addresses and ports | Included in **1070 - Channel configuration** and **1090 - Registers** |

Confirm that the download sessions complete successfully for the stores that use the configuration, and then restart Store Commerce.

## Create and release label requests

Create a label print request when headquarters needs to send a specific list of products to one or more stores. Each line identifies an exact product or variant, a label type, and the requested number of copies.

To create and release a request, follow these steps:

1. In headquarters, open **Released products** or **Released products by category** in the appropriate legal entity.
1. Select the products that need labels.
1. On the Action pane, select **Print label in Store Commerce** to open **Send products for label printing**.
1. To create a new request, set **Append to an existing draft** to **No**.
1. Select **Default label type** for the products.
1. In **Stores**, select the target stores in the current legal entity. Use **Filter** to find stores, or **Select all** and **Clear all** to update the selection.
1. Review the product lines. For products with variants, select **Choose variants** and select the exact variants. Each selected variant becomes a separate line.
1. Set **Copies** for each line to a whole number from 1 through 1,000. Use **Remove** to exclude a product line.
1. Select **Send** to save the request as a draft.
1. Go to **Retail and Commerce** > **Inventory management** > **Bar codes and labels** > **Label print requests**, select the draft, and review its stores, products, variants, label types, and quantities.
1. Select **Release request** and confirm that the content can no longer be edited.
1. Run or schedule **1020 - Prices and discounts** to distribute the released request, including its target stores and product lines. Confirm that the download sessions complete successfully for the target stores, and then refresh the request list in Store Commerce.

> [!IMPORTANT]
> **Released** means that headquarters published the request. It doesn't mean that labels are printed. Releasing a request locks its content but doesn't verify that every target store's printer has a matching label format.

Only released requests targeted to the current store are available in Store Commerce. A request appears after its complete released content reaches the channel.

### Manage retained requests

Requests have two headquarters statuses: **Draft** and **Released**. Printing doesn't change either status, report completion to headquarters, or hide a request. A released request remains available for repeated printing until an authorized headquarters user deletes it.

Delete requests when stores no longer need them. Removal reaches stores through synchronization, so a store that didn't receive the deletion might still see the request. Deleting a request isn't evidence that its labels were printed.

## Print labels in Store Commerce

Store associates can print labels from a released headquarters request or directly from modern product details without a request.

### Check the printer and print a test label

Before printing product labels, check the configured printer in Store Commerce.

1. Select the Hardware Station used for label printing.
1. Open **Health check**, and check the label printer's status.
1. Select the label printer, and select **Print test label**. This action prints a diagnostic label and uses label media.
1. Inspect the physical output.

A successful health check or diagnostic test doesn't confirm that your product label format fits the label stock. Print a product label with your configured format, and verify its alignment, text, number of copies, and barcode readability before using it in the store.

### Print labels from a headquarters request

To print requested labels in Store Commerce, follow these steps:

1. Open the **Label printing** operation. You don't need an active transaction or an open shift.
1. Select a released request.
1. Review the products and variants, and select the lines to print. Use **Select all eligible lines** to include eligible lines throughout the request, not only those currently visible.
1. In **Label printer**, select the configured network printer.
1. If needed, change **Copies** for individual lines. Enter a whole number from 1 through 1,000.
1. If needed, use **Label type override** for the selection or change **Label type** on an individual line. Available types depend on the selected printer's profile.
1. Review any validation messages and correct the selected lines that can't be printed.
1. Select **Print** and wait for the operation to finish.

A successful **Label dispatch completed** message means that the labels were sent without a reported error. It doesn't certify physical output. If some selected lines were blocked, review their reasons; valid lines can still be sent.

### Print a label for a selected product

You can print a product label without creating a headquarters request by using modern product details in Store Commerce.

1. Open the product in modern product details.
1. If the product has variants, select the exact variant to print.
1. Select **Print label**.
1. Select a configured label printer and an available label type.
1. Enter the number of copies, from 1 through 1,000.
1. Select **Print**.

## Related resources

- [Retail peripherals overview](retail-peripherals-overview.md)
- [Support for network peripherals](dev-itpro/network-peripherals.md)
- [POS operations](pos-operations.md)
- [Modernized product details page in Store Commerce](pos-modern-product-details.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
