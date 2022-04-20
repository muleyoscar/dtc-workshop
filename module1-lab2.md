### Module 1: The Modern API - Design: Lab 2 

### **Overview**

In the first lab of this module we learned how to discover the Shopify Experience API published in Anypoint Exchange. But of course, somebody had to design this API in the first place. For the purposes of this exercise, let’s ignore the fact that the Shopify Experience API already exists. Instead, let’s take on the role of the API designer and explore how to design the experience API using a **Design First** approach with MuleSoft’s API-led Connectivity methodology. The goal of our _Design First_ approach is to be able to design APIs that are easy to use for their intended target audience.

Anypoint Platform provides first-class tooling to support the needs of the API Designer. Anypoint Design Center provides a robust RAML editor for designing the specifications of the API and standing up a "mock" service to accelerate development efforts. It is also tightly integrated with Anypoint Exchange to simplify the process of discovering and referencing other API design-oriented assets like common data types, traits, schemas, and data examples.

For the purposes of this workshop we will design new API’s using REST. RESTful API’s are very popular right now and support a variety of patterns that help solve many reliability, scalability and integration challenges you might face. We will use an API-first design approach using the RESTful API Modeling Language (RAML) standard. We will follow REST best practices to promote adoption to your consumers. This lab will also introduce the main concepts of resource oriented design and will show how RAML is used to bring APIs to life. For more information on RAML, please see: [www.raml.org](http://www.raml.org/).

![](https://user-images.githubusercontent.com/84099162/164139877-1fbde779-1dca-4354-b6c3-8d3ee5279d3e.png)

In this lab, we will start designing a new REST API and test it before implementing it. We will use Anypoint Platform’s **Design Center** to design the API. 

We will then use **Anypoint Exchange** to search and find data definitions and examples published across the organization that enable us to standardize on common data elements. 

Lastly, we will utilize the **Mocking Service** to unlock resource dependencies of your API design. This significantly cuts down the time spent building the omni-channel application by turning the RAML design over to the omni-channel developers immediately and adopting a rapid prototyping style. Developers can utilize the mocked up API capabilities to produce a "working" application that calls the Mocking Service.

**Understanding Resource Oriented Design (ROD)**

Designing REST interfaces is a bit of a paradigm change compared to SOAP services. SOAP services design was thinking in actions and methods whereas ROD wants you to think along the lines of your business entities that should be modeled as resources. And resources might be everything from a document, a video, your favorite device or an order process.

**The quintessence on ROD is:**  
1\. [Use standard methods](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (e.g. HTTP GET, PUT, POST, DELETE, HEAD) and notice their specifications - e.g. GET, HEAD, DELETE and PUT are idempotent methods

2\. [Use standard response codes](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) for success and error; use existing patterns e.g. not every successful call should return a 200 OK - often a 201 Created is appropriate after a POST /products or a 202 Accepted when a long running task was started by the server

3\. [Use standard header parameters](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)

4\. Design and craft resources in **your** business language - here is where [RAML](http://raml.org/) comes into play

5\. **Interlink** as many of your resources as you can; e.g. when you return a collection of products, have every product in the result carry its own link so the client can easily access it

**Collection Resources**

Typically resources are designed as either collection or instance resources. Collection resources hold a collection of resources that can be queried, ordered, extended and most importantly linked.

Let’s take a typical example of a product resource. Most likely there are several of them and you want to be able to create new products also.

By designing a **/order** resource a list of products is available. Typically the methods

![](https://lh5.googleusercontent.com/kww254HrO0K8a4nXoIVRysFZTp-Qk0QIMnE4iDU1kR_QuctNAvDw_p6wQMNMf_vcSTw9OsuCJKvak24RO4rlLIzHBdVCvR9VwihSbP1VbvZbKjeRVFN06M4XEl3YHPgHNkVc_YDMdzyi)

*   GET (get the list)
*   PATCH (can both create new order records or modify existing order record to specified target
*   POST (will create order(s) at its intended target)  

**Instance Resources**

Instance resources contain the details of a specific resource, i.e. the instantiation of a resource. For our inventory example that might include a product id and id of the store. Highly valuable are then links to other parameters (e.g. quantity) that might be part of that inventory management process.

Instance resources must be uniquely identify-able and typically look like this: **/inventory/{location\_id}/{product\_id}/{quantity\_value}**. Typically the methods  
![](https://lh3.googleusercontent.com/YCwSW_x4D2NqDaBjn-o3SnX8iNZvu09mcja4ZLliIbsiYCC8SHCy-sSxSTr_xofJzlj4mURgRd2jAC-vo4AGJBVqSFx1ItJGpQ0YhxCgE2uSN0oIYKOy4hp3IQW8D1QsRhGdQkJHgaNv)

*   GET (retrieve an inventory list of products)
*   POST (update inventory data by location and specific product while   
    specifying quantity to update)

are available on the inventory resource.

Now we understand resources let’s explore how we can work with the resources.

### Step 1: Review the E-Commerce Application Requirements

You have a new requirement for a new Shopify application. The NTO business team has the following requirements we are asked to fulfill. It is written in the language of the e-commerce developer and we will derive the RAML specification from that.

**Functionality:**

*   Products:
    *   List all the products available
        *   Name
        *   Description
        *   Product Variants by SKU
        *   Category/Brand
    *   Get information about a specific product by identifier (ID)
*   Orders:
    *   List all consumer orders made in Shopify
        *   Get information of an Order by its Order ID
    *   Create new consumer order from other systems and post to Shopify for status updates via Shopify:
    *   Bulk update and add new orders into Shopify
*   Inventory:
    *   List all product inventory across all NTO store locations
    *   Update a specific product inventory level at certain store location

### Step 2: Create the Shopify Experience API

In this step, you will create an API and design it using the Anypoint Design Center.

You can access Anypoint Design Center from the home page of Anypoint Platform:

![](https://lh3.googleusercontent.com/hBN4M9KRxi6THRda--9L2B6_YIziyLSbU-gEhIblCYf1TNlWdElsYZO7xbzU9WlL3XWCJKxeopCTicIt9pQrzdfFWFsZLkyxFsiybWFPN2xk7X4hLMdOhWjl85hlSs_EqhgJyOyU7Jnt)  

Alternatively you can use the "hamburger menu" from any page within Anypoint Platform portal to navigate to Design Center:

![](https://lh6.googleusercontent.com/JOSRHDlN3Yx80bloxbvgEf2UMfnQxQ7UH_rPVpGrpOUBC-KDZg8it-rkD2vSGMoa5VkbXP259qmYhuhXwLrnh6XeptFSMc0ImmqcCiEYWgjEf9JGpLndmqT5G1csL9XuznzGDQdowwhM)

1.  **Anypoint Design Center** is used to design your API’s. When you arrive at the Design Center landing page you will see a list of API’s that have already been designed by your organization.

![](https://lh4.googleusercontent.com/JdKf3HozfIQwfBI8NEwVhZjGWKXRwAa4oehEzlHZABfvrRdpdb0Ae2Vp23we84ukSMjzGRD3Ywz8_bXAdTLokt5f_yC3RZOzl-aBx3-iJDr_qN3ccYaxpjuosb5BlgBtp5gEuZQGkUNn)

**Anypoint Design Center** is used to design your API’s. When you arrive at the Design Center landing page you will see a list of API’s that have already been designed by your organization.

![](https://lh4.googleusercontent.com/t1OkJ7x4PopDMDXHaxL3ZcM7bk5nE0aEWzEul0pDFcdU2ebOt26j3WR6_Dtck3Aa_L7rlGUcFx0XmbT6BPuSfEFgY6tXQnB2wv7VteF96DStWjSuaDMMembe7UkdG43NZHygnLGHnLBF)

3\. To create a new API, Click on the **Create new** button

![](https://user-images.githubusercontent.com/84099162/164259795-3893ca3f-f64e-4947-a96a-700d4b79cd12.png)

4\. Select “New API Spec”:  
![](https://user-images.githubusercontent.com/84099162/164260092-e8df6fb6-e429-4073-8c9e-053d9835e238.png)

5.  Set the following values in the **Add API** form:  

A. API name: **\<your name or initials> - Shopify Experience API**.  
![](https://lh4.googleusercontent.com/jAT_h7F0YHkPnhA7BEPu1FyZrcg_T89uylUUr6RV5wEc40_ALKt5blNZobbjEB3c6oVg1CrtsjPFAWkn_t2rgdxz8gqhKwoBvxVq4ACrLMf7yGzfDLbTqH-j00Ex_9_xpIujGfJLq9WQ)

B. How do you want to draft the API Spec: Select **Guide me through it** radio button.

C. Select **Create API Spec** button.

![](https://user-images.githubusercontent.com/84099162/164260604-8eeccb0a-c9ec-4242-bdb1-8fe3c546f8ba.png)

6\. After clicking **Create API Spec**. This will create the basic structure of your RAML-based API specification. Note that for full RAML support, you should start with the first option (API Designer), which is the standard RAML-based API Designer.

![](https://lh5.googleusercontent.com/xVTUI_1JXxUdoEHWFtnrKtYLA-izBsvwK7baMQg-guArVKPFN5blmp_t9QLh-qSZphKZOFwdVoOk7AcacjF20S8PA6FAYgO8GRQ5lwcSXU2CVJUZPnrXoG1KsuhT3asH_zkm81EL7zBX)

**Step 3: Create the Orders List Resource**

In order to provide order handling functionality for the e-commerce application, we will design a list resource in our API using RAML.

**Anypoint Design Center** will provide a visual API editor to start with a step-by- step tutorial to guide you through designing your API visually.

1.    Let’s add some general details about the API.

A. Name the API by setting the title to: “**\<your name or initials>- Shopify Experience API”**.  
B. Since this is our first design let’s set API Version to “**1.0”**  
C.Select protocol as “**HTTP”**  
D. Set the media type to “**application/json”**.  
E. Most API specifications will designate an API endpoint Base URI. This tells the API consumer where they will access the API. Set the URI to **“**[**http://localhost:8081/api**”](http://localhost:8081/api)

You should now see the something like  following in your API design:

![](https://user-images.githubusercontent.com/84099162/164261448-1edc032f-92e5-4b93-9446-9c7b516e46b1.png)

**Step 3: Create the Orders List Resource**

2.  Now you need to add a resource. A resource is the definition of an entity that your API will manage. Click the **+** to the right of **Resources**, then choose **Add resource**.

![](https://user-images.githubusercontent.com/84099162/164261713-8c10d004-d5cd-4d7c-9efa-7060e41b2c0f.png)  

3.  To create the order resource for the Shopify API we will need to do the follow:

A. Rename the resource from **/new-resource** to **/order.**   
B. Select the **GET** option and under summary → description, give it a description  
C. Scroll to and select **Responses** tab below. It will have a default **200** Status (which signals successfully operation) preselected and hit **Add**  
D. Notice the generated RAML on the right.

![](https://user-images.githubusercontent.com/84099162/164262153-f936fa84-8d3b-4595-a566-dfed4d0ab754.png)

**Step 4: Create the Order Instance Resource**

In the previous step we created an Order collection resource and GET method to grab all Shopify Orders. But in most cases for NTO, information on a single order will be needed. We need to create a new resource underneath the Order instance and use the GET method.

1\.   So we will do the following:

A. By the **order** resource hover your mouse on the resource and you should see a trash can and “\*\*+**” icon. Under the “**+**” icon,**  
**\*\*Nested resource** call out is visible to indicated we can nest child resource under **order**  

![](https://user-images.githubusercontent.com/84099162/164262671-c61ab3aa-5236-4f31-b301-402f0571ae9a.png)  

B. Click the “+” icon and you will see that another resource, **/order/new-resource** has been added under **order**.

C. Change “\*\*/order/new-resource**” to “**/order/{id}\*\*” in the title pane

D. Scroll to and select **Responses** tab below. It will have a default **200** Status (which signals successfully operation) preselected and hit **Add**

![](https://user-images.githubusercontent.com/84099162/164263784-0afa37a0-a77e-4871-9a1a-db87c9100c3f.png)

2\. Now let’s add a specific body to the 200 response for **order/{id}** instance.

A. Select **Add Body**

![](https://user-images.githubusercontent.com/84099162/164263269-4794bbd1-fce4-40be-a7e6-6838589ab368.png)

B. Keep **application/json** as the Media Type and hover to the arrow icon at the right to expand options.

![](https://user-images.githubusercontent.com/84099162/164264271-d0bb6e76-e050-4f4c-b837-af4260ce745d.png)

C. Once expanded it should look like this:

![](https://user-images.githubusercontent.com/84099162/164264427-17f4df98-ccb4-4016-8394-d400396c6bb3.png)  
3\. Click **Edit**

4.  Now let’s copy and paste the following code into the body:

> {
> 
>      "id": 413413890297800,
> 
>      "confirmed": true,
> 
>      "fulfilled": false,
> 
>      "created": "2021-12-09T09:05:34-05:00",
> 
>      "currency": "USD",
> 
>      "total": 75.55,
> 
>      "customer": {
> 
>        "id": 1616616,
> 
>        "email": "jane@gmail.com",
> 
>        "address1": "567 Main St",
> 
>        "city": "Stafford",
> 
>        "state": "VA",
> 
>        "country": "USA",
> 
>        "zip": "22554",
> 
>        "phone": "555-710-9325",
> 
>      "line\_items": \[
> 
>        {
> 
>          "id": 10417352802515,
> 
>          "sku": "841483107332",
> 
>          "name": "Waist Cincher - Soft Nude / L",
> 
>          "quantity": 1,
> 
>          "gift\_card": false,
> 
>          "price": 75.55,
> 
>          "tax\_code": "PC040100"
> 
>        }
> 
>      \]
> 
>    }
> 
>  }  

![](https://user-images.githubusercontent.com/84099162/164264685-821f6b79-bf2d-461a-8f3d-3bab14ddf695.png)

**Step 5: Use Mocking Service**

A very useful feature during the design phase is having the ability for your consumers to interact with your API without having to code anything. The mocking service is a feature of the Anypoint Platform. You can simulate calls to the API in API Designer before publishing the API specification to Exchange or in Exchange after publishing the API specification. The mocking service will read the RAML specification of your API, create the API/service and return example data responses. This service allows users to interact with the API as if it was built and deployed. This feature allows you to rapidly iterate the API design with its consumer to finalize the contract.

First we are going to enable the mocking service for internal use.

Click the **Circular Arrow** icon in the right-hand toolbar it should expand the pane like so:

![](https://user-images.githubusercontent.com/84099162/164265600-6392cad0-fdc7-4f54-a833-a17cd79f2e6c.png)

**\*\*\*If you see an empty pane check to make sure the order/{id} resource is highlighted in the left pane like so:**

![](https://lh5.googleusercontent.com/eEItqnwB0Z8qBMniPfP6akWYwXdsIMKaQ90QgBycH3dn4ZNG2yBNvRNDGB8uaEjejLKZiM8XE91rvJacaBJkSNQPnjV1IEFWDaXieKxRYwkr7CVX57gGVnzpXLzq_dOYwDMer5MZ4oh7)

2\.   From **Select Server** dropdown change the selection from [**http://localhost:8081/api**](http://localhost:8081/api) to **Mocking Service**

3\.   Under **URI parameters (id\*)** you can add any number you would like to.

4\.   Then click the **Send** Button.

5.  You will notice at the bottom the sample response with the sample JSON code we copy and pasted in the order/{id} resource response body is showing. The mock response also shows a **200 OK** and **Time** output to simulate a the request and reply process for Shopify API.

Use the mocking service and check the examples is updated too.

The API design is ready. In the next lab we are going to publish the API so it can be discoverable by anybody in the organization.

![](https://lh3.googleusercontent.com/tBG1DAe6hVgZiuX6UG8pT8T-QAeLsRowiMcG8mTbHqc1t7AWL3ZX1sC15_opcStbV0EdSfQ88w0iZcN598Bu2LbscLDEACACOweAUePclQQMsfxfMi0TGFLa_3XMKiZhBLa8_WtOp26k)  

### **Summary**

In this lab, you completed the following steps:

*   [Step 1: Review the Shopify Requirements](http://workshop.tools.mulesoft.com/modules/module1_lab2#step-1-review-the-e-commerce-application-requirements)
*   [Step 2: Create the Shopify Experience API](http://workshop.tools.mulesoft.com/modules/module1_lab2#step-2-create-the-omni-channel-experience-api)
*   [Step 3: Create the Orders List Resource](http://workshop.tools.mulesoft.com/modules/module1_lab2#step-3-create-the-orders-list-resource)
*   [Step 4: Create the Order Instance Resource](http://workshop.tools.mulesoft.com/modules/module1_lab2#step-4-create-the-order-instance-resource)
*   [Step 5: Use the Mocking Servic](http://workshop.tools.mulesoft.com/modules/module1_lab2#Step%207:%20Use%20the%20Mocking%20Service)e

We easily designed the framework for our Shopify API, providing the ability to get orders and check single order. We leveraged RAML for a **design first approach**.

We saw how the mock service can be utilized to provide application developers an API mock up they can build their applications on. This significantly **speeds up end to end development**.  

To learn more about RAML follow this [tutorial](http://raml.org/docs.html).

*   See [Designing Your API](https://docs.mulesoft.com/design-center/design-create-publish-api-visual-editor) for more information on API design.
*   See [Design Mocking Service](https://docs.mulesoft.com/design-center/design-mocking-service) for more information on API design

**Congratulations! You have completed Lab 2.**

### [\--> Proceed to Lab 3](/module1-lab3.md)
