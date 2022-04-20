Module 1: The Modern API - Design: Lab 2 

Overview

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

3. [Use standard header parameters](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)

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

2. **Anypoint Design Center** is used to design your API’s. When you arrive at the Design Center landing page you will see a list of API’s that have already been designed by your organization.

![](https://lh4.googleusercontent.com/JdKf3HozfIQwfBI8NEwVhZjGWKXRwAa4oehEzlHZABfvrRdpdb0Ae2Vp23we84ukSMjzGRD3Ywz8_bXAdTLokt5f_yC3RZOzl-aBx3-iJDr_qN3ccYaxpjuosb5BlgBtp5gEuZQGkUNn)  
  
**Anypoint Design Center** is used to design your API’s. When you arrive at the Design Center landing page you will see a list of API’s that have already been designed by your organization.

![](https://lh4.googleusercontent.com/t1OkJ7x4PopDMDXHaxL3ZcM7bk5nE0aEWzEul0pDFcdU2ebOt26j3WR6_Dtck3Aa_L7rlGUcFx0XmbT6BPuSfEFgY6tXQnB2wv7VteF96DStWjSuaDMMembe7UkdG43NZHygnLGHnLBF)
