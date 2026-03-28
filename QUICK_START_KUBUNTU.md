# Quick Start Guide for Kubuntu Users

## 🚀 Getting Started in 5 Minutes

### Step 1: Open the Files

You now have three files:
1. `mogcdsw-strategic-dashboard.html` - The main dashboard (what users see)
2. `admin-panel.html` - The admin panel (where you update data)
3. `dashboard-data.json` - The data file (optional, for easier updates)

### Step 2: Open Admin Panel in Browser

```bash
# Navigate to your downloads folder
cd ~/Downloads

# Open the admin panel
firefox admin-panel.html
# OR
google-chrome admin-panel.html
```

### Step 3: Update Your Data

In the admin panel:
1. Click on a department card (e.g., "Gender Affairs")
2. Update the numbers:
   - Activities completed
   - Outcome progress percentages
   - Current indicator values
3. Click "💾 Save Department Data"
4. Repeat for all departments

### Step 4: Export the Data

1. Click the "💾 Export Data" tab
2. Click "📥 Download JSON Data File"
3. This saves a file like `dashboard-data-2025-02-02.json`

### Step 5: View the Dashboard

```bash
# Open the main dashboard
firefox mogcdsw-strategic-dashboard.html
```

You'll see all your updated data displayed beautifully!

---

## 📤 Publishing to GitHub Pages (10 Minutes)

### Option A: Using GitHub Website (No Commands)

1. **Create GitHub Account**
   - Go to https://github.com
   - Sign up for free

2. **Create Repository**
   - Click "+" → "New repository"
   - Name: `strategic-dashboard`
   - ✅ Public
   - ✅ Add README
   - Click "Create"

3. **Upload Files**
   - Click "Add file" → "Upload files"
   - Drag these files:
     - `mogcdsw-strategic-dashboard.html`
     - `admin-panel.html`
     - `dashboard-data.json`
   - Click "Commit changes"

4. **Enable GitHub Pages**
   - Go to Settings → Pages
   - Source: "main" branch
   - Click "Save"
   - Wait 2 minutes

5. **Your Dashboard is Live!**
   ```
   https://YOUR-USERNAME.github.io/strategic-dashboard/mogcdsw-strategic-dashboard.html
   ```

### Option B: Using Git Commands (For Advanced Users)

```bash
# Install git
sudo apt update
sudo apt install git

# Configure git (first time only)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Create project folder
mkdir ~/strategic-dashboard
cd ~/strategic-dashboard

# Copy your files here
cp ~/Downloads/*.html .
cp ~/Downloads/*.json .

# Initialize repository
git init
git add .
git commit -m "Initial dashboard"

# Connect to GitHub
git remote add origin https://github.com/YOUR-USERNAME/strategic-dashboard.git
git branch -M main
git push -u origin main
```

---

## 🔄 Regular Update Workflow

### Every Week/Month:

1. **Open Admin Panel**
   ```bash
   firefox ~/strategic-dashboard/admin-panel.html
   ```

2. **Update Department Data**
   - Select department
   - Update numbers
   - Click "Save"
   - Repeat for all departments

3. **Update Budget** (if needed)
   - Click "💰 Budget" tab
   - Update disbursed/utilized amounts
   - Click "Save"

4. **Export Data**
   - Click "💾 Export Data" tab
   - Click "📥 Download JSON"
   - Save the file

5. **Update GitHub** (if hosting online)

   **Via Website:**
   - Go to your GitHub repository
   - Click "Add file" → "Upload files"
   - Upload the new JSON file
   - Replace the old one
   - GitHub Pages updates automatically in 2-5 minutes

   **Via Command Line:**
   ```bash
   cd ~/strategic-dashboard
   git add dashboard-data-*.json
   git commit -m "Monthly update - February 2025"
   git push
   ```

---

## 💡 Pro Tips

### Tip 1: Bookmark the Admin Panel
```bash
# Create a desktop shortcut
ln -s ~/Downloads/admin-panel.html ~/Desktop/Dashboard-Admin.html
```
Now you can double-click from desktop!

### Tip 2: Set Up Auto-Backup
```bash
# Create a backup script
nano ~/backup-dashboard.sh
```

Add this content:
```bash
#!/bin/bash
cp ~/strategic-dashboard/dashboard-data-*.json ~/Dropbox/dashboard-backups/
```

Make it executable:
```bash
chmod +x ~/backup-dashboard.sh
```

### Tip 3: Share the Dashboard Link
Once published on GitHub Pages, you can share the link with anyone:
```
https://YOUR-USERNAME.github.io/strategic-dashboard/mogcdsw-strategic-dashboard.html
```

They can view but cannot edit!

---

## 🔒 Security Notes

### Admin Panel Security:
- The admin panel saves data to your browser's localStorage
- Data is stored locally on your computer only
- No one else can access your admin panel
- When you export JSON and upload to GitHub, that becomes public

### Making Admin Panel Private:
If you host the admin panel on GitHub, anyone can access it!

**Solution**: Keep admin panel on your local computer only. Don't upload it to GitHub.

**Upload to GitHub:**
- ✅ `mogcdsw-strategic-dashboard.html` (main dashboard - public)
- ✅ `dashboard-data.json` (data file - public)
- ❌ `admin-panel.html` (keep private on your computer)

---

## 📱 Mobile Access

The dashboard works on phones and tablets!
Just open the GitHub Pages URL on any device.

The admin panel also works on mobile, but it's easier to use on desktop.

---

## 🆘 Common Issues

### Issue: Dashboard shows old data
**Solution:** Hard refresh the browser
- Press `Ctrl + F5`
- Or `Ctrl + Shift + R`

### Issue: Admin panel data lost after closing browser
**Solution:** Always export JSON file after making changes!

### Issue: GitHub Pages not updating
**Solution:** 
- Wait 5 minutes
- Clear browser cache
- Check GitHub Actions tab for errors

### Issue: Can't push to GitHub (authentication error)
**Solution:** GitHub removed password authentication. Use Personal Access Token:
1. GitHub → Settings → Developer Settings → Personal Access Tokens
2. Generate new token
3. Use token as password when pushing

---

## 📊 Data Structure Quick Reference

### Update Activity Progress:
```json
"activitiesCompleted": 8,     // How many done
"totalActivities": 45          // Total planned
```

### Update Outcome Progress:
```json
"outcomes": [
  {
    "name": "Reduced GBV",
    "progress": 15              // Percentage (0-100)
  }
]
```

### Update Indicators:
```json
"keyIndicators": [
  {
    "name": "Women in Parliament",
    "baseline": "23%",          // Don't change
    "current": "25%",           // UPDATE THIS
    "target": "40%"             // Don't change
  }
]
```

### Update Budget:
```json
"budget": {
  "disbursed": 12000000,        // UPDATE THIS
  "utilized": 8500000           // UPDATE THIS
}
```

---

## 🎯 Next Steps

Choose your workflow:

### Beginner Path:
1. ✅ Use admin panel locally
2. ✅ Export JSON monthly
3. ✅ Upload to GitHub via website
4. ✅ Share dashboard link

### Advanced Path:
1. ✅ Learn basic Git commands
2. ✅ Use command line for updates
3. ✅ Set up auto-backup script
4. ✅ Integrate with Google Sheets (ask me!)

### Enterprise Path:
1. ✅ Set up Firebase database
2. ✅ Multiple users with login
3. ✅ Real-time syncing
4. ✅ Mobile app (ask me!)

---

## 🙋 Need More Help?

I can create:
1. **Video tutorial** (with screenshots for each step)
2. **Google Sheets integration** (update from Excel-like interface)
3. **Automatic email reports** (weekly progress emails)
4. **PDF export feature** (download dashboard as PDF)
5. **Excel import** (upload Excel file to update data)

Just let me know what would be most helpful!

---

## 📞 Quick Commands Reference

```bash
# Open admin panel
firefox ~/Downloads/admin-panel.html

# Open dashboard
firefox ~/Downloads/mogcdsw-strategic-dashboard.html

# Update GitHub (from project folder)
cd ~/strategic-dashboard
git add .
git commit -m "Update data"
git push

# Create backup
cp dashboard-data-*.json ~/Backups/
```

---

**Last Updated:** February 2, 2025  
**Version:** 1.0
