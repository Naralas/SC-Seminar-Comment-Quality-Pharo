Herbelin Ludovic<br>
Seminar Software Composition 2020<br>

Software Comments Quality Metrics
===

## Introduction

This document lists some of the software comment quality metrics, the goals and how effective they are based on a few papers. [refs]

## Quality Analysis of Source Code Comments

Based on [Quality Analysis of Source Code Comments] the quality of the source code comments has 4 main criterias :
- **Coherence :** How code and comments relate, member comments up-to-date with the method name. Comments should provide additional information than method name.
- **Usefulness :** Comments should be perceived as helpful by the readers. If the code is not harder to read without the comment, it is useless.
- **Completeness :** Comment should appear all the time at certain positions, E.G. copyright, header for class, method and field of an API.
- **Consistency :** E.G. comments should be written in the same language, same coypright format, etc.

**2 metrics defined for coherence**

Using the distance between words in the comment and in the method, compare if the comment is too similar (no use) or too dissimilar (method should be renamed) to the method name
- Levenshtein distance : Words are similar if $d(w1, w1) < 2$
    - Then compute the $c_{coeff}$ for the comment $c_{coeff} = \frac{N_{similar}}{N_{words}}$
    - Experimentally determined $c_{coeff} = 0$ -> not enough coherence, add info the emphasize relation with method identifier
    - Experimentally determined $c_{coeff} > 0.5$ -> too trivial, does not contain additional info

Comment length : Experimentally (after normalization) : words with 1-2 words can be deleted. Comments with at least 30 words are too complex for the length to be used. 


## Automatic Quality Assessment of Source Code Comments: The JavadocMiner

2 categories of metrics : Natural Language Quality and Code/Comment consistency

### NL quality

- **Token, Noun, Verb count heuristics** : detect well formed sentences
- **Words Per Javadoc Comment (WPJC)** : detect members, classes, etc. that could be under documented -> comment length of first paper
- **Abbreviation Count Heuristic (ABB)** : detect number of abreviations (to avoid)
- **Readability heuristics** : Fog index, Flesch Reading Ease Level, Flesch-Kincaid Grade Level Score -> in the paper studies infeasible for source code comments ?


### Code / Comment Consistency

- **Documentable Item Ratio Heuristic (DIR)** : Must document all aspects of method @throws, @return, @parameter, etc.
- **Any Javadoc Comment heuristic (ANYJ)** : Ratio of nb of identifiers (?) to total number of identifiers
- **Sync Heuristics** : Return types, Parameters, Exceptions must be valid (up-to-date), IE having correct name of the type, parameters names and exceptions names
    - **RSYNC** : Return type
    - **PSYNC** : Parameters
    - **ESYNC** : Exceptions