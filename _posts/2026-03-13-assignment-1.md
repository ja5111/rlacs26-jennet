---
title: "Assignment 1"
date: 2026-03-13
categories: blog
---

## Feeling the Story: Emotional Word Frequency and Reader Enjoyment in Harry Potter Canon and Fanfiction

*Computational Text Analysis by Jennet and Dalila*

## Introduction

What makes the story more satisfying, and can that pattern be measured? Literature does more than tell stories; it shapes emotional experiences. With the help of digital tools, here we tried to analyze literary works by examining the frequency of certain words, and ask whether those frequencies tell us something meaningful about how readers respond to a text.

This study applies exploratory data analysis (EDA) to five texts from the Harry Potter universe: J.K. Rowling's *Harry Potter and the Goblet of Fire* and *Harry Potter and the Deathly Hallows*, alongside three works of fan fiction, *Harry Potter: Adoptive Kaiju* by Gojirahkiin, *Harry Potter: Djinn Awakened* by Invaderdoom, and *Resurrection* by Sugahhuney, to examine how positive words (happy, love, win, brave) and negative words (fear, hate, loss, sad) are distributed across canonical and fan-created texts, and what that distribution might tell us about reader engagement.

Our guiding question is whether emotional word frequency might serve as a tentative predictor of reader enjoyment. We do not claim a causal relationship, but we explore the possibility that word-level emotional patterns leave a detectable trace in how audiences receive a text. Because the Rowling novels and the fanfiction texts exist in different publishing contexts, it was not possible to use a single engagement metric across all five texts; we use Goodreads ratings for the Rowling texts and AO3 kudos for the fanfics. The results proved more nuanced and, as Ted Underwood might caution, more ambiguous than we had anticipated.

## Corpus Selection

The two Rowling texts anchor the canonical end of the corpus. *Harry Potter and the Goblet of Fire* (2000) is the fourth installment in the series, centered on a dangerous magical tournament. *Harry Potter and the Deathly Hallows* (2007) is the series finale, structured around war, sacrifice, and death.

The three fanfiction texts were selected from the broader Harry Potter fan fiction corpus provided for this course:

- *Harry Potter: Adoptive Kaiju* by Gojirahkiin — a crossover narrative blending themes of belonging and found family with Kaiju mythology
- *Harry Potter: Djinn Awakened* by Invaderdoom — blends the HP universe with Djinn mythology, introducing a darker supernatural conflict
- *Resurrection* by Sugahhuney — a time-travel fix-it narrative centering on loss, redemption, and familial love

In terms of engagement, Resurrection leads the three fanfics with 962 AO3 kudos, followed by Adoptive Kaiju (485) and Djinn Awakened (255). For the Rowling texts, Deathly Hallows holds a Goodreads average rating of 4.62 and Goblet of Fire a 4.57 average.

## Methods

Analysis was conducted using two tools: Voyant Tools for cross-corpus trend visualization and R Markdown in posit.cloud for word frequency heatmapping. In Voyant, we tracked eight target words with wildcard matching (e.g., love*, fear*) across all five texts. In R, we generated a heatmap of raw word counts for the same lexicon, normalized per document.

Our word list was small: four positive words (happy, love, win, brave) and four negative words (fear, hate, loss, sad). The analysis here is therefore exploratory rather than conclusive, consistent with the EDA framing of the assignment.

## Findings

### Fear Dominates the Heatmap, But Not the Trend Graph

In the heatmap, fear registers a raw count of 54 in *Deathly Hallows* — the single highest cell value in the entire visualization. However, the Voyant trend graph does not confirm this dominance in relative frequency terms. This discrepancy is itself a methodological finding: raw counts and relative frequencies can produce different interpretations of the same data.

*[INSERT VOYANT IFRAME HERE]*

*Figure 1: Relative frequency of selected words across all five texts in Voyant Tools.*

### Win Belongs to Goblet of Fire

Win* shows a sharp, localized spike in *Goblet of Fire* in the Voyant trend graph, reaching nearly 0.0019 relative frequency — the highest single-word peak across all eight terms and all five texts. This makes immediate contextual sense: *Goblet of Fire* is structured around a competition. The insight here is methodological: word frequency without context can mislead.

