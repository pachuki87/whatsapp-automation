# 🤖 WhatsApp Automation Plugin for Agent Zero

## 📋 Description

Full WhatsApp Web automation plugin with persistent sessions in headless Chrome. Allows sending messages, reading conversations, and monitoring chats without needing to scan the QR code every time.

## ✨ Main Features

### 🔄 **Persistent Session**
- ✅ Keeps session active after system reboots
- ✅ Docker container compatible
- ✅ Works without graphical interface (headless mode)
- ✅ Survives browser closures

### 🤖 **Full Automation**
- 📤 Send messages automatically
- 📥 Read and monitor conversations
- 🔍 Search for specific messages
- 📊 Extract conversation data
- 🎯 Create custom bots

### 🛠 **Agent Zero Integration**
- 🔗 Native Chrome DevTools MCP
- 📝 Automated bash scripts
- 🎯 Easy workflow integration
- 📈 Real-time monitoring

## 🚀 Installation

### **Prerequisites**

- ✅ Agent Zero v1.0.0 or higher
- ✅ Google Chrome or Chromium installed
- ✅ Root or sudo permissions
- ✅ Access to port 9222
- ✅ Minimum 500MB of disk space

### **Automatic Installation**

```bash
# 1. Clone the repository
git clone https://github.com/agent0ai/whatsapp-automation.git
cd whatsapp-automation

# 2. Run installation script
chmod +x scripts/install.sh
./scripts/install.sh

# 3. Verify installation
./scripts/check_persistence.sh
```

### **Manual Installation**

```bash
# 1. Create persistent directory
mkdir -p /a0/usr/workdir/chrome-profile/
chmod -R 755 /a0/usr/workdir/chrome-profile/

# 2. Verify Chrome installation
google-chrome --version

# 3. Start Chrome with persistent session
./scripts/start_whatsapp_persistent.sh

# 4. Scan QR code (first time only)
```

## 📖 Usage

### **Start Persistent WhatsApp**

```bash
# Use the startup script
./scripts/start_whatsapp_persistent.sh

# Or start Chrome manually
google-chrome \
  --headless=new \
  --disable-gpu \
  --no-sandbox \
  --disable-dev-shm-usage \
  --remote-debugging-port=9222 \
  --user-data-dir=/a0/usr/workdir/chrome-profile/ \
  https://web.whatsapp.com &
```

### **Verify Session Status**

```bash
# Use verification script
./scripts/check_persistence.sh

# Verify manually
ls -lh /a0/usr/workdir/chrome-profile/Default/{Cookies,"Session Storage",IndexedDB}
```

### **Monitor Chrome in Real Time**

```bash
# Use monitoring script
./scripts/monitor_chrome.sh
```

## 🤖 Agent Zero Integration

### **Example 1: Take WhatsApp Snapshot**

```json
{
  "thoughts": ["I need to see the current state of WhatsApp Web"],
  "tool_name": "chrome_devtools.take_snapshot",
  "tool_args": {}
}
```

### **Example 2: Capture QR Code**

```json
{
  "thoughts": ["I need to capture the QR code to scan it"],
  "tool_name": "chrome_devtools.take_screenshot",
  "tool_args": {
    "filePath": "/a0/usr/workdir/whatsapp_qr.png"
  }
}
```

### **Example 3: Send Message**

```json
{
  "thoughts": ["I am going to send a message to the active chat"],
  "tool_name": "chrome_devtools.fill",
  "tool_args": {
    "uid": "message-input-uid",
    "value": "Hello from Agent Zero! 🤖"
  }
}
```

### **Example 4: Click on a Chat**

```json
{
  "thoughts": ["I am going to select a specific chat"],
  "tool_name": "chrome_devtools.click",
  "tool_args": {
    "uid": "chat-element-uid"
  }
}
```

### **Example 5: Navigate to WhatsApp Web**

```json
{
  "thoughts": ["I am going to navigate to WhatsApp Web"],
  "tool_name": "chrome_devtools.navigate_page",
  "tool_args": {
    "type": "url",
    "url": "https://web.whatsapp.com"
  }
}
```

## 🔧 Available Scripts

### **start_whatsapp_persistent.sh**

Starts Chrome with a persistent profile and loads WhatsApp Web.

```bash
./scripts/start_whatsapp_persistent.sh
```

**Configurable parameters:**
- `PROFILE_DIR`: Profile directory (default: `/a0/usr/workdir/chrome-profile/`)
- `DEBUG_PORT`: DevTools port (default: `9222`)
- `WHATSAPP_URL`: WhatsApp Web URL (default: `https://web.whatsapp.com`)

### **check_persistence.sh**

Verifies that persistence files are created and functioning.

```bash
./scripts/check_persistence.sh
```

**Verifies:**
- ✅ Cookies file exists and has data
- ✅ Session Storage directory exists
- ✅ IndexedDB directory exists
- ✅ Local Storage directory exists

### **monitor_chrome.sh**

Monitors the Chrome process in real time.

```bash
./scripts/monitor_chrome.sh
```

## 🐛 Troubleshooting

### **Problem: Chrome doesn't start**

**Solutions:**
```bash
# 1. Verify port 9222
netstat -tlnp | grep 9222

# 2. Kill zombie processes
pkill -9 -f google-chrome

# 3. Verify Chrome is installed
google-chrome --version

# 4. Verify permissions
ls -la /a0/usr/workdir/chrome-profile/
chmod -R 755 /a0/usr/workdir/chrome-profile/
```

### **Problem: Session is lost after reboot**

