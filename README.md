# Capstone-AI-Humanities
A Generative AI framework for Digital Ethnography: Decoding local authenticity and cultural signals in Vietnamese gastronomy reviews.

# The Authentic Gaze: Decoding Gastronomic Heritage

> **Course:** 2026S 136031-1 GenAI for Humanists
> **Author:** Nguyen Ngoc Huyen Tran
> **Matrikelnummer:** 11922332
> **Status:** Project Proposal & Architecture

---

## 1. Personal Motivation & Context

This project is inspired by my recent journey through Vietnam. As a member of the Vietnamese diaspora born in the West, my goal was to reconnect with my heritage by seeking out "local-approved" culinary experiences.

During this trip, I realized that platforms like Google Maps often prioritize high-volume, tourist-rated locations. I found myself manually filtering through hundreds of reviews, looking for Vietnamese names and non-translated "Teencode" to find the "real" food. This project uses Generative AI to study that filtering process rather than simply automate it — see Section 3 for why this distinction matters.

---

## 2. Project Objectives

The objective of this capstone is to leverage Generative AI to:

* **Deconstruct the "Tourist Bubble":** Examine how review platforms and their algorithms surface certain linguistic and cultural signals over others, and what gets systematically pushed down.
* **Bridge the Diaspora Gap:** Build an interactive application that helps "Việt Kiều" (Overseas Vietnamese) read reviews through a more locally-grounded lens.
* **Demonstrate a Human-in-the-Loop Re-Ranking Method:** Produce an interactive web prototype showing how an alternative, locally-weighted ranking shifts recommendations for a small, hand-coded sample of venues.

---

## 3. Relevance to Humanistic Inquiry & Literature Review

This project sits at the intersection of **Digital Ethnography**, **Tourism Studies**, and **Gastropolitics**. Rather than treating "authenticity" as a fact to be detected, the project treats it as a *discourse* — something produced through language, platform design, and the positionality of the reviewer. Key frameworks:

* **John Urry — The Tourist Gaze (1990):** Urry argues that tourists don't see places neutrally; they see them through socially and historically constructed expectations of what is worth looking at. Review platforms can be read as infrastructure that organizes and reproduces this gaze, surfacing what conforms to outsider expectations of "exotic" or "authentic" Vietnamese food.
* **Dean MacCannell — Staged Authenticity (1973, *The Tourist Setting*):** MacCannell's concept of "staged authenticity" describes how spaces are deliberately presented to *appear* backstage/authentic to visitors while remaining a performance. This is directly relevant to vendors who may perform "localness" for a tourist audience — meaning even "authentic-coded" reviews may be reviewing a staged front, not unmediated local life.
* **Arjun Appadurai — Gastropolitics (1981, "Gastro-Politics in Hindu South Asia"):** Appadurai's framing of food as a site where social and political relations are negotiated supports treating restaurant reviews not as neutral consumer feedback but as a political text — claims of who has the right to evaluate, define, or "own" a cuisine.

This literature reframes the project's contribution: it is not just a ranking tool, but an empirical case study in how a corpus of user-generated text encodes contested cultural authority, building on this lineage of "gaze" and "staging" theory.

---

## 4. The Central Research Question

Rather than optimizing for "authenticity" as a fixed target, this project asks:

> **What signals do reviewers code as "authentic," and whose interests does that coding serve?**

This reframes the deliverable: the goal is not to build a machine that correctly *identifies* authentic food, but to build a method for *surfacing and interrogating the linguistic patterns* that different reviewer groups use to claim authority over what counts as authentic — and to make visible whose voice (local, diaspora, tourist) the dominant platform ranking privileges.

### Working Sub-Questions:
* Do Vietnamese-language and English-language reviews of the same venue diverge in what they praise (technique, ingredients, price, décor, service)?
* Does the platform's default sort (rating, review count) correlate with reviews that use tourist-coded language (English, comfort, cleanliness) over locally-coded language (technique, regional dialect, specific dish terms)?
* What do reviewers who *do* use insider language have in common, and what do they implicitly exclude?

