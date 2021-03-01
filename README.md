# language_on_a_holiday


### Description

Unsupervised machine learning, applying NLP techniques to philosophical texts. This project investigates the possibilities of unspupervised machine learning models for Natural Language Processing, to discover algorithmic approaches to distinguish philosophical writing style and locating passages of text having certain qualities that might be appropriate for recommendor systems.

The presentation can be viewed in

`langauge_on_a_holiday.pptx`

<https://github.com/jmailman/language_on_a_holiday/blob/master/langauge_on_a_holiday.pptx>

`langauge_on_a_holiday.pdf`

<https://github.com/jmailman/language_on_a_holiday/blob/master/langauge_on_a_holiday.pdf>


### Features

* Word counts and resulting word distributions

### Goals
* Distinguish diverse prose styles of philosophical texts

### Applications
* Recommender systems
* Automated text-to-speech (and song)
* Education

### Data Used

* Full-text books downloaded from [Project Gutenberg](www.gutenberg.org) and [Internet Archive](www.archive.org)
  - David **Hume**'s _Enquiry Concerning Human Understanding_ (from Gutenberg)
  - William **James**'s _Pluralist Universe_ (from Gutenberg)
  - Alfred North **Whitehead** _Process and Reality_ (from archive.org)

### Analysis models
* **NMF (Non-negative Matrix Factorization)** for topic modeling
  - trained on entire corpus and fit to each book
  - trained on sections of books and fit to each paragraph within the section
* **_Alpha scaled TF-IDF_**, a modified version of TF-IDF which restores some of the emphasis on extremely rare words that the log transformation of IDF in the conventional TF-IDF dampens.

### Visualizations

* _Wordcloud_
 - for each book
* Confusion matrix
  - to observe topic distribution in entire books
* Line graphs
  - to trace paragraph-to-paragraph topic continuity
* Oblong color matrix
  - adapted to depict chronology of paragraphs
* SpaCy _Scattertext_
  - compare word frequency in Whitehead vs. in Hume and James
*  Chronological (orthochronic) graphs of _alpha scaled TF-IDF_
 - for each book: scatterplot _as-TF-IDF_ of all words
    - helps isolate the rarest prevalent words
 - for Whitehead _Process and Reality_
   - 1000-word moving-window line graph of _as-TF-IDF_
   - Scatterplot (with _lowess_ curve) of _as-TF-IDF_ for each paragraph
   - Line graph (with _B-spline_ smoother) of word-by-word _as-TF-IDF_ for a single sentence
   - Animated B-spline line graph of word-by-word _as-TF-IDF_ for a long excerpt

### Results
1. Topic modeling of paragraphs reveals that Hume begins with more topical continuity from paragraph to the next, as compared to Whitehead's more fragmentary shifting between topics.
 - Sequences of paragraphs with topical continuity could be _recommended_ on that basis

2. Topic modeling reveals that a Whitehead paragraph with the highest topic concentration is comparitively self-contained (self-explantory)
 - A paragraph that is relatively self-explanatory could be _recommended_ on that basis

3. _Alpha scaled TF-IDF_ reveals:

  a. The overall amount of rare words (verbal semantic eccentricity or idiosyncrasy) is higher across Whitehead's _Process and Reality_ as compared to Hume's an James's books
    - The degree of verbal-semantic eccentricity or idiosyncrasy can serve as a feature in a recommender system

  b. How to locate specific paragraphs in Whitehead's _Process and Reality_ that are verbally most idiosyncratic
    - Depending on the use-case, the most verbally idiosyncratic paragraphs (or songs) could be recommended on that basis

  c. The fluctuation of verbal idiosyncrasy from one word to the next within Whitehead's sentences.  
    - The verbal idiosyncrasy score (_alpha scaled TF-IDF_) of individual words within a sentence could serve as a useful parameter to inform inflection in text-to-speach or algorithmic song composition applications.

  ## NOTE: code files 2b and 3 still require a significant amount of cleaning up and markdown annotation
