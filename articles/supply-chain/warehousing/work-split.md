# Work Split
#
## About work split

Work split functionality is designed to provide possibility of splitting of work that is in status open or in progress. Warehouse managers need sometimes to split large works to multiple works in order to assign them to other warehouse workers,  so the same work can be simultaneously picked by several warehouse workers.

## All work and work details

Added a new button to the work details (_Warehouse management_ - _Work_ - _Work details)_ and all work (_Warehouse management_ - _ Work_ - _All work)_ forms in the WORK – WORK section of the ribbon called &#39;Split work&#39;

### Validation

The button will not be enabled if:

- There is a container id associated on the work header
  - Systematically splitting a container is not possible as it requires physical actions.
- The work is associated with a cluster
- The work order type is not:
  - Sales orders
  - Raw material picking
  - Transfer issue
- The work status is not &#39;Open&#39; or &#39;In Process&#39;
- The work is currently being split by another user (an error will be thrown when trying to enter the splitting screen for a work which is already being Split by another user)

A new Blocking Reason will be used to indicate if the work header is currently in the process of being split and will be referenced by both the work split form and the mobile device.

## Work split form

### Design

Following has been added to a form.

#### Ribbon

Two buttons:

- Split work – Triggers the new work split process
- The standard Options tab to personalize, use the advanced filter/sort, etc.

#### Grid

Show one grid that contains work lines

Fields:

- Line number
- Work status
- Item number
- Item name
- Location
- Location profile
- Zone Id
- Work quantity
- Unit
- Inventory dimensions fields (similar to the existing WHSWorkTable form)

### Initialization

When the form opens, by default show all initial pick work lines that are in an open status. The &#39;Split Work&#39; Blocking Reason will be inserted for the current work and the work will be blocked.

The name of the &#39;Blocked Wave&#39; field from work header was modified to &#39;Blocked&#39; when using the blocking reasons.

#### Mobile device user blocking

On the mobile device, if the work is being split, when the user tries to execute work, an error will be displayed &quot;The work with ID %1 is currently being split.&quot;.

The user can click Cancel button which will allow the user to exit the mobile device flow and process other work.

### Other operations blocking

Any operations that are modifying the work lines, work inventory transactions, or replenishment links related to a work that is being split will fail with an error : The work with ID %1 is currently being split.&quot;.

### Grid options

Add an option above the grid to let the user show all work lines if desired. The default behavior should be that only the open (available to be split) work lines are visible. If the user changes the option, all work lines should be shown. Label the checkbox &quot;Show all lines&quot;.

### Splitting

After the form has opened and the user has applied any filtering they want (either from the grid filters, location format filters, or query), they will select some or all the records shown in the grid (using the normal record selection functionality).

When the user clicks &#39;Split work&#39; in the action bar the system will create a new work header that contains all of the initial pick lines that are selected in the grid. The initial pick lines that are selected in the grid are cancelled on the original work header, and the new work header will contain all the selected work lines .

The system needs to validate that the &#39;Split Work&#39; Blocking Reason is still present when trying to perform the actual split operation. If it&#39;s not, then show the user the error &quot;Work splitting session no longer valid. Please close form and try again.&quot; There will not be performed any splitting actions.

The existing work template structure, and location of the put (as well as future pick/put pairs) will be maintained. The following work header fields will be copied from the original work to the new work:

- Load ID
- Shipment ID

- Order number
- Site
- Warehouse
- Work priority
- Work pool ID
- Wave ID
- Work creation number

The following fields will not be copied to the new work header:

- Work ID (new work ID generated from number sequence)
- Work status (Open)
- Locked by (Blank initially)
- Target license plate ID (Blank)
- Created date and time (Current date/time)
- Blocked wave/Frozen (it will be recomputed for the original and new work header)

The new work will also not be assigned to any user immediately. If desired, a user can be assigned using the existing functionality from the work details form.

### Finishing splitting of a work.

In order to finish the splitting of a work, the &#39;Split work&#39; blocking reasons has to be removed.

There are two possibilities to remove the &#39;Split Work&#39; blocking reason.

The first one is that the user which is splitting the work to close the &#39;Split Work&#39; form(button in the top right corner). When closing the form, the &#39;Split Work&#39; blocking reasons will be removed, the &#39;Blocked&#39; state of this work will be recomputed(if there no blocking reasons left for this work, the work will be unblocked ).

The second possibility is to press the &#39;Cancel work split session&#39; button. When having a work header selected and pressing this button, the &#39;Split work&#39; blocking reason will be removed and the &#39;Blocked&#39; state of this work will be recomputed, similar as when closing the &#39;split work&#39; form. This button can be clicked by a different user than the user which is splitting the work.

After the &#39;Split Work&#39; blocking reason is removed(and if the &#39;Blocked&#39; state is set to No), the work can be executed on the mobile device.



### Logging

When the new work header is created from the work that has been split, write a line in the work creation history log that the new work header was created by splitting the original work, and mention the original work Id : Work %1 has been created by splitting off from original work %2.

### Enable the feature

In order to enable the Split work feature, this step must be followed.

1. Enabled the &#39;WHSWorkBlockingToggle&#39; flight.
2. Go to &#39;Warehouse management parameters - General - Work&#39;. Click &#39;Upgrade blocking capabilities&#39; button. This button is visible only if the &#39;WHSWorkBlockingToggle&#39; is enabled. When clicking this button, all the the works which are not Closed or Cancelled and with the &#39;Blocked wave&#39; field set to True will be processed and blocking reasons will be added according to why the work is blocked. The blocking reasons are a way to know why the work is blocked.
The existing blocking reasons are &#39;HeldWave&#39;(work is blocked by a wave with status Held), &#39;Unprocessed Replenishment work&#39;(work is linked to unprocessed replenishment work), &#39;Undefined reason&#39;(either work was manually blocked or the work template is configured to block work) and &#39;Unprocessed overpick work&#39;(work is linked to unprocessed staging overpick work). It is possible to have a work blocked by multiple blocking reasons. The upgrade of the blocking reasons must be performed when there is no activity in the warehouse.
3. Enabled the &#39;WHSSplitWorkToggle&#39; flight. When this flight is activated, the &#39;Split work&#39; blocking reason will be used.

With the two flights enabled and the upgrade of the blocking reasons performed, the &#39;Split Work&#39; button will be visible, so the feature is activated.
