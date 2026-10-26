<div align="center">

  <img src="https://raw.githubusercontent.com/brewkits/.github/main/assets/brewkits-banner-dark.png" alt="BrewKits — Industrial-Grade Mobile Infrastructure" width="100%" />

  <br />

  # BrewKits

  **Industrial-Grade Mobile Infrastructure & Zero-Copy Vision Engines**

  *Kotlin Multiplatform &bull; Native Android / iOS &bull; Flutter &bull; High-Throughput Media Pipelines*

  <br />

  [![Kotlin Multiplatform](https://img.shields.io/badge/Kotlin_Multiplatform-2.0+-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org/)
  [![Android Native](https://img.shields.io/badge/Android-Camera2_%2F_Vulkan-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://developer.android.com)
  [![iOS Native](https://img.shields.io/badge/iOS-AVFoundation_%2F_Metal-000000?style=for-the-badge&logo=apple&logoColor=white)](https://developer.apple.com)
  [![Flutter](https://img.shields.io/badge/Flutter-Cross_Platform-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
  [![License](https://img.shields.io/badge/License-Apache_2.0_%2F_MIT-F59E0B?style=for-the-badge)](https://www.apache.org/licenses/LICENSE-2.0)

  <br />

  > *"Don't just wrap the camera. Own the memory."*

</div>

---

### &bull; Engineering Manifesto

At **BrewKits**, we build mission-critical mobile infrastructure. We reject fragile abstraction wrappers, unbounded memory allocations, and inefficient platform-channel roundtrips.

Every engine in our ecosystem is governed by three industrial rules:
1. **Zero-Copy Memory Pipelines:** We eliminate CPU-side memory duplication. Physical buffer pointers (`NativeBuffer`, DMA, `SurfaceTexture`, `CVPixelBuffer`) route directly into reactive GPU render layers and ML inferencing engines.
2. **Deterministic Lifecycle & Concurrency:** Concurrency is strictly bounded with scoped mutexes (`withLock`), atomic operations (`compareAndSet`), and lifecycle-safe cleanup to guarantee zero memory leaks and crash immunity across configuration changes.
3. **Validated in Commercial Production:** We don't publish theoretical code. Our libraries are battle-tested in commercial apps shipping on the Apple App Store and Google Play Store.

---

### &bull; Architectural Blueprint

<div align="center">
  <img src="https://raw.githubusercontent.com/brewkits/.github/main/assets/brewkits-architecture-matrix.png" alt="BrewKits Mobile Architecture Matrix" width="90%" />
</div>

```
┌────────────────────────────────────────────────────────────────────────┐
│                        COMPOSE MULTIPLATFORM UI                         │
│       Shared Tactile Controls  •  Design Tokens  •  Dynamic Layouts    │
├────────────────────────────────────────────────────────────────────────┤
│                  VISIONX HYPERFLOW ENGINE™ (ZERO-COPY)                 │
│     Direct DMA Buffer Pointers  •  Atomic Ref Counting  •  No Memcpy   │
├───────────────────────────────────┬────────────────────────────────────┤
│          ANDROID ENGINE           │             APPLE ENGINE           │
│   Camera2 / CameraX + Vulkan      │   AVFoundation + Metal Viewport    │
└───────────────────────────────────┴────────────────────────────────────┘
```

---

### &bull; Core Ecosystem

#### 1. High-Performance Vision & Graphics Engines
High-throughput camera, rendering, and zero-copy data pipelines eliminating the cross-platform framework tax.

| Repository | Platform | Architecture & Technical Highlights |
| :--- | :--- | :--- |
| **[`kmp-visionx`](https://github.com/vietnguyentuan2019/KMP-VisionX)** | KMP (Android, iOS, macOS) | **VisionX HyperFlow Engine™**: Dual native camera pipelines (Camera2 / AVFoundation) unified under Compose Multiplatform with manual ISO, shutter, tactile dials, and 60 FPS real-time processing. |
| **[`kmp-zerocopy`](https://github.com/vietnguyentuan2019/KMP-VisionX)** | KMP & C++ / JNI | **Direct Hardware Buffer Bridge**: Direct DMA pointer mapping (`NativeBuffer`), sub-microsecond frame access, and zero CPU `memcpy` to keep memory bandwidth at ~0 MB/s CPU under continuous ML load. |
| **[`hyper_render`](https://github.com/brewkits/hyper_render)** | Flutter & Dart | **Single-RenderObject Layout Engine**: Renders HTML, Markdown, and Quill Delta in a single unified `RenderObject`. Full support for CSS float, flexbox, grid, CJK Ruby/furigana, and cross-document selection. |

#### 2. OS Scheduling & Background Execution
Industrial background task runners adhering to modern Android WorkManager & iOS BGTaskScheduler OS execution constraints.

| Repository | Platform | Architecture & Technical Highlights |
| :--- | :--- | :--- |
| **[`native_workmanager`](https://github.com/brewkits/native_workmanager)** | Flutter | **Zero-Overhead Background Task Chains**: Harnesses pure Kotlin `CoroutineWorker` on Android and Swift `BGProcessingTask` on iOS with zero Dart VM boot latency for unchained performance. |
| **[`kmpworkmanager`](https://github.com/brewkits/kmpworkmanager)** | Kotlin Multiplatform | **Unified Multiplatform Job Scheduler**: Orchestrates one-off, periodic, exact, and chained background jobs with advanced constraints, structured logging, and event-driven completion. |

#### 3. Enterprise Infrastructure & Reliability
Deterministic state synchronization, multiplatform permissions, and high-frequency event routing.

| Repository | Platform | Architecture & Technical Highlights |
| :--- | :--- | :--- |
| **[`Grant`](https://github.com/brewkits/Grant)** | Kotlin Multiplatform | **ViewModel-First Permissions**: Clean permission orchestration without Fragment/Activity bindings. Ready for Compose Multiplatform; completely resolves Android dead clicks and iOS deadlocks. |
| **[`KRelay`](https://github.com/brewkits/KRelay)** | Kotlin Multiplatform | **Rotation-Safe Event Relay**: Dispatches Toasts, Navigation, and System Events from shared KMP ViewModels to Android & iOS. Zero memory leaks, survives screen orientation changes. |
| **[`flutter_debounce_throttle`](https://github.com/brewkits/flutter_debounce_throttle)** | Flutter & Dart | **Enterprise Rate Limiter**: Precision debounce and throttle engine with Redis-style rate-limiting semantics, zero dependencies, and over 360+ verified test cases. |

---

### &bull; Production Flagship: LAM – Film Camera

Our architectural stack is proven in production. **LAM** is a commercial analog film camera app built on top of `kmp-visionx` and `kmp-zerocopy`.

- **Sustained 60 FPS Viewfinder:** Real-time sensor stream rendered via native GPU surfaces without frame drop or thermal throttling.
- **Shared Compose UI:** 100% of the vintage camera tactile interface, dials, and haptics shared across platforms.
- **16-Locale Localization:** Comprehensive internationalization across Asian and Western markets.
- **Independent Native Pipelines:** Android Camera2 hardware level 3 + iOS AVFoundation Pro-stream integration.

<div align="center">
  <br />
  <a href="https://apps.apple.com/app/id6773256954">
    <img src="https://img.shields.io/badge/App_Store-LAM_Film_Camera-000000?style=for-the-badge&logo=apple&logoColor=white" alt="LAM on iOS App Store" />
  </a>
  &nbsp;&nbsp;
  <a href="https://play.google.com/store/apps/details?id=dev.brewkits.lam">
    <img src="https://img.shields.io/badge/Google_Play-LAM_Film_Camera-34A853?style=for-the-badge&logo=google-play&logoColor=white" alt="LAM on Google Play" />
  </a>
  <br />
</div>

---

### &bull; Engineering Standards & Contribution Quality Gates

We enforce strict quality gates across all modules:
- **Test Execution:** Automated test verification via AGP 9 KMP toolchain:
  ```bash
  # Run shared and host unit tests
  ./gradlew testAndroidHostTest test

  # Run Tier-3 zero-copy JNI regression net
  ./gradlew :kmp-zerocopy:connectedAndroidDeviceTest
  ```
- **Coverage Discipline:** Committed Kover regression floors enforced across all 13 SDK modules and shared app logic.
- **Static Quality:** Clean Detekt inspection required on all merge requests (`./gradlew detekt`).
- **Memory Safety:** Scoped native pointers with atomic reference counting. No unbounded static collection leaks.

---

<div align="center">
  <sub>Designed & Maintained with Precision by <b>BrewKits Engineering</b></sub>
  <br />
  <sub>&copy; 2026 BrewKits. Open-source under Apache License 2.0 & MIT.</sub>
</div>
