# Auto release shipment for cross docking

This topic describes a cross docking strategy that allows you to automatically release a demand order to the warehouse, and to move the quantity required for its fulfillment from the production output location directly to outbound location when production order supplying the demand quantity is reported as finished.

Cross docking is a warehouse handling flow where quantity required to fulfil an outbound order is directed towards the order&#39;s outbound dock or staging area from the location of the inbound order (purchase, transfer or production) receipt. While the Advanced cross-docking feature [link to the article] supports all supply and demand orders, and requires the outbound demand to be released by the time cross-dock opportunity is identified, the Auto-release shipment feature:

- supports only production order as supply, and sales and transfer orders as demand
- does not require the demand order to have been released to warehouse prior to registration of the supply receipt, i.e. report as finished of production order, for the cross-docking work operation to commence

The advantage of this cross-docking functionality is two-fold:

- allow the warehouse operations to skip putting finished goods quantities away to the regular warehouse storage area, only to be picked up again for the outbound order fulfilment, and instead to move quantities once - from output location to a packing/shipping location. This minimizes the number of times stock is being handled and ultimately maximizes time and space savings on the warehouse shop floor.
- allow the warehouse operations to postpone releasing sales and transfer orders to the warehouse until the finished goods output of the associated production order is reported as finished. This may be particularly relevant in the make-to-order production environments where manufacturing lead times tend to be longer compared to make-to-stock operations.

## Auto-release shipment for cross-docking prerequisites

| Prerequisite | Description |
| --- | --- |
| Item | The item must be enabled for warehouse management processes. **Note:** Catchweight-enabled items cannot be included in the cross-docking processes |
| Warehouse | The warehouse must be enabled for warehouse management processes. |
| Cross docking templates | At least one cross docking template with the **At supply receipt** Demand release policy must be set up for a given warehouse |
| Work class | A cross docking work class ID for the **Cross docking** work order type must be created |
| Work templates | Work templates of the **Cross docking**  **work order** type are required in order to create cross docking pick and put work. |
| Location directives | Location directives of the **Cross docking**  **work order** typeare required to guide **Put** work to the locations at/from which sales order quantity are to be packed/shipped |
| Marking between demand order and production order exists | Sales and transfer orders must be reserved and marked against a production order in order for the warehouse system to trigger automatic release of the outbound order shipment and create a cross docking work at the report-as-finished action.   |

## A cross docking flow

A cross docking flow typically progresses through the key steps as follows:

1. A sales order taker creates a sales order for a make-to-order product. Typically, the requested quantity is not on-hand and must be produced first.
2. A sales order taker creates a production order directly from the sales order line, which reserves and marks the sales order quantity against the production order quantity. Alternatively, a production planner specifies that marking must be updated when firming planned orders.
3. Production order goes through a series of execution steps as follows:
   1. a production planner estimates (including raw material reservation) and releases (including release to warehouse) production order
   2. a warehouse worker starts and completes raw material picking from the storage to the production input location according to Production pick work
   3. a shop floor operator starts production order
   4. on the last operation, a machine operator uses the mobile device to report the production order as finished (RAF)
4. The system identifies the cross-docking event for the two linked orders (as per setup) and does the following:
   1. automatically releases to warehouse the associated sales order to create shipment
   2. automatically creates a cross docking work that instructs to pick the finished goods from the output location and move them to the outbound location assigned to the sales order by the cross-docking location directives.
   3. prompts a machine operator to complete the cross-docking work right after the production order RAF&#39;ing
5. Upon completion of the cross docking work and loading quantities onto the vehicle, an outbound warehouse planner confirms sales shipment

## Example scenario

For this scenario, you must have demo data installed, and you must use the **USMF** demo data company.

## Set up cross docking with the auto-release shipment

### Cross dock template

1. Go to **Warehouse Management** &gt; **Setup** &gt; **Work** &gt; **Cross docking templates**
2. Click **New**
3. In the **Sequence number** field, enter 1
4. In the **Cross docking template ID** field, type a name, for example &#39;XDock\_RAF&#39;
5. In the **Demand release policy** field, select &#39;At supply receipt&#39;
6. In the **Warehouse** field, enter the warehouse number where you want to set up cross docking process. For this example, select &#39;51&#39;.

  > [!Note] 
   > As soon as you select &#39;At supply receipt&#39; as a demand release policy for the template, all other fields on the form become disabled. Likewise, you cannot define any supply sources. This is because the Cross docking with the automatic shipment release feature only supports production orders as supply source and requires marking to exist between sales and production orders. The fields on the **Planning** tab and **Supply sources** tab are open for edit if you select ´Before supply receipt` as a demand release policy. Learn more about the Advanced cross-docking feature [insert link].

### Work classes

1. Go to **Warehouse Management** &gt; **Setup** &gt; **Work** &gt; **Work classes**
2. Click **New**.
3. In the **Work class ID** field, type a name, for example &#39;CrossDock&#39;.
4. In the **Work order type** field, select &#39;Cross docking&#39;.

    You can limit the types of locations to which you want to put the cross-docked finished goods by specifying one or more valid location types.

### Work templates

