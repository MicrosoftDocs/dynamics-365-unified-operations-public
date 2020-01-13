# Release to warehouse rule

# Released in version 10.0.2
#
# About

Release to warehouse rule introduces new abilities for greater flexibility when releasing to warehouse. It serves as a defining setup parameter to determine whether release of partially reserved order lines is allowed by the system or not. It works hand-in-hand with advanced cross docking functionality where a part of an order line might be marked against a supply source and a part of the order line can still be processed in the warehouse, to allow the release of such line and continue with warehouse processing for the available inventory quantity.

# Setup

## Initialization

Once the flight has been enabled, the new feature needs to be initialized. Go to Warehouse management parameters, and in the General – Company information section there will be a button &#39;Initialize release to warehouse rule&#39;. Clicking this will set the status of the rule to the correct initial state for all warehouses. If the warehouse is not warehouse management enabled, it will be set to &#39;Not applicable&#39;, if it is warehouse management enabled, then it will be set to &#39;Allow partial reservation&#39;

## Warehouse parameter

Navigate to _Warehouse management_ _-_ _Setup - Warehouses_ and select Warehouse 62. Open the Warehouse FastTab.

Locate the Requirement for inventory reservation parameter and specify the value to be as needed.

- Not applicable – Only used for non-warehouse management enabled warehouses, not valid for warehouse management enabled warehouses.
- Allow partial reservation – Orders are allowed to be released with any quantity reserved. The unreserved qty will be evaluated towards marking for advanced cross docking. If no marking exists, only work for the reserved qty will be created.
- Require full reservation – An order will only be released if the entire quantity is reserved

# Demo 1 – Require full Release (no planned cross docking)

This demo will describe the functionality where _Require full reservation_ is set on the Warehouse parameter.

Navigate to _Sales and marketing - Sales orders - All sales orders_ and create a new order. Specify Customer account = US-004 and Warehouse = 62.

- Add a line for item A0001, quantity 2 pcs.
- Add a line for item A0002, quantity 2 pcs.

Reserve the first order line, but not the second one. Release the order to warehouse.

Result: Error will be shown to the user &quot;The full qty must be either physically reserved or planned for cross docking&quot; and Work will not be created. Shipment or Load will also not be created.

NOTE: The same behavior is expected when the second line is only partially reserved (and the first one is fully).

# Demo 2 – Allow Partial Release

This demo will describe the functionality where _Allow Partial Release_ is set on the Warehouse parameter.

Navigate to _Sales and marketing - Sales orders - All sales orders_ and create a new order. Specify Customer account = US-004 and Warehouse = 62.

- Add a line for item A0001, quantity 2 pcs.
- Add a line for item A0002, quantity 2 pcs.

Reserve the first order line, but not the second one. Release the order to warehouse.

Result: No error is received; Work and associated Shipment and Load are created for the reserved quantities. No indication of planned cross docking evaluation for the unreserved quantities is shown to the user.

NOTE: The same behavior is expected when the second line is only partially reserved (and the first one is fully). In that case, Work will be created for the partial line qty.
