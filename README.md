<img width="1280" height="640" alt="git (1)" src="https://github.com/user-attachments/assets/8920b256-2ba8-4988-b824-5351134eb4bd" />



# cross the line 🎯


## Basic Details
### Team Name: real fighters


### Team Members
- Team Lead: Kevin Twinkle - Viswajyothi college of engineering
- Member 2: Ajin Thomas - Viswajyotji college of engineering


### Project Description
A funny cross the line game

### The Problem (that doesn't exist)
It doesn't solve a practical problem — it's a joke about subverted expectations: doing it "right" (crossing the line) loses, and doing it "wrong" (double-clicking) loses worse. If there's a point, it's the last line: trusting a system's rules doesn't protect you from the person who built it. Beyond that, it's just a fun exercise in building state machines, animations, and timing logic

### The Solution (that nobody asked for)
There's no real-world problem being solved — the "solution" is just the mechanic that delivers the joke. Both paths (patient clicking or double-clicking) are wired to end in a loss screen, so no matter what the player does, they lose. That's implemented through simple state machines: track position/clicks, detect the ribbon or launch trigger, then branch into whichever pre-built loss sequence fits.

## Technical Details
### Technologies/Components Used
For Software:
- Html,javascript,css
  

For Hardware:
- none
- none
- none

### Implementation
For Software:
# Installation
none

# Run
Start-Process fan.html

### Project Documentation
For Software:# Make Him Cross The Line — Software Documentation

A single-file, browser-based novelty game. No installation, no build step, no server required.

| Item | Detail |
|---|---|
| File | `cross-the-line.html` |
| Type | Browser game |
| Dependencies | None |

---

## 1. Overview

The player raises a character toward a red ribbon at the center of the screen using an up-arrow button. Reaching the ribbon "the right way" is itself a losing outcome, and an alternate double-click action branches into a second, unrelated losing outcome. The game has no winnable end state — it exists as a piece of comedic, absurdist interaction design rather than a conventional game.

## 2. Tech Stack

| Layer | Technology | Notes |
|---|---|---|
| Structure | HTML5 | Single self-contained file |
| Styling & animation | CSS3 (keyframes, transitions, `clip-path`) | No CSS framework |
| Logic | Vanilla JavaScript (ES6) | No framework, no bundler |
| Graphics | CSS shapes + inline SVG | Hand-authored, no external image assets |

No package manager, no external libraries, no CDN calls. The file is fully portable.

## 3. System Requirements

- Any modern browser (Chrome, Firefox, Safari, Edge) with JavaScript enabled.
- No OS-specific requirements — runs identically on Windows, macOS, and Linux.

## 4. Installation

None. Download `cross-the-line.html` to any folder.

## 5. Running the Software

Open the file directly in a browser, either by double-clicking it or via a terminal command:

```bash
# macOS
open cross-the-line.html

# Windows (cmd)
start cross-the-line.html

# Windows (PowerShell)
Start-Process cross-the-line.html

# Linux
xdg-open cross-the-line.html
```

