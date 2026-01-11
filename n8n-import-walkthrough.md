# n8n Workflow Import Walkthrough

This guide explains how to copy the workflow JSON and import it into n8n.

---

## 📋 What This Workflow Does

The **LinkedIn Job Scraper** workflow:
- Accepts a resume via a web form
- Uses AI to analyze the resume and recommend suitable job roles
- Searches LinkedIn for matching jobs
- Analyzes each job against your resume
- Generates a match score and cover letter
- Saves all results to Google Sheets

---

## 🚀 How to Import the Workflow to n8n

### Step 1: Copy the JSON

1. Open the workflow JSON file (`test.json`) in any text editor (VS Code, Notepad++, etc.)
2. Select **all the content** in the file:
   - **Windows/Linux**: Press `Ctrl + A`
   - **Mac**: Press `Cmd + A`
3. Copy the selected content:
   - **Windows/Linux**: Press `Ctrl + C`
   - **Mac**: Press `Cmd + C`

> [!TIP]
> Make sure you copy the **entire file content**, including the opening `{` and closing `}` braces.

---

### Step 2: Save the JSON File (if needed)

If you have the JSON content but need to save it as a file:

1. Open a text editor (Notepad, VS Code, etc.)
2. Paste the JSON content (`Ctrl + V` or `Cmd + V`)
3. Save the file:
   - **File** → **Save As**
   - Choose a location (e.g., Desktop)
   - Name the file with `.json` extension (e.g., `my-workflow.json`)
   - Set **"Save as type"** to **"All Files (*.*)"** if using Notepad
4. Click **Save**

> [!IMPORTANT]
> The file **must** have a `.json` extension for n8n to recognize it properly.

---

### Step 3: Open n8n

1. Launch your n8n instance:
   - **Self-hosted**: Navigate to your n8n URL (e.g., `http://localhost:5678`)
   - **n8n Cloud**: Go to [https://app.n8n.cloud](https://app.n8n.cloud)
2. Log in with your credentials

---

### Step 4: Import the Workflow

There are **two methods** to import:

#### Method A: Import from Clipboard (Paste JSON Directly)

1. In n8n, go to the **Workflows** section from the left sidebar
2. Click the **"+"** button or **"Add Workflow"** to create a new workflow
3. On the empty canvas, right-click anywhere
4. Select **"Import from JSON"** or **"Paste from clipboard"**
5. Paste your copied JSON (`Ctrl + V` or `Cmd + V`)
6. The workflow will appear on the canvas

#### Method B: Import from File

1. In n8n, go to the **Workflows** section from the left sidebar
2. Click the **three dots menu (⋮)** in the top-right corner
3. Select **"Import from File"**
4. Browse to your saved `.json` file and select it
5. Click **Open** or **Import**
6. The workflow will be imported and appear in your workflow list

---

### Step 5: Configure Credentials

After importing, you'll need to set up the required credentials:

| Node | Credential Required |
|------|---------------------|
| Google Gemini Chat Model | Google Gemini (PaLM) API Key |
| Google Sheets | Google Sheets OAuth2 |

**To configure credentials:**

1. Click on any node that shows a warning icon (⚠️)
2. In the node settings, find the **Credentials** section
3. Click **"Create New"** or select an existing credential
4. Follow the authentication steps:
   - **Google Gemini**: Paste your API key from [Google AI Studio](https://aistudio.google.com/app/apikey)
   - **Google Sheets**: Complete the OAuth login flow

> [!WARNING]
> The workflow will **not run** until all credentials are properly configured.

---

### Step 6: Update the Google Sheet URL

1. Find the **"Append or update row in sheet1"** node
2. Click on it to open settings
3. Update the **Document ID** to your own Google Sheet URL
4. Make sure your sheet has these columns:
   - Link (using to match)
   - Title
   - Company
   - Location
   - Score
   - Cover Letter
   - Skills
   - Improvements

---

### Step 7: Activate and Test

1. Click the **"Save"** button (top-right corner)
2. Toggle the workflow to **Active** using the switch in the top-right
3. To test:
   - Click **"Test Workflow"** or run a manual test
   - For the Form Trigger, visit the form URL shown in the node

---

## 🔧 Troubleshooting

| Issue | Solution |
|-------|----------|
| Import fails with JSON error | Ensure you copied the complete JSON (all braces match) |
| Nodes show red/warning | Configure missing credentials |
| Workflow doesn't trigger | Make sure the workflow is set to **Active** |
| Google Sheets error | Verify OAuth permissions and sheet access |

---

## 📁 File Reference

The workflow JSON file is located at:
```
c:\Users\sushu\OneDrive\Desktop\Workflows\test.json
```

---

> [!NOTE]
> After importing, customize the workflow to match your specific requirements, such as changing the job search parameters or modifying the AI prompts.
