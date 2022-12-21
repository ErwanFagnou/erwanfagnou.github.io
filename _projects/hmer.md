---
title: "Handwritten Mathematical Expression Recognition"
excerpt: "Designing a deep learning model based on the transformer architecture to read the image of a mathematical expression and convert it to LateX."
collection: projects
teaser: "/images/projects/hmer/teaser.png"
teaser_type: "image"
teaser_video_hover: false
dates: "Nov. 2022 - Ongoing"
---

## Context

I chose to do this project as the final project of the "[Deep Learning](https://www.master-mva.com/cours/cat-deep-learning/)" course that I took during the first semester of my third year (2022-2023).

I have been interested for some time in the task of converting the image of a handwritten mathematical expression to either LaTeX or similar formats. I only recently discovered that it is actually a real field of research. HMER (Handwritten Mathematical Expression Recognition) can be viewed as a variation of OCR (Optical Character recognition). The difference is that while OCR algorithms have to deal with sentences of words (which have a relatively simple structure), mathematical expressions have complex spatial and syntactic structures. Moreover, some symbols may have very different scales (e. g. a square root around a big expression). The difficulty of HMER is mostly because of the syntactic relationships complexity rather than symbol recognition.

What makes this task interesting is that current state-of-the-art algorithms are far below human performance: SAN <a href="#yuan22">[Yuan 2022]</a>, a recently published model, makes a mistake in at least 37% of the test images for the CROHME datasets of 2014, 2015 and 2019.

## Approach

Although I don’t think I will be able to best the state of the art models, I think it would be very interesting to design my own model architecture based on my lectures and readings. I already started with a vision transformer, but I know there are better architectures for this task.

The project is ongoing, so I will update this page as I make progress.

## References

<div style="text-indent: -3ch; margin-left: 3ch">
<p><a id="yuan22"></a>[1] Ye Yuan, Xiao Liu, Wondimu Dikubab, Hui Liu, Zhilong Ji, Zhongqin Wu, and Xiang Bai. 2022. <i>Syntax-Aware Network for Handwritten Mathematical Expression Recognition</i>. arXiv. DOI:<a href="https://doi.org/10.48550/ARXIV.2203.01601">https://doi.org/10.48550/ARXIV.2203.01601</a></p>
</div>
