# AI Listing Assistant: Amazon Listing Copy from a Short Brief

**Harini Ganesan** · Tools: Claude (Project with custom instructions) · Products are generic examples, not from any company

## 1. Problem

Writing an Amazon listing (title, 5 bullet points and search terms) by hand takes me about 30 to 45 minutes. Quality also varies: titles run over the character limit, bullets repeat each other, and unproven claims slip in.

**Question:** can a simple AI assistant with fixed instructions write listings faster, without losing quality?

## 2. How the tool works

| Part | Detail |
|---|---|
| Tool | A Claude Project with fixed instructions (see [`instructions.md`](instructions.md)) |
| Input | A one-line product brief |
| Output | Title (up to 200 characters), 5 bullet points and backend search terms |
| Rules | Fixed title order, benefit-led bullets, no promotional words, and use only facts from the brief |

## 3. Test design

| Item | Detail |
|---|---|
| Products | 3 generic products |
| Baseline | My usual time to write one listing by hand at work (estimate, not timed) |
| With the tool | I ran each brief through the assistant and timed it, including reading and editing the output |
| Quality check | Each output checked against the same 5-point checklist |

**Briefs**

| # | Brief |
|---|---|
| A | Stainless steel water bottle, 750 ml, keeps drinks cold 24 hrs and hot 12 hrs, leak-proof lid, BPA-free, for gym and office |
| B | Bamboo toothbrush, pack of 4, soft bristles, biodegradable handle, for adults |
| C | Anti-slip yoga mat, 6 mm, TPE material, with carry strap, for beginners |

## 4. Results

**Time per listing**

| Listing | By hand (my usual time, estimate) | With the tool, incl. review (timed) |
|---|---|---|
| A | 30–45 min | 3 min 40 sec |
| B | 30–45 min | about 2–3 min |
| C | 30–45 min | about 2–3 min |

**Time saved:** about **88–92% per listing**. For a batch of 20 listings, that is roughly 9–14 hours by hand against about 1 hour with the tool.

**Quality checklist (✅ met, ❌ not met)**

| Check | A | B | C |
|---|---|---|---|
| Title within 200 characters | ✅ 158 | ✅ 128 | ✅ 124 |
| Key specs in the title | ✅ | ✅ | ✅ |
| 5 distinct bullets, no repetition | ✅ | ✅ | ✅ |
| Search terms added | ✅ | ✅ | ✅ |
| Only facts from the brief | ✅ after my edits | ❌ | ❌ |

## 5. Key finding: the tool still invents details

Even with a clear "use only facts in the brief" rule, the tool added product details that were not in the brief:

| Listing | Details the tool added |
|---|---|
| B | Moso bamboo, nylon bristles, handles numbered 1 to 4, kraft paper packaging, each brush in its own box |
| C | Textured on both sides, dual-layer build, body alignment lines, water-resistant surface |

These sound believable, which makes them risky: if the real product differs, the listing is misleading and can lead to returns or complaints.

For listing A, I used the review step to add real details myself (brand name, steel grade and care instructions). That is the right way round: **the human supplies the facts, the tool supplies the structure and wording.**

## 6. Sample output (listing A, after my review)

**Title** (158 characters)
> Bolt Vacuum Insulated Water Bottle with Leak-Proof Lid, Keeps Drinks Cold 24 Hours and Hot 12 Hours, 750 ml, 304 Stainless Steel, BPA-Free, for Gym and Office

**Bullets**
- 24 HRS COLD, 12 HRS HOT: Double-wall vacuum insulation keeps drinks cold for up to 24 hours and hot for up to 12 hours, so chilled water lasts your full gym session and morning tea stays warm at your desk.
- 750 ML CAPACITY: Holds 750 ml of water, tea or coffee, enough for a complete workout or a long day of meetings, so you make fewer trips to the water cooler. No sweating on the outside, so bags and desks stay dry.
- 304 STAINLESS STEEL AND BPA-FREE: Made from food-grade 304 stainless steel with a BPA-free lid. Does not hold on to smells or flavours, so you can switch between water, tea and coffee without any aftertaste.
- LEAK-PROOF SCREW LID: The screw-on lid with carry loop seals tight, so you can toss the bottle into your gym bag or office backpack without spills. Easy to clean: rinse with warm soapy water. Hand wash only.
- FOR GYM, OFFICE AND TRAVEL: Made for gym-goers, working professionals and daily commuters who want one bottle all day. In the box: 1 Bolt 750 ml stainless steel water bottle with leak-proof lid.

**Backend search terms**
> flask thermos sipper metal double wall travel commute daily use sports workout fitness yoga cycling hiking trekking spill proof non toxic men women college gift

*"Bolt" is a made-up brand for this test.*

## 7. Limits

| Limit | Effect |
|---|---|
| By-hand time is my estimate, not timed | The time saving is approximate |
| Only 3 products | A small test, not a full study |
| One person tested and reviewed | No second reviewer checked quality |

## 8. Improvement made after the test

I updated [`instructions.md`](instructions.md) so the tool must end every listing with **a list of every detail it used that was not in the brief**. The reviewer can then check each one instead of hunting for them. A fuller brief (material, size, what's in the box) would also cut down invented details.

## 9. What I learned

- AI cut drafting time by about 90%, but **review is not optional**: the tool added believable details that were not in the brief.
- Clear instructions control structure and length very well. They control facts less well.
- The best use is **human facts + AI structure**: I bring the product knowledge, the tool handles the format and wording.
