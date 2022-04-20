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

1.  Go to and click **Edit RAML** located at the top right corner.

![](https://user-images.githubusercontent.com/84099162/164269349-55205109-6fe7-4c01-b097-2d6cd7b8c0e7.png)

2\. An **Edit RAML** window should appear with a warning. Select the radio button **“Yes, send me to the text editor”** and then the **Continue** Button.  
  
![](https://user-images.githubusercontent.com/84099162/164289177-445d882c-13f7-48c6-b7da-e10ee8ac84c7.png)  
  
3\. You will notice that we are no longer in the **Visual Editor,** but are now in **Text Editor:**  
  
**![](https://user-images.githubusercontent.com/84099162/164289474-27bb00f3-2af1-46b1-bba2-3adf6122a12d.png)**  
  
 4. Go to the Setup located at the top right corner.

 5. In the drop down menu select **Import from Exchange**  
  
**![](https://user-images.githubusercontent.com/84099162/164289639-a8b4f96c-7926-4bfb-b69d-c2e5ed0507d8.png)**

  6. Look for **Shopify Experience API** and Select it.

  7. Press  **Import asset**  
  
**![](https://user-images.githubusercontent.com/84099162/164289786-995db317-e999-4d1c-9c1a-3a36e8c93a0f.png)**  
  
 8. Choose **Yes** from the Window **Replace** **root file**.  
  
![](https://user-images.githubusercontent.com/84099162/164289943-441af19f-e686-4924-b589-8f96a83ffe4b.png)

9\. On the left pane locate the **\<you name or initials>-shopify-experience-api** and click   
on the three dots.

10\. Select last option on the list, **Delete…**   
  
**![](https://user-images.githubusercontent.com/84099162/164290087-90d05b0d-f6d1-4ce8-ab83-9be63a1206d9.png)**

11\. A **Delete File** Window will appear, Click **Delete**.

![](https://user-images.githubusercontent.com/84099162/164290213-e6c77513-fe6e-4f10-ae0b-9a6b33003c62.png)
