# LeetNotify

> 🧠 A native macOS menu bar app that delivers daily LeetCode prompts — lightweight, customizable, and perfect for consistent algorithm practice.


## ✨ Features

- ⏰ Daily problem notifications with native macOS alerts
- 🔧 Fully customizable via script
- 🍎 Built with [Platypus](https://sveinbjorn.org/platypus), lightweight and native
- 🧠 Supports your daily LeetCode habit effortlessly

## 🛠 Tech Stack

- Ruby
- Platypus (for macOS app packaging)
- AppleScript
- terminal-notifier

## 🚀 Usage

### 1. Run as a Script

If you just want the core functionality without the app:

```bash
ruby leetCodeEx.rb
```

*This will trigger a LeetCode notification via terminal-notifier.*

⚠️ Requires terminal-notifier:
```
brew install terminal-notifier
```

### 2. Build the `.app` using Platypus

If you want a native macOS `.app` version:

1. Install [Platypus](https://sveinbjorn.org/platypus)
2. Open Platypus
3. Set the following options:
   - **Script path**: `leetCodeEx.rb`
   - **Interface**: `None` 
   - **Icon**: Select `AppIcon.icns` if desired
4. Save the `.app` file
5. *(Optional)* Set the app to **launch at login** in macOS settings


## 📌 Status

🛠 Ongoing: Open-sourced, but not distributed via installer yet.  
To use the app, please build it locally using Platypus.
