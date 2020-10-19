# Replenishment

## Work XXXX cannot be unblocked because it has unfinished replenishment work.

**Issue:** Picking work is blocked with dependent replenishment work.

**Fix:** When using wave demand replenishment; if it is determined that a picking location must be replenished in order to fulfil the source order demand, then the system creates \*both\* the replenishment work and the picking work; however, it blocks the picking work until the replenishment work is completed. This is intentional because without completing the replenishment work, the picking location wouldn't have sufficient inventory.
