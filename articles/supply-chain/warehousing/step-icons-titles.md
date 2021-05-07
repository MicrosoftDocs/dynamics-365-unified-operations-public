---
title: Assign step icons and titles for the Warehouse Management mobile app
description: This topic describes on how to assign step icons and titles for new or customized task flows for the Warehouse Management mobile app.
author: MarkusFogelberg
ms.date: 05/06/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mafoge
ms.search.validFrom: 2021-05-06
ms.dyn365.ops.version: 10.0.17
---

# Assign step icons and titles for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This topic describes on how to assign step icons and titles for new or customized task flows for the Warehouse Management mobile app.

The following screenshot shows how step titles and icons appear in the Warehouse Management mobile app.

![Example step title and icon in the Warehouse Management mobile app](media/step-icon-example.png "Example step title and icon in the Warehouse Management mobile app")

## Turn on this feature in your system

Before you can use this feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module**: *Warehouse management*
- **Feature name**: *User settings, icons, and step titles for the new warehouse app*

## Standard step IDs, classes, and icons

Each step in a task flow is identified by a step ID, and each step ID has its corresponding step class. The step icon and title are specified in each step class.

### <a name="step-ids-classes"></a>Step IDs and step classes

The following table provides a list of all the currently available step IDs and their corresponding step classes. The control name of the primary input field is used as the step ID.

