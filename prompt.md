The previous implementation is not close enough to the `/Ref` screenshots. Do a corrective pass and fix the layout, spacing, missing sections, data rendering, and structure. Keep the existing work only where it matches the references; otherwise rewrite the page structure and CSS.

Important: The page must not be one giant bordered container. Each section must be its own independent section with its own background, spacing, card style, and shadow exactly like the references.

REFERENCE TARGET
Use the `/Ref` screenshots as the source of truth:
- Blog_main_01.jpeg to Blog_main_06.jpeg for the desktop main blog/Ayurveda listing page.
- Mobile_01.png to Mobile_09.png for the mobile article page.
- ref_01.png to ref_10.png for the desktop internal article page.

The current result has these problems that must be fixed:
1. Header spacing is wrong.
2. Footer is wrong and incomplete.
3. “Find your topic” section is missing.
4. Featured article section is missing.
5. Content after the first boxed sections is missing or not rendering.
6. Multiple sections are incorrectly appearing inside the same big bordered box.
7. Section backgrounds are too similar; the references use different soft cream/ivory/saffron areas.
8. Cards need individual subtle shadows and borders.
9. The small burnt-orange/light-red divider/accent line must appear where shown in the references, especially under category card images and on accent cards.
10. The topic grid must be metaobject-field driven, but it must also show demo fallback topics by default when metaobjects are empty.

FIX THE PAGE STRUCTURE FIRST
Rebuild the desktop main listing page as this exact section order:

1. Header
2. Hero
3. Care Paths card section
4. Daily Rhythm section
5. Featured article section
6. Find your topic / Browse topic grid
7. Vaidya consultation section
8. Footer
9. Floating Ask Guruji button

These must be sibling sections, not nested inside one parent card. Only individual cards should have borders. Do not wrap the whole page content in one huge outlined box.

HEADER FIX
Match the desktop reference header exactly:
- Header background: `#FFFDF8`.
- Header height: about 72px.
- Thin bottom border: `1px solid #EADCC8`.
- Inner header max width: 1120–1180px.
- Header content should be horizontally centered on the page.
- Logo must be left-aligned inside the max-width container.
- Nav must be centered, not too close to the logo.
- Right controls must be right-aligned.
- Use this structure:
  - Left: DhyanHQ logo.
  - Center: Today, Yoga, Gyaan, Ayurveda.
  - Right: English dropdown, Sign in.
- Active Ayurveda nav pill:
  - Background `#FFF0E2`.
  - Text/icon `#C8521B`.
  - Rounded pill.
- The current header looks compressed and uneven; fix spacing using a grid:
  `grid-template-columns: 1fr auto 1fr`
  with logo in left, nav centered, actions right.
- Do not let the nav drift left.

HERO FIX
Match Blog_main_01:
- Hero should have its own soft warm gradient background:
  `linear-gradient(180deg, #FFF4E4 0%, #FFFDF8 100%)`
  or similar.
- Hero content max width 1120–1180px.
- Hero should not be inside a bordered card.
- Hero padding should be generous: around 80px top and 72px bottom.
- Text block width around 560–620px.
- Eyebrow: “AYURVEDA INSIDE THE ASHRAM”.
- Heading:
  “आयुर्वेद · daily care for the body you practice with”
- CTA and metric pills must appear below the copy.
- Keep the right side mostly empty like the reference.

CARE PATHS SECTION FIX
This section currently looks like content is trapped in one giant box. Fix it.

- Create one large rounded container only for the Care Paths content.
- This container should be max width 1120–1180px, centered.
- Background: `#FFFDF8`.
- Border: `1px solid #EADCC8`.
- Border radius: 28px.
- Shadow: `0 18px 50px rgba(75, 48, 20, 0.08)`.
- Padding: around 36–40px.
- Layout: two columns.
  - Left column: pale inner card.
  - Right column: stacked care path rows.
- Left inner card:
  - Background `#FFF4E4` or `#FFF7EA`.
  - Border `1px solid #EADCC8`.
  - Border radius 22px.
  - It must have its own subtle shadow.
- Right rows:
  - Each row separated by thin beige divider.
  - Titles left, tags upper-right, link lower-right when present.
  - The last row must show the blue link “See the day rhythm”.
