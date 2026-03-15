# Claude Models Missing in VS Code - Fix Guide

## 🚨 Issue: Claude Models Disappeared from VS Code

If Claude models (like Claude Sonnet) were previously available in your VS Code GitHub Copilot but have now disappeared, showing "Contact your admin" or not appearing in the model list at all, this guide will help you restore access.

### The Situation

You mention that:
- ✅ Claude models work for you in the web interface (like this conversation)
- ❌ Claude models are missing from your VS Code GitHub Copilot
- ✅ Your friends with student accounts can access Claude in VS Code through Copilot
- 📸 Previously, these models were visible in your VS Code

**This suggests the models should be available to you, but something has changed.**

## 🚀 One-Command Terminal Fix

**Try this first!** Close VS Code completely, then run this command in your terminal:

### For macOS:
```bash
rm -rf ~/Library/Application\ Support/Code/Cache/* ~/Library/Application\ Support/Code/CachedData/* && killall "Visual Studio Code" 2>/dev/null; code
```

**Note for macOS users:** If your shell asks "sure you want to delete all the files?" - type `y` and press Enter. This is safe - it only deletes VS Code's cache files (temporary data), not your settings or extensions.

### For Linux:
```bash
rm -rf ~/.config/Code/Cache/* ~/.config/Code/CachedData/* && killall code 2>/dev/null; code
```

### For Windows (PowerShell - Run as Administrator):
```powershell
Stop-Process -Name "Code" -Force -ErrorAction SilentlyContinue; Remove-Item -Path "$env:APPDATA\Code\Cache\*" -Recurse -Force; Remove-Item -Path "$env:APPDATA\Code\CachedData\*" -Recurse -Force; Start-Process code
```

**What this does:**
1. Clears VS Code cache (where corrupted model data might be stored)
2. Kills any running VS Code processes
3. Restarts VS Code with a fresh cache

**Is it safe?** Yes! The cache contains only temporary files that VS Code will recreate. Your settings, extensions, and code are NOT affected.

After VS Code reopens:
1. Sign in to GitHub Copilot again (if prompted)
2. Check the model selector - Claude models should now appear

If this doesn't work, try the detailed fixes below.

---

## Quick Fixes (Try These First)

### Fix 1: Reload VS Code Window
1. Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
2. Type "Developer: Reload Window"
3. Press Enter
4. Check if Claude models reappear in Copilot

### Fix 2: Sign Out and Sign Back In
1. Open VS Code
2. Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux)
3. Type "GitHub Copilot: Sign Out"
4. Confirm sign out
5. Restart VS Code
6. Sign back in to GitHub Copilot
7. Verify your GitHub student account is connected

### Fix 3: Check Copilot Extension Version
1. Go to Extensions (Cmd+Shift+X or Ctrl+Shift+X)
2. Search for "GitHub Copilot"
3. Click the gear icon → "Install Another Version"
4. Try the latest version or roll back to a previous version if issues started recently
5. Restart VS Code

### Fix 4: Clear VS Code Cache
```bash
# Close VS Code first, then run:

# On macOS:
rm -rf ~/Library/Application\ Support/Code/Cache/*
rm -rf ~/Library/Application\ Support/Code/CachedData/*

# On Linux:
rm -rf ~/.config/Code/Cache/*
rm -rf ~/.config/Code/CachedData/*

# On Windows (PowerShell):
Remove-Item -Path "$env:APPDATA\Code\Cache\*" -Recurse -Force
Remove-Item -Path "$env:APPDATA\Code\CachedData\*" -Recurse -Force
```
Then restart VS Code.

### Fix 5: Verify GitHub Education Status
1. Go to https://education.github.com/benefits
2. Verify your GitHub Student Developer Pack is active
3. Check that GitHub Copilot is listed as an available benefit
4. If expired, renew your student verification

### Fix 6: Update GitHub Copilot Settings
1. Open VS Code Settings (Cmd+, or Ctrl+,)
2. Search for "copilot"
3. Look for model-related settings
4. Try toggling "GitHub Copilot: Enable" off and back on
5. Check for any "model selection" or "advanced model" settings

### Fix 7: Reinstall GitHub Copilot Extension
1. Uninstall GitHub Copilot extension completely
2. Uninstall GitHub Copilot Chat extension (if installed)
3. Restart VS Code
4. Reinstall both extensions from the marketplace
5. Sign in again with your student GitHub account

## Understanding the Issue

### Why This Happens

