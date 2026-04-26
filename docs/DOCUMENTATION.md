# Coda — Complete Documentation

> *22 keys. The distilled form of Cadenza.*

**Version:** v0.1 (concept) · **Date:** April 2026 · **Author:** one7two99  
**Status:** Design complete — hardware not yet available

---

## Table of Contents

1. [Introduction](#introduction)
2. [Design Philosophy](#design-philosophy)
3. [Letter Placement — Frequency + Strength](#letter-placement)
4. [Ergonomic Metrics](#ergonomic-metrics)
5. [Comparison: Coda vs. QWERTZ / Dvorak / Colemak-DH / Cadenza](#comparison)
6. [Layer Architecture](#layer-architecture)
7. [Layer Reference](#layer-reference)
   - [L0 Base](#l0-base)
   - [L-Nav Navigation](#l-nav-navigation)
   - [L-Sym Symbols](#l-sym-symbols)
   - [L-Num Numbers](#l-num-numbers)
   - [L-Code Code & CLI](#l-code-code--cli)
   - [L-WM Tiling WM](#l-wm-tiling-window-manager)
   - [L-Fn Function Keys](#l-fn-function-keys--media)
   - [L-Mouse Mouse](#l-mouse-mouse)
   - [L-Overflow Alpha Overflow](#l-overflow-alpha-overflow)
8. [Tap Dance Reference](#tap-dance-reference)
9. [Macro Reference](#macro-reference)
10. [Combo Reference](#combo-reference)
11. [Hardware & Firmware](#hardware--firmware)
12. [Known Limitations](#known-limitations)
13. [Roadmap](#roadmap)

---

## Introduction

Coda is a 22-key split keyboard layout derived from Cadenza v1.0.0. The core question it answers: *what is the minimum number of keys needed to type German and English prose, write shell scripts, and navigate a tiling window manager — without compromising ergonomics?*

The answer turns out to be 22: nine finger keys per side (index, middle, ring × three rows) plus two thumb keys per side. No pinkies. No inner column.

The name refers to the musical coda — the concentrated concluding passage that distills the movement's essential content. Cadenza is the virtuoso improvisation; Coda is the essential statement that follows.

---

## Design Philosophy

### Core principles

**1. No pinky column — by design, not constraint.**  
The pinky is the weakest finger and the primary source of keyboard-related RSI. Removing it entirely forces better decisions for every other key.

**2. No inner column — inherited from Colemak-DH.**  
Lateral index finger movement destabilises hand position. Colemak-DH was created partly to address this. Coda enforces it physically.

**3. Strongest finger earns highest priority.**  
Index > Middle > Ring within every row. The most frequent letter in each position group goes to the strongest available finger.

**4. A and O on thumbs — the frequency gap solution.**  
Removing the pinky column eliminates two home-row positions. In Colemak-DH those positions hold A (7.4%) and O (5.0%). Moving them to thumbs gives the two highest-frequency non-home letters to the strongest fingers in the hand.

**5. Colemak-DH inner home row preserved.**  
T · S · R (left) and N · E · I (right) are identical to Cadenza. Muscle memory transfers directly.

**6. Frequency × Ergonomic quality = access key assignment.**  
Layer access keys are assigned by multiplying usage frequency with the ergonomic quality of the key position. `A` thumb (Navigation) earns the best position because navigation is the most-used non-alpha function.

**7. Bilateral access for critical layers.**  
Navigation, WM, and Meta are accessible from either hand so the other hand is free for the primary task.

**8. NEIO = ← ↓ ↑ → everywhere.**  
All directional inputs — arrow keys, WM focus switching, window movement — follow the same spatial convention. Once learned, it generalises.

**9. Tap = primary, Hold = secondary.**  
Every tap-dance key's tap function is a letter or the most common action. The hold function is always secondary.

**10. Combos replace dedicated keys where possible.**  
`Space` + `Ent` = Backspace. `N` + `E` = ↑ arrow. `Z` + `K` = Page Up. This frees physical positions for more valuable uses.

---

## Letter Placement

### Combined German + English frequency analysis

```
Rank  Letter  Freq    Position          Rationale
────────────────────────────────────────────────────────────────
  1   E       15.0%   R home middle     Highest freq → best position
  2   N        8.0%   R home index      Strongest R finger
  3   T        7.5%   L home index      Strongest L finger
  4   A        7.4%   L thumb           Solves pinky-removal gap
  5   I        7.3%   R home ring       Colemak home ✓
  6   S        6.8%   L home middle     Colemak home ✓
  7   R        6.5%   L home ring       Colemak home ✓ · ER cross-hand ✓
  8   H        5.5%   R top index       TH cross-hand ✓ · CH inward roll ✓
  9   O        5.0%   R thumb           Solves pinky-removal gap
 10   D        4.7%   L top index       DE cross-hand ✓ (German der/die/das)
 11   L        3.7%   L top ring        EL cross-hand ✓
 12   U        3.6%   R bot ring        Avoids EU and UN same-finger
 13   C        2.8%   R top ring        CH inward roll ✓✓ (German most common digraph)
 14   G        2.5%   L top middle      IG cross-hand ✓ (German -ig ending)
 15   M        2.5%   L bot index       DM, TM same-finger — both rare ✓
 16   W        2.1%   L bot middle      WE cross-hand ✓
 17   F        1.9%   R top middle      FR cross-hand ✓ · hold=Meta
 18   B        1.7%   L bot ring        BR, BL same-finger — low frequency ✓
 19   Z        0.9%   R bot index       Base layer: "zu" is extremely common in German
 20   K        1.0%   R bot middle      EK, FK same-finger — both very rare ✓
────────────────────────────────────────────────────────────────
Overflow layer: P(0.8%) V(0.7%) Y(0.4%) J(0.2%) X(0.1%) Q(0.05%)
```

### Column design — same-finger bigram avoidance

The six finger columns were chosen to avoid placing common bigrams on the same finger:

| Column | Letters | Key same-finger bigrams | Assessment |
|---|---|---|---|
| L-Index | D · T · M | DT ~0.1% | ✓ acceptable |
| L-Middle | G · S · W | SW ~0.1% | ✓ acceptable |
| L-Ring | L · R · B | RL ~0.3%, LB ~0.2% | ✓ acceptable |
| R-Index | H · N · Z | NZ ~0.15% | ✓ acceptable |
| R-Middle | F · E · K | FE ~0.3%, EK ~0.1% | ✓ acceptable |
| R-Ring | C · I · U | CI ~0.1%, IU ~0.05% | ✓ acceptable |

Critical German bigrams avoided: IG cross-hand ✓, CH inward roll ✓, EU different hands ✓, UN different hands ✓.

---

## Ergonomic Metrics

### Measured and estimated values

| Metric | Value | Source |
|---|---|---|
| SFB rate | ~0.90% | Estimated from column pair analysis |
| Home row usage (fingers) | 51.1% | Calculated: T+S+R+N+E+I frequencies |
| Home row usage (fingers + thumbs) | 63.5% | Add A+O on thumbs |
| Pinky load | 0% | No pinky column by design |
| Lateral index stretch | 0 instances | No inner column by design |
| Left/Right hand balance | ~46% / 54% | Right heavy due to E=15% on right middle |
| Heaviest single finger | R-Middle ~17.9% | E(15%) + F(1.9%) + K(1.0%) — but all on home row |

### Finger load distribution

```
L-Ring   11.9%  ████████████
L-Middle 11.4%  ████████████
L-Index  14.7%  ██████████████████
L-Thumb   7.4%  ████████           (letter A)
                ─────────────┼─────────────
R-Thumb   5.0%  ██████             (letter O)
R-Index  14.4%  ██████████████████
R-Middle 17.9%  ██████████████████████  ← E on best key
R-Ring   13.7%  ██████████████████
```

Note: R-Middle's high load (17.9%) is concentrated on the home-row position — the ergonomically best key. High frequency on the best position is ideal, not problematic.

---

## Comparison

### vs. QWERTZ

| Dimension | QWERTZ | Coda | Δ |
|---|---|---|---|
| SFB rate | 6.31% | ~0.90% | **−5.4 pp** |
| Pinky load | ~14% | 0% | **−14 pp** |
| Home row usage | 34% | 64% | **+30 pp** |
| Lateral stretch | Very high | Zero | **eliminated** |
| Umlauts (ä ö ü) | Dedicated keys | Dead key + vowel | ← QWERTZ advantage |
| ß | Dedicated key | AltGr+S (direct keycode) | slight QWERTZ advantage |
| Learning curve | None | Extreme | ← QWERTZ advantage |

QWERTZ was designed for German typesetting machines, not human ergonomics. Its advantage is exclusively institutional — everyone already knows it.

### vs. Dvorak

| Dimension | Dvorak | Coda | Δ |
|---|---|---|---|
| SFB rate | 2.62% | ~0.90% | **−1.7 pp** |
| Home row usage | 71% | 64% | −7 pp |
| Pinky load | ~7% | 0% | **−7 pp** |
| German EI bigram | Varies by config | Adjacent roll | Coda better |
| German CH bigram | Cross-hand | Inward roll | Both good |
| Hand balance | 57% L / 43% R | 46% L / 54% R | Coda more balanced |

Dvorak optimised heavily for home row usage but kept pinkies and placed all vowels on the left hand, creating left-hand overload. Its German support is incidental.

### vs. Colemak-DH

| Dimension | Colemak-DH | Coda | Δ |
|---|---|---|---|
| SFB rate | 1.28% | ~0.90% | **−0.38 pp** |
| Home row usage | 68% | 64% | −4 pp |
| Pinky load | ~6% | 0% | **−6 pp** |
| Lateral stretch | Low (DH mod) | Zero | Coda better |
| German CH bigram | Cross-hand | Inward roll | Comparable |
| German IG bigram | Varies | Cross-hand | **Coda better** |
| Hardware availability | Any keyboard | Custom 22-key PCB | ← Colemak-DH advantage |

Colemak-DH is the strongest traditional alternative. Coda's ergonomic improvements over Colemak-DH are real but incremental. The decisive differences are: zero pinky (not just low), zero lateral (not just reduced), and purpose-built layers for German, CLI, and WM work.

### vs. Cadenza

| Dimension | Cadenza | Coda | Notes |
|---|---|---|---|
| Keys | 36 | 22 | −14 keys |
| Pinky load | ~5% | 0% | Coda eliminates pinkies |
| Base-layer letters | 26 | 20 | Coda has 6 on overflow |
| Layer count | 13 | 9 | Coda has fewer but denser |
| Tap dances | 43 | 34 | Coda uses combos instead of some TDs |
| Firmware | Vial/QMK | QMK keymap.c | Coda requires C for layer-specific combos |
| Hardware | Corne Choc (available) | Custom PCB (concept) | Cadenza advantage |
| Daily driver | Yes | Not yet | Cadenza is current daily driver |

Coda is not a replacement for Cadenza. It is a design study that pushes the ergonomic principles to their logical conclusion, and may inform future Cadenza iterations.

---

## Layer Architecture

### Access key summary

```
Single thumb hold:
  A   hold  →  Navigation        (left inner thumb)
  Spc hold  →  Symbols           (left outer thumb)
  O   hold  →  Numbers           (right inner thumb)
  Ent hold  →  Code / CLI        (right outer thumb)

Finger key hold (bilateral):
  G   hold  →  WM  (left mid top  — right hand free for WM ops)
  H   hold  →  WM  (right idx top — left hand free for numpad ★)
  L   hold  →  Meta (left ring top)
  F   hold  →  Meta (right mid top)

Two-thumb hold combos:
  O  + Ent  hold  →  Function Keys + Media
  A  + Spc  hold  →  Mouse
  A  + Ent  hold  →  Alpha Overflow (P V Y J X Q ß €)

Two-thumb tap combos:
  Spc + Ent  →  Backspace ★
  A   + O    →  Escape
  A   + Ent  →  Tab
  Spc + O    →  Delete

Layer-specific combos (Nav layer only):
  N + E  →  ↑ up arrow
  Z + K  →  Page Up
```

### Priority rationale

The most-used layer earns the best key position:
1. **Navigation** — arrows, word skip, clipboard: left inner thumb (`A`) — most frequent non-alpha action
2. **Symbols** — every comma and equals sign: left outer thumb (`Spc`) — second
3. **Numbers** — right inner thumb (`O`) — third
4. **Code/CLI** — right outer thumb (`Ent`) — fourth
5. **WM** — index top-row hold (bilateral `G`/`H`) — deliberate access, not reflex
6. **Meta** — ring/middle top-row hold (bilateral `L`/`F`) — composable modifier

---

## Layer Reference

### L0 Base

```
 ┌───┬───┬───┐    ┌───┬───┬───┐
 │ D │ G │ L │    │ H │ F │ C │
 │   │WM*│⊞* │    │WM*│⊞* │   │   * = hold function
 ├───┼───┼───┤    ├───┼───┼───┤
 │ T │ S │ R │    │ N │ E │ I │
 │⇧* │⌃* │⌥* │    │⇧* │⌃* │⎇* │
 ├───┼───┼───┤    ├───┼───┼───┤
 │ M │ W │ B │    │ Z │ K │ U │
 └───┴───┴───┘    └───┴───┴───┘
     ┌───┬───┐    ┌───┬───┐
     │ A │Spc│    │ O │Ent│
     │Nav│Sym│    │Num│CLI│
     └───┴───┘    └───┴───┘

⇧=Shift ⌃=Ctrl ⌥=Alt ⎇=AltGr ⊞=Meta/Super WM=WM layer
```

**Home row mods (HRM):** Tap Dance on all home-row keys. Tipping terms: index/middle 200 ms, ring 250 ms.

| Key | Tap | Hold | Side |
|---|---|---|---|
| T | t | Shift | Left index |
| S | s | Ctrl | Left middle |
| R | r | Alt | Left ring (250 ms) |
| N | n | Shift | Right index |
| E | e | Ctrl | Right middle |
| I | i | AltGr | Right ring (250 ms) |

**Layer access holds:**

| Key | Tap | Hold |
|---|---|---|
| G | g | MO(WM) |
| L | l | Meta/Super |
| H | h | MO(WM) |
| F | f | Meta/Super |

---

### L-Nav Navigation

*Access: Hold `A` (left inner thumb). Left hand holds, right hand navigates.*

```
 ┌─────────┬─────────┬──────┐    ┌──────────┬──────────┬──────┐
 │  Meta   │ Ctrl+←  │ Caps │    │  Ctrl+←  │  Ctrl+→  │ Del  │
 ├─────────┼─────────┼──────┤    ├──────────┼──────────┼──────┤
 │  Shift  │  Ctrl   │  Alt │    │    ←     │    ↓     │  →   │
 ├─────────┼─────────┼──────┤    ├──────────┼──────────┼──────┤
 │  Undo   │  Copy   │ Paste│    │   Home   │  PgDn   │ End  │
 └─────────┴─────────┴──────┘    └──────────┴──────────┴──────┘
     ┌──────┬──────┐                  ┌──────┬──────┐
     │ held │  Cut │                  │Scrl↑ │ Redo │
     └──────┴──────┘                  └──────┴──────┘
```

**Nav-layer combos (QMK COMBO_ONLY_FROM_LAYER):**

| Combo | Output | Fingers |
|---|---|---|
| N + E simultaneously | ↑ up arrow | Right index + middle (adjacent, comfortable) |
| Z + K simultaneously | Page Up | Right index + middle, bottom row |

**Design rationale:** All four arrows on the right home row. ↑ via combo frees H for word navigation (Ctrl+←/→). No row-jumping needed for basic navigation. Modifiers on left for selection (Shift+arrow) and word-skip (Ctrl+arrow).

---

### L-Sym Symbols

*Access: Hold `Space` (left outer thumb). Both hands free.*

```
 ┌───┬───┬───┐    ┌───────┬───────┬───┐
 │ ! │ # │ @ │    │ < | > │ [ | ] │ ; │
 ├───┼───┼───┤    ├───────┼───────┼───┤
 │ = │ - │ / │    │   .   │   ,   │ : │
 ├───┼───┼───┤    ├───────┼───────┼───┤
 │ & │ | │ \ │    │   ?   │   `   │ { │ ← { via TD: tap={  hold=}
 └───┴───┴───┘    └───────┴───────┴───┘
     ┌───┬──────┐    ┌───┬───┐
     │ _ │ held │    │ % │ * │
     └───┴──────┘    └───┴───┘

| = bracket pairs via Tap Dance (tap=open, hold=close)
```

**Frequency ranking (code + German prose combined):**

| Rank | Symbol | Key | Rationale |
|---|---|---|---|
| 1 | `=` | T (left index) | Strongest left finger |
| 2 | `-` | S (left middle) | Very common: dash, subtraction, CSS |
| 3 | `/` | R (left ring) | Paths, division, regex |
| 4 | `.` | N (right index) | Sentence end, decimal, method access |
| 5 | `,` | E (right middle) | Separator |
| 6 | `:` | I (right ring) | Python, YAML, JSON |

**Bracket pairs (Tap Dance):** tap = open · hold = close:
- `H` on Sym → `(` tap · `)` hold
- `F` on Sym → `[` tap · `]` hold
- `U` on Sym → `{` tap · `}` hold
- Right top: `<` tap · `>` hold (TD_ANGLE)

---

### L-Num Numbers

*Access: Hold `O` (right inner thumb). Right hand holds, left hand uses numpad.*

```
 ┌───┬───┬───┐    ┌───┬───┬───┐
 │ 7 │ 8 │ 9 │    │ . │ / │ = │
 ├───┼───┼───┤    ├───┼───┼───┤
 │ 4 │ 5 │ 6 │    │ ( │ ) │ * │
 ├───┼───┼───┤    ├───┼───┼───┤
 │ 1 │ 2 │ 3 │    │ , │ - │ € │
 └───┴───┴───┘    └───┴───┴───┘
     ┌───┬───┐    ┌──────┬───┐
     │ 0 │ . │    │ held │Ent│
     └───┴───┘    └──────┴───┘

Numpad: ring=1/4/7  middle=2/5/8  index=3/6/9  (matches L5 in Cadenza)
€ = AltGr+5 direct keycode
```

**Spatial memory:** Same finger positions as Cadenza's L5 Numbers layer. Once learned, the positions transfer directly to the WM layer workspace numbers.

---

### L-Code Code & CLI

*Access: Hold `Ent` (right outer thumb). Left hand holds, right hand free for operators.*

```
 ┌─────┬─────┬─────┐    ┌────────────┬────────────┬──────────┐
 │     │     │     │    │    => ->   │            │          │
 ├─────┼─────┼─────┤    ├────────────┼────────────┼──────────┤
 │ | │ │ && │ || │    │  / ~/ ../  │ $() ${}   │  != ==   │
 ├─────┼─────┼─────┤    ├────────────┼────────────┼──────────┤
 │     │     │     │    │    $?      │   2>&1     │          │
 └─────┴─────┴─────┘    └────────────┴────────────┴──────────┘
     ┌─────┬─────┐    ┌─────┬──────┐
     │     │ Spc │    │     │ held │
     └─────┴─────┘    └─────┴──────┘

Key positions on right hand:
  N (idx home)  = TD: / (tap) · ~/ (hold) · ../ (double)
  E (mid home)  = TD: $() (tap, cursor inside) · ${} (hold, cursor inside)
  I (rng home)  = TD: != (tap) · == (hold)
  H (idx top)   = TD: => (tap) · -> (hold)
  Z (idx bot)   = $? (last exit code)
  K (mid bot)   = 2>&1 (stderr redirect)

Left hand (deliberate order):
  T (idx home)  = " | " (pipe with spaces) — M11 macro
  S (mid home)  = && (and-chain) — M15 macro
  R (rng home)  = || (or-chain) — M16 macro
```

**Design note:** The left home row order (pipe / && / ||) is intentional — not frequency order, but conceptual grouping from most-used to least-used in typical shell pipelines. Same convention as Cadenza L9.

---

### L-WM Tiling Window Manager

*Access: Hold `H` (right index top) → left hand free for numpad workspace selection.*  
*Alternate: Hold `G` (left middle top) → right hand free for WM operations.*

```
WS numpad positions (left hand) — ring=1/4/7, mid=2/5/8, idx=3/6/9:

 ┌──────┬──────┬──────┐    ┌─────────┬──────────┬───────────┐
 │ WS7  │ WS8  │ WS9  │    │  ⊞+→   │ Full     │ Float     │
 │  L   │  G   │  D   │    │  focus  │  ⊞+F    │  ⊞+Spc   │
 ├──────┼──────┼──────┤    ├─────────┼──────────┼───────────┤
 │ WS4  │ WS5  │ WS6  │    │  ⊞+←   │  ⊞+↓    │  ⊞+↑     │
 │  R   │  S   │  T   │    │  focus  │  focus   │  focus    │
 ├──────┼──────┼──────┤    ├─────────┼──────────┼───────────┤
 │ WS1  │ WS2  │ WS3  │    │  ⊞⇧+← │  ⊞⇧+↓  │  ⊞⇧+↑  │
 │  B   │  W   │  M   │    │  win←   │  win↓    │  win↑     │
 └──────┴──────┴──────┘    └─────────┴──────────┴───────────┘
     ┌──────┬──────┐    ┌──────┬──────┐
     │ WS10 │ held │    │ held │ Kill │
     │  A   │      │    │      │ ⊞⇧Q │
     └──────┴──────┘    └──────┴──────┘

Each WS key = Tap Dance:
  Tap  = ⊞+N  → go to workspace N
  Hold = ⊞⇧+N → move focused window to workspace N
```

**WM focus switching (right home):** N=⊞+← · E=⊞+↓ · I=⊞+↑ · H=⊞+→ (top index)  
**Window movement (right bottom):** Z=⊞⇧+← · K=⊞⇧+↓ · U=⊞⇧+↑

**Meta for ad-hoc WM shortcuts:**  
Hold `L` or `F` for Meta, then press any key: `L`+`Ent`=⊞+Enter (open terminal), `L`+`N`(Shift)=⊞⇧ etc.

---

### L-Fn Function Keys & Media

*Access: Hold `O` + `Ent` simultaneously (both right thumbs).*

```
 ┌────┬────┬────┐    ┌──────┬──────┬───────┐
 │ F7 │ F8 │ F9 │    │ Prev │PrtSc │ ScrLk │
 ├────┼────┼────┤    ├──────┼──────┼───────┤
 │ F4 │ F5 │ F6 │    │ F10  │ F11  │  F12  │
 ├────┼────┼────┤    ├──────┼──────┼───────┤
 │ F1 │ F2 │ F3 │    │ Mute │ Play │ Stop  │
 └────┴────┴────┘    └──────┴──────┴───────┘
     ┌──────┬──────┐    ┌──────┬──────┐
     │ Vol- │ Vol+ │    │ held │ held │
     └──────┴──────┘    └──────┴──────┘

F1–F9 on left in numpad positions (same spatial shape as L-Num)
```

---

### L-Mouse Mouse

*Access: Hold `A` + `Space` simultaneously (both left thumbs).*

```
 ┌──────┬──────┬──────┐    ┌──────┬───────┬──────┐
 │ Meta │      │      │    │ M↑   │ Scrl↑ │      │
 ├──────┼──────┼──────┤    ├──────┼───────┼──────┤
 │Shift │ Ctrl │  Alt │    │ M←   │  M↓   │  M→  │
 ├──────┼──────┼──────┤    ├──────┼───────┼──────┤
 │      │      │      │    │      │ Scrl↓ │      │
 └──────┴──────┴──────┘    └──────┴───────┴──────┘
     ┌──────┬──────┐    ┌──────┬──────┐
     │ held │ held │    │ Btn1 │ Btn2 │
     └──────┴──────┘    └──────┴──────┘

Mouse movement: N(←) E(↓) I(→) H(↑) — right hand
Modifiers left for Shift-click, Ctrl-click
```

---

### L-Overflow Alpha Overflow

*Access: Hold `A` + `Ent` simultaneously.*

```
 ┌───┬───┬───┐    ┌───┬───┬───┐
 │ J │ X │ Q │    │   │   │   │
 ├───┼───┼───┤    ├───┼───┼───┤
 │ P │ V │ Y │    │ ä │ ö │ ü │
 ├───┼───┼───┤    ├───┼───┼───┤
 │   │   │   │    │ ß │ € │   │
 └───┴───┴───┘    └───┴───┴───┘

P/V/Y on left home (strongest, most frequent of the overflow letters)
ä/ö/ü via " dead key + vowel (US International — no separate macro needed)
ß = AltGr+S direct keycode · € = AltGr+5 direct keycode
```

---

## Tap Dance Reference

*Total: 34 tap dances. QMK `keymap.c` — no slot limit.*

### Layer access (4)

| TD | Key | Tap | Hold | Term |
|---|---|---|---|---|
| TD_A | A (L thumb) | a | MO(Nav) | 200 ms |
| TD_SPC | Space (L thumb) | Space | MO(Sym) | 200 ms |
| TD_O | O (R thumb) | o | MO(Num) | 200 ms |
| TD_ENT | Enter (R thumb) | Enter | MO(Code) | 200 ms |

### Bilateral WM + Meta (4)

| TD | Key | Tap | Hold | Term |
|---|---|---|---|---|
| TD_G | G | g | MO(WM) | 200 ms |
| TD_H | H | h | MO(WM) | 200 ms |
| TD_L | L | l | KC_LGUI (Meta) | 250 ms |
| TD_F | F | f | KC_LGUI (Meta) | 250 ms |

### Home Row Mods (6)

| TD | Key | Tap | Hold | Term |
|---|---|---|---|---|
| TD_T | T | t | KC_LSFT | 200 ms |
| TD_S | S | s | KC_LCTL | 200 ms |
| TD_R | R | r | KC_LALT | **250 ms** |
| TD_N | N | n | KC_RSFT | 200 ms |
| TD_E | E | e | KC_RCTL | 200 ms |
| TD_I | I | i | KC_RALT (AltGr) | **250 ms** |

### Symbol pairs — Sym layer (6)

| TD | Tap | Hold | Usage |
|---|---|---|---|
| TD_PAREN | `(` | `)` | Sym layer H |
| TD_SQBR | `[` | `]` | Sym layer F |
| TD_CURL | `{` | `}` | Sym layer U |
| TD_ANGLE | `<` | `>` | Sym layer right top |
| TD_QUOTE | `"` dead key | `"` literal (M9) | Sym · L10 German umlauts |
| TD_BTICK | `` ` `` dead key | `` ` `` literal (M10) | Sym · double = ` ``` ` (M11) |

### Code actions — Code layer (4)

| TD | Tap | Hold | Double | Usage |
|---|---|---|---|---|
| TD_SLASH | `/` | `~/` (M1) | `../` (M2) | Code N — path navigation |
| TD_EXP | `$()` + ← (M3) | `${}` + ← (M4) | — | Code E — expansion |
| TD_CMP | `!=` (M5) | `==` (M6) | — | Code I — comparison |
| TD_ARR | `=>` (M7) | `->` (M8) | — | Code H — arrows |

### Workspace tap/hold — WM layer (10)

| TD | Tap | Hold | Position |
|---|---|---|---|
| TD_WS1 | `LGUI(KC_1)` ⊞+1 | `SGUI(KC_1)` ⊞⇧+1 | B (L-bot-ring) |
| TD_WS2 | `LGUI(KC_2)` | `SGUI(KC_2)` | W (L-bot-mid) |
| TD_WS3 | `LGUI(KC_3)` | `SGUI(KC_3)` | M (L-bot-idx) |
| TD_WS4 | `LGUI(KC_4)` | `SGUI(KC_4)` | R (L-hom-ring) |
| TD_WS5 | `LGUI(KC_5)` | `SGUI(KC_5)` | S (L-hom-mid) |
| TD_WS6 | `LGUI(KC_6)` | `SGUI(KC_6)` | T (L-hom-idx) |
| TD_WS7 | `LGUI(KC_7)` | `SGUI(KC_7)` | L (L-top-ring) |
| TD_WS8 | `LGUI(KC_8)` | `SGUI(KC_8)` | G (L-top-mid) |
| TD_WS9 | `LGUI(KC_9)` | `SGUI(KC_9)` | D (L-top-idx) |
| TD_WS10 | `LGUI(KC_0)` | `SGUI(KC_0)` | A (L-thumb) |

---

## Macro Reference

*Total: 16 macros. In QMK `keymap.c` these are C functions with no slot limit.*

| ID | Output | Function | Triggered by |
|---|---|---|---|
| M1 | `~/` | Home directory | TD_SLASH hold |
| M2 | `../` | Parent directory | TD_SLASH double |
| M3 | `$()` + ← | Shell expansion, cursor inside | TD_EXP tap |
| M4 | `${}` + ← | Variable expansion, cursor inside | TD_EXP hold |
| M5 | `!=` | Not equal | TD_CMP tap |
| M6 | `==` | Equal | TD_CMP hold |
| M7 | `=>` | Fat arrow (Python, JS, Rust) | TD_ARR tap |
| M8 | `->` | Thin arrow / pointer (C, Rust, PHP) | TD_ARR hold |
| M9 | `"` + Space | Literal quote (US Intl dead-key bypass) | TD_QUOTE hold |
| M10 | `` ` `` + Space | Literal backtick (US Intl dead-key bypass) | TD_BTICK hold |
| M11 | ` ``` ` | Markdown code fence | TD_BTICK double |
| M12 | ` 2>&1 ` | Stderr redirect with spaces | Code K |
| M13 | ` \| ` | Pipe with surrounding spaces | Code T |
| M14 | `$?` | Last exit code | Code Z |
| M15 | `&&` | And-chain | Code S |
| M16 | `\|\|` | Or-chain | Code R |

---

## Combo Reference

*Total: 9 combos — 7 global, 2 Nav-layer-specific.*

### Global combos (active on all layers)

| Keys | Type | Output | Notes |
|---|---|---|---|
| Space + Enter | tap | Backspace | Most important — pressed dozens/hour |
| A + O | tap | Escape | Cross-hand, unambiguous |
| A + Enter | tap | Tab | Cross-hand diagonal |
| Space + O | tap | Delete | Cross-hand diagonal |
| O + Enter | hold | L-Fn layer | Both right thumbs held |
| A + Space | hold | L-Mouse layer | Both left thumbs held |
| A + Enter | hold | L-Overflow layer | Cross-hand hold |

### Nav-layer combos (`COMBO_ONLY_FROM_LAYER`)

| Keys | Output | Physical motion |
|---|---|---|
| N + E | ↑ up arrow | Right index + middle simultaneously (adjacent, comfortable) |
| Z + K | Page Up | Right index + middle, bottom row |

**QMK implementation note:** Nav combos use `COMBO_ONLY_FROM_LAYER` or a layer check in the combo action:

```c
bool get_combo_must_hold(uint16_t index, combo_t *combo) {
    return false;  // all tap combos
}

uint8_t combo_ref_from_layer(uint8_t layer) {
    switch (layer) {
        case _NAV: return _NAV;  // Nav combos only active in Nav layer
        default:   return _BASE;
    }
}
```

---

## Hardware & Firmware

### Hardware requirements

Coda requires a custom 22-key split PCB:
- 3×3 finger matrix per half (no pinky column, no inner column)
- 2 thumb keys per half
- MX or Choc spacing depending on preference
- Split communication (TRRS or USB)

No commercial PCB matching this exact specification exists as of 2026. The closest approach is a Corne Choc with the outer (pinky) column physically removed, though this requires PCB modification.

### Firmware

Coda targets QMK `keymap.c` rather than Vial for three reasons:

1. **Layer-specific combos** — `COMBO_ONLY_FROM_LAYER` enables the Nav-layer ↑ and PgUp combos without triggering on base layer
2. **34 Tap Dances** — manageable in C, unwieldy in Vial's GUI
3. **16+ macros** — no slot limit in C; Vial limits to 16

```c
// config.h
#define TAP_DANCE_ENTRIES 34
#define COMBO_COUNT 9
#define TAPPING_TERM 200       // default; overridden per-key for ring/pinky
#define PERMISSIVE_HOLD        // helps with HRM in fast typing
#define HOLD_ON_OTHER_KEY_PRESS  // for layer-access thumbs

// OS keyboard layout: US International (required for dead keys and AltGr combos)
// ß = RALT(KC_S) · € = RALT(KC_5) · dead " for ä/ö/ü
```

---

## Known Limitations

| Limitation | Severity | Workaround |
|---|---|---|
| Custom hardware doesn't exist | Critical | Use Ferris Sweep (34 keys) as interim |
| Backspace is a combo | High | Muscle memory adapts in 1–2 weeks |
| P, V on overflow layer | Medium | ~1.5% of characters need extra hold |
| Meta + Alt same finger (L and R both left ring) | Medium | Remap ⊞+Alt shortcuts in WM config |
| German umlauts via dead key (vs QWERTZ dedicated) | Low | Standard on non-QWERTZ German setups |
| No ⊞⇧+→ (win right) on WM layer | Low | Use resize mode or add to right thumb |
| Extreme learning curve | Expected | Not a bug — this is a new paradigm |

---

## Roadmap

### v0.1 — Current (concept)
- [x] Complete letter placement with bigram analysis
- [x] Full layer system (9 layers)
- [x] 34 tap dances specified
- [x] 16 macros specified
- [x] 9 combos specified
- [x] WM integration with bilateral access
- [x] Meta bilateral (L+F)
- [x] Nav redesign with combo-based ↑ and PgUp
- [x] Ergonomic comparison vs QWERTZ, Dvorak, Colemak-DH, Cadenza

### v0.2 — Hardware prototype
- [ ] Commission or design custom 22-key PCB
- [ ] Build and flash QMK firmware
- [ ] Real-world tipping term validation
- [ ] Measure actual SFB rate with keylog analysis
- [ ] Validate combo timing (N+E for ↑, Z+K for PgUp)

### v0.3 — Daily driver validation
- [ ] 30-day daily use period
- [ ] WPM and error rate tracking
- [ ] Layer usage heatmap analysis
- [ ] Adjust symbol layer based on actual usage patterns
- [ ] Evaluate P/V frequency impact in practice

### v1.0 — Stable release
- [ ] Hardware design finalised and open-sourced
- [ ] QMK firmware published
- [ ] All tipping terms validated
- [ ] Documentation complete with actual (not estimated) metrics

---

*Coda v0.1 · April 2026 · one7two99 · MIT License*  
*Sibling of [Cadenza](https://github.com/one7two99/cadenza) · Based on Colemak-DH by stevep99*
