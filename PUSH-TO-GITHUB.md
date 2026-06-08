# East End Assembly of God — Website Redesign Strategy

*Audacious directions for eastendag.org*
Prepared June 2026

---

## The honest starting point

East End Assembly of God is a diverse community church in the heart of Pittsburgh's East End, with a clear and beautiful promise: *"Restoring Hope… Changing Lives."* The current website does not carry that promise. It carries 2016.

A quick audit of what's live today:

- **It's frozen in time.** The footer reads © 2016. A "Message from Pastor York about the Coronavirus" still anchors the homepage, and a "2019 VBS" link sits in the main navigation. The single most important signal a visitor reads — *is this church alive right now?* — currently says no.
- **The hero works against you.** A full-bleed photo with a dark translucent box dropped on top, body copy centered inside it, hard-to-read links. It's the default template move of a decade ago.
- **No clear first step.** A nervous first-time visitor lands and has to choose between HOME / VISIT / SERVE / CONNECT / GROW / CONTACT / GIVE with no guidance. Seven equal doors, none of them obviously "start here."
- **No live/online front door.** "Watch our Sunday Service Live here" is buried as a hyperlink in the overlay. For a church that learned during 2020 that online *is* a front door, this should be unmissable.
- **Mobile + accessibility are afterthoughts.** Small serif nav over photography fails contrast checks and pinch-zoom reality, where the majority of church-search traffic actually lives.

None of this reflects the warmth that's obviously in the room. The redesign's job is to make the website finally *feel* like the church.

---

## The strategic idea

Most church websites are brochures. They describe the church. The redesign should instead behave like a **front door and a greeter** — it should reduce the anxiety of a first visit and make the next step obvious. Every audacious visual choice below is in service of one metric: *a stranger goes from landing on the page to confidently planning a first visit (in person or online).*

Three audiences, ranked:

1. **The first-time visitor** (highest value, most nervous) — wants to know: Will I fit in? What happens when I walk in? Where do I park? What about my kids?
2. **The regular** — wants service times, the live stream, the giving link, this week's info. Fast.
3. **The seeker at a distance** — may never walk in physically. Wants to watch, listen, and feel something.

---

## Three concepts, safe → wild

### Concept A — "Dawn / Light Breaks In" *(the lead concept — built as the prototype)*

The most audacious *and* the most on-brand, because it makes the motto literal. "Restoring Hope" becomes a visual system: a dark, cinematic canvas with light breaking across the top of the screen — a sunrise behind a city. Hope, dawning.

- **Mood:** dark editorial background, warm sunrise gradient (gold → rose → violet → sky) borrowed straight from the existing logo's colors, so it feels evolved rather than foreign.
- **Typography:** a big expressive serif (Fraunces) for emotional headlines paired with a clean sans (Inter) for everything functional. Massive hero type: *"Restoring hope. Changing lives."*
- **Motion:** breathing light behind the headline, scroll-triggered reveals, a live countdown to the next Sunday service, a kinetic value marquee ("Everyone welcome ✶ Following Jesus ✶").
- **Structure:** a single scrolling story — Hero → live "next gathering" bar → *I'm New* (three clear paths) → all-week gatherings → Watch live → Connect & Serve (bento grid) → Give → footer with address, times, contact.

This is the concept rendered in the attached HTML prototype.

### Concept B — "The Open Table" *(bold but warmer/softer)*

Leans into the diverse-community identity and the literal photo on the current site (kids around a table sharing a meal). Light, cream-and-terracotta palette, lots of real candid photography of the actual congregation, hand-drawn accents. Editorial magazine layout. Feels human and Pittsburgh-neighborhly rather than cinematic. Lower production cost, very high warmth. Good fallback if "dark and dramatic" feels off-brand to leadership.

### Concept C — "Living Liturgy" *(most experimental)*

