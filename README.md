<!--suppress HtmlDeprecatedAttribute CheckImageSize-->
<div align="center">

<img src="img/OneURL_squircle.png" height="150" alt="OneURL Icon"/>

# OneURL
### A URL-Shortener and QR Code Generator with Samsung OneUI Design

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

## 📖 Overview (পরিচিতি)

**OneURL** হলো একটি ওপেন সোর্স অ্যান্ড্রয়েড অ্যাপ্লিকেশন যা একাধিক শর্টেনার সার্ভিসের মাধ্যমে লং ইউআরএল (Long URL)-কে নিমিষেই ছোট (Short URL) করতে পারে এবং যেকোনো লিংকের জন্য কাস্টম কিউআর কোড (QR Code) তৈরি করে দেয়। অ্যাপ্লিকেশনটি সম্পূর্ণভাবে স্যামসাংয়ের **OneUI Design Guidelines** অনুসরণ করে তৈরি করা হয়েছে, যার ফলে এটি ব্যবহারে অত্যন্ত মসৃণ, দ্রুত এবং ওয়ান-হ্যান্ডেড ব্যবহারের জন্য দারুণ উপযোগী।

---

## ✨ Features & Functions (বৈশিষ্ট্য ও কাজের পদ্ধতি)

অ্যাপের মূল ফিচারগুলো এবং সেগুলি যেভাবে ব্যাকএন্ড ও ইউআই-তে কাজ করে:

### 1. 🔗 Multiple URL Shortener Providers (একাধিক শর্টেনার প্রোভাইডার)
* **বর্ণনা**: ব্যবহারকারী একাধিক জনপ্রিয় ও বিশ্বস্ত URL শর্টেনিং সার্ভিসের মধ্য থেকে নিজের পছন্দমতো সার্ভিস বেছে নিতে পারেন।
* **যেভাবে কাজ করে**: অ্যাপটিতে `da.gd`, `is.gd`, `v.gd`, `tinyurl.com`, `t.ly`, `lstu`, `tny.im`, `murl`, `spoome`, `zws.im` সহ ২০টিরও বেশি সার্ভিসের API ইন্টিগ্রেট করা রয়েছে। প্রোভাইডার সিলেক্ট করে রিকোয়েস্ট পাঠালে স্বয়ংক্রিয়ভাবে সংশ্লিষ্ট API-এর সাথে যোগাযোগ করে শর্ট লিংক রিটার্ন করা হয়। যদি কোনো প্রোভাইডার ডাউন থাকে, ব্যবহারকারী তাৎক্ষণিকভাবে অন্য প্রোভাইডারে সুইচ করতে পারেন।

### 2. ✏️ Custom Alias Support (কাস্টম অ্যালিয়াস বা নাম)
* **বর্ণনা**: র্যান্ডম ক্যারেক্টারের বদলে আপনার ব্র্যান্ড বা বিষয়ের সাথে মিলিয়ে পছন্দসই কাস্টম নাম দিয়ে শর্ট লিংক তৈরি করার সুবিধা।
* **যেভাবে কাজ করে**: যেসকল সার্ভিস কাস্টম অ্যালিয়াস সমর্থন করে (যেমন: `tinyurl`, `da.gd`, `vgd`, ইত্যাদি), সেগুলোতে ইনপুট বক্সে অ্যালিয়াস দিলে অ্যাপটি প্রোভাইডারের API রুলস (ক্যারেক্টার লিমিট, অনুমোদিত ক্যারেক্টার) যাচাই করে এবং কাঙ্ক্ষিত নামে শর্ট লিংক তৈরি করে দেয়।

### 3. 🛡️ URL Safety & Malware Protection (লিংক নিরাপত্তা পরীক্ষণ)
* **বর্ণনা**: লিংক শর্ট করার আগেই সেটির নিরাপত্তা যাচাই করা হয় যেন কোনো ম্যালিশাস বা ক্ষতিকর লিংক শর্ট না হয়।
* **যেভাবে কাজ করে**: `GenerateURLUseCase` চলার সময় অ্যাপটি স্বয়ংক্রিয়ভাবে **URLhaus** ডেটাবেজের মাধ্যমে লিংকটি স্ক্যান করে। যদি লিংকটি ফিশিং, স্প্যাম, বটনেট বা ম্যালওয়্যার হিসেবে ব্ল্যাকলিস্টেড থাকে, তবে অ্যাপটি ইউজারকে সতর্কবার্তা দেখায় এবং লিংক শর্ট হওয়া থেকে বিরত রাখে।

