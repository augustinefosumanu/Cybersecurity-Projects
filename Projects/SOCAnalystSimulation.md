# Security Operations Center (SOC) Analyst Simulation

## Overview

This project simulates the role of a Security Operations Center (SOC) analyst for Virtual Space Industries (VSI), a company developing virtual-reality programs. As an SOC analyst, I am responsible for detecting and analyzing potential cyberattacks—particularly from a known competitor, JobeCorp—using Splunk as the central monitoring and analysis tool. </br>

The monitored systems include: </br>

-  Apache Web Server: Hosts VSI's public website and administrative portal. </br>

-  Windows Server: Contains sensitive intellectual property tied to next-gen VR products. </br>

## Technical Skills

✅ Log Collection & Ingestion (Windows & Apache Logs) </br>
✅ Splunk Deployment & Configuration </br>
✅ Dashboard Creation & Custom Reporting </br>
✅ Alert Rule Development for Threat Detection </br>
✅ Log Correlation & Timeline Reconstruction </br>
✅ Cyberattack Behavior Analysis </br>
✅ SIEM-Based Threat Hunting </br>
✅ Real-Time Security Monitoring Implementation </br>
✅ Incident Investigation & Forensics </br>
✅ Executive-Level Summary Report & Presentation Preparation </br>

## Windows Logs

#### Upload Windows Server Logs to Splunk

