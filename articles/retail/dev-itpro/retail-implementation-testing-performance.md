# Testing and performance 
### User acceptance testing (UAT)

The main goal of acceptance testing is to verify that specific business scenarios function according to expectations. The testing should not only include the customizations, but out-of-the-box Microsoft functionality and non-happy path testing.  The goal is to catch anything that may not function properly before going to the production environment.  

For best results, the users acceptance testing (UAT) environment should be a Tier 2 – 5 environment and not a development environment. 

If a development environment (Tier 1) is used, there are scenarios where a developer using the same environment could cause errors (uncommitted source changes, debugger attached errors, etc.). Also, the  switching between Internet Information Services (IIS) Express and IIS may cause issues. Additionally, because there is no way to know exactly what has happened on a development machine, Microsoft support will be very limited for a Tier 1 environment. 

A production environment could be used for UAT (for example as a go-live dry run). However, the disadvantage is that anything you wanted to do in SQL would have to go through deployment support engineer (DSE) service requests. This may not be efficient. Also, a production environment is not available for a long period of time before the planned go-live date. 

The UAT should be done after deploying officially- built deployable packages and not on Visual Studio built packages. The reason is that it cannot be proven what code changes were included in a manually built package. Only an official build system provides assurance and an audit trail of the exact changes that are in a certain build.  

If you do use POS, make sure that you use the correct user roles. You should test by signing in as both a manager and a lower-privileged cashier. 

### Performance 
#### Channel performance 

In some cases channel performance may not be as good as anticipated. Poor performance is often caused by the following factors (listed in the order from highest impact): 

- Additional custom Retail Server calls. By extending the product with additional Retail Server calls, the performance often is decreased substantially. Not only is there the possibility of additional processing, but the network latency must also be considered. It is recommended to try to avoid any additional Retail Server calls. Often, ExtensionProperties and extending existing CRT handlers or triggers can accomplish the same tasks. 
- Additional Channel Database SQL extensions. Make sure that SQL is efficient and uses proper indexes 
- The same custom or built-in CRT SQL queries are exercised multiple times. If it is too expensive and appropriate, caching could be applied.  

For more details, see the section on [Retail development](../../dev-retail-home-page). 
 
When investigating store performance, follow the ideas on Retail Channel performance investigations.

#### Using telemetry data to find performance issues 
To troubleshoot Retail and Finance and Operations performance (especially slow SQL queries or SQL deadlocks), the LCS environment diagnostics page exposes valuable telemetry data. This data can be used to find potential performance issues in code, configuration, or design. Additional details can be found [here](https://blogs.msdn.microsoft.com/axsa/2018/06/05/how-to-use-environment-monitoring-view-raw-logs/). With this information, you should be able to get an idea why certain batch processes or form loads are slow.   

#### Performance testing 

Testing the performance of a system usually makes most sense for the components where many resources are competed for because they are shared. These resources may be different for various projects, customers or requirements.  

Some of the reasons for bottlenecks may include: 

- Resource intensive calculations in Finance and Operations, such as statement posting, change calculations for channel data sync, warehousing operations with large product assortment, MRP runs, etc. 
- Complex retail business logic for multiple terminals or stores running on a few Retail Servers (either in the cloud or in a scale unit). 
- Integrated third-party systems (integrated either from Finance and Operations or Retail Server). 
- Realtime transaction services frequently called from Retail Server. 

In general, default and non-real time POS operations are not considered a bottleneck as it has its own dedicated resource - the computer it is installed or running on.  Performance issues are typically caused by the business logic or chatty calls to RetailServer. 

Ideally, the performance testing should be done after some initial optimizations according to the information above has already completed. If it does not perform well for a single user or process, it will not perform well concurrently either.  For more information, see Retail Channel Performance investigations. Also, refer to the Finance and Operations documentation, and search for "PerfSdk" or “Trace parser." 

Every project is different so it is not easy to give a general answer for what exact performance tests are needed to be run. For exmample, if the transaction sales line count is low (less than 100,000 per day for all stores) and no custom extension code has been added for statement posting, there should be no need to do a performance test for posting. However, if the sales line count is substantially  higher or major custom changes have been added, it would be a good idea to do so. 

Each environment usually has a different hardware capability. However, performance issues can usually be reproduced similarly on different environments as long as the code and data is similar. We do not reccomend using a production environment for performance testing. A good practice is to use the same data in development, test and production. In that case, the development environment can be used to work on and verify a fix. Many performance-critical code paths are data dependent, the same issues may not be seen on a Contoso sample database. 

When finished with a performance fix, the fix should be verified to improve the issue in a test environment (after a deployment of an officially built package) before the deployable package could be marked a release package in order to be able to “go to production”.
