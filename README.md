# Capstone-AI-Humanities
A Generative AI framework for Digital Ethnography: Decoding local authenticity and cultural signals in Vietnamese gastronomy reviews.

# The Authentic Gaze: Decoding Gastronomic Heritage

> **Course:** 2026S 136031-1 GenAI for Humanists
> **Author:** Nguyen Ngoc Huyen Tran
> **Matrikelnummer:** 11922332
> **Status:** Project Proposal (Delivery 2 — Revised)

## 1. Personal Motivation & Context

This project is inspired by my recent journey through Vietnam. As a member of the Vietnamese diaspora born in the West, my goal was to reconnect with my heritage by seeking out "local-approved" culinary experiences.

During this trip, I realized that platforms like Google Maps often prioritize high-volume, tourist-rated locations. I found myself manually filtering through hundreds of reviews, looking for Vietnamese names and non-translated "Teencode" to find the "real" food. This project uses Generative AI to study that filtering process rather than simply automate it — see Section 3 for why this distinction matters.

## 2. Project Objectives

The objective of this capstone is to leverage Generative AI to:

* **Deconstruct the "Tourist Bubble":** Examine how review platforms and their algorithms surface certain linguistic and cultural signals over others, and what gets systematically pushed down.
* **Bridge the Diaspora Gap:** Build a prototype that helps "Việt Kiều" (Overseas Vietnamese) read reviews through a more locally-grounded lens.
* **Demonstrate a Re-Ranking Method:** Produce a working demonstration — not a deployed product — that shows how an alternative, locally-weighted ranking could look for a small, hand-picked sample of venues. (Revised from "Empower Small Vendors": see Section 8.)

## 3. Relevance to Humanistic Inquiry & Literature Review

This project sits at the intersection of **Digital Ethnography**, **Tourism Studies**, and **Gastropolitics**. Rather than treating "authenticity" as a fact to be detected, the project treats it as a *discourse* — something produced through language, platform design, and the positionality of the reviewer. Key frameworks:

* **John Urry — The Tourist Gaze (1990):** Urry argues that tourists don't see places neutrally; they see them through socially and historically constructed expectations of what is worth looking at. Review platforms can be read as infrastructure that organizes and reproduces this gaze, surfacing what conforms to outsider expectations of "exotic" or "authentic" Vietnamese food.
* **Dean MacCannell — Staged Authenticity (1973, *The Tourist Setting*):** MacCannell's concept of "staged authenticity" describes how spaces are deliberately presented to *appear* backstage/authentic to visitors while remaining a performance. This is directly relevant to vendors who may perform "localness" for a tourist audience — meaning even "authentic-coded" reviews may be reviewing a staged front, not unmediated local life.
* **Arjun Appadurai — Gastropolitics (1981, "Gastro-Politics in Hindu South Asia"):** Appadurai's framing of food as a site where social and political relations are negotiated supports treating restaurant reviews not as neutral consumer feedback but as a political text — claims of who has the right to evaluate, define, or "own" a cuisine.
* **Lugosi & Bell — Platform-mediated food culture:** Their work on hospitality, food, and digital platforms is relevant to how reviews on Google Maps/TripAdvisor are shaped by platform incentives (star ratings, review-volume sorting, language defaults) — meaning the "Tourist Bubble" is partly an artifact of platform design, not just user behavior.

This literature reframes the project's contribution: it is not just a ranking tool, but an empirical case study in how a corpus of user-generated text encodes contested cultural authority, building on this lineage of "gaze" and "staging" theory.

## 4. The Central Research Question

Rather than optimizing for "authenticity" as a fixed target, this project asks:

> **What signals do reviewers code as "authentic," and whose interests does that coding serve?**

This reframes the deliverable: the goal is not to build a machine that correctly *identifies* authentic food, but to build a method for *surfacing and interrogating the linguistic patterns* that different reviewer groups use to claim authority over what counts as authentic — and to make visible whose voice (local, diaspora, tourist) the dominant platform ranking privileges.

Working sub-questions:
* Do Vietnamese-language and English-language reviews of the same venue diverge in what they praise (technique, ingredients, price, décor, service)?
* Does the platform's default sort (rating, review count) correlate with reviews that use tourist-coded language (English, comfort, cleanliness) over locally-coded language (technique, regional dialect, specific dish terms)?
* What do reviewers who *do* use insider language have in common, and what do they implicitly exclude?

## 5. AI Techniques to Be Employed

* **Multilingual LLM Analysis:** Using models such as GPT-4 or Gemini to analyze reviews in their original Vietnamese, identifying cultural markers and regional slang (e.g., distinguishing "ngon" from more specific, technique-referencing local praise).
* **Sentiment Weighting:** Categorizing what reviews praise (e.g., broth depth, traditional technique) versus what they praise less centrally (e.g., English-speaking staff, décor), to make visible — not optimize away — the difference in evaluative criteria between reviewer groups.
* **Zero-Shot Persona Tagging ("Cultural Insider" vs "Casual Traveler"):** See Section 6 for the concrete operationalization of this classifier.

