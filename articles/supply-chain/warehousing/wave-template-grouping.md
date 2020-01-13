# Wave template grouping

# Released in version 10.0.3
#
# About

Wave template grouping functionality is like existing Work template grouping behavior, but instead it enables grouping and breaking by functionality already on the Wave template. This addition can be useful in the warehouses where Waves are being created based on a certain criterion, but automatic Wave creation is preferred to manual.

The system can leverage this Wave template setup to split released lines and appropriately create multiple Waves when required. If set up correctly, as the new Shipment is released, the system will attempt to add it to the first Wave if the grouping or break field(s) match, otherwise it will continue to evaluate other Waves until it must create a new one.

# Setup

## Wave template

Navigate to _Warehouse management_ - _Setup_ - _Waves_ - _Wave templates_ and select &#39;62 Shipping default&#39;

Open the _Edit query_, and add sorting on Shipments – Carrier service – Ascending

Open _Wave template grouping_ from the ribbon and check the Group by box for Shipments – Carrier service.

Set Automate wave creation and Assign to open waves to Yes. Set Process wave at release to warehouse to No.

# Demo

This demo will demonstrate how Wave template grouping can be used to automatically create multiple waves per certain criteria. In this example, one wave will be created per carrier service.

1. Navigate to _Sales and marketing_ - _Sales orders_ - _ All sales orders_ and create a new Sales order. Specify Customer account = US-004, Warehouse = 62, **Carrier = Air cargo and Carrier service = Air**.

-
  - Add a line for item A0001, quantity 1 pcs.

Reserve and release the order to warehouse. New Shipment and Wave are created.

Navigate to _Warehouse management_ - _Outbound Waves_ - _Shipment Waves_ - _All Waves_ and open the newly created Wave to ensure the Shipment has been added to it.

1. Navigate to _Sales and marketing_ - _Sales orders_ - _All sales orders_ and create a new Sales order. Specify Customer account = US-005, Warehouse = 62, **Carrier = Flower moving and Carrier service = STD**.

-
  - Add a line for item A0001, quantity 1 pcs.

Reserve and release the order to warehouse. New Shipment and new wave are created.

Navigate to _Warehouse management_ - _Outbound Waves_ - _Shipment Waves_ - _All Waves_ and open the newly created Wave to ensure the Shipment has been added to it.

1. Navigate to _Sales and marketing_ - _Sales orders_ - _All sales orders_ and create a new Sales order. Specify Customer account = US-006, Warehouse = 62, **Carrier = Air cargo and Carrier service = Air**.

-
  - Add a line for item A0002, quantity 1 pcs.

Reserve and release the order to warehouse. New Shipment is created and added to the wave created for sales order 1 (as the carrier service is the same).

Navigate to _Warehouse management_ - _Outbound Waves_ - _Shipment Waves_ - _All Waves_ and open the previously created Wave to ensure the second Shipment has been added to it.
