<!-- # About Me
I am a Data Science / Machine Learning enthusiast originated from Indonesia. I graduated from University of Minnesota with a Bachelor of Science in Statistical Science with minors in Computer Science and Mathematics. The skills I possess include coding in Python and R, usage of common data science libraries, collaborating on Github, writing in LateX, etc. -->

# Research Projects

## [1. Graph-Based Active Learning Research Project](https://jwcalder.github.io/GraphLearning/active_learning.html)
In this project I researched many graph-based active learning techniques that works alongside graph-based semi-supervised learning frameworks. Semi-supervised learning is a method of using a small subset of labeled data to predict the remaining/future unlabeled data. The idea behind graph-based active learning is to choose the most optimal points to label given a graph structure that represents the dataset. That way we can have a labeling approach that is more methodological than simply randomly sample points to label. The hope of this approach is to minimize number of labeled data while still obtaining a sufficiently high accuracy or some other performance metric.

The outcome of this research led me to build a python module for my research professor's ([*Dr. Jeff Calder*](https://www-users.cse.umn.edu/~jwcalder/)) graph-based semi-supervised learning package called [GraphLearning](https://github.com/jwcalder/GraphLearning), which can be viewed from the link by clicking the project title. Check out the link [here](https://github.com/jasonmsetiadi/UROP/blob/main/Signals_Bounds_VOPT.ipynb) if you are interested in learning more about how the active learning methods work through some visualtizations on a toy dataset.

## [2. Astronomy Active Learning Research Project](https://github.com/ZwickyTransientFacility/scope)
In this project, I worked as a undergraduate research assistant for [Dr. Michael Coughlin](https://www.michaelwcoughlin.com/)'s astronomy group called *Coughlin Multi-Messenger Astronomy Group*. In general, my work is about performing active learning to identify ambiguous light curve objects, from selecting points to label, labeling them by hand, and uploading the labeled data to the source website called [Fritz](https://fritz.science/). Some skills involved in this process include data manipulation using *Pandas* and usage of *Rest APIs* to create and filter processed data sets using a *MongoDB* framework. All work in this group can be viewed through the link on the project title that will lead to the github page. Some of my contributions include creating Python scripts to [find ambiguous objects](https://github.com/ZwickyTransientFacility/scope/blob/main/tools/scope_upload_disagreements.py), [upload labeled objects](https://github.com/ZwickyTransientFacility/scope/blob/main/tools/scope_upload_classification.py), as well as [download labeled objects](https://github.com/ZwickyTransientFacility/scope/blob/main/tools/scope_download_classification.py).

# Capstone Projects

## [1. Independent Research Project: Logistic Regression vs Perceptron](Research.pdf)
This project asks each student to do their own independent research on some topic of their choice in statistics. I chose to research about the connections between logistic regression and perceptron, contrasting their similarities and differences, since I find them to be interesting and worth noting. Besides discussing the theory behind these two techniques, I also applied them to a famous [US Census dataset](https://archive.ics.uci.edu/ml/datasets/adult) to observe their performance. Here is the summary of my research presented in a table. For more details regarding my research, click on the link on the title.

|                          | **Logistic Regression** | **Perceptron** |
|--------------------------|:-----------------------:|:--------------:|
| **Number of Parameters** |           p+1           |     2*(p+1)    |
| **Activation Function**  |     Logistic/Sigmoid    |     Softmax    |
| **Output**               |     Continuous [0,1]    | Discrete {0,1} |
| **Assumptions**          |           Yes           |       No       |
| **Interpretable**        |           Yes           |       No       |

## [2. Statistical Consultation Project: Effect of Wood Harvesting on *Bursera Simaruba* Population](Consulting.pdf)
In this project, we are trying to answer several research questions that a PhD student has regarding her dataset. Our task is to perform statistical analyses to observe any significance caused by predictors of interest (whether the plot has been harvested, plot's vegetation type, and whether the plot adopts *Milpa* agricultural system) on different response variables (basal area, stem density, and population size structure). In general, we use the ANOVA to observe any significant effects as well as ggplot to perform visualizations to gain more insight.