**Solutions:**
```bash
# 1. Verify persistent directory
ls -lh /a0/usr/workdir/chrome-profile/Default/Cookies

# 2. Verify disk space
df -h /a0/usr/workdir/

# 3. Recreate corrupt profile
rm -rf /a0/usr/workdir/chrome-profile/
mkdir -p /a0/usr/workdir/chrome-profile/
./scripts/start_whatsapp_persistent.sh
```

### **Problem: QR code appears every time**

**Solutions:**
```bash
# 1. Verify directory permissions
chmod -R 755 /a0/usr/workdir/chrome-profile/

# 2. Verify Cookies exists and has data
ls -lh /a0/usr/workdir/chrome-profile/Default/Cookies

# 3. Verify IndexedDB
ls -la /a0/usr/workdir/chrome-profile/Default/IndexedDB/
```

### **Problem: WhatsApp Web doesn't load**

**Solutions:**
```bash
# 1. Verify internet connection
ping -c 4 web.whatsapp.com

# 2. Verify firewall
iptables -L -n | grep 9222

# 3. Restart Chrome
pkill -f google-chrome
./scripts/start_whatsapp_persistent.sh
```

## 📊 Technical Architecture

### **Critical Persistence Files**

| File | Purpose | Importance |
|----------|-----------|-------------|
| **Cookies** | Session tokens | 🔴 CRITICAL |
| **Session Storage/** | Web session state | 🔴 CRITICAL |
| **IndexedDB/** | Local database | 🔴 CRITICAL |
| **Local Storage/** | Local storage | 🔴 CRITICAL |
| **Sessions/** | Browser sessions | 🟡 IMPORTANT |
| **GCM Store/** | Push notifications | 🟢 OPTIONAL |

### **Directory Structure**

```
chrome-profile/
├── Default/                    # Main user profile
│   ├── Cookies                 # ✅ Session tokens
│   ├── Cookies-journal         # Cookie transactions
│   ├── Session Storage/        # ✅ Web session state
│   ├── Local Storage/          # ✅ Local storage
│   ├── IndexedDB/              # ✅ Local database
│   ├── Sessions/               # ✅ Browser sessions
│   ├── Web Data                # Forms and passwords
│   ├── History                 # Browsing history
│   └── Preferences             # User settings
└── Local State                 # Global Chrome state
```

## 🔒 Security Considerations

### **Stored Sensitive Data**

The persistent directory contains:
- 🔒 Authentication cookies
- 🔒 Session tokens
- 🔒 Saved passwords
- 🔒 Browsing history
- 🔒 WhatsApp conversation data

### **Security Recommendations**

```bash
# 1. Restrictive permissions
chmod 700 /a0/usr/workdir/chrome-profile/

# 2. Regular backups
cp -r /a0/usr/workdir/chrome-profile/ /backup/

# 3. Do not share the directory
# Keep the directory private

# 4. Limit bot actions
# Implement confirmations for critical actions
```

## 🚀 Advanced Use Cases

### **Case 1: 24/7 Notification Bot**

```bash
# 1. Start persistent Chrome
./scripts/start_whatsapp_persistent.sh

# 2. Create automation script
# Bot can access WhatsApp 24/7 without scanning QR
```

### **Case 2: Auto-reply Automation**

```python
# Python script for auto-replies
import time
from mcp import chrome_devtools

chrome = chrome_devtools.ChromeDevTools(port=9222)

while True:
    # Check for new messages
    snapshot = chrome.take_snapshot()
    # Process new messages
    # (automation logic)
    time.sleep(60)
```

### **Case 3: Monitor Specific Chats**

```python
# Monitor specific chat
chrome = chrome_devtools.ChromeDevTools(port=9222)
chrome.navigate_page(url="https://web.whatsapp.com")
# Search for specific chat
# (search logic)
# Monitor activity
# (monitoring logic)
```

### **Case 4: Data Extraction**

```python
# Extract conversation data
chrome = chrome_devtools.ChromeDevTools(port=9222)
snapshot = chrome.take_snapshot()
# Process conversation data
# (extraction logic)
```

## 📚 Additional Resources

### **Official Documentation**
- [Chrome DevTools Protocol](https://chromedevtools.github.io/devtools-protocol/)
- [WhatsApp Web FAQ](https://faq.whatsapp.com/web)
- [Agent Zero Documentation](https://docs.agentzero.ai)

### **Scripts and Examples**
- `/scripts/start_whatsapp_persistent.sh` - Start persistent Chrome
- `/scripts/check_persistence.sh` - Verify persistence
- `/scripts/monitor_chrome.sh` - Monitor Chrome

### **Repository**
- [GitHub Repository](https://github.com/agent0ai/whatsapp-automation)
- [Issues](https://github.com/agent0ai/whatsapp-automation/issues)
- [Pull Requests](https://github.com/agent0ai/whatsapp-automation/pulls)

## 🤝 Contributions

Contributions are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This plugin is part of Agent Zero and is available under the MIT license.

## 📞 Support

If you have issues or questions:

1. Check the troubleshooting section
2. Check GitHub issues
3. Open a new issue if necessary

## 🔖 Version

**Current version:** 1.0.0  
**Last updated:** 2026-03-26  
**Author:** Agent Zero Team

## 🎯 Next Steps

1. ✅ Install the plugin
2. ✅ Configure persistent Chrome
3. ✅ Scan QR code (first time)
4. ✅ Test basic automation
5. ✅ Implement advanced use cases

---

**Enjoy WhatsApp automation with Agent Zero! 🚀**