I selected “Add Data” in Splunk, chose the “Upload” method, and selected the windows_server_logs.csv file from the **/splunk/logs/Week-2-Day-3-Logs/** directory. Without changing the source type settings, I clicked “Next,” updated the “Host” field to “Windows_server_logs,” and reviewed the settings. After submitting, I saw a success message and clicked “Start Searching” to begin analyzing the data. </br>
</br>
![image](https://github.com/user-attachments/assets/ca1575de-c28b-4cd0-a624-251eacde2c3f)
![image](https://github.com/user-attachments/assets/0ef41984-1cbe-458f-b88b-f31e53c55eec)
![image](https://github.com/user-attachments/assets/519bd1cf-ae3a-4d07-b399-fd964fb18829)
![image](https://github.com/user-attachments/assets/2f1fb6d8-c626-4e33-bf96-c2b8cf5e3095)
![image](https://github.com/user-attachments/assets/b8032a27-59df-4879-9f40-c6d5a1a4e4e5)
</br>

### Reports

#### Signature Table with Signature IDs

I entered a Splunk Processing Language (SPL) query to extract unique combinations of signature names and signature IDs. To avoid duplicate entries, I used the **dedup** command in my search:
```shell
source="windows_server_logs.csv" host="Windows_Server_Logs" sourcetype="csv" | dedup signature, signature_id | table signatures, signature_id
```
This command ensures that only one instance of each unique signature and ID pair appears in the table. Once the data was confirmed to be accurate and complete, I selected Save As > Report, named the report “Signatures and associated signature IDs” and added a short description to clarify its purpose.
</br>
</br>
![image](https://github.com/user-attachments/assets/099b912e-7bd5-4abf-b09e-019151b7ca19)
![image](https://github.com/user-attachments/assets/813c46c2-4bed-427d-8f37-8efe9129ae01)
![image](https://github.com/user-attachments/assets/4f5c3b0e-def8-473c-9ade-ae0e896293e7)
![image](https://github.com/user-attachments/assets/62e3f1f4-fe4b-4126-aae0-2c134cd3ec7c)
</br>
</br>

#### Windows Log Severity Distribution Report

I used the following SPL to calculate both the count and percentage of each severity level:
```shell
source="windows_server_logs.csv" | stats count by severity | eventstats sum(count) as total | eval percentage=round((count/total)*100,2) | table severity, count, percentage
```
This search first aggregates the number of events by severity using the stats count command. Then, using eventstats, it calculates the total number of events across all severities. The eval command computes the percentage of each severity level, rounding it to two decimal places for readability. The final table displays three columns: severity, count, and percentage, providing a clear view of the distribution of severity levels in the logs. Once I verified that the output accurately represented the data, I selected Save As > Report, named it “Windows Log Severity Distribution Report,” and added a brief description outlining its purpose.
</br>
![image](https://github.com/user-attachments/assets/9cbc9d5e-8061-4aac-a490-a85c5e5dcf5c)
![image](https://github.com/user-attachments/assets/0767585e-e232-4032-ba17-10df872dbaaa)
![image](https://github.com/user-attachments/assets/9bfa034b-4b0b-43f4-b71e-413b6ff60f99)
![image](https://github.com/user-attachments/assets/b6c0244f-0ed0-4ea4-8018-6d250ded434e)
</br>
</br>

#### Windows Activity Success vs Failure Report

I used the following SPL query:
```shell
source="windows_server_logs.csv" |stats count by status | eventstats sum(count) as total | eval percentage=round((count/total)*100,2) | table status, count, percentage
```
This search uses stats to count the number of events grouped by the status field (which includes values like "success" or "failure"). The eventstats command calculates the total number of events, and then eval computes the percentage share for each status type. The resulting table clearly shows how many activities were successful versus how many failed, along with their respective percentages, allowing VSI to quickly spot anomalies—such as an unusually high failure rate. Once I reviewed and confirmed the data, I saved the search as a report titled “Windows Activity Success vs Failure Report” and included a short description explaining its purpose.
</br>
![image](https://github.com/user-attachments/assets/3574244d-ecd8-4633-9d09-15f1272ddf68)
![image](https://github.com/user-attachments/assets/83fcf936-a1aa-4f1e-a719-19f5ee7eed57)
![image](https://github.com/user-attachments/assets/45c796aa-9022-40b3-a465-a6bfe4873bab)
![image](https://github.com/user-attachments/assets/c39cb1ef-0c8a-4776-a3af-6bc2dc44feb4)
</br>
</br>

### Alerts

#### Alert: Failure Baseline Threshold Breached

I used the status field to identify failures and structured the SPL query as follows:
```shell
source="windows_server_logs.csv" status="failure" | timechart span=1h count as failures

source="windows_server_logs.csv" status="failure" | bin _time span=1h | stats count as failure_count by _time | where failure_count > 10
```
This query generates a time series chart showing the count of failures each hour. By reviewing the historical data over several days or weeks, I chose the current highest count as the current threshold. I completed the setup and enabled the alert. Now, any time the number of failed Windows activities exceeds the defined threshold within a single hour, an automated email will be sent to VSI’s SOC team for immediate awareness and action.
</br>
![image](https://github.com/user-attachments/assets/31bf07eb-0e8b-4087-8aed-97dfe8ae4f4f)
![image](https://github.com/user-attachments/assets/08dcf0ea-ef45-47be-9d15-783b8bc919c1)
![image](https://github.com/user-attachments/assets/1e4e3369-3bcc-4896-b404-1aa298c75efe)
![image](https://github.com/user-attachments/assets/749d308b-f0de-4dad-b4d5-2dd779993552)
</br>
</br>

#### Alert: Successful Logins Baseline Threshold Breached

I created an alert in Splunk based on the signature ID rather than the signature text. The signature of interest is “An account was successfully logged on,” which is commonly associated with signature ID 4624 in Windows Security logs.
Using the following SPL query, I analyzed historical data to establish a baseline:
```shell
source="windows_server_logs.csv" signature_id=4624 | timechart span=1h count as successful_login

source="windows_server_logs.csv" signature_id=4624 | bin _time span=1h | stats count as successful_login by _time | where successful_login > 21
```
This query displays how often the 4624 event occurs each hour. After reviewing the data over a period of time, I determined that normal logon activity typically ranges between 20–40 successful logons per hour. I set the alert threshold at 21 logons per hour, as this was the current highest count in the logs and any breach would indicate a suspicious activity.
</br>
![image](https://github.com/user-attachments/assets/6b17b390-e3ba-4224-a146-e8e426d02769)
![image](https://github.com/user-attachments/assets/8dbdafaf-c7e9-418c-a4be-6324ead72ff0)
![image](https://github.com/user-attachments/assets/411971df-3978-4cd6-b27d-75ade1df3c1a)
![image](https://github.com/user-attachments/assets/2e8f7f2d-457c-4cd6-a2e3-87d5ba79a89e)
</br>
</br>

#### Alert: User Account Deletion Baseline Breached

To monitor for unusual or potentially malicious account deletions, I designed an alert in Splunk using the signature ID for the event “A user account was deleted,” which corresponds to event ID 4726 in Windows Security logs. Using the signature ID ensures reliability, even if the event name changes due to Windows updates.
Using the following SPL query, I reviewed past patterns:
```shell
source="windows_server_logs.csv" signature_id="4726" | timechart span=1h count as account_deletions

source="windows_server_logs.csv" signature_id="4726" | bin _time span=1h | stats count as account_deletion_per_hour by _time | where account_deletion_per_hour > 22
```
I found that the current highest count of account deletions was 22. Therefore, I set a threshold of 22 deletions per hour as the point where the activity becomes suspicious, potentially indicating unauthorized or mass account removals.
</br>
![image](https://github.com/user-attachments/assets/1837e4f4-2b26-4b30-a79b-546538094842)
![image](https://github.com/user-attachments/assets/571316f7-cab7-484f-8ca8-cfc1c31dada3)
![image](https://github.com/user-attachments/assets/be8e17f4-2165-4020-9bec-240a993a3893)
![image](https://github.com/user-attachments/assets/d7cce954-0f9c-435e-99df-a0b630beaac3)
</br>
</br>

### Visualization and Dashboards

#### Signature Fields Over Time

 I created a line chart in Splunk that displays the values of the signature field across hourly intervals. This helps VSI monitor trends and spot unusual spikes or patterns tied to specific log events.
```shell
source="windows_server_logs.csv" | timechart span=1h count by signature
```
![image](https://github.com/user-attachments/assets/f00f7f34-4ed6-4ae5-9231-761ceeefdb66)

</br>

#### User Fields Over Time

To visualize how different users are generating activity over time in the Windows logs, I created a line chart in Splunk based on the user field. This helps VSI track which user accounts are most active and quickly identify abnormal behavior such as sudden spikes in activity for specific users.
```shell
source="windows_server_logs.csv" | timechart span=1h count by user
```
![image](https://github.com/user-attachments/assets/8c412a1d-7afe-4311-9933-430da3658de1)
</br>

#### Signature Fields Over Time

To help VSI quickly understand the distribution of different Windows event signatures, I created a visualization that displays the count of each unique signature in the logs. This provides a clear snapshot of which types of events are most common and can help identify unusual or dominant patterns in system activity.
```shell
source="windows_server_logs.csv" | stats count by signature
```
![image](https://github.com/user-attachments/assets/fb7844a3-e578-4af4-bc08-1295db394efe)
</br>

#### User Fields Over Time

To provide VSI with a clear view of how frequently each user appears in the Windows event logs, I created a visualization in Splunk that illustrates the count of different users. This is useful for identifying which user accounts are generating the most activity—potentially revealing privileged accounts, compromised users, or unexpected behavior.
```shell
source="windows_server_logs.csv" | stats count by user
```
![image](https://github.com/user-attachments/assets/0fb1ba67-3900-4c34-b20e-ec18bdfb9bac)
</br>

#### Password Policy Modification

To illustrate the value of single-value visualizations in quickly highlighting a key metric, I created a radial gauge in Splunk that displays the total number of password policy modification (Event ID 4739) within the current day. This type of visualization is excellent for drawing immediate attention to an important data point, such as a potential spike in unauthorized access attempts.
```shell
source="windows_server_logs.csv" signature_id="4739" |stats count as password_policy_modified
```
![image](https://github.com/user-attachments/assets/556af82b-8ffe-4186-bf5a-8f3f4dde8dad)
</br>

## Apache Logs

#### Upload Apache Server Logs to Splunk

I selected “Add Data” in Splunk, chose the “Upload” method, and selected the windows_server_logs.csv file from the **/splunk/logs/Week-2-Day-3-Logs/** directory. Without changing the source type settings, I clicked “Next,” updated the “Host” field to “apache_server_logs,” and reviewed the settings. After submitting, I saw a success message and clicked “Start Searching” to begin analyzing the data. </br>
![image](https://github.com/user-attachments/assets/d0b66019-ef4b-4355-b455-349cdc6421c1)
![image](https://github.com/user-attachments/assets/7084cf27-8a61-4677-ad38-f3d3f03555a9)
![image](https://github.com/user-attachments/assets/8ce3fd82-f711-46dd-bb6a-9a5dd0e1602d)
</br>

### Reports

#### HTTP Method Usage Summary

To give VSI visibility into the types of HTTP requests made to their web server, I created a report in Splunk that displays a table of the different HTTP methods (such as GET, POST, HEAD, and OPTIONS).
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" |stats count by method |sort - count
```
![image](https://github.com/user-attachments/assets/37738e96-1c92-4551-892b-1da45ebb1322)
![image](https://github.com/user-attachments/assets/e7f64377-c46d-4c76-b142-604709e1dd82)
</br>

#### Top Referring Domains to VSI Web Assets

To help VSI identify potential malicious or suspicious referrers, I created a report in Splunk that displays the top 10 referring domains to VSI’s website. Monitoring referrers provides valuable insight into who is directing traffic to the site—whether it’s legitimate sources, marketing partners, or unexpected and potentially harmful domains.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined"| top limit=10 referer_domain
```
![image](https://github.com/user-attachments/assets/d1bae2b6-f840-4290-a991-6b2704a04352)
![image](https://github.com/user-attachments/assets/59a92908-22ba-4cfd-96da-0db132a5dcbe)
![image](https://github.com/user-attachments/assets/6e9eda64-076b-4056-9d73-3bc5ba956eb8)
</br>

#### HTTP Response Code Summary

To provide VSI with visibility into potential issues or suspicious behavior on their web servers, I created a report in Splunk that shows the count of each HTTP response code. This allows the SOC team to quickly identify unusual patterns—such as spikes in 4xx (client errors) or 5xx (server errors)—that may indicate scanning, misconfigurations, or active attacks.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | stats count by status | sort - count
```
High 403 or 401 codes, which might suggest brute-force attempts or unauthorized access, spikes in 404s, possibly from scanners probing for vulnerabilities, and frequent 500-level errors, which may indicate server misconfigurations or application issues.
![image](https://github.com/user-attachments/assets/96a4e270-7dcf-4014-ac20-b8c7a3dd7098)
![image](https://github.com/user-attachments/assets/a28e1c0a-2347-4aa1-bc4f-aa7a53f377c7)
</br>


### Alerts

#### High Foreign Log Volume Detected (Non-US)

To help VSI detect unusual foreign activity that may signal a security threat, I created a Splunk alert that monitors hourly log volume from countries outside the United States, establishes a baseline, and triggers an alert when activity exceeds the defined threshold.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | iplocation clientip | where Country!="United States" | bin _time span=1h |stats count as foreign_events by _time

source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | iplocation clientip | where Country!="United States" | bin _time span=1h |stats count as foreign_events by _time | where foreign_events > 240
```
![image](https://github.com/user-attachments/assets/19e16826-46b9-4bb6-8fa9-8324e2312dfa)
![image](https://github.com/user-attachments/assets/edc53d9c-cdbf-4631-aee5-c2ecf06f246d)
![image](https://github.com/user-attachments/assets/1b671b0d-b1c8-4f82-be3f-dfce0e2c1cac)
</br>

#### Excessive HTTP POST Requests Detected

To help VSI detect potential misuse of the web server—such as unauthorized data uploads, form abuse, or exploitation attempts—I created a Splunk alert that monitors the hourly count of HTTP POST requests, establishes a baseline, and triggers a notification when that count exceeds a defined threshold.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" method="POST" | timechart span=1h count as http_post_method

source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" method="POST" | bin _time span=1h | stats count as http_post_method | where http_post_method > 14
```
![image](https://github.com/user-attachments/assets/594761a5-8acc-494a-af53-e844081b9b3b)
![image](https://github.com/user-attachments/assets/f9af1ffc-aa69-4f51-a1c9-12f02419a00c)
![image](https://github.com/user-attachments/assets/eb57db1c-6d36-4df0-a04b-2b57eb032966)
</br>

### Visualization and Dashboards

#### HTTP Method Trends Over Time

I created a line chart in Splunk that shows the count of each HTTP method per hour. This helps VSI monitor request types and spot anomalies like sudden spikes in uncommon methods.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | timechart span=1h count by method
```
![image](https://github.com/user-attachments/assets/bb6ade5e-fafe-4ec9-bd36-2f5cee5dd785)
</br>

#### Client IP Geolocation Map

 I created a geographical map in Splunk using the clientip field to determine location. This map offers valuable insights into the geographic distribution of requests, making it easier to detect unexpected foreign access or regional attack patterns.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | iplocation clientip| geostats latfield=lat longfield=lon count by Country
```
![image](https://github.com/user-attachments/assets/8905d49f-4084-4d51-8e55-4385e3570ea2)
</br>

#### URI Access Frequency

 I created a custom visualization that displays the count of different URIs (Uniform Resource Identifiers). This helps identify popular endpoints as well as potentially suspicious or unexpected ones being targeted by users or bots.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | stats count by uri_path | sort - count
```
The result was a visually intuitive breakdown of URI activity, helping VSI’s SOC team quickly spot: </br>
-  Frequently accessed pages </br>
-  Rare or abnormal URIs that might indicate scanning or exploitation attempts </br>
![image](https://github.com/user-attachments/assets/076e22dd-3961-4d14-8579-cc5e0620dcaf)
</br>

#### Top 10 Countries by Log Volume

 I created a bar chart visualization that displays the top 10 countries by log volume. This provides a clear picture of geographic access trends, which can be useful for identifying expected versus suspicious traffic patterns.
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | iplocation clientip | stats count by Country | sort - count | head 10
```
![image](https://github.com/user-attachments/assets/62dbcb96-5fab-4f84-ae7d-b377519b9302)
</br>

#### User Agent Activity Overview

 I created a pie chart visualization that displays the count of different user agents. This is valuable for identifying trends, detecting unusual traffic patterns, or spotting suspicious or outdated clients
```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined" | stats count by useragent | sort - count | head 10
```
To enhance clarity, I applied filters to show only the top 10 user agents, preventing clutter from long or rare strings. Each bar represented a specific browser, bot, or application, and its height reflected its frequency in the logs.
![image](https://github.com/user-attachments/assets/1e2a7d08-a87f-4457-9bde-088c07828958)
</br>

#### GET Requests Guage

 I created a single-value radial gauge visualization that shows the total number of GET requests. This kind of visual is ideal for executive dashboards or security operations centers (SOCs) where immediate awareness is essential.
 ```shell
source="apache_logs.txt" host="apache_server_logs" sourcetype="access_combined"  method=GET | stats  count as get_requests
```
![image](https://github.com/user-attachments/assets/c592bc6d-3adc-49a6-a220-4292b32d2d60)
</br>
