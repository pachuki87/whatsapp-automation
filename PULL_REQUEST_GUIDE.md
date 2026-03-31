# 📝 Pull Request Guide - WhatsApp Automation Plugin

## 🎯 Summary
This plugin provides full WhatsApp Web automation with persistent Chrome sessions in headless mode for Agent Zero.

## 📋 File Structure

### 1. Plugin Repository (GitHub)
```
whatsapp_automation/
├── plugin.yaml           # Plugin metadata
├── README.md             # Complete documentation
├── CONTRIBUTING.md        # Contribution guide
├── PULL_REQUEST_GUIDE.md # This file
└── scripts/
    ├── install.sh                   # Installation script
    ├── start_whatsapp_persistent.sh  # Start persistent Chrome
    ├── check_persistence.sh          # Verify persistence
    └── monitor_chrome.sh            # Monitor Chrome
```

### 2. Directory for PR to a0-plugins
```
a0-plugins-submit/
└── plugins/
    └── whatsapp_automation/
        └── index.yaml    # Metadata for the index
```

## ✅ Specification Verification

### a0-plugins Requirement Compliance:
- ✅ Plugin name matches between folder and plugin.yaml: `whatsapp_automation`
- ✅ Title: "WhatsApp Automation" (20 characters, max 50)
- ✅ Description: clear and concise (less than 500 characters)
- ✅ GitHub URL: points to the plugin repository
- ✅ Tags: 5 tags (max 5)
- ✅ index.yaml: 592 bytes (max 2000)
- ✅ Only one plugin per PR

### Content of index.yaml:
```yaml
title: "WhatsApp Automation"
description: "Full WhatsApp Web automation with persistent Chrome sessions in headless mode. Allows sending messages, reading conversations and monitoring chats without needing to scan QR every time."
github: "https://github.com/agent0ai/whatsapp-automation"
tags:
  - whatsapp
  - automation
  - chrome
  - headless
  - persistence
```

## 🚀 Steps for the Pull Request

### Step 1: Create the Plugin Repository

1. Create a new repository on GitHub: `https://github.com/agent0ai/whatsapp-automation`
2. Upload all plugin files:
   ```bash
   cd /a0/usr/workdir/whatsapp_automation_plugin/
   git init
   git add .
   git commit -m "Initial commit: WhatsApp Automation Plugin v1.0.0"
   git branch -M main
   git remote add origin https://github.com/agent0ai/whatsapp-automation.git
   git push -u origin main
   ```

### Step 2: Fork the a0-plugins Repository

1. Go to: https://github.com/agent0ai/a0-plugins
2. Fork the repository

### Step 3: Create PR Structure

1. Clone your a0-plugins fork:
   ```bash
   git clone https://github.com/YOUR_USER/a0-plugins.git
   cd a0-plugins
   ```

2. Create the plugin structure:
   ```bash
   mkdir -p plugins/whatsapp_automation
   cp /a0/usr/workdir/a0-plugins-submit/plugins/whatsapp_automation/index.yaml plugins/whatsapp_automation/
   ```

3. Verify content:
   ```bash
   cat plugins/whatsapp_automation/index.yaml
   ```

### Step 4: Commit and Push

```bash
git add plugins/whatsapp_automation/
git commit -m "Add WhatsApp Automation plugin"
git push origin main
```

### Step 5: Create Pull Request

1. Go to: https://github.com/agent0ai/a0-plugins
2. Click on "Pull Requests"
3. Click on "New Pull Request"
4. Select your fork and branch
5. PR Title: `Add WhatsApp Automation Plugin`
6. Description:
   ```markdown
   ## Description
   
   This plugin provides full WhatsApp Web automation with persistent Chrome sessions in headless mode for Agent Zero.
   
   ## Features
   
   - Persistent WhatsApp Web session (survives reboots)
   - Docker container compatible
   - Headless Chrome without graphical interface
   - Installation and maintenance scripts
   - Integration with Chrome DevTools MCP
   
   ## Documentation
   
   - README.md with complete documentation
   - Automation scripts in /scripts/
   - Usage examples with Agent Zero
   - Detailed Troubleshooting
   
   ## Validation
   
   - ✅ Plugin name matches: whatsapp_automation
   - ✅ Title < 50 characters
   - ✅ Description < 500 characters
   - ✅ Valid GitHub URL
   - ✅ 5 tags (maximum allowed)
   - ✅ index.yaml < 2000 characters
   
   ## Links
   
   - Plugin repository: https://github.com/agent0ai/whatsapp-automation
   ```

7. Click on "Create Pull Request"

## 🔍 Automatic Validation

The a0-plugins CI will automatically verify:
- Correct folder structure
- Plugin name matches plugin.yaml
- Required fields present in index.yaml
- Length limits met
- Valid GitHub URL

## 📝 Human Review

After passing automatic validation, the PR will be reviewed by an Agent Zero maintainer.

## ✨ Expected Result

If the PR is approved:
- The plugin will appear in the a0-plugins index
- Users will be able to install it easily
- The Agent Zero community will have access to WhatsApp automation

---

**Thank you for contributing to the Agent Zero community! 🎉**
