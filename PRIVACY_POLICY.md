# Privacy Policy — TDLidar

**Last Updated: May 5, 2026**
*Applies to TDLidar 7.1 and later, including the optional TDLidar Watch App companion and the TDLidar Pro in-app purchases (auto-renewing subscription and one-time lifetime purchase).*
*The companion **End User License Agreement (EULA)** lives next to this policy and is referenced from in-app: see [EULA.md](./EULA.md).*

## Overview

TDLidar is a real-time capture suite developed by Aristides Lintzeris for streaming depth, camera, motion, audio, and tracking data from an iPhone (and optionally an Apple Watch) into TouchDesigner, OBS, Resolume, and other NDI / OSC receivers on the same Wi-Fi network.

**The short version: TDLidar does not collect, store, or transmit any personal data off your local network. Period.**

There is no account, no analytics, no cloud, no third-party SDK that phones home. The app operates entirely on your device and on your local Wi-Fi.

### What changed in v7.1

v7.1 is a polish + bug-fix release on top of v7.0's TDLidar Pro launch. **No new categories of data are accessed, no new permissions are requested, no new network destinations exist, no new third-party SDKs were added.** The privacy posture is identical to v7.0. v7.1 changes are entirely in code paths that the user already opted into in v7.0 — OSC settings now reconnect immediately when the user changes the IP / port; speech-recognition permission is requested on the user's first "Activate Speech" tap (was firing silently before); speech transcription messages now ship on a dedicated UDP port (9002) so a TouchDesigner OSC In DAT receiver can bind it without colliding with the OSC In CHOP that handles the rest of `/tdlidar/*` traffic. All of this remains local-Wi-Fi-only.

---

## What TDLidar does NOT do

- **No personal information** is collected (name, email, phone number, etc.)
- **No usage analytics** or telemetry of any kind
- **No crash reports** are sent to us or any third party
- **No advertising** or ad tracking
- **No cookies** or similar tracking technologies
- **No user accounts** — the app requires no sign-up or login
- **No data is sent to our servers** — we don't have servers
- **No biometric identification** — TDLidar does not use Face ID or any face-recognition feature
- **No sharing of TrueDepth or face data with third parties** — depth maps and ARKit face data never leave your device except as live OSC / NDI on your own local Wi-Fi
- **No reading of your existing photos or videos** — Photos access is write-only

---

## Data TDLidar accesses, and why

All of the following is processed in real time, on-device, and emitted only to receivers on your local Wi-Fi network. Nothing is stored long-term unless you explicitly tap "Record" or "Save".

### Camera (NSCameraUsageDescription)

- **Front TrueDepth camera** — used for the depth video stream (NDI) and ARKit Face Tracking mode.
- **Rear LiDAR scanner** (Pro iPhones) — used as an alternative depth source.
- **Regular cameras** — used for the optional RGB NDI stream (v5.2+) and as the visual reference for ARKit body and hand tracking.

The camera image is processed in memory and sent to NDI receivers on your local network. It is never recorded or written to disk unless you explicitly start a recording (see *Recording* below).

### TrueDepth API + ARKit Face Tracking

When you enable Face mode on the Tracking page, TDLidar uses ARKit's `ARFaceTrackingConfiguration` to compute:

- 52 ARKit blend-shape coefficients (e.g., `browInnerUp`, `eyeBlinkLeft`, `jawOpen`)
- The 4×4 face transform matrix

This **face data** is used solely as live OSC control data under `/tdlidar/face/*` for visual / interactive applications. It is **not stored, not used for identification, and not transmitted off your local Wi-Fi network**. No face image, no face mesh geometry, no Face ID hash leaves the app.

**Per Apple's TrueDepth API requirements:** TrueDepth depth maps and ARKit face-tracking data **are never shared with third parties** by TDLidar. Nothing collected from the TrueDepth API is sold, traded, or transmitted to any analytics provider, advertiser, server, or partner. The only network destinations are NDI / OSC receivers on your own local Wi-Fi network, which you choose and control yourself.

