# Mobile Adaptation: "Deutsch b'Darija" (Bauhaus × Moroccan Zellige)

Adapt and optimize the tactile, portfolio-grade **"Bauhaus × Moroccan Zellige"** web application so it looks stunning, ergonomic, and effortless to navigate on smartphones (360px–430px viewports) while maintaining the exact same neo-brutalist visual identity, 3D borders, mascots, and sound design.

---

## User Review & Critical Decisions

> [!IMPORTANT]
> The brand identity, color palette, custom SVG mascots (*Ostaz Bouchaib*, *Umlaut Monster*, *Brand Emblem*), and Web Audio sound synthesizer are preserved 100%. All changes focus strictly on mobile responsiveness, touch hitboxes, and one-handed thumb ergonomics.

- **Confirmed Decision 1 (Sticky Header)**: Compact sticky mobile header with streamlined badges (flame streak + XP pill), mute toggle, and an ultra-clean 3-way language switcher (`🇲🇦` | `🇸🇦` | `🇬🇧`) fitting comfortably on 360px screens without horizontal overflow.
- **Confirmed Decision 2 (Roadtrip Journey Map)**: Full-width lesson cards aligned along an anchored vertical transit track (side-aligned rail with glowing milestone nodes and animated dashes) replacing the desktop snake curve on narrow screens.
- **Confirmed Decision 3 (Thumb Ergonomics)**: Lesson Studio step navigation and *Der/Die/Das* Arcade Blitz buttons are placed in the bottom thumb reach zone with large $\ge 48\text{px}$ touch targets and active 3D press feedback.
- **Confirmed Decision 4 (Bottom Navigation Bar)**: Ergonomic floating bottom navigation bar with adequate bottom padding (`pb-28` / safe-area insets) across all tabs so content and action buttons are never obscured.

---

## 1. Overview & Mobile Ergonomic Concept

- **What It Delivers**: A mobile-first, tactile language learning experience tailored for one-handed smartphone use. Cards, buttons, audio speed triggers, and quizzes feel like a physical handheld gadget without clipping, horizontal scrollbars, or cramped text.
- **Target Audience / Persona**: Moroccan and Arabic speakers on the go (commuting, on mobile data, studying on iPhone/Android devices) wanting fast, fun German lessons (A1–B2) with instant audio and clear cultural humor.
- **Key Value**: Retains the distinctive, artful "Bauhaus × Zellige" neo-brutalism while feeling like a native iOS/Android educational app.

---

## 2. Mobile User Experience & Visual Layout Adaptation

```
┌────────────────────────────────────────────────────────┐
│ [🇩🇪🇲🇦 Logo]  🔥 3   ⭐ 120   [🔊]  [🇲🇦|🇸🇦|🇬🇧]          │ <- Compact Top Bar (54px)
├────────────────────────────────────────────────────────┤
│  [ 🛫 A1 ]   [ 🥨 A2 ]   [ ⚙️ B1 ]   [ 👑 B2 ]          │ <- Horizontal Level Bar
├────────────────────────────────────────────────────────┤
│  │                                                     │
│  ●── [ Card 1: Alphabet & Phonetics       ] [Start]    │ <- Roadside Transit Rail
│  │   XP: +25 · 🔊 1.0x / 0.6x                          │    with Milestone Dots
│  │                                                     │
│  ●── [ Card 2: Personal Pronouns & Sein   ] [Start]    │
│  │   XP: +30 · 5 Min                                   │
│  │                                                     │
│  ▼                                                     │
├────────────────────────────────────────────────────────┤
│       [ 📚 الدروس ]    [ 💬 الحوارات ]    [ 🎯 تمرن ]   │ <- Floating Bottom Nav
└────────────────────────────────────────────────────────┘
```

### A. Compact Sticky Header (`CleanHeader.tsx`)
- **Single-Line Responsive Top Bar**:
  - Left / Brand: Compact logo emblem (34px) + title text that truncates or stays compact (`text-sm font-bold`).
  - Center / Stats: Consolidated pill combining Streak (`🔥 3`) and XP (`⭐ 120`) to save horizontal real estate on sub-390px screens.
  - Sound & Theme: Compact tactile audio toggle icon button ($\ge 44\text{px}$ hitbox).
  - Language Switcher: 3-way segmented pill using country flags (`🇲🇦` | `🇸🇦` | `🇬🇧`) on mobile, expanding to full labels on wider screens.
- **Strict 15% Sticky Cap**: Header height stays under 56px, preserving >85% of screen height for learning content.

### B. "Casa-to-Berlin" Roadtrip Journey Map (`LessonsTab.tsx`)
- **Vertical Roadside Transit Track**:
  - On mobile (`< 640px`), instead of a hidden or clipped SVG wave, render an anchored vertical transit track (2.5px solid dark line with dashed styling) running along the leading edge (left in LTR, right in RTL).
  - Each milestone node anchors directly to the transit line with a 36px circular badge (`🛫`, `🥨`, `⚙️`, `👑`, or checkmark if completed).
  - Full-width Bento cards stretch comfortably to the remaining width with generous touch padding.
- **Scrollable Level Selector**:
  - Horizontal swipeable pill bar for A1, A2, B1, and B2 with clean snap behavior and active Gold accent.

