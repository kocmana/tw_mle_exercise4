# Exercise 4 - more comparative evaluation
This exercise follows very much the style of the previous exercise - you shall do experiments with different data sets and classifiers. Again, you can do the exercise alone, or in a group of two.

The datasets to use are
* The datasets from the exercise 3, i.e. Iris, Optical Digits (and if you are in a group, then also Breast Cancer)
* Either the music or the image data set - decided by your matriculation number modulo 2, 0 means music, 1 means image (If you are doing this exercise in a group, then you shall take both data sets)

The classifiers & parameters to use are
* All the classifiers & parameters from exercise 3
* Decision trees, you shall have two setups: one fully grown tree, and one setting for a pruned or pre-pruned tree.
   * (If you are a group, you shall try a total of four settings: two unpruned trees using two different split criteria, and two setups for different amounts of (pre)-pruning the tree.)
* Random Forests, using two different settings for the number of trees
   * (If you are in a group, also vary the number of attributes that are used in each split; use three different values resp. computation methods (sqrt, log, fraction, ...); this should give you a total of 6 runs: (2 number of trees) x (3 number of attributes))
* SVMs: just use the default settings, but use both SVC and LinearSVC classifiers (http://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html, http://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html)

## Image Dataset
We will use the "Fruit Image Dataset", originally provided at http://data.vicos.si/datasets/FIDS30/, but with an edited version linked from Moodle (some images had an encoding not compatible with e.g. python libraries). Your task is to classify images into the category of fruit (a total of 30 defined categories) they belong to.

As this is image data, feature extraction is a requirement before we can actually learn anything. As you shouldn't spend too much time on that, there is demo code on how to work with this data available, linked from the course main page.

This code generates a set of 4 different features, all rather simple and based on histograms of colours (i.e. counts on how often a certain colour appears). You shall work with all four of them, and likely will see very different results.

## Music Dataset

We will use the dataset provided by George Tzanetakis, called "gtzan". This dataset contains 1.000 songs, 100 songs for 10 genres, and the task is therefore to predict the genres of a song; to limit file size, the songs are only 30 second snippets, and sampled with 22 khz only. You can download the dataset from the Moodle main page, or also at at http://kronos.ifs.tuwien.ac.at/GTZANmp3_22khz.zip. As this is copyrighted materials, please do not redistribute it...!

As this is audio data, feature extraction is a requirement before we can actually learn anything. Therefore, there is demo code on how to work with this data available, linked from the course main page.

This code generates different features, very simple ones containing just BeatsPerMinute, to more advanced ones based on advanced signal processing.  You shall work with all of them, and likely will see very different results.

## Working in a group
If you work in a group, as partially written above, your scope will be extended

* More datasets: both music & image datasets
* More parameter variations
* More evaluation: for the Music&Image datasets, you shall also add an analysis of the confusion matrix for these datasets. It is sufficient, to provide one confusion matrix per feature set, you can select either the best classifier that you had on that feature set, or also other interesting ones.

## Links for python
* http://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html
* http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html
* http://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html

## Non-python feature extractors
### Java
* For images, you can use a port of openCV, the OpenCV bindings (http://docs.opencv.org/2.4/doc/tutorials/introduction/desktop_java/java_dev_intro.html) or a different implementation in  Java: https://github.com/bytedeco/javacv. The sample code should then be quite similar to the one in python.
* For music: http://jmir.sourceforge.net/index_jAudio.html (the jAudio component) offers a GUI for extracting features, best is to use BPM (strongest beat), MFCCs and Chroma, and their derivatives, i.e. the statistics that are also used in the sample code. jAudio should be able to generate ARFF files for WEKA.

### C#
* For image, you should find OpenCV bindings as well for C#