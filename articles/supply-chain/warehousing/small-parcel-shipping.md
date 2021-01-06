
# Small parcel shipping

The small parcel shipping (SPS) feature rates packed containers and fetches the required tracking numbers. It also calculates freight cost and can print shipping labels using a Zebra Programming Language (ZPL) printer.

The SPS feature interacts with your shipping carrier through a dedicated *rate engine*, which must be provided to you by your carrier or developed in collaboration with them. <!--KFM: Is this true? And do we need an engine for *each* carrier? --> The rate engine enables Supply Chain Management to submit details about a packed container to your carrier and receive back a shipping label, rate, and tracking number. You can then print the returned label automatically using ZPL printer and apply the label to the shipment.

## Prepare your system to support small parcel shipping

Before you can begin using small parcel shipping features, you must enable the SPS feature in feature management, add your rate engine, and set up the Transportation management and Warehouse management modules to support it.

### Turn on the SPS feature

Before you can use this feature, it must be turned on in your system. Administrators can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Transportation management*
- **Feature name** - *Small parcel shipping*

### Deploy and set up your rate engines

Supply Chain Management does not include any rate engines. You must obtain or create them as needed and then add them to your system. However, Microsoft also provides a demo rate engine that you can use for testing.

#### Download and deploy the demo rate engine

To get the demo rate engine:

