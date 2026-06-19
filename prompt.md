Perfect — these screenshots make it clear. The target is a **scalable Ayurveda blog system**, not a single replicated page.

We should build **two dynamic Shopify templates**:

```text
1. Blog hub template
2. Article detail template
```

Everything should be driven by Shopify blogs, articles, metafields, metaobjects, and article tags.

---

# 1. What we are replicating

## Blog hub page design

From your screenshots, the blog index has:

```text
URL style:
stage.dhyanhq.com/ayurveda
```

Visual structure:

```text
Header
Large soft cream hero
Eyebrow text
Large heading with Hindi + English
Short description
Primary CTA
Stats pills: Topics / Reads

Care path card
Large editorial featured article
Topic/category card grid
Consultation CTA section
Footer
Floating “Ask Guruji” button
```

In Shopify, this should become:

```text
/blogs/ayurveda
```

Using:

```text
templates/blog.ayurveda.json
sections/dhyan-blog-hub.liquid
snippets/dhyan-topic-card.liquid
snippets/dhyan-article-card.liquid
```

---

## Article detail page design

From your article screenshots, each article has:

```text
Large image hero
Back/category pill
Feature label
Article title
Hindi subtitle
Short intro
Author/read time/review text
At a glance card
Illustration/info card
Main article body
Pull quote
Tip card section
Ingredient/herb card
Words to know card
Sources
Medical disclaimer
Related articles
Footer
Floating “Ask Guruji” button
```

In Shopify, this should become:

```text
/blogs/ayurveda/acidity-heartburn
/blogs/ayurveda/gas-bloating
/blogs/ayurveda/easing-constipation
```

Using:

```text
templates/article.ayurveda.json
sections/dhyan-article-template.liquid
snippets/dhyan-related-article-card.liquid
```

---

# 2. Final scalable structure

Use this exact Shopify structure:

```text
templates/
  blog.ayurveda.json
  article.ayurveda.json

sections/
  dhyan-blog-hub.liquid
  dhyan-article-template.liquid

snippets/
  dhyan-article-card.liquid
  dhyan-topic-card.liquid
```

This keeps the system clean and scalable.

---

# 3. Content should be dynamic like this

## Blog hub uses

```liquid
blog.title
blog.articles
blog.metafields.custom.hero_heading
blog.metafields.custom.hero_subheading
blog.metafields.custom.hero_eyebrow
blog.metafields.custom.featured_article
blog.metafields.custom.topic_cards
blog.metafields.custom.consultation_heading
blog.metafields.custom.consultation_text
```

## Article page uses

```liquid
article.title
article.excerpt
article.content
article.image
article.author
article.published_at
article.tags
article.metafields.custom.hindi_title
article.metafields.custom.hero_badge
article.metafields.custom.at_a_glance
article.metafields.custom.visual_explainer
article.metafields.custom.pull_quote
article.metafields.custom.try_this_today
article.metafields.custom.ingredient_cards
article.metafields.custom.words_to_know
article.metafields.custom.sources
article.metafields.custom.medical_disclaimer
article.metafields.custom.related_articles
```

---

# 4. Metafields and metaobjects to create

Create these under:

```text
Shopify Admin → Settings → Custom data
```

## Blog metafields

Owner type: **Blog**

```text
custom.hero_eyebrow
Single line text

custom.hero_heading
Single line text

custom.hero_subheading
Multi-line text

custom.primary_cta_label
Single line text

custom.primary_cta_link
URL

custom.topic_count_label
Single line text

custom.read_count_label
Single line text

custom.featured_article
Article reference

custom.topic_cards
List of metaobject references: dhyan_topic_card

custom.consultation_heading
Single line text

custom.consultation_text
Multi-line text

custom.consultation_cta_label
Single line text

custom.consultation_cta_link
URL
```

---

## Article metafields

Owner type: **Article**