Optional — serve locally instead of using `file://` (not required for any current feature):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/cross-the-line.html
```

## 6. Functional Specification

### 6.1 Climb scene (starting state)
- White background. A standing character sits near the bottom of the screen.
- A red horizontal ribbon is fixed at the vertical center of the screen, captioned **"Make Him Cross The Line."**
- An up-arrow button sits on the side of the screen.

### 6.2 Single-click path
- Each single click on the up-arrow raises the character a small, fixed distance.
- After every click, the character's position is checked against the ribbon's position.
- If the character reaches the ribbon, a full-screen overlay appears reading **"YOU LOSE — it took so long,"** with a **Start Over** button that reloads the page.

### 6.3 Double-click path
- Double-clicking the up-arrow (at any point before reaching the ribbon) triggers a rapid, uncontrolled launch: the character shoots upward, a crack opens in the ceiling, the screen shakes briefly, and the scene transitions to space.
- **Space sequence:** the character tumbles and drifts across the screen. After a few seconds, two buttons fade in: **Save him** and **Kill him**.
- **Either choice** leads to the same outcome: the character inflates through four escalating visual stages (increasing scale, saturation, and a shaking "strain" effect), then bursts into a particle explosion with a screen flash.
- The game then cuts to a black **game-over screen** with stylized blood-red blot shapes and white monospace text reading **"YOU LOSE. you trusted the creator,"** with a **Start Over** button that reloads the page.

## 7. Architecture Notes

- **State machine:** three mutually exclusive scenes (`climb`, `space`, `gameover`) are toggled via `classList` (`display:none` ↔ `display:block`) rather than any routing system. A small set of boolean flags (`launched`, `slowLost`, `doomed`) gate which transitions are allowed.
- **Click vs. double-click detection:** implemented manually with a ~240ms `setTimeout` debounce rather than relying on the native `dblclick` event. This makes single- and double-click behavior reliably distinguishable across browsers, since a native double-click would otherwise also fire two separate `click` events.
- **Ribbon collision detection:** resolved with `getBoundingClientRect()` on both the character element and the ribbon element after every single click, comparing the character's top edge to the ribbon's bottom edge. This makes the check resolution-independent rather than relying on hardcoded pixel values.
- **Launch animation:** achieved by transitioning the character's `bottom` CSS property to a very large value over a short duration (`cubic-bezier` easing), producing the "rapid ascent" effect, combined with a `classList`-triggered screen-shake keyframe animation and a growing "ceiling crack" element.
- **Inflate/explode sequence:** driven by a chain of `setTimeout` calls that progressively add CSS classes (`puff-1` → `puff-2` → `puff-3` → `puff-max`) to the character, each scaling and recoloring it via `transform` and `filter`, before a final class hides the character and a JS loop generates and animates a burst of particle `<div>` elements outward from the center point.
- **Character art:** a single hand-drawn inline SVG (spiky-haired, black-outfit figure) is reused across both the climb scene and the space scene for visual consistency.

## 8. File Structure

```
project-root/
└── cross-the-line.html
```

Everything — markup, styles, and logic — lives in this one file.

## 9. Known Limitations

- No persistence: reloading the page resets all state. This is intentional; the game uses no `localStorage` or backend.
- No touch-specific double-tap handling beyond standard `click` events — works on touch screens, but double-tap timing may feel different from a mouse double-click.
- Minimal accessibility support: interactive elements have basic `aria-label`s, but there is no full screen-reader walkthrough of scene changes.

## 10. Possible Extensions

- Add sound effects for the climb, launch, inflate, and explosion beats.
- Track and display the number of clicks taken before reaching the ribbon or triggering the launch.
- Add a genuine alternate ending for players who never double-click and never reach the ribbon (currently the game has no "good" ending at all).

# Screenshots (Add at least 3)
<img width="1892" height="543" alt="image" src="https://github.com/user-attachments/assets/528015aa-dd1a-4bf9-b0f7-27a45ee43936" />
interface of the cross the line game 


![Screenshot2](Add screenshot 2 here with proper name)
<img width="1910" height="717" alt="image" src="https://github.com/user-attachments/assets/72edf1b8-002f-485e-9aca-8528e7764155" />
interface of the game after we moved the human a little bit

![Screenshot3](Add screenshot 3 here with proper name)
<img width="1873" height="823" alt="image" src="https://github.com/user-attachments/assets/414bca08-2f88-4249-b6cf-f2add8a17189" />
interface of the human after he reached the space

# Diagrams
![Workflow](<img width="2720" height="2400" alt="cross_the_line_launch_sequence" src="https://github.com/user-attachments/assets/01cc8f58-4606-4132-aee7-d8bf84b3f0d3" /><img width="2720" height="1280" alt="cross_the_line_flow_overview" src="https://github.com/user-attachments/assets/6bf6acb2-64e2-484e-9919-c60cb3869afc" />

)
*Add caption explaining your workflow*

For Hardware:

# Schematic & Circuit
![Circuit](<img width="2720" height="2400" alt="cross_the_line_pcb_circuit" src="https://github.com/user-attachments/assets/bda71f67-d023-413f-ba65-e33437bd2bc1" />
)
*Add caption explaining connections*

![Schematic](<img width="2720" height="2560" alt="cross_the_line_logic_schematic" src="https://github.com/user-attachments/assets/fb136eff-cef4-404c-be3e-a5ae2acdaa90" />
)
*Add caption explaining the schematic*

# Build Photos
![Components](Add photo of your components here)
*List out all components shown*

![Build](Add photos of build process here)
*Explain the build steps*

![Final](Add photo of final product here)
*Explain the final build*

### Project Demo
# Video
[Add your demo video link here]
*Explain what the video demonstrates*

# Additional Demos
[Add any extra demo materials/links]

## Team Contributions
- [Kevin Twinkle]: [Specific contributions]
- [Ajin Thomas]: [Specific contributions]
- [Name 3]: [Specific contributions]

---
Made with ❤️ at TinkerHub Useless Projects 

![Static Badge](https://img.shields.io/badge/TinkerHub-24?color=%23000000&link=https%3A%2F%2Fwww.tinkerhub.org%2F)
![Static Badge](https://img.shields.io/badge/UselessProjects--26-26?link=https%3A%2F%2Ftinkerhub.org%2Fevents%2F1M8ORET9A1%2Fuseless-projects-3.0)



