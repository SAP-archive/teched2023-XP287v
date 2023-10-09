# Exercise 5 - Outlook: Event-driven infrastructure automation

This is not an exercise as part of the SAP TechEd tutorial, as there is no plan in the SAP BTP trial for [SAP Event Mesh](https://discovery-center.cloud.sap/serviceCatalog/event-mesh?region=all). Nevertheless, it should demonstrate to you the potential of the business events that can be emitted by SAP Landscape Management Cloud. You got to know these events in [Exercise 3 - Setup alerts for unforeseen situations](../ex3/README.md) when you made use of SAP Alert Notification service. 

The power of event-driven infrastructure automation can be used when you want to react to changes in your system landscape in a standardized fashion. This allows you to quickly solve standard problems that might occur or to automate flows across different cloud services in a losely coupled fashion.

## Exercise 5.1 Event-driven infrastructure automation in case of problems

When using SAP Landscape Management Cloud as part of your system landscape tooling, you might want to react if an activity didn't succeed, thus has failed. A potential reaction could be to trigger the activity again and if it fails again, notify the system administrators. It's impossible to foresee when any activity is failing. With only having API endpoints available, it would be necessary to poll the `/activities` endpoint on a regular basis and validate all their status.

By using event-drivin infrastructure automation, you configure event routing inside SAP Landscape Management Cloud to forward all events to an event broker. This broker might filter for the "Activity.STARTSERVICE.v1" and "Activity.STOPSERVICE.v1" events as described in [SAP Business Accelerator Hub](https://api.sap.com/event/OperationEvents/resource) and once the "status" payload is set to "FAILED", the event broker forwards the payload to a pre-defined script. This script can instantly use the "activityId" within the payload and talk to the `/activities/{activityId}` REST API endpoint for retrieving all details. Afterwards, a new POST request could be created for re-trying. 

## Exercise 5.2 Event-driven infrastructure automation for a lose coupling of tooling

In reality, SAP Landscape Management Cloud is not the only tool used for infrastructure and system management. Many different tools with different purposes are combined. Typically, processes across these tools are modeled and have to be executed one step after another. This can be realized in an event-driven fashion.

Imagine you schedule a maintenance weekend for a particular system. This has to be documented typically in a ticketing system. Once the maintenance window starts, this ticketing system could create a POST request for stopping the desired systems. Once this task has finished, which can easily take an hour, an event is sent out and the next step is triggered. This could be a de-registration of the stopped system from monitoring tools to avoid unnecessary system alerts. 

This speeds up the process execution as no API polling in a given time frame has to be defined.

## Exercise 5.3 Trying it out in case you have access to SAP Event Mesh

If you have access to an instance of SAP Event Mesh, you can follow this [blog post](https://blogs.sap.com/2023/07/10/sap-landscape-management-cloud-lama-cloud-event-routing-and-posting-to-ms-teams/) for trying it out yourself. In case you noticed within the introduction to [Exercise 3 - Setup alerts for unforeseen situations](../ex3/README.md), SAP Alert Notification can send alerts to Microsoft Teams and this blog post describes how you can trigger messages to Microsoft Teams as well. Both routes are a valid option and depending on your use case, might come in handy.

If you only want to trigger alerts to users, going via SAP Alert Notification might be the straight forward path. If you have scripts in place which trigger follow-up actions **and** should send a message to Microsoft Teams, following the instructions of the blog post might make more sense. 


## Summary

🎉 Congratulations! You've understood why SAP Landscape Management Cloud provides event routing capabilities.

Back to the overview - [SID 115558 - SAP System Management with SAP BTP and SAP Landscape Management Cloud](https://github.com/SAP-samples/teched2023-XP287v/tree/main)
