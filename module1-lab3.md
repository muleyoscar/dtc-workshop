### Overview

In Lab 1 we examined how to use **Anypoint Exchange** to facilitate the API discovery process. In Lab 2 we learned how to use **Anypoint Design Center** to design the specifications for a modern RESTful API. In this lab we will learn how to publish our API to **Anypoint Exchange** so that API consumers and API developers within the organization are able to leverage the API through "self-service".

One of the biggest challenges encountered by early adopters of SOA was how to scale their development activities. SOA maintains many of the reuse principles that we have discussed in our "API-led" approach to software development. Unfortunately, most SOA efforts could not achieve their reusability objectives because of a few limiting factors including:

*   Poorly documented services
*   Lack of mature tools to facilitate service discovery
*   Over-reliance on limited number of knowledgeable resources
*   Burdensome processes for gaining access to services

As a result, many SOA-based initiatives were only able to partially achieve their reusability objectives because developers would adopt the path of least resistance and simply recreate services rather than reuse them. The **MuleSoft Anypoint Platform** addresses all of these issues by providing innovative tools like **Anypoint Exchange** that alleviate these challenges.

Let’s take a look at the process for publishing and documenting our reusable **Shopify Experience API**.  
  
**Step 1: Complete the Shopify Experience API Specification**

Before we get started, make sure you are logged into the **Anypoint Platform** and viewing the **Anypoint Design Center** screen. You should have your **"\<your name or initials> - Shopify Experience API"** open and visible. We have only defined a few resources and methods at this point and need to author the full API in order to complete the exercise. Rather than build it from scratch, we have the ability to import an API specification previously constructed for the workshop.

Go to and click **Edit RAML** located at the top right corner.  
  
![](https://user-images.githubusercontent.com/84099162/164269349-55205109-6fe7-4c01-b097-2d6cd7b8c0e7.png)
