+++
title = "Part 5: Alerting"
chapter = false
weight = 500
+++

In this module, we'll set up alerts in Lumigo.

## Setting up alerts

* Go to the [Alerts](https://platform.lumigo.io/config/issues) page, you can see that Lumigo has configured a couple of default alerts.

![Default Alerts](/images/mod05-lumigo-default-alerts-new.png)

By enabling `auto-trace` on our functions, they have been configured with these default alerts.

![Default Alert Functions](/images/mod05-lumigo-default-alert-functions.png)

By default, they're configured to send you at most one alert per an hour. You can dial this up or down (up to as frequent as to alert you on `Every Event`).

* Click on each of the alerts and change the `Alert Frequency` in the dialogue to `Every Event`. Don't forget to click `Save Alert` when you're done.

![Alert Frequency](/images/mod05-lumigo-alert-frequency.png)

* Let's add another alert, click the `Add Alert` button on the top right. In the new dialogue, choose `Alert Type` as `Error Ratio` and set the percentage to 5%.

![New Alert](/images/mod05-lumigo-new-alert.png)

Select the 5 functions we have.

![New Alert Functions](/images/mod05-lumigo-new-alert-functions.png)

Finally, choose how we want to be notified. If you follow the `here` link below...

![Alert Channel](/images/mod05-lumigo-new-alert-here.png)

You will arrive at the [Integrations](https://platform.lumigo.io/integrations) page where you can integrate with other vendor software you might be using already.

![Alert Channel](/images/mod05-lumigo-integrations.png)

Finally, click `Add Alert` to finish the process.

* Go back to the demo app, request a bunch of unicorns like you did earlier. You should see errors, and sure enough, a short while later you will receive an alert via the medium you configured:

![Notification rules](/images/mod05-lumigo-email-alert.png)