---
title: "Preventing rumor spread with deep learning"
excerpt: "Daejin Choi, Hyuncheol Oh, Selin Chun, Taekyoung Kwon, and Jinyoung Han"
collection: datasets
---

Daejin Choi, Hyuncheol Oh, Selin Chun, Taekyoung Kwon, and Jinyoung Han,
accepted to Expert Systems With Applications

-----
## Citation
[BibTex]({{ base_path }}/files/eswa-factcheckers/22eswa_choi.bib)

## Abstract
The spreading of false rumors through online media is a serious social problem.
The current process of fact-checking mostly relies on the responses of crowds or
journalists to perform investigations, which can be performed after a rumor has
widely spread. This study proposes a bi-directional encoder representations from
transformers (BERT)-based model that only takes a claim sentence of a rumor,
which can be used to identify false rumors before it goes viral. By evaluating
the proposed model with the rumor dataset that is collected from Snopes and
Politifact, this study demonstrates the effectiveness of the model that can
accurately identify false rumors with only a given claim text. We also reveal
that the performance of the models that are trained from the rumors in specific
categories (e.g., business, politics) can be improved by transfer learning.
Transfer learning uses the model parameters that are trained from a category as
an initial state of the model for another category. Our analysis shows that a
pre-trained model from a category that deals with a broad range of topics (e.g.,
fauxtography) is a useful source that can be transferred to other categories
(e.g., entertainment). We believe that the proposed model can help mitigate
potential social risks such as social turmoil or monetary chaos that are caused
by false rumors, as the rumors can be detected before they go viral.

-----
## Models

The goal of the proposed model is to determine whether a given claim is true or
false. To this end, we propose a deep learning-based model that consists of two
steps: (i) claim embedding and (ii) fact-checking, as illustrated the Figure
below.

<br/><img src='/files/eswa-factcheckers/models.png'>"

For claim embedding, we first investigate and evaluate the diverse models that
extract the linguistic features and it is decided to use the BERT pre-trained
model since it can extract the comprehensive features from the given
text. The extracted claim feature
vectors from the claim embedding step are then fed into multiple layers at the
fact-checking phase for the final true/false decisions. Formally, the predicted
value y<sub>r</sub> of the given rumor claim r is computed as follows.

y<sub>r</sub> = &phi;(X;&theta;)

where X and &theta; are the set of rumor claims and the set of parameters
that are to be trained, respectively.

The implementation codes are available with sharing agreement. Please contact to
Daejin Choi (djchoi@inu.ac.kr).


-----
## Dataset


We collected rumors and their corresponding claims from two popular
fact-checking sites, [*Snopes*](http://snopes.com) and
[*Politifact*](http://politifact.com). In *Snopes*, an editor chooses a claim and
concludes its veracity (e.g.,true, false, or a mixture) based on a manual
inspection. The determined claims are then classified into one of 57 categories
including politics, health, and science. We collected 7,403 claims whose
veracities were either true or false, as reported in *Snopes* from 2012
to 2017. The proportions of true and false claims are 22% and 78%,
respectively, in our dataset. We also noted a category for individual claims in
our dataset. Here, we combined two categories --- Politics and
Politicians, which was denoted as ``Politics'' since they share similar topics.

We also collected a dataset from another fact-checking service,
*Politifact*. A major difference between *Snopes* and
*Politifact* is that *Snopes* deals with a broad range of rumor
topics such as fauxtography, entertainment, and business, whereas
*Politifact* focuses on political rumors. The collected dataset contains
864 claims that were reported in *Politifact* from 2007 to 2017. The
number of true and false claims was 2,227 and 2,847, respectively.

* [Rumors in Snopes]({{ base_path }}/files/eswa-factcheckers/snopes.tsv) (898K)
  * The files are written in TSV forms.
  * Dataset Schema is written in the first row of the file.

* [Rumors in Polififact]({{ base_path }}/files/eswa-factcheckers/politifact.tsv) (462K)
  * The files are written in TSV forms.
  * Dataset Schema is written in the first row of the file.


-----
## Contact
Daejin Choi (djchoi@inu.ac.kr)
Jinyoung Han (jinyounghan@skku.edu)

