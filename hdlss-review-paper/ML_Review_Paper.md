MACHINE LEARANING FOR HIGH-DEMENSIANAL SMALL-SAMPLE DATA 

**Machine Learning Models for High-Dimensional, SmallSample Data: A Review of Microarray Gene Expression Classification Studies** 

P. U. O. Fernando (HNDDS25.2-002) 

P. S. S. Vithanage (HNDDS25.2-003) 

D. M. D. Gunawardhana (HNDDS25.2-004) 

Module: Machine learning 01 

Course work 02 

Department of Data Science 

National Institute of Business Management 

HND in Data Science, Batch HNDDS 25.2F 

August 2026 

MACHINE LEARANING FOR HIGH-DEMENSIANAL SMALL-SAMPLE DATA 

# **Machine Learning Models for High-Dimensional, Small-Sample Data: A Review of Microarray Gene Expression Classification Studies** 

There's a critical assumption behind most machine learning algorithms, which one's easy to miss: that training examples are far more numerous than variables that describe them. All of these models require sufficient data to estimate consistent relationships among data features, or between features and outcomes, to allow regression, decision trees, and neural networks to work. But in much of the contemporary research, this is the other way around. In many scenarios, such as genomics, medical imaging and text analysis, the number of variables measured is in the thousands, and the sample or subject size is in the tens or low hundreds. This is known as the high-dimensional, small-sample problem, or the “large p, small n” problem, and is a real challenge to traditional classification and clustering algorithms, as they can learn to fit more parameters to their training data than they have observations, and they will fit it very well, but failed to generalise to anything new. 

One of the most obvious examples is the gene expression data obtained from microarrays. Only a few dozen tissue samples are typically used in most studies published to date, as there are cost, ethical, and difficulty constraints to getting patients to participate in a single microarray experiment to record the expression level of several thousand genes. A reliable classifier, such as one that could classify between tumour and normal tissue, requires learning from a set of data with a number of features (hundreds or thousands) much larger than the number of samples (jyst tens, or a few dozen). This makes the microarray classification a good test case to gain insight into the behavior of various machine learning models when the number of samples is very low compared to the number of features, it’s also the exact setting used in the research paper reviewed here. 

This paper is a review of a paper that was published by Pirooznia et al. (2008) where they compared various classification, clustering and feature selection techniques for eight publicly available microarray datasets. Instead of merely summarizing their findings, the goal is to analyze the implications that the study draws from the behavior of machine learning systems on highdimensional, small-sample data, and to compare their results with more recent work that has focused on developing techniques for high-dimensional, small-sample data. Finally, the review ends with remarks that apply to the work that we did in our course, where similar situations of high dimension and small sample size may be encountered. 

# **Review** 

Pirooznia et al. (2008) used eight binary-class microarray datasets covering Lymphoma, Breast Cancer, Colon cancer, Lung cancer, Adenocarcinoma and Ovarian cancer. Numbers of samples 

MACHINE LEARANING FOR HIGH-DEMENSIANAL SMALL-SAMPLE DATA 

ranged from 25 to 96 and numbers of genes ranged from 917 to just over 8,000 per dataset, so all datasets in the study had far more features than samples. The authors used seven classifiers (SVM, RBF neural network, MLP neural network, naive Bayes, two decision tree variants, random forest, and bagging) and four different clustering methods (k-means, expectation-maximisation, farthestfirst, and density-based clustering), as well as three feature selection techniques (SVM-RFE, correlation-based feature selection, and chi-squared testing) to the preprocessed intensity data. The accuracy was estimated using ten-fold cross-validation throughout as a good choice for small-scale samples, although it is also limited at this size, as will be explained later. 

Without any feature selection the best general performance was obtained by support vector machines and RBF neural networks with accuracy of more than 94% for most of the datasets and as high as 97.6% in case of breast cancer. The worst results were obtained by decision trees, which achieved an overall accuracy rate of 48% on the smallest lymphoma dataset (25 samples), barely performing better than random guessing on a two class problem. Naive Bayes was in the middle with an average score of around 80's to low 90's. The most notable thing here is that none of the methods came out on top on all the datasets. Some classifiers, such as naive Bayes and J48 decision tree, achieved an abnormal success rate on the colon and lung cancer sets, while other classifiers, such as random forest and bagging, underperformed relative to SVM and RBF networks on nearly all of the sets. That's a nice overall principle in machine learning, that no single algorithm will work on every problem, but this gets even more pronounced when you go down to a few dozen cases; a few weird patients can move the needle by 10 or 20 percent on the accuracy of a classifier. The best result in the paper is about feature selection. Nearly all combinations of feature selection method (SVM-RFE, correlation-based selection and chi-squared) and each of the classifiers tested showed an increase in accuracy after reduction of each dataset to its top 50 genes, as well as a reduction in processing time and memory required to train the classifiers. The improvement was greatest in the case of the weaker classifiers. Decision trees, naive Bayes, and those models that had poor performance when supplied with the entire gene set, came into closer alignment with the accuracy of SVM and RBF networks when the number of features was limited. SVM-RFE and SVM classifier gave 100% accuracy for four out of eight datasets including smallest dataset. This is an impressive finding, and one that is relevant to the broader field of bioinformatics: feature selection is not an optional turning step but close to a necessary condition for building a workable model when the number of features is orders of magnitude larger than the number of samples (Saeys et al., 2007). 

The results from the unsupervised clustering were definitely poorer than the supervised classification results and were not as consistent. Farthest-first traversal gave the most stable 

MACHINE LEARANING FOR HIGH-DEMENSIANAL SMALL-SAMPLE DATA 

