---
# required metadata

title: View product search publishing status in back-office (HQ)
description: This article describes about an ability to view product search publishing status in back-office (HQ)
author: ashishmsft
ms.date: 10/03/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2023-01-30
---

# View product search publishing status in back-office (HQ)

In this article, you can learn how to view the publishing status for product search in the back-office. Starting 10.0.32, you can enable this feature 'Search publishing sessions monitoring' from feature management and this will enable "Session publishing sessions" form that shows the status of the product/customer Commerce publishing sessions to Azure Search.

With this feature, we are introducting an ability for back-office users to view product search publishing status in back office, that means whenever you are publishing product information by channel, you would be able to see how many products were published, how many catalogs were published, how many products failed. Total product count is for simple and product masters, it is excluding excluding variants. And publishing status will be one of the following - 

|Publishing status |Description |
--- | --- |
|Queued|Waiting for publisher to start publishing|
|In-progress|Publishing is in-progress|
|Completed|Publishing was successfully completed|
|Failed|There was an error in publishing, system will re-try automatically|
|Timed out|Due to some reason, bad query plan or unavailability of required resources or network latency issue it couldn't complete the publishing in appropriate time|


It's gonna be either in the queued state or it's gonna be in progress state, which means the publishing is happening the publishing. So what status is this is showing and always I'll tell you is like these are gonna be the change. So change when I mean is like you have completed the CDX jobs 10401150 and 70.
Post the conclusion of those publishing jobs gets skewed from a CSU to get published to the Azure search index, right? And that has been sort of behind the scene.
Ohh activity which has been lacking visibility and this is our attempt to bring the visibility to it and post the CDL jobs. I've concluded the publishing jobs get queued and as soon as the like algorithm picks up which is the next job to be pushed it will start in progress and there are two three possibilities to it. Either it can get failed, it can get timed out or it can get successfully completed. Now when it gets.
So either it get failed, so today it's gonna show you failed. So at least you are aware of it like last successful publish was maybe say yesterday, but today's changes have been failing for whatever reason. So you are aware of it as like there is some issue with the publishing and our support team can also look into it as such. But you are not into the limbo of like hey, why are they not doing it? So this is our attempt to kind of bring that visibility in it to you the timeout capability. Ohh sorry timeout status is generally because of the fact that the resources were not available.


But those are gonna be reattempted and those would result into the following row. You would see in the publishing statuses to show you completed or failed as well. Now what does it doesn't do today.

Is like it would not give you the exact mirror view of the products in the search index because that's the ideal state we would like us to be. Meaning it's like our by channel. I have a sorted 100 products.

If it is showing me that 80 products have successfully been published but 20 have not been published, uh, which 20? Did not make it? We want to give you that visibility and we are trying to see what is the most voting can say effective manner to kind of produce that result to you. But very soon I mean that is something we are thinking on those lines to bring that. But today it is just gonna be the count provide as such. But then if you may remember in the last webinar I kind of showcased is something called as a merchandising configuration validator.
That's gonna actually help you of these two things are gonna actually help in conjunction. Say something is failing here while we are not able to show you all the set of the failure reasons which would be our aim in the future to kind of bring more, add more color to the failed. Why did it fails as such. But for now you can actually in parallel or complement it with the merchandising configuration validator results where it would kind of a showcase to you what product configurations would have been required.
For the publisher to kind of have pushed these 50 products successfully by the channel.
Lastly, today by catalog we are not able to show the like ideally on a catalog that's itself. When you do the publish or sorry, validate catalog and then you do publish catalog. We would also like to show you just like on the channel, we would also like to show you on the catalog as well how many products were successfully published and when was it successfully published all the way to ACS, meaning to say Azure search index rather than just showing that yes it has been published to the channel DB. So that is there and these changes are coming to you.

By channel database ID, which operating unit number is is that and what is the status of it and when was it queued? When was it started and when it got completed. So you would actually see how much time it is taking for the size of the products you have by channel and number of catalogs. You have a number of locales you have and all of that would kind of give you some deterministic way to have to know how much time it is actually taking for you to.
