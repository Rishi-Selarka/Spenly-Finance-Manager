# 💰 Spenly - AI Money Manager

**An easy and simple money manager with AI insights, iCloud sync, and pro tooling.**

> **🚀 Live on the App Store** — 550+ downloads and 65+ premium users.

[![App Store](https://img.shields.io/badge/App%20Store-Live-blue)](https://apps.apple.com/app/spenly/id6736744066)

## 📱 App Overview

Spenly helps you track expenses, manage budgets, and understand spending with AI-powered insights. Built with SwiftUI (MVVM) and synced securely with iCloud. iPhone only; iPad not supported.

### ✨ Key Features

- **🧠 AI Spending Insights** — Context-aware summaries, anomaly hints, and chat
- **👤 Payee & Payer Management** — Add/search contacts for cleaner records
- **💳 Expense Tracking** — Fast entry with categories, notes, and receipt links
- **☁️ iCloud Sync** — Private sync across devices with CloudKit
- **📊 Visual Analytics** — Trends by category, month, and custom ranges
- **📄 Receipt Attachments** — Scan and attach receipts to transactions
- **🌍 Multi-Currency** — Live rates and automatic conversion
- **📤 Export** — PDF and CSV
- **🔔 Reminders** — Smart nudges to stay on top of logging
- **👥 Multiple Accounts** — Cash, cards, and bank accounts
## 💎 Spenly Premium

Unlock advanced capabilities while supporting development:

- Ad‑free experience
- Advanced AI analysis and deeper context
- Unlimited templates and categories
- Priority receipt processing
- Richer CSV/PDF export options

> Already supporting the app: 60+ premium users.

## 🧠 AI Capabilities

- Spenly Chat: ask “Why did groceries spike this month?”
- Auto‑suggest categories from description, merchant, and your history
- Insights: outlier detection and recurring pattern surfacing


## 🛠 Technical Stack

- **Framework**: SwiftUI
- **Data Storage**: Core Data with CloudKit integration
- **Architecture**: MVVM pattern with Combine
- **Cloud Sync**: CloudKit for device synchronization
- **AI**: Gemini-based analysis via `AIManager`/`GeminiManager`
- **Crash Monitoring**: Firebase Crashlytics
- **Ads**: Google AdMob integration
- **Minimum iOS**: 16.6+

### 🏗 Project Architecture

```swift
// Core manager example - CloudKit sync with error handling
class CloudKitSyncManager: ObservableObject {
    @Published var isSyncEnabled: Bool
    @Published var syncStatus: SyncStatus
    @Published var lastSyncDate: Date?
    
    func forceSyncNow() {
        // Production sync implementation
    }
}
```

### 📂 Project Structure
```
Spenly/
├── 📱 App/
│   ├── AppDelegate.swift          # App lifecycle and Firebase setup
│   ├── SceneDelegate.swift        # Scene configuration
│   └── MainAppCoordinator.swift   # Main navigation flow
├── 🎨 Views/
│   ├── HomeView.swift            # Main dashboard with expense overview
│   ├── AddTransactionView.swift  # Transaction creation form
│   ├── SettingsView.swift        # App settings and iCloud sync
│   ├── CategoriesView.swift      # Category management
│   ├── TransactionHistoryView.swift # Transaction list and filtering
│   └── AdViews/                  # AdMob banner integration
├── 🧠 Managers/
│   ├── CloudKitSyncManager.swift # iCloud synchronization logic
│   ├── CoreDataManager.swift     # Local data persistence
│   ├── AuthManager.swift         # User authentication (Apple ID/Guest)
│   ├── CategoryManager.swift     # Expense category management
│   ├── AccountManager.swift      # Multiple account handling
│   └── CurrencyRateManager.swift # Currency conversion
├── 📊 Models/
│   ├── TransactionData.swift     # Core Data transaction model
│   ├── CurrencyInfo.swift        # Currency definitions and rates
│   ├── Theme.swift               # App theming system
│   └── SpendingAnalyzer.swift    # Analytics calculations
├── 🔧 Utilities/
│   ├── DocumentGenerator.swift   # PDF/CSV export functionality
│   ├── ReceiptManager.swift      # Image attachment handling
│   └── CurrencyFormatter.swift   # Localized number formatting
└── 📄 Legal/
    ├── PrivacyPolicy.md          # Privacy policy content
    └── TermsOfService.md         # Terms of service content
```

## 🚀 Technical Implementation

### ☁️ CloudKit Integration
```swift
private func handleCloudKitError(_ error: Error) {
    if let ckError = error as? CKError {
        switch ckError.code {
        case .partialFailure:
            // Continue with partial success
        case .quotaExceeded:
            // Handle storage limits
        case .networkUnavailable:
            // Retry logic for network issues
        }
    }
}
```

### 📊 Data Analytics
- Real-time expense calculations by category
- Monthly and yearly spending trends
- Interactive charts using SwiftUI
- Export capabilities for financial planning

### 🎨 User Interface
- **SwiftUI-first approach** with clean, modern design
- **Dark mode optimized** for better user experience
- **Responsive layout** supporting all iPhone screen sizes
- **Custom animations** for smooth interactions

## 📱 Screenshots

### Home View
*Main dashboard showing expense overview and recent transactions*

<img src="https://github.com/user-attachments/assets/4e51892b-2763-47fa-9ac2-706a4bdbe99e" width="300" alt="Spenly Home View">

### Settings View
*iCloud sync configuration and app preferences*

<img src="https://github.com/user-attachments/assets/cb6fbecc-d9c2-474f-ac67-fe5f1af646f2" width="300" alt="Spenly Settings View">

### Categories View
*Expense category management with custom icons*

<img src="https://github.com/user-attachments/assets/196f480a-9951-4a0c-ad3d-afb7601773f9" width="300" alt="Spenly Categories View">

### Add Transaction View
*Transaction creation with category selection and receipt attachment*

<img src="https://github.com/user-attachments/assets/42ebd3f9-84b9-4f84-b852-0defa1a049df" width="300" alt="Spenly Add Transaction View">

## 💻 Code Quality Features

### Error Handling & Monitoring
```swift
private func logError(_ error: Error, context: String) {
    Crashlytics.crashlytics().log("Error in \(context): \(error.localizedDescription)")
    Crashlytics.crashlytics().record(error: error)
    Crashlytics.crashlytics().setCustomValue(context, forKey: "error_context")
}
```

### Memory Management
```swift
@objc func handleMemoryWarning() {
    ImageCache.shared.clearCache()
    CoreDataManager.shared.handleMemoryWarning()
    clearTemporaryResources()
}
```

### Data Persistence
- Core Data with CloudKit for reliable sync
- SQLite WAL mode for performance
- Automatic data migration handling
- Background sync operations

## 🔒 Privacy & Security

- **iCloud encryption** for data synchronization
- **Local Core Data encryption** for device storage
- **Minimal data collection** - only essential app functionality
- **No personal data sharing** with third parties
- **Firebase Crashlytics** for anonymous crash reporting only

## 📊 Production Status

- **Live on the App Store**
- **300+ downloads**
- **60+ premium users**
- **CloudKit sync** reliable in production
- Crash monitoring via Firebase Crashlytics
- AdMob integration generating revenue

## 🧪 Testing & Quality

- Core Data operations testing
- CloudKit sync functionality validation
- UI component testing for critical flows
- Memory usage optimization
- Performance monitoring in production

## 📞 Contact & Support

- **App Store**: [Spenly – AI Money Manager](https://apps.apple.com/app/spenly/id6736744066)
- **Support Email**: teamspenlyapp@gmail.com
- **Privacy Policy**: [View Privacy Policy](https://rishi-selarka.github.io/spenly-legal/privacy-policy)
- **Terms of Service**: [View Terms of Service](https://rishi-selarka.github.io/spenly-legal/terms-of-service)

---

## 🏆 Technical Skills Demonstrated

- **iOS Development**: SwiftUI, Core Data, CloudKit
- **Architecture**: MVVM with Combine reactive programming  
- **Cloud Integration**: CloudKit sync with production deployment
- **Data Management**: Core Data optimization and migration
- **Production Experience**: Live App Store app with real users
- **Quality Assurance**: Crash monitoring and performance optimization
- **Modern iOS**: Dark mode, multi-device sync, accessibility

---

**Built with ❤️ by Rishi Selarka**

*© 2025 Rishi Selarka. All rights reserved.*
