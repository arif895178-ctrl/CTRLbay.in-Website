# CTRLbay Landing Page — Edit Guide

This document maps every editable part of `ctrlbay-landing.html` to its exact location.  
Open the HTML file in any text editor (VS Code recommended). Use **Ctrl+G** (or **Cmd+G** on Mac) to jump to a line number.

---

## Quick Reference — Most Common Edits

| What you want to change | Line(s) |
|---|---|
| Brand accent color (green) | 19 |
| Page background color | 15 |
| Logo text in nav | 1002 |
| Logo text in footer | 1516 |
| Nav button text ("Start a Build") | 1011 |
| Nav links | 1005–1010 |
| Loading screen tagline | 989 |
| Loading screen duration | 1549–1554 |
| Hero headline (Power / Precision / CTRL) | 1025–1029 |
| Hero subtext paragraph | 1030–1032 |
| Hero button 1 text ("View Prebuilds") | 1035 |
| Hero button 2 text ("How It Works") | 1043 |
| Hero stats (500+, 4.9★, 1yr, 100%) | 1049–1064 |
| Bubble labels (right side floating text) | 1582 |
| Bubble sizes | 1583 |
| PC illustration opacity (background behind bubbles) | 187 |
| PC illustration glow brightness | 192–193 |
| Scrolling marquee text | 1153–1164 |
| Scroll strip stats (big numbers section) | 1130–1145 |
| Prebuild card names | 1183, 1196, 1209 |
| Prebuild card descriptions | 1184, 1197, 1210 |
| Prebuild card tier labels | 1182, 1195, 1208 |
| "Why CTRLbay" heading | 1222 |
| "Why CTRLbay" body text | 1223 |
| Why section USP tiles (4 boxes) | 1228–1249 |
| How It Works steps | 1259–1280 |
| Testimonial quotes | 1292, 1305, 1318 |
| Testimonial names & roles | 1296–1298, 1309–1311, 1321–1323 |
| CTA section heading | 1334 |
| CTA buttons (links) | 1339–1340 |
| WhatsApp number | 1339, 1340, 1519 |
| Footer tagline | 1518 |
| Footer links (Builds, Company, Contact) | 1521–1535 |
| Copyright year | 1541 |

---

## Colors & Fonts — Lines 14–28

These CSS variables control the entire color scheme and typography. Change one variable here and it updates everywhere on the page.

```
Line 15  --bg          Page background (very dark black: #0c0c0c)
Line 16  --surface     Slightly lighter background used on alternate sections
Line 17  --card        Card/tile background color
Line 18  --card-hover  Card color when mouse hovers over it
Line 19  --accent      Brand green (#4ade80) — change this to update ALL green across the site
Line 21  --border      Subtle border color between elements
Line 22  --white       Main text color (#efefef — off-white, easier on eyes than pure white)
Line 23  --muted       Secondary/body text color (grey)
Line 24  --muted2      Darker grey, used for very subtle labels
Line 25  --font-head   Heading font (Syne — bold display font)
Line 26  --font-body   Body font (Inter)
Line 27  --font-mono   Monospace font (JetBrains Mono — used for labels, tags, stats)
```

**To change the brand color:** Find `--accent: #4ade80;` on line 19 and replace the hex code.

---

## Loading Screen — Lines 303–392 (CSS) · Lines 985–990 (HTML) · Lines 1527–1555 (JS)

The full-screen intro that plays when the page first loads.

**Text content:**

```
Line 988   Tagline shown under the logo animation
             Edit: change "Crafted by Gamers. Powered by You." to anything
```

**Timing — Lines 1527–1555 (JS):**

```
Line 1537  Logo text that types itself letter-by-letter ("CTRLbay.in")
             To change it: replace 'CTRLbay.in' with your brand name

Line 1538  accents = new Set([4,5,6,7,8,9])
             These are the character positions (0-indexed) that appear in green.
             'CTRLbay.in' → C=0, T=1, R=2, L=3, b=4, a=5, y=6, .=7, i=8, n=9
             So positions 4–9 (bay.in) are green. Adjust if you change the brand name.

Line 1544  animationDelay = (0.04 + i * 0.07) + 's'
             Controls how fast each letter appears. Lower 0.07 = faster typing.

Line 1549  setTimeout(..., 1900)
             How long (in milliseconds) the loader stays visible before it exits.
             1900 = 1.9 seconds. Increase for a longer intro, decrease for quicker.

Line 1553  setTimeout(..., 900)
             How long the exit wipe animation takes before the loader is fully removed.
```

