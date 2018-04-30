---
title: Add an address to a service order
TOCTitle: Add an address to a service order
ms:assetid: 58bfa7d0-020b-45e8-8a5d-3a37d97ea462
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa549071(v=AX.60)
ms:contentKeyID: 62629946
ms.date: 07/25/2014
mtps_version: v=AX.60
_tocRel: gg231005(v=ax.60)/toc.json
---

# Add an address to a service order 




This topic describes how to add a customer address to a service order. When you create a service order, the address information is transferred from the project that the service order is attached to. However, you can select an alternative location from addresses that are already entered in Microsoft Dynamics AX for customers, vendors, sites, warehouses, service orders, and projects.

You can also create a new address. By default, the new address is transferred to the project. However, you can specify that the new address is only relevant for this instance of the service. If you do, the new address is not transferred to the project.

## Create a customer address for a service order

To add an address to a service order, follow these steps:

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Open the service order that you want to create an address for.

3.  On the **Action Pane**, click **Edit**, and then click **Header view**.

4.  On the **Address** FastTab, click **Add address**.

5.  In the **New address** form, enter a unique name for the address and complete the remaining fields. For more information about a specific field in the form, see [Manage addresses (form)](https://technet.microsoft.com/en-us/library/hh370713\(v=ax.60\)).
    

    > [!WARNING]
    > <P>If you enter the same name as an existing address, the information that you enter in the remaining fields will overwrite information for the existing address.</P>



6.  Click **OK** to copy the new address to your service order.

## Specify an alternative address on a service order

To add an alternative address to a service order, follow these steps:

1.  Click **Service management** \> **Common** \> **Service orders** \> **Service orders**.

2.  Open the service order that you want to enter an alternative address for.

3.  On the **Action Pane**, click **Edit**, and then click **Header view**.

4.  On the **Address** FastTab, click **Other address**.

5.  In the **Address selection** form, in the **Record type** field, select **Service orders**.

6.  Select an address, and then click **OK** to copy it to your service order.

## See also

[Service orders (form)](https://technet.microsoft.com/en-us/library/aa554361\(v=ax.60\))

[Select or enter a new address for a party record](select-or-enter-a-new-address-for-a-party-record.md)

[Global address book overview](global-address-book-overview.md)

  


