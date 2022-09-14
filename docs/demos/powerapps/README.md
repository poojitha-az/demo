# Podcast Approval application using Microsoft Power Apps

Before getting started, ensure that you have access imported the application into your Power Apps environment. Follow the detailed guidelines [here](https://github.com/user/repo/src/PowerApps/README.md)


# Create a custom connector

[Custom connectors](https://docs.microsoft.com/en-us/connectors/custom-connectors/) are a powerful way to connect to any existing API from within PowerApps. A custom connector is a wrapper around a REST API that allows the Power Platform to communicate with your REST API.

From within Azure API Management, you can easily create such custom connectors. [Follow the detailed guidelines](https://docs.microsoft.com/en-us/azure/api-management/export-api-power-platform) on how to export your API from API Management.

# Connect your Podcast Approval application with your web API

Open your Podcast Approval App within Power Apps:
![editpowerapp](./assets/editpowerapp.jpg)

You will see a lot of error messages within your Power App:
![powerapp](./assets/powerapp.jpg)

To fix these, we will have to add our custom connector to our Power App via the data tab:
![customconnector](./assets/customconnector.jpg)
*Note: Search for the name of your custom connector created via API Management.*
*Note: If you have enabled subscription keys. You can find the subscription key within the Azure Portal in your API Management instance under Subscriptions.*

# Update your Power App

Next, we have to update our Power App via the Power Editor.


## OnStart

Every time someone opens up the Power App, we want to make an API call getting us the information about current requests. For this we have to change our [OnStart behavior](https://docs.microsoft.com/en-us/power-platform/power-fx/reference/object-app) for the Power App. We need to update **'.NETPodcasts'.GetUserSubmittedFeeds()**:
![onstart](./assets/onstart.jpg)

Additional Information:
- **'.NETPodcasts'** is referencing the name of our custom connector
- **GetUserSubmittedFeeds()** is referencing our API's method name


# Refresh Button

We also implemented a refresh button, for this we also have to update **'.NETPodcasts'.GetUserSubmittedFeeds()**:
![refreshbutton](./assets/refreshbutton.jpg)