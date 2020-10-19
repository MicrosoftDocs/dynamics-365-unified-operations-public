# Upgrade and migration

## java.security.cert.certPathValidatorException: Trust anchor for certification path is not found.

**Issue:** On OnPrem environments, self-signed certificates are not trusted on Android 8+ causing this error to occur on the warehouse mobile app.

**Fix:** Use external (public) CA. A fix for this issue has been made available in 1.9.0.0.

## Moving from Basic to Advanced Warehousing.

**Issue:** We are currently running under stock/inventory management and using basic stock functionality. We want to move to advanced warehousing to take advantage of mobile devices / waves / work. We cannot change our products to storage dimension - Site/Warehouse/Location as they have transactions against them. What is the approved process to move from basic to advanced warehousing?

**Fix:** Please find the below links for more information. Which would give more details about the process.

-   <https://cleverax.wordpress.com/2017/12/06/d365fo-enable-warehouse-management-process-for-existing-items-and-warehouses/#:~:text=Navigate%20to:%20Warehouse%20management%20%3E%20Setup,profile%20for%20existing%20inventory%20locations>.

-   <https://cloudblogs.microsoft.com/dynamics365/no-audience/2015/08/17/migration-of-microsoft-dynamics-ax-wms-to-new-r3-warehouse-and-transportation-functionality/>

-   <https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/05/03/wmsiwms2-item-migration/>


