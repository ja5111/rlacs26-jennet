---
title: "Assignment 2"
date: 2026-04-30
categories: blog
---

## Can a Computer Separate Style from Content?

*Computational Text Analysis by Dalila and Jennet*

Literature does more than carry information. It creates patterns, rhythms, and textures that shape how the reader moves through a text. With the help of digital tools, in this essay we tried to examine whether those patterns can be meaningfully distinguished from the content they carry.

This work applies two computational methods to 18 science fiction texts from Project Gutenberg, written by six authors: Leigh Brackett, Philip K. Dick, Henry Kuttner, Andre Norton, H.G. Wells, and Marion Zimmer Bradley. Stylo analyzes style through the most frequent words, the grammatical scaffolding that tends to remain consistent across an author's work regardless of subject. TF-IDF analyzes content through the most distinctive words, the vocabulary that sets each text apart from others. Running both methods on the same corpus gives us a good insight of different pictures of the same texts, and comparing those pictures is where the interesting questions begin to arise.

Our guiding question in this essay is whether style and content reliably pull apart or whether they collapse back into each other. Here, we tried to use the agreement and disagreement between the two methods to explore what each one sees and what each one misses.

## What Stylo Sees: The Grammar of Style

Stylo works by counting the most frequent words in each text and measuring stylistic distance between them. The top words (the, and, of, a, to, i, in, he, was, it, that, his, had, with, on) in the generated wordlist are function words and the grammatical skeleton of English prose. Writers cannot easily control how they use them, even when they are carefully shaping their content. This is precisely what makes them useful for authorship attribution.

But the wordlist does not stay at function words. By the 50th or 100th word, more distinctive vocabulary begins to appear: character names like stark, dane, martin, moreau, and martians, alongside genre words such as robot, space, ship, planet, and war. This is the first sign that style and content are not as cleanly separated as the method assumes. Even in a list of the most frequent words, content starts to bleed in.

## The Bootstrap Consensus Tree

The Bootstrap Consensus Tree clusters across MFW settings from 100 to 500 and reports only what holds consistently. This makes it a more reliable Stylo result, not a snapshot of one parameter choice but a consensus across many.

The BCT reveals two kinds of authors: those whose style is consistent enough for the algorithm to identify reliably, and those whose internal variety defeats it.

Dick and Norton fall into the first group. All three of Dick's texts cluster together on a tight branch regardless of parameters. Norton's three texts do the same. Their stylistic patterns are stable enough that the algorithm has no difficulty recognizing them.

Kuttner falls into the second group. His three texts scatter across the dendrogram. The Ego Machine clusters near Brackett's The Blue Behemoth, both being lighter and more comedic than the rest of their authors' work. Kuttner's range was simply too wide for a single stylistic identity to emerge.

Wells produces the clearest result of all. The Salvaging of Civilization is always isolated, and always far from his two fiction texts. Non-fiction prose has a fundamentally different function-word profile from narrative fiction. The method is measuring something real, but what it measures is genre as much as authorship.

## The PCA Loadings

At 100 MFW, the first principal component, accounting for 21.3% of variance, separates action-driven narrative prose from argumentative, essayistic writing. This is a distinction between two fundamentally different modes of writing: narrative versus argument, fiction versus non-fiction, showing versus telling.

As MFW increases from 100 to 1000, the individual voices of Brackett, Kuttner, Norton, Dick, and Bradley begin to blur into a shared genre register. The pulp science fiction writers of the 1950s converged on a common stylistic baseline, shaped by the same editorial demands, the same readership, and the same cultural moment. Stylo makes that convergence visible.

## The TF-IDF Visualizations

If Stylo reveals the grammar of style, TF-IDF reveals the vocabulary of content. Where Stylo asks "how does this author write?", TF-IDF asks "what does this text talk about?".

There are two texts that remain at the extremes across both settings: *Jackie Sees a Star* which sits alone in the upper-left corner of the plot, and *The Salvaging of Civilization* which sits alone in the upper-right. These two texts are maximally distant from each other and from everyone else.

The most meaningful shift between 100 and 3000 MFW happens in the central cluster. By 3000 MFW, distinctions have blurred as the cluster compressed. This is the shared genre vocabulary taking over — words like ship, space, planet, and war appear across almost all these texts, pulling everything toward the same center.

## Comparing Two Methods: Where the Separation Breaks Down

The cases where style and content refuse to separate are the most literarily revealing. Brackett's Stark stories cluster together in both methods, but not simply because of Brackett's style in the abstract. The style cannot be separated from the content because the content created the style.

Wells's *Salvaging of Civilization* makes the same point differently. Its argumentative prose style is the content. The method that claims to measure only style and the method that claims to measure only content both detect the same thing, because it cannot be split.

## A Note on Gender

One question the assignment invites is whether gender produces stable clustering patterns. The answer, across both methods, is that it does not. Norton, Bradley, and Brackett do not cluster together in either Stylo or TF-IDF. Genre conventions and individual stylistic habits dominate over gender as a signal.

## Conclusion

Can a computer separate style from content? The answer, we believe, is partially. For Dick, the separation is real. But for Brackett's Stark stories, Wells's political writing, and Bradley's child narrator, it breaks down. In those cases, style and content are too intertwined to pull apart — they are really just two ways of looking at the same text.

## References

- Underwood, Ted. *Distant Horizons: Digital Evidence and Literary Change.* University of Chicago Press, 2019.
- Brackett, Leigh. The Blue Behemoth (1943); Enchantress of Venus (1949); Black Amazon of Mars (1951). Project Gutenberg.
- Dick, Philip K. Second Variety (1953); The Defenders (1953); The Variable Man (1953). Project Gutenberg.
- Kuttner, Henry. The Black Kiss (1937); The Ego Machine (1952); Thunder in the Void (1942). Project Gutenberg.
- Norton, Andre. Plague Ship (1956); Star Hunter (1961); Voodoo Planet (1959). Project Gutenberg.
- Wells, H.G. The Island of Doctor Moreau (1896); The Salvaging of Civilization (1921); The War of the Worlds (1898). Project Gutenberg.
- Bradley, Marion Zimmer. Falcons of Narabedla (1957); Jackie Sees a Star (1954); The Door Through Space (1961). Project Gutenberg.