**CSS animation speeds:**

```
Line 317   loader-exit: 0.7s — speed of the wipe-up exit animation
Line 338   char-in: 0.5s — how fast each letter bounces in
Line 352   fade-in-slow: 0.6s delay 0.9s — tagline fade-in timing
Line 368   bar-fill: 1.1s delay 0.5s — green progress bar fill speed
```

---

## Navigation — Lines 55–125 (CSS) · Lines 994–1015 (HTML)

**Logo in nav — Line 1002:**
```html
<span class="logo-text">CTRL<em>bay</em><em style="color:rgba(74,222,128,0.55);">.in</em></span>
```
- `CTRL` — plain white text
- `<em>bay</em>` — green (uses --accent color)
- `<em style="...">.in</em>` — slightly dimmer green

**To use an image logo instead:** Replace the entire `<span class="logo-text">...</span>` with:
```html
<img src="your-logo.png" alt="CTRLbay" class="logo-img" />
```
Then adjust logo height at line 80: `--logo-height: 28px;`

**Nav links — Lines 1005–1010:**  
Change link text or `href` targets (e.g. `#builds`, `#why`, `#process`, `#testimonials`).

**Nav button — Line 1011:**  
`Start a Build` — change the button label here. The button scrolls to the `#cta` section.

**Sticky nav background — Line 68:**  
`background: rgba(12,12,12,0.92)` — opacity of the blurred nav background when scrolling.

---

## Hero Section — Lines 127–165 (CSS) · Lines 1018–1070 (HTML)

The main first screen with the large headline and bubble panel.

**Headline — Lines 1025–1029:**
```html
<span class="line-dim">Power.</span>    ← ghost/outline style word
<span>Precision.</span>                  ← normal white
<span class="line-accent">CTRL.</span>  ← green accent word
```
Change any of these words directly.

**Subtext paragraph — Lines 1030–1032:**  
Edit the body copy under the headline.

**Button 1 ("View Prebuilds") — Line 1035:**  
Change label text. The `href="#builds"` links to the Prebuilds section.

**Button 2 ("How It Works") — Line 1043:**  
Change label text. The `href="#process"` links to the Process section.

**Stats bar (500+, 4.9★, 1yr, 100%) — Lines 1049–1064:**
```
Line 1051  meta-val = big number (e.g. 500)
Line 1052  <span>+</span> = colored suffix after the number
Line 1053  meta-label = small label below (e.g. "BUILDS SHIPPED")
```
Each stat follows this same pattern. There are 4 stats total.

**Hero background grid — Lines 138–148:**  
The faint dot grid behind the text. Change `background-size: 80px 80px` on line 144 to resize the grid.

**Green glow behind right panel — Lines 149–155:**  
Reduce `rgba(74,222,128,0.05)` opacity on line 152 to make it less visible.

---

## Bubble Panel (Right Side of Hero) — Lines 159–274 (CSS) · Lines 1073–1127 (HTML) · Lines 1579–1734 (JS)

The floating interactive bubbles visible only on desktop.

**Bubble labels — Line 1582 (JS):**
```javascript
const labels = ['Expert Assembly', '1 Year Free Service', 'Fully Custom', 'Zero Bloat'];
```
Edit any of these 4 strings to change what each bubble says. Keep them short (2–4 words work best).

**Bubble sizes — Line 1583 (JS):**
```javascript
const sizes = [150, 130, 160, 120]; // diameter in pixels, one per bubble
```
Match order to labels array. Bigger number = bigger bubble.

**Bubble speed — Line 1599–1600 (JS):**
```javascript
vx: (Math.random() - 0.5) * 0.8,
vy: (Math.random() - 0.5) * 0.8,
```
Increase `0.8` to make bubbles move faster. Decrease for slower drift.

**Bubble pop respawn delay — Line 1677:**  
`2500` = 2.5 seconds before a popped bubble reappears. Change to any millisecond value.

**Bubble colors — Lines 208–216 (CSS):**  
The `rgba(74,222,128,...)` values control the green tint. Lower opacity = more transparent/glassy.

**PC illustration opacity — Line 187:**  
`opacity: 0.22` — how visible the PC illustration is behind the bubbles. 0 = invisible, 1 = fully visible.

**PC illustration glow pulse — Lines 192–193:**  
The `pc-breathe` animation pulses between `0.22` and `0.28` opacity. Change these values to adjust the breathing range.

**Hide/show bubbles on mobile — Line 962 (CSS):**  
`.hero-right { display: none; }` — this line hides the entire bubble panel on screens ≤768px wide.  
To show bubbles on mobile too: delete this line entirely.