### 4. 📱 Samsung OneUI Design & Experience (ওয়ানইউআই ডিজাইন)
* **বর্ণনা**: বড় স্ক্রিনের স্মার্টফোনে একহাতে আরামদায়ক ব্যবহারের জন্য স্যামসাং OneUI ৮ ডিজাইন সিস্টেম।
* **যেভাবে কাজ করে**: ডিসপ্লে এরিয়া এবং ইন্টার‍্যাকশন এরিয়া আলাদা রাখা হয়েছে (Viewing Area উপরে এবং Actionable Controls নিচে)। এর সাথে রয়েছে ফুল ডার্ক মোড সাপোর্ট, ফ্লুইড ট্রানজিশন এবং নেটিভ ওয়ানইউআই উইজেট ও বোতাম।

### 5. 📷 QR Code Generation & Quick Sharing (কিউআর কোড তৈরি ও শেয়ারিং)
* **বর্ণনা**: যেকোনো তৈরি করা শর্ট ইউআরএল অথবা কাস্টম লিংকের জন্য হাই-রেজোলিউশন কিউআর কোড তৈরি করার সুবিধা।
* **যেভাবে কাজ করে**: 
  - **Save**: ইমেজ ফরম্যাটে ডিভাইসের মেমোরিতে সরাসরি সেভ করা যায়।
  - **Copy**: ক্লিপবোর্ডে কপি করে সরাসরি যেকোনো মেসেজিং অ্যাপে পেস্ট করা যায়।
  - **Quick Share & Android ShareSheet**: সিস্টেম ডায়ালগের মাধ্যমে তাৎক্ষণিকভাবে অন্যদের সাথে কিউআর কোড শেয়ার করা যায়।

### 6. 📋 Instant Clipboard & Auto-Copy (স্বয়ংক্রিয় কপি সুবিধা)
* **বর্ণনা**: শর্ট লিংক তৈরি হওয়া মাত্রই ক্লিপবোর্ডে কপি হয়ে যাওয়ার অপশন।
* **যেভাবে কাজ করে**: সেটিংস থেকে **Automatic copying** অপশন চালু রাখলে লিংক সফলভাবে তৈরি হওয়া মাত্র স্বয়ংক্রিয়ভাবে ক্লিপবোর্ডে যুক্ত হয় এবং ইউজার স্ক্রিনে একটি টোস্ট কনফার্মেশন দেখতে পান।

### 7. 💾 Local History & Favorites (হিস্ট্রি এবং ফেভারিটস বুকমার্কিং)
* **বর্ণনা**: তৈরি করা সমস্ত ইউআরএল লোকাল ডেটাবেজে সংরক্ষিত থাকে যাতে পরবর্তীতে যেকোনো সময় দেখা ও ব্যবহার করা যায়।
* **যেভাবে কাজ করে**: এটি **Room Database** এবং Clean Architecture ব্যবহার করে তৈরি। প্রতিটি তৈরি করা লিংকের টাইটেল, তৈরির তারিখ এবং ভিজিট কাউন্ট লোকালি স্টোর করা থাকে। যেকোনো লিংক ফেভারিট মার্ক করে আলাদা ট্যাবে দ্রুত খুঁজে পাওয়া যায়।

---

## 🛠️ Architecture & Tech Stack (প্রযুক্তি ও স্থাপত্য)

- **Language**: Kotlin 2.x
- **Architecture**: Clean Architecture (Data, Domain, UI) + MVVM Pattern
- **Dependency Injection**: Hilt (Dagger)
- **UI & Design**: Samsung OneUI Design System (SESL Components)
- **Networking**: Volley (RequestQueueSingleton)
- **Local Database**: Room DB (SQLite) + SharedPreferences
- **Asynchronous**: Kotlin Coroutines & StateFlow
- **Code Quality & Testing**: Spotless, Detekt, Konsist, Roborazzi (Screenshot Testing), Kotest

---

## 📥 Installation (ইন্সটলেশন)

সবচেয়ে সাম্প্রতিক সংস্করণ ডাউনলোড করতে ভিজিট করুন:
👉 **[Releases Page](https://github.com/smartworldarafath/OneUI_URL/releases)**

1. সর্বশেষ রিলিজ থেকে `app-release.apk` ফাইলটি ডাউনলোড করুন।
2. আপনার অ্যান্ড্রয়েড ফোনে ফাইলটি ওপেন করে ইন্সটল করুন।

---

## 📄 License

এই প্রকল্পটি **Apache License 2.0** এর আওতায় প্রকাশিত। বিস্তারিত জানতে [LICENSE](LICENSE) ফাইলটি দেখুন।
