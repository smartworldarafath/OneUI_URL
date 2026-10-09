<!--suppress HtmlDeprecatedAttribute CheckImageSize-->
<div align="center">

<img src="img/OneURL_squircle.png" height="150" alt="OneURL Icon"/>

# OneURL
### A URL-Shortener and QR Code Generator crafted with Samsung OneUI Design

[![Latest Release](https://img.shields.io/github/v/release/smartworldarafath/OneUI_URL?style=flat-square&color=388e3c)](https://github.com/smartworldarafath/OneUI_URL/releases/latest)
[![](https://img.shields.io/github/last-commit/smartworldarafath/OneUI_URL?style=flat-square)](https://github.com/smartworldarafath/OneUI_URL/commits/)
[![](https://img.shields.io/github/issues-raw/smartworldarafath/OneUI_URL?color=%23ff4400&style=flat-square)](https://github.com/smartworldarafath/OneUI_URL/issues)
[![](https://img.shields.io/github/issues-pr-raw/smartworldarafath/OneUI_URL?color=%23bb00bb&style=flat-square)](https://github.com/smartworldarafath/OneUI_URL/pulls)
[![](https://img.shields.io/github/repo-size/smartworldarafath/OneUI_URL?style=flat-square)](https://github.com/smartworldarafath/OneUI_URL)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=flat-square)](LICENSE)

<br/>

<p align="center">
  <img loading="lazy" src="app/src/test/screenshots/main_default_dark.png" height="340" alt="Main Screen"/>
  <img loading="lazy" src="app/src/test/screenshots/add_url_default_dark.png" height="340" alt="Add URL Screen"/>
  <img loading="lazy" src="app/src/test/screenshots/provider_default_dark.png" height="340" alt="Provider Selection Screen"/>
  <img loading="lazy" src="app/src/test/screenshots/url_default_dark.png" height="340" alt="URL Details Screen"/>
  <img loading="lazy" src="app/src/test/screenshots/generate_qr_code_default_dark.png" height="340" alt="QR Code Screen"/>
  <img loading="lazy" src="app/src/test/screenshots/settings_default_dark.png" height="340" alt="Settings Screen"/>
</p>

</div>

---

## 📖 Overview

**OneURL** is an open-source Android application designed to shorten long URLs through multiple reputable URL-shortening services while instantly generating customizable, high-resolution QR codes for any link. Built strictly adhering to Samsung's **OneUI Design Guidelines**, it delivers an intuitive, fluid, and one-handed friendly user experience on modern Android devices.

---

## 📁 Project Architecture & Master Tree

```text
OneUI_URL/
├── app/                                 <-- Main Android Application Module
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/de/lemke/oneurl/
│   │   │   │   ├── data/                <-- Data Layer: Room DB, DAO, Preferences & QR Exporters
│   │   │   │   │   ├── database/        <-- AppDatabase, URLDao, Entities & Converters
│   │   │   │   │   ├── QRCodeCache.kt   <-- In-Memory & Disk QR Code Caching Engine
│   │   │   │   │   ├── QRCodeExporter.kt<-- Storage Access Framework & Share Exporter
│   │   │   │   │   ├── URLRepository.kt <-- Room Repository managing URL Persistence
│   │   │   │   │   └── UserSettings.kt  <-- User Settings & SharedPreferences wrapper
│   │   │   │   ├── di/                  <-- Dependency Injection (Hilt Modules)
│   │   │   │   │   ├── DispatchersModule.kt <-- Coroutine Dispatchers (@Default, @Io)
│   │   │   │   │   ├── PersistenceModule.kt <-- Room DB & DAO bindings
│   │   │   │   │   ├── ProviderModule.kt    <-- ShortURLProvider injection bindings
│   │   │   │   │   └── SettingsModule.kt    <-- App Settings provider injection
│   │   │   │   ├── domain/              <-- Domain Layer: Business Logic & Use Cases
│   │   │   │   │   ├── generateURL/     <-- URL Generation, Safety & Volley Request Engine
│   │   │   │   │   │   ├── GenerateURLUseCase.kt <-- Core URL Shortening Pipeline
│   │   │   │   │   │   └── RequestQueueSingleton.kt <-- Volley Networking Queue
│   │   │   │   │   ├── model/           <-- 20+ URL Provider Implementations (TinyURL, da.gd, etc.)
│   │   │   │   │   ├── CheckURLSafetyUseCase.kt <-- URLhaus Threat Intelligence Scanner
│   │   │   │   │   ├── GenerateQRCodeUseCase.kt <-- High-res QR Code Generator
│   │   │   │   │   └── URLUseCases.kt   <-- Add, Delete, Observe, Update & Get URLs
│   │   │   │   └── ui/                  <-- Presentation Layer: Activities, Adapters & ViewModels
│   │   │   │       ├── MainActivity.kt  <-- Core Hub displaying Saved URLs & Favorites
│   │   │   │       ├── AddURLActivity.kt<-- URL Creation & Provider Selection Interface
│   │   │   │       ├── URLActivity.kt   <-- Detailed URL Inspection & Analytics View
│   │   │   │       ├── GenerateQRCodeActivity.kt <-- Standalone QR Code Generation Tool
│   │   │   │       ├── SettingsActivity.kt       <-- App Preferences & Configuration Screen
│   │   │   │       └── QRCodeExport.kt  <-- Quick Share, Clipboard & Export Handlers
│   │   │   └── res/                     <-- Android Resources: Layouts, Drawables, Strings, OneUI Themes
│   │   └── test/                        <-- Architecture, Unit & Roborazzi Screenshot Tests
│   └── build.gradle.kts                 <-- App-level build config, dependencies & baseline profiles
│
├── benchmarks/                          <-- Android Macrobenchmark & Baseline Profile Generator
│   ├── src/main/java/.../benchmarks/    <-- Startup, Scroll & Metrics Automation Tests
│   └── build.gradle.kts                 <-- Benchmark runner & target app configurations
│
├── config/                              <-- Code Quality & Analysis Rules
│   ├── detekt/detekt.yml                <-- Detekt Static Code Analysis ruleset
│   └── spotless/                        <-- License Header & ktlint formatting specs
│
├── gradle/                              <-- Gradle Wrapper & Version Catalogs
│   ├── libs.versions.toml               <-- Centralized dependency & plugin version catalog
│   └── wrapper/                         <-- Gradle wrapper binary and configuration
│
├── img/                                 <-- Project Media Assets
│   └── OneURL_squircle.png              <-- High-Resolution App Icon
│
├── build.gradle.kts                     <-- Top-level Gradle root project build configuration
├── settings.gradle.kts                  <-- Gradle project settings & repository resolution
├── CLAUDE.md                            <-- Architecture, commands & build reference guide
├── LICENSE                              <-- Apache 2.0 Open-Source License
└── README.md                            <-- Comprehensive Master Documentation
```

---

## ✨ Features & Functionality

Detailed breakdown of features and how each functions under the hood, mapped to its exact codebase implementation:

### 1. 🔗 Multiple URL Shortener Providers
* **Description**: Users can choose from over 20 reliable URL-shortening engines rather than relying on a single third-party service.
* **How It Works**: When a user selects a provider and triggers shortening, the app dispatches an asynchronous network request through Volley (`RequestQueueSingleton`). Each service is decoupled as an independent object implementing `ShortURLProvider`. If an endpoint is rate-limited or unavailable, users can immediately toggle to another provider with instant fallback.

```text
ShortURLProvider_System/
├── ShortURLProvider.kt                 <-- Base ShortURLProvider interface & contract
├── ShortURLProviderCompanion.kt        <-- Registry of all active, grouped & disabled services
├── Dagd.kt                             <-- da.gd provider implementation
├── Tinyurl.kt                          <-- tinyurl.com provider implementation
├── VgdIsgd.kt                          <-- is.gd & v.gd provider implementation
├── Tly.kt                              <-- t.ly and sub-domain provider engine
├── Kurzelinks.kt                       <-- ogy.de, t1p.de, ocn.de, kurzelinks.de engines
└── Spoome.kt                           <-- Standard and Emoji URL shortener engines
```

---

### 2. ✏️ Custom Alias Support
* **Description**: Create personalized, branded, and easy-to-remember short links instead of arbitrary random characters.
* **How It Works**: Providers supporting customized slugs declare an `AliasConfig` specifying allowed character sets and character length limits. The client checks input validity in real time prior to API transmission, preventing invalid network roundtrips and ensuring deterministic error handling.

```text
Custom_Alias_Engine/
├── AliasConfig.kt                      <-- Min/Max length thresholds and regex patterns
├── AddURLViewModel.kt                  <-- Real-time validation & user feedback StateFlow
└── AddURLActivity.kt                   <-- Input textfield & error banner interface
```

---

### 3. 🛡️ URL Safety & Malware Verification
* **Description**: Proactively scans target destinations for malware, phishing, and spam before executing the shortening process.
* **How It Works**: `GenerateURLUseCase` queries the **URLhaus** Threat Intelligence API (`CheckURLSafetyUseCase`) using the destination URL. If identified on spam or malicious blacklists (Spamhaus, SURBL, URLhaus), the operation is halted, displaying detailed diagnostic findings and VirusTotal links directly to the user.

```text
Safety_Verification_Engine/
├── CheckURLSafetyUseCase.kt            <-- URLhaus API client & threat assessment
├── GenerateURLUseCase.kt               <-- Intercepting safety pipeline before provider call
└── AddURLErrorDialogs.kt               <-- Security alert dialogs with VirusTotal links
```

---

### 4. 📱 Samsung OneUI Design System
* **Description**: Engineered specifically for fluid, comfortable one-handed navigation on large smartphone displays.
* **How It Works**: Implemented using the official Samsung SESL (Samsung Experience Support Library) wrappers (`io.github.tribalfs:oneui-design`). The interface divides into an upper viewing Header zone and lower interaction Actionable zone, complete with native spring animations, ripple touch feedback, and automated light/dark mode adaptation.

```text
OneUI_Design_System/
├── res/layout/activity_main.xml        <-- OneUI Appbar & collapsible toolbar structure
├── res/values/styles.xml               <-- Theme.OneUI primary and secondary accents
├── res/values-night/styles.xml         <-- Amoled dark mode color definitions
└── SESL_Components/                    <-- SeslRecyclerView, SeslSwitchPreference & SeslButtons
```

---

### 5. 📷 QR Code Generation & Sharing
* **Description**: Instantly renders sharp, customizable QR codes for any created short link or arbitrary input string.
* **How It Works**: The `GenerateQRCodeUseCase` generates vector-accurate Bitmaps using `QrEncoder`. The `QRCodeExportStateHolder` coordinates background execution via coroutines—allowing one-tap export to storage via Android's Storage Access Framework, system clipboard copy, or dispatch to nearby devices via Samsung Quick Share and Android ShareSheet.

```text
QRCode_Engine/
├── GenerateQRCodeUseCase.kt            <-- High-resolution bitmap renderer with custom styling
├── QRCodeCache.kt                      <-- In-memory LRU cache preventing duplicate renders
├── QRCodeExporter.kt                   <-- MediaStore & Storage Access Framework exporter
├── QRCodeExport.kt                     <-- StateHolder managing Save, Copy & Share states
└── QRBottomSheet.kt                    <-- Fluid OneUI modal sheet with full export actions
```

---

### 6. 📋 Instant Clipboard & Auto-Copy
* **Description**: Eliminates repetitive steps by immediately copying successfully shortened URLs straight to the device clipboard.
* **How It Works**: Governed by the `auto_copy_on_create` preference stored in `UserSettings`. Once `GenerateURLUseCase` signals success, `AddURLViewModel` interacts with Android's `ClipboardManager`, accompanied by an audible/haptic feedback toast notification.

```text
AutoCopy_Service/
├── UserSettings.kt                     <-- DataStore / SharedPreferences toggle flag
├── SettingsActivity.kt                 <-- OneUI toggle preference UI
└── AddURLViewModel.kt                  <-- Automated clipboard dispatch on Success state
```

---

### 7. 💾 Local History & Favorites Bookmarks
* **Description**: Completely offline archive ensuring all your past shortened links and stats remain instantly accessible.
* **How It Works**: An in-app **Room SQLite Database** stores URL entities (`URLDb`), mapping them to clean domain models via `DomainMapper`. Built-in reactive Kotlin `Flow` streams deliver real-time database updates to the UI, enabling instant search, visit counting, and fast toggle of favorite bookmarks.

```text
Persistence_Archive/
├── AppDatabase.kt                      <-- Room Database configuration & schema migrations
├── URLDao.kt                           <-- Reactive CRUD queries (Insert, Delete, Observe)
├── DomainMapper.kt                     <-- Clean Architecture converter (URLDb <-> URL)
├── URLRepository.kt                    <-- Single Source of Truth wrapping Room calls
└── MainViewModel.kt                    <-- Emits filtered Flow<List<URL>> (All / Favorites)
```

---

## 🛠️ Architecture & Tech Stack

- **Language**: Kotlin 2.x
- **Architecture Pattern**: Clean Architecture (Data, Domain, UI layers) + MVVM
- **Dependency Injection**: Hilt (Dagger)
- **UI Framework**: Samsung OneUI Design Library (SESL Components)
- **Networking**: Volley (RequestQueueSingleton)
- **Local Persistence**: Room Database (SQLite) + Encrypted Preferences
- **Concurrency**: Kotlin Coroutines & StateFlow
- **Code Quality & Testing**: Spotless, Detekt, Konsist, Roborazzi (Screenshot Golden Tests), Kotest

---

## 📥 Installation

To download the latest APK release, visit:
👉 **[Releases Page](https://github.com/smartworldarafath/OneUI_URL/releases)**

1. Download `app-release.apk` from the latest release tag.
2. Open the file on your Android device and proceed with the installation.

---

## 📄 License

This project is licensed under the **Apache License 2.0**. See the [LICENSE](LICENSE) file for complete details.
