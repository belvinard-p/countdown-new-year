# New Year Countdown

A lightweight, zero-dependency countdown timer that displays the exact time remaining until the next New Year — with a festive celebration animation when midnight strikes.

🌐 **Live Demo:** [belvi-project05-countdown-new-year.netlify.app](https://belvi-project05-countdown-new-year.netlify.app/)

![Countdown Screenshot](countdown.png)

---

## Table of Contents

1. [About](#about)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Architecture](#architecture)
5. [Project Structure](#project-structure)
6. [Getting Started](#getting-started)
7. [Configuration](#configuration)
8. [Security](#security)
9. [Contribution Guidelines](#contribution-guidelines)
10. [Roadmap](#roadmap)
11. [License](#license)
12. [Acknowledgements](#acknowledgements)
13. [Author](#author)

---

## About

New Year Countdown is a pure vanilla JavaScript project that calculates and displays the real-time countdown to January 1st of the next year. It was built to practice core JavaScript concepts — DOM manipulation, the `Date` API, `setInterval`, and `setTimeout` — without relying on any framework or library.

The project automatically detects the current year, targets the next New Year, and resets itself every year without any manual update needed.

---

## Features

- Live countdown displaying days, hours, minutes, and seconds updated every second
- Target year displayed dynamically — always points to the next New Year
- "Happy New Year!" celebration message with a pulsing gold animation when the countdown hits zero
- Automatic restart — after 30 minutes of celebration, the countdown resets for the following year
- Two-digit formatting for all time units (e.g. `07` instead of `7`)
- Hover scale effect on each time unit
- Responsive layout — adapts to mobile, tablet, and desktop screens
- No dependencies, no build step — open `index.html` and it works

---

## Tech Stack

- HTML5 — semantic page structure
- CSS3 — Flexbox layout, keyframe animations, CSS pseudo-elements for labels, media queries
- JavaScript (ES6+) — `Date` API, `setInterval`, `setTimeout`, DOM manipulation

No frameworks, no libraries, no build tools required.

---

## Architecture

This is a single-page static application with no backend or external dependencies.

```
Browser
  └── index.html          ← Page structure (countdown container, year display)
        ├── style.css     ← Layout, colors, animations, responsive breakpoints
        └── index.js      ← Countdown logic (calculate, update, celebrate, restart)
```

**Countdown logic flow:**

```
Page loads
  └── Read current year → set targetYear = currentYear + 1
        └── setInterval (every 1000ms)
              └── Calculate gap = newYearTime - now
                    ├── gap > 0  → update DOM (days, hours, minutes, seconds)
                    └── gap ≤ 0  → show "Happy New Year!" animation
                                    └── setTimeout (30 min)
                                          └── restartCountdown() → targetYear += 1
```

---

## Project Structure

```
JS-01-newyearcountdown/
├── index.html      # Page markup — countdown container, year div, script link
├── index.js        # All countdown logic — update, format, celebrate, restart
├── style.css       # Styling — layout, colors, animations, responsive rules
├── favicon.png     # Browser tab icon
├── countdown.png   # Screenshot used in README
└── README.md
```

| File         | Responsibility |
|--------------|----------------|
| `index.html` | Defines the DOM structure — heading, year display, four time unit divs |
| `index.js`   | Calculates time remaining, updates the DOM every second, handles celebration and restart |
| `style.css`  | Full visual design — background, countdown box, CSS labels via `::before`, animation, media queries |

---

## Getting Started

No installation or build step required.

**Option 1 — Open directly**

```bash
# Clone the repository
git clone https://github.com/belvinard-p/JS-01-newyearcountdown.git
cd JS-01-newyearcountdown

# Open in browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

**Option 2 — Use a local server** (recommended to avoid browser file restrictions)

```bash
# With VS Code Live Server extension — right-click index.html → Open with Live Server

# Or with Python
python -m http.server 8080
# Then visit http://localhost:8080
```

That's it — no `npm install`, no build, no configuration needed.

---

## Configuration

The countdown target is calculated automatically from the system clock — no configuration is needed.

To change the celebration display duration, edit the `setTimeout` delay in `index.js`:

```js
// Default: 30 minutes (1800000ms)
setTimeout(() => {
    restartCountdown();
}, 1800000);
```

To change the background color, update the `body` rule in `style.css`:

```css
body {
    background-color: indianred; /* change to any color */
}
```

To change the celebration animation repeat count, update the `animate` property in `style.css`:

```css
.new-year-message {
    animation: celebrate 1s 10; /* change 10 to any number of repetitions */
}
```

---

## Security

- No user input is collected or processed
- No external APIs, CDNs, or third-party scripts are loaded
- No cookies, localStorage, or sessionStorage are used
- The project runs entirely client-side with no network requests

---

## Contribution Guidelines

Contributions are welcome for bug fixes or visual improvements.

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Keep changes minimal — this is intentionally a vanilla JS project with no dependencies
4. Do not introduce frameworks, libraries, or build tools
5. Test in at least one modern browser before submitting
6. Submit a pull request with a clear description of the change

---

## Roadmap

**v1.0.0 — Completed**
- Live countdown to next New Year
- Automatic year detection and reset
- Celebration animation on midnight
- Responsive design for all screen sizes
- Two-digit time formatting

**v1.1.0 — Planned**
- Sound effect on celebration
- Confetti animation using Canvas API
- Timezone selector so users can count down to their local midnight
- Dark / light background toggle

---

## License

This project is for portfolio and learning purposes. All rights reserved © Belvinard Pouadjeu.

If you use this project as a reference or template, please credit the original author.

---

## Acknowledgements

- [MDN Web Docs](https://developer.mozilla.org/) — `Date` API, `setInterval`, `setTimeout` reference
- [CSS Tricks](https://css-tricks.com/) — Flexbox and keyframe animation guides
- [Netlify](https://www.netlify.com/) — Free static site hosting

---

## Author

**Belvinard Pouadjeu**
Fullstack Developer & Data Engineer

- Portfolio: [belvinard-resume.netlify.app](https://belvinard-resume.netlify.app/)
- GitHub: [github.com/belvinard-p](https://github.com/belvinard-p)
- LinkedIn: [linkedin.com/in/belvinard-pouadjeu-19a734377](https://www.linkedin.com/in/belvinard-pouadjeu-19a734377)
- Email: belvinardpouadjeu@gmail.com
