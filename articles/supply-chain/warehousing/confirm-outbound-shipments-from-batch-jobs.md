# Confirm outbound shipments from batch jobs

[!include [banner](../includes/banner.md)]

This topic describes the ability to set up batch jobs that automatically confirm outbound shipments for ready-to-ship loads. For load lines related to transfer orders, the system will automatically run a process that updates the transfer order shipments. However, for sales orders, an operator still must manually run a sales packing slip update from the load to update the outbound cost.

## Enable the Confirm outbound shipments from batch jobs feature
Before you can use this feature, it must be enabled on your system. Administrators can use the feature management settings to check the feature status and enable it if needed. You must enable the feature with **Feature name** *Confirm outbound shipments from batch jobs*.

## Process outbound shipments
In this section it will be explained how to setup a scheduled batch job going to run the outbound shipment confirmation for loads ready to ship.

1. Go to **Warehouse management** \> **Periodic tasks** \> **Process outbound shipments**.
2.	Select **Filter**
3.	Select the **Range** section and insert a range for the table **Loads**, field **Load status** and select **Criteria** as **Loaded**.
4.	Select **OK** to return to the main dialog.
5.	Enable **Batch processing** under the **Run in background section**.
6.	Select **Recurrence** and setup the batch job to process based on interval needed for your business.
7.	Select **OK** to return to the main dialog.
8.	Select **OK** in the main dialog to get the batch job added to the batch queue.

For more information, see [Batch processing overview](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md)
