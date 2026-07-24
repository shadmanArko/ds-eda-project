# Slide Content Draft — King County Housing EDA for Bonnie Brown

Target: ~10 minutes presenting (14 slides, ~40–45 sec/slide average), + 5 min discussion. Build this in Keynote/PowerPoint/Google Slides, export the final deck to PDF, and save it in this `slides/` folder. Do not present from the Jupyter notebook.

Each slide below has: **Title**, **On-slide content** (keep it this short — slides are prompts, not scripts), **Speaker notes** (what you actually say), and **Visual** (what to screenshot/embed from `05_eda.ipynb`).

---

## Slide 1 — Title

**On-slide:**
> Should You Sell Now, or Wait?
> A Data-Driven Look at King County's Middle-Class Housing Market
> Prepared for Bonnie Brown by [Your Name]

**Speaker notes:** Introduce yourself in one sentence — who you are and what you did (analyzed King County home sales data to answer Bonnie's specific questions about selling her house).

**Visual:** None, or a clean title graphic. No chart yet.

---

## Slide 2 — Agenda

**On-slide:**
- Who is Bonnie, and what does she need to decide?
- What data we looked at
- What we found
- What we recommend

**Speaker notes:** One sentence per bullet, just orienting the audience to the shape of the talk. Keep this slide on screen for ~15 seconds max.

**Visual:** None.

---

## Slide 3 — Meet the Client

**On-slide:**
- **Bonnie Brown** — selling her house
- Lives in a "middle-class" King County neighborhood
- Wants to move within the next 6–12 months
- Goal: the best possible sale price

**Speaker notes:** State plainly that Bonnie is a hypothetical client built for this project, and that "middle-class neighborhood" is something you defined precisely with data (teased here, explained fully next slide) — not a vague guess.

**Visual:** None, or a simple icon/illustration.

---

## Slide 4 — What Counts as "Middle-Class"?

**On-slide:**
- We ranked all King County zip codes by median home price
- "Middle-class" = the middle 20% of that ranking (40th–60th percentile)
- Result: **14 zip codes**, all genuinely comparable to Bonnie's situation

**Speaker notes:** This is the one assumption you should be most explicit about, per the brief. Explain briefly *why* percentile-of-median-price is a reasonable definition (it's relative, county-wide, and defensible) rather than something arbitrary. Keep it simple — no SQL, no formulas on screen.

**Visual:** Optional simple diagram (a number line with the middle band highlighted), or skip visual and rely on speech.

---

## Slide 5 — The Data

**On-slide:**
- **3,818 home sales** across those 14 zip codes
- Sold between **May 2014 and May 2015**
- Includes size, condition, quality, age, renovation history, and location for each home

**Speaker notes:** Ground the audience in scale and time span before any findings. Mention (briefly, one sentence) that the data was cleaned first — fixed a data-entry bug, handled missing values responsibly — so the numbers that follow can be trusted. Don't go into cleaning mechanics here; that's not for this audience.

**Visual:** The "Bonnie's market, at a glance" summary table from the Data Overview section (median price, typical size, typical layout, typical grade, % renovated).

---

## Slide 6 — What a Typical Home Looks Like

**On-slide:**
- Median sale price: **$450,000**
- Typical size: **~1,970 sqft**
- Typical layout: **3 bed / 2.2 bath**
- Only **2.9%** of homes had ever been renovated

**Speaker notes:** This is the baseline everything else compares against. Mention briefly that you use the *median*, not the average, because a few very expensive sales would otherwise skew the picture — one plain-English sentence, not a stats lecture.

**Visual:** The price distribution histogram (with the median line).

---

## Slide 7 — How We Approached This

**On-slide:**
- We tested 5 specific questions relevant to Bonnie's situation:
  1. Does *when* she sells matter?
  2. Does condition or build quality matter more?
  3. Is renovating worth it?
  4. Does her exact location matter?
  5. What matters more — size or room count?

**Speaker notes:** Frame this as "we didn't just look at everything randomly — we asked the questions that actually matter for someone in Bonnie's position, then checked what the data says." This sets up the results section as answers to a checklist, which is easy for a non-technical audience to follow.

**Visual:** None — this is a transition/roadmap slide.

---

## Slide 8 — Finding 1: Location Still Matters (Geographic)

**On-slide:**
- Even within "middle-class," prices vary a lot by zip code
- Highest: **$515,000** (zip 98072) — Lowest: **$401,250** (zip 98019)
- That's a **28% difference**, zip code to zip code
- Higher-priced areas cluster closer to Seattle and the water

**Speaker notes:** This is your required geographic insight — give it real weight. Point out on the map where the expensive vs. cheaper clusters are. Land the point: "middle-class" is not one price, and Bonnie's specific zip code matters more than any single fix-up she could make.

**Visual:** The interactive map (screenshot it, or embed a static export) and/or the sorted zip-code bar chart.

---

## Slide 9 — Finding 2: Buyers Pay for Quality, Not Just Upkeep

**On-slide:**
- **Build quality (grade)** strongly affects price — moving up a couple of grade levels can mean **~59% more**
- **Condition** (cleanliness/upkeep) barely affects price at all
- Translation: a fresh coat of paint won't fix a lower-quality build

**Speaker notes:** This is the most counter-intuitive, most memorable finding — spend real time here. Emphasize the practical implication: don't expect cosmetic touch-ups to raise the price much. Contrast "how well-built" vs. "how well-kept" clearly, since these are easy to conflate.

**Visual:** The two boxplots (price by condition, price by grade) side by side.

---

## Slide 10 — Finding 3: Space Beats Room Count

**On-slide:**
- Livable **square footage** is the strongest single driver of price
- More bedrooms alone — without more usable space — barely moves the price
- Two "3-bedroom" homes can be worth very different amounts

**Speaker notes:** Practical takeaway: if Bonnie is ever weighing "add a bedroom" vs. "add square footage" (e.g., finish a basement), the data favors usable space.

**Visual:** The sale-price-vs-living-area scatter plot with trend line.

---

## Slide 11 — Finding 4: Renovation Pays Off More Than Timing

**On-slide:**
- Renovated homes sell for **~21% more per square foot**
- The season of sale only moves price by **3–4%** (Spring is slightly best)
- Renovation is a bigger, more expensive decision — but a real one

**Speaker notes:** Be upfront about the caveat here (softly, in plain language): this is based on a smaller group of renovated homes, so treat it as a strong signal, not a guarantee. If Bonnie has budget and her 6–12 month timeline allows it, a real renovation looks worthwhile; picking the "right month" to list is a nice-to-have, not a game-changer.

**Visual:** The renovated vs. not-renovated price-per-sqft boxplot, and/or the season boxplot.

---

## Slide 12 — Bonus Finding: Water Changes Everything

**On-slide:**
- Only **~1%** of homes in this data are waterfront — but they sell for **$1.15M+ median**, more than double the typical price
- Homes with any view also sell for significantly more
- Worth checking if this applies to Bonnie's home specifically

**Speaker notes:** Frame as a "we noticed something bigger than what we set out to check" moment — it's honest, it shows thoroughness, and it's a natural high note before recommendations. Keep it brief; it's a footnote to the main story, not a new deep-dive.

**Visual:** The waterfront/view bar charts, or a couple of numbers on screen.

---

## Slide 13 — Our Recommendations for Bonnie

**On-slide:**
1. Price based on **her exact zip code**, not "middle-class" in general
2. Skip pure cosmetic fixes — they won't move the price
3. Consider a **real renovation** if time and budget allow
4. If adding space, prioritize **square footage over bedroom count**
5. List in **spring** if her timeline is flexible
6. Check for **any water view** — it could change the whole plan

**Speaker notes:** Walk through these briskly — the audience has already seen the evidence for each, so this slide is a recap/checklist, not a new argument. Point out these are ordered roughly by impact (location and quality-related factors first, timing last).

**Visual:** None — clean bulleted list, this is the slide people will screenshot.

---

## Slide 14 — Closing / Questions

**On-slide:**
> Thank you — Questions?
> [Your name / contact]

**Speaker notes:** One honest caveat before opening for questions: this analysis shows strong patterns in the data, not guarantees for any one house — it's meant to guide Bonnie's priorities, not replace a realtor's specific appraisal. Then open the floor.

**Visual:** None.

---

## Timing Guide (10 minutes)

| Slides | Section | Target time |
| --- | --- | --- |
| 1–2 | Intro/agenda | 0:30 |
| 3–4 | Client & "middle-class" definition | 1:00 |
| 5–6 | Data overview | 1:30 |
| 7 | Approach/roadmap | 0:30 |
| 8–12 | Five findings + bonus | 5:00 (~1 min each) |
| 13 | Recommendations | 1:00 |
| 14 | Closing | 0:30 |

That totals ~10 minutes, leaving the full 5 minutes after for discussion. If you're running long in rehearsal, the easiest cuts are Slide 4 (fold into speech over slide 3) and Slide 12 (mention verbally instead of its own slide).