A site that changes with the rhythm of the week. The homepage *knows what day it is*: Sunday morning it flips to a full-bleed "We're live now — join us" state; mid-week it surfaces the home groups; it shifts color temperature with the actual time of day (cool dawn → warm evening). A scripture-of-the-day animates in. Optional ambient audio of worship on the watch page. Genuinely novel — few churches anywhere do this — but it's the heaviest build and needs ongoing content discipline to not break the illusion.

---

## Recommended visual system (for Concept A)

| Element | Direction |
|---|---|
| **Color** | Ink `#0e0b18` canvas; sunrise accents gold `#ffb23e`, rose `#ff6b8a`, violet `#8b6bff`, sky `#5ec8ff`; cream `#fbf6ee` text |
| **Display type** | Fraunces (expressive serif) — headlines, emotional moments |
| **Body type** | Inter — nav, body, UI, anything functional |
| **Motion** | Scroll reveals, breathing light, live countdown, hover lift on cards. Respect `prefers-reduced-motion` |
| **Imagery** | Real, candid photos of the actual congregation — diverse, joyful, un-staged. This matters more than any graphic |
| **Texture** | Subtle film grain over gradients so the dark canvas feels filmic, not flat |

---

## Information architecture

Collapse seven flat tabs into **five intent-based destinations** plus one always-visible primary action.

- **I'm New** — the single most prominent path. What to expect, what to wear, kids, parking, "plan a visit" form.
- **Sundays** — service times, location/map, the all-week home groups.
- **Watch** — live stream + sermon archive (audio & video).
- **Connect** — serve teams, home groups, prayer requests, weekly email signup.
- **Give** — fast, secure, mobile-first. Persistent button in the nav.

Everything currently under SERVE / GROW / CONNECT folds cleanly into *Connect*. CONTACT lives in the footer where people expect it.

---

## Signature features worth building

1. **"Plan Your Visit" flow** — a 3-tap form (which service / bringing kids? / want someone to say hi?). The single highest-ROI thing a church site can add. Triggers a warm personal email, not an autoresponder.
2. **Live "Next Gathering" bar** with a real countdown to Sunday 10:30 (already working in the prototype).
3. **Sermon library** — searchable, with audio + video, shareable clips. Turns one-time watchers into regulars.
4. **One-tap Give** — Apple Pay / Google Pay, recurring option, no account required to give once.
5. **Sunday-aware homepage** *(Concept C crossover)* — auto-flips to "We're live now" during service hours.
6. **Accessibility as a feature, not a checkbox** — WCAG AA contrast, full keyboard nav, captions on the stream, reduced-motion support. A church that says "everyone welcome" should mean it technically too.

---

## Recommended build path

- **Platform:** A modern, low-maintenance stack the church can actually update. Options, simplest first: **Squarespace** (cheapest to maintain, decent design ceiling) → **Webflow** (far more design control, still no-code) → **Astro/Next.js on Vercel** (the prototype's ceiling, needs a developer). For most small churches, Webflow hits the sweet spot of "looks like the prototype" + "a volunteer can edit it."
- **Streaming:** keep using the existing platform (YouTube/Facebook Live) but embed it natively in the *Watch* page rather than linking out.
- **Giving:** Tithe.ly, Pushpay, or Givebutter — all do one-tap mobile giving.
- **CMS discipline:** whoever owns content needs a 10-minute weekly habit — update the sermon, the verse, the announcements. The Concept A design degrades gracefully if a week is missed; Concept C does not.

---

## Phasing

**Phase 1 (launch):** Concept A homepage, I'm New flow, Sundays, Watch, Give. Kill every dated element (2016 footer, COVID message, 2019 VBS). This alone transforms perception.

**Phase 2:** Full sermon archive with search, weekly-email automation, serve-team signup.

**Phase 3:** Sunday-aware / time-of-day behaviors from Concept C, ambient touches, richer storytelling pages (staff, beliefs, our story).

---

## What success looks like

Not "a prettier website." The bar is: *a stranger who has never set foot in a church lands on eastendag.org, immediately understands they'd be welcome, and books a visit before they talk themselves out of it.* Every choice in the attached prototype is pointed at that moment.
