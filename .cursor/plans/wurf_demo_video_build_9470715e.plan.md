---
name: Wurf Demo Video Build
overview: "Build a single-page HTML/CSS/JS auto-playing demo video showing a Wurf-powered chat widget floating over a merchant dashboard, demonstrating two scenarios: footfall analysis and location scouting for a second store."
todos:
  - id: scaffold
    content: Create index.html with dashboard layout (sidebar nav, metric cards, placeholder chart area) and chat widget shell, plus CDN imports for GSAP, Chart.js, and Google Fonts
    status: completed
  - id: dashboard-ui
    content: Build the static merchant dashboard UI -- sidebar with nav items, top metric cards (revenue, transactions, avg ticket), a main chart area, and store info section
    status: completed
  - id: chat-widget
    content: Build the Wurf chat widget component -- floating panel with header, message list area, typing indicator, and input bar (decorative)
    status: completed
  - id: animation-timeline
    content: "Implement the GSAP master timeline orchestrating all scenes: dashboard entrance, chat widget entrance, Scene 1 (footfall), Scene 2 (location), outro, and loop"
    status: completed
  - id: scene1-footfall
    content: Implement Scene 1 content -- typing effect for user message, bot response with animated Chart.js bar chart for footfall trends and count-up metrics
    status: completed
  - id: scene2-location
    content: Implement Scene 2 content -- typing effect for user message, bot response with comparison table card, animated score badge, and summary text
    status: completed
  - id: polish
    content: Final polish -- easing curves, stagger timings, glassmorphism effects, subtle shadows, smooth loop transition, and cross-browser testing
    status: completed
isProject: false
---

# Wurf B2B PSP Demo Video

## Concept

A single `index.html` page containing an auto-playing animated demo that loops continuously. The animation shows a **merchant dashboard** (styled like a modern POS analytics portal) with a **Wurf chat widget** floating in the bottom-right corner. Two scenarios play out sequentially through scripted chat interactions with typing effects, animated data cards, and chart reveals.

---

## Visual Design

- **Dashboard**: Dark sidebar + light content area, showing revenue charts, transaction counts, and store info -- sets the "payment processor" context (think Dojo/Stripe merchant portal)
- **Chat Widget**: Glassmorphism-style floating panel, bottom-right, with Wurf branding. Messages animate in with typing indicators, response cards slide up with data visualizations
- **Palette**: Deep navy (`#0f172a`) sidebar, white/light gray content, vibrant teal (`#06b6d4`) as primary accent for Wurf branding, warm amber for highlights
- **Typography**: Google Fonts -- "Plus Jakarta Sans" for body, "Space Grotesk" for dashboard headings

---

## Animation Timeline (auto-play loop, ~30-40 seconds total)

### Scene 1: Footfall Analysis (~15s)

1. **0s** -- Dashboard fades in with staggered entrance (sidebar, then cards, then charts)
2. **2s** -- Chat widget bounces in from bottom-right with a welcome message: *"Hi! I'm Wurf. Ask me anything about your business context."*
3. **4s** -- Typing indicator appears, then user message types out: *"Show me foot traffic trends near my store this month"*
4. **6s** -- Bot thinking indicator (3 dots pulse)
5. **7s** -- Bot responds with a rich card: animated mini bar chart showing daily footfall data, peak hours highlighted, a summary line: *"Footfall is up 12% vs last month. Peak hours: 12-2pm on weekdays. Saturday saw a 23% spike due to a local market event."*
6. **10s** -- Data card fully rendered, numbers count up

### Scene 2: Location Scouting (~15s)

1. **12s** -- User types: *"Is Shoreditch High Street a good location for a second store?"*
2. **14s** -- Bot thinking indicator
3. **15s** -- Bot responds with a location analysis card: comparison table (current store vs proposed location), metrics like avg footfall, rent per sqft, competitor density, demographic match. A score badge animates in: *"Location Score: 82/100 -- Strong Match"*
4. **20s** -- Summary text: *"High footfall corridor with 15% lower rent than your current area. 2 direct competitors within 500m, but demographic overlap is 78%."*

### Transition

1. **25s** -- Chat minimizes, dashboard fades slightly
2. **28s** -- Wurf logo + tagline fades in center: *"Wurf -- External context for every payment processor. One API."*
3. **32s** -- Loop restarts

---

## Tech Stack

- **Single `index.html`** -- self-contained, no build step
- **GSAP** (via CDN) -- timeline-based animation engine for precise sequencing
- **Chart.js** (via CDN) -- animated bar/doughnut charts inside response cards
- **Google Fonts** -- Plus Jakarta Sans + Space Grotesk
- **CSS Custom Properties** -- for theming/palette
- **Vanilla JS** -- orchestrating the GSAP timeline, typing effects, counter animations

## File Structure

```
wurf_b2b_psp_video/
  index.html          -- main demo page (all HTML/CSS/JS inline or scoped)
  README.md           -- brief setup instructions
```

Everything is inlined in a single HTML file for maximum portability (easy to embed, screenshot, or screen-record).

---

## Key Implementation Details

- **Typing effect**: Character-by-character reveal using GSAP's `onUpdate` callback stepping through string indices
- **Chart animations**: Chart.js with `animation.duration` synced to the GSAP timeline via `onComplete` callbacks
- **Number counters**: GSAP `snap` tweens on innerHTML for count-up effects on metrics
- **Chat flow**: An array of message objects `{role, content, type, delay}` driven by GSAP timeline `.add()` calls at specific offsets
- **Responsiveness**: Fixed 1280x720 viewport wrapper (16:9) centered on page so it looks like a product screenshot/video frame at any screen size
- **Loop**: GSAP timeline `repeat: -1` with `repeatDelay: 3`

