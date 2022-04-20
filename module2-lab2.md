# **Lab 2 Implement the Shopify API In Studio**

Overview

Since you understand how to start a project by importing the Shopify RAML Specification. You have also seen how the project scaffolding works with all the required resource endpoints. Now we need to add connectivity to Shopify and we will be using a Shopify Connector that will allow us to quickly create connectivity. 

The implementation will consist of a few steps

1.  Find the Shopify Connector via Anypoint Studio (through Exchange)
2.  Create Configuration Properties YAML to externalize needed Shopify credentials
3.  Add our Shopify Connector operator in the flow we will be working on 
4.  Update the Transform Message in the flow we are working on
5.  Test the implementation by running the Shopify project  

**Step 1: Setup up working on your flow**

We will start to add implementation connectivity of Shopify and will test out on flow endpoint resource **get\\order:shopify-exp-api-config**. To make working on this endpoint a bit easier let’s collapse all of the flows in the Project. We do so by right clicking in the body (any blank area will do) and right-mouse click to see the **Collapse All** option and select it.

![](https://user-images.githubusercontent.com/84099162/164312107-69a5e5c9-4601-42c9-b8c1-7ddef4489b74.png)

2\. Now find the **get\\order:shopify-exp-api-config** flow and click on the blue arrow in the top left to expand the flow like this: 

![](https://user-images.githubusercontent.com/84099162/164312229-c34622fd-eb76-4d1f-b57f-02ca16e98fa6.png)

**Step 2: Find and load the Shopify Connector**

1\. Put your cursor to the far right pane called Mule Palette. And click on the **Search in Exchange** option.

![](https://user-images.githubusercontent.com/84099162/164312382-4ce53bf7-907f-48bb-a619-ca7d7d0e7339.png)

2\. The **Add Dependencies to Project** Window will appear. In the search area type **“shopify”.** The **Shopify Connector - “MuleSoft”**should be the first option to appear. 

3\. Select the connector to highlight it.

3\. Select the connector and click the **Add** button.

4\. Then Select **Finish.**

**![](https://user-images.githubusercontent.com/84099162/164312587-9f98672f-69f5-4040-8c5d-93f247db12c6.png)**

5\. The Mule Palette in the right pane should have updated with the Addition of the **Shopify Connector**.

6\. On the furthest right sub pane there will be an extensive list of Shopify Operators.

![](https://user-images.githubusercontent.com/84099162/164314617-5a9f99c3-dc1e-40ac-8707-fffb5f45338b.png)

1\. In the operator sub palette Find and Select **Order List** This operator is perfect for what we are looking to do, which is retrieve all orders from within the **NTO Shopify Site**. 

![](https://user-images.githubusercontent.com/84099162/164314799-b5cc3d3e-3d68-477a-9a10-bac0e5ae0b61.png)  
  
2\. Highlight and drag **Order List** to the **get:\\order:shopify-exp-api-config** flow. Try to drag **Order List** next to the **Transform Message** like so:  
  
![](https://user-images.githubusercontent.com/84099162/164314881-1607e1a7-eb85-4981-820e-c601dabb879c.png)

3\. Double click on the **Order List in** the **get:\\order:shopify-exp-api-config** flow. Look at the lower pane just below the flow and you will see configuration settings with an **Attribute ‘config-ref’ is required** Warning. We need to configure the connector.   
  
![](https://user-images.githubusercontent.com/84099162/164315084-b275bb01-0431-470b-a46f-ccbf3ebf8196.png)  
 

**Step 4: Create a Property File**

We could enter our Shopify configuration details directly in the below area. But it’s a good practice to create a configuration file to hold all the parameterized properties in the project. We are going to create one and configure the connection credentials for our Shopify API implementation. First, we are going to create a folder and then create the config file.

1\. In the left pane labeled **Package Explore**, Click on **src/main/resources** in the **Package Explorer** view, right click and create a **New → Folder**, name it **configuration** and click **Finish**  
  
**![](https://user-images.githubusercontent.com/84099162/164315216-caded1ab-c414-4daf-af38-08f32bb2687c.png)**  
  
2\. Click on **src/main/resources/configuration** in the **Package Explorer** view, right click and create a **New → File.**  
  
**![](https://user-images.githubusercontent.com/84099162/164315305-c75f2216-1d9d-4c15-b22d-e86d34510477.png)**  
  
3\. Name it **config.yaml** and click **Finish**.  
  
![](https://user-images.githubusercontent.com/84099162/164315415-0337decf-f3e0-4072-a2b6-b2e0d7ec8347.png)

4\. Copy the following contents into **config.yaml**. These are the connection credentials your API will use for the Shopify connector.

>  shopify:  
>      host: "https://gamingo-vegas.myshopify.com"  
>      user: "e6b1cde4acb1b3704d8266b855ded8e0"  
>       password: "shppa\_68da37123914ee5df94eb3b1255bbf2d"  
>  

![](https://user-images.githubusercontent.com/84099162/164316236-d73ec862-4173-47cd-a461-96294e7e8ff6.png)

5\. Click the **Save All icon** on the top Navigation Menu.  
  
![](https://user-images.githubusercontent.com/84099162/164316100-e4070e22-7879-4bcf-abb2-2c99ed7b0801.png)  
  
6\. Close **config.yaml** file tab.  
  
![](https://user-images.githubusercontent.com/84099162/164316336-955edca2-dc48-4bda-9d28-3efb56a0ef31.png)

7\. To finish the configuration of the properties file for your API, click on the **shopify-exp-api** view and click on the **Global Elements** tab at the bottom of the pane.  
8\. Click the **Create** Option.  
9\. Go to Global **Configurations> Configuration Properties.**   
10\. Click **OK.**  
  
![](https://user-images.githubusercontent.com/84099162/164316691-a8b1388a-1676-40fe-b821-66496b25e47a.png)

11\. By **File** Click the **…**  
12\. Select the **config.yaml** file you just created  
13\. Click **OK.**  
  
**![](https://user-images.githubusercontent.com/84099162/164316775-c48a640e-6c67-43a4-8d4d-c915cd978686.png)**

14\. Navigate down to the lower configuration panel and click on the green **“+”** by **Connector configuration: Shopify\_Connector\_Config**  
  
**![](https://user-images.githubusercontent.com/84099162/164316924-66a873c0-1fd4-4870-bff3-c21ca6a594f2.png)**  
  
15\. Enter the following in the **Shopify\_Connector\_Config** Window:

*   **Username: ${shopify.user}**
*   **Password: ${shopify.password}**
*   **Base Uri: ${shopify.host}**  
     

16\. Click **OK.**  
  
![](https://user-images.githubusercontent.com/84099162/164317179-70ca7ca7-d75e-4681-826c-afd244257f5e.png)  
 

17\. Click **Test Connection...** Anypoint Studio will now attempt connecting to the NTO Shopify. **\*\*There are several different was to authenticate to Shopify, but for the sake of the workshop we are using this Basic Authentication method.\*\***   
  
18\. You should receive a “**Test connection successful”** Message. Press **OK** to Close the message.  
  
19\. Click OK again in the **Shopify\_Connector\_Config** Window.  
  
![](https://user-images.githubusercontent.com/84099162/164317458-ad94a4d9-0974-4685-bba8-26374974af96.png)  
  
Now our Shopify API is connected to **NTO’s Shopify Account**!  
  
**Step 5: Transform Message**

1\. Click **Message Flow** tab to switch out of the Global Element Pane back to the Message Flow pane where we need to update our **get:\\order:shopify-exp-api-config** flow.  
  
2\. Move your mouse to the Transform Message in the **get:\\order:shopify-exp-api-config** flow and double click it.

3\. In the below **Transform Message** pane you will see some code in the right pane called **Output Payload**. This is example response body that we created when we designed the **Shopify API** in **Module 1**. 

![](https://user-images.githubusercontent.com/84099162/164317586-4a580fa7-0529-4676-aec0-ae81568ddd7a.png)

1\. Delete the sample code under the Output Payload pane and replace with the following:

> %dw 2.0  
> **output** **application/json**  
> \---  
> payload

  
2\. Click the **Save icon** at the top right corner of the **Transform Message** Pane. To save you changes.

We have now made the necessary changes to the **get:\\order:shopify-exp-api-config** flow and we are now ready to test it!  
  
![](https://lh3.googleusercontent.com/hnfenAFO3uciTpuIny-Y1HH6CqIEISzU1OKP9DvXxyWPWtFe1-zEVaHUFib43c09utPby-vCFry4FowYwxj0Ojhuinegz9o87G0qQWUTwwTOc0x9lpYlmjm3sr-fUfiDxhXK4gBP6AFb)

**Step 6: Testing the Shopify API Connectivity to NTO’s Shopify**

In order to test the API we will need to run our project on our local machine. 

1\. To run the project all you need to do is Right Click in any blank area in the **shopify-exp-api**  Message Flow and Select **Run** **project shopify-experience-api.**  
  
**![](https://user-images.githubusercontent.com/84099162/164317965-956c272b-e48c-4443-be91-47cf43d59c51.png)**
