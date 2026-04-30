---
title: "Assignment 2"
date: 2026-04-30
categories: blog
---

## Can a Computer Separate Style from Content?

*Computational Text Analysis by Dalila and Jennet*

Literature does more than carry information. It creates patterns, rhythms, and textures that shape how the reader moves through a text. With the help of digital tools, in this essay we tried to examine whether those patterns can be meaningfully distinguished from the content they carry.

This work applies two computational methods to 18 science fiction texts from Project Gutenberg, written by six authors: Leigh Brackett, Philip K. Dick, Henry Kuttner, Andre Norton, H.G. Wells, and Marion Zimmer Bradley. Stylo analyzes style through the most frequent words, the grammatical scaffolding that tends to remain consistent across an author's work regardless of subject. TF-IDF analyzes content through the most distinctive words, the vocabulary that sets each text apart from others. Running both methods on the same corpus gives us a good insight of different pictures of the same texts, and comparing those pictures is where the interesting questions begin to arise.

Our guiding question in this essay is whether style and content reliably pull apart or whether they collapse back into each other. Here, we tried to use the agreement and disagreement between the two methods to explore what each one sees and what each one misses. As Ted Underwood warns in *Distant Horizons* (2019), computational results carry an air of authority that can obscure the many choices behind them. Running two methods side by side is one way of keeping those choices more visible.

The Corpus includes 18 texts that span nearly seventy years. They include fiction and non-fiction, novels and short stories, solo-authored and co-authored works. Three of the six authors are women writing in a male-dominated field: Andre Norton under a male pen name, Leigh Brackett as the "Queen of Space Opera" who fused noir with planetary romance, and Marion Zimmer Bradley whose work explicitly engaged with gender and social hierarchy.

The diversity matters because it sets up the central tension the methods will have to navigate. Philip K. Dick's three texts (*Second Variety*, *The Defenders*, and *The Variable Man*) were all written in 1953, at the height of Cold War anxiety, and share his preoccupation with paranoia, artificial intelligence, and the instability of reality. Henry Kuttner's three texts could not be more different from each other: *The Black Kiss* (co-authored with Robert Bloch) is cosmic horror, *The Ego Machine* is a Hollywood comedy about a playwright and a robot, and *Thunder in the Void* is a space adventure. And H.G. Wells presents the sharpest test case of all: two canonical scientific romances alongside *The Salvaging of Civilization*, a work of non-fiction political philosophy about education and world governance.

A corpus this varied asks hard questions of any classification method. The question is not whether the methods will cluster texts perfectly by author but what the failures reveal.

## What Stylo Sees: The Grammar of Style

Stylo works by counting the most frequent words in each text and measuring stylistic distance between them. The top words (the, and, of, a, to, i, in, he, was, it, that, his, had, with, on) in the generated wordlist are function words and the grammatical skeleton of English prose. Writers cannot easily control how they use them, even when they are carefully shaping their content. This is precisely what makes them useful for authorship attribution.

But the wordlist does not stay at function words. By the 50th or 100th word, more distinctive vocabulary begins to appear: character names like stark, dane, martin, moreau, and martians, alongside genre words such as robot, space, ship, planet, and war. This is the first sign that style and content are not as cleanly separated as the method assumes. Even in a list of the most frequent words, content starts to bleed in.

## The Bootstrap Consensus Tree: What Holds Across Parameters

The Bootstrap Consensus Tree clustering across MFW settings from 100 to 500 and reports only what holds consistently. This makes it a more reliable Stylo result, not a snapshot of one parameter choice but a consensus across many.

![Figure 1: Bootstrap Consensus Tree at 100-500 MFW](/rlacs26-jennet/assets/images/figure1-bct.png) 
*Figure 1: Bootstrap Consensus Tree at 100-500 MFW*

The BCT reveals two kinds of authors: those whose style is consistent enough for the algorithm to identify reliably, and those whose internal variety defeats it.

Dick and Norton fall into the first group. All three of Dick's texts cluster together on a tight branch regardless of parameters. Norton's three texts do the same. Their stylistic patterns are stable enough that the algorithm has no difficulty recognizing them. This is Stylo working as intended.

Kuttner falls into the second group. His three texts scatter across the dendrogram. *The Ego Machine* clusters near Brackett's *The Blue Behemoth*, both being lighter and more comedic than the rest of their authors' work. *The Black Kiss*, co-authored with Robert Bloch, drifts elsewhere. Kuttner's range was simply too wide for a single stylistic identity to emerge. Interestingly, the algorithm here is trying to detect something real about the difference between Kuttner's horror, comedy, and adventure registers.

Brackett is a partial case. Her two Eric John Stark stories, *Enchantress of Venus* and *Black Amazon of Mars*, cluster reliably together. But *The Blue Behemoth* drifts away. This is the first moment where the style and content separation starts to break down. The Stark stories share not just an author but a protagonist, a world, and a moral universe. Their clustering may reflect not Brackett's style in the abstract but the specific voice she adopted for that series.

