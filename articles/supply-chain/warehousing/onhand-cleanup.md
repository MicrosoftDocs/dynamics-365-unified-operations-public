# Improve performance by running the Warehouse management on-hand entries cleanup job – for New AX and for AX2012 R3 CU10

## Introduction

Calculation of the on-hand are used from many forms but also during many business processes, the latter being less obvious to end-users. Therefore, it is always of interest to us to improve the performance of these operations since the overall impact on many processes can be quite significant.

The nature of the queries used to calculate the on-hand involves joins and aggregation and the performance is affected by the number of records in the tables involved. One way to improve the performance of such operations is to reduce the number of records that SQL server has to consider.

In this posting we will cover the Warehouse management on-hand entries cleanup job which deletes records in the InventSum and WHSInventReserve tables. These tables are used to store on-hand information for items enabled for warehouse management processing (WHS items). Cleaning up these records can lead to significant improvements of the on-hand calculations.

The cleanup job is available for the new Dynamics AX and also for the in-market version of AX 2012 R3 with KB article 3063513 – Performance improvement of On-hand queries by running new clean up job for on-hand entries for WHS enabled items.


## Running the clean up

The cleanup job is available under Inventory Management>Periodic tasks>Clean up>Warehouse management on-hand entries cleanup.

The cleanup job can be ran during normal business hours but it is recommended to run it outside of working hours to avoid collisions where a user is updating a record that is also being cleaned up. By setting the Delete if not updated for this many days parameter in the dialog to an appropriate value, the risk of deleting used on-hand entries can be reduced.

If the job ends up trying to delete a record for an item while it is used by another user, a deadlock error will be experienced by either the cleanup job or the user impacting the on-hand of the item.

The job is running with a commit size of 100 meaning it will try to commit for every 100 deletes. However, since some deletes are set-based, there might be scenarios where more than 100 records can be deleted in the same transaction, hence there is no guarantee that lock escalations will not occur.

 

## What is the clean up job actually doing ?

That is a fair question that we were asked by our colleges in the field so we wanted to share the answer with you.

The overall idea is that the cleanup job is deleting records in the WHSInventReserve and InventSum tables where all the field values are 0, since these should not contribute to the on-hand. The job only deletes records below the Location level.

If negative physical inventory is allowed then we might not be able to delete all entries with all zeros, since we need to account for a special scenario where a license plate has multiple serial numbers and one serial number has gone negative.

For this special case we will do a breadth-first delete, trying to delete from lower levels first.

If we don’t allow negative physical inventory we will delete upwards the hierarchy. This approach means that for a scenario were we had serial number 1 and 2 on the same license plate and the job is stopped, we might still have a record in WHSInventReserve on the lowest level, e.g. for serial number 2 but not one on the level above that. This is ok, since no record, is semantically the same as “nothing available or reserved”.

If we should get on-hand again after records have been deleted, the records will just be re-created as part of the normal business logic.

 

## Possible user impact

A possible user impact is that if we have deleted all records for e.g. the license plate level, then the functionality where we can see that we at some point had on-hand at a license plate does not work as expected, simply because we have no on-hand entries to represent that.

This is the functionality where Quantity <> 0 is checked in the Dimension Display settings when viewing on-hand.

We decided that this was an acceptable loss of functionality compared to the performance improvement that customers should experience from cleaning up the records.