performance across the eight datasets, but expectation-maximization clustering swung between 54.2% on one lymphoma dataset and 81% on the melanoma dataset, with no clear explanation for why it worked well on one and poorly on another. This is not unexpected with the issue in mind. Clustering algorithms classify samples based on the distance or density between them, based on thousands of genes, many of which are not directly related to the class label which the researchers are interested in. When there is no label information to use for determining which genes are relevant, noise from irrelevant genes will swamp the distance calculation function and it will be much more difficult for a clustering algorithm to recover the true class structure than for a supervised classifier to do so for the identical, already-reduced, feature set. 

The study is really useful as a comparison of methods but there are a couple of points to note, particularly in the light of the development of the field since 2008. Firstly, the paper provides point accuracy results for 10-fold cross-validation, without confidence intervals, standard errors or significance tests. Each fold of the cross validation has only 2-3 samples, meaning that a single misclassified sample is enough to affect the accuracy by a few percentage points. The one number that is reported, e.g., SVM-RFE achieving an accuracy of 100% on a particular split of the data, needs to be accompanied by a statement of the degree of stability it would have if it was obtained from a different split. Second, the paper chose 50 genes not because of a clear statement of the statistical criterion for selection, but because of computational convenience, and it does not explicitly state whether feature selection was repeated within each of the cross validation folds, or whether it took place once on the full dataset before cross-validation began. This is significant when feature selection is performed on the test samples prior to calculating accuracy, as it can lead to an overly optimistic estimate of the accuracy, a pitfall that reviews of feature selection in bioinformatics specifically warn against that one must be wary of (Saeys et al., 2007). Third, the classifiers tested in the study (SVM, neural networks, decision trees, Bayesian methods) were all originally built to work with the more common scenario of more samples than features, but were not "tuned" to the micro-array data set. 

Later research in this field has turned towards the construction of classifiers and feature selectors based on the high dimensional, small sample constraint itself as opposed to testing off-the-shelf general-purpose algorithms on this constraint. Shen, Er and Yin (2022) for instance, have developed a linear classifier specifically for high-dimensional, low-sample-size data by maximizing how spread out each class is within itself, not the distance between classes, targeting the kind of overfitting that can occur with standard SVMs once the number of features runs in to the thousands. To address the issue of overfitting in small sample sizes, Chen, Weiss, and Liu (2023) adopted a graph-based deep learning approach that considers relationships among samples as well as 

MACHINE LEARANING FOR HIGH-DEMENSIANAL SMALL-SAMPLE DATA 

relationships among features for feature selection. Also not limited to newer methods: there is an entire line of research dedicated to small sample size behaviour of the linear discriminant analysis which is a much older and simpler method than SVM or neural networks, where the within-class scatter matrix becomes unreliably estimated as soon as there are more features than samples (Sharma & Paliwal, 2015). These targeted techniques are not the ones used by Pirooznia et al. (2008), who still use them today, but they are less advanced and the basic idea was to simply use an existing classifier along with an existing feature selection method and observe the results. 

# **Conclusions** 

Combined, the results of Pirooznia et al. (2008) provide a pretty good picture of the behavior of machine learning models on high-dimensional, small-sample microarray data. Support vector machines and RBF neural networks tend to be strong default choices, decision trees tend to struggle unless the feature space is reduced first, and feature selection has a large and fairly consistent positive effect on accuracy across almost every classifier tested prior to classification. Unsupervised clustering is much less reliable in this context, with the absence of class labels to point the way through thousands of mostly irrelevant genes. The study at the same time contains certain restrictions which researchers have sought to remove since then, such as the validity of accuracy estimates from very small sample sizes, and the potential for feature selection bias if it is not sufficiently distinguished from the validation process. 

For our project, which is indeed also dealing with data, but in which the number of features can be high, relative to the number of available samples, this review suggests a few practical lessons. Dimensionality reduction should be treated as a core part of the modelling process rather than an afterthought, cross-validation needs to be set up carefully so that feature selection does not leak information from the test folds, and reported accuracy figures should be read cautiously when the sample size is small enough that a handful of cases can swing the result the reported accuracy figures when the sample size is so small that a few cases can change the outcome. There might be newer, bespoke techniques for high-dimensional, small-sample data worth investigating in the future, but the comparative method of Pirooznia et al. (2008) is a good starting point to understanding the behaviour of ordinary classifiers before more specialised techniques can be attempted. 

# **References** 

MACHINE LEARANING FOR HIGH-DEMENSIANAL SMALL-SAMPLE DATA 

Chen, C., Weiss, S. T., & Liu, Y.-Y. (2023). Graph convolutional network-based feature selection for high-dimensional and low-sample-size data. Bioinformatics, 39(4), Article btad135. <u>https://doi.org/10.1093/bioinformatics/btad135</u> 

Pirooznia, M., Yang, J. Y., Yang, M. Q., & Deng, Y. (2008). A comparative study of different machine learning methods on microarray gene expression data. BMC Genomics, 9(Suppl 1), Article S13. https://doi.org/10.1186/1471-2164-9-S1-S13 

Saeys, Y., Inza, I., & Larrañaga, P. (2007). A review of feature selection techniques in bioinformatics. Bioinformatics, 23(19), 2507–2517. https://doi.org/10.1093/bioinformatics/btm344 

Sharma, A., & Paliwal, K. K. (2015). Linear discriminant analysis for the small sample size problem: An overview. International Journal of Machine Learning and Cybernetics, 6(3), 443–454. <u>https://doi.org/10.1007/s13042-013-0226-9</u> 

Shen, L., Er, M. J., & Yin, Q. (2022). The classification for high-dimension low-sample size data. Pattern Recognition, 130, Article 108828. https://doi.org/10.1016/j.patcog.2022.108828 

