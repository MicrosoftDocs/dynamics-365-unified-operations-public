Allocation

Understanding allocation in D365 business performance planning is fundamental for accurate and informed business planning. This article talks about how allocation operates at different levels within dimensions, so users can leverage D365 business performance planning effectively to strategize and plan business operations with confidence.

# Understanding Data Levels in Dimensions

Your data within Dataverse can have various levels underneath it. These levels depict hierarchical relationships, where for instance, a "parent" category may be followed by more specific "child" entities, such as a product category and its respective SKUs.

# Allocation Principles

## Allocation at different levels

When writing values at the "parent" level, BPP engages in allocation across all subsidiary "child" values. The allocation process varies based on certain conditions as described below.

## Allocation Options

### Equal Allocation for zero and equal amount child values

If all child values are \$0 or equal amounts, D365 Finance business performance planning defaults to an equal allocation across each child cell. For instance, allocating \$1,000 across 10 child cells results in \$100 allocated to each child.

### Respect for Preexisting Distributions

When child cells contain preexisting values, BPP respects this distribution. Allocation occurs proportionately based on existing values. For instance, allocating \$200 across 2 child cells with existing values \$5 and \$15 respectively results in \$50 and \$150 respectively.

Relative Increase

To enter a relative increase or decrease use **i** or **d** in front of the number for example **i10%** or **d10%** to increase or decrease by 10% or use the **Relative Increase/Decrease** option in the right-click context menu.

Fill right

Using **r** write the entered value to every cell on the same level to the right. For example **r1000** entered in January for a time dimension will write 1000 from February to December or use the **Fill Right** option in the right-click context menu.

Allocation with multi-select

If the multiselect mode is turned on the **s** prefix in the multi-select value dialog field allows you to spread an entry to the selected cells and use their current distribution.

Copy Like

This option is available only with right-click context menu and it enables you to apply any distribution in the used cube with your entry.

# Power of BPP for Accurate Business Planning

BPP empowers high-level business planning with an assurance that forecasted or budgeted data accurately mirrors historical actuals. This functionality allows users to:

-   Plan business strategies confidently at higher levels, knowing that BPP ensures alignment with historical data.
-   Leverage BPP's allocation mechanism, which adapts to various levels of granularity, ensuring accurate planning even when working with complex hierarchical data structures.
