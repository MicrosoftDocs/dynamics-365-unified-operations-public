Introduction
============

In economic activity that involves an intermediary, there are three
participants:

-   The person who sells or purchases goods (works or services)

-   The third-party supplier or buyer

-   The intermediary between the first two participants

Russian legislation defines three legal forms of intermediation:

-   A commission agreement, where the committer (also known as the principal)
    engages a commissioner

-   An agency agreement, where the principal engages an agent

-   An assignment agreement, where the principal retains an attorney

The intermediary (that is, the commissioner, agent, or attorney) performs legal
actions and other actions (transactions) on behalf of the principal.
Intermediaries can perform these actions in one of two ways:

-   In their own name but at the principal's expense

-   In the principal's name and at the principal's expense

This topic provides information about the functionality for accounting
intermediary deals that are made by an agent. Throughout this topic, the term
*principal* refers to the party that engages the agent.

Overview
--------

The current implementation of this functionality has the following limitations:

-   Credit notes can be registered only in the module where the original
    factures were registered.

-   Sub-commission isn't supported.

-   No commission bonus is calculated.

-   No transactions are created in the general ledger, based on the report for
    the principal.

Preliminary setup
=================

Set up an inventory profile for an agent's transactions
-------------------------------------------------------

1.  Go to **Inventory management \> Setup \> Dimensions \> Inventory profiles**.

2.  Select **New** to create an inventory profile.

3.  In the **Inventory profile** field, enter a name for the inventory profile.

4.  In the **Name** field, enter a description.

5.  In the **Kind of activity** field, select **Commission agent**.

6.  Set the **Don't match** option to **No**.

7.  In the **Kind of inventory** field, specify **Common**.

8.  Select **Save**.

![A screenshot of a computer Description automatically generated](media/0a9c51ce5474f9cf5825f7827eef5eeb.png)

Set up the Inventory profile and Owner tracking dimensions
----------------------------------------------------------

1.  Go to **Product information management \> Setup \> Dimension and variant
    groups \> Tracking dimension groups**.

2.  Select **New** to create a dimension group.

3.  In the **Name** field, enter a name for the dimension group.

4.  In the **Description** field, enter a description.

5.  On the **Tracking dimensions** FastTab, set up the Inventory profile and
    Owner tracking dimensions:

-   On the **Inventory profile** line, select the **Active**, **Primary
    stocking**, **Physical inventory**, **Financial inventory**, **Coverage plan
    by dimensions**, and **Transfer** check boxes.

-   On the **Owner** line, select the **Active**, **Physical inventory**, and
    **Transfer** check boxes.

1.  Select **Save**.

![A screenshot of a cell phone Description automatically generated](media/497fe795792a699157dd804119f090aa.jpg)

Set up a number sequence for the report for the principal
---------------------------------------------------------

1.  Go to **General ledger \> Ledger setup \> General ledger parameters**.

2.  On the **Number sequences** tab, in the **Number sequence code** field,
    select a number sequence code for the **Report code** reference.
