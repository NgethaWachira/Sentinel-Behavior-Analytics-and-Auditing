# Objective
The objective is to guide users in setting up and using Microsoft Sentinel for security monitoring, anomaly detection, auditing, and content search. We explain how to enable UEBA to detect abnormal user behaviors, configure audit logging to track user activities, and perform content searches for compliance and investigation purposes. We also cover the integration of Microsoft Entra ID, setting up diagnostic settings, and querying logs in Azure Log Analytics Workspace to improve security, monitoring, and data analysis.

## Skills Learned
- UEBA Configuration and Usage: Learned how to enable and configure User Entity Behavior Analytics (UEBA) in Microsoft Sentinel to detect abnormal user behavior and analyze user activity.

- I understood how to set up anomaly-based rules, such as Near Real Time (NRT) rules, to identify unusual activities in the environment using KQL (Kusto Query Language).

- Sentinel Data Integration: Gained knowledge on how to collect and integrate data from SaaS applications, on-premises applications, and Microsoft Entra ID into Microsoft Sentinel.

- Learned how to enable and configure audit logging in Microsoft Sentinel to record user and admin activity, as well as setting permissions to manage audit functions.

- Content Search and eDiscovery: Learned how to perform content searches for compliance, as well as using eDiscovery features for forensic investigations and managing eDiscovery roles.

- I understood how to set up diagnostic settings for Microsoft Entra ID and integrate them with Azure Log Analytics to collect log data.

- Log Querying and Management: I learned how to perform queries on log data within Azure Log Analytics and handle Microsoft Graph Activity Logs.

- Role and Permission Management: I gained experience in managing roles and permissions related to auditing and eDiscovery to ensure proper access control for sensitive activities.

## Tools Used
<div>
<img src="https://img.shields.io/badge/-User%20Entity%20Behavior%20Analytics%20%28UEBA%29-cca385?style=for-the-badge&logo=cloudflare&logoColor=white" alt="User Entity Behavior Analytics (UEBA)">
<img src="https://img.shields.io/badge/-Microsoft%20Sentinel-f7f5f2?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Microsoft Sentinel">
<img src="https://img.shields.io/badge/-Entra%20ID-00ffcc?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Entra ID">
<img src="https://img.shields.io/badge/-Kusto%20Query%20Language%20%28KQL%29-006666?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Kusto Query Language (KQL)">
<img src="https://img.shields.io/badge/-Microsoft%20Purview-ff804c?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Microsoft Purview">
<img src="https://img.shields.io/badge/-eDiscovery-660a3d?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="eDiscovery">
<img src="https://img.shields.io/badge/-Microsoft%20Graph%20API-9900cc?style=for-the-badge&logo=Microsoft%20Graph&logoColor=white" alt="Microsoft Graph API">
<img src="https://img.shields.io/badge/-Azure%20Log%20Analytics%20Workspace-ffcc00?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Azure Log Analytics Workspace">
<img src="https://img.shields.io/badge/-Azure%20Monitor-9e9c61?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Azure Monitor">
<img src="https://img.shields.io/badge/-Azure%20Resource%20Groups-33cc33?style=for-the-badge&logo=Microsoft%20Azure&logoColor=white" alt="Azure Resource Groups">
</div>

## Steps
- First, we set up User Entity Behavior Analytics (UEBA) in Microsoft Sentinel by going to Microsoft Sentinel service in the Azure portal, choose the Sentinel Workspace that you want to configure UEBA for, for our case it's SentinelLogWorkspace. Go to Threat Management, and under it select Entity Behavior, this is where you manage UEBA settings, 
Configure UEBA Settings by clicking on Entity Behavior Settings - Note: Only users with Global Admin or Security Admin roles can configure UEBA settings, so ensure you have the appropriate permissions.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/aac44ff355ba1466fdb03754aca001d6f3177811/Images/Entity%20behavior%20settings.png" width="700" />
</p>

- Sync Sentinel with Entra ID (formerly Azure AD) - If your organization is not using an on-premise Active Directory (AD), ensure that Microsoft Sentinel is connected to Entra ID (formerly Azure AD). This is necessary because UEBA relies on Azure AD identities to analyze user and entity behaviors. After setting up Entra ID, make sure to apply the changes so that the sync is complete. 

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/b6b64a6c83ba6c6847aa09cc0aef41d0331a5cb3/Images/Setting%20UEBA.PNG" width="700" />
</p>

