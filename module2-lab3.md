# Module 2: API Deployment : Overview 

### Briefing

Anypoint projects can be deployed in a number of ways (via our Cloud, On Premise Data Center, 3rd Party (AWS, Google,Azure), or a mix of all. This workshop will show how deployment can be done in our Cloud managed offering, **CloudHub**.

![](https://lh4.googleusercontent.com/9Vto911syRW6ydu0m2YrytspwpgZ7gm8LdqzQbU5XQNsP0owr_H1jgZsDiIS_5xXd6n4a9lfeMTFvAhBpUuNtt-r_v-mqltUgw1SmA7eWYMDjWZFZJBzVbdF6kIjuKT_FWR2j2K3MmX8)

**\*\*Footnote: In some of our more advanced workshops we also show complete CI/CD process of deployment. Reach out to you Account Executive if you like to learn more about MuleSoft’s CI/CD capabilities.**

**Step 1: Deploy Shopify Project from Anypoint Studio**

1\. With your mouse select the **shopify-experience-api** under Package Explorer in the left pane and **Right Mouse Click.**  
2\. Menu option should appear scroll down and select **Anypoint Platform.**  
3\. Sub menu will appear to the right. Select **Deploy to Cloud.**

**![](https://user-images.githubusercontent.com/84099162/164335876-f8eacecf-a2f6-4995-b3f3-d5db005e2add.png)**

4\. Anypoint login window will appear. Enter your Anypoint credentials and click **Sign In.**

![](https://user-images.githubusercontent.com/84099162/164335934-1ab0016f-b3c4-451c-a171-b33a7674ec46.png)

5\. Under **Choose Environment** Select **Sandbox**.

![](https://user-images.githubusercontent.com/84099162/164336004-eee0ca29-5689-47b1-9e6a-b842e716d647.png)

6\. Under Deployment Application name you deployment “\<\*\*first name or initials>-shopify-exp-api-v1”\*\*.   
7\. Click **Deploy Application.**

**![](https://user-images.githubusercontent.com/84099162/164336078-db95f892-a393-46ff-8b04-18dc48f32e8a.png)**

8\. Screen will show that your application is **Deploying**. Click **Open in Browser.**

**![](https://user-images.githubusercontent.com/84099162/164336138-7b563159-a236-44a2-ad35-9e3987e9474b.png)**

9\. Screen will show that your application is **Deploying**.

![](https://user-images.githubusercontent.com/84099162/164336200-4451d3fd-ff2c-415b-8959-f8de100f77a7.png)

10\. Wait until you see that status has changed to **Started.** Click on the **\<first name or initials>shopify-exp-api-v1.**

**![](https://user-images.githubusercontent.com/84099162/164336241-05f6633a-c905-4a41-9593-83aaf4570af6.png)**

11\. You will be taken to a Dashboard screen **Right Click** on the **\<first name or initials>shopify-exp-api-v1 and select Open link in new Tab.**

![](https://user-images.githubusercontent.com/84099162/164336285-a46809ae-3566-48e3-868d-cfa534ff1b05.png)

12\. Replace browser URL with: **http://\<your first name or initial>-**[**shopify-exp-api-v1.us-e2.cloudhub.io/api/order**](http://shopify-exp-api-v1.us-e2.cloudhub.io/) and hit **Enter/Return.**

You should get a payload response like so.

![](https://user-images.githubusercontent.com/84099162/164336418-33c1aa91-0551-40c0-a5ea-829ab228ccda.png)

Now we have successfully deployed our Shopify API!

**Congratulations! You have completed Module 2!**

[**\-->Proceed to Module 3**](/module3-overview.md)