---

## 5. AI Techniques to Be Employed

* **Multilingual LLM Analysis:** Using advanced models (e.g., GPT-4 / Gemini) to analyze reviews in their original Vietnamese, identifying cultural markers and regional slang (e.g., distinguishing generic praise from specific, technique-referencing local terminology).
* **Linguistic Attribute Weighting:** Categorizing what reviews praise (e.g., broth depth, traditional technique) versus peripheral markers (e.g., English-speaking staff, infrastructure), to make visible the differences in evaluative criteria between reviewer groups.
* **Zero-Shot Persona Tagging ("Cultural Insider" vs "Casual Traveler"):** Executing a programmatic classifier using specialized prompt engineering to evaluate reviewer positionality.

---

## 6. Operationalizing the Classifier

The classifier is driven by a defined, checkable feature set:

### Candidate Linguistic Features:
1. Review written in Vietnamese (vs. English or machine-translated).
2. Use of regional/colloquial slang or "Teencode" rather than standard or tourist-guidebook Vietnamese.
3. Mention of specific traditional techniques or ingredients (e.g., bone-broth simmering time, specific herb names, regional variants) rather than generic praise.
4. Comparative references to other specific local venues or to a home-cooked/family standard ("like my grandmother's") rather than to other tourist venues.
5. Absence of tourist-infrastructure commentary (English menu, AC, card payment, "easy to find") as the central focus of the review.
6. Use of regional dialect markers tied to a specific province/city rather than generalized Vietnamese.

---

## 7. Human-in-the-Loop Validation Plan

To maintain absolute academic transparency and prevent treating LLM outputs as blind ground truth, the classifier undergoes a strict human evaluation workflow:

1. **The Ground Truth Set:** A curated corpus of restaurant reviews across multiple distinct venues is hand-coded.
2. **Manual Blind Coding:** I manually classify each review as `cultural insider` or `casual traveler` using the strict linguistic feature checklist prior to executing the AI script.
3. **LLM Execution:** The API processes the identical corpus using the programmatic prompt structure.
4. **Agreement Evaluation:** Overall Cohen’s Kappa or Percentage Agreement rates are calculated. Divergences are treated as critical qualitative data for "error analysis" in the final thesis, unpacking where the model over-indexes on syntax over cultural intent.

---

## 8. Expected Outcomes

* **Interactive Re-Ranking Chat Interface / Prototype:** A lightweight **Streamlit web application** simulating an intelligent ethnographic partner. Users can interact with the system or toggle weights (e.g., "Prioritize Insider Signals") to witness how a hand-picked culinary sample re-ranks itself when stripping away the "Tourist Bubble."
* **A Methodology & Critique Paper:** Documenting the literature review (Section 3), the validation data comparisons (Section 7), and an academic discussion of where automated cultural judgment breaks down.
* **Creative Reflection:** A humanistic critique focused on the ethics of utilizing structural AI to "curate" heritage and map human tastes.

---

## 9. Ethics & Positionality

* **Terms of Service & Data Integrity:** Data utilization complies cleanly with target platform restrictions, relying exclusively on small, specialized sampling to maintain compliance while prioritizing qualitative human evaluation.
* **Anonymization & Privacy:** Reviews are entirely anonymized in all published materials. Usernames, profile imagery, and easily traceable personal references are stripped out to protect public profiles.
* **The Boundaries of Tagging:** Tagging individuals as "Cultural Insider" vs "Casual Traveler" is acknowledged as an act of boundary-drawing. Results are strictly framed as *the model's reading of linguistic text structures*, not as a finite existential judgment on an individual’s identity or heritage.
* **Diaspora Positionality Statement:** As a member of the Western-born diaspora, my own background shapes what features are weighted as "authentic local signals." This subjectivity is openly embraced as an ethnographic reality of the project framework, rather than hidden behind claims of objective algorithmic truth.