1. Download the [demo rate engine DLL on GitHub](https://github.com/microsoft/Dynamics-365-FastTrack-Implementation-Assets/tree/master/SCM/SPS).
1. On your Supply Chain Management server, save the downloaded DLL in the following folder:  
`\AOSService\PackagesLocalDirectory\ApplicationSuite\bin`

#### Create and deploy functional rate engines

For details about how to create and deploy functional rate engines for use on a production or test environment, see the following topics:

- [Create a new transportation management engine](../transportation/create-new-transportation-management-engine.md)
- [Set up transportation management engines](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-transportation-management-engines)

More information about how to create create an SPS rate engine is available on the following blog post: [Small Parcel Shipping: How to leverage small parcel shipping functionality in Microsoft Dynamics 365](https://hub.bhsolutions.com/creating-a-mock-parcel-engine-in-d365?submissionGuid=46a1fccf-80b0-4b70-a6a0-4bf45a8756b5).

#### Set up a rate engine in Supply Chain Management

After you have created and deployed rate engine for SPS, follow these steps to set up the new rate engine:

1. Go to **Transportation management \> Setup \> Engines \> Rate engine**.
1. On the Action Pane, select **New** to add a new row to the grid.
1. Make the following settings for the new row:
    - **Rating engine** - Enter a unique name for this rate engine. (For the demo rate engine, enter *Demo*.)
    - **Name** - Enter a short description of this rate engine. (For the demo rate engine, enter *Demo rate engine*.)
    - **Rating metadata ID** - <!--  KFM: What do we enter here? -->
    - **Engine assembly** - Enter the file name of the DLL package that you have deployed. (For the demo rate engine, this is `TMSSmallParcelShippingEngine.dll`.)
    - **Engine class** - <!--  KFM: What is this? How do we find it for non-demo engines? --> (For the demo rate engine, this is `TMSSmallParcelShippingEngine.SmallParcelShippingRateEngine`.)

## Example scenario

This example scenario shows how to set up and use SPS once you have prepared your system as described earlier in this topic. This scenario uses the demo rate engine described previously.

### Enable demo data

To work through this scenario using the demo records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

### Set up the scenario

For this example scenario, you will need a demo carrier, carrier group, packing policy, and packing profile. The following subsections explain how to prepare the records needed for the scenario. In a production scenario, you would typically set each of these up in a similar way, but you would specific values different from those suggested here.

#### Set up carriers

Set up carrier by doing the following:

1. Go to **Transportation management \> Setup \> Carriers \> Shipping carriers**.
1. On the Action Pane, select **New** to add a new carrier.
1. Make the following settings in the header section of the page:
    - **Shipping carrier** - *Demo*
    - **Name** - *Demo Carrier*
    - **Mode** - *Ground*
1. On the **Overview** FastTab, make the following settings:
    - **Activate shipping carrier** - *Yes*
    - **Activate carrier rating** - *Yes*
1. On the **Services** FastTab, select **New** from the toolbar to add a new service to the grid.
1. For the new service, set **Transportation method** to *Ground* and enter demo values for all of the other columns as needed. (A new **Mode of delivery** will be created and set automatically when you save the new shipping carrier record.)
1. On the **Rating profiles** FastTab, select **New** from the toolbar to add a new profile to the grid.
1. For the new row, set **Rate engine** to the name of the rate engine you have set up for this carrier. If you are using the demo rate engine, select *SmallParcelShipping*. <!--  KFM: Where does this value come from? Should it match a value we entered earlier (we didn't suggest entering this), or does it come directly from the DLL? --> Enter demo values for all of the other columns as needed.
1. On the Action Pane, select **Save**.

For more information about how to set up carriers, see [Set up shipping carriers](../transportation/tasks/set-up-shipping-carriers.md).

#### Set up carrier service accounts

Set up a carrier service account by doing the following:

1. Go to **Transportation management \> Setup \> Rating \> Carrier service account**.
1. On the Action Pane, select **New** to add a new carrier service account.
1. Make the following settings for the new account:
    - **Shipping Carrier** – *Demo Carrier*
    - **Carrier service** - Select a carrier service. <!--KFM: Does it matter which one? Can we give some advice or an example here? -->
    - **Carrier customer account number** - Enter the carrier customer account number used to verify and authenticate the connection to shipping carrier. <!--KFM: Supplied by the carrier? What do we enter if we are doing the demo? -->
    - **Site** - *6*
    - **Warehouse** - *62*

    > [!NOTE]
    > Often, **Carrier customer account number** is the only setting required to authenticate the connection. However, if your carrier requires additional authentication parameters, your organization should customize this page to add the extra fields as needed.

#### Set up a container packing policy

Set up a container packing policy by doing the following:

1. If you haven't already done so, set up a ZPL printer definition using the Document Routing Agent application. For more information, see [Document printing overview](../../fin-ops-core/dev-itpro/analytics/print-documents.md) and its related topics.
1. Go to **Warehouse Management \> Setup \> Containers \> Container packing policies**.
1. On the Action Pane, select **New** to add a new container packing policy.
1. In the header of the new policy, make the following settings:
    - **Container packing policy** - *Demo container packing policy*.
    - **Description** - Enter a description og the policy.
1. On the **Overview** FastTab, make the following settings:
    - **Warehouse** - *62*
    - **Default location for final shipment** - *Baydoor*
    - **Weight unit** - *KG*
    - **Container closing policy** - *Automatic release*
    - **Container release policy** - *Make available at final shipping location*
1. On the **Container manifest** FastTab, make the following settings:
    - **Automatic manifest at container close** - *Yes*
    - **Manifest requirements for container** - *Transportation management*
    - **Print container shipping label** - *Always*
1. On the **Carrier label printing** FastTab, set Printer name to the name of the ZPL printer where you want to print shipping labels. <!--KFM: Should we recommend a setting for **Print container shipping label rule**. Seems like we might set this to Never if we don't want to print labels during the scenario. -->

#### Set up a packing profile

Set up a packing profile by doing the following:

1. Go to **Warehouse Management \> Setup \> Packing \> Packing profiles**.
1. On the Action Pane, select **New** to add a new packing profile to the grid.
1. Make the following settings for the new profile:
    - **Packing profile ID** - *Demo packing profile*.
    - **Description** - Enter a description of the profile.
    - **Container packing policy** - *Demo container packing policy*.
    - **Container ID mode** - *Auto*.
    - **Container type** - *SmallBox*

#### Set up a customer to use the SPS carrier

Now set up a customer to use carrier that you created for the example scenario. Do the following:

1. Go to **Accounts receivable \> customers \> All customers**.
1. Find and select customer *US-027* in the grid.
1. On the Action Pane, open the **General** tab and, from the **Set up** group, select **Carrier customer accounts**.
1. The **Carrier customer accounts** page opens. On the Action Pane, select **New** to add a new account to the grid.
1. Make the following settings for the new account:
    - **Shipping carrier** - *Demo Carrier*.
    - **Carrier customer account number** - Enter an account number. <!--KFM: Does it matter what we type here? Can we give some advice or an example? -->

### Walk through the example scenario

Once you have set up all of the sample data, as described in the previous section, you are ready to work through the example scenario provided here.

#### Create a sales order and process the work

Create a new sales order by doing the following:

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the **Customer account** to *US-027*.
1. Select **OK** to create the new sales order and close the dialog box.
1. Your new sales order opens. On the **Sales order header** FastTab, set the **Carrier customer account number** to the value you selected previously. <!--KFM: If we can provide an example ID in the previous section, we could just repeat that here. -->
1. In the **Sales order lines** section, add a sales line with the following settings:
    - **Item number** - *A0001*
    - **Site** - *6*
    - **Warehouse** - *62*
    - **Quantity** - *1*
1. Open the **Header** tab at the top-right of the page.
1. On the **Delivery** FastTab, make the following settings:
    - **Shipping carrier** - *Demo Carrier*.
    - **Carrier service** - Select the carrier service you selected when setting up the carrier service account for this demo. <!--KFM: If we can provide an example value in that section, we could just repeat that here. -->
1. Open the **Lines** tab at the top-right of the page.
1. In the **Sales order lines** section, select the order line you set up previously and, from the toolbar, select **Inventory \> Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. Don't reserve the second order line.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse**.
1. Work will be created to move items from the picking location to the pack station.
1. Complete the created work to simulate moving your items to the packing station. <!--KFM: Seems like we are missing very many steps here. I think we need to do this using the warehouse (mobile) app; if so, we should at least mention that, but a full procedure using our sample data values would be better (maybe in its own section after this one). -->

#### Pack the shipment

Pack the shipment by doing the following:

1. Go to **Warehouse management \. Picking and containerization \> Pack**.
1. The **Select packing station** dialog box opens. Make the following settings here:
    - **Site** – *6*
    - **Warehouse** - *62*
    - **Location** - *Pack*
    - **Packing profile ID** - *Demo packing profile*
1. Select **OK**. <!-- KFM: Here I get an error "Worker must be specified in order to log in". The **Worker** field is read-only, so I am unable to continue and could not verify the rest of this procedure. We probably need to add some steps, or at least a note, to prevent this error. The rest of this procedure probably needs more work too. -->
1. The **Pack** page opens. Enter a **Shipment ID**. <!-- KFM: What ID, anything? -->
1. Create a new container. <!-- KFM: How? -->
1. Add the item ID to be packed (*A0001*). <!-- KFM: How? -->
1. The item should now be added to the container.
1. Select containers for the shipment. <!-- KFM: How/where? -->
1. The **Container manifest ID** is currently empty. This is because we didn't yet receive a label and tracking number from the carrier. <!-- KFM: Where can I see this? -->
1. Close the container and specify the gross weight (*1 KG*). <!-- KFM: How? -->
1. Post the packing slip if you have configured it. <!-- KFM: How? -->
1. Look under containers for shipping and note that the **Container manifest ID** and **Total freight** have now been added as received from the carrier. <!-- KFM: Where are these listed? How do I get there? -->
1. Your label should now print on the ZPL printer you selected previously. It should resemble the following example:
    ![Example shipping label](media/sps-label-example.png "Example shipping label")