For an example of how these are used, see the implementation for the method `WHSMobileAppStepInfoBuilder.stepId()` provided in [Example of assigning step titles and icons for a custom flow](#example), later in this topic.

| Step ID                                        | Step Class                                    |
|------------------------------------------------|-----------------------------------------------|
| MobileDeviceQueueMessageCollectionIdentifierId | WHSMobileAppStepSelectOrder                   |
| InventBatchId                                  | WHSMobileAppStepBatch                         |
| BatchDisposition                               | WHSMobileAppStepBatchDisposition              |
| Carrier                                        | WHSMobileAppStepCarrier                       |
| CatchWeight                                    | WHSMobileAppStepCatchWeight                   |
| NewCaptureWeight                               | WHSMobileAppStepCatchWeight                   |
| OutboundWeight                                 | WHSMobileAppStepCatchWeight                   |
| CatchWeightQtyOutboundWeight                   | WHSMobileAppStepCatchWeight                   |
| CatchWeightTag                                 | WHSMobileAppStepCatchWeightTag                |
| OutboundCatchWeightTag                         | WHSMobileAppStepCatchWeightTag                |
| CatchWeightTagWeight                           | WHSMobileAppStepCatchWeightTagWeight          |
| ChangeWarehouseSuccess                         | WHSMobileAppStepChangeWarehouseSuccess        |
| CheckDigit                                     | WHSMobileAppStepCheckDigit                    |
| ClusterId                                      | WHSMobileAppStepClusterId                     |
| ClusterPosition                                | WHSMobileAppStepClusterPosition               |
| ConfigId                                       | WHSMobileAppStepConfigId                      |
| Confirmation                                   | WHSMobileAppStepConfirmation                  |
| ConsolidateFromLicensePlateId                  | WHSMobileAppStepConsolidateFromLicensePlateId |
| ConsolidateLPConfirmation                      | WHSMobileAppStepConsolidateLPConfirmation     |
| ConsolidateToLicensePlateId                    | WHSMobileAppStepConsolidateToLicensePlateId   |
| ContainerType                                  | WHSMobileAppStepContainerType                 |
| CountingReasonCode                             | WHSMobileAppStepCountingReasonCode            |
| CycleCountingAddLPOrFinish                     | WHSMobileAppStepCycleCountingAddLPOrFinish    |
| CycleCountQty1                                 | WHSMobileAppStepCycleCountQty                 |
| CycleCountQty2                                 | WHSMobileAppStepCycleCountQty                 |
| CycleCountQty3                                 | WHSMobileAppStepCycleCountQty                 |
| CycleCountQty4                                 | WHSMobileAppStepCycleCountQty                 |
| Disposition                                    | WHSMobileAppStepDisposition                   |
| DriverCheckInConfirmation                      | WHSMobileAppStepDriverCheckInConfirmation     |
| DriverCheckOutConfirmation                     | WHSMobileAppStepDriverCheckOutConfirmation    |
| ExpDate                                        | WHSMobileAppStepExpDate                       |
| FromBatchDisposition                           | WHSMobileAppStepFromBatchDisposition          |
| FullQty                                        | WHSMobileAppStepFullQty                       |
| InventColorId                                  | WHSMobileAppStepInventColorId                 |
| InventLocation                                 | WHSMobileAppStepInventLocation                |
| FromInventoryStatus                            | WHSMobileAppStepInventoryStatusFrom           |
| InventSerialId                                 | WHSMobileAppStepInventSerialId                |
| InventSizeId                                   | WHSMobileAppStepInventSizeId                  |
| InventStatusId                                 | WHSMobileAppStepInventStatus                  |
| InventStyleId                                  | WHSMobileAppStepInventStyleId                 |
| InventVersionId                                | WHSMobileAppStepInventVersionId               |
| ItemId                                         | WHSMobileAppStepItem                          |
| KanbanCardId                                   | WHSMobileAppStepKanbanCard                    |
| KanbanOrCardId                                 | WHSMobileAppStepKanbanCard                    |
| KanbanCardToEmpty                              | WHSMobileAppStepKanbanCardToEmpty             |
| LicensePlateId                                 | WHSMobileAppStepLicensePlate                  |
| LoadId                                         | WHSMobileAppStepLoadId                        |
| WMSLocationId                                  | WHSMobileAppStepLocation                      |
| LocationLicensePlatePosition                   | WHSMobileAppStepLocationLicensePlatePosition  |
| LocOrLP                                        | WHSMobileAppStepLocOrLP                       |
| LocOrLPCheck                                   | WHSMobileAppStepLocOrLPCheck                  |
| LocOrLP\_From                                  | WHSMobileAppStepLocOrLPFrom                   |
| LocOrLP\_To                                    | WHSMobileAppStepLocOrLPTo                     |
| LPAdjustIn                                     | WHSMobileAppStepLPAdjustIn                    |
| LPBreakChildLP                                 | WHSMobileAppStepLPBreakChildLP                |
| LPBreakParentLP                                | WHSMobileAppStepLPBreakParentLP               |
| LPBuildChildLP                                 | WHSMobileAppStepLPBuildChildLP                |
| LPBuildParentLP                                | WHSMobileAppStepLPBuildParentLP               |
| LPVerification                                 | WHSMobileAppStepLPVerification                |
| MergeContainerId                               | WHSMobileAppStepMergeContainerId              |
| MixedLPLineNum                                 | WHSMobileAppStepMixedLPLineNum                |
| MovementConfirmCancel                          | WHSMobileAppStepMovementConfirmCancel         |
| NewQty                                         | WHSMobileAppStepNewQty                        |
| OverridePutNewLocation                         | WHSMobileAppStepOverridePutNewLocation        |
| POLineNum                                      | WHSMobileAppStepPOLineNum                     |
| PONum                                          | WHSMobileAppStepPONum                         |
| PositionFull                                   | WHSMobileAppStepPositionFull                  |
| PositionFullQty                                | WHSMobileAppStepPositionFullQty               |
| Potency                                        | WHSMobileAppStepPotency                       |
| PrinterName                                    | WHSMobileAppStepPrinterName                   |
| ProdId                                         | WHSMobileAppStepProdId                        |
| ProdLastPalletConfirmation                     | WHSMobileAppStepProdLastPalletConfirmation    |
| ProductConfirmation                            | WHSMobileAppStepProductConfirmation           |
| ProductionScrapConfirmation                    | WHSMobileAppStepProductionScrapConfirmation   |
| PutawayClusterId                               | WHSMobileAppStepPutawayClusterId              |
| Qty                                            | WHSMobileAppStepQty                           |
| QtyAdjust                                      | WHSMobileAppStepQtyAdjust                     |
| QtyWithScanningLimit                           | WHSMobileAppStepQtyAdjust                     |
| QtyShort                                       | WHSMobileAppStepQtyShort                      |
| QtyToConsume                                   | WHSMobileAppStepQtyToConsume                  |
| QtyToPick                                      | WHSMobileAppStepQtyToPick                     |
| QtyToPut                                       | WHSMobileAppStepQtyToPut                      |
| QtyToScrap                                     | WHSMobileAppStepQtyToScrap                    |
| QtyVerification                                | WHSMobileAppStepQtyVerification               |
| PieceByPieceConfirmation                       | WHSMobileAppStepQtyVerification               |
| ClusterPickQtyVerification                     | WHSMobileAppStepQtyVerification               |
| ReasonString                                   | WHSMobileAppStepReasonString                  |
| RecvLocationId                                 | WHSMobileAppStepRecvLocationId                |
| RemoveContainerId                              | WHSMobileAppStepRemoveContainerId             |
| ReprintLabelConfirmation                       | WHSMobileAppStepReprintLabelConfirmation      |
| RMANum                                         | WHSMobileAppStepRMANum                        |
| ShortPickReason                                | WHSMobileAppStepShortPickReason               |
| SortConOrLP                                    | WHSMobileAppStepSortConOrLP                   |
| SortLicensePlateId                             | WHSMobileAppStepSortLicensePlateId            |
| SortPositionId                                 | WHSMobileAppStepSortPositionId                |
| SortVerification                               | WHSMobileAppStepSortVerification              |
| StartLocationId                                | WHSMobileAppStepStartLocationId               |
| StartProdOrderConfirmation                     | WHSMobileAppStepStartProdOrderConfirmation    |
| TargetLicensePlateId                           | WHSMobileAppStepTargetLicensePlateId          |
| TOLineNum                                      | WHSMobileAppStepTOLineNum                     |
| ToLocation                                     | WHSMobileAppStepToLocation                    |
| TONum                                          | WHSMobileAppStepTONum                         |
| TransportLoadId                                | WHSMobileAppStepTransportLoadId               |
| InventLocationId                               | WHSMobileAppStepWarehouse                     |
| ToWarehouse                                    | WHSMobileAppStepWarehouseTo                   |
| WaveLabelId                                    | WHSMobileAppStepWaveLabelId                   |
| WaveLblQty                                     | WHSMobileAppStepWaveLblQty                    |
| Weight                                         | WHSMobileAppStepWeight                        |
| WeightToConsume                                | WHSMobileAppStepWeightToConsume               |
| WHSAdjustmentType                              | WHSMobileAppStepWHSAdjustmentType             |
| WHSReceivingException                          | WHSMobileAppStepWHSReceivingException         |
| WHSWorkException                               | WHSMobileAppStepWHSWorkException              |
| WorkId                                         | WHSMobileAppStepWorkId                        |
| WorkIdToCancel                                 | WHSMobileAppStepWorkIdToCancel                |
| WHSWorkLicensePlateId                          | WHSMobileAppStepWorkLicensePlateId            |
| WorkLPIdPutawayCluster                         | WHSMobileAppStepWorkLPIdPutawayCluster        |
| WorkPoolId                                     | WHSMobileAppStepWorkPoolId                    |
| ZoneId                                         | WHSMobileAppStepZoneId                        |
| ITMContainerID                                 | ITMMobileAppStepContainerId                   |
| ITMShipmentID                                  | ITMMobileAppStepShipmentId                    |
| InboundPut                                     | WHSMobileAppStepInboundPut                    |
| OutboundPut                                    | WHSMobileAppStepOutboundPut                   |
| Put                                            | WHSMobileAppStepPut                           |
| DriverCheckInId                                | WHSMobileAppStepDriverCheckInId               |
| DriverCheckOutId                               | WHSMobileAppStepDriverCheckOutId              |
| LocVerification                                | WHSMobileAppStepLocVerification               |

### <a name="step-icons"></a>Available step icons

The system includes a collection of standard step icons that you can also reuse for your custom steps. The system does not currently support uploading custom step icons, so you must always select one of the standard ones. The following table shows each standard step icon and its name.

|  |  |  |  |
|-------------------------|-------------------------|-------------------------|-------------------------|
| ![About step icon](media/step-icons-about.png "About step icon")</br>About | ![Add license plate or item step icon](media/step-icons-add-lp.png "Add license plate or item step icon")</br>AddLpOrItem | ![Batch disposition step icon](media/step-icons-batch-disposition.png "Batch disposition step icon")</br>BatchDisposition | ![Carrier step icon](media/step-icons-carrier.png "Carrier step icon")</br>Carrier |
| ![Catch weight tag step icon](media/step-icons-cw-tag.png "Catch weight tag step icon")</br>CatchWeightTag | ![Catch weight tag weight step icon](media/step-icons-cw-tag-weight.png "Catch weight tag weight step icon")</br>CatchWeightTagWeight | ![Check digit step icon](media/step-icons-check-digit.png "Check digit step icon")</br>CheckDigit | ![Check in or out ID step icon](media/step-icons-check-in-out.png "Check in or out ID step icon")</br>CheckInOutId |
| ![Child license plate step icon](media/step-icons-child-lp.png "Child license plate step icon")</br>ChildLP | ![Cluster ID step icon](media/step-icons-cluster-id.png "Cluster ID step icon")</br>ClusterId | ![Cluster position step icon](media/step-icons-cluster-position.png "Cluster position step icon")</br>ClusterPosition | ![Config ID step icon](media/step-icons-config-id.png "Config ID step icon")</br>ConfigId |
| ![Configured field step icon](media/step-icons-configured-field.png "Configured field step icon")</br>ConfiguredField | ![Con or LP step icon](media/step-icons-con-lp.png "Con or LP step icon")</br>ConOrLP | ![Consolidate from license plate ID step icon](media/step-icons-consolidate-from-LP.png "Consolidate from license plate ID step icon")</br>ConsolidateFromLicensePlateID | ![Consolidate to license plate ID step icon](media/step-icons-consolidate-to-LP.png "Consolidate to license plate ID step icon")</br>ConsolidateToLicensePlateID |
| ![Container type step icon](media/step-icons-container-type.png "Container type step icon")</br>ContainerType | ![Counting step icon](media/step-icons-counting.png "Counting step icon")</br>Counting | ![Counting reason code step icon](media/step-icons-counting-reason.png "Counting reason code step icon")</br>CountingReasonCode | ![Country of origin code step icon](media/step-icons-country-origin.png "Country of origin code step icon")</br>CountryOfOrigin |
| ![Disposition step icon](media/step-icons-disposition.png "Disposition step icon")</br>Disposition | ![Done step icon](media/step-icons-done.png "Done step icon")</br>Done | ![Driver check in confirmation step icon](media/step-icons-driver-check-in-confirmation.png "Driver check-in confirmation step icon")</br>DriverCheckInConfirmation | ![Driver check in ID step icon](media/step-icons-driver-check-in-id.png "Driver check-in ID step icon")</br>DriverCheckInId |
| ![Driver check out ID step icon](media/step-icons-driver-check-out-id.png "Driver check-out ID step icon")</br>DriverCheckOutId | ![Expiration date step icon](media/step-icons-exp-date.png "Expiration date step icon")</br>ExpDate | ![Field step icon](media/step-icons-field.png "Field step icon")</br>Field | ![From batch disposition step icon](media/step-icons-from-batch.png "From batch disposition step icon")</br>FromBatchDisposition |
| ![From inventory status step icon](media/step-icons-from-inventory-status.png "From inventory status step icon")</br>FromInventoryStatus | ![ID attribute step icon](media/step-icons-id-attribute.png "ID attribute step icon")</br>IdAttribute | ![Inventory batch ID step icon](media/step-icons-invent-batch-id.png "Inventory batch ID step icon")</br>InventBatchID | ![Inventory color ID step icon](media/step-icons-invent-color-id.png "Inventory color ID step icon")</br>InventColorID |
| ![Inventory location step icon](media/step-icons-invent-location.png "Inventory location step icon")</br>InventLocation | ![Inventory serial ID step icon](media/step-icons-invent-serial-id.png "Inventory serial ID step icon")</br>InventSerialID | ![Inventory size ID step icon](media/step-icons-invent-size-id.png "Inventory size ID step icon")</br>InventSizeID | ![Inventory status ID step icon](media/step-icons-invent-status-id.png "Inventory status ID step icon")</br>InventStatusID |
| ![Inventory style ID step icon](media/step-icons-invent-style-id.png "Inventory style ID step icon")</br>InventStyleID | ![Inventory version ID step icon](media/step-icons-invent-version-id.png "Inventory version ID step icon")</br>InventVersionID | ![Item ID step icon](media/step-icons-item-id.png "Item ID step icon")</br>ItemID | ![ITM container ID step icon](media/step-icons-itm-contianer-id.png "ITM container ID step icon")</br>ITMContainerID |
| ![ITM shipment ID step icon](media/step-icons-itm-shipment-id.png "ITM shipment ID step icon")</br>ITMShipmentID | ![Kanban card ID step icon](media/step-icons-kanban-card-id.png "Kanban card ID step icon")</br>KanbanCardID | ![Kanban or card ID step icon](media/step-icons-kanban-or-card-id.png "Kanban or card ID step icon")</br>KanbanOrCardID | ![License plate ID step icon](media/step-icons-license-plate-id.png "License plate ID step icon")</br>LicensePlateID |
| ![Load ID step icon](media/step-icons-load-id.png "Load ID step icon")</br>LoadId | ![Location license plate position step icon](media/step-icons-location-lp-pos.png "Location license plate position step step icon")</br>LocationLicensePlatePosition | ![Location or license plate step icon](media/step-icons-location-or-lp.png "Location or license plate step icon")</br>LocOrLP | ![Location or license plate checkl step icon](media/step-icons-location-or-lp-check.png "Location or license plate check step icon")</br>LocOrLPCheck |
| ![Location or license plate from step icon](media/step-icons-location-or-lp-from.png "Location or license plate from step icon")</br>LocOrLPFrom | ![Location or license plate to step icon](media/step-icons-location-or-lp-to.png "Location or license plate to step icon")</br>LocOrLPTo | ![Long process completed step icon](media/step-icons-long-process-complete.png "Long process completed step icon")</br>LongProcessCompleted | ![LP break parent LP step icon](media/step-icons-lp-break-parent.png "LP break parent LP step step icon")</br>LPBreakParentLP |
| ![Merge container ID step icon](media/step-icons-merge-container.png "Merge container ID step icon")</br>MergeContainerId | ![Mixed license plate line number step icon](media/step-icons-mixed-lp-line.png "Mixed license plate line number step icon")</br>MixedLPLineNum | ![Product confirmation step icon](media/step-icons-product-confirm.png "Product confirmation step icon")</br>ProductConfirmation | ![Put step icon](media/step-icons-put.png "Put step icon")</br>Put |
| ![Outbound weight icon](media/step-icons-outbound-weight.png "Outbound weight icon")</br>OutboundWeight | ![Owner step icon](media/step-icons-owner.png "Owner step icon")</br>Owner | ![Parent license plate step icon](media/step-icons-parent-lp.png "Parent license plate step icon")</br>ParentLP | ![Please confirm step icon](media/step-icons-please-confirm.png "Please confirm step icon")</br>PleaseConfirm |
| ![Purchase order line number step icon](media/step-icons-po-line-num.png "Purchase order line number step icon")</br>POLineNum | ![Purchase order number step icon](media/step-icons-po-num.png "Purchase order number step icon")</br>PONum | ![Position full step icon](media/step-icons-position-full.png "Position full step icon")</br>PositionFull | ![Potency step icon](media/step-icons-potency.png "Potency step icon")</br>Potency |
| ![Printer name step icon](media/step-icons-printer-name.png "Printer name step icon")</br>PrinterName | ![Prod ID step icon](media/step-icons-prod-id.png "Prod ID step icon")</br>ProdId | ![Putaway cluster ID step icon](media/step-icons-putaway-cluster-id.png "Putaway cluster ID step icon")</br>PutawayClusterId | ![Quantity step icon](media/step-icons-qty.png "Quantity step icon")</br>Qty |
| ![Quantity adjust in step icon](media/step-icons-qty-adjust-in.png "Quantity adjust in step icon")</br>QtyAdjustIn | ![Quantity short step icon](media/step-icons-qty-short.png "Quantity short step icon")</br>QtyShort | ![Quantity to consume step icon](media/step-icons-qty-to-consume.png "Quantity to consume step icon")</br>QtyToConsume | ![Quantity to put step icon](media/step-icons-qty-to-put.png "Quantity to put step icon")</br>QtyToPut |
| ![Quantity to scrap step icon](media/step-icons-qty-to-scrap.png "Quantity to scrap step icon")</br>QtyToScrap | ![Quantity confirmation step icon](media/step-icons-qty-confirmation.png "Quantity confirmation step icon")</br>QuantityConfirmation | ![Report as finished end job step icon](media/step-icons-raf-end-job.png "Report as finished end job step icon")</br>RAFEndJob | ![Receive location ID step icon](media/step-icons-recv-loc-id.png "Receive location ID step icon")</br>RecvLocationID |
| ![Remove container ID step icon](media/step-icons-remove-container-id.png "Remove container ID step icon")</br>RemoveContainerID | ![RMA number step icon](media/step-icons-rma-no.png "RMA number step icon")</br>RMANum | ![Select order step icon](media/step-icons-select-order.png "Select order step icon")</br>SelectOrder | ![Short pick reason step icon](media/step-icons-short-pick-reason.png "Short pick reason step icon")</br>ShortPickReason |
| ![Sort position ID step icon](media/step-icons-sort-position-id.png "Sort position ID step icon")</br>SortPositionId | ![Target license plate ID step icon](media/step-icons-target-lp-id.png "Target license plate ID step icon")</br>TargetLicensePlateId | ![To line number step icon](media/step-icons-to-line-no.png "To line number step icon")</br>ToLineNum | ![To location step icon](media/step-icons-to-location.png "To location step icon")</br>ToLocation |
| ![To number step icon](media/step-icons-to-number.png "To number step icon")</br>ToNum | ![To warehouse step icon](media/step-icons-to-warehouse.png "To warehouse step icon")</br>ToWarehouse | ![Transport load ID step icon](media/step-icons-tranport-load-id.png "Transport load ID step icon")</br>TransportLoadId | ![Vendor batch ID step icon](media/step-icons-vendor-batch-id.png "Vendor batch ID step icon")</br>VendBatchId |
| ![Wave label ID step icon](media/step-icons-wave-label-id.png "Wave label ID step icon")</br>WaveLabelId | ![Wave label quantity step icon](media/step-icons-wave-label-qty.png "Wave label quantity step icon")</br>WaveLblQty | ![Weight step icon](media/step-icons-weight.png "Weight step icon")</br>Weight | ![Weight to consume step icon](media/step-icons-weight-to-consume.png "Weight to consume step icon")</br>WeightToConsume |
| ![WHS adjustment type step icon](media/step-icons-whs-adjustment-type.png "WHS adjustment type step icon")</br>WHSAdjustmentType | ![WHS receiving exception step icon](media/step-icons-whs-receiving-exception.png "WHS receiving exception step icon")</br>WHSReceivingException | ![WMS location ID step icon](media/step-icons-wms-location-id.png "WMS location ID step icon")</br>WMSLocationID | ![Work ID step icon](media/step-icons-work-id.png "Work ID step icon")</br>WorkId |
| ![Work ID to cancel step icon](media/step-icons-work-id-to-cancel.png "Work ID to cancel step icon")</br>WorkIdToCancel | ![Work license plate ID step icon](media/step-icons-work-lp-id.png "Work license plate ID step icon")</br>WorkLicensePlateId | ![Work license plate ID putaway cluster step icon](media/step-icons-work-lp-putaway-cluster.png "Work license plate ID putaway cluster step icon")</br>WorkLPIDPutawayCluster | ![Work pool ID step icon](media/step-icons-work-pool-id.png "Work pool ID step icon")</br>WorkPoolID |
| ![Zone ID step icon](media/step-icons-zone-pool-id.png "Zone ID step icon")</br>ZoneID |  |  |  |

## <a name="example"></a>Example of assigning step titles and icons for a custom flow

This example illustrates how to set up step titles and icons for a custom task flow. The scenario is built on a custom task flow example that is also presented and further explored in the blog post [Customizing the Warehousing Mobile App](https://cloudblogs.microsoft.com/dynamics365/it/2017/07/06/customizing-the-warehousing-mobile-app). The task flow works as follows:

1. The app shows a screen asking the worker to provide a container ID (for example, by scanning a barcode).
1. If the container ID is valid, the app opens a new screen, asking for the weight. (If the container ID isn't valid, the worker is returned to the first screen.)
1. When the worker enters a valid weight, the system stores the weight and returns to the initial screen.

The following figure illustrates this task flow.

![Task flow diagram](media/step-icons-example-task-flow.png "Task flow diagram")

### Create a step class for the container input screen

The container input screen enables the worker to scan or enter a container ID.

![Container input screen](media/step-icons-example-container-input.png "Container input screen")

On the container input screen, the control name of the input field is `ContainerId`, which is not in the [step ID list](#step-ids-classes), so you won't find an existing step based on this control name. Therefore, you must create a step class to present the step. The following code provides an example:

```xpp
[WHSMobileAppStepId('ContainerId')]
final internal class WHSMobileAppStepContainerId extends WHSMobileAppStep
{
    private const WHSMobileAppStepIcon PopulationIcon = 'InventBatchID';
    private const WHSMobileAppStepTitle InputNotFilledTitle = "@WAX:WHSMobileAppStepContainerID_InputNotFilled"; //Scan a container

    protected void initValues()
    {
        defaultStepIcon = PopulationIcon;
        defaultStepTitle = InputNotFilledTitle;
    }

}
```

The step icon identifier is stored in class member `defaultStepIcon` and step title is stored in class member `defaultStepTitle`.

To assign a step icon, set `defaultStepIcon` to one of the icon IDs listed in [Available step icons](#step-icons).

### Use a standard or custom step title and icon for the weight input

The weight input screen enables the worker to enter a weight.

![Weight input screen](media/step-icons-example-weight-input.png "Weight input screen")

On the weight input screen, the control name of the input field is `Weight` which is in the step ID list. So, if you can accept the step title and icon defined in class `WHSMobileAppStepWeight`, then you don't need to change anything this step.

However, if you prefer to use a different title or icon for this step, you can do so by overriding either the `stepId()` or `stepInfo()` method in the builder class. Each task flow has its own step info builder.

#### Override the stepId() method

The following code example shows one way to modify a builder class by overriding the `stepId()` method.

```xpp
[WHSWorkExecuteMode(WHSWorkExecuteMode:: WeighContainer)]
public class WHSMobileAppStepInfoBuilderWeighContainer extends WHSMobileAppStepInfoBuilder
{
    protected WHSMobileAppStepId stepId()
    {
        WHSMobileAppStepId stepIdLocal = super();

        if (stepIdLocal == 'Weight')
        {
            return 'NewWeight';
        }

        return stepIdLocal;
    }

}
```

Then create a step class for the `NewWeight` step, which should be similar to the `ContainerId` example provided previously.

#### Override method stepInfo()

The following code example shows one way to modify a builder class by overriding the `stepInfo()` method.

```xpp
[WHSWorkExecuteMode(WHSWorkExecuteMode:: WeighContainer)]
public class WHSMobileAppStepInfoBuilderWeighContainer extends WHSMobileAppStepInfoBuilder
{
    protected WHSMobileAppStepInfo stepInfo()
    {
        if (stepId != 'Weight')
        {
            return super();
        }

        WHSMobileAppStepInfo stepInfo = WHSMobileAppStepInfo::construct();
        stepInfo.parmStepIcon('NewIcon');
        stepInfo.parmStepTitle('NewTitle');
        return stepInfo;
    }

}
```

Then construct a `WHSMobileAppStepInfo` object and set the icon and/or title directly.

## Additional resources

- [Install and connect the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Mobile device user settings](mobile-device-user-settings.md)
