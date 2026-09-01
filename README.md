# 🏔️ TrailMedic — Offline AI First Aid for Trekkers


<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=flat-square&logo=android"/>
  <img src="https://img.shields.io/badge/AI-Gemma%202B%20IT-blue?style=flat-square&logo=google"/>
  <img src="https://img.shields.io/badge/Status-In%20Development-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/Offline-100%25-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/iQOO%20Hackathon-2026-red?style=flat-square"/>
</p>

---

## 🚨 The Problem

Every year, thousands of trekkers face life-threatening medical emergencies — falls, fractures, hypothermia, cardiac events — in remote areas with **zero cellular coverage**. The average response time for rescue teams in mountainous regions is 4–12 hours. During this window, the only resource available is whoever is standing next to the victim.

Most people don't know what to do.

---

## 💡 The Solution

**TrailMedic** is a fully offline Android app that runs a local AI model on-device to act as an intelligent first aid guide. No internet. No signal. No server. Just the phone in your pocket.

The AI conducts a structured medical interview — asking targeted questions one at a time — then delivers clear, step-by-step first aid instructions tailored to the specific emergency.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🤖 **On-Device AI** | Gemma 2B IT (INT4 quantized) runs fully locally via MediaPipe |
| 📴 **100% Offline** | Zero network dependency for core functionality |
| 🩺 **Smart Triage** | AI interviews the user before diagnosing — no guessing |
| 🎙️ **Voice I/O** | Offline speech recognition + text-to-speech for hands-free use |
| ⚡ **Battery Aware** | Reduces AI token load when battery is low |
| 📋 **Session Export** | Save and export first aid session logs for medical handoff |
| 🗂️ **Fallback Mode** | Rule-based symptom tree works even if AI model isn't loaded |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────┐
│              UI Layer                   │
│  Jetpack Compose + Material 3 (Dark)    │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│           ViewModel Layer               │
│     MVVM + StateFlow + Hilt DI          │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│            Domain Layer                 │
│    UseCases · Models · Repositories     │
└────────────────┬────────────────────────┘
                 │
┌────────────────▼────────────────────────┐
│             Data Layer                  │
│  ┌──────────────┐  ┌───────────────┐   │
│  │ LLM Engine   │  │  Room DB      │   │
│  │ (MediaPipe)  │  │  (Sessions +  │   │
│  │ Gemma 2B IT  │  │  SymptomTree) │   │
│  └──────────────┘  └───────────────┘   │
└─────────────────────────────────────────┘
```

**Stack:**
- **Language:** Kotlin
- **UI:** Jetpack Compose + Material 3
- **AI Runtime:** MediaPipe LLM Inference API
- **Model:** Gemma 2B IT (INT4, ~1.5GB)
- **DI:** Hilt
- **Database:** Room
- **Architecture:** MVVM + Clean Architecture
- **Min SDK:** 26 (Android 8.0)

---

## 🗺️ App Flow

```
Launch → Check model downloaded?
              │
        NO ───┴─── YES
        │               │
  Onboarding       Home Screen
  + Download            │
                   Select Emergency
                   Category
                        │
                   AI Interview
                   (3–5 questions)
                        │
                   Diagnosis +
                   First Aid Steps
                        │
                   Save / Export
                   Session Log
```

---

## 📱 Screens

- **Splash / Onboarding** — First-launch model download (one-time, WiFi)
- **Home Dashboard** — SOS button + 8 emergency category quick-select
- **Emergency Chat** — AI interview + streamed first aid instructions
- **Session History** — Past emergency sessions with export
- **Settings** — TTS, text size, emergency contact, model management

---

## 🚀 Development Status

> ⚠️ **This project is actively under development for the iQOO Hackathon 2026.**

| Module | Status |
|---|---|
| Project Setup + Gradle | ✅ Done |
| Theme + Design Tokens | ✅ Done |
| Domain Models | ✅ Done |
| LLM Engine (MediaPipe) | 🔄 In Progress |
| Conversation Manager | 🔄 In Progress |
| Home Screen UI | 🔄 In Progress |
| Emergency Chat Screen | ⏳ Planned |
| Voice Input + TTS | ⏳ Planned |
| Session History + Room | ⏳ Planned |
| Model Download Flow | ⏳ Planned |
| Settings Screen | ⏳ Planned |
| Fallback Symptom Tree | ⏳ Planned |
| Battery Awareness | ⏳ Planned |

---

## 🛠️ Building Locally

> ⚠️ Requires a **physical Android device** with 4GB+ RAM. LLM inference does not run on emulators.

```bash
git clone https://github.com/YOUR_USERNAME/TrailMedic.git
cd TrailMedic
```

1. Open in Android Studio Hedgehog (2023.1.1) or newer
2. Sync Gradle
3. On first launch, the app will prompt you to download the Gemma 2B model (~1.5 GB) over WiFi
4. Run on a physical device

**Model:** Gemma 2B IT INT4 is downloaded at runtime via the app's onboarding flow. It is not bundled in the repo due to size constraints.

---

## 📂 Project Structure

```
app/src/main/java/com/trailmedic/
├── di/               # Hilt dependency injection modules
├── domain/           # Models, use cases, repository interfaces
├── data/             # Room DB, LLM engine, repository implementations
├── ui/               # Compose screens, ViewModels, components
└── utils/            # TTS, voice input, battery, download managers
```

---

## 🎯 Hackathon Context — iQOO 2026

TrailMedic was conceived for the iQOO Hackathon 2026 under the **AI + Safety** track. The iQOO device's high-performance Snapdragon chipset and large RAM configuration make it an ideal host for on-device LLM inference — turning a flagship phone into a life-saving medical companion in the world's most remote locations.

---


---

## 👤 Author

**Swapnil**