### Microphone (NSMicrophoneUsageDescription)

When Audio or Transcription mode is active, the microphone feed is processed in real time for:

- **Audio analysis** — FFT spectrum, bass / mid / high levels, beat detection, dynamics, all streamed under `/tdlidar/audio/*`
- **Speech recognition** (when in Transcription mode) — see below

Audio buffers are processed in-memory and discarded each frame. They are **not recorded, not stored, and not transmitted off the device** other than as derived OSC values on your local Wi-Fi.

### Speech Recognition (NSSpeechRecognitionUsageDescription)

When Transcription mode is active, TDLidar uses Apple's on-device speech recognition (`SpeechAnalyzer` on iOS 26+, falling back to `SFSpeechRecognizer`) to convert speech to text. Recognition happens entirely on the device — **audio is never sent to Apple or any third-party server**. Recognized words are streamed as OSC under `/tdlidar/speech/*` and are not stored.

### Motion Sensors (NSMotionUsageDescription)

When Motion mode is active, TDLidar reads:

- Accelerometer
- Gyroscope
- Magnetometer (compass)
- Barometer / altitude
- Battery level

These values are streamed as live OSC under `/tdlidar/motion/*`. No motion history is recorded.

### Local Network (NSLocalNetworkUsageDescription, NSBonjourServices)

TDLidar publishes itself as an NDI source via Bonjour (`_ndi._tcp` / `_ndi._udp`) on your local Wi-Fi so NDI receivers (TouchDesigner, OBS, Resolume, vMix) can discover it. OSC messages are sent as UDP to the IP and port you configure in Settings. **No traffic leaves your local network.**

### Recording (NSPhotoLibraryAddUsageDescription)

When you tap the record button on the LiDAR page, TDLidar writes the colormapped NDI depth output to an `.mp4` video file inside the app's private storage (`Documents/NDIRecordings/`). These files are visible only to TDLidar; they are not synced to iCloud unless you have iCloud Backup enabled at the device level.

When you open the Recordings folder in the app and tap "Save" on a clip, TDLidar uses **write-only Photos access** (`PHPhotoLibrary.requestAuthorization(for: .addOnly)`) to copy that single clip into your Photos library. TDLidar **cannot read your existing photos or videos** — the access is strictly write-only and limited to clips you explicitly export.

You can delete recordings from inside the app at any time. Uninstalling TDLidar removes the in-app recordings; clips already exported to Photos remain in Photos until you delete them.

### PLY Export (TDLidar Pro feature, no additional permission)

When you tap **Save PLY** on a Pro install, TDLidar takes a one-shot snapshot of the live depth + RGB and writes it to a `.ply` (Stanford Polygon Format) point-cloud file inside the app's private storage (`Documents/PLY-Captures/`). The Save PLY action then opens iOS's standard share sheet so you can AirDrop / Mail / Save-to-Files / open the file in MeshLab or Blender. **No PLY data is uploaded anywhere by TDLidar** — the share sheet hands the file off to whatever destination you pick. Captured PLYs stay in the app sandbox until you delete them inside the app or uninstall TDLidar.

---

## In-App Purchases & TDLidar Pro Subscription (NEW IN 7.0)

TDLidar 7.0 introduces an optional paid feature tier — **TDLidar Pro** — sold as one of two in-app purchases through Apple's App Store:

- **TDLidar Pro Yearly** (`aristides.lintzeris.TDLidar.pro.annual`) — auto-renewing subscription, $9.99/year, includes a 7-day free trial for new subscribers.
- **TDLidar Pro Lifetime** (`aristides.lintzeris.TDLidar.pro.lifetime`) — non-consumable one-time purchase, $29.99, never expires.

The free tier of TDLidar continues to include every feature shipped in 6.x. Pro adds HD depth output, edge-preserving smoothing, additional colormaps, point cloud OSC streaming, head-overlay mode, alpha-channel NDI, and Raw-mode customization.

### Payment processing

