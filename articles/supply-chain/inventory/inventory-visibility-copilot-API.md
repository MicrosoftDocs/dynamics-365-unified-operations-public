
## Prerequisites

To use the product search service, your system must meet the following requirements:

- You must be running Inventory Visibility version 1.2.2.54 or newer.

## Overview

In the fast-paced world of business, efficient inventory management is the linchpin of success. Inventory Visibility Copilot emerges as the definitive solution to empower organizations across various industries in conquering the complex terrain of inventory management by using natural language. 

Inventory Visibility Copilot introduces an API-driven solution that simplifies and revolutionizes the management of your inventory. 

## IV Copilot API

~~~ Txt

Path:
/Copilot/nl/iv/{environmentId}/query
Method:
    Post
Headers:
    Api-Version="1.0"
Authorization="Bearer $access_token"
x-ms-client-session-id={ your session id }       // New seesionId will clear chat history. 
ContentType:
    application/json
Body:
    {
        "Text" : { Your text input }
    }
~~~

Sample Body

~~~ TXT
   {
        "Text" : "what's the inventory of product D0001 in organization usmf, site 1, location 11"
   }
~~~
