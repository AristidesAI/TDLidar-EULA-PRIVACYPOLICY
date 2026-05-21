# End User License Agreement — TDLidar

_Last updated: 21 May 2026_

This End User License Agreement (the **"Agreement"**) is a legal contract between you (**"you"**, **"User"**) and Aristides Lintzeris (**"Developer"**, **"we"**, **"us"**), the developer of the **TDLidar** application for iOS, watchOS, and iPadOS (the **"App"**). By downloading, installing, or using the App you agree to be bound by the terms of this Agreement. If you do not agree to these terms, do not download, install, or use the App.

This Agreement supplements and incorporates by reference Apple's **Licensed Application End User License Agreement** (the **"Apple LALC"**, available at [apple.com/legal/internet-services/itunes/dev/stdeula](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/)). In the event of any conflict between this Agreement and the Apple LALC, this Agreement controls solely with respect to those terms expressly addressed herein; otherwise the Apple LALC governs.

---

## 1. License Grant

Subject to your compliance with this Agreement, we grant you a personal, limited, non-exclusive, non-transferable, revocable license to download, install, and use the App on any iOS, watchOS, or iPadOS device that you own or control, in accordance with the Usage Rules set forth in the Apple Media Services Terms and Conditions.

---

## 2. Pro Mode (In-App Purchase)

The App is free to download and includes a full set of free features (NDI streaming, OSC tracking, basic depth output, and all standard tracking modes). Certain advanced features are gated behind **"Pro Mode"**, which is unlocked via a single, non-recurring in-app purchase administered by Apple through the App Store.

### 2.1 One-Time Purchase

Pro Mode is a **one-time, non-consumable in-app purchase**. There is no subscription, no recurring billing, no automatic renewal, and no trial period. You pay once and Pro Mode remains unlocked for that Apple ID indefinitely on every device signed into that Apple ID, subject to Apple's policies governing in-app purchases.

### 2.2 Pro Mode Features

At the time of writing, Pro Mode unlocks the following features. The exact list may evolve in future updates; the App will always display the current list in the Pro Mode upgrade screen before purchase:

- **Extended Range** — Depth Anything on-device ML model that fuses with the LiDAR / TrueDepth sensor for depth beyond the sensor's hardware range.
- **HD Output** — 1080p and 1440p depth output via on-device MPS upscale.
- **Edge Smoothing** — bilateral filtering on the depth stream.
- **Pro Colormaps + Custom LUTs** — additional depth colormaps and import-your-own LUT support.
- **Depth-Mask Alpha NDI** — output the NDI stream with transparency where depth is invalid.
- **Raw Mode Customization** — full control over Raw Mode's glitch, color, posterize, bloom, and scanline parameters (Raw Mode itself is free).
- **VJ Mode** — background audio FFT / level / beat OSC streaming alongside NDI and recording, with configurable mic input and OSC destination.
- **AirPods Motion OSC** — head-pose OSC streaming from CMHeadphoneMotionManager (pitch, roll, yaw, acceleration, gravity, rotation rate).

### 2.3 Refunds

