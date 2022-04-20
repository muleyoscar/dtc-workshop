# **Module 1: Lab 3 Publish the Shopify API To Exchange**

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

 12. You should see the following complete API specification with only the  **shopify-experience-api.raml** in the left pane:

![](https://user-images.githubusercontent.com/84099162/164290421-1c97c8a4-05bb-469a-9213-09c7528c625e.png)

**Step 2: Publish Your API to Anypoint Exchange**

Click on the **Publish** button and then on the **Publish to Exchange** button:

![](https://user-images.githubusercontent.com/84099162/164290687-a8179c7c-9915-404c-ba79-2a13b8716523.png)  

A popup window to capture the attributes that you want to publish to Exchange will appear. Most of these fields will be pre-populated and the RAML will be verified to ensure that there are no errors. Complete the **Asset version** field with “**1.0.0.”**

**![](https://user-images.githubusercontent.com/84099162/164290850-ad0bb78c-53cd-4eab-9fde-28018675c120.png)**

Click the "Publish to Exchange" button when you have finished reviewing the API name and version information. We have now published our Shopify Experience API to **Anypoint Exchange** for other developers to discover and consume!

![](https://user-images.githubusercontent.com/84099162/164290972-e7a6ab7c-afac-497f-b653-ded7ce71236e.png)

Each time you publish an API Specification you will generate two assets:

*   RAML Spec: This is the RAML Specification. Everybody on the organization can discover the spec and documentation.
*   Rest Connector: This is a connector automatically generated for the API you have just defined. We will cover this in more details on Module 2 and Module 9.  

**Step 3: Augment the Documentation for Your API**

As demonstrated in Step 2, publishing your API to exchange is as easy as a few clicks. However, Exchange has really only just captured the basic attributes and documentation for your API at this point. Ensuring that your API is easy to find and "self-service ready" is your responsibility as an API designer. Let’s find our API in Exchange and add more to our API documentation.

1a.     After you click the **Publish to Exchange** the **Shopify Experience API** Specification will start loading into **Exchange**. Once loaded there will be a pop window letting you know that your **Shopify Experience API** is in **Exchange**. To go to the API specification you can simply click on the **“Exchange”** link in the window. 

![](https://user-images.githubusercontent.com/84099162/164291282-6f7b6aba-7cb7-4fa1-9031-afd4c766d7cf.png)

1b.   **Alternatively,** if you had already closed out of the confirmation window you can Navigate to Exchange from the "hamburger menu" at the top left corner of **Design Center**.

![](https://lh3.googleusercontent.com/BdjvvA85j-71xd3xtQrZhVUGl15R26fArReFnhc9I2SDcb4b5j4Sv-DkWutf5NTLBihy18nMy-8K_5NRqe1JvLc4xAE9Dhu1kT3YinWZUz9wwuyATq9s2lYxxKujFzwMRYgzQ67r108Y)

You can then quickly search for the **“\<your name or initial>-Shopify Experience API”** in **Exchange** as we did [**Lab 1**](/module1-lab1.md) of this **Module.**

2.  Once you are in the **\<your name or initial>-Shopify Experience API** you should see something that looks like this:

![](https://user-images.githubusercontent.com/84099162/164291674-a17b3689-0f3e-4e62-b6b8-7d514c9d5e72.png)

3\. Let’s start adding some content to the API by click on the **Edit documentation** icon

4a.  Exchange assets are documented using "markdown" language. Markdown language is a format-agnostic syntax used for creating documentation independent of how it will be rendered (i.e. HTML, PDF, text, etc). It is used by popular applications like GitHub as the standard way to create software documentation. For more information on markdown please refer to:

[https://guides.github.com/features/mastering-markdown/](https://guides.github.com/features/mastering-markdown/)

Create your own documentation for your API, or copy the following text into the editor:

> Welcome to the \*\*NTO developer portal\*\*. This API represents the Direct to Consumer Shopify Shopping Cart Application - that includes:
> 
> \-order 
> 
> \-product
> 
> \-inventory tracking
> 
> The \*\*Shopify API is an Experience API\*\* that is a part of NTO's API led Architecture . This same architecture allows NTO to leverage a \*\*headless commerce\*\* platform that is \*\*highly composable\*\* and \*\*future proof!\*\*

4b.  **Alternatively**, if you are more comfortable with WYSIWYG editing you can click on the Visual button and copy an paste the following into the editor body:

> Welcome to the **NTO developer portal.** This API represents the Direct to Consumer Shopify Shopping Cart Application - that includes:
> 
> *   Order
> *   Product
> *   inventory tracking
> 
> The **Shopify API is an Experience API** that is a part of NTO's API led Architecture . This same architecture allows NTO to leverage a **headless commerce** platform that is **highly composable** and **future proof!**  

5.  Click on the **"Save"** button at bottom of screen. Your draft of the API documentation is saved but not published until you formally **"Publish"** the final updates to Exchange, so feel free to save multiple drafts as you create your documentation.

![](https://user-images.githubusercontent.com/84099162/164292230-74e667f0-f6f3-41ff-82eb-609e61662255.png)

6\. You can press Publish, Discard , Edit or View published.

*   Discard - Throw away changes
*   View Published - View published documentation
*   Edit - Lets you edit the content
*   Publish - Publish documentation changes to exchange

![](https://user-images.githubusercontent.com/84099162/164292446-8daa8700-cd3f-4d9d-a805-e7c5ae136159.png)

7.    Press the **Publish** button. Your documentation changes are now visible on Exchange!

![](https://user-images.githubusercontent.com/84099162/164292654-a54fb284-0eab-4887-acb7-9fc639c391da.png)

**Exchange** documentation can be comprised of multiple pages. So far we have just created the home page for our API.

It is common practice to include links to other content like video tutorials in our Exchange documentation. This makes it easier for the interested developer to gain access to all of the documentation required to learn how to use the API.

**Congratulations! You have completed all of the labs in Module 1!**

### [\-->Proceed to Module 2](/module2-overview.md)
