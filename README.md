# 🔐 Defender Secure Score → Slack Notifications (Logic App)

This repository provides a production-ready Azure Logic App (Consumption) template that monitors Microsoft Defender Secure Score (Identity controls) and sends actionable notifications to Slack for controls that are not fully implemented.

The solution is designed to be easily deployable across tenants using a standard Deploy to Azure experience and follows best practices for parameterization, portability, and managed identity authentication.

## 🎯 What this solution does
Queries Microsoft Graph Security API for Secure Score data
Filters Identity-related controls
Identifies controls with score < 100% (pending remediation)
Enriches each control with additional metadata
Sends structured notifications to a Slack channel

This enables security teams to:

Track identity posture gaps continuously
Drive remediation actions proactively
Integrate Microsoft security signals into collaboration workflows
##⚙️ Key Features
Fully parameterized ARM template for cross-tenant deployment
Uses System Assigned Managed Identity (no secrets stored)
Designed for customer environments (multi-tenant ready)
Minimal dependencies (only Slack connection required)
Daily scheduled execution (configurable)
## 🧩 Architecture Overview
Trigger
Daily recurrence (configurable)
Data Collection
Calls Microsoft Graph:
/security/secureScores
/security/secureScoreControlProfiles
Processing
Filters:
Identity category
Score < 100%
Notification
Sends formatted message to Slack via API connection
## 🚀 Deployment

Click below to deploy directly to your Azure subscription:

## 📋 Prerequisites

Before deployment:

An Azure subscription with permissions to deploy resources
A Slack API connection created in the target subscription
Required permissions granted to the Logic App Managed Identity for Microsoft Graph (Security APIs)
## 🔧 Post-deployment steps
Authorize the Slack connection (if not already authenticated)
Assign required Microsoft Graph permissions to the Logic App identity
Validate the workflow run from the Logic App portal
## 🧠 Use Cases
Continuous monitoring of Identity security posture
SOC / SecOps notification pipelines
Integration of Defender signals into collaboration tools
Lightweight alternative to full SIEM alerting for posture tracking
## ⚠️ Notes
Slack channel ID must be provided during deployment
Microsoft Graph beta endpoints are currently used
Connection authentication is tenant-specific and must be completed in the destination environment
## 📦 Repository Contents
azuredeploy.json → Main ARM template
azuredeploy.parameters.json → Sample parameter file
README.md → Documentation and deployment instructions