All purchases are processed by Apple. Refund requests are handled by Apple under Apple's standard refund policy and are not within the Developer's control. You can request a refund at [reportaproblem.apple.com](https://reportaproblem.apple.com).

### 2.4 Restoring a Prior Purchase

If you have previously purchased Pro Mode and Pro Mode is not unlocked on a new device or after reinstalling the App, open the upgrade screen and tap **Restore Purchases**. The App will fetch your current entitlements from Apple and unlock Pro Mode automatically if a prior purchase is found on your Apple ID.

### 2.5 Legacy Subscribers

Prior versions of the App offered an annual auto-renewing subscription option for Pro Mode. That subscription is no longer offered for purchase. Customers who previously subscribed will continue to receive Pro Mode access for as long as their subscription remains active in Apple's system. To cancel an existing subscription, go to **iOS Settings → Apple ID → Subscriptions** on your device.

---

## 3. Restrictions

You agree not to:

- Reverse engineer, decompile, disassemble, or attempt to derive the source code of the App, except to the extent permitted by applicable law;
- Modify, adapt, translate, or create derivative works of the App;
- Remove, alter, or obscure any proprietary notices on the App;
- Use the App in any unlawful manner or for any purpose that violates the rights of any third party;
- Use the App to transmit, distribute, or store any data that infringes intellectual property rights, violates privacy laws, or is otherwise unlawful;
- Bypass, disable, or interfere with security or copy-protection features of the App, including the Pro Mode entitlement check;
- Use the App to develop a competing product.

---

## 4. Privacy

The App processes camera, microphone, motion, and depth data locally on your device. The App streams this data over your local network via NDI and OSC to receivers you configure (e.g. TouchDesigner, Resolume, OBS). No data leaves your local network unless you explicitly configure the App to do so.

For full details on what data the App collects, processes, and transmits, see the separate Privacy Policy at [github.com/AristidesAI/TDLidar-EULA-PRIVACYPOLICY/blob/main/PRIVACY_POLICY.md](https://github.com/AristidesAI/TDLidar-EULA-PRIVACYPOLICY/blob/main/PRIVACY_POLICY.md).

---

## 5. Ownership

The App, including all underlying source code, models, assets, and documentation, is the intellectual property of the Developer. This Agreement grants you a license to use the App; it does not transfer ownership of any intellectual property. All rights not expressly granted are reserved.

The NDI® name and logo are trademarks of NDI, LLC. TDLidar uses the NDI SDK under license; TDLidar is not affiliated with or endorsed by NDI, LLC.

---

## 6. Third-Party Services

The App integrates with several third-party services and frameworks, including:

- **NDI SDK** (network streaming) — governed by the [NDI SDK License](https://ndi.video/).
- **Apple Frameworks** — AVFoundation, ARKit, Vision, Core ML, Core Motion, Speech, StoreKit, WatchConnectivity. Governed by Apple's developer agreements.

Your use of these services is subject to the respective third-party terms. The Developer is not responsible for the operation, availability, or content of third-party services.

---

## 7. Disclaimer of Warranties

THE APP IS PROVIDED **"AS IS"** AND **"AS AVAILABLE"** WITHOUT WARRANTIES OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, NON-INFRINGEMENT, AND ACCURACY. WE DO NOT WARRANT THAT THE APP WILL BE UNINTERRUPTED, ERROR-FREE, OR FREE OF HARMFUL COMPONENTS. THE ENTIRE RISK ARISING OUT OF USE OR PERFORMANCE OF THE APP REMAINS WITH YOU.

The App is intended for use in live performance, installation, and content creation contexts. The App is **not** medically certified, safety-certified, or intended for any use where failure could result in personal injury, death, or property damage. Do not rely on the App for navigation, autonomous control, safety-critical systems, or medical diagnosis.

---

## 8. Limitation of Liability

TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, IN NO EVENT WILL THE DEVELOPER BE LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, OR PUNITIVE DAMAGES, OR ANY LOSS OF PROFITS OR REVENUES, WHETHER INCURRED DIRECTLY OR INDIRECTLY, OR ANY LOSS OF DATA, USE, GOODWILL, OR OTHER INTANGIBLE LOSSES, RESULTING FROM (A) YOUR USE OF OR INABILITY TO USE THE APP; (B) ANY UNAUTHORIZED ACCESS TO OR USE OF OUR SERVERS AND/OR ANY PERSONAL INFORMATION STORED THEREIN; (C) ANY INTERRUPTION OR CESSATION OF TRANSMISSION TO OR FROM THE APP; (D) ANY BUGS, VIRUSES, TROJAN HORSES, OR THE LIKE THAT MAY BE TRANSMITTED TO OR THROUGH OUR APP BY ANY THIRD PARTY; OR (E) ANY ERRORS OR OMISSIONS IN ANY CONTENT.

THE DEVELOPER'S TOTAL CUMULATIVE LIABILITY ARISING OUT OF OR RELATING TO THIS AGREEMENT OR YOUR USE OF THE APP WILL NOT EXCEED THE AMOUNT YOU PAID FOR THE APP, OR USD $50, WHICHEVER IS GREATER.

---

## 9. Termination

This Agreement is effective until terminated. Your rights under this Agreement will terminate automatically without notice if you fail to comply with any of its terms. Upon termination you must stop all use of the App and delete it from all devices you own or control. The provisions of Sections 3, 5, 7, 8, 9, 10, 11, and 12 will survive termination.

---

## 10. Apple-Specific Terms

You acknowledge and agree:

- This Agreement is between you and the Developer only, not with Apple. Apple is not responsible for the App or its content.
- Apple has no obligation to provide maintenance or support for the App.
- Apple is not responsible for addressing any claims by you or any third party relating to the App, including product liability claims, claims that the App fails to conform to legal or regulatory requirements, and claims arising under consumer protection or similar legislation.
- In the event the App fails to conform to any applicable warranty, you may notify Apple, who will refund the purchase price for the App. To the maximum extent permitted by law, Apple will have no other warranty obligation whatsoever with respect to the App.
- Apple and Apple's subsidiaries are third-party beneficiaries of this Agreement, and upon your acceptance of the terms of this Agreement, Apple will have the right (and will be deemed to have accepted the right) to enforce this Agreement against you as a third-party beneficiary.
- You represent and warrant that (i) you are not located in a country that is subject to a U.S. Government embargo, or that has been designated by the U.S. Government as a "terrorist supporting" country; and (ii) you are not listed on any U.S. Government list of prohibited or restricted parties.

---

## 11. Governing Law

This Agreement is governed by and construed in accordance with the laws of New South Wales, Australia, without regard to its conflict of law principles. Any dispute arising out of or relating to this Agreement will be subject to the exclusive jurisdiction of the courts of New South Wales, Australia, except where such exclusive jurisdiction is precluded by applicable law (including mandatory consumer-protection law in your jurisdiction).

---

## 12. Changes to this Agreement

We may update this Agreement from time to time. The "Last updated" date at the top of this document indicates when the Agreement was last revised. Material changes will be communicated through the App or via the GitHub repository where this Agreement is hosted. Continued use of the App after a change constitutes acceptance of the revised Agreement.

---

## 13. Contact

If you have questions about this Agreement, contact the Developer at:

**Aristides Lintzeris**
[aristideslintzeris@icloud.com](mailto:aristideslintzeris@icloud.com)

---

_TDLidar is an independent project by Aristides Lintzeris. NDI® is a registered trademark of NDI, LLC._