- Select data sources from the Entity Behavior Settings, you’ll find an option to select which data sources you want to enable for UEBA, common data sources include Azure AD logs, Defender for Identity, and Microsoft Defender for Office 365. Once you've selected the appropriate data sources, ensure you enable UEBA for those sources. After enabling, Sentinel will start collecting and analyzing user and entity behavior patterns from the selected data sources and generating insights about potential risks and anomalies. We can set up alert rules based on suspicious behavior detected by UEBA, allowing us to take timely action.

- Once UEBA is set up, go to the Entity Search Area - this area allows you to search for entities such as accounts, devices, host IPs, and other objects of interest. Enter the entity e.g., an account name like “James Rain” for our case or an IP address you wish to search for, specify the type of object you’re investigating (accounts, devices, IPs, etc.) to refine your search. After searching, the system will show any anomalies linked to that entity, these anomalies could include unusual logins, failed access attempts, or other suspicious activity that Sentinel has flagged based on UEBA analysis. Adjust the timeline filter to help you narrow down and investigate activity over a specific timeframe.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/093aef5055729e355ee945db694895340579b9ad/Images/Searching%20using%20entity%20pages%201.PNG" width="300" />
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/093aef5055729e355ee945db694895340579b9ad/Images/Searching%20using%20entity%20pages%202.PNG" width="300" />
</p>

- Next we conduct Anomaly Monitoring and Analysis in Microsoft Sentinel. Open the Microsoft Sentinel portal, In the left-hand menu, under Configuration, select Analytics, find and click on Anomalies. This section provides a detailed view of all the anomaly-based alerts and entries that Sentinel has detected, which could indicate unusual or suspicious activity.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/dfef391db334742fa44f521ecc8b5c0d512d4a7e/Images/Configuring%20anomaly%20detection%20rules.PNG" width="700" />
</p>

- Edit any anomaly entry using the ellipsis at the end of the log. Click on the ellipsis and it will open a menu with options such as edit, investigate, view details, or assign. Select edit to modify the anomaly's details such as changing its severity, marking it as resolved, or providing additional context or notes. These anomalies are monitored in real-time or near-real-time, ensuring that any new developments or behaviors are flagged promptly.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/dfef391db334742fa44f521ecc8b5c0d512d4a7e/Images/Editing%20an%20anomaly.PNG" width="700" />
</p>

- We will also create a Near Real-Time (NRT) Rule in Microsoft Sentinel for anomaly detection as well. From the microsoft Sentinel navigation pane, select Configuration, then click on Analytics. Click on Create to create a new rule, choose scheduled query rule for the type of rule, set query frequency to a near-real-time frequency, and proceed to the rule logic configuration.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/d26b70b764330b3ccce0e2d02820a5df9d48154a/Images/Creating%20NRT%20rule%20anomaly.PNG" width="700" />
</p>

- Next we define the rule’s parameters using KQL. In the rule logic section, we wrote a Kusto Query Language (KQL) query that will detect anomalies based on our data. Example KQL query for anomaly detection on `SecurityEvent` table. Configure the logic to trigger on any anomalies detected, review the details and click Create to save the rule. It will now run continuously based on the defined schedule, monitoring for anomalies.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/4a32200e780d4969d642dbd092f3e37f38db487e/Images/KQL%20Editing.PNG" width="700" />
</p>

- Setting up auditing in Microsoft Purview from the Microsoft 365 admin center, in the left-hand navigation menu, go to Environment, under Environment, select Solutions, then click on Audit. This is where you'll configure and manage auditing settings. (Understand the Licensing differences, Standard (E3 Office) License provides basic auditing features while Premium (E5 Office) License offers advanced auditing capabilities).
- In the Audit section, navigate to Settings, click on Role and Scopes, go to Role Groups and look for the Audit Manager role group, ensure the necessary individuals or groups are added to the Audit Manager role to give them permission to manage and configure auditing. Here we are giving ourselves permission to audit.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/5d20ddf98baf7868a0c52784ed10d78910ec2e45/Images/Authority%20to%20audit.PNG" width="300" />
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/04302d6e53a68469334119502a9f743f9eac9313/Images/Assigning%20user%20to%20audit.PNG" width="300" />
</p>

- Next we activate auditing by `Start Recording User and Admin Activity` as seen in the image. Go to the Audit tab within the Audit section, click on `Start recording user and admin activity`, this action will activate auditing, allowing Purview to start logging user and admin activity within your environment, all menu items will now be fully accessible and no longer grayed out.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/73d27a59ea2f901ca2988ce4d139857ee3b69ec7/Images/Turning%20on%20auditing.PNG" width="700" />
</p>

