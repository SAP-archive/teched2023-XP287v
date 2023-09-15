# Exercise 3 - Setup alerts for unforseen situations

In this exercise, you will connect SAP Landscape Management Cloud with SAP Alert Notification Service for SAP BTP from within your SAP BTP trial account. Imagine you are a SAP Basis Administrator and you want to automatically get notified in case unforseen problems occur when managing your SAP landscape. In that case, you want to instantly get this information instead of seeing it upon your next logon into SAP Landscape Management Cloud. That's what SAP Alert Notification Service is all about. Its so-called "Actions" can send information if a certain condition has materialized. Here is a list of all channels that can be served by Actions:

![SAP ANS Actions list](./images/03_00_0010.png)

([Source](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/managing-actions?locale=en-US))

Therefore, you will setup an instance of SAP Alert Notification Service, generate credentials, and add them to SAP Landscape Management Cloud. This will allow you to forward the business events for triggering an action.

## Exercise 3.1 Discover business events of SAP Landscape Management Cloud

After completing these steps, you will know about the business events SAP Landscape Management Cloud can emit. Events are standardized messages the help shifting from tightly coupled point-to-point integrations towards loosely coupled event-based integrations supports a reduction in this integration complexity. SAP Landscape Management Cloud can generate events in case activities are executed, finished, or failed when it comes to starting, stoping, and discovering new SAP systems in the connected IaaS accounts. 

Review the available [SAP Landscape Management Cloud operation events](https://api.sap.com/package/SAPLandscapeManagementCloudBusinessEvents/event) in the SAP Business Accelerator Hub before continuing the next exercise steps.

## Exercise 3.2 Create an instance of SAP Alert Notification Service
 
After completing these steps, you will have setup an instance of SAP Alert Notification Service and generated a service key which you will use inside SAP Landscape Management Cloud.

1. Open your [SAP BTP Trial account](https://account.hanatrial.ondemand.com/trial/#/home/trial).
2. Select `Go To Your Trial Account`. 
3. Select the subaccount `trial`. 
4. Select `Services > Service Marketplace`. 
5. Scroll down to the section "Foundation / Cross Services" and select `Alert Notification`.
6. Select `Create` at the top right to open the instance creation wizard.
7. Change the "Runtime Environment" selection to `Other`.
8. Provide an instance name e.g. "ansForLama" and select `Next`.

Now that you've create a service instance, lets continue by generating a service key:
9. Select `Instances and Subscriptions` in the left navigation.
10. In the area "Instances", select the entry for Alert Notification, e.g. `ansforlama`.
11. On the right side, select `create` in the lower section titled "Service Keys".
12. Provide a binding name, e.g. "ansbinding".
13. Select `Create`.

You can now open the credentials in the list below. Opening them will show you a JSON similar to this one:

```JSON
{
    "url": "https://lorem-ipsum.cfapps.us10.hana.ondemand.com",
    "client_id": "sb-abcd4e23-8dbb-08e0070725d8!b1235|ans-xsuaa!b673",
    "client_secret": "something-something-4fdc-a426-a08a8b1128da$feojt1R4zxfjJbyl3osVYN6iYZVYaY-VNRygYMKgxwQ=",
    "oauth_url": "https://subdomain.authentication.us10.hana.ondemand.com/oauth/token?grant_type=client_credentials"
}
```

Select `Download` to keep them for later.

## Exercise 3.3 Enable SAP Landscape Management Cloud to emit events to SAP Alert Notificaiton Service

After completing these steps, SAP Landscape Management Cloud will be able to send events to SAP Alert Notification Service.

https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/integrating-with-cloudevents-publishers?locale=en-US


## Exercise 3.4 Configure actions and conditions for e-mail alerts

At the end of this section, failed activities in SAP Landscape Management Cloud will trigger an email to your inbox via SAP Alert Notification.


https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/configuration-management-using-sap-btp-cockpit?locale=en-US

## Summary

🎉 Congratulations! You've now 

Continue to - [Exercise 4 - Create scripts to trigger landscape management tasks](../ex4/README.md)