### C. Step-by-Step Lesson Studio (`CleanLessonPlayer.tsx`)
- **Bottom Thumb Action Bar**:
  - The "Next / التالي" and "Back / السابق" buttons are anchored into a bottom sticky bar (`sticky bottom-0 p-3 bg-white/95 backdrop-blur-md border-t-2 border-slate-900`) with large 48px hitboxes.
- **Sound & Grammar Lab**:
  - Audio speed buttons (`🔊 1.0x` and `🐢 0.6x`) rendered with high-contrast colored borders and min-h 44px for easy thumb tapping.
  - Interactive **Verb Splitter cannon** (`aufstehen` -> `stehe ... auf!`) reformatted into stacked responsive cards so prefixes don't clip on 360px screens.
- **Quiz Card**:
  - Large full-width vertical option buttons with `active:translate-y-1` tactile feedback and instant audio confirmation.

### D. Arcade Blitz & Bureaucracy Form (`PracticeTab.tsx` & `DialoguesTab.tsx`)
- **Der / Die / Das Arcade Blitz**:
  - 3 large, full-width thumb pads arranged in an ergonomic 3-column grid directly under the German noun card:
    - **`DER` (Majorelle Cobalt `#2563EB`)**
    - **`DIE` (Berliner Pop Coral `#FF3366`)**
    - **`DAS` (Atay Mint Emerald `#00D68F`)**
  - Minimum button height of 56px with bold typography and instant Web Audio feedback.
- **Anmeldung Bureaucracy Form**:
  - Form fields arranged in a clean single-column mobile stack with clear Arabic/Darija labels, helper tooltips, and big "Validate & Stamp / فحص وتوثيق" button.
- **WhatsApp Comic Chat Simulator**:
  - Chat bubbles sized appropriately for mobile screens (max-w 85%), with tap-to-listen audio icons and tap-to-reveal translation cards.

### E. Floating Bottom Navigation & Safe Areas (`App.tsx`)
- Floating 3-tab bar elevated with `shadow-neo` and safe-area inset (`env(safe-area-inset-bottom)`).
- All scrollable main views have `pb-32` to guarantee zero overlap between bottom card buttons and the floating navigation.

---

## 3. Key Product Decisions & Trade-Offs

- **Decision 1: Side-Anchored Transit Track vs. Snake Curve on Mobile**
  - *Chosen*: Side-anchored vertical rail on mobile screens (`< 640px`) and sinuous SVG snake on desktop (`sm:block`).
  - *Why*: Horizontal zig-zagging on 360px–390px phones leaves lesson cards cramped into tiny 140px boxes. A side-anchored rail gives cards 100% of usable reading width while preserving the transit journey motif.
- **Decision 2: Flag-Only Language Pill on Small Screens**
  - *Chosen*: Flag emojis (`🇲🇦` | `🇸🇦` | `🇬🇧`) on mobile viewports; flags + labels (`🇲🇦 الدارجة`) on desktop (`sm:`).
  - *Why*: Prevents header wrapping or awkward multi-line stacks on narrow devices while keeping the 3-way toggle immediately recognizable.
- **Decision 3: Sticky Bottom CTA for Lesson Player**
  - *Chosen*: Pin primary progression buttons to the player viewport bottom.
  - *Why*: In multi-slide lessons, users should never need to scroll down just to click "Next". The action is always within natural thumb reach.

---

## 4. Technical Architecture & Layout Hierarchy

```
┌────────────────────────────────────────────────────────┐
│                        App.tsx                         │
│  ├─ CleanHeader.tsx (Compact 54px Mobile Bar)          │
│  │    ├─ Brand Emblem + Title                          │
│  │    ├─ Combined Streak & XP Badge                    │
│  │    ├─ Web Audio Mute Toggle                         │
│  │    └─ 3-Way Language Segmented Pill                 │
│  │                                                     │
│  ├─ Active Tab View Container (pb-32 safe-area)        │
│  │    ├─ LessonsTab: Side-Rail Roadtrip + Bento Cards  │
│  │    ├─ DialoguesTab: Mobile Form + Chat Simulator    │
│  │    └─ PracticeTab: 3-Pad Blitz + Name Speller + AI  │
│  │                                                     │
│  ├─ Floating Bottom Navigation (3 Tabs, h-16)          │
│  │                                                     │
│  └─ Modals (Lesson Player, Streak Celebration, Kit)    │
│       └─ Max-H 90vh, Bottom Sticky Action Buttons      │
└────────────────────────────────────────────────────────┘
```

---

## 5. Verification Plan

1. **Static Analysis & Compilation**:
   - Run `lint_applet` (`tsc --noEmit`) to verify zero type mismatches or syntax issues.
   - Run `compile_applet` (`npm run build`) to verify Vite bundling.
2. **Viewport Responsiveness Checks**:
   - Test at standard mobile viewports: 360px (Galaxy S), 375px (iPhone SE), 390px (iPhone 13/14), 430px (iPhone Pro Max).
   - Verify zero horizontal scrolling (`overflow-x-hidden`) on mobile viewports.
   - Check that all buttons, audio toggles, and quiz choices have $\ge 44\text{px}$ touch targets.
   - Verify proper RTL alignment when Darija or Arabic is active and LTR alignment for German texts.