Model availability in VS Code can change due to:
- **Extension updates** - New versions may change model access
- **Authentication token expiration** - Your session may need refresh
- **GitHub policy changes** - Student benefits may have been updated
- **Cache corruption** - Stale cache can hide available models
- **Network/proxy issues** - May prevent model list from loading
- **Regional restrictions** - Some regions may have different model access

### Important Context

Based on your situation:
- **GitHub Copilot for Students** may include Claude models through a partnership
- **Web access works** suggests your account has proper permissions
- **Friends have access** confirms this should work for you too
- **Recently disappeared** indicates a local VS Code issue, not an account problem

## Advanced Troubleshooting

### Check Copilot Status in VS Code
1. Look at the bottom-right status bar in VS Code
2. You should see a Copilot icon
3. Click it to see status and model options
4. If no models appear, there's a connection issue

### Verify Network Connectivity
```bash
# Test connection to GitHub Copilot services
curl -I https://api.github.com/copilot_internal/v2/token

# Test connection to Anthropic (if using direct Claude)
curl -I https://api.anthropic.com/
```

### Check VS Code Output Logs
1. Go to View → Output
2. Select "GitHub Copilot" from the dropdown
3. Look for error messages about models or authentication
4. Select "GitHub Copilot Chat" for chat-specific logs

### Enable Verbose Logging
1. Add to VS Code settings.json:
```json
{
  "github.copilot.advanced": {
    "debug.overrideEngine": "",
    "debug.testOverrideProxyUrl": "",
    "debug.overrideProxyUrl": ""
  }
}
```
2. Restart VS Code
3. Check Output logs for more details

## Still Not Working? Try These

### Option A: Use GitHub Copilot Chat
If models appear in Chat but not in autocomplete:
1. Install "GitHub Copilot Chat" extension
2. Open the chat panel (Cmd+Shift+I or Ctrl+Shift+I)
3. You might be able to select Claude models there

### Option B: Contact GitHub Education Support
Since this is student account related:
1. Go to https://support.github.com/
2. Select "Education" as the category
3. Explain that Claude models disappeared from Copilot
4. Mention your friends with student accounts have access
5. Provide your screenshot showing the models before

### Option C: Check University/Institution
1. Some institutions have special GitHub partnerships
2. Contact your university's GitHub administrator
3. They may need to reactivate your access
4. Your student email verification might need renewal

## Comparing Access Points

| Feature | Web (This Conversation) | VS Code with Copilot |
|---------|------------------------|----------------------|
| Claude Access | ✅ Working | ❌ Not working for you |
| Your Friends | N/A | ✅ Working |
| Authentication | GitHub account | GitHub student account |

This confirms: **The issue is VS Code-specific, not account-specific.**

## What Your Friends Might Be Doing Differently

Ask your friends to check:
1. Which VS Code version they're using
2. Which GitHub Copilot extension version
3. Whether they had to configure anything special
4. If they're using any specific settings
5. Which region/country they're accessing from

## Expected Behavior (When Working)

When Claude models are properly available in VS Code:
- Models appear in the model selector dropdown
- You can select between GPT models and Claude models
- Both chat and autocomplete work with selected model
- Status bar shows which model is active

## Resources

- **GitHub Education**: https://education.github.com/
- **GitHub Copilot Docs**: https://docs.github.com/en/copilot
- **VS Code GitHub Copilot**: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot
- **GitHub Support**: https://support.github.com/

## Quick Checklist

Before contacting support, verify:
- [ ] VS Code is up to date
- [ ] GitHub Copilot extension is up to date
- [ ] Signed in with correct GitHub account (student account)
- [ ] GitHub Student Developer Pack is active
- [ ] Tried signing out and back in
- [ ] Tried reloading VS Code window
- [ ] Cleared VS Code cache
- [ ] Checked output logs for errors
- [ ] Tested that web access still works (like this conversation)

## Screenshots/Evidence to Collect

When seeking help, provide:
1. Screenshot of your current model selector (showing missing models)
2. Screenshot of your GitHub Education benefits page
3. Screenshot of VS Code Extensions showing Copilot version
4. Output logs from GitHub Copilot (sanitized for privacy)
5. Your previous screenshot showing models were available

---

**Note**: This guide assumes GitHub Copilot for students includes Claude model access based on your report that friends have access. If GitHub policy has changed, some solutions may not restore access, but the troubleshooting steps will help identify if it's a technical issue or a policy change.
