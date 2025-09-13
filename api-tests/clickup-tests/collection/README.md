# ClickUp API Tests - Technical Instructions
Detailed documentation for running and configuring the ClickUp API test collection.

## 📋 Prerequisites

### 1. ClickUp Account
* Create a free account on ClickUp.com
* Navigate to **Settings → Apps**
* Generate **Personal API Token**
* Save the token securely (will be needed for configuration)

### 2. Test Data Preparation

**Template List in ClickUp**
1. Create a **new list** in your Workspace
2. Go to **List Settings → Advanced**
3. Click **"Save as Template"**

*(List ID doesn't require manual notation - tests automatically retrieve template through GET request)*

**Attachment File**
1. Create a test.txt file with any content
2. Place it in an easily accessible folder on your computer
3. Check in Postman **Settings → General → Working Directory** if the path is correctly set
4. File will be used in task attachment tests

## 🚀 Installation and Configuration

**Step 1: Import collection**
Import the collection from the `.json` file or shared link using Import button in Postman.

**Step 2: Create environment - Add required variables:**

| Variable | Value |
|----------|-------|
| clickUpBaseUrl | https://api.clickup.com/api/v2 |
| clickUpApiToken | pk_YOUR_TOKEN_HERE |

Remaining variables are created dynamically during tests and pre-requests - no prior manual addition required.

**Step 3: Activate environment**

**Step 4: Run entire collection**

## ✅ Expected Result
If configured correctly, all tests should pass with 100% success rate. The collection runs approximately 43 requests in ~27 seconds with built-in rate limiting.