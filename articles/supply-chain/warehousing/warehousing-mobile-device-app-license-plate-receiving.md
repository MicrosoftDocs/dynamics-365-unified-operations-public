# Warehousing mobile-device app license plate receiving

This topic describes how to receive physical inventory via a warehousing app license plate receiving process.

The functionality can be used to quickly record the receiving of inbound inventory related to an advance ship notice (ASN). An ASN gets automatically created when shipping a transfer order via warehouse management processes and for the purchase order process an ASN can either be manually recorded or automatically imported via an inbound ASN data entity process.

The ASN data is linked to loads and shipments via the **Packing structures** where pallets (parent license plates) can contain cases (nested license plates).

! Note:

To reduce the number of inventory transactions when using packing structures for cases the nested license plate structures will be recorded, but the physical on-hand representation will get recorded with physical on-hand on the parent license plate. A following process to move the physical inventory from the parent license plate to the individual nested license plates must follow via the process of using the **Pack to nested license plates** work creation process mobile device option.

## Warehousing mobile-device app processing

A license plate receiving process gets initialized by scanning the incoming license plate ID and based on this information the content of the license plate (data coming from the ASN) gets physically registered at the inbound dock location. The following flows depends business process needs.

## Work policies

As for e.g. the Report as finished mobile device menu item process, the license plate receiving process supports several workflows depending on the defined setup.

### With work creation:

Registration of physical on-hand where either the same warehouse worker immediately process a put-away work process following the inbound receiving (License plate receiving and put away) or where the registration and put away process gets handled as two different warehouse operations (License plate receiving) following the processing of the put-away work by using the existing work process via another mobile device menu item.

### Without work creation:

By using the feature **Warehouse app license plate receiving processing without work creation** the license plate receiving process can be used without work creation.

By defining **Work policies** with the **Work order type** for **Transfer receipt** and/or **Purchase orders** and using the **Process** for **License plate receiving (and put away)** the two Warehousing app process:

- --License plate receiving
- --License plate receiving and put away

 will not create work, but only register the inbound physical inventory on the license plate at the inbound receiving dock.

To read more about the Report as finished production scenario, see [https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/warehouse-work-policies](https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/warehouse-work-policies)

## Display receiving summary page

An additional detailed Warehouse app flow can be leveraged as part of the license plate receiving process by using the feature **Control whether to display a receiving summary page on mobile devices**.

With this feature enabled and using a license plate receiving mobile device menu item the **Display receiving summary page** controls whether the Warehousing mobile-device app will display a receiving summary page during the license plate receiving process or not. If you choose to show the summary, workers will see an extra page that includes the full advance shipment notice (ASN) information. If you choose to skip the summary page, then warehouse workers also won&#39;t be able to set a disposition code or add exceptions during the receiving process.

## Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse

A license plate receiving process will not be allowed in case an ASN contains a license plate id which already exists with physical on-hand data on another warehouse location than where the license plate registration happens.

For transfer order scenarios where the transit warehouse does not track license plates (and thereby physical on-hand tracking per license plate), you can prevent physical on-hand updates of license plates in transit by using the **Prevent transfer order shipped license plates from being used on other warehouses than the destination warehouse** feature.

By setting the Warehouse management parameters \&gt; General \&gt; License plates \&gt; **Transit warehouse license plate policy** to **Prevent reuse of non-tracked license plate** then only on-hand updates related to a shipped license plate will be allowed at the destination warehouse until the transfer order has been received

Additional information:

To read more about inbound loads, see \*\*\*NEW\_INBOUND\_LOAD\_PAGE\*\*\*.

To read more about Warehousing mobile-device menu items, see [https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/configure-mobile-devices-warehouse](https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/configure-mobile-devices-warehouse)
