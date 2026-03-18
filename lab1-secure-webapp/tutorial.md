# Lab 1 – Secure Web App with Microsoft Entra ID

## Objective

Deploy a web application in Azure and secure access using Microsoft Entra ID authentication.

This lab demonstrates how identity providers can be used to protect cloud applications.

---

## Architecture

User → Microsoft Entra ID → Azure Web App

Users must authenticate through Microsoft Entra ID before accessing the application.

---

## Step 1 – Create Resource Group

1. Log in to the Azure Portal.
2. Search for **Resource Groups**.
3. Click **Create**.

Configuration example:

Resource Group Name: iam-lab-rg  
Region: Italy North

---

## Step 2 – Deploy Web App

1. Search for **App Services** in the Azure portal.
2. Click **Create Web App**.

Example configuration:

Web App Name: iam-secure-webapp  
Resource Group: iam-lab-rg  
Runtime Stack: .NET / Node.js / Python  
Pricing Tier: Free (F1)

Once deployed the application will be available at:

(https://iam-lab-webapp.azurewebsites.net)

---

## Step 3 – Enable Authentication

1. Open the deployed Web App.
2. Navigate to:

Settings → Authentication

3. Click **Add Identity Provider**.
4. Select **Microsoft Entra ID**.
5. Choose **Create new App Registration**.

Save the configuration.

### Authentication Configuration

![Authentication Settings](screenshots/authentication-config.png)

---

## Step 4 – Test Login

1. Open the web application URL.
2. The application will redirect to the Microsoft login page.
3. Sign in using your Azure account.

After authentication you will be redirected back to the web application.

### Web App Protected by Entra ID

![Web App Running](screenshots/webapp-running.png)

---

## Step 5 – Verify App Registration

1. Navigate to **Microsoft Entra ID**.
2. Open **App Registrations**.
3. Locate the application created for the web app.

Review the authentication settings and permissions.

### App Registration

![App Registration](screenshots/app-registration.png)

---

## Result

The web application is now secured using Microsoft Entra ID authentication.

Only authenticated users can access the application.

---

## Security Concepts Demonstrated

• Identity-based authentication  
• OAuth login using Microsoft Entra ID  
• Application registration  
• Securing applications with centralized identity providers
----


## Identity and Access Control Lab

To simulate a real IAM scenario, multiple users and roles were created in Microsoft Entra ID.

### Users
- app-admin (administrator)
- app-user (standard user)
- app-guest (unauthorized user)

### Groups
- WebApp-Admins
- WebApp-Users

Users were assigned to groups to represent different privilege levels.

### Authentication

The Azure Web App was configured to use Microsoft Entra ID authentication based on OAuth 2.0.

### Token-Based Access

After login, Microsoft Entra ID issues an OAuth token containing user identity and group membership.

The application can use this token to determine user access levels.

### Test Results

- app-user → Access granted
- app-admin → Access granted
- app-guest → No assigned role (restricted scenario)
