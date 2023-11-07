---
title: "[Contest] Protein Function Prediction"
excerpt: "A Kaggle challenge about predicting the function of proteins from their sequences and 3D structure."
collection: projects
teaser: "/images/projects/protein_function_prediction/proteins.jpg"
teaser_type: "image"
teaser_video_hover: false
dates: "Dec. 2022 - Jan. 2023"
sorting_key: 202301
date_published: 2023-01-31
date_modified: 2023-01-31
---

<div style="text-align: right"> <a href="https://github.com/ErwanFagnou/Protein_function_prediction" target="_blank"><i class="fab fa-fw fa-github" aria-hidden="true" style="color: #000"></i> Our code</a> </div>

<div style="text-align: right"> <a href="https://github.com/ErwanFagnou/Protein_function_prediction" target="_blank"><i class="fab fa-fw fa-kaggle" aria-hidden="true" style="color: #1fb7f6"></i> Kaggle contest</a> </div>

<ins>Ranking:</ins> **1st place** (out of 37 teams)

<ins>Teammate:</ins> Denis Duval

## The contest
This Kaggle contest was hosted by the teachers of the "[ALTEGRAD](https://www.master-mva.com/cours/cat-deep-learning/)" (advanced learning for text and graph data) course of the MVA Master. The challenge involved classifying proteins into 18 different functions, using both the sequence of amino acids and a graph representation of their 3D structure. Among the 6111 proteins of the dataset, 4888 are labeled and hence constitute the training data while the unlabeled remaining part constitute the test data on which we have to make predictions. The latter is the data our models were evaluated and ranked in the challenge's leaderboard.

For each of these proteins we were given the following information:

- The sequence of amino acids
- The features of the amino acids (there are 86 in total): 3D position, type (as a one hot vector), hydrogen bond acceptor and donor status, and more features derived from the EXPASY protein scale
- The edges of the protein graphs
- The features of the edges of the graphs: the distance between the two connected nodes, and the type of edge (peptide bond, hydrogen bond, k-NN edge, or distance-based edge)

## Our solution

The difficulty of the task was that the dataset was very small, leading to a lot of overfitting.

Our first approach was to use graph convolutional networks (GCN), to take advantage of the graph structure of the protein. The performance was however quite poor. We then tried to pretrain language models on the sequences to generate better features, which proved to be useful. However, the game changer was the pretrained model ESM-2 <a href="#lin22"> [Lin 2022]</a>, which is a very large RoBERTa-like model trained on masked language modeling. Our final model uses features extracted from the hidden layers of the pretrained ESM-2 model with 3 billion parameters, while the classification head is a multihead attention (to aggregate the features in a fixed-size vector) followed by an MLP.

A few additional techniques were used to improve the validation loss of the model, like dropout, label smoothing, and ensemble methods (averaging the predictions of dozens of models).

For more details about our attempts and the final results, see our full [report](https://github.com/ErwanFagnou/Protein_function_prediction/blob/master/report.pdf).

## References

<div style="text-indent: -3ch; margin-left: 3ch">
<p><a id="lin22"></a>[1] Zeming Lin, Halil Akin, Roshan Rao, Brian Hie, Zhongkai Zhu, Wenting Lu, Allan dos Santos Costa, Maryam Fazel-Zarandi, Tom Sercu, Sal Candido, Alexander Rives. 2022. <i>Language models of protein sequences at the scale of evolution enable accurate structure prediction</i>. bioRxiv. DOI: <a href="https://doi.org/10.1101/2022.07.20.500902">https://doi.org/10.1101/2022.07.20.500902</a></p>
</div>
