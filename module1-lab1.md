# Module 1: The Modern API - Design: Lab 1

### Lab 1: Search for an API in Exchange

#### Overview

API’s are the reusable assets that simplify and accelerate the creation of modern software applications. As a Mulesoft developer you will need to consume API’s created by other members of the organization and publish new API’s for others to consume. This new consumption model is the foundation of a new approach for delivering software solutions where API’s form the building blocks of the modern enterprise.

This first lab will focus on using **Anypoint Exchange** to search for API’s and other assets published in the private exchange.

### Step 1: Login to Anypoint Platform

1.   Go to [http://anypoint.mulesoft.com](http://anypoint.mulesoft.com/)

You should have received an email from [demos@mulsoft.com](mailto:demos@mulsoft.com) with contents similar to the below:

![](https://lh5.googleusercontent.com/PSKwSLl4gHrotuO_iDZ98cg-HMmz81nGgyXaulvDargIZYtEgGVrMnImTFDCsqQ4qL4FiG6vDUgQd4FyMnlo5wxo4TbJT3jO_dwAaijoq3plnEdeN8U1mngE_oR-6fApjmsz713xl-2u)

Enter **your credentials** into the Username and Password fields:

![](https://lh3.googleusercontent.com/I3BmVSIOrRI7-MOYw1bwLIwLXbQhanAGkbLxU8nXPJBdrfT3Q48do4MTAT_-CspwMolWh9MdLMXpesaUBVeH_TzQ9B-RKA1YrtcXacWcFxFEw6bNkD-aeSDD7MgcH7s1D3qrvIRp3iij)

![](https://user-images.githubusercontent.com/84099162/163307176-edb5c8b1-bdd6-4e62-95c7-9486a34b7ba3.png)

3.    You should see the following landing page once you are logged in to Anypoint Platform.

![](https://lh3.googleusercontent.com/12uiw4WgEb8UXtVs5USDIxp-U92nW8cbwOixWN2Dl9RbcoFgVV7h2RfGP9wRV7gxEMKEhFB0YhF-Sblc3WHJitEq-p2NWMe9QvQxYgh2DZGCv4sPwRyoNERyynrtyUuarA5pZlvazu4v)

4\.     Click on the Business Group that is on the right top corner of the screen. The name will vary with the class. Select sub group that has “**DTC Workshop…**” labelled. 

![](https://user-images.githubusercontent.com/84099162/163307773-70b053e7-5dff-48b6-bf84-a01c563bb83b.png)

### Step 2: Access Anypoint Exchange

1.   Click on the icon labeled: **"Discover & share"**

![](https://lh4.googleusercontent.com/WfLVdBHMKu_aoimqMRxzs3gTPxmD8-1S8al2kpriEDrTHSDj8vs7ifUUEeGOLHsAPoltFVa6tXkmvQW1swcnq1HZLhS0zXAj3y2-z7h8x459yJlx519BAd2AvY7fgJ-KZXurlAlUMmUP)

2\.  You will now be presented the landing page for the **Anypoint Exchange** portal:

![](https://lh3.googleusercontent.com/RqJVjLuBYeiFcr8ezbjlMCEGcCocqE1s41lqMgFt5I1mxFGyjgteQ4B2jZGOdox0Dz7KD7gF5FFxyouy8psVQUq9OrfpiDgZ_D7kSTyssSffSxq6jO8D_WFJUKDgpCNsMHOcRzmmDEB7)

**Anypoint Exchange** should be your initial starting point for just about any project. If you are looking to reuse an API then **Anypoint Exchange** is obviously where you should start. But even if you are creating a new API to be reused by others, it makes sense to first look in Exchange to see if the API already exists. Sometimes you will find that someone else has already undertaken the task of creating the API, or has created a subset of what you need.

**3.  Anypoint Exchange** allows for discovery on the _public_ or _private_ exchange. Every organization will automatically have a private exchange created for them.

Software assets stored in **Anypoint Exchange** can only be discovered by users that have permissions for the private exchange for that organization. Furthermore, organization administrators can also create independent _business groups_ to provide even more restrictive discovery. **Anypoint Exchange** users can only search within their currently selected business group. The currently selected business group, "Public" in this example, is shown.

![](https://user-images.githubusercontent.com/84099162/163308447-9440003e-6e7a-44a1-856d-9b56e0be2048.png)

As you can see from the screen above, there are organizational search criteria on the left hand side of the page. By default searches will search the private exchange only, but you can restrict or expand your searches by selecting a different organizational level. Select **All assets** to select both MuleSoft public and your private repositories.

There are two more items behind the last organization **My applications** and **Public Portal**. We will describe them but they are covered in Module 3 and Lab 4.

*   **My applications**: These are the clients registered in the organization that are consuming the APIs that are deployed in the organization.
*   **Public Portal**: You can define a public portal to let any user to consume any public org API that the organization may publish.

![](https://user-images.githubusercontent.com/84099162/163308640-a9bc0142-148b-490e-8bb6-8990127ef3ca.png)