---

## Scrolling Marquee Strip — Lines 491–514 (CSS) · Lines 1148–1164 (HTML)

The scrolling text band that appears after the hero.

**Marquee text items — Lines 1151–1163:**  
Each `<span class="marquee-item">` is one item. Edit the text inside directly.  
Note: The items are duplicated (appears twice) — that's intentional to make the loop seamless.  
Edit both copies to keep it consistent.

**Scroll speed — Line 502:**  
`animation: marquee 30s linear infinite` — reduce `30s` for faster scrolling.

---

## Scroll Stats Strip — Lines 393–437 (CSS) · Lines 1128–1146 (HTML)

The large-number section (500+, 4.9★, etc.) that appears after the marquee as you scroll.

**Each stat — Lines 1130–1145:**
```html
<div class="stat-val">500<span>+</span></div>   ← big number, + is green
<div class="stat-label">Builds Shipped</div>     ← label below
```
Four stat blocks total. Edit numbers and labels directly.

---

## Prebuild Cards — Lines 574–682 (CSS) · Lines 1166–1215 (HTML)

The 3 featured build cards (The Rookie, The Operator, The Overlord).

**Card 1 — The Rookie — Lines 1178–1191:**
```
Line 1182  Tier label ("Entry Build")
Line 1183  Card name ("The Rookie")
Line 1184  Card description paragraph
```

**Card 2 — The Operator — Lines 1192–1204:**
```
Line 1195  Tier label ("Mid-Range")
Line 1196  Card name ("The Operator")
Line 1197  Card description paragraph
```

**Card 3 — The Overlord — Lines 1205–1218:**
```
Line 1208  Tier label ("Flagship · Most Popular")
Line 1209  Card name ("The Overlord")
Line 1210  Card description paragraph
```

**To add a price back:** Inside any card, after the `<p class="card-desc">` block, add:
```html
<div class="card-price"><span class="card-from">Starting at</span>₹55,000</div>
```

**Featured card (green highlight) — Line 1205:**  
The card with `class="build-card featured"` gets the green accent dot on the tier label.  
Add or remove `featured` from any card's class to control which one is highlighted.

---

## Why CTRLbay Section — Lines 684–724 (CSS) · Lines 1219–1250 (HTML)

**Section heading — Line 1222:**
```html
<h2>We don't just<br>build PCs.<br><span class="a">We build yours.</span></h2>
```
The `<span class="a">` makes that line green. Edit freely.

**Body paragraph — Line 1223:**  
The longer description paragraph.

**CTA button — Line 1225:**  
"Get a Free Quote →" — change text or `href`.

**USP tiles (4 boxes on the right) — Lines 1228–1249:**  
Each tile has:
- `.usp-icon` — the emoji
- `.usp-title` — bold title
- `.usp-body` — description paragraph

Edit any of these directly. To swap an emoji, replace the character inside `.usp-icon`.

---

## How It Works (Process) — Lines 726–767 (CSS) · Lines 1253–1280 (HTML)

Four numbered steps.

```
Lines 1257–1261  Step 01 — title and description
Lines 1262–1266  Step 02 — title and description
Lines 1267–1271  Step 03 — title and description
Lines 1272–1276  Step 04 — title and description
```

Each step: edit `.step-title` for the heading, `.step-desc` for the body.

---

## Testimonials — Lines 769–830 (CSS) · Lines 1282–1329 (HTML)

Three review cards.

**Card 1 (Arjun K.) — Lines 1286–1300:**
```
Line 1292  Quote text
Line 1296  Name ("Arjun K.")
Line 1297  Role/location ("FPS Player · Hyderabad")
Line 1290  Avatar initials ("AK")
```

**Card 2 (Priya R.) — Lines 1301–1314:**  
Same structure. Lines 1305 (quote), 1309 (name), 1310 (role), 1303 (avatar).

**Card 3 (Vikram S.) — Lines 1315–1328:**  
Lines 1318 (quote), 1321 (name), 1322 (role), 1316 (avatar).

---

## CTA Section — Lines 832–849 (CSS) · Lines 1330–1345 (HTML)

The final "call to action" block before the footer.

```
Line 1332  Small label above heading ("Ready?")
Line 1334  Main heading ("Your rig. / Your rules.")
Line 1337  Description paragraph
Line 1339  Button 1 — "Start Your Build →" — href links to WhatsApp
Line 1340  Button 2 — "WhatsApp Us →" — href links to WhatsApp
Line 1344  Small footnote line at bottom
```

