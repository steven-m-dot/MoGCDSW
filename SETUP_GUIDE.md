# MoGCDSW Strategic Plan Dashboard - Setup Guide for Kubuntu

## Table of Contents
1. [Local Setup on Kubuntu](#local-setup-on-kubuntu)
2. [How to Update Dashboard Data](#how-to-update-dashboard-data)
3. [Hosting on GitHub Pages](#hosting-on-github-pages)
4. [Advanced: Setting Up a Data Management System](#advanced-setting-up-a-data-management-system)

---

## Local Setup on Kubuntu

### Option 1: Simple - Just Open in Browser (Recommended for Start)

1. **Locate the file**
   ```bash
   cd ~/Downloads  # or wherever you saved the file
   ```

2. **Open in Firefox/Chrome**
   ```bash
   firefox mogcdsw-strategic-dashboard.html
   # OR
   google-chrome mogcdsw-strategic-dashboard.html
   ```

That's it! The dashboard will open and work immediately.

### Option 2: Set up a Local Web Server (Better for Development)

1. **Install a simple HTTP server**
   ```bash
   # Python method (Python is pre-installed on Kubuntu)
   cd ~/path/to/dashboard/folder
   python3 -m http.server 8000
   ```

2. **Open in browser**
   ```
   http://localhost:8000/mogcdsw-strategic-dashboard.html
   ```

3. **Alternative: Using Node.js**
   ```bash
   # Install Node.js if not installed
   sudo apt update
   sudo apt install nodejs npm
   
   # Install http-server globally
   sudo npm install -g http-server
   
   # Run server
   cd ~/path/to/dashboard/folder
   http-server -p 8000
   ```

---

## How to Update Dashboard Data

### Method 1: Direct Editing (Simple, Manual)

1. **Open the HTML file in a text editor**
   ```bash
   kate mogcdsw-strategic-dashboard.html
   # OR
   nano mogcdsw-strategic-dashboard.html
   # OR use any text editor you prefer
   ```

2. **Find the data section** (around line 27)
   Look for the `strategicData` object that starts with:
   ```javascript
   const strategicData = {
       overview: {
   ```

3. **Update the values**
   
   **Example: Updating Gender Affairs Progress**
   ```javascript
   {
       id: 'gender',
       name: 'Gender Affairs',
       color: '#E91E63',
       outcomes: [
           { 
               name: 'Reduced Gender Based Violence', 
               progress: 15,  // CHANGE THIS NUMBER (0-100)
               target: 100 
           },
           // ... more outcomes
       ],
       keyIndicators: [
           { 
               name: 'Women experiencing violence', 
               baseline: '34%', 
               current: '32%',  // UPDATE THIS
               target: '10%' 
           },
           // ... more indicators
       ],
       activitiesCompleted: 8,  // UPDATE THIS
       totalActivities: 45
   }
   ```

4. **Save and refresh browser** - Changes appear immediately!

### Method 2: Using a Separate Data File (Recommended for Easy Updates)

I'll create an improved version where data is in a separate JSON file:

**Create a new file: `dashboard-data.json`**
```json
{
  "overview": {
    "currentYear": 2025,
    "totalYears": 7
  },
  "departments": [
    {
      "id": "gender",
      "name": "Gender Affairs",
      "color": "#E91E63",
      "activitiesCompleted": 8,
      "totalActivities": 45,
      "outcomes": [
        {
          "name": "Reduced Gender Based Violence",
          "progress": 15
        }
      ],
      "keyIndicators": [
        {
          "name": "Women experiencing violence",
          "baseline": "34%",
          "current": "32%",
          "target": "10%"
        }
      ]
    }
  ]
}
```

**Then update only this JSON file** - much easier!

### Method 3: Create a Simple Update Form (Advanced)

I can create an HTML form where you input data through a user interface instead of editing code.

---

## Hosting on GitHub Pages

### Step 1: Install Git (if not already installed)
```bash
sudo apt update
sudo apt install git
```

### Step 2: Create a GitHub Account
Go to https://github.com and create a free account if you don't have one.

### Step 3: Create a New Repository

1. **On GitHub website:**
   - Click "+" → "New repository"
   - Name: `mogcdsw-strategic-dashboard`
   - Description: "Strategic Plan Implementation Dashboard 2024-2030"
   - Make it **Public**
   - ✅ Check "Add a README file"
   - Click "Create repository"

### Step 4: Upload Your Dashboard

**Option A: Using GitHub Web Interface (Easiest)**
1. In your repository, click "Add file" → "Upload files"
2. Drag and drop `mogcdsw-strategic-dashboard.html`
3. Click "Commit changes"

**Option B: Using Git Command Line**
```bash
# Navigate to your dashboard folder
cd ~/path/to/dashboard

# Initialize git (first time only)
git init

# Add your GitHub repository as remote
git remote add origin https://github.com/YOUR-USERNAME/mogcdsw-strategic-dashboard.git

# Add files
git add mogcdsw-strategic-dashboard.html

# Commit
git commit -m "Initial dashboard upload"

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 5: Enable GitHub Pages

1. **In your repository on GitHub:**
   - Click "Settings" tab
   - Scroll to "Pages" in left sidebar
   - Under "Source", select "main" branch
   - Click "Save"

2. **Wait 2-5 minutes**, then your dashboard will be live at:
   ```
   https://YOUR-USERNAME.github.io/mogcdsw-strategic-dashboard/mogcdsw-strategic-dashboard.html
   ```

### Step 6: Rename for Cleaner URL (Optional)
Rename the file to `index.html` so the URL becomes:
```
https://YOUR-USERNAME.github.io/mogcdsw-strategic-dashboard/
```

---

## Advanced: Setting Up a Data Management System

### Option 1: Google Sheets Integration

You can update data in Google Sheets and have the dashboard read from it automatically.

**Steps:**
1. Create a Google Sheet with your data
2. Publish the sheet as CSV
3. Modify dashboard to fetch data from the CSV URL
4. Update the sheet, dashboard updates automatically!

Would you like me to create this version?

### Option 2: Simple Admin Panel

I can create a second HTML page that serves as an "admin panel" where you:
- Click buttons to update progress
- Fill forms to add new activities
- Export updated data

The updated data saves to browser storage or downloads as JSON.

### Option 3: Full Database Solution

For enterprise use with multiple users:
- **Firebase** (Google's free database)
- **Supabase** (Open source alternative)
- Multiple people can update from different computers
- Authentication and access control
- Automatic syncing

---

## Quick Reference: Updating Data

### Most Common Updates You'll Make:

1. **Update Activity Completion**
   ```javascript
   activitiesCompleted: 8,  // Change this number
   totalActivities: 45      // Keep this unless adding new activities
   ```

2. **Update Outcome Progress**
   ```javascript
   { name: 'Reduced GBV', progress: 15 }  // Change 15 to new percentage
   ```

3. **Update Current Indicators**
   ```javascript
   { 
       name: 'Women experiencing violence',
       baseline: '34%',     // Don't change (historical)
       current: '32%',      // UPDATE THIS regularly
       target: '10%'        // Don't change (goal)
   }
   ```

4. **Update Budget**
   ```javascript
   budget: {
       totalBudget: 50000000,
       allocated: 35000000,
       disbursed: 12000000,  // UPDATE THIS
       utilized: 8500000     // UPDATE THIS
   }
   ```

---

## Recommended Workflow for Your Ministry

### Weekly/Monthly Updates:
1. **Collect data** from all departments
2. **Open the HTML file** in Kate/text editor
3. **Update the numbers** in the `strategicData` object
4. **Save the file**
5. **Push to GitHub** (if hosted there)
   ```bash
   git add mogcdsw-strategic-dashboard.html
   git commit -m "Monthly update - January 2025"
   git push
   ```
6. **GitHub Pages automatically updates** in 2-5 minutes

### Quarterly Reviews:
- Add new milestones
- Update major indicators
- Review overall progress

---

## Troubleshooting

### Dashboard won't open
```bash
# Check file permissions
ls -l mogcdsw-strategic-dashboard.html
# Should show readable permissions

# If not, fix it:
chmod 644 mogcdsw-strategic-dashboard.html
```

### Changes not showing after editing
- Clear browser cache: `Ctrl + F5` (hard refresh)
- Or open in private/incognito window

### Git push asks for password
```bash
# Set up SSH key or use Personal Access Token
# GitHub removed password authentication
# See: https://docs.github.com/en/authentication
```

---

## Next Steps - Choose Your Path

### Path 1: Simple & Quick
✅ Use the dashboard as-is  
✅ Update by editing HTML file manually  
✅ Host on GitHub Pages  
**Good for: Getting started quickly**

### Path 2: Easier Updates
✅ Use the dashboard with separate JSON data file  
✅ Only edit JSON (simpler format)  
✅ Host on GitHub Pages  
**Good for: Regular updates by multiple people**

### Path 3: Professional Setup
✅ Dashboard with admin panel  
✅ Cloud database (Firebase/Supabase)  
✅ Multiple users with login  
✅ Automatic data syncing  
**Good for: Long-term institutional use**

---

## Need Help?

Let me know which path you'd like to take, and I can:
1. Create the separate JSON data file version
2. Build an admin panel for easy updates
3. Set up the Firebase/database integration
4. Create documentation for your team
5. Add export features (PDF reports, Excel downloads, etc.)

Would you like me to create any of these enhanced versions?