- Do not put Daily Rhythm or Consultation inside this same container.

IMPORTANT ACCENT LINE
Where the reference shows the small burnt-orange/light-red line, implement it:
- Category cards must have a thin burnt-orange divider strip directly under each image.
- Use color `#C8521B`.
- Height around 4px.
- Full card width under the image, following the image/card rounded shape.
- Accent cards like “At a glance” on article pages must have a vertical burnt-orange left border/accent line.

DAILY RHYTHM SECTION FIX
This must be a separate section below Care Paths with its own spacing.
- Section max width 1120–1180px.
- Layout two columns:
  - Left card: “Care before symptoms get loud”.
  - Right card: Morning/Midday/Evening/Weekly list.
- Each card must have its own:
  - Background `#FFF8EC`.
  - Border `1px solid #EADCC8`.
  - Border radius 22px.
  - Shadow `0 14px 36px rgba(75, 48, 20, 0.06)`.
- Do not leave huge blank empty areas inside the left card. Its height should follow content or visually match the right card intentionally.
- The right rhythm list must have proper row dividers and spacing.

FEATURED ARTICLE SECTION — MISSING, ADD IT
Add this section after Daily Rhythm and before Find your topic.

Content:
- Eyebrow: `READ · पढ़ें`
- Heading: `Everyday Ayurveda, explained simply`
- Large horizontal featured article card.
- Left side image.
- Right side text.

Card details:
- Max width 1120–1180px.
- Border radius 24px.
- Border `1px solid #EADCC8`.
- Shadow `0 18px 50px rgba(75, 48, 20, 0.08)`.
- Image left width about 50%.
- Content right width about 50%.
- Background `#FFFBF3`.

Text:
- Eyebrow: `FEATURED`
- Title: `Acidity and heartburn`
- Description:
  `A calm, plain-language look at why acidity and heartburn happen, what Ayurveda sees behind that burning feeling, and a few everyday habits the tradition suggests you can start today.`
- Link:
  `Read this first →`

FIND YOUR TOPIC SECTION — MISSING, ADD IT
This is mandatory. Add it after the Featured Article section.

Section header:
- Eyebrow: `BROWSE · विषय`
- Heading: `Find your topic`
- Subcopy:
  `The full library, sorted into shelves you can actually navigate. 250 articles`

Topic grid:
- Desktop: 4 columns.
- Tablet: 2 columns.
- Mobile: 1 column unless 2 columns fits cleanly.
- Each card must have:
  - Watercolor image at top.
  - Thin burnt-orange divider line below the image.
  - English title.
  - Hindi title/subtitle in orange.
  - Count aligned right.
  - Cream background.
  - Beige border.
  - Rounded corners.
  - Soft shadow.

Metaobject-driven requirement:
- The topic grid should read from metaobject fields / CMS data if available.
- If there are no metaobjects or the request returns empty, render this fallback demo data by default so the page is never empty.

Fallback topic data:
[
  { title: "Digestion & gut", hindi: "पाचन", count: 24 },
  { title: "Food & kitchen", hindi: "आहार", count: 16 },
  { title: "Herbs & remedies", hindi: "औषधि", count: 10 },
  { title: "Weight & cravings", hindi: "वजन और लालच", count: 13 },
  { title: "Immunity", hindi: "रोग-प्रतिरोध", count: 15 },
  { title: "Seasons & routine", hindi: "ऋतुचर्या", count: 11 },
  { title: "Sleep & energy", hindi: "नींद और ऊर्जा", count: 14 },
  { title: "Mind & calm", hindi: "मन और शांति", count: 14 },
  { title: "Daily habits", hindi: "दिनचर्या", count: 16 },
  { title: "Joints & body", hindi: "जोड़ और शरीर", count: 17 },
  { title: "Skin & glow", hindi: "त्वचा", count: 16 },
  { title: "Hair & scalp", hindi: "बाल", count: 11 },
  { title: "Eyes, ears & mouth", hindi: "आँख, कान, मुँह", count: 11 },
  { title: "Women’s wellbeing", hindi: "स्त्री-स्वास्थ्य", count: 13 },
  { title: "Men’s wellbeing", hindi: "पुरुष-स्वास्थ्य", count: 9 },
  { title: "Children’s care", hindi: "बच्चों की देखभाल", count: 13 },
  { title: "Elder care", hindi: "बुजुर्गों की देखभाल", count: 11 },
  { title: "Ayurveda basics", hindi: "आयुर्वेद की बुनियाद", count: 16 }
]

