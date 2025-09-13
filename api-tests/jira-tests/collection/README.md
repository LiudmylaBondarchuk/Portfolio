# Jira Cloud API Tests - Technical Instructions

Detailed documentation for running and configuring the Jira Cloud API test collection.

---

## 📋 Prerequisites

1. **Jira Cloud Account**
    - Create a free account on [Atlassian.com](https://www.atlassian.com/)  
    - Log in to [API Tokens](https://id.atlassian.com/manage-profile/security/api-tokens)  
    - Click **Create API token**  
    - Give your token a name and click **Create**  
    - Copy the token and save it securely (you can't retrieve it later)  

2. **Access Data**
    - **Email** – email address used to log in to Jira  
    - **Base URL** – URL of your Jira instance  
    - **API Token** – generated in the previous step  

---

## 🚀 Installation and Configuration

### Step 1: Import collection
Import the collection from the `.json` file or shared link using the **Import** button in Postman.

### Step 2: Create environment
Add required variables:

| Variable      | Value                                         |
|---------------|-----------------------------------------------|
| jiraBaseUrl   | `https://YOUR-INSTANCE.atlassian.net/rest/api/3` |
| jiraApiToken  | `YOUR_API_TOKEN`                              |
| jiraEmail     | `your-email@domain.com`                       |

> Remaining variables are created dynamically during tests and pre-requests – no prior manual addition required.

### Step 3: Activate environment
Select the newly created environment in Postman before running the collection.

### Step 4: Run entire collection
Execute the collection using Postman's **Run** button.

---

## ✅ Expected Result

If configured correctly:  
- Tests should pass with **98.3% success rate**  
- The collection runs approximately **98 requests** in ~1m 37s with built-in rate limiting  

**Execution Metrics:**  
- 117 integration tests  
- 98 API requests


