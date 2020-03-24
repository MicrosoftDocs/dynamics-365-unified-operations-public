## Build Odata metadata cache when AOS starts

Starting from Platform update 32 we have introduced the ability to build **Odata metadata cache during AOS startup** as opposed to when the first Odata request occurs which will significantly decrease the response time for the first Odata call after an AOS process restart.

This option is very useful when your business process cannot wait for the Odata metadata cache to be built each time the AOS process restarts


1. Go to **System administration** \> **Setup** \> **System parameters**.
2. On the **General Tab**, click on **Build metadata cache when AOS starts**.
3. Click on **Save**.


> [!NOTE]
> AOS should be up and running and has already served one OData request, the cache is already warmed up, this option will take effect during next restart.
