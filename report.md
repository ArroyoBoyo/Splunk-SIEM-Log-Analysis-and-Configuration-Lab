# Splunk SIEM Foundations Lab Report

## Project Overview
This project documents the steps I took in a foundational SIEM lab using Splunk Enterprise in a Windows 11 virtual machine environment. The goal of the lab was to configure and analyze Windows log ingestion, explore and analyze event data, create a basic alert for suspicious failed logon activity, and build a dashboard to improve visibility into authentication and system events. However, the main focus is to demonstrate practical familiarity with SIEM technology before moving into more advanced projects focused on specific threat monitoring, like phishing and incident investigations. Let's get into it!

## Lab Setup and Log Ingestion

I built the lab in a Windows 11 virtual machine using VirtualBox and chose Splunk Enterprise as my primary SIEM platform. After confirming that the platform was accessible and functioning properly via services.msc, I configured log ingestion for 4 core Windows log sources, including the Application, Security, System, and Setup logs. The focus of the project was not just to bring data into Splunk, but to understand what that data represented and how it could be used in a monitoring context.

<img width="1556" height="590" alt="03-screenshot-DataSelection" src="https://github.com/user-attachments/assets/99bd3530-b2ad-4ecd-8021-75d2dcca922a" />

Once the log sources were added, I validated that the data was being successfully ingested and that Splunk could search across the available events. This part of the project was important because it established the core of the SIEM workflow, which is collecting data, normalizing visibility, and ensuring that useful logs are available for analysis. This is where the real fun starts.

<img width="2531" height="1067" alt="04-screenshot-DataSourceInfo" src="https://github.com/user-attachments/assets/b9457fa3-4905-420e-811b-52aa793c06fd" />

## Log Analysis and Investigation Focus

Although multiple Windows log sources were ingested, I chose to focus primarily on Windows Security logs because they provided the most data and a clear path into security-relevant events. This made the lab more meaningful from a SOC perspective, in my opinion, since Security logs contain authentication events, user activity, and other data that are commonly analyzed in a SOC environment.

From there, I used Splunk searches to explore event activity and better understand how Windows Security events appear within the platform. I focused particularly on logon events (EventCode 4624), repeated authentication failures (EventCode 4625), and process-related activity (EventCode 4688). 

<img width="1218" height="1055" alt="07-screenshot-AlertCreation" src="https://github.com/user-attachments/assets/7c9b8411-f266-4dfc-9363-0716fb3fad79" />

This helped me understand not only how to retrieve the data, but how to interpret it. Instead of just seeing raw events, I was able to connect those events to specific  security use cases such as suspicious login behavior and increased authentication noise that could warrant analyst review.

<img width="854" height="936" alt="06-screenshot-FailedLoginAttempts" src="https://github.com/user-attachments/assets/80074b49-1a51-4ee3-9feb-7b9113b63d9c" />

## Alert Creation and Monitoring Value

After reviewing the log data manually, it was obvious that the current setup was far too inefficient for my selected focus of authentication-related alerts. Therefore, I created a basic alert for suspicious failed login activity, specifically targeting failed login attempts via EventCode 4625. The purpose of this was to show how security events can move from simple logs to actual monitoring logic. In other words, rather than only searching for failed logons after the fact, I used Splunk to create a real-time alert that highlights suspicious behavior when it occurs.

<img width="1218" height="1055" alt="07-screenshot-AlertCreation" src="https://github.com/user-attachments/assets/a829a5c0-718e-4033-8954-22f686e2f5b3" />

This was an important step in the project because it showed the transition from passive analysis to active monitoring. Even though the alert itself was intentionally simple, it reflected a key SIEM concept: identifying useful security events and operationalizing them in a way that improves visibility for future review. For a foundational project, this was enough to demonstrate that I understand how SIEM tools support both event analysis and alerting workflows.

<img width="2508" height="466" alt="08-screenshot-AlertTriggered" src="https://github.com/user-attachments/assets/160a6b0e-6587-4848-831f-31b1bfd2f432" />

## Dashboard Development

To make the data easier to review and more useful from a monitoring standpoint, I built a dashboard focusing on these specific Windows security events. The dashboard was designed to improve visibility into the authentication-related activity mentioned earlier in the report, and make it easier to track failed logon behavior and other important event patterns without relying entirely on raw searches.

Building the dashboard helped reinforce one of the most practical lessons from this lab. SIEM tools are not only useful for storing logs, but also for organizing and presenting that data in a way that improves efficiency. Instead of treating Splunk purely as a search engine, this part of the project showed how dashboards can make recurring or high-interest data easier to monitor and review in a structured format.

<img width="2510" height="1065" alt="09-screenshot-dashboard" src="https://github.com/user-attachments/assets/91d75adc-3c6b-4335-90a7-8bd384783bdb" />

## Key Findings and Takeaways

The most valuable takeaway from this project was gaining a better understanding of how Windows event data is collected, surfaced, and interpreted inside a SIEM platform. I was able to work through the full foundational workflow of setting up Splunk, ingesting logs, validating the data, exploring event activity, and turning a useful event type into both an alert and a dashboarded monitoring view.

This lab also helped clarify the difference between simply having logs and actually using them in a meaningful way. Not to mention clarity into what Application, System, and Security logs actually track within the Windows system. By focusing on failed logon activity and Windows Security events, I was able to connect raw log data to a real monitoring use case. It only gets more fun from here!
