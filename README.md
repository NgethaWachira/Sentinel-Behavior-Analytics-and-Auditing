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








