---
title: "[Internship at INRIA] Robust PCA for Traffic Prediction"
excerpt: "Design of an algorithm for noise extraction inspired by Robust Principal Component Analysis, during a short research internship at INRIA."
collection: projects
teaser: "/images/projects/robust_pca/rpca.png"
teaser_type: "image"
teaser_video_hover: false
dates: "July - Aug. 2021"
---

During summer 2021, I did an internship at INRIA (French Institute for Research in Computer Science), supervised by [Jean-Marc Lasgouttes](https://who.rocq.inria.fr/Jean-Marc.Lasgouttes/) ([RITS](https://team.inria.fr/rits/) team) and [Cyril Furtlehner](https://www.lri.fr/membre.php?mb=488) ([LRI](https://www.lri.fr/index.php) team). They had developed a machine learning algorithm for traffic prediction <a href="#furtlehner22">[Furtlehner 2022]</a>, and they were wondering whether the algorithm could be improved by preprocessing the data with a robust PCA algorithm. Indeed, the input data is that of hundreds of sensors subject to errors and failures. However, it was not so simple to clean the data, because unpredictable events happen a lot in traffic.

Concretely, I was in charge of programming a Robust PCA (Principal Component Analysis), inspired from <a href="#hu21">[Hu 20221]</a>. In simple terms, PCA is a method to "smooth" data (remove noise caused by randomness and errors, to keep only the important information). Its Robust version is more complete because it allows to control in a much more precise way the way one smoothes the data, and it works with missing data. In particular, it allows to take better advantage of correlations between sensors, between days and between weeks. Another advantage is that by carefully designing regularization methods, I was able to separate the abnormal events into two categories: those observed by all the sensors (traffic jams) and those measured by only one sensor (bugs). Then we had to determine what we wanted to keep: above all, we wanted to remove all unpredictable events. As the Robust PCA, in addition to detecting these anomalies, proposes a correction, there are several ways to use its result for the traffic prediction algorithm.

{% include project_image.html
path="/images/projects/robust_pca/rpca.png"
caption="Application of Robust PCA to data from the city of Vienna. There is one line per sensor, and the time is on the x-axis. White areas are missing data, and the more yellow an element is, the more cars were present at that time. Here only the 86th day is displayed. From left to right: raw data (with missing data, sensor bugs and an event affecting all sensors around 1pm), a completely cleaned version, the detected sensor bugs, the detected anomalies affecting the whole traffic, and the final data after only removing the sensor bugs."
%}

## References

<div style="text-indent: -3ch; margin-left: 3ch">
<p><a id="furtlehner22"></a>[1] <a name="furlasattpezgen2021"></a>Cyril Furtlehner, Jean-Marc Lasgouttes, Alessandro Attanasi, Marco Pezzulla, and Guido Gentile. <a href="https://hal.inria.fr/hal-03285664">Short-term forecasting of urban traffic using spatio-temporal Markov field</a>. <cite>IEEE Transactions on Intelligent Transportation Systems</cite>, 23(8):10858–10867, 2022. (<a href="https://who.rocq.inria.fr/Jean-Marc.Lasgouttes/publications/UrbanTraffic2021.pdf">PDF</a>) DOI:<a href="http://dx.doi.org/10.1109/TITS.2021.3096798">10.1109/TITS.2021.3096798</a></p>

<p><a id="hu21"></a>[2] Yue Hu and Daniel B. Work. 2021. Robust Tensor Recovery with Fiber Outliers for Traffic Events. <i>ACM Trans. Knowl. Discov. Data</i> 15, 1 (December 2021). DOI:<a href="https://doi.org/10.1145/3417337">10.1145/3417337</a></p>
</div>
