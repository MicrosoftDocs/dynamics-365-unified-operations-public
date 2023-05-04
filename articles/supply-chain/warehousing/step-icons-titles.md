---
title: Assign step icons and titles for the Warehouse Management mobile app
description: This article describes how to assign step icons and titles for new or customized task flows for the Warehouse Management mobile app.
author: Mirzaab
ms.date: 05/17/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this article to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-05-17
ms.dyn365.ops.version: 10.0.17
---

# Assign step icons and titles for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article describes how to assign step icons and step titles for new or customized task flows for the Warehouse Management mobile app.

The following illustrations shows how step icons and titles appear in the Warehouse Management mobile app.

![Example of a step icon and a step title in the Warehouse Management mobile app.](media/step-icon-example.png "Example of a step icon and a step title in the Warehouse Management mobile app")

## Turn this feature on or off

To use the functionality described in this article, the *User settings, icons, and step titles for the new warehouse app* feature must be turned on for your system. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *User settings, icons, and step titles for the new warehouse app* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Standard step IDs, classes, and icons

Each step in a task flow is identified by a step ID, and each step ID has a corresponding step class. The step icon and title are specified in each step class.

### <a name="step-ids-classes"></a>Step IDs and step classes

The following table lists every step ID that is currently available, and its corresponding step class. The control name of the primary input field is used as the step ID.

