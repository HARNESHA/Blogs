# Mastering Email Deliverability

## 📧 Setting Up Amazon SES Observability with CloudWatch 🚀

Email is a crucial communication channel for businesses, and ensuring its reliability is paramount. Amazon Simple Email Service (SES) is a powerful tool for sending transactional and marketing emails. To maintain high deliverability and troubleshoot issues efficiently, robust observability is essential. In this guide, we'll walk through setting up comprehensive observability for Amazon SES using Amazon CloudWatch. Let’s dive in! 🌊

***

### 🛠️ Create a Configuration Set

A Configuration Set in SES allows you to publish event data to Amazon CloudWatch. This is the foundation for our observability setup.

* **Navigate to the SES Console:**
  * Go to the [Amazon SES Console](https://console.aws.amazon.com/ses/).
*   **Create a Configuration Set:**

    * Click on **Configuration Sets** in the left-hand navigation pane.
    * Click **Create Configuration Set**.
    * Enter a name for your configuration set and click **Create Configuration Set**.



    <figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXeUOTdX478hl1T0VjFlZ_-DG5hyNZaCPgoKIr-mhVuyb_rXxbiikBkvLBZ9hlphWtUtxn41xFzxdkoo0iub96LxWwuDh-jIEYCbqQAmRGZYDyFaDW4GPSRMdIH2ZMiMBbIRlFCpvA_9KOuv5TZjYSxfogE?key=jA2TK0iQRl7CPWB8QOBCUg" alt=""><figcaption></figcaption></figure>
* **Add CloudWatch Event Destination:**
  * Select your newly created configuration set.
  * Click **Create Event Destination**.
  * Choose **CloudWatch** as the destination.
  * Select the event types you want to monitor (e.g., sends, deliveries, bounces, complaints).
  * Click **Create Event Destination**.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcFArVay63AH7iqpPrklVFFjD-5dPrFzDsDtLTRj6sbozswgl6mRy46GLxWvrCIpDv1QJIjYPVRON6hpfEwxWhJUM_mIhnl3JfiyLECXuD7syMAOnG1NGb_XVPdtgFbQR4IyAs_C_EAPMJJe9p2ABLPJq_Y?key=jA2TK0iQRl7CPWB8QOBCUg" alt=""><figcaption></figcaption></figure>

### 🏷️ Create Event Destination with Message Tags and SES

To gain deeper insights, we’ll add dimensions to our CloudWatch events.

* **Add Event Destination:**
  * Within your configuration set, click **Create Event Destination**.
  * Name the event destination.
  * Select **CloudWatch** as the destination type.
  * Under **Event Types**, select the types of emails you want to monitor (e.g., send, delivery, open, click, bounce, complaint, reject).
  *   In the **CloudWatch Dimension Configuration** section, add dimensions:

      * **Dimension Name:** MessageTag
      * **Dimension Value Source:** Message Tag
      * **Dimension Name:** ses:from-domain
      * **Dimension Value Source:** One verified identity from your account



      <figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXcs4XukRhFuD35sRtAQdCyR18ZkVzxhkpZJE6GOBBl5YfBLEadk-oUvnjipXXu_3tUFcN4fE7u_Vkp6MFsFr4YCm1fqFUHeWygNDNheSs4rfGQQ_21oxRS3En2tJq5dHWV-DE87xorL3AwMcTcGxF6VIOUL?key=jA2TK0iQRl7CPWB8QOBCUg" alt=""><figcaption></figcaption></figure>

### 🔗 Create and Associate an Identity with the Configuration Set

Associating an identity ensures that your configuration set is applied to the correct email domain or address.

* **Navigate to Identities:**
  * In the SES console, click on **Identities**.
* **Create Identity:**
  * Click **Create Identity**.
  * Choose the type of identity (Domain, Email Address, or Managed Domain).
  * Enter the necessary details and click **Create Identity**.
*   **Associate Configuration Set:**

    * Select the identity you just created.
    * In the **Configuration Sets** tab, click **Add Configuration Set**.
    * Select the configuration set you created earlier.

    <figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXdCn-nKhi8wAFxKFBlSTmUw4GRv3ypW8KaxAxga_oPetun947DyP69xP5wqLlaCDXNtQPPxaB-t4-Ie1M0yVT4eEag7KbOvE4zHG41cOXcHxj2Mxd3_ld54rLf7ggcjQok5toaLo33ItQ7Cf26XOK1rAZs?key=jA2TK0iQRl7CPWB8QOBCUg" alt=""><figcaption></figcaption></figure>

### 📈 Enable Virtual Deliverability Manager

Virtual Deliverability Manager (VDM) provides advanced deliverability insights.

* **Enable VDM:**
  * In the SES console, click on **VDM**.
  * Click **Enable VDM**.
  * Follow the instructions to enable VDM for your account.

### 📊 Import a CloudWatch Dashboard

A pre-configured CloudWatch dashboard provides an at-a-glance view of your email metrics.

* **Navigate to CloudWatch Console:**
  * Go to the [Amazon CloudWatch Console](https://console.aws.amazon.com/cloudwatch/).
* **Create Dashboard:**
  * Click on **Dashboards** in the left-hand navigation pane.
  * Click **Create dashboard**.
  * Enter a name for your dashboard and click **Create dashboard**.
* **Import Dashboard JSON:**
  * Click on **Add widget**, then select **Import widget**.
  * Paste your JSON configuration into the text box.
  * Click **Import**.

<figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXexmzaVYEH8eDqbRYyVC-vcjp-THitX9HUd9WwBIj3STCwPxhMhkyRqJpzYh7EuQ3XnX7nVg5nkzz_E74wSYPIqvo8_0Hc7JrszDIct_F4RkTs3CMm1mm7ntmiSqKomtQerLg8n39BMqFzxEjRkr-yoapq-?key=jA2TK0iQRl7CPWB8QOBCUg" alt=""><figcaption></figcaption></figure>

### 📬 Monitor Mail Count with CloudWatch Dashboard

Your CloudWatch dashboard should now display SES metrics.

* **View the Dashboard:**
  * Go to your CloudWatch dashboard to see the metrics for your SES emails.
  * Ensure you have widgets for different SES metrics such as sends, deliveries, bounces, complaints, etc.

### 🔍 Gain Insights from Virtual Deliverability Manager

The Virtual Deliverability Manager offers detailed insights into email performance.

* **Navigate to VDM Insights:**
  * In the SES console, go to **Virtual Deliverability Manager**.
  * Click on **Insights**.
*   **Monitor Individual Mail Filters:**

    * Use the **Message Insights** section to filter by specific message tags, from-domains, or other parameters.
    * This will give you more detailed insights into complaints, bounces, and other email metrics.

    <figure><img src="https://lh7-us.googleusercontent.com/docsz/AD_4nXfvt6xPHBdr3Rj5QcIlwbVNY1_pSB3YeB_cgDhStn7wDDqJMwoB2mDHTEA9orSi-2YlG6gfD8Eq2LU_wxS0wbqW5wzI5EBbF411NWjweYbt14gvNZx3AG3iPZws88ZRjU4xOLX079jIoSOhxRgi0oBTnMNP?key=jA2TK0iQRl7CPWB8QOBCUg" alt=""><figcaption></figcaption></figure>

***

By following these steps, you’ll have a robust observability setup for Amazon SES using CloudWatch. This configuration will help you monitor and improve your email deliverability, ensuring that your messages reach their intended recipients.
