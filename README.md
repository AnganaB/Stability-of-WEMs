# Stability-of-WEMs

A representation learning method is considered stable if it consistently generates similar representation of the given data across multiple runs. Word Embedding Methods (WEMs) are a class of representation learning methods that generate dense vector representation for each word in the given text data. The central idea of this paper is to explore the stability measurement of WEMs using intrinsic evaluation based on word similarity. We experiment with three popular WEMs: Word2Vec, GloVe, and fastText. For stability measurement, we investigate the effect of five parameters involved in training these models. We perform experiments using four real-world datasets from different domains: Wikipedia, News, Song lyrics, and European parliament proceedings. We also observe the effect of WEM stability on three downstream tasks: Clustering, POS tagging, and Fairness evaluation. Our experiments indicate that amongst the three WEMs, fastText is the most stable, followed by GloVe and Word2Vec.

We may update this README in future. Please get an updated copy of the same using the following link.
For a clearer and updated view of this README file go to https://github.com/AnganaB/Stability-of-WEMs

# Requirements

`Python 3.5 or higher`
`Jupyter Notebook`

# Libraries required

`Gensim`
`NLTK`
`keras`
`Pandas`
`Numpy`
`Sklearn`
`Seaborn`
`Matplotlib`
`Pickle`
`Scipy`

# Datasets

We performed experiments using four publicly available real-world datasets. These datasets represent diverse styles of natural language usage. Online collaborative writing style is covered in our [Wikipedia (Sample) dataset](https://dumps.wikimedia.org/enwiki/). It contains a subset of English Wikipedia articles from October 2017 Wikipedia dump. News articles are covered in the [NewsCrawl(2007) dataset](http://www.statmt.org/wmt16/translation-task.html). We have used the News Crawl articles for the year 2007. The Lyrics dataset represents creative writing style and include datasets from [[1]](#1) and [[2]](#2). It contains over 400K English songs of around 7.2K artists from the period 1938 to 2016. Formal parliamentary communication is covered in our [Europarl (Sample) dataset](http://www.statmt.org/wmt16/translation-task.html). It includes the English version of the proceedings of Bulgarian, Czech, Slovak, Slovene, Romanian and Polish parliaments. Our Lyrics dataset had around fifty million tokens. We sampled other datasets to match the size of our Lyrics dataset. We have deliberately chosen these diverse corpora that vary in corpus parameters like size of vocabulary and topics to assess our models with realistic examples. We have pre-processed these corpora by tokenizing sentences and removing non-alphabetic characters and converting all characters to lower cases. We have also removed the stop words by using the stop words corpora of [NLTK](http://www.nltk.org/). We have also considered a minimum word occurrence of five and removed all words that appear less than five times in a corpus.

# Instructions

**Effect of hyperparameter on stability of WEMs**

_Frequency_Stability.ipynb_: This file contains the code to analyze the effect of frequency on stability of WEMs.

_Dimension_Stability.ipynb_: This file contains the code to analyze the effect of dimension on stability of WEMs.

_Context Window Size_Training Epochs_Stability.ipynb_: This file contains the code to analyze the effect of context window size and number of training epochs on stability of WEMs.

**Effect of stability on downstream tasks**

_SNN_DBSCAN.ipynb_: This contains the code to analyze the effect of WEM stability on Word Clustering. We have chosen Shared Nearest Neighbor Density Based Clustering (SNND) algorithm since it is a well known robust clustering algorithm for high-dimensional data and it clusters data based on the shared top K-nearest neighbors (KNN). This intuition of clustering correlates with our stability measurement.

_POS_Stability.ipynb_: This contains the code to analyze the effect of WEM stability on Parts of Speech tagging. For experimentation, we combine a number of corpora using the NLTK library. These include treebank (consists of 5\% of Penn Treebank), Brown, CONLL (Conference on Computational Natural Language Learning) 2000, 2002 and 2007. The total corpora size consists of 2.5 million tokens. We chose a simple a bidirectional LSTM model like the previous stability studies [[3]](#3).

_WEAT_Test.ipynb_: This contains the code to analyze the effect of WEM stability on Fairness Evaluation. Implicit Association Test (IAT)[[4]](#4) is designed to measure biases with human subjects. The Word Embedding Association Test (WEAT) is proposed by Caliskanet al.[[5]](#5). The WEAT test is an improvisation over the IAT test such that biases can be measured directly from the word embeddings in the absence of humans subjects. This test computes the similarity between words using cosine similarity. The task here involves measuring biases in the the given set of word embeddings using the WEAT test.

**Experiment-Images**

This folder contains the experiment images of all the tasks performed. 

# Conclusion

In this work, we found that WEMs are not completely stable. Out of three three WEMs studied, fastText is the most stable and Word2Vec is the least stable method. We also observed the effect of WEMs instability on three downstream tasks. While training word embeddings, one needs to carefully analyze the effect of various design choices on the stability of word embeddings. In future, we need a deeper analysis and theoretical explanation for various stability trends observed in this paper.


# References
<a id="1">[1]</a> 
Barman, M. P., Awekar, A., & Kothari, S. (2019, July). Decoding the style and bias of song lyrics. In Proceedings of the 42nd International ACM SIGIR Conference on Research and Development in Information Retrieval (pp. 1165-1168).

<a id="2">[2]</a>
Fell, M., & Sporleder, C. (2014, August). Lyrics-based analysis and classification of music. In Proceedings of COLING 2014, the 25th international conference on computational linguistics: Technical papers (pp. 620-631).

<a id="3">[3]</a>
Wendlandt, L., Kummerfeld, J. K., & Mihalcea, R. (2018). Factors influencing the surprising instability of word embeddings. arXiv preprint arXiv:1804.09692.

<a id="4">[4]</a>
Greenwald, A. G., McGhee, D. E., & Schwartz, J. L. (1998). Measuring individual differences in implicit cognition: the implicit association test. Journal of personality and social psychology, 74(6), 1464.

<a id="5">[5]</a>
Caliskan, A., Bryson, J. J., & Narayanan, A. (2017). Semantics derived automatically from language corpora contain human-like biases. Science, 356(6334), 183-186.