For an example that shows how these step IDs and classes are used, see the implementation of the `WHSMobileAppStepInfoBuilder.stepId()` method in the [Example: Assign step icons and titles for a custom flow](#example) section later in this article.

| Step ID | Step Class |
|-|-|
| BatchDisposition | WHSMobileAppStepBatchDisposition |
| Carrier | WHSMobileAppStepCarrier |
| CatchWeight | WHSMobileAppStepCatchWeight |
| CatchWeightQtyOutboundWeight | WHSMobileAppStepCatchWeight |
| CatchWeightTag | WHSMobileAppStepCatchWeightTag |
| CatchWeightTagWeight | WHSMobileAppStepCatchWeightTagWeight |
| ChangeWarehouseSuccess | WHSMobileAppStepChangeWarehouseSuccess |
| CheckDigit | WHSMobileAppStepCheckDigit |
| ClusterId | WHSMobileAppStepClusterId |
| ClusterPickQtyVerification | WHSMobileAppStepQtyVerification |
| ClusterPosition | WHSMobileAppStepClusterPosition |
| ConfigId | WHSMobileAppStepConfigId |
| Confirmation | WHSMobileAppStepConfirmation |
| ConsolidateFromLicensePlateId | WHSMobileAppStepConsolidateFromLicensePlateId |
| ConsolidateLPConfirmation | WHSMobileAppStepConsolidateLPConfirmation |
| ConsolidateToLicensePlateId | WHSMobileAppStepConsolidateToLicensePlateId |
| ContainerType | WHSMobileAppStepContainerType |
| CountingReasonCode | WHSMobileAppStepCountingReasonCode |
| CycleCountingAddLPOrFinish | WHSMobileAppStepCycleCountingAddLPOrFinish |
| CycleCountQty1 | WHSMobileAppStepCycleCountQty |
| CycleCountQty2 | WHSMobileAppStepCycleCountQty |
| CycleCountQty3 | WHSMobileAppStepCycleCountQty |
| CycleCountQty4 | WHSMobileAppStepCycleCountQty |
| Disposition | WHSMobileAppStepDisposition |
| DriverCheckInConfirmation | WHSMobileAppStepDriverCheckInConfirmation |
| DriverCheckInId | WHSMobileAppStepDriverCheckInId |
| DriverCheckOutConfirmation | WHSMobileAppStepDriverCheckOutConfirmation |
| DriverCheckOutId | WHSMobileAppStepDriverCheckOutId |
| ExpDate | WHSMobileAppStepExpDate |
| FromBatchDisposition | WHSMobileAppStepFromBatchDisposition |
| FromInventoryStatus | WHSMobileAppStepInventoryStatusFrom |
| FullQty | WHSMobileAppStepFullQty |
| InboundPut | WHSMobileAppStepInboundPut |
| InventBatchId | WHSMobileAppStepBatch |
| InventColorId | WHSMobileAppStepInventColorId |
| InventLocation | WHSMobileAppStepInventLocation |
| InventLocationId | WHSMobileAppStepWarehouse |
| InventSerialId | WHSMobileAppStepInventSerialId |
| InventSizeId | WHSMobileAppStepInventSizeId |
| InventStatusId | WHSMobileAppStepInventStatus |
| InventStyleId | WHSMobileAppStepInventStyleId |
| InventVersionId | WHSMobileAppStepInventVersionId |
| ItemId | WHSMobileAppStepItem |
| ITMContainerID | ITMMobileAppStepContainerId |
| ITMShipmentID | ITMMobileAppStepShipmentId |
| KanbanCardId | WHSMobileAppStepKanbanCard |
| KanbanCardToEmpty | WHSMobileAppStepKanbanCardToEmpty |
| KanbanOrCardId | WHSMobileAppStepKanbanCard |
| LicensePlateId | WHSMobileAppStepLicensePlate |
| LoadId | WHSMobileAppStepLoadId |
| LocationLicensePlatePosition | WHSMobileAppStepLocationLicensePlatePosition |
| LocOrLP | WHSMobileAppStepLocOrLP |
| LocOrLP_From | WHSMobileAppStepLocOrLPFrom |
| LocOrLP_To | WHSMobileAppStepLocOrLPTo |
| LocOrLPCheck | WHSMobileAppStepLocOrLPCheck |
| LocVerification | WHSMobileAppStepLocVerification |
| LPAdjustIn | WHSMobileAppStepLPAdjustIn |
| LPBreakChildLP | WHSMobileAppStepLPBreakChildLP |
| LPBreakParentLP | WHSMobileAppStepLPBreakParentLP |
| LPBuildChildLP | WHSMobileAppStepLPBuildChildLP |
| LPBuildParentLP | WHSMobileAppStepLPBuildParentLP |
| LPVerification | WHSMobileAppStepLPVerification |
| MergeContainerId | WHSMobileAppStepMergeContainerId |
| MixedLPLineNum | WHSMobileAppStepMixedLPLineNum |
| MobileDeviceQueueMessageCollectionIdentifierId | WHSMobileAppStepSelectOrder |
| MovementConfirmCancel | WHSMobileAppStepMovementConfirmCancel |
| NewCaptureWeight | WHSMobileAppStepCatchWeight |
| NewQty | WHSMobileAppStepNewQty |
| OutboundCatchWeightTag | WHSMobileAppStepCatchWeightTag |
| OutboundPut | WHSMobileAppStepOutboundPut |
| OutboundWeight | WHSMobileAppStepCatchWeight |
| OverridePutNewLocation | WHSMobileAppStepOverridePutNewLocation |
| PieceByPieceConfirmation | WHSMobileAppStepQtyVerification |
| POLineNum | WHSMobileAppStepPOLineNum |
| PONum | WHSMobileAppStepPONum |
| PositionFull | WHSMobileAppStepPositionFull |
| PositionFullQty | WHSMobileAppStepPositionFullQty |
| Potency | WHSMobileAppStepPotency |
| PrinterName | WHSMobileAppStepPrinterName |
| ProdId | WHSMobileAppStepProdId |
| ProdLastPalletConfirmation | WHSMobileAppStepProdLastPalletConfirmation |
| ProductConfirmation | WHSMobileAppStepProductConfirmation |
| ProductionScrapConfirmation | WHSMobileAppStepProductionScrapConfirmation |
| Put | WHSMobileAppStepPut |
| PutawayClusterId | WHSMobileAppStepPutawayClusterId |
| Qty | WHSMobileAppStepQty |
| QtyAdjust | WHSMobileAppStepQtyAdjust |
| QtyShort | WHSMobileAppStepQtyShort |
| QtyToConsume | WHSMobileAppStepQtyToConsume |
| QtyToPick | WHSMobileAppStepQtyToPick |
| QtyToPut | WHSMobileAppStepQtyToPut |
| QtyToScrap | WHSMobileAppStepQtyToScrap |
| QtyVerification | WHSMobileAppStepQtyVerification |
| QtyWithScanningLimit | WHSMobileAppStepQtyAdjust |
| ReasonString | WHSMobileAppStepReasonString |
| RecvLocationId | WHSMobileAppStepRecvLocationId |
| RemoveContainerId | WHSMobileAppStepRemoveContainerId |
| ReprintLabelConfirmation | WHSMobileAppStepReprintLabelConfirmation |
| RMANum | WHSMobileAppStepRMANum |
| ShortPickReason | WHSMobileAppStepShortPickReason |
| SortConOrLP | WHSMobileAppStepSortConOrLP |
| SortLicensePlateId | WHSMobileAppStepSortLicensePlateId |
| SortPositionId | WHSMobileAppStepSortPositionId |
| SortVerification | WHSMobileAppStepSortVerification |
| StartLocationId | WHSMobileAppStepStartLocationId |
| StartProdOrderConfirmation | WHSMobileAppStepStartProdOrderConfirmation |
| TargetLicensePlateId | WHSMobileAppStepTargetLicensePlateId |
| TOLineNum | WHSMobileAppStepTOLineNum |
| ToLocation | WHSMobileAppStepToLocation |
| TONum | WHSMobileAppStepTONum |
| ToWarehouse | WHSMobileAppStepWarehouseTo |
| TransportLoadId | WHSMobileAppStepTransportLoadId |
| WaveLabelId | WHSMobileAppStepWaveLabelId |
| WaveLblQty | WHSMobileAppStepWaveLblQty |
| Weight | WHSMobileAppStepWeight |
| WeightToConsume | WHSMobileAppStepWeightToConsume |
| WHSAdjustmentType | WHSMobileAppStepWHSAdjustmentType |
| WHSReceivingException | WHSMobileAppStepWHSReceivingException |
| WHSWorkException | WHSMobileAppStepWHSWorkException |
| WHSWorkLicensePlateId | WHSMobileAppStepWorkLicensePlateId |
| WMSLocationId | WHSMobileAppStepLocation |
| WorkId | WHSMobileAppStepWorkId |
| WorkIdToCancel | WHSMobileAppStepWorkIdToCancel |
| WorkLPIdPutawayCluster | WHSMobileAppStepWorkLPIdPutawayCluster |
| WorkPoolId | WHSMobileAppStepWorkPoolId |
| ZoneId | WHSMobileAppStepZoneId |

### <a name="step-icons"></a>Available step icons

The system includes a collection of standard step icons that you can also use for your custom steps. You can't currently upload custom step icons. Therefore, you must always select one of the standard step icons.

The following table shows every standard step icon that is currently available, and its name.

<table>
<tbody>
<tr>
<td><img src="media/step-icons-about.png" alt="About step icon" title="About step icon"><br>About</td>
<td><img src="media/step-icons-add-lp.png" alt="Add license plate or item step icon" title="Add license plate or item step icon"><br>AddLpOrItem</td>
<td><img src="media/step-icons-batch-disposition.png" alt="Batch disposition step icon" title="Batch disposition step icon"><br>BatchDisposition</td>
<td><img src="media/step-icons-carrier.png" alt="Carrier step icon" title="Carrier step icon"><br>Carrier</td>
</tr>
<tr>
<td><img src="media/step-icons-cw-tag.png" alt="Catch weight tag step icon" title="Catch weight tag step icon"><br>CatchWeightTag</td>
<td><img src="media/step-icons-cw-tag-weight.png" alt="Catch weight tag weight step icon" title="Catch weight tag weight step icon"><br>CatchWeightTagWeight</td>
<td><img src="media/step-icons-check-digit.png" alt="Check digit step icon" title="Check digit step icon"><br>CheckDigit</td>
<td><img src="media/step-icons-check-in-out.png" alt="Check in or out ID step icon" title="Check in or out ID step icon"><br>CheckInOutId</td>
</tr>
<tr>
<td><img src="media/step-icons-child-lp.png" alt="Child license plate step icon" title="Child license plate step icon"><br>ChildLP</td>
<td><img src="media/step-icons-cluster-id.png" alt="Cluster ID step icon" title="Cluster ID step icon"><br>ClusterId</td>
<td><img src="media/step-icons-cluster-position.png" alt="Cluster position step icon" title="Cluster position step icon"><br>ClusterPosition</td>
<td><img src="media/step-icons-config-id.png" alt="Config ID step icon" title="Config ID step icon"><br>ConfigId</td>
</tr>
<tr>
<td><img src="media/step-icons-configured-field.png" alt="Configured field step icon" title="Configured field step icon"><br>ConfiguredField</td>
<td><img src="media/step-icons-con-lp.png" alt="Con or LP step icon" title="Con or LP step icon"><br>ConOrLP</td>
<td><img src="media/step-icons-consolidate-from-LP.png" alt="Consolidate from license plate ID step icon" title="Consolidate from license plate ID step icon"><br>ConsolidateFromLicensePlateID</td>
<td><img src="media/step-icons-consolidate-to-LP.png" alt="Consolidate to license plate ID step icon" title="Consolidate to license plate ID step icon"><br>ConsolidateToLicensePlateID</td>
</tr>
<tr>
<td><img src="media/step-icons-container-type.png" alt="Container type step icon" title="Container type step icon"><br>ContainerType</td>
<td><img src="media/step-icons-counting.png" alt="Counting step icon" title="Counting step icon"><br>Counting</td>
<td><img src="media/step-icons-counting-reason.png" alt="Counting reason code step icon" title="Counting reason code step icon"><br>CountingReasonCode</td>
<td><img src="media/step-icons-country-origin.png" alt="Country of origin code step icon" title="Country of origin code step icon"><br>CountryOfOrigin</td>
</tr>
<tr>
<td><img src="media/step-icons-disposition.png" alt="Disposition step icon" title="Disposition step icon"><br>Disposition</td>
<td><img src="media/step-icons-done.png" alt="Done step icon" title="Done step icon"><br>Done</td>
<td><img src="media/step-icons-driver-check-in-confirmation.png" alt="Driver check in confirmation step icon" title="Driver check in confirmation step icon"><br>DriverCheckInConfirmation</td>
<td><img src="media/step-icons-driver-check-in-id.png" alt="Driver check in ID step icon" title="Driver check in ID step icon"><br>DriverCheckInId</td>
</tr>
<tr>
<td><img src="media/step-icons-driver-check-out-id.png" alt="Driver check out ID step icon" title="Driver check out ID step icon"><br>DriverCheckOutId</td>
<td><img src="media/step-icons-exp-date.png" alt="Expiration date step icon" title="Expiration date step icon"><br>ExpDate</td>
<td><img src="media/step-icons-field.png" alt="Field step icon" title="Field step icon"><br>Field</td>
<td><img src="media/step-icons-from-batch.png" alt="From batch disposition step icon" title="From batch disposition step icon"><br>FromBatchDisposition</td>
</tr>
<tr>
<td><img src="media/step-icons-from-inventory-status.png" alt="From inventory status step icon" title="From inventory status step icon"><br>FromInventoryStatus</td>
<td><img src="media/step-icons-id-attribute.png" alt="ID attribute step icon" title="ID attribute step icon"><br>IdAttribute</td>
<td><img src="media/step-icons-invent-batch-id.png" alt="Inventory batch ID step icon" title="Inventory batch ID step icon"><br>InventBatchID</td>
<td><img src="media/step-icons-invent-color-id.png" alt="Inventory color ID step icon" title="Inventory color ID step icon"><br>InventColorID</td>
</tr>
<tr>
<td><img src="media/step-icons-invent-location.png" alt="Inventory location step icon" title="Inventory location step icon"><br>InventLocation</td>
<td><img src="media/step-icons-invent-serial-id.png" alt="Inventory serial ID step icon" title="Inventory serial ID step icon"><br>InventSerialID</td>
<td><img src="media/step-icons-invent-size-id.png" alt="Inventory size ID step icon" title="Inventory size ID step icon"><br>InventSizeID</td>
<td><img src="media/step-icons-invent-status-id.png" alt="Inventory status ID step icon" title="Inventory status ID step icon"><br>InventStatusID</td>
</tr>
<tr>
<td><img src="media/step-icons-invent-style-id.png" alt="Inventory style ID step icon" title="Inventory style ID step icon"><br>InventStyleID</td>
<td><img src="media/step-icons-invent-version-id.png" alt="Inventory version ID step icon" title="Inventory version ID step icon"><br>InventVersionID</td>
<td><img src="media/step-icons-item-id.png" alt="Item ID step icon" title="Item ID step icon"><br>ItemID</td>
<td><img src="media/step-icons-itm-contianer-id.png" alt="ITM container ID step icon" title="ITM container ID step icon"><br>ITMContainerID</td>
</tr>
<tr>
<td><img src="media/step-icons-itm-shipment-id.png" alt="ITM shipment ID step icon" title="ITM shipment ID step icon"><br>ITMShipmentID</td>
<td><img src="media/step-icons-kanban-card-id.png" alt="Kanban card ID step icon" title="Kanban card ID step icon"><br>KanbanCardID</td>
<td><img src="media/step-icons-kanban-or-card-id.png" alt="Kanban or card ID step icon" title="Kanban or card ID step icon"><br>KanbanOrCardID</td>
<td><img src="media/step-icons-license-plate-id.png" alt="License plate ID step icon" title="License plate ID step icon"><br>LicensePlateID</td>
</tr>
<tr>
<td><img src="media/step-icons-load-id.png" alt="Load ID step icon" title="Load ID step icon"><br>LoadId</td>
<td><img src="media/step-icons-location-lp-pos.png" alt="Location license plate position step icon" title="Location license plate position step icon"><br>LocationLicensePlatePosition</td>
<td><img src="media/step-icons-location-or-lp.png" alt="Location or license plate step icon" title="Location or license plate step icon"><br>LocOrLP</td>
<td><img src="media/step-icons-location-or-lp-check.png" alt="Location or license plate check step icon" title="Location or license plate check step icon"><br>LocOrLPCheck</td>
</tr>
<tr>
<td><img src="media/step-icons-location-or-lp-from.png" alt="Location or license plate from step icon" title="Location or license plate from step icon"><br>LocOrLPFrom</td>
<td><img src="media/step-icons-location-or-lp-to.png" alt="Location or license plate to step icon" title="Location or license plate to step icon"><br>LocOrLPTo</td>
<td><img src="media/step-icons-long-process-complete.png" alt="Long process completed step icon" title="Long process completed step icon"><br>LongProcessCompleted</td>
<td><img src="media/step-icons-lp-break-parent.png" alt="LP break parent LP step icon" title="LP break parent LP step icon"><br>LPBreakParentLP</td>
</tr>
<tr>
<td><img src="media/step-icons-merge-container.png" alt="Merge container ID step icon" title="Merge container ID step icon"><br>MergeContainerId</td>
<td><img src="media/step-icons-mixed-lp-line.png" alt="Mixed license plate line number step icon" title="Mixed license plate line number step icon"><br>MixedLPLineNum</td>
<td><img src="media/step-icons-outbound-weight.png" alt="Outbound weight step icon" title="Outbound weight step icon"><br>OutboundWeight</td>
<td><img src="media/step-icons-owner.png" alt="Owner step icon" title="Owner step icon"><br>Owner</td>
</tr>
<tr>
<td><img src="media/step-icons-parent-lp.png" alt="Parent license plate step icon" title="Parent license plate step icon"><br>ParentLP</td>
<td><img src="media/step-icons-please-confirm.png" alt="Please confirm step icon" title="Please confirm step icon"><br>PleaseConfirm</td>
<td><img src="media/step-icons-po-line-num.png" alt="Purchase order line number step icon" title="Purchase order line number step icon"><br>POLineNum</td>
<td><img src="media/step-icons-po-num.png" alt="Purchase order number step icon" title="Purchase order number step icon"><br>PONum</td>
</tr>
<tr>
<td><img src="media/step-icons-position-full.png" alt="Position full step icon" title="Position full step icon"><br>PositionFull</td>
<td><img src="media/step-icons-potency.png" alt="Potency step icon" title="Potency step icon"><br>Potency</td>
<td><img src="media/step-icons-printer-name.png" alt="Printer name step icon" title="Printer name step icon"><br>PrinterName</td>
<td><img src="media/step-icons-prod-id.png" alt="Prod ID step icon" title="Prod ID step icon"><br>ProdId</td>
</tr>
<tr>
<td><img src="media/step-icons-product-confirm.png" alt="Product confirmation step icon" title="Product confirmation step icon"><br>ProductConfirmation</td>
<td><img src="media/step-icons-put.png" alt="Put step icon" title="Put step icon"><br>Put</td>
<td><img src="media/step-icons-putaway-cluster-id.png" alt="Putaway cluster ID step icon" title="Putaway cluster ID step icon"><br>PutawayClusterId</td>
<td><img src="media/step-icons-qty.png" alt="Quantity step icon" title="Quantity step icon"><br>Qty</td>
</tr>
<tr>
<td><img src="media/step-icons-qty-adjust-in.png" alt="Quantity adjust in step icon" title="Quantity adjust in step icon"><br>QtyAdjustIn</td>
<td><img src="media/step-icons-qty-short.png" alt="Quantity short step icon" title="Quantity short step icon"><br>QtyShort</td>
<td><img src="media/step-icons-qty-to-consume.png" alt="Quantity to consume step icon" title="Quantity to consume step icon"><br>QtyToConsume</td>
<td><img src="media/step-icons-qty-to-put.png" alt="Quantity to put step icon" title="Quantity to put step icon"><br>QtyToPut</td>
</tr>
<tr>
<td><img src="media/step-icons-qty-to-scrap.png" alt="Quantity to scrap step icon" title="Quantity to scrap step icon"><br>QtyToScrap</td>
<td><img src="media/step-icons-qty-confirmation.png" alt="Quantity confirmation step icon" title="Quantity confirmation step icon"><br>QuantityConfirmation</td>
<td><img src="media/step-icons-raf-end-job.png" alt="Report as finished end job step icon" title="Report as finished end job step icon"><br>RAFEndJob</td>
<td><img src="media/step-icons-recv-loc-id.png" alt="Receive location ID step icon" title="Receive location ID step icon"><br>RecvLocationID</td>
</tr>
<tr>
<td><img src="media/step-icons-remove-container-id.png" alt="Remove container ID step icon" title="Remove container ID step icon"><br>RemoveContainerID</td>
<td><img src="media/step-icons-rma-no.png" alt="RMA number step icon" title="RMA number step icon"><br>RMANum</td>
<td><img src="media/step-icons-select-order.png" alt="Select order step icon" title="Select order step icon"><br>SelectOrder</td>
<td><img src="media/step-icons-short-pick-reason.png" alt="Short pick reason step icon" title="Short pick reason step icon"><br>ShortPickReason</td>
</tr>
<tr>
<td><img src="media/step-icons-sort-position-id.png" alt="Sort position ID step icon" title="Sort position ID step icon"><br>SortPositionId</td>
<td><img src="media/step-icons-target-lp-id.png" alt="Target license plate ID step icon" title="Target license plate ID step icon"><br>TargetLicensePlateId</td>
<td><img src="media/step-icons-to-line-no.png" alt="To line number step icon" title="To line number step icon"><br>ToLineNum</td>
<td><img src="media/step-icons-to-location.png" alt="To location step icon" title="To location step icon"><br>ToLocation</td>
</tr>
<tr>
<td><img src="media/step-icons-to-number.png" alt="To number step icon" title="To number step icon"><br>ToNum</td>
<td><img src="media/step-icons-to-warehouse.png" alt="To warehouse step icon" title="To warehouse step icon"><br>ToWarehouse</td>
<td><img src="media/step-icons-tranport-load-id.png" alt="Transport load ID step icon" title="Transport load ID step icon"><br>TransportLoadId</td>
<td><img src="media/step-icons-vendor-batch-id.png" alt="Vendor batch ID step icon" title="Vendor batch ID step icon"><br>VendBatchId</td>
</tr>
<tr>
<td><img src="media/step-icons-wave-label-id.png" alt="Wave label ID step icon" title="Wave label ID step icon"><br>WaveLabelId</td>
<td><img src="media/step-icons-wave-label-qty.png" alt="Wave label quantity step icon" title="Wave label quantity step icon"><br>WaveLblQty</td>
<td><img src="media/step-icons-weight.png" alt="Weight step icon" title="Weight step icon"><br>Weight</td>
<td><img src="media/step-icons-weight-to-consume.png" alt="Weight to consume step icon" title="Weight to consume step icon"><br>WeightToConsume</td>
</tr>
<tr>
<td><img src="media/step-icons-whs-adjustment-type.png" alt="WMS adjustment type step icon" title="WMS adjustment type step icon"><br>WHSAdjustmentType</td>
<td><img src="media/step-icons-whs-receiving-exception.png" alt="WMS receiving exception step icon" title="WMS receiving exception step icon"><br>WHSReceivingException</td>
<td><img src="media/step-icons-wms-location-id.png" alt="WMS location ID step icon" title="WMS location ID step icon"><br>WMSLocationID</td>
<td><img src="media/step-icons-work-id.png" alt="Work ID step icon" title="Work ID step icon"><br>WorkId</td>
</tr>
<tr>
<td><img src="media/step-icons-work-id-to-cancel.png" alt="Work ID to cancel step icon" title="Work ID to cancel step icon"><br>WorkIdToCancel</td>
<td><img src="media/step-icons-work-lp-id.png" alt="Work license plate ID step icon" title="Work license plate ID step icon"><br>WorkLicensePlateId</td>
<td><img src="media/step-icons-work-lp-putaway-cluster.png" alt="Work license plate ID putaway cluster step icon" title="Work license plate ID putaway cluster step icon"><br>WorkLPIDPutawayCluster</td>
<td><img src="media/step-icons-work-pool-id.png" alt="Work pool ID step icon" title="Work pool ID step icon"><br>WorkPoolID</td>
</tr>
<tr>
<td><img src="media/step-icons-zone-pool-id.png" alt="Zone ID step icon" title="Zone ID step icon"><br>ZoneID</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## <a name="example"></a>Example: Assign step icons and titles for a custom flow

This example explains how to set up step icons and titles for a custom task flow. The scenario is built on an example of a custom task flow that is presented and explored in more detail in the following blog post: [Customizing the Warehousing Mobile App](https://cloudblogs.microsoft.com/dynamics365/it/2017/07/06/customizing-the-warehousing-mobile-app). The task flow works in the following way:

1. The app shows a page that prompts the worker to provide a container ID (for example, by scanning a bar code).
1. If the container ID is valid, the app opens a new page that prompts the worker for the weight. (If the container ID isn't valid, the worker is returned to the first page.)
1. When the worker enters a valid weight, the system stores the weight and returns the worker to the first page.

The following illustration shows this task flow.

![Task flow diagram.](media/step-icons-example-task-flow.png "Task flow diagram")

### Create a step class for the container input page

The container input page lets the worker scan or enter a container ID.

![Container input page.](media/step-icons-example-container-input.png "Container input page")

On the container input page, the control name of the input field is `ContainerId`. Because this control name isn't in the [list of step IDs](#step-ids-classes), you won't find an existing step that is based on it. Therefore, you must create a step class that represents the step. Here is an example.

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

The identifier of the step icon is stored in the `defaultStepIcon` class member, and the step title is stored in the `defaultStepTitle` class member.

To assign a step icon, set `defaultStepIcon` to one of the icon IDs that are listed in the [Available step icons](#step-icons) section earlier in this article.

### Use a standard or custom step icon and title for the weight input

The weight input page lets the worker enter a weight.

![Weight input page.](media/step-icons-example-weight-input.png "Weight input page")

On the weight input page, the control name of the input field is `Weight`, which is in the [list of step IDs](#step-ids-classes). Therefore, if the step icon and title that are defined in the `WHSMobileAppStepWeight` class are acceptable to you, you don't have to change anything for this step.

However, if you prefer to use a different icon or title for this step, you can override either the `stepId()` method or the `stepInfo()` method in the builder class. Each task flow has its own step info builder.

#### Override the stepId() method

The following example shows one way that you can modify a builder class by overriding the `stepId()` method.

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

You then create a step class for the `NewWeight` step. The code should resemble the code for the `ContainerId` example that was shown earlier in this article.

#### Override the stepInfo() method

The following example shows one way that you can modify a builder class by overriding the `stepInfo()` method.

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

You then construct a `WHSMobileAppStepInfo` object, and set the icon and/or title directly.

## Additional resources

- [Install and connect the Warehouse Management mobile app](install-configure-warehouse-management-app.md)
- [Mobile device user settings](mobile-device-user-settings.md)
