## Estimated costs

Most companies need to determine the costs of landing imported goods. Using Landed cost, this is possible, the estimates use the shipment auto costs to determine the estimate and different scenarios can be specified to deliver the most accurate estimate. These are stored and can be reviewed/compared to actuals within a report. Furthermore, it is possible to update the Item price.

### Setup for estimate costs

#### Cost templates

Cost templates can be set up to default certain settings that the user getting the estimate cost may not necessarily know. They can be a method of reducing complexity in the estimating process by minimizing the selections that the user needs to specify to get an accurate estimate.

The cost templates form is found by navigating to **Landed cost \> Costing setup \> Cost templates**.

| **Field** | **Description** |
| --- | --- |
| **ID** | Unique identifier for the cost template that will be used. It typically describes the factor or cost multiplier for the cost template |
| **Description** | Description of the cost template. |
| **Mode of delivery** | The mode of delivery used by the identified cost template when calculating the estimated cost of a good. This will assist in determining the auto costs associated to the goods on the cost estimate. |
| **Shipping container type** | The shipping container type associated to the cost template. This will assist in determining which auto costs are associated to the goods during a cost estimate. |
| **Customs broker** | The customs broker (vendor) associated to the cost template. This will assist in determining which auto costs are associated to the cost estimate. |
| **Factor** | The factor is an optional field that allows users to add a certain percentage automatically to the cost estimate of goods. For example, if you would like to add 10% to the calculated cost estimate a factor of 1.10 would be entered in the factor field. |

#### Create estimate costs

These settings along with the defaults from the template will be used to determine the estimated landed costs of goods. The cost estimate form is primarily used when working with standard cost items. By adding in the estimate landed costs to the standard cost of goods in inventory, it will allow for smaller variance transactions when the goods are added to a voyage, as the standard cost will reflect the estimates of such landed costs.

The estimate costs form is found by navigating to **Landed cost \> periodic tasks \> cost estimate.**

#### Parameters tab

| **Field** | **Description** |
| --- | --- |
| **Cost Template** | Select the correct cost template to be used. This selection will be used to locate the correct auto costs to be applied to the Costing |
| **Estimate Date** | This date will be defaulted to &#39;todays&#39; date however this can be updated if required.The date specified will be used to locate the correct Sales Prices, Purchase Prices, Auto Costs and Exchange (where shipping rate is used) |
| **Measurement** | If measurement is applicable such as air freight and the rate changes based on the cube or weight then enter the measurement, if not it is recommended that you select 1 unless you are certain that no apportionment occurs using measurement. |
| **Journey Template** | Select the correct [journey template](#_Toc390850928) to be used. This selection will be used to locate the correct auto costs to be applied to the costing. |
| **From Port** | The port that the item will be shipped from will be populated based on the journey template selected. |
| **To Port** | The port that the item will be shipped to will be populated based on the journey template selected. |
| **Currency** | The currency that the item will be purchased in should be specified here. |
| **Containers** | If multiple containers are normally used then specify the number of containers, Dynamics 365 Finance and Operations, Enterprise Edition will then use costs for multiple containers whilst estimating the costs. |
| **Folios** | If multiple folios are normally used then specify the quantity, this is normally 1. |
| **Site** | Specify the Site. |

#### Items tab

It is possible to select many items to estimate.

| **Field** | **Description** |
| --- | --- |
| **Item Number** | Select the item that you wish to determine the price for. If the item has not yet been created simply create a dummy item, optionally attach to the voyage item cost group, and either leave the price blank or create/change the price |
| **Vendor Account** | Select the vendor that you wish to use for the estimate of this item. Note: If the item selected has a default vendor, this will be populated |
| **Quantity** | Select the quantity that will be purchased |
| **Cost Price** | Dynamics 365 Finance and Operations, Enterprise Edition will find the price using standard Dynamics 365 Finance and Operations, Enterprise Edition pricing rules, override if necessary |
| **Measurement** | If measurement is used specify the measurement against each line |

### Manage estimate costs

When the cost estimate is created, the below information will be displayed at the time of creation. It is also possible to view via the inquiries form for cost estimates by navigating to **Landed cost \> Inquiries \> Cost estimates**. The Cost estimate form shows how the estimated cost was derived and the estimated landed cost for each item based on the parameters outlined on the cost estimate periodic job From the inquiries form, users can additionally modify the estimate costs of the goods by changing the cost price and currency associated to the goods. Users can modify the associated voyage costs at both the voyage and container level as well. When users modify the costs within the inquiries form, they will be asked to recalculate the estimate costs for the items within the cost estimate. Once the cost estimates are to your liking, you can choose to use the estimates to update the cost price of the items within the cost template.

| **Field** | **Description** |
| --- | --- |
| **Cost Estimate Number** | The ID for this cost estimate. |
| **Cost Template** | The template that was used to derive this cost. |
| **Estimate Date** | The date that the exchange rate used, if applicable. |
| **Journey template** | Journey templates are routes that the goods take between two ports. [Journey templates](#_Journey_templates). |
| **Currency** | The currency that the item will be purchased in. |
| **Measurement** | The measurement used to derive the cost. |
| **Estimated Landed Cost** | The total landed cost value in the system currency. |

#### Lines

| **Field** | **Description** |
| --- | --- |
| **Vendor Account** | The vendor account used, if applicable. |
| **Item Number** | The item number is shown here. |
| **Site** | The site is shown here. |
| **Quantity** | The number of items used to determine the cost. |
| **Cost Price** | The cost price (trade agreement) shown in local currency. |
| **Measurement** | The individual measurement is shown here. |
| **Estimated Landed Cost** | The estimated landed cost for the total quantity. |
| **Per Unit** | The estimated landed cost divided by the quantity. |

#### Actions header

| **Button** | **Description** |
| --- | --- |
| **Cost Inquiry** | View all costs for the shipment. Cost can be viewed at the individual item level if required. |
| **Update standard cost** | Once cost estimate has been calculated, the **update item price** button can be selected. This will update the standard cost using the version is defaulted from the shipment parameters. It is possible to override this version.Note: If an item has many item dimensions i.e. Various sizes / colors / configurations and these have not been selected for the estimate, Dynamics 365 Finance and Operations, Enterprise Edition will then create a Pending price for each combination. **IMPORTANT** : The price breakdown is created; this is used to determine the standard cost variance per landed Cost. |
| **Voyage costs** | View/Add voyage costs to all goods within the shipment. |
| **Recalculate** | When voyage costs are updated/added/removed, the **recalculate** button must be selected to update the estimated landed costs. |
| **Lock** | The costing sheet can be locked so that no further changes can be made. |

#### Actions lines

| **Button** | **Description** |
| --- | --- |
| **Add** | Add items to the cost estimate. **Note** : The recalculate button must be selected following update. |
| **Remove** | Remove items from the cost estimate.Note: The recalculate button must be selected following update. |
| **Voyage costs** | View/Add voyage costs to all goods within the item. |

### Item cost price update

**Landed cost \> Periodic task \> Item Cost Price Update**

This routine runs the estimated landed cost price as described above all together. This will be completed for every inventory item that falls within the filter parameters set up within the periodic task.

**Note** : The following information must be populated for this periodic task to run:

- Released Products \> Gross depth
- Released Products \> Gross width
- Released Products \> Gross height
- Released Products \> Default vendor
- Vendor \> From port