### Love Rises in Fanfiction

Love* tells a different story. While Rowling's two novels show moderate love-word frequency, *Resurrection* spikes dramatically — the highest love* frequency of any text in the corpus. This aligns with its higher AO3 engagement and its genre as a hurt/comfort narrative.

### The Heatmap as Comparative Snapshot

*Deathly Hallows* presents the most emotionally intense profile for negative words: the highest fear (54), and middling sad (4) and hate (6). Among the fanfics, *Resurrection* is distinguished by its love dominance, while *Djinn Awakened* shows more balanced emotional distribution.

![Heatmap]({{ site.baseurl }}/assets/images/heatmap.jpg)
*Figure 2: Word frequency heatmap across all five texts. Color intensity reflects raw word count.*

## Interpretations and Risk of Distant Reading

These patterns are suggestive, but Ted Underwood's caution in *Distant Horizons* is directly applicable here. He warns that quantitative models are no more objective than any other historical interpretation. Our eight-word lexicon is precisely the kind of narrow instrument Underwood would flag. The presence of win* in *Goblet of Fire* is a frequency artifact of plot, not a signal of emotional positivity.

Our engagement metrics carry their own limitations. Goodreads ratings reflect a broad readership of published book readers, while AO3 kudos reflect a specific online fan community. What we can say is that within the fanfiction texts, the pattern holds tentatively: *Resurrection*, the most love-saturated text in the corpus, also has the highest kudos.

## Conclusion

This analysis offers a tentative answer to our opening question: emotional word density, particularly high love* frequency, appears to correlate with stronger reader engagement in fan-created texts. *Resurrection*, which leads the fanfic corpus in both love* frequency and AO3 kudos (962), supports the hypothesis that emotional intensity leaves a detectable trace in how audiences receive a text.

What surprised us most was how genre-specific the word distributions were. Win* belongs almost entirely to *Goblet of Fire*; fear* defines *Deathly Hallows*; love* characterizes *Resurrection*. This suggests that distant reading at word-frequency level may be more useful as a genre signature detector than as a measure of emotional tone broadly.

As Underwood reminds us, the patterns here are real, but they are also partial. Distant reading and close reading remain partners, not rivals, and any meaningful claim about what makes a story satisfying will require both.

## Works Cited

**Primary Texts**

- Rowling, J.K. *Harry Potter and the Goblet of Fire*. Bloomsbury, 2000.
- Rowling, J.K. *Harry Potter and the Deathly Hallows*. Bloomsbury, 2007.
- Gojirahkiin. *Harry Potter: Adoptive Kaiju*. Archive of Our Own, 5 Feb. 2017.
- Invaderdoom. *Harry Potter: Djinn Awakened*. Archive of Our Own, 22 Jan. 2021.
- Sugahhuney. *Resurrection*. Archive of Our Own.

**Scholarly Sources**

- Underwood, Ted. *Distant Horizons: Digital Evidence and Literary Change*. University of Chicago Press, 2019.
- Rockwell, Geoffrey, and Stéfan Sinclair. *Hermeneutica: Computer-Assisted Interpretation in the Humanities*. MIT Press, 2016.
- Moravec, Kimberly. "My Secret Editing Weapon: The Google Ngram Viewer." Medium, 26 Jan. 2021.

## Acknowledgements

*Jennet:* It was really nice working with Dalila in this project. The project was developed jointly from the start: we brainstormed our research question and corpus selection together, produced the Voyant and R visualizations collaboratively, and co-edited the final essay. It was a genuinely enjoyable collaboration and I appreciate her creativity and analytical thinking throughout the process.

*Dalila:* It was a pleasure working with Jennet on this assignment. From the very beginning of the project we collaborated on brainstorming ideas and shaping our research question. Jennet did an excellent job in analyzing our findings, approaching the data with great attention to detail and critical thinking. I genuinely appreciate her dedication and collaborative spirit during the entire process.