- We then configure the scope of the audit, select the time range, choose the activities, specify which users, and workloads to audit. After the audit search completes, you will see the results displayed on the screen. To analyze the data offline or share it with others, click on the Export option and select Export as CSV, this will download the audit data as a CSV file, which you can open and analyze using Excel or other tools.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/f259ca95018567a788c4795d513fd0a7e92084c4/Images/Input%20parameters%20for%20our%20audit.PNG" width="700" />
</p>

- To set up eDiscovery and Content Searches in Microsoft Purview, the account you are using must have the eDiscovery Manager role. To assign the eDiscovery Manager Role, in the Microsoft 365 compliance center, go to Permissions under the Compliance section, look for the eDiscovery Manager role group, add the users or accounts who need to perform searches and manage eDiscovery cases as eDiscovery Managers.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/b34f782875db22aaea2e7baf46832b58fe505b04/Images/E-discovery%20manager%20role.PNG" width="700" />
</p>

- Assign eDiscovery Managers and Administrators in the Role Settings through the Compliance center, navigate to Permissions. Under the eDiscovery Manager role group, click Edit, add the necessary users to the eDiscovery Manager group. (eDiscovery Manager Role allows users to create and manage eDiscovery cases, run searches, and export search results while eDiscovery Administrator Role has more comprehensive permissions, such as configuring eDiscovery settings, managing hold policies, and setting up content searches).

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/cddac95784aec633875fe2863d53fa8e07856c44/Images/e-discovery%20manager%20and%20administrator.PNG" width="700" />
</p>

- To access Content Search, in the Microsoft Purview Compliance portal, navigate to Solutions, under Solutions, select eDiscovery. Click on Content Search, it allows you to search across various workloads (e.g., Exchange, SharePoint, OneDrive) to locate specific data across your organization's environment. Create a Search, specify the search criteria, run the search - Purview will scan the specified locations for the content that matches your conditions, review the results such as number of items found and metadata like the date, sender, or author. You have an option to export the results for offline analysis or legal purposes.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/ebe9a1aa861418d26838e01aa3eaa945112da11d/Images/eDiscovery%20content%20search.PNG" width="700" />
</p>

- Next we integrate Graph Activity Logs into our Azure environment using Log Analytics. We first create an Azure Log Analytics Workspace by accessing Azure Portal, search for Log Analytics in the search bar, click on Log Analytics workspaces and create a new Workspace.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/9043980ad2ff45d84292733986f69425c366f082/Images/Creating%20a%20log%20analytics%20workspace.PNG" width="700" />
</p>

- We then go to Microsoft Entra ID from Azure portal, in the Microsoft Entra ID pane, find and select Diagnostic Settings under Monitoring in the left-hand menu. Add diagnostic setting, this will allow us to configure the logs that will be sent to our Log Analytics workspace.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/f20cbff7b36b3058dfdbb8814a558ef010e7a79d/Images/Diagnostic%20settings%20in%20Entra%20ID.PNG" width="700" />
</p>

- Enable “MicrosoftGraphActivityLogs” and send to Log Analytics Workspace. After clicking on Add diagnostic setting, name the diagnostic setting, enable MicrosoftGraphActivityLogs - it's selected to capture logs related to Graph API activity, send logs to Log Analytics Workspace that we created earlier from the drop-down list, and click Save to apply the diagnostic settings.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/eb4955705d031d1b9e7699f6834d3049335bd01f/Images/Sending%20to%20our%20log%20analytics%20workspace%20that%20we%20created.PNG" width="700" />
</p>

- After configuring diagnostic settings, logs will start flowing into your workspace, go to the Log Analytics Workspace that we created, for our case it is `graphlogworkspace`, click on Logs under the General section in the workspace menu, use Kusto Query Language (KQL) to query and analyze the Graph Activity logs. You can modify the query to filter by specific activities, users, or time periods as needed. If no longer needed, delete the workspace by removing the associated resource group.

<p align="center">
  <img src="https://github.com/NgethaWachira/Sentinel-Behavior-Analytics-and-Auditing/blob/03faa0d57bf3cabb4ce06a2acddab2020d3ba119/Images/Where%20we%20perform%20log%20queries.PNG" width="700" />
</p>





