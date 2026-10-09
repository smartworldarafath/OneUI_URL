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

## 📁 Project Architecture & Directory Structure

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

Detailed breakdown of features and how each functions under the hood:

### 1. 🔗 Multiple URL Shortener Providers
* **Description**: Users can select from a wide array of reliable URL-shortening engines rather than relying on a single service.
* **How It Works**: The app integrates REST APIs for over 20 providers (including `da.gd`, `is.gd`, `v.gd`, `tinyurl.com`, `t.ly`, `lstu`, `tny.im`, `murl`, `spoome`, and `zws.im`). When a request is triggered, the app communicates with the chosen provider's endpoint. If a provider experiences rate limits or server downtime, users can seamlessly switch to another service with a single tap.

### 2. ✏️ Custom Alias Support
* **Description**: Allows creating human-readable and personalized short links instead of random alphanumeric strings.
* **How It Works**: For providers supporting custom aliases (such as `tinyurl`, `da.gd`, and `v.gd`), the app validates the desired alias format (character constraints, min/max length) client-side before dispatching the creation request to the provider's API.

### 3. 🛡️ URL Safety & Malware Verification
* **Description**: Ensures security by screening every target URL for malicious content prior to shortening.
* **How It Works**: Through `GenerateURLUseCase`, the application queries the **URLhaus** threat intelligence database in real time. If the target URL is flagged as phishing, malware distribution, botnet C&C, or abusive redirector, the shortening process aborts immediately and warns the user with actionable security reports.

### 4. 📱 Samsung OneUI Design System
* **Description**: Ergonomically structured interface crafted for effortless one-handed operation on modern large displays.
* **How It Works**: Utilizing Samsung SESL components, screen layouts separate viewing areas (top) and actionable interaction areas (bottom). It natively supports automatic light/dark theming, smooth spring animations, and native system haptic feedback.

### 5. 📷 QR Code Generation & Sharing
* **Description**: Instantly generates sharp QR codes for every generated short URL or custom input link.
* **How It Works**:
  - **Save to Storage**: Exports QR codes directly into device storage as high-quality PNG images via Android's Storage Access Framework.
  - **Copy to Clipboard**: Copies the bitmap data directly to the clipboard for rapid pasting into messaging and document apps.
  - **Share Options**: Integrates with Android ShareSheet and Quick Share for direct transfer across nearby devices and installed applications.

### 6. 📋 Instant Clipboard & Auto-Copy
* **Description**: Streamlines workflow by eliminating the need to manually copy newly generated links.
* **How It Works**: When the **Automatic copying** option is toggled on in Settings, successful link creation automatically places the shortened URL onto the system clipboard alongside visual toast confirmation.

### 7. 💾 Local History & Favorites Bookmarks
* **Description**: Keeps an offline archive of all your shortened URLs for quick reference and tracking.
* **How It Works**: Built using **Room Database** and reactive Kotlin Flows. Each record preserves the destination URL, short URL, QR code cache, creation timestamp, and visit count. Key links can be starred as favorites to filter and access them instantly.

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
