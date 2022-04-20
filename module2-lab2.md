# **Lab 2 Implement the Shopify API In Studio**

###   
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