```text
custom.hindi_title
Single line text

custom.hero_badge
Single line text

custom.review_label
Single line text

custom.read_time
Single line text

custom.at_a_glance
List of metaobject references: dhyan_bullet_item

custom.visual_explainer
Metaobject reference: dhyan_visual_explainer

custom.pull_quote
Multi-line text

custom.try_this_today
List of metaobject references: dhyan_tip_item

custom.ingredient_cards
List of metaobject references: dhyan_ingredient_card

custom.words_to_know
List of metaobject references: dhyan_definition_item

custom.sources
Multi-line text

custom.medical_disclaimer
Multi-line text

custom.related_articles
List of article references

custom.sticky_cta_label
Single line text

custom.sticky_cta_link
URL
```

---

# 5. Metaobjects to create

## `dhyan_topic_card`

Used for the blog hub topic grid.

```text
image
File

title
Single line text

hindi_title
Single line text

article_count
Number

link
URL
```

Matches these cards:

```text
Digestion & gut
Food & kitchen
Herbs & remedies
Weight & cravings
Immunity
Sleep & energy
Skin & glow
Hair & scalp
```

---

## `dhyan_bullet_item`

Used in “At a glance.”

```text
text
Multi-line text
```

---

## `dhyan_visual_explainer`

Used for the “Agni · The digestive fire” style card.

```text
eyebrow
Single line text

heading
Single line text

image
File

description
Multi-line text
```

---

## `dhyan_tip_item`

Used in “Try this today.”

```text
title
Single line text

description
Multi-line text
```

---

## `dhyan_ingredient_card`

Used for herb/ingredient cards.

```text
image
File

name
Single line text

sanskrit_name
Single line text

description
Multi-line text
```

---

## `dhyan_definition_item`

Used in “Words to know.”

```text
term
Single line text

definition
Multi-line text
```

---

# 6. Visual rules from the screenshots

Use these as the design system.

## Colors

```text
Page background: #fffdf8 / warm white
Cream cards: #fff7ea / #fff8ef
Borders: #eadcc8
Primary orange: #c94f17 / #d35418
Dark text: #1e1e1e
Body text: #4e4a45
Muted text: #7b746c
Blue link: #1f5f9d
```

## Layout

```text
Main container: 1040px to 1120px
Article content width: 680px to 760px
Large cards: 100% width inside article column
Blog grid: 4 columns desktop
Related articles: 3 columns desktop
Mobile grid: 1 column
Tablet grid: 2 columns
```

## Border radius

```text
Large cards: 22px to 28px
Article cards: 18px
Buttons/pills: 999px or 16px
```

## Typography

```text
Large blog heading: 48px to 56px desktop
Article title: 36px to 44px desktop
Section headings: 24px to 30px
Body text: 16px to 18px
Line height: 1.7 to 1.85
Eyebrows: uppercase, orange, letter-spaced
```

## Components to match

```text
Cream editorial cards
Thin orange left border on “At a glance”
Rounded article cards with image top
Orange divider below images
Floating “Ask Guruji” button
Soft shadow under big cards
Sticky header behavior optional
Mobile sticky CTA optional
```

---

# 7. Best implementation prompt

Use this prompt to generate the actual Shopify code:

```text
You are an expert Shopify Liquid theme developer.

We are building a scalable Shopify blog system inspired by the provided DhyanHQ Ayurveda screenshots.

Important:
This is not a one-off page. Do not hardcode “Acidity and heartburn” content. Build reusable Shopify Blog and Article templates that work for every article inside the Ayurveda blog.

Create these files:

1. templates/blog.ayurveda.json
2. templates/article.ayurveda.json
3. sections/dhyan-blog-hub.liquid
4. sections/dhyan-article-template.liquid
5. snippets/dhyan-article-card.liquid
6. snippets/dhyan-topic-card.liquid

The design should match the screenshots:
- Warm Ayurveda editorial style
- Cream/off-white backgrounds
- Orange accents
- Rounded cards
- Thin borders
- Soft shadows
- Large article hero image
- Centered article content column
- Blog hub with hero, featured article, topic grid, and consultation CTA
- Article detail with hero, metadata, at-a-glance card, visual explainer card, article body, pull quote, tip cards, ingredient cards, words-to-know card, sources, disclaimer, related articles, and floating CTA

Use this dynamic content model:

Blog fields:
- blog.title
- blog.articles
- blog.metafields.custom.hero_eyebrow
- blog.metafields.custom.hero_heading
- blog.metafields.custom.hero_subheading
- blog.metafields.custom.primary_cta_label
- blog.metafields.custom.primary_cta_link
- blog.metafields.custom.featured_article
- blog.metafields.custom.topic_cards
- blog.metafields.custom.consultation_heading
- blog.metafields.custom.consultation_text
- blog.metafields.custom.consultation_cta_label
- blog.metafields.custom.consultation_cta_link

Article fields:
- article.title
- article.excerpt
- article.content
- article.image
- article.author
- article.published_at
- article.tags
- article.metafields.custom.hindi_title
- article.metafields.custom.hero_badge
- article.metafields.custom.review_label
- article.metafields.custom.read_time
- article.metafields.custom.at_a_glance
- article.metafields.custom.visual_explainer
- article.metafields.custom.pull_quote
- article.metafields.custom.try_this_today
- article.metafields.custom.ingredient_cards
- article.metafields.custom.words_to_know
- article.metafields.custom.sources
- article.metafields.custom.medical_disclaimer
- article.metafields.custom.related_articles
- article.metafields.custom.sticky_cta_label
- article.metafields.custom.sticky_cta_link

Metaobjects:
1. dhyan_topic_card
Fields:
- image
- title
- hindi_title
- article_count
- link

2. dhyan_bullet_item
Fields:
- text

3. dhyan_visual_explainer
Fields:
- eyebrow
- heading
- image
- description

4. dhyan_tip_item
Fields:
- title
- description

5. dhyan_ingredient_card
Fields:
- image
- name
- sanskrit_name
- description

6. dhyan_definition_item
Fields:
- term
- definition

Code requirements:
- Use valid Shopify Liquid.
- Use Online Store 2.0 JSON templates.
- Use complete {% schema %} in both sections.
- Use image_url and image_tag, not img_url or img_tag.
- Use metafield values safely with .value where needed.
- Render metaobject reference lists dynamically.
- Render article reference lists dynamically.
- Add graceful fallbacks if metafields are empty.
- Do not hardcode article-specific content.
- Do not use external CSS or JS libraries.
- Prefix all classes with dhyan-blog- or dhyan-article-.
- Keep CSS scoped to the sections.
- Use responsive CSS inside {% stylesheet %}.
- Match desktop and mobile layouts.
- Use semantic HTML.
- Use accessible links and buttons.
- Add a floating “Ask Guruji” CTA using section settings.
- Add a mobile sticky CTA on article pages only when the article metafield exists.

Responsive rules:
- Desktop blog topic grid: 4 columns.
- Tablet blog topic grid: 2 columns.
- Mobile blog topic grid: 1 column.
- Desktop related articles: 3 columns.
- Mobile related articles: 1 column.
- Article content max width: around 760px.
- Main page max width: around 1120px.
- Hero image should be full width with soft fade/rounded visual treatment similar to screenshots.
- Cards should use cream background, orange accent, border, and rounded corners.

Output:
Give the full code for each file separately, with the file path before each code block.
Also include concise installation steps and a QA checklist.
```

---

# 8. How each new article will work

For every Ayurveda article:

1. Create a new Shopify article inside the Ayurveda blog.
2. Add title, excerpt, image, and article body.
3. Fill the article metafields.
4. Add related articles.
5. Add cards like “At a glance,” “Try this today,” and “Words to know.”
6. The template automatically renders the full design.

Example:

```text
Article:
Acidity and heartburn

Article body:
Long editorial explanation

Metafields:
Hindi title
At a glance bullets
Agni visual explainer
Try this today cards
Ingredient cards
Words to know
Sources
Related articles
```

Then another article like “Gas and bloating” uses the same exact template, only with different metafield values.

---

# 9. Final build order

Build in this order:

```text
1. Create metaobject definitions
2. Create blog metafields
3. Create article metafields
4. Build snippets
5. Build blog hub section
6. Build article template section
7. Create JSON templates
8. Assign blog template to Ayurveda blog
9. Assign article template to Ayurveda articles
10. QA desktop and mobile
```

This gives you the same design language as the screenshots, but in a scalable Shopify blog architecture.
