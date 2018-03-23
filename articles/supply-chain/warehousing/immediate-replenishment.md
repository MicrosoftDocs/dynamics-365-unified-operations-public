Immediate replenishment

Immediate replenishment allows you to replenish inventory right after a location
directive line has failed to allocate inventory. The replenishment will happen
based on a single line in the location directive setup and if inventory is not
on hand in this unit of measure, replenishment of the unit of measure that is
specified for this line will happen immediately.

Immediate replenishment provides an alternative to the method where allocation
of inventory is based on more lines in the location directive and where the
demand is summed up at the end of the allocation and replenished in the unit of
measure that is specified by the last line in the location directive. .

The benefit of using immediate replenishment is that replenishment can be
restricted by specific units and the quantity will be directed to specific
locations.

Business scenario

Say that we have a warehouse with picking areas for boxes and eaches, and we
want to optimize picking with as many boxes as possible and with the remaining
quantity, less than a box, to be picked from the each area. In this case, we can
use immediate replenishment to optimize the process. Immediate replenishment can
be set up for boxes which will enable you to replenish using demand
replenishment as soon as there is a shortage of boxes to be picked for the
demand quantity. This way the picking will be optimized to include as many boxes
as possible. Immediate replenishment will generate replenishment of the boxes
and the demand will not be passed on to have the quantities picked in eaches.
That is, only what was supposed to be picked in eaches, quantities of less than
a box, will be picked from the each area. In the case of a shortage in a box
area, we will still be able to send as many boxes as possible out of the total
demand and the rest will be picked from the each area.

Where it applies

Immediate replenishment is used during wave execution if allocation fails for a
location directive line that has a replenishment template set.

Set up immediate replenishment

-   Under **Warehouse management** \> **Setup** \> **Location directives**,
    select a replenishment template for wave demand in the **Immediate
    replenishment template** list on the **Lines** tab.

The replenishment template is applied if the location directive line fails to
allocate a dedicated unit of measure.

Troubleshooting

If immediate replenishment is selected for a location directive line, and no
replenishment work is generated when you use demand replenishment templates for
this location directive line, two main reasons need to be investigated.

1.  Make sure that the demand replenishment template that is applied is set up
    with the correct locations templates and with work templates of the type
    Replenishment.

2.  Make sure that the quantities of on-hand inventory are sufficient on the
    locations where the demand replenishment template searches for on-hand
    inventory for replenishment.