## 6. Operationalizing the Cultural Insider / Casual Traveler Classifier

This was previously left abstract ("based on linguistic nuance"). The classifier will be driven by a defined, checkable feature set:

**Candidate linguistic features (the prompt will ask the LLM to look for these explicitly):**
1. Review written in Vietnamese (vs. English or machine-translated).
2. Use of regional/colloquial slang or "Teencode" rather than standard or tourist-guidebook Vietnamese.
3. Mention of specific traditional techniques or ingredients (e.g., bone-broth simmering time, specific herb names, regional variants of a dish) rather than generic praise.
4. Comparative references to other specific local venues or to a home-cooked/family standard ("like my grandmother's") rather than to other tourist venues.
5. Absence of tourist-infrastructure commentary (English menu, AC, card payment, "easy to find") as the central focus of the review.
6. Use of regional dialect markers tied to a specific province/city rather than generalized Vietnamese.

**Before scaling up, 5–10 example prompts will be written and manually checked**, e.g.:
* "Classify this review as Cultural Insider or Casual Traveler. List which of the following features are present: [feature list]. Quote the specific phrase that triggered each feature. If none of the features are present, classify as Casual Traveler by default."
* A second prompt variant that asks the model to give a confidence score and a one-sentence justification, to catch borderline cases.
* A third variant tested on a deliberately ambiguous review (e.g., written in Vietnamese but praising only service) to check the classifier doesn't over-trigger on language alone.

These prompts will be iterated on the hand-coded set described in Section 7 before being applied to the full corpus.

## 7. Validation Plan

To avoid treating LLM output as ground truth, the classifier will be validated as follows:

1. A sample of **30–50 reviews** will be selected (mixed Vietnamese/English, mixed venues).
2. I will hand-classify each review as Cultural Insider / Casual Traveler myself, using the feature checklist in Section 6, before running any model.
3. The LLM will then classify the same set using the finalized prompt.
4. **Agreement rate** (percent agreement, and Cohen's kappa if feasible) between my manual labels and the LLM's labels will be calculated and reported **honestly**, including cases of disagreement and a short qualitative discussion of *why* they diverged (e.g., does the LLM over-weight language choice over content?).
5. This validation step, and its results — including any low agreement — will be included in the final methodology paper as a finding in itself, not hidden as a limitation.

## 8. Expected Outcomes (Revised)

* **A Re-Ranking Demonstration:** Using a small, hand-picked sample of venues, a prototype showing how a "local-signal-weighted" re-ranking could differ from the platform's default sort. This is explicitly a demonstration of method, not a deployed or scaled tool, and makes no claim to "empower" vendors in practice.
* **A Methodology Paper:** Documenting the literature review (Section 3), the classifier design and validation (Sections 6–7), and a discussion of where the method succeeded or failed.
* **Creative Reflection:** A critical reflection on the ethics of using AI to "curate" heritage (Section 9) and on the limits of automating cultural judgment.

## 9. Ethics

This project raises several ethical questions that need to be addressed directly, not as an afterthought:

* **Terms of Service & data collection:** Review data (e.g., from Google Maps) will only be collected in ways that comply with the relevant platform's Terms of Service. This likely rules out bulk scraping of Google Maps reviews directly, since Google's ToS restricts automated extraction of review content. The project will instead use either: (a) a sanctioned API (e.g., Google Places API, within its usage limits and data-handling terms) for a small sample, (b) a smaller manually-collected/screenshotted sample for the validation set with clear documentation of how it was gathered, or (c) an existing, licensed/public dataset of Vietnamese restaurant reviews if one is identified. Whichever route is chosen, the ToS of the source platform will be cited and quoted in the methodology paper, and any usage limits will be respected.
* **Privacy of individual reviewers:** Reviews are written by identifiable individuals (often with full names and photos attached). Any reviews quoted or shown as examples in the methodology paper or prototype will be anonymized (no usernames, no profile photos, and minor paraphrasing of distinctive details where a quote could otherwise be traced back to a specific public profile).
* **The politics of labeling some reviewers "more authentic":** Tagging individuals as "Cultural Insider" vs "Casual Traveler" is itself an act of gatekeeping — the same kind of boundary-drawing the project critiques in platforms. The classifier's output will be framed and reported as *the model's reading of linguistic signals*, not as a judgment on any individual's identity, heritage, or right to an opinion about Vietnamese food. The paper will state this limitation explicitly.
* **The diaspora-as-arbiter question:** As a member of the diaspora, I occupy an ambiguous position — neither a "local" by current residence nor a "tourist" by heritage. This means the project's own design choices (which features count as "authentic," whose Vietnamese is treated as "standard" vs "slang") are not neutral; they reflect my particular diaspora vantage point. This will be made explicit in the methodology paper as a positionality statement, rather than presenting the classifier as an objective instrument. Where possible, I will note alternative interpretations a Vietnam-resident researcher might offer for the same data.
