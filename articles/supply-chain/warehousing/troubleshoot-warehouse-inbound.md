# Inbound warehouse operations

## Quality order XXXX has been generated. Cluster profile could not be found please check your configuration.

**Issue:** Related to a receiving process where QM or QMS is enabled; additional detail about the transaction could further enhance the fix.

**Fix:** Check the Cluster Profile set-up; you cannot use a cluster picking mobile device menu item without the cluster profiles.

## Mixed License Plate receiving doesn't work for other disposition codes than Credit.

**Issue:** The user is only able to successfully use the mixed License Plate receiving menu item when the disposition code is equal to "Credit".

**Remarks:** Microsoft has evaluated this issue and determined it to be a feature limitation. The Disposition codes with Action Credit and Scrap are only supported at this time.

## Update product receipts periodic task.

**Issue:** After running periodic task "Update product receipts" D365 automatically confirms unconfirmed purchase orders with a status of inventory transaction "Registered".

**Fix:** Use new inbound load handling. Requires feature management enablement: First enable \*\*Associate purchase order inventory transactions with load\*\*, this allows you to now enable the feature \*\*Over receipt of load quantities\*\*. Details for this feature will be found in the topic "Warehouse handling of inbound loads for purchase orders". https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/inbound-load-handling\#post-registered-quantities-from-the-load-page