**All payment processing for TDLidar Pro is handled exclusively by Apple Inc. via the App Store.** TDLidar does not receive, process, view, or store any payment information — no card numbers, no billing addresses, no Apple ID details, no purchase tokens. Payment is charged to the Apple ID of the device on which the purchase is made.

The only purchase data TDLidar reads is Apple's `Transaction.currentEntitlements` API, which returns a yes/no entitlement state ("Pro is unlocked" / "Pro is not unlocked") and is used solely to gate Pro-only feature toggles inside the app. The entitlement state is cached locally in `UserDefaults` so a paying customer can use Pro features offline; it is never transmitted off the device.

### Subscription terms

- **Auto-renewal:** The Pro Yearly subscription auto-renews at the end of each annual period unless cancelled at least 24 hours before the renewal date.
- **Free trial:** The 7-day free trial is offered to new subscribers only. If you cancel during the trial, you are not charged. If you do not cancel, the subscription begins automatically at the end of the trial.
- **Cancellation:** You can cancel at any time in **iOS Settings → Apple ID → Subscriptions** (or via the App Store app → your account → Subscriptions). Cancellation takes effect at the end of the current paid period — Apple does not pro-rate.
- **Lifetime purchase:** The Lifetime in-app purchase is one-time and never renews. It is tied to the Apple ID that made the purchase and can be restored on any device signed in with the same Apple ID via the **Restore Purchases** button in the paywall or in Settings → TDLidar Pro.

### Refunds

All refund requests for TDLidar Pro are handled by Apple under their standard refund policy. To request a refund, visit <https://reportaproblem.apple.com>. TDLidar (Aristides Lintzeris) does not have access to your payment information and cannot issue refunds directly — Apple is the only party who can.

### End User License Agreement (EULA)

Use of TDLidar — including the TDLidar Pro in-app purchases — is governed by the **TDLidar End User License Agreement**, which lives next to this Privacy Policy: see [EULA.md](./EULA.md). The TDLidar EULA is at least as protective of you as Apple's Standard EULA for Licensed Applications and is the EULA referenced from the App Store Connect listing for TDLidar in accordance with Apple's Developer Program License Agreement, Schedule 2. By installing TDLidar or purchasing TDLidar Pro, you agree to that EULA in addition to this Privacy Policy.

### Restore Purchases

Per App Store Review Guideline 3.1.1, the **Restore Purchases** button is provided in two locations: at the bottom of the in-app paywall, and in Settings → TDLidar Pro. Tapping it calls Apple's `AppStore.sync()` API to refresh entitlements from your Apple ID — useful after reinstalling the app, switching to a new device, or resolving any "Pro features locked" state for a paid subscriber.

---

## Apple Watch Companion (optional)

The TDLidar Watch App is an **optional** companion. Users without an Apple Watch never see it. When installed and active, the watch app reads:

- **Motion sensors** (`CMMotionManager`) — wrist orientation, accel, gyro
- **HealthKit** — heart rate during a foreground workout session (Active Energy is also written so the workout session stays alive)

These values are sent over Apple's `WCSession` (Bluetooth / Wi-Fi peer link to the paired iPhone), where the iPhone-side `PhoneSessionManager` republishes them as OSC under `/tdlidar/watch/*`.

The watch app:
- Does **not** transmit data over its own internet connection
- Does **not** store sensor or health data anywhere
- Uses HealthKit only as an in-memory live source — no records are written to your Health app other than the workout session itself, which is required by Apple to keep the heart-rate stream open

---

## Data storage

TDLidar stores the following on your device only:

- **App settings** (depth mode, frame rate, NDI options, motion sensitivity, etc.) in the iOS settings sandbox. Removed when you uninstall the app.
- **Welcome-screen "seen" flag** in `UserDefaults`. Removed when you uninstall.
- **NDI Recordings** in the app's `Documents/NDIRecordings/` folder when you tap Record. You control these — delete them in the Recordings view inside TDLidar, or by uninstalling the app.

No personal data, no sensor history, no user-identifying information is stored.

---

## Third-party software

TDLidar uses the following third-party software, none of which collects user data:

