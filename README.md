<div align="center">

```
  ┌─────────────────────────────────────────────────┐
  │                                                 │
  │                   C  O  D  A                    │
  │                                                 │
  │          22 keys. The distilled form.           │
  │                                                 │
  └─────────────────────────────────────────────────┘
```

  <p>
    <img src="https://img.shields.io/badge/status-concept-orange?style=flat-square" alt="Status">
    <img src="https://img.shields.io/badge/keys-22-blue?style=flat-square" alt="Keys">
    <img src="https://img.shields.io/badge/base-Colemak--DH-purple?style=flat-square" alt="Base">
    <img src="https://img.shields.io/badge/firmware-QMK%20keymap.c-red?style=flat-square" alt="Firmware">
    <img src="https://img.shields.io/badge/tap%20dances-34-yellow?style=flat-square" alt="TDs">
    <img src="https://img.shields.io/badge/SFB-~0.90%25-brightgreen?style=flat-square" alt="SFB">
    <img src="https://img.shields.io/github/license/one7two99/coda?style=flat-square" alt="License">
  </p>

</div>

---

> *Coda (n.): the concluding passage — a concentrated, essential statement that brings everything together.*

**Coda** is a 22-key split keyboard layout and the minimal sibling of [Cadenza](https://github.com/one7two99/cadenza). It removes the pinky column and inner column entirely — not as a constraint, but as a deliberate ergonomic choice. The result is a layout with zero pinky load, zero lateral index stretch, and an estimated SFB rate of ~0.90% — lower than Colemak-DH.

> *22 keys. The distilled form.*

---

## ✦ The Coda family

```
Cadenza   36 keys   Full layout — Vial/QMK, all 13 layers, daily driver
Coda      22 keys   Distilled form — QMK keymap.c, concept stage
```

Coda shares Cadenza's design DNA: Colemak-DH base, Home Row Mods via Tap Dance, frequency-ranked symbol placement, dedicated CLI and International layers, and bilateral access for critical functions. What changes is the physical constraint: 3 fingers per side instead of 5, 2 thumbs per side instead of 3.

---

## ✦ Physical layout

```
 Left              Right
 ┌───┬───┬───┐    ┌───┬───┬───┐
 │ D │ G │ L │    │ H │ F │ C │   ← top row
 ├───┼───┼───┤    ├───┼───┼───┤
 │ T │ S │ R │    │ N │ E │ I │   ← home row  ← fingers rest here
 ├───┼───┼───┤    ├───┼───┼───┤
 │ M │ W │ B │    │ Z │ K │ U │   ← bottom row
 └───┴───┴───┘    └───┴───┴───┘
         ┌───┬───┐    ┌───┬───┐
         │ A │Spc│    │ O │Ent│   ← thumbs
         └───┴───┘    └───┴───┘

  Fingers: Index · Middle · Ring  (no Pinky, no Inner column)
```

**22 positions total.** The Colemak-DH inner home row — `T S R` / `N E I` — is preserved unchanged. `A` (7.4%) and `O` (5.0%) move from pinky keys to thumbs, solving the frequency gap created by removing the outer column.

---

## ✦ Why remove the pinky?

The pinky finger is responsible for the highest incidence of repetitive strain injury in keyboard users. It is simultaneously the weakest finger and — on a standard layout — one of the most heavily loaded:

| Layout | Pinky load | Lateral stretch |
|---|---|---|
| QWERTZ | ~14% | Very high |
| Dvorak | ~7% | Moderate |
| Colemak-DH | ~6% | Low |
| **Coda** | **0%** | **Zero** |

---

## ✦ Key metrics

| Metric | QWERTZ | Dvorak | Colemak-DH | **Coda** |
|---|---|---|---|---|
| SFB rate | 6.31% | 2.62% | 1.28% | **~0.90%** |
| Home row usage | 34% | 71% | 68% | **64%** |
| Pinky load | 14% | 7% | 6% | **0%** |
| Lateral index stretch | Very high | Moderate | Low | **Zero** |
| German CH bigram | Same-finger | Cross-hand | Cross-hand | **Inward roll** |
| German IG bigram | Same-hand | Varies | Varies | **Cross-hand** |

*SFB = Same-Finger Bigrams. QWERTZ, Dvorak, Colemak-DH values documented (carpalx / Patrick Steele corpus). Coda estimated from column analysis. German + English combined corpus.*

---

## ✦ Layer overview

| Layer | Access | Purpose |
|---|---|---|
| **L0 Base** | Always active | 20 letters · Tap Dance HRM |
| **L-Nav** | Hold `A` | Arrows · Word nav · Modifiers |
| **L-Sym** | Hold `Space` | Symbols · Punctuation · Brackets |
| **L-Num** | Hold `O` | Numpad 1–9 · Operators |
| **L-Code** | Hold `Ent` | Shell operators · Path nav · Code macros |
| **L-WM** | Hold `G` or `H` | Workspaces 1–10 · Focus · Window movement |
| **L-Fn** | Hold `O` + `Ent` | F1–F12 · Media |
| **L-Mouse** | Hold `A` + `Space` | Pointer · Scroll · Buttons |
| **L-Overflow** | Hold `A` + `Ent` | P V Y J X Q · ß € |

### Access key design

Layer access follows **Frequency × Ergonomic Quality**:

- `A` thumb → Navigation (most-used directional layer)
- `Space` thumb → Symbols (second most-used)
- `O` thumb → Numbers (third)
- `Ent` thumb → Code/CLI (fourth)
- `G` / `H` holds → WM (bilateral — hold right hand, left free for numpad)

---

## ✦ Highlights

- **Zero pinky load** — physically impossible on this hardware
- **Zero lateral stretch** — no inner column exists
- **Colemak-DH home row preserved** — T·S·R / N·E·I identical to Cadenza
- **A and O on thumbs** — the two highest-frequency non-home letters on the strongest fingers
- **CH as inward roll** — German's most common digraph (2.4%) is a fast right-hand roll
- **IG cross-hand** — German `-ig` endings (richtig, wenig) never cause same-finger bigrams
- **Bilateral WM + Meta** — `G`/`H` for WM · `L`/`F` for Meta · left hand free for numpad
- **Nav combos** — all 4 arrows on home row: `N`=← `E`=↓ `I`=→ `N+E`=↑
- **Pre-encoded WM shortcuts** — tap=⊞+N · hold=⊞+⇧+N, no manual Meta hold needed
- **QMK keymap.c** — unlimited macros, layer-specific combos, full C programmability

---

## ✦ Honest limitations

- **⚠ Concept only** — no commercial 22-key PCB with this exact layout exists yet
- **Steep learning curve** — new hardware paradigm + layers + combos
- **Backspace is a combo** — `Space` + `Ent` simultaneously
- **Symbols require layer hold** — every comma and period needs a thumb hold
- **P, V on overflow** — ~1.5% of characters are one step deeper
- **Meta + Alt conflict** — `L` (Meta) and `R` (Alt) share the left ring finger

---

## ✦ Hardware

Coda requires a custom 22-key split PCB. Closest commercial options:

| Board | Keys | Gap |
|---|---|---|
| Ferris Sweep | 34 | Has pinkies + inner column |
| Ferris Sweep Bling | 34 | Same |
| Absolem | 46 | Too many keys |
| **Custom PCB** | **22** | **Target hardware** |

The Coda PCB would be a Corne Choc variant with the outer (pinky) column physically absent.

---

## ✦ Firmware

Coda targets **QMK `keymap.c`** — not Vial. Reasons:

- Layer-specific combos require `COMBO_ONLY_FROM_LAYER` — not available in Vial
- 34 Tap Dance definitions exceed Vial's ergonomic management threshold
- Unlimited macros in C vs. 16 in Vial
- Full git history of every key decision

```c
// config.h
#define TAP_DANCE_ENTRIES 34
#define COMBO_COUNT 9
#define COMBO_ONLY_FROM_LAYER  // layer-specific combos for Nav ↑ and PgUp
```

---

## ✦ Documentation

| File | Contents |
|---|---|
| [`docs/index.html`](https://one7two99.github.io/coda/) | Complete design documentation in a nice HTML file which can be downloaded, showing all layers, tap dances, macros, combos |
| [`docs/DOCUMENTATION.md`](docs/DOCUMENTATION.md) | Complete design documentation — principles, metrics, all layers, TD/macro/combo reference |
| [`docs/coda_compare.png`](docs/coda_compare.png) | Ergonomic comparison — radar chart + metrics vs QWERTZ/Dvorak/Colemak-DH |

---

## ✦ Relationship to Cadenza

Coda emerged from [Cadenza v1.0.0](https://github.com/one7two99/cadenza) as a design exercise: *what if we removed everything non-essential?* The core home row, the HRM model, the CLI layer, the International layer, and the WM layer all carry over. What Coda adds is the radical physical constraint that forces every design decision to be justified.

Cadenza is the daily driver. Coda is the thought experiment that sharpens it.

---

## ✦ License

Designed by **one7two99** · [MIT](LICENSE) · 2026

> *Sibling of [Cadenza](https://github.com/one7two99/cadenza) · Based on [Colemak-DH](https://colemakmods.github.io/mod-dh/) by stevep99*
