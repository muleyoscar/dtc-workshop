# Module 3:  Apply Policy to Shopify API: Lab 1

### Overview

API management is essential to an API-Led architecture as it provides a governance framework to your APIs in all three layers. For API Management to take place, we need to be able to host our APIs, both new and existing, on an API Gateway that will be used for enforcing policies and collecting data for analytics.

MuleSoft can apply governance directly to a MuleSoft implemented API or through a proxy gateway for these and other external existing APIs.

The APIs we will use are two versions of the Shopify API. You will create a proxy gateway to an already deployed mock implementation in this Lab 1.

In this lab, we will define an API that will act as a proxy for NTO’s Shopify API. The proxy will be deployed to Anypoint Platform’s API Gateway, which is powered by the Mule runtime.

  
Clients will access the API through the API Gateway which will then forward the requests to the actual Omni Channel API Mock Implementation. Having the proxy deployed on the API gateway allows Anypoint Platform to manage, control access and monitor the usage of the API, which we will look at in the succeeding labs.  
  
![](https://lh6.googleusercontent.com/77dmhqs1B1WfBilfs87d2Wnkl-wYDEUh6kui8abfJG2N679Dn3HcUjylmzaU9JXLyrDGV47CDL5bz9Upl2Hpss1MJIYpLQIC5s93Yi6S9ukyQU4QWXSzvs87ckFslhHMVIYtKhS-OWZq)

**Step 1: Go to API Manager**

1\. In Anypoint Platform ([https://anypoint.mulesoft.com](https://anypoint.mulesoft.com/)), click the **API Manager** icon to start creating your API.  
  
![](https://user-images.githubusercontent.com/84099162/164337074-e231b7eb-8154-4b8a-a2b0-6258d96ac807.png)

2\. Select **SANDBOX** as the environment

![](https://user-images.githubusercontent.com/84099162/164337186-7b078ad8-c951-40c6-ae09-95e87fbddf80.png)

  
**Step 2: Configure an API Proxy**

For this lab, we are going to configure the API as a proxy to NTO’s Shopify API Implementation. The API is available as an HTTP Restful API accessible through the base URL [**http://shopify-exp-api-v1.us-e2.cloudhub.io/api.**](http://shopify-exp-api-v1.us-e2.cloudhub.io/)

Let’s take a look to the products resource of this API that returns product information when an HTTP GET is issued.

To see the all the resources of this API, you can view the API definition and Summary in Exchange

![](https://lh5.googleusercontent.com/iBkD1YMC4vC-LH29kyRgr2hCnBQpgGfRmHR8K3BSFviDhSnSo0-85JUCiCLDYU1a3K15P49ieEbarC4VdUDHsBhfHNuNjPee8FpJGXObxx4uAg4yM5y_g7Hf_7FvJd5Gn7KM8bAXl9v_)  
 

To create the proxy we are going to get the API Definition from **Exchange**.

1\. Now let’s configure an API proxy gateway for this API. Navigate to the API Manager page, click on **Manage API** and select **Manage API from Exchange**.

![](https://user-images.githubusercontent.com/84099162/164337319-ae92431d-e348-45a9-9826-ba0a1ce4fd81.png)  
  
Configure the API with the following information:

2\. Under **API name**: Type “**Shopify Experience API”**. Notice when you start to write the name, the field is auto completed:

a. **Asset type**: Select from the drop down list **RAML/OAS.**  
b. **API version**: Select from the drop down list **1.0.0.**  
c. **Asset version**: Select from the drop down list **1.0.1.**  
d. **Managing type**: Select **Endpoint with proxy**.  
e. **Proxy Deployment Target**: Choose **Cloudhub**  
f. **Mule Version**: Check the **Mule 4** option.  
  
![](https://user-images.githubusercontent.com/84099162/164337491-e61d77cf-6b7b-48ea-94fe-dc6ee20697b6.png)

  
Configure the API with the following information:

3\. Type: [**http://shopify-exp-api-v1.us-e2.cloudhub.io/api**](http://shopify-exp-api-v1.us-e2.cloudhub.io/) in the Section labeled **Implementation URI**:   
  
4\. Click **Advanced options** to expand to as follows.

5\. Add **\<first name or initials>-proxy-shopify** in the field, **API Instance label.**  
  
**![](https://user-images.githubusercontent.com/84099162/164337578-8f3277d0-5ebf-4f85-bbbe-09dddfb68e05.png)**

6\. And Click **Save.**  
  
Configure the API with the following information:

7\. Set the field Runtime version to **4.4.0.**

8\. In Proxy application field type:   
**\<first name or initials)-proxy-shopify**

9\. Then click **Deploy**.  
  
![](https://user-images.githubusercontent.com/84099162/164337644-214ac064-e9bc-4df3-bcaa-837535e2f0ca.png)

10. Click on **Click Here** to see the log data and monitor the progress.  
  
![](https://user-images.githubusercontent.com/84099162/164337711-a44bfe97-0467-4500-9904-1fd23410cbd5.png)  
  
11. A new browser tab will open that will show the CloudHub log for this application in **Runtime Manager**.

12\. Wait until you see “**Your application is started** “ and you can close this browser tab and go to back to the previous tab.  
  
![](https://user-images.githubusercontent.com/84099162/164337796-a7fa5dc0-a729-4f5a-92e4-7a248ffce97f.png)

13. Go back to the previous browser tab where you were configuring the API. You should see the green Deploy Successful in the status bar. Click **Close.**  
  
**![](https://user-images.githubusercontent.com/84099162/164337850-642ed467-eff9-4070-9dbe-6112cc0f75ca.png)**

14. Once it is deployed, at the top of the page you will see the status of the API. It should be green with a green dot next to it, as shown below. This indicates that your API was successfully deployed with its corresponding Proxy and is now being managed.  
  
![](https://user-images.githubusercontent.com/84099162/164337926-261f0d2e-2c3b-43c0-a6bc-8dc6337d0f77.png)

  
 

**Step 3: Test the API Proxy**

Your proxy API is now accessible via CloudHub.  
  
1\. At the Proxy URL, Right Click the URL and Select **Open Link in New Tab.** This will open a new Browser Tab.  
  
![](https://user-images.githubusercontent.com/84099162/164337990-e7c03d67-b445-4306-a2c6-a2bb6f522fd9.png)

Your proxy API is now accessible via CloudHub.  
  
2\. You will see a page with a error message stating: **“resource\_not\_found”**  
  
**![](https://user-images.githubusercontent.com/84099162/164338038-5af75ff0-682b-41f7-b056-8f76a12a06d3.png)**

3\. Add **“/order”** to the end of the proxy URL in the Browser and   
  
4. **Refresh** the Page.  
  
![](https://user-images.githubusercontent.com/84099162/164338103-176ab9dd-768b-42d9-943e-f229795271dd.png)  
  
You should see the Shopify GET orders payload response. Good the proxy is working! Now to our next Step.

**Step 4: Apply Policy To API** 

Your proxy API is now accessible via CloudHub.  
  
1\. Toggle to your previous Browser tab that has details on your Shopify API as seen:

2\. Click **Policies** on the left menu pane  
  
![](https://user-images.githubusercontent.com/84099162/164338164-6534a0ad-b3d6-4f46-bdfd-9ff803c8e27e.png)

3\. In the next Screen Click the **Apply New** **Policy** Button.

![](https://user-images.githubusercontent.com/84099162/164338226-ee8454ac-230a-40c3-b317-c2283abdf6c8.png)

You will see a screen showing a list of different Policies. At the top **All Categories** you can filter the Policy listing by categories (e.g. Security, Quality of Service and so on).  
  
Since we are trying to get NTO’s Shopify Order data our requirement is to have some sort of system authentication before giving retrieving that data from Shopify. 

4\. Select **Basic Authentication - Simple**  
  
5\. Choose radio button **1.2.2**  
  
6\. Click **Configure Policy** Button Below.  
  
![](https://user-images.githubusercontent.com/84099162/164338308-c367809b-0ec4-45ce-91a6-03c8e94b0481.png)

7\. In User Name and Password Fields type:  
**”workshop”**  
  
8\. Click the **Apply** Button. 

![](https://user-images.githubusercontent.com/84099162/164338375-127be50a-a42d-47e3-a024-d7872c54265d.png)

9\. You will see that the new Policy, **Basic authentication - Simple** is being enforced for our Shopify API.  
  
![](https://user-images.githubusercontent.com/84099162/164338449-44c8ef35-94ca-4726-aabb-a6625ed82583.png)  
  
  
It may take a several minutes before the policy takes effect, Great time to take a small break and come back.  
 

10\. Toggle back to the Browser Tab you had for proxy URL:  
**\<your first name or initials>-shopify.us-e2.cloudhub.io/order**  
  
11\. Continue to **Refresh** the Browser until you see the following:  
  
12\. Enter **“workshop”** In the Username and Password Fields.

13\. Click **Sign In**  
  
**![](https://user-images.githubusercontent.com/84099162/164338539-306e5887-db86-414b-86cf-85054e9c5af0.png)**

### 14\. You should see the Shopify Order Payload Response.  
  
![](https://user-images.githubusercontent.com/84099162/164338651-89331a4e-a315-481d-aac4-f07ab5d28c7a.png)  
  
We did it! We just created a security policy for our Shopify API!   
  
**Plus, we have completed all Modules and Lab for this DTC Workshop! CONGRATS!!!"**  
  
![](https://lh6.googleusercontent.com/pntjbXLFKBUBujWEwS70GN8FsZkyae1L1-XVU7LlpzB_xmHjBh-O882AfNwXwv_cdAjpptp98M7dNOSNeoRNW5WqgGsc8yiyE6i5v0qfhUVusWrdkGpn0qLS6eU0Bty-sIX-FS1tmhQz)  
  
Summary

In this lab, we completed the following steps:

*   Overview of Anypoint API Manager
*   Configure the API proxy
*   Test the API proxy using Postman

We saw how easy it is to proxy existing APIs and deploy it on a CloudHub-based API Gateway. This provides a **low friction** approach to manage existing APIs across your environment. You are able to leverage a **hybrid** API Gateway service offering which can be on-premise or on the cloud. In this lab, we saw how we can deploy our API Gateway to CloudHub which can significantly **speed up your deployment** without having to manage and maintain infrastructure.

For further reading on deploying an API gateway and proxying your API, please refer to the following documentation:

*   [Proxying Your API](https://docs.mulesoft.com/api-manager/2.x/api-proxy-landing-page)
*   [Deployment Options](https://docs.mulesoft.com/runtime-manager/deployment-strategies)

![](https://user-images.githubusercontent.com/84099162/164338778-13c87e07-ab81-44dc-9e69-fc4b613e4b59.png)
