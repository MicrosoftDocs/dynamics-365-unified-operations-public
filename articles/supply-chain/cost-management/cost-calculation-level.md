# Cost calculation level

The BOM level named "Cost calculation level" excludes production and batch orders from its calculations. The system uses this level when executing Cost calculations in costing versions. The system will use the "Costing level" BOM level in processes such as recalculation and inventory close.
A simple scenario explains the differences in BOM level Cost calculation level and Costing level.

For example, consider three products A, B and C. Product C is the component of product B, and product B is the component of product A.

- The **Costing level** will assign following BOM levels:
  - Product A is 0
  - Product B is 1
  - Product C is 2

- The **Cost calculation level** will assign following BOM levels:
  - Product A is 0
  - Product B is 1
  - Product C is 2

Then, a production order for product C is created and product A is added to the production order BOM.  After the order is estimated, BOM levels are updated as follows. 

- The **Costing level** will assign following BOM levels:
  - Product B is 1
  - Product C is 2
  - Product A is 3

- The **Cost calculation level** will assign following BOM levels:
  - Product A is 0
  - Product B is 1
  - Product C is 2

This ensures that changes done to production order BOM’s doesn’t affect the cost calculations going forward 
