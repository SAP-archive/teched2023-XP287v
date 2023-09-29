# Exercise 4 - Create scripts to trigger landscape management tasks

In this exercise, you will use the REST APIs of SAP Landscape Management Cloud for retrieving all managed SAP systems. You will generate an API key for your tenant and make use of the credentials inside a Python script deployed in SAP BTP, Cloud Foundry runtime. 

> ℹ INFORMATION: This exercise is based on the sample [LaMa-Cloud_REST_API](https://github.com/SAP-samples/landscape-management-sample-scripts/tree/main/LaMa%20-Cloud_REST_API) and the blog post [SAP Landscape Management Cloud (LaMa Cloud) REST API Sample](https://blogs.sap.com/2023/06/21/sap-landscape-management-cloud-lama-cloud-rest-api-sample/).

## Exercise 4.1 Create an API Key for your SAP Landscape Management Cloud tenant

After completing these steps, you have all details required to communicate with your SAP Landscape Management Cloud tenant via API.

1. Open your trial tenant of SAP Landscape Management Cloud.
2. In the left navigation, select `Configuration > API Management`. 
3. Select `Create`. 
4. Provide an "API Key Name" e.g. "techEdLaMa".
5. Check both checkboxes for the "API Scopes".
6. In this example we will not use the X.509 certificate so deselect it.
7. At the bottom right, select `Create`.
8. Copy the generated JSON to a text file on your computer as you will need it later on and it won't show up again. 

The JSON looks similar to 

```JSON
{
	"url": "https://api.lama.cloud.sap/v1",
	"tokenUrl": "https://<yourSubdomain>.authentication.eu10.hana.ondemand.com/oauth/token",
	"clientId": "sb-xsuaa-9f3dbb85-1234-45676-834a-2f2ebe2c7ca7!b235026|lmc-eu10-api!b1234",
	"clientSecret": "<loremIpsum>-9271-44f5-834a-2f2ebe2c7ca7$iudzM_WM5qdYTDRYY9X1LN5bJk8rP3067Y="
}
```

## Exercise 4.2 Review REST API endpoints of SAP Landscape Management Cloud

After completing these steps, you will be familiar with the REST API endpoints provided by SAP Landscape Management Cloud.

1. Visit the [SAP Business Accelerator Hub](https://api.sap.com/api/SAPLMC/overview).
2. Select `API Reference`.
3. Familiarize yourself with the "GET /systems" endpoint.

## Exercise 4.3 Fork or download Python sample and apply your changes

After completing these steps, you will have created a test application that is making use of the REST API of SAP Landscape Management Cloud.

1. Open [this folder inside the SAP-samples repository](https://github.com/SAP-samples/landscape-management-sample-scripts/tree/65574abc0ec34a8c6073b275af2a351430d8205b/LaMa%20-Cloud_REST_API). This contains the source code for the small application you are going to deploy.
2. Read about the containing files via the [Description](https://github.com/SAP-samples/landscape-management-sample-scripts/tree/65574abc0ec34a8c6073b275af2a351430d8205b/LaMa%20-Cloud_REST_API#description) section.
3. If you are familiar with GitHub, visit the parent repository [landscape-management-sample-scripts](https://github.com/SAP-samples/landscape-management-sample-scripts/tree/main) and fork it to your local machine. 
Alternatively, visit the parent repository [landscape-management-sample-scripts](https://github.com/SAP-samples/landscape-management-sample-scripts/tree/main) and select the green button `Code > Download ZIP` at the top right to retrieve all files of the samples.
4. Unpack the ZIP archive and browse into the folder "LaMa -Cloud_REST_API > samples".
5. Open the file "server.py"
6. Copy and paste the API credentials of your SAP Landscape Management Cloud tenant into the respective lines 10-13 so that the code looks similar to this:

```python
# OAuth 2 client configuration
client_id = "sb-xsuaa-9f3dbb85-1234-45676-834a-2f2ebe2c7ca7!b235026|lmc-eu10-api!b1234"
client_secret = "<LoremIpsum>-9271-44f5-834a-2f2ebe2c7ca7$iudzM_WM5qdYTDRYY9X1LN5bJk8rP3067Y="
token_url = 'https://<yourSubdomain>.authentication.eu10.hana.ondemand.com/oauth/token'
```

> ℹ INFORMATION: The variable "api_url" is the same for every tenant of SAP Landscape Management Cloud. Hence, there is no need to modify it.


7. Save the file.
8. Go back to the "samples" folder in your operating system's file explorer, select all containing files, and create a ZIP archive. The zip file needs to be created such that the "server.py" is at the top level.
   

## Exercise 4.4 Push the application to the SAP BTP, Cloud Foundry runtime in your trial account

After this exercise, you will have deployed the Python app to the space inside your SAP BTP, Cloud Foundry runtime which is available in the SAP BTP trial account.

1. Open your [SAP BTP Trial account](https://account.hanatrial.ondemand.com/trial/#/home/trial).
2. Select `Go To Your Trial Account`. 
3. Select the subaccount `trial`. 
4. In the section "Cloud Foundry Environment", you can see that there is one space created called "dev". Select this line in the table to open it.
5. Select `Deploy Application`.
6. For the "File location", select `Browse...` and navigate to your ZIP archive created in exercise 4.3.
7. For the "Manifest Location", select `Browse...` and navigate to the file "manifest.yml" in the same folder as the sample. 
8. Select `Deploy`. 

After the deployment is finished, you need to create an external route so that you can try the app.

9. In the left navigation, select `Routes`.
10. Select `New Route`.
11. As "Domain", select `cfapps.ap21.hana.ondemand.com`.
12. Pick any host name, e.g. `myapp-<yourname>` and keep the "Path" field empty.
13. Select `Save`. 
14. At the "Actions" column, select `Map Route`.
15. In the drop-down list, select your app and select `Save`. 

## Exercise 4.5 Try it out

After following these steps, you can fetch a list of managed SAP systems in a browser window via the REST API endpoints of SAP Landscape Management Cloud.

1. Try out the externally exposed app. Replace the placeholder <HostName> with the host name you picked in Exercise 4.4 (e.g. “myapp-<yourname>”) in following url: [https://<HostName>.cfapps.ap21.hana.ondemand.com](https://<HostName>.cfapps.ap21.hana.ondemand.com). When you then click on the url you should see “Hello, World!”
2. Try fetching all managed systems by opening [https://<HostName>.cfapps.ap21.hana.ondemand.com/api/v1/systems](https://<HostName>.cfapps.ap21.hana.ondemand.com/api/v1/systems).

This will list the GET call to your tenant of SAP Landscape Management Cloud.

# Outlook

This exercise shows how to make use of the REST API endpoints provided by SAP Landscape Management Cloud. Getting a list of managed systems is only the beginning of a useful script. With this list of systems, you can build a logic that picks a particular system id (e.g. "370c5e1d-763e-4f06-8239-df23a78ef691") and afterwards generates a POST request against the `/activities` endpoint for stopping the system with the body
```JSON
{
   "requestType": "StopSystemRequest",
   "systemId": "370c5e1d-763e-4f06-8239-df23a78ef691",
   "executeGraceful": true
}
```

This might be useful if a maintenance window is planned for the system and SAP Landscape Management Cloud should stop it. After the maintenance window, the system can  be started again via API with “StartSystemRequest”.


## Summary

🎉 Congratulations! You've used the REST API endpoints of SAP Landscape Management Cloud!

Continue to - [Exercise 5 -  Outlook: Event-driven infrastructure automation](../ex5/README.md)
