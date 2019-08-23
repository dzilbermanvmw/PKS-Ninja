# PKS Intro to PKS Monitoring & Operations

### 1.1 Configure Wavefront & vRLI in Enterprise PKS

The steps in this lab walk you through installation of VMware vRealize Log Insight and Operations appliances in the same or different Data Center where NSX-T/PKS products are deployed, installation of NSX-T and PKS/Kubernetes management packs and content and configuration of those management packs to receive logs/events and metrics data from those products.

THIS IS DEFINITELY WORK IN PROGRESS LAB

1.1.1 Launch vRLI UI https://<IP of vRLI server> and land select "New Installation" option which should land on the following screen:

<details><summary>Screenshot 1.1.1</summary>
<img src="Images/vrli1.png">
</details>
<br/>

1.1.2 Continue to work with vRLI initial setup UI:

<details><summary>Screenshot 1.1.2</summary>
<img src="Images/vrli2.png">
</details>
<br/>

1.1.3 Open the "VMware PKS" Integration. Navigate to the setup tab inside PKS. Copy the "Wavefront URL" and the "API Token"

<details><summary>Screenshot 1.1.3</summary>
<img src="Images/vrli3.png">
</details>
<br/>

1.1.4 From the Control Center desktop, navigate to Ops Manager at "opsman.corp.local" and open the PKS Tile

<details><summary>Screenshot 1.1.4</summary>
<img src="Images/vrli4.png">
</details>
<br/>

1.1.5 Select the monitoring tab to open the Wavefront integration page

<details><summary>Screenshot 1.1.5</summary>
<img src="Images/vrli5.png">
</details>
<br/>

1.1.6 Fill in the fields for "Wavefront URL" and "Wavefront Access Token" from step 1.1.3". Remember to press "Save" at the bottom of the page to save the configuration.

<details><summary>Screenshot 1.1.6</summary>
<img src="Images/vrli6.png">
</details>
<br/>

1.1.7 Click on the Logging section and enter the following settings, as shown in the screenshot:

- Enable Syslog for PKS: No
- Enable VMware vRealize Integration: Yes
 - Host: vrli-01a.corp.local
 - Enable SSL: false
 - Enable Sink Resources: Yes
- Click Save

<details><summary>Screenshot 1.1.7</summary>
<img src="Images/7.png">
</details>
<br/>

1.1.8 From the Ops Manager Home page click on the `BOSH Director for vSphere` tile.

<details><summary>Screenshot 1.1.8</summary>
<img src="Images/8.png">
</details>
<br/>

1.1.9 Click on the Syslog tab and enter the following details:

- Do you want to configure syslog for BOSH Director?: Yes
- Address: vrli-01a.corp.local
- Port: 514
- Transport Protocol: UDP

<details><summary>Screenshot 1.1.9</summary>
<img src="Images/9.png">
</details>
<br/>

1.1.10 Return to the Ops Manager Homepage and click `Review Pending Changes`, and then click apply changes. You will need to wait for the redeploy to complete before being able to make use of the updated settings, this could take up to an hour to complete.

<details><summary>Screenshot 1.1.10</summary>
<img src="Images/10.png">
</details>
<br/>

### 1.2 [Configure Prometheus with PKS](https://github.com/CNA-Tech/Apps-on-PKS/tree/master/prometheus)