Use fallback watercolor placeholder illustrations if actual topic images are missing. Do not hide the cards just because images are missing.

CONSULTATION SECTION FIX
This should appear after Find your topic, not immediately after Daily Rhythm unless the topic grid exists above it.

- Large pale cream card.
- Max width 1120–1180px.
- Background `#FFF4E8` or `#FFF7EA`.
- Border `1px solid #EADCC8`.
- Border radius 28px.
- Soft shadow.
- Left:
  - Eyebrow `VAIDYA CONSULT`
  - Heading `Book a consultation with a vaidya`
  - Supporting paragraph.
  - Outlined button `WhatsApp consults opening soon`
- Right:
  - White rounded steps card with:
    01 Share the pattern
    02 Receive a small plan
    03 Fold it into Today
- Disclaimer should sit inside or directly under this section as in the reference:
  `Ayurveda guidance on DhyanHQ is supportive care, not emergency or diagnostic medical treatment.`

FOOTER FIX
The current footer is wrong and incomplete.

Desktop footer must match the references:
- Background: warm cream / ivory.
- Top border: `1px solid #EADCC8`.
- Max width aligned with page content.
- Padding around 28–40px vertical.
- Left:
  `© 2026 DhyanHQ · built with respect for the tradition`
- Right links:
  `Legal center`
  `Terms`
  `Privacy`
  `Refund policy`
  `Health disclaimer`
- Do not show only “Privacy policy”.
- Do not place footer inside the consultation card.
- Footer must be full-width cream area with an inner max-width row.

BACKGROUND COLORS BY SECTION
Use different but subtle backgrounds:
- Body/page: `#FFFDF8`.
- Hero: warm cream/peach gradient.
- Care paths section area: ivory body, card `#FFFDF8`, inner card `#FFF4E8`.
- Daily rhythm section: ivory body, cards `#FFF8EC`.
- Featured section: body `#FFFDF8`, card `#FFFBF3`.
- Topic grid section: body `#FFFDF8`, cards `#FFFBF3`.
- Consultation: card `#FFF4E8`.
- Footer: `#FFF8EC`.

SHADOWS
Each major card must have its own soft shadow:
- Major containers:
  `box-shadow: 0 18px 50px rgba(75, 48, 20, 0.08);`
- Smaller cards:
  `box-shadow: 0 10px 28px rgba(75, 48, 20, 0.06);`
- Do not add harsh dark shadows.
- Do not add one shadow around the entire page.

SPACING
Fix vertical spacing:
- Sections should have 72–96px vertical spacing on desktop.
- Content max width should be consistent.
- Do not let sections touch each other.
- Do not leave accidental huge blank gaps inside cards.
- Do not crop or hide content below the fold.
- The page must scroll through all sections from hero to footer.

FLOATING ASK GURUJI BUTTON
Keep the floating button on desktop:
- Position fixed bottom-right.
- Burnt-orange pill.
- White text.
- Soft shadow.
- It must not overlap footer text or important content.

MOBILE REQUIREMENTS
Do not break mobile. Mobile article pages must still match Mobile_01 to Mobile_09:
- Large app-like header.
- Fixed bottom nav.
- Article hero image.
- Large mobile body type.
- At-a-glance card.
- Agni card.
- Try This Today.
- Ingredient card.
- Words to Know.
- Sources.
- Disclaimer.
- More from Ayurveda.
- Footer.
- Add bottom padding so the fixed bottom nav does not cover content.

ACCEPTANCE CHECKLIST
Before finishing, verify these are visible on the main desktop page in this exact order:
1. Header
2. Hero with CTA and metric pills
3. Care Paths card
4. Daily Rhythm cards
5. “Everyday Ayurveda, explained simply” featured article
6. “Find your topic” topic grid with 18 demo cards if metaobjects are empty
7. Vaidya consultation card
8. Correct footer with all five links
9. Floating Ask Guruji button

If any of these are missing, do not stop. Fix it before finalizing.