+++
title = "4.1 Debugging performance issues"
chapter = false
weight = 410
+++

## Debugging performance issues

* Go to the [Dashboard](https://platform.lumigo.io/dashboard) page, and have a look at the `Service Latency` widget at the bottom right. This shows you the tail latency for services that you are calling from your Lambda functions.

![service latency](/images/mod04-lumigo-service-latency.png)

* By default, this widget is sorted by the *p95 (ms)* column. Somewhere amongst the top, you might see similar to `4fsay0n12a.execute-api.us-east-1.amazonaws.com` up there, by either *p95 (ms)* or *p99 (ms)*.

![slow dependency](/images/mod04-lumigo-slow-dependency.png)

* Click on the p99 latency value (454 in my case)

![click on the p99 value](/images/mod04-lumigo-p99.png)

This takes you to the [Explore](https://platform.lumigo.io/explore) page with a prefilled query that finds the transactions where this service was involved and recorded a latency that's equal to or greater than the latency value you clicked on.

![find slow transactions](/images/mod04-lumigo-p99-transaction.png)

* Click on one of these transaction to see what happened.

![slow transaction](/images/mod04-lumigo-slow-transactions.png)

In this transaction, you can see that we made 3 calls to `4fsay0n12a.execute-api.us-east-1.amazonaws.com`.

* Click on the ***Timeline*** tab and you will see that one of the requests to `4fsay0n12a.execute-api.us-east-1.amazonaws.com` took 4345ms.

![transaction timeline](/images/mod04-lumigo-slow-transaction-timeline.png)

* Click on the slow HTTP request, and see that the response was for `Bucephalus`.

![slow request](/images/mod04-lumigo-slow-request.png)

* Go back to the [Explore](https://platform.lumigo.io/explore) page and find other transactions where `4fsay0n12a.execute-api.us-east-1.amazonaws.com` had been slow. See if you can spot any commonalities to these slow requests.
