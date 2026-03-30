# Climate Triple Takes — Design Guidelines

## What this project is
A single-page HTML newsletter (`index.html`) presenting the same climate news story in three switchable tones. Readers pick their mood via a sticky nav. Deployed at https://climatetripletakes.netlify.app via Netlify (linked to GitHub repo `tinahuang1994/my-first-claude-project`).

## The three tones
| Mode | Name | Tone | Icon |
|------|------|------|------|
| A | Unhinged Planet | Sharp satire, dark wit | 💀 |
| B | The Dispatch | Solutions-focused, optimistic | ☀️ |
| C | Ground Truth | Straight, exasperated, real | 😤 |

## Never change the text
All article copy is final. Design changes only — no edits to headlines, body paragraphs, pull quotes, or any other text content.

## Typography rules
Three fonts are loaded: Playfair Display, DM Sans, DM Mono. Their roles are locked and must not change per-mode:

- **Playfair Display** → article headlines + pull quote text only
- **DM Sans** → all body text, masthead (kicker, subtitle, date, switcher label), tab descriptions
- **DM Mono** → metadata/labels only: bylines, source links, badges, footer note

Do not switch font families between modes. Differentiate modes through color, weight, spacing, and size — not font switching. The pull quote is already visually distinct (Playfair italic) without any extra help.

## Color system — the design pattern
Each mode follows the same formula (modeled on Unhinged Planet):
1. **Vivid, saturated background color**
2. **Dark complementary banner color** (used for masthead, sticky nav, footer via `--ink`)
3. **Dot texture** using the banner color at ~10% opacity on the background
4. **Card backgrounds** = very pale tint of the banner color

| Mode | Background | Banner (`--ink`) | Accent | Notes |
|------|-----------|-----------------|--------|-------|
| A — Unhinged Planet | Pink `#FFD1DC` | Teal `#004F4F` | Teal | Pink + teal are the benchmark — user loves this |
| B — The Dispatch | Amber `#FFD08A` | Forest green `#1B4332` | Forest green | Warm amber chosen over yellow (too harsh) and peach (too similar to pink) |
| C — Ground Truth | Steel blue `#D4E6F1` | Dark navy `#0E1E35` | Signal red `#B71C1C` | Red accent cuts through calm blue as urgency signal |

The three backgrounds read as a family: **pink / amber-gold / steel blue** — warm, warm-orange, cool.

## Typography sizing per mode
Size/weight changes are allowed (not family changes):
- **The Dispatch:** body 16.5px / 1.85 line-height, headlines weight 700 — generous, easy morning read
- **Ground Truth:** body 15px / 1.75 line-height — slightly denser, more serious
- **Unhinged Planet:** default sizing, headline has a subtle skew transform

## Explainer cards behavior
When a mode is selected, the other two explainer cards fade to 28% opacity + slight grayscale (`ex-inactive` class). Only the active mode's card is fully visible. This is handled in `setStyle()` in the JS.

## Deployment
- Local directory: `/Users/tinahuang/Desktop/climate-site/`
- Git remote: `https://github.com/tinahuang1994/my-first-claude-project.git`
- Deploy command: `npx netlify-cli deploy --prod --dir .`
- The site is linked to Netlify site ID `5091e958-8832-47ec-a63a-4624f7ce3e8e`
- Always commit to git AND deploy via Netlify CLI after changes

## Design decisions to not revisit
- Dark mode for Ground Truth was tried and rejected — hard to read
- Bright lemon yellow for Dispatch was tried and rejected — too harsh on eyes
- Peach for Dispatch was considered but rejected — too similar to Unhinged Planet pink
- Font switching per mode was tried and rejected — breaks reading flow, creates cognitive friction
- The dot grid texture is a core part of the design identity — keep it on all modes
