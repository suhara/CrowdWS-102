# CrowdWS-102

![Summary](/images/summary.png)

## What is CrowdWS-102?

CrowdWS-102 is a crowdsourced collection of the similarity and relatedness scores of word pairs. Word similarity datasets, such as WordSimilarity-353 (WS-353), are commonly used for evaluating NLP techniques, such as word-embedding methods. Existing word similarity datasets have been created based on averaging the scores reported by several annotators to create a gold standard.

The aim of this dataset is to collect word similarity scores from a large number of annotators to understand the following three hypotheses.

- (H1) The framing effect influences similarity ratings by human assessors.
- (H2) The distribution of similarity rating does not follow the Gaussian distribution.
- (H3) Semantic relatedness is not symmetric. The relatedness between words (e.g., tiger and cat) yields different similarity ratings in the opposite word order.


## Data Collection

The 102 word pairs in the dataset were randomly chosen from [WS-353](http://alfonseca.org/eng/research/wordsim353.html), a well-known word similarity dataset. Then, we published crowdsourcing tasks at Amazon Mechanical Turk to collect 0-10 scale word similarity annotations from 50 distinct annotators for each word pair. We also used the same instructions as WordSim353.

Here is a screenshot of an example task.

![Screenshot](/images/screenshot.png)

To evaluate the symmetricity of the word similarity of a word pair, we tested the four conditions (sim, inverted-sim, dissim, inverted-dissim) for the 102 selected pairs. For instance, the questions used to determine the similarity score between word **X** and **Y** were as below:

- **Similarity (sim)**: "How is X similar to Y?"
- **Inverted similarity (inv-sim)**: "How is Y similar to X?"
- **Dissimilarity (dis)**: "How is X dissimilar to Y?"
- **Inverted dissimilarity (inv-dis)**: "How is Y dissimilar to X?"


## Dataset Description

`crowdws-102.csv` contains all of the dataset’s information. A schema description of the file can be found below.

- **pair (str)**: Word pair
- **word_x (str)**: Word X
- **word_y (str)**: Word Y
- **scores (list)**: List of scores (0-10). `10` (`0`) means closely related, and `0` (`10`) means very unrelated for `qtype="sim" ("dis")` or `qtype="inv-sim" ("inv-dis")`. Note that the scores have opposite meanings for "similarity annotation" and "dissimilarity annotation"
- **qtype (str)**: Question type {"sim", "dis", "inv-sim", "inv-dis"}


Here is example Python code that shows the first five lines of the dataset.

```
>>> import pandas as pd
>>> df = pd.read_csv("")
                  pair     word_x      word_y  \
0      word-similarity       word  similarity
1         tiger-jaguar      tiger      jaguar
2  territory-kilometer  territory   kilometer
3          stock-phone      stock       phone
4           start-year      start        year

                                              scores qtype
0  [1.0, 1.0, 5.0, 5.0, 6.8, 0.0, 2.0, 4.0, 4.0, ...   sim
1  [9.0, 10.0, 1.0, 7.0, 7.5, 8.0, 9.0, 7.0, 3.0,...   sim
2  [3.0, 6.0, 4.0, 5.0, 5.9, 5.0, 5.0, 0.0, 6.0, ...   sim
3  [0.0, 0.0, 3.0, 4.0, 7.9, 0.0, 3.0, 0.0, 4.0, ...   sim
4  [2.0, 3.0, 8.0, 4.0, 4.8, 2.0, 2.0, 0.0, 4.0, ...   sim
```

## References

Please cite the following publication if you use the dataset in your work.

```
Malay Bhattacharyya, Yoshihiko Suhara, Md Mustafizur Rahman, Markus Krause,
``Possible Confounds in Word-based Semantic Similarity Test Data'',
In Proc. ACM Conference on Computer Supported Cooperative Work and
Social Computing (CSCW '17), pp. 147-150, 2017.

Available: http://dx.doi.org/10.1145/3022198.3026357
```

This is a blog article that summarizes our project at CrowdCamp 2016.

- [CrowdCamp Report: Finding Word Similarity with a Human Touch - Follow the Crowd](https://humancomputation.com/blog/?p=9492)


## License

CrowdWS-102 is made available under the Open Data Commons Attribution License: http://opendatacommons.org/licenses/by/1.0/.


## Acknowledgement

This work was sponsored by the CrowdCamp workshop held at AAAI HCOMP 2016.