1. Go to **Warehouse Management** &gt; **Setup** &gt; **Work** &gt; **Work templates**
2. In the **Work order type** field, select &#39;Cross docking&#39;.
3. Click **New**
4. In the **Sequence number** field, enter 1.
5. In the **Work template** field, type a name, for example &#39;CrossDock\_51&#39;
6. Click **Save**.
7. In the **Work Template Details** tab **,** click **New**.
8. For the new line, in the **Work type** field, select &#39;Pick&#39;. In the **Work class ID,** select &#39;CrossDock&#39;.
9. Click **New.**
10. For the new line, in the **Work type** field, select &#39;Put&#39;. In the **Work class ID,** select &#39;CrossDock&#39;.

### Location directives

Similarly to a standard put-away process of finished goods, which requires a &#39;Put&#39; location directive to guide movement of picked production quantities to a regular storage space, you must set up a cross-docking &#39;Put&#39; location directive to instruct the work to place the finished quantity to a designated  outbound location that services shipment of the associated sales order.

As is the case for the regular finished goods put-away, it is not necessary to create a location directive for pick work action because the output location is given and is expected to be set up as default &#39;Output location&#39; on one of the resource-related records (i.e. resource, resource group relation, or resource group) or as a &#39;Default production finished goods location&#39; for a warehouse.

1. Go to **Warehouse Management** &gt; **Setup** &gt; **Location directives**
2. In the **Work order type** field, select &#39;Cross docking&#39;
3. Click **New**
4. In the **Sequence number** field, enter 1
5. In the **Name** field, type a name, for example &#39;Baydoor&#39;
6. In the **Work type** field, select &#39;Put&#39;
7. In the **Site** and **Warehouse** fields, select 5 and 51 respectively
8. In the **Lines** tab, click **New**.
9. In the **To quantity** field, enter the maximum quantity of the range, for example &#39;1000000&#39;.
10. Click **Save**.
11. In the **Location directives actions** tab **,** click **New.**
12. In the **Name** field, type a name, for example &#39;Baydoor&#39;.
13. Click **Save**.
     
     Use the standard query facility to limit put locations to one or more specific locations:
14. Click **Edit query** and select &#39;51&#39; as criteria for the **Warehouse** field on the **Locations** table.

## Cross dock finished goods to the outbound location

To cross dock finished goods quantity to the outbound location of the associated sales order, follow these steps:

1. Go to **Sales and marketing** &gt; **Sales orders** &gt; **All sales orders**
2. Click **New**.
3. For the sales order header, select customer account **US-001** and a warehouse that is set up to use Cross docking with shipment auto-release.
4. Add a new line for a finished product, enter quantity 10.
5. From the sales order lines action bar, click **Product and supply** &gt; **Production order**.
6. Review the default details on the Create production order form and click **Create**. A new production order is created and linked (reserved and marked) to the sales order.
7. (optional) Change the value in the **Quantity** field to be higher than the one required to fulfil the sales order. When the production quantity is reported as finished, the system will create a cross docking work for the marked quantity and put-away work the remaining quantity, as per regular finished goods put away handling procedure.

   As mentioned earlier, marking between the sales and production orders must exist for the cross docking to work. Marking can be created in multiple ways:
   - Automatically by the system, when:
     - production order is created manually directly from the sales order line (see step 6 above)
     - planned production orders are firmed, with the value in the **Update marking** field set to &#39;Standard&#39;.
   - Manually by the user by opening the Marking form from the demand order line.

   Be aware that the second option is not available for items that are set to use Standard and Weighted average as inventory models.

8. In the **Production order** form, on the Action Pane, on the **Production order** tab, in the **Process** group, click **Estimate** , and then click **OK**. The order is now estimated, and raw material quantity is reserved for the production.
9. On the Action Pane, on the **Production order** tab, in the **Process** group, click **Release,** and then click **OK**. Warehouse pick work for the raw materials is now created.
10. Open and review the work. On the Action Pane, on the **Warehouse** tab, in the **General** group, click **Work details**. Note the work ID.
11. Open and log in to the Warehouse Mobile App to execute work in warehouse 51
12. Navigate to **Production** &gt; **Production pick** menu.
13. Enter the work ID to start and complete the raw material picking. Once the work is registered as finished, quantity of raw materials is available in the production input location, &#39;005&#39; in USMF demo data, for the production order execution to start.
14. In the **Production order** form, on the Action Pane, on the **Production order** tab, in the **Process** group, click **Start** , and then click **OK**.
15. In the Warehouse Mobile App, navigate to **Production** &gt; **RAF and put away** menu
16. In the **Prod ID** field, enter the production order number and other mandatory details, and click **OK.**

Observe that the system now:

1. triggers the release to warehouse of the linked sales order
2. based on this release, creates a shipment and a cross docking work that instructs the warehouse operator to pick the quantities required to fulfil the sales order line and put them to the outbound location specified in the cross-docking location directive
3. (if the production order quantity is higher than the one required by the sales order), creates a regular put-away work that instructs the warehouse operator to pick the finished goods quantities remaining after cross-docking and move them into the regular storage as per location directive.
