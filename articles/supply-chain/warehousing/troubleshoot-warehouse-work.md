# Warehouse work

## Movement with serialized item issue.

**Issue:** Unable to move a license plate with "Movement" menu item if the serial number has "Blank issue allowed" and "Blank receipt allowed" in tracking dimension group and there are multiple license plates in the same location, some with serial number and some others without.

**Fix:** KB number: 4571546: Making "Serial number" field not mandatory, if Blank receipt and Blank issue are allowed.

## The inventory owner XXXX is not allowed in this process.

**Issue:** Inventory dimension Owner missing when making movements using the warehousing app. A regular inventory transfer journal from the D365 client appears to work as intended and can only be posted with the Owner dimension filled in.

**Fix:** Microsoft has evaluated this issue and determined it to be a feature limitation. Currently the warehouse management processes only supports inventory owned by the legal entity.
