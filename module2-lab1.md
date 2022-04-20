# Module 2: Ubiquitous Connectivity Lab 2

### Overview

In this first lab, you will use Anypoint Studio to create a Mule application where there will be one flow for each method of each resource (i.e. GET). Additionally you will use APIKit (as part of your Mule application) to process each REST requests, transform them to messages to be handled and processed by each flow.

The implementation will consist of a few steps

1.  Create a new Mule Project in Anypoint Studio from the Shopify API RAML
2.  Review the Project with the Shopify API Scaffolding in place

Then we will test this new API using the API Console.

**Step 1: Create a new Mule Project from the RAML**

In this step we will create a new Mule application in Anypoint Studio from the Omni Channel API RAML Definition. This will be the implementation of our REST API.

1.  If you are using Remote Desktop look for the Start **Anypoint Studio** from the desktop icon.  
      
    ![](https://user-images.githubusercontent.com/84099162/164308439-799d169f-3a97-4b00-9ca9-34f43906e8d8.png)  
     
2.  When you open the Studio for the first time, you are going to be asked for the workspace where the projects are going to be saved. Select the one that comes by default.  
      
    ![](https://lh6.googleusercontent.com/BKO949A7GPjAacivwOlGCipl1RIpgKFJHvjQBIC7ZqLTEoif1XV0NVOroYh3g99nh83Kwz5zyBhdZxlemuotbSv99aI6yM5jkrvUApB9g628IEl_gpD1qq34nFb0MIdFoXckn59CV77b)  
      
    3\. You are presented with the Anypoint Studio Welcome Screen.  
      
    ![](https://lh5.googleusercontent.com/B7HsSedQYkxW1f1VpmrSgWbDsTG6dVhU4XbhLkdNjM4M_nSbqpGZo02Yp_ikF6OZDGVbBAiPKJnmtgBdlmaqXTiNyuVHrgWr9C5H6d0yyS5LlljY-l3E1Mvb47MsI4TNfWOqBybK8sqh)  
      
    4\. Scroll to the bottom if you want to know more on Studio. After that, press **Continue to Studio**.  
    5\. In the Workspace Launcher, use the default workspace directory location.  
    6\. From Anypoint Studio’s menu, select **File > New > Mule Project** to create a New Mule project. A Window will pop-up to define the details of this new application.  
      
    ![](https://user-images.githubusercontent.com/84099162/164308758-5f573e54-48e5-4368-8fe2-3bd8678a21e4.png)  
    7.  Give the project the name **shopify-exp-api-v1**  
    8. Select the **Mule Server 4.4.0 EE** (or latest version if present).  
    9.  Under **Import a Published API** we are going to import the RAML Spec from Exchange. Click on **green +** this will present two options from Exchange or from Maven  
    10\. Select from **Exchange.**  
      
    ![](https://user-images.githubusercontent.com/84099162/164308982-5a8c4b74-c32a-4a55-ae21-91cd561edf4b.png)  
      
    11\. Once you clicked there, you will see a new window. You need to login to the Anypoint Platform. So click on the **Add Account** button.  
      
    ![](https://user-images.githubusercontent.com/84099162/164309151-cdda6097-b62a-4b5d-b1b2-08b4ce3cdec3.png)  
      
    12\. A **Secure Storage** prompt will appear click **Yes** to proceed.  
      
    ![](https://user-images.githubusercontent.com/84099162/164309268-7db882b1-23c2-4c41-a331-dfbe21510ac5.png)  
      
    13\. A new Login window will appear. Insert the credentials that were sent to your email earlier.  
      
    ![](https://user-images.githubusercontent.com/84099162/164309407-4c9fb327-5633-4a1f-956a-fe8c10235c14.png)  
      
    14\. You will be taken to a Password Recovery Setup window. From there add the following details:

*   Question 1: Question: **workshop** Answer: **dtc**
*   Question 2: Question: **connector** Answer: **shopify**  
      
    **![](https://user-images.githubusercontent.com/84099162/164309612-946c9488-9777-432e-b74e-c3d9fd3df0c4.png)**  
     

15\. You will be taken to the Add Dependencies to Project window. From there type **“shopify”** in the search area.

16\. You might see several options, select the **Shopify Experience API** that doesn’t have any names or initials in front of it.

17\. Click the **Add** button.

18\. The **Shopify Experience API** should be on the right pane of **Selected modules.** Make sure that is the case before proceeding.

19\. Click **Finish**.

![](https://user-images.githubusercontent.com/84099162/164309827-d5abd6fd-6aa4-426c-8e49-a63e76f9bfd3.png)

20\. You should be back at the **Project Settings** Window. Click **Finish**.

![](https://user-images.githubusercontent.com/84099162/164309948-f9e87534-2c64-40a3-a1c5-fc8d4143837a.png)

Done! Now let’s explore what was automatically generated for our project.  
  
![](https://lh3.googleusercontent.com/d8OyKhMVEGD1lRyMveLXgy2wHvE7JWh0TNSSfhc8FLcApmIwrBzY9GGoGx5kQHBDBOu2ys9A6ESwKjwtTNLpMY2nHrDimiFXjlOq0VpVCcAwrwTJUygBR1LKCx_X-ayG1Ng0E8qAlAh5)

If you click your mouse cursor to the middle pane under the tab called **shopify-exp-api,** you will see our first **“flow”** called **shopify-exp-api-main.** When you scroll your mouse down you will start seeing other flows (e.g. **shopify-exp-api-console**, and so on).

All the flows are defined by your API Design in the RAML file and have created a scaffolding for the Shopify API project. Typically, there will be flows that look like this **get:\\resource**, **post:\\resource**, **put:\\resource**, etc. Note that the name of the flow is very important for the **APIkit router** to be able to route the request to the appropriate flow - you don’t want to change these

![](https://user-images.githubusercontent.com/84099162/164310236-f84c1787-c27c-498c-bafa-5bb641e7539b.png)

**Step 2: Review Scaffolded Flows in the Project**

When APIkit detects example data in the response of a method in the RAML it inserts a **Dataweave Transform Message** into the flow which returns the static response specified by the example data reference.

The static response returned by the auto-generated **Dataweave Transform Message** allows you to test the API as a stub immediately after generation. The placeholder Transform Message will have sample payload outputs like the one you supplied for your version of the Shopify API in Module 1 Lab 2. Obviously these flows can be enhanced to evolve them into full API implementation as we will see in the next lab.  
  
![](https://user-images.githubusercontent.com/84099162/164310414-1dc89b36-aaac-4fdf-8b75-3dd21bad4826.png)  
  
Let’s review a few of the flows in our Mule project.

1. **shopify-exp-api-main**

This is the main flow. It exposes an HTTP service and processes the requests using the [APIKit Router](https://docs.mulesoft.com/apikit/4.x/).

The HTTP request will be converted to a mule message, and redirected to the requested flow by the APIKit router.

By selecting the http listener one can take a look at the HTTP configuration, there you will see the Protocol, Host and Port attributes, all that information means that the listener is in fact listening for requests on [http://localhost:8081/api](http://localhost:8081/api).  
  
Inside the api-main flow also an [Error-Handling](https://docs.mulesoft.com/mule-runtime/3.9/error-handling) block is included. In this block multiple **On Error Propagate** definitions are autogenerated for common API error responses such as **METHOD\_NOT\_ALLOWED**, **BAD\_REQUEST** etc.

![](https://user-images.githubusercontent.com/84099162/164310672-73cf9972-3a69-48dc-9a81-5b8acb4ce348.png)

2. **shopify-exp-api-console**  
The console flow is not mandatory. It provides an auto generated interactive HTML console for interacting with your api for testing etc. It is auto generated from your RAMl/api spec. Where as to test an API you will be able to test from the similar UI as when where Mocking Services previously in [Module 1](/module1-lab2.md).   
  
![](https://user-images.githubusercontent.com/84099162/164310914-a0743dfc-1302-41cb-a09f-7fbabe72451b.png)

3. **patch:\\order:application\\json:shopify-exp-api-config**  
Is our first flow that represents a resource endpoint. This flow is the framework for the PATCH operator in our order resource of our Shopify API. Patch command will add new consumer orders in NTO’s Shopify and can update existing orders from the same call.

![](https://user-images.githubusercontent.com/84099162/164311157-27733f57-5814-4e91-bfb9-5818794b7255.png)

Let’s review a few of the flows in our Mule project.

4. **get\\inventory:shopify-exp-api-config**  
This flow will be the end point to allow the full list retrieval of items and inventory within NTO’s Shopify application.

5. **get\\order:shopify-exp-api-config**  
This flow will get the all consumer orders that reside in NTO’s Shopify site. **This will be the flow we will be working on in our next lab, Lab 2.** 

6. **get\\order\\(id):shopify-exp-api-config**  
This flow is getting an instance or a single order by ID.

![](https://user-images.githubusercontent.com/84099162/164311321-af9b4d6f-897e-4e61-a736-a79ae8050abb.png)

Let’s review a few of the flows in our Mule project.

7. **get\\products:shopify-exp-api-config**  
This flow will retrieve full list retrieval of products and product data within NTO’s Shopify Site.  
 

8. **get\\products\\(id):shopify-exp-api-config**  
This flow will get product information from a single product.  
 

9. **post:\\inventory\\(location)\\(id)\\(quantity):shopify-exp-api-config**

This flow is will allow to update inventory levels within NTO’s Shopify Site while passing three needed attributes (Product ID, location ID, Updated Quantity). This way of executing the end point offers a lightweight POST command that doesn’t require a BODY in the POST request.

![](https://user-images.githubusercontent.com/84099162/164311448-f369c983-f416-4204-a36e-221c3c6796c4.png)  
  
10. **post\\order:shopify-exp-api-config**

Lastly, we have a POST orders to allow for consumer orders that were not created in Shopify to be in the Shopify order details as away of allowing for consistent consumer experience across channels.

Now that we have familiarized ourselves with the scaffolding of our Shopify API we can now proceed to building the connectivity to the NTO Shopify Site.

![](https://user-images.githubusercontent.com/84099162/164311570-57ed2e65-821e-4494-8b9e-7067a21c1f85.png)

### [\--> Proceed Lab 2](/module2-lab2.md)