Wells produces the clearest result of all. *The Salvaging of Civilization* is always isolated, and always far from his two fiction texts. Non-fiction prose has a fundamentally different function-word profile from narrative fiction, dominated by words like world, are, most, much, this, has, more, than rather than narrative action words. No amount of shared authorship bridges that gap. The method is measuring something real, but what it measures is genre as much as authorship.

## The PCA Loadings

![Figure 2: Principal Component Analysis at 100 MFW](/rlacs26-jennet/assets/images/figure2-pca.png)
*Figure 2: Principal Component Analysis at 100 MFW*

At 100 MFW, the first principal component, accounting for 21.3% of variance, separates action-driven narrative prose from argumentative, essayistic writing. Words like eyes, away, back, came, her, him, was, and had pulled in one direction. Words like world, are, most, much, this, has, more, and then pull in the other. This is a distinction between two fundamentally different modes of writing: narrative versus argument, fiction versus non-fiction, showing versus telling.

As MFW increases from 100 to 1000, something important happens. The central cluster of 1950s pulp science fiction texts compresses together. The individual voices of Brackett, Kuttner, Norton, Dick, and Bradley begin to blur into a shared genre register. This is not a failure of the method. It is a finding. The pulp science fiction writers of the 1950s converged on a common stylistic baseline, shaped by the same editorial demands, the same readership, and the same cultural moment. Stylo makes that convergence visible.

## The TF-IDF Visualizations

If Stylo reveals the grammar of style, TF-IDF reveals the vocabulary of content. Where Stylo asks "how does this author write?", TF-IDF asks "what does this text talk about?". Comparing the two PCA plots (at 100 and 3000 MFW) against what Stylo found makes the differences between these methods more visible.

![Figure 3: TF-IDF at 100 MFW](/rlacs26-jennet/assets/images/figure3-tfidf-100.png)
*Figure 3: TF-IDF at 100 MFW*

Looking at the two most contrasting parameter settings (100 and 3000 MFW) reveals what happens as more vocabulary is included in the analysis. At 100 MFW, texts are spread across a wider horizontal range, with several notable outliers pulling in different directions. By 3000 MFW, the entire plot has shifted to the right and the central cluster of fiction texts had compressed noticeably together. This mirrors what Stylo showed at higher MFW settings; as words are included, the shared genre baseline of 1950s science fiction begins to dominate, pulling texts toward each other and smoothing over individual differences.

There are two texts that remain at the extremes across both settings: *Jackie Sees a Star* which sits alone in the upper-left corner of the plot, and *The Salvaging of Civilization* which sits alone in upper-right. These two texts are maximally distant from each other and from everyone else. Wells's nonfiction isolation mirrors the Stylo result; its vocabulary of civilization, education, and governance has no equivalent anywhere in the fiction corpus. But Bradley's short story is a different kind of outlier. *Jackie Sees a Star* is the only text in the corpus narrated primarily from a child's perspective, and its distinctive vocabulary is simpler, and closer to everyday speech, which pushes the text far from the pulp adventure baseline that most other texts share. This is something Stylo partially captured (it was the most distant of Bradley's three texts in the cluster analysis) but TF-IDF makes it far more visible.

![Figure 4: TF-IDF PCA at 3000 MFW](/rlacs26-jennet/assets/images/figure4-tfidf-3000.png)
*Figure 4: TF-IDF PCA at 3000 MFW*

*The Ego Machine* is another persistent outlier, sitting alone on the left side of the plot at both settings. Its Hollywood setting gives it a content profile that no other text in the corpus shares. This is actually a case where TF-IDF is less informative than Stylo. The stylometric analysis connected *The Ego Machine* to *The Blue Behemoth* through their shared comedic tone, which is a genuinely interesting observation. TF-IDF, by contrast, simply isolates it as topically unusual without revealing what it shares with anything else.

The most meaningful shift between 100 and 3000 MFW happens in the central cluster. At 100 MFW, there is still visible separation between texts. By 3000 MFW, these distinctions have blurred as the cluster compressed to the right. This is the shared genre vocabulary taking over. Words like ship, space, planet, and war appear across almost all these texts, and as they accumulate they pull everything toward the same center.

The most interesting disagreement between the two methods concerns Brackett and Bradley. Stylo kept them in separate authorial clusters, correctly identifying that their stylistic fingerprints differ. In the TF-IDF plots however, Brackett's *Enchantress of Venus* and *Black Amazon of Mars* sit close to Bradley's *Falcons of Narabedla*. Both authors are writing about displaced protagonists and alien civilizations, and TF-IDF picks up on their shared content vocabulary where Stylo saw only different authors. Neither result is wrong. They are measuring different things, and the gap between them, we think, is where the most interesting questions live.