**WhatsApp number — Lines 1339 and 1340:**  
Both buttons link to `https://wa.me/919108461069`.  
To change the number: replace `919108461069` with `91` + your 10-digit Indian mobile number.

---

## Footer — Lines 851–904 (CSS) · Lines 1347–1545 (HTML)

**Footer logo — Line 1516:**  
Same structure as nav logo. Replace with `<img>` tag to use an image logo.

**Footer tagline — Line 1518:**  
`"Premium custom gaming PCs built by people who actually care..."` — edit directly.

**Footer column: Builds — Lines 1521–1527:**  
Four links. Edit `href` and link text.

**Footer column: Company — Lines 1528–1535:**  
Four links. Edit `href` and link text.

**Footer column: Get in Touch — Lines 1536–1542:**  
Email, WhatsApp, Instagram, Discord links.  
Line 1537: email `href="mailto:hello@ctrlbay.in"` — update the email address.  
Line 1538: WhatsApp link — update number same as CTA above.

**Copyright line — Line 1541:**  
`© 2025 CTRLbay.in` — update year or brand name.

**Social links (bottom right) — Lines 1543–1548:**  
Instagram, Discord, YouTube, Twitter. Add actual URLs to the `href` attributes.

---

## Scroll Animations — Lines 1758–1809 (JS)

Every section uses one of 5 animation types. You can change which animation a specific element uses by changing its CSS class in the HTML.

| Class | Effect | Used on |
|---|---|---|
| `anim-fade-up` | Fades in while rising upward | Headings, step numbers, labels |
| `anim-fade-in` | Pure fade, no movement | Supporting text, descriptions |
| `anim-slide-left` | Slides in from the left | Why section left column, card 1 |
| `anim-slide-right` | Slides in from the right | Card 3 |
| `anim-scale` | Scales up from 94% to 100% | USP tiles, testimonial cards |

**To change an element's animation:** Find the element in the HTML and replace its class. For example, changing `class="anim-fade-up"` to `class="anim-scale"` makes that element scale in instead of rising.

**Animation trigger point — Line 1764:**  
`start: 'top 90%'` — the element starts animating when its top edge hits 90% down the viewport. Lower the % to trigger earlier.

**Animation speed — Line 1762:**  
`duration: 0.65` — seconds. Lower = faster.

---

## Hero Entrance Animation Timing — Lines 1572–1577 (JS)

The hero content animates in after the loader exits.

```
Line 1573  delay: 2.1 — waits 2.1 seconds (matching the loader duration) before starting
Line 1574  #h-head — the big headline animates first
Line 1575  #h-sub  — subtext follows, overlapping slightly
Line 1576  #h-act  — buttons follow
Line 1577  #h-meta — stats bar follows last
```

If you change the loader duration (line 1549), update this delay to match.

---

## Responsive Breakpoints — Lines 932–980 (CSS)

Controls layout at different screen sizes.

```
Line 933  max-width: 1100px — large tablets / small laptops
Line 944  max-width: 900px  — tablets (hero becomes single column, bubbles still show)
Line 956  max-width: 768px  — phones (bubbles hidden, hero stacks vertically)
Line 975  max-width: 480px  — small phones
```

**Key mobile rule — Line 962:**
```css
.hero-right { display: none; }
```
This hides the bubble panel on phones. Remove this line to show bubbles on mobile.

---

## Tips for Common Tasks

**Change all green to a different color:**  
Line 19: change `--accent: #4ade80;` to any hex color. Everything updates automatically.

**Add a 5th stat to the hero:**  
Copy one `<div class="meta-item">` block (lines 1049–1053) and paste it after line 1063. Edit the number and label.

**Add a 4th prebuild card:**  
Copy any `<div class="build-card ...">` block and paste it inside the `.builds-grid` div. Note: the grid uses 3 columns, so a 4th card will start a new row.

**Change WhatsApp number everywhere at once:**  
Search for `919108461069` in the file — it appears 3 times (CTA button 1, CTA button 2, footer). Replace all three.

**Make the loading screen shorter:**  
Line 1549: change `1900` to `1200` (1.2 seconds). Then line 1573: change `delay: 2.1` to `delay: 1.4`.

**Remove the loading screen entirely:**  
Delete lines 985–990 (the loader HTML), and change line 1573 from `delay: 2.1` to `delay: 0.2`.

**Add a real Instagram link:**  
Find `<a href="#">Instagram</a>` in the footer (around line 1539) and replace `#` with your Instagram URL.