- **NDI® SDK** by Vizrt NDI AB — used solely for local-network video transport. No analytics, no internet calls.
- **Apple frameworks only** for everything else (AVFoundation, ARKit, CoreMotion, CoreLocation–not used, HealthKit on watch, SpeechAnalyzer / SFSpeechRecognizer, Photos, Vision, CoreML).

NDI® is a registered trademark of Vizrt NDI AB.

---

## Children's Privacy

TDLidar does not collect any data from anyone, including children under 13. The app is rated 4+ and contains no objectionable content.

---

## Changes to This Policy

If we make changes to this privacy policy, we will update the "Last Updated" date at the top of this page. Since TDLidar does not collect data, future changes would only reflect new features or clarifications — not new data collection practices.

---

## Disclaimer of Warranty

TDLidar (including the optional Apple Watch companion and the TDLidar Pro in-app purchases) is provided **"AS IS"** and **"AS AVAILABLE"** without warranty of any kind, either express or implied, including but not limited to the implied warranties of merchantability, fitness for a particular purpose, and non-infringement.

The developer (Aristides Lintzeris) does not warrant that the app will be uninterrupted, error-free, secure, or free of viruses, and does not guarantee compatibility with every iPhone model, every iOS version, every Wi-Fi network configuration, or every NDI / OSC receiver. Use of TDLidar in production environments — including live performances, broadcast settings, and commercial installations — is at the user's own risk. The user is responsible for testing the app in their specific deployment environment before relying on it.

## Limitation of Liability

To the maximum extent permitted by applicable law, in no event shall the developer be liable for any indirect, incidental, special, consequential, or punitive damages, including but not limited to loss of profits, loss of data, loss of goodwill, business interruption, equipment damage, or any other commercial damages or losses, arising out of or in connection with the use or inability to use TDLidar — even if the developer has been advised of the possibility of such damages.

Total liability for any claim arising out of or relating to the app shall not exceed the amount you paid for the app or for any active TDLidar Pro subscription in the 12 months preceding the claim.

Some jurisdictions do not allow the exclusion of certain warranties or the limitation or exclusion of liability for incidental or consequential damages, so the above limitations or exclusions may not apply to you. In those jurisdictions, the developer's liability is limited to the greatest extent permitted by law.

## Healthkit notes

(Unchanged from v7.6. No new data types collected. No new SDKs. No new tracking. Re-confirm the existing answers when re-submitting — App Store Connect carries them over automatically for minor updates.)

The Watch app's HealthKit-read scope (heart rate, HRV, active energy) and HealthKit-write scope (workouts, active energy) are already declared on the existing privacy questionnaire under Health & Fitness — collected, not linked, not used for tracking. No update needed.

## Governing Law

This Privacy Policy and your use of TDLidar are governed by the laws of the developer's country of residence, without regard to its conflict-of-law principles. Any dispute arising under this Privacy Policy that is not resolved through Apple's standard App Store dispute process shall be brought in the courts of that jurisdiction.

## Severability

If any provision of this Privacy Policy is held to be invalid or unenforceable by a court of competent jurisdiction, the remaining provisions remain in full force and effect.

## Contact

For privacy questions about TDLidar, contact the developer (Aristides Lintzeris) at any of:

- Email: aristideslintzeris@icloud.com
- App Store listing: <https://apps.apple.com/us/app/tdlidar/id6760954732>
- Instagram: <https://www.instagram.com/aristides.lab/>
- Patreon: <https://www.patreon.com/cw/aritd>
- X / Twitter: <https://x.com/AristidesLab>

For payment, billing, refund, and subscription-management questions, please contact Apple Support at <https://support.apple.com> — TDLidar (Aristides Lintzeris) does not have access to payment information and cannot resolve billing issues directly.

For EULA / license questions, see [EULA.md](./EULA.md).

---

NDI® is a registered trademark of Vizrt NDI AB. TouchDesigner is a registered trademark of Derivative. Apple, iPhone, iPad, Apple Watch, App Store, ARKit, TrueDepth, and SiriKit are trademarks of Apple Inc.