## Comparing Two Methods: Where the Separation Breaks Down

These disagreements matter precisely because of what Underwood identifies as one of distant reading's core risks that scholars might forget that "the point of the enterprise is, after all, illuminating the enjoyment of poems, plays, and novels". The disagreements between Stylo and TF-IDF are not problems to resolve by running more parameters. They are invitations to read.

The cases where style and content refuse to separate are the most literarily revealing. Brackett's Stark stories cluster together in both methods, but not simply because of Brackett's style in the abstract. The style cannot be separated from the content because the content created the style: Stark required a harder, darker, more physical voice than *The Blue Behemoth*, and Brackett gave it to him. Style followed content here, not the other way around.

Wells's *Salvaging of Civilization* makes the same point differently. Its argumentative prose style is the content. Wells is not writing about civilization in a neutral register. He is making an argument, and the argument shapes every grammatical choice. The method that claims to measure only style and the method that claims to measure only content both detect the same thing, because it cannot be split.

*Jackie Sees a Star*, always isolated, always at the edge of both plots, presents the most poignant case. Its first-person child narrator, its brief length, and its unique scenario of psychic contact with a dying star are not separately "style" and "content". A child narrator is a stylistic choice that is simultaneously a content choice. The intimacy of the voice and the wonder of the subject are the same literary decision viewed from two angles.

## A Note on Gender

One question the assignment invites is whether gender produces stable clustering patterns. The answer, across both methods, is that it does not. Norton, Bradley, and Brackett do not cluster together in either Stylo or TF-IDF. Genre conventions and individual stylistic habits dominate over gender as a signal. This is historically striking: Andre Norton published under a male pen name fearing that her gender would cost her readers. Marion Zimmer Bradley wrote explicitly about gender and social hierarchy. Yet the computational analysis cannot see gender as a primary signal. It sees style and content.

## Conclusion: What the Disagreements Teach Us

Working with these methods also raises what Underwood calls the third risk of distant reading: the challenge of new literacies. Tools like Stylo and TF-IDF PCA demand a kind of technical fluency that feels quite different from the skills humanists are trained in. Learning to interpret dendrograms, understand statistical measures, and make sense of visualizations is not trivial, and it sits uncomfortably alongside more familiar practices like close reading, historical context, and genre knowledge. But this discomfort is productive. Distant reading does not replace humanistic inquiry. It expands the questions available to it.

Ultimately, we come back to the question we started with: can a computer separate style from content? The answer, we believe, is 'partially'. For Dick, the separation is real and it shows a consistent voice ranging across different Cold War scenarios, all written in the same year. But for Brackett's Stark stories, Wells's political writing, and Bradley's child narrator, it breaks down. In those cases, style and content are too intertwined to pull apart; they are really just two ways of looking at the same text. The scatter plots and dendrograms point toward the interesting questions we can ask, and in a corpus as varied and historically rich as this one, six authors writing across seven decades of a genre shaped by war, technology, and the anxieties of a post-WW2 world, there are more than enough interesting questions to pursue.

## References

- Underwood, Ted. *Distant Horizons: Digital Evidence and Literary Change.* University of Chicago Press, 2019.
- Brackett, Leigh. *The Blue Behemoth* (1943); *Enchantress of Venus* (1949); *Black Amazon of Mars* (1951). Project Gutenberg.
- Dick, Philip K. *Second Variety* (1953); *The Defenders* (1953); *The Variable Man* (1953). Project Gutenberg.
- Kuttner, Henry (& Robert Bloch). *The Black Kiss* (1937); *The Ego Machine* (1952); *Thunder in the Void* (1942). Project Gutenberg.
- Norton, Andre. *Plague Ship* (1956); *Star Hunter* (1961); *Voodoo Planet* (1959). Project Gutenberg.
- Wells, H.G. *The Island of Doctor Moreau* (1896); *The Salvaging of Civilization* (1921); *The War of the Worlds* (1898). Project Gutenberg.
- Bradley, Marion Zimmer. *Falcons of Narabedla* (1957); *Jackie Sees a Star* (1954); *The Door Through Space* (1961). Project Gutenberg.

## Acknowledgements

Jennet: It was very nice working with Dalila. I truly appreciate her dedication and her thoughtful contribution to the assignment. She brought a lot of thoughtfulness and care to the research, and her contributions to the author profiles and the TF-IDF analysis made the whole thing come together.

Dalila: I would like to thank Jennet for her dedication and active involvement in completing this assignment. I appreciate the time and effort she put into strengthening the Stylo analysis and improving the structure of our essay. I think working together allowed us to produce a more thoughtful work by contributing valuable ideas and challenging each other's thinking.

Ready for Grading 🙌