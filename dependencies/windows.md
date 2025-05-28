# Windows Development Setup Guide

## Prerequisites
- Windows 10/11
- Administrator access

## Step 1: Install Git

### Option A: Git for Windows (Recommended)
1. Go to [git-scm.com](https://git-scm.com/download/win)
2. Download the 64-bit Git for Windows installer
3. Run installer with these settings:
   - **Select Components**: Check "Git Bash Here" and "Git GUI Here"
   - **Default editor**: Use Visual Studio Code (if installed) or Notepad++
   - **PATH environment**: Select "Git from the command line and also from 3rd-party software"
   - **Line ending conversions**: "Checkout Windows-style, commit Unix-style line endings"
   - **Terminal emulator**: "Use Windows' default console window"

### Option B: Using Winget (Windows Package Manager)
```powershell
# Run PowerShell as Administrator
winget install --id Git.Git -e --source winget
```

## Step 2: Install Node.js

### Option A: Official Installer (Recommended)
1. Go to [nodejs.org](https://nodejs.org/)
2. Download the **LTS version** (not Current)
3. Run installer with default settings
4. **Important**: Check "Automatically install the necessary tools" for native modules

### Option B: Using Winget
```powershell
# Run PowerShell as Administrator
winget install OpenJS.NodeJS.LTS
```

## Step 3: Configure PowerShell

### Fix Execution Policy Issues
```powershell
# Run PowerShell as Administrator
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Verify Installations
```powershell
# Check versions (restart PowerShell first)
node --version
npm --version
git --version
```

## Step 4: Configure Git (First Time Setup)
```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main
```

## Common PowerShell Issues & Fixes

### Issue: "execution of scripts is disabled"
```powershell
# Run as Administrator
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Issue: npm commands fail
```powershell
# Clear npm cache
npm cache clean --force

# Update npm to latest
npm install -g npm@latest
```

### Issue: Path not found after installation
1. Close all PowerShell windows
2. Open new PowerShell window
3. If still not working, restart Windows

### Issue: Permission errors with npm
```powershell
# Set npm prefix to avoid permission issues
npm config set prefix %APPDATA%\npm
```

## Recommended: Install Windows Terminal
1. Install from Microsoft Store: "Windows Terminal"
2. Set as default terminal in Windows 11 Settings

## Test Your Setup
```powershell
# Create test project
mkdir test-project
cd test-project
npm init -y
npm install express
echo "console.log('Hello World')" > app.js
node app.js
```

## Pro Tips
- Always use PowerShell (not Command Prompt)
- Run as Administrator when installing global packages
- Restart PowerShell after installations
- Use `npm list -g --depth=0` to see global packages
