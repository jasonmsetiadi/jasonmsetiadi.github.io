# About Me
I am a Data Scientist/Machine learning Enginner at DataOn Corp Indonesia. I am currently designing a production machine learning system for predicting employee attrition risk. I graduated from University of Minnesota in 2022 with a Bachelor of Science in Statistical Science degree with minors in Computer Science and Mathematics. Some of the things I like to do in my free time are playing sports such as badminton, table tennis, or soccer, as well as cooking or trying out different cuisines. Feel free to connect with me on [Linkedin](https://www.linkedin.com/in/jasonmsetiadi/). 

# Industry Projects

## 1. ([DataOn](https://www.humanica.com/en/dataon/)) ML System Design for Employee Attrition Risk Prediction
[System Design](design.pdf)

Problem Statement:
* Cost of hiring and training new employees is huge, so it is important to retain employees for a long term

Challenges:
* Framing the problem (data labeling, classification or regression, ensemble models trained on different datasets)
* Collecting informative/relevant features

Model requirements:
* Compatible with SHAP TreeExplainer or LinearExplainer for model interpretation
* Low dimensionality for fast fitting time, shap values computation time, and smaller memory size
  
System Evaluation:
* Precision (% of actual resignations out of those predicted to resign)

Impact:
* Help companies reduce attrition rate through applying targeted retention strategies on employees with high attrition risk based on feature impact

## 2. ([Altair](https://www.altair.com/)) MLOps - Pre-/Post-processing Pipelines in Model Endpoints  
The objective of this internship project is to package upstream data processing code/pipeline into the model endpoint. Some of the key points/steps to achieve this objective are:
* Learn about data science processes and machine learning frameworks (e.g. TensorFlow, PyTorch, scikit-learn), with specific focus in the area of MLOps (operationalizing machine learning models).
* Determine the scope and use cases relevant for the implementation of the pre- and post-processing pipelines in model endpoints as a new feature for the product.
* Research and compare different open source tools/packages available to solve the problem.
* Work on a coding solution as a proof of concept through performing these steps:
  * create a DockerFile that specifies package dependencies and deploy the model using Seldon Core
  * register/log the model using MLFlow by providing the model file (.pkl (sklearn)/.pt (pytorch)/.pb (tensorflow)) and a script to load the model and perform prediction
  * build a docker image and run it in a docker container using Docker Desktop
  * send api request to the model endpoint using Postman by providing the inference/scoring data to predict.
* Document the findings on tools/packages to solve the problem and the proof of concept of the feature using Confluence.
* Present the internship project to technical and non-technical audiences within Altair.

Why this project is important? Because it helps to eliminate the need for users to create an authoring batch pipeline and recode the data processing for model endpoint.

# Research Projects

## [1. Graph-Based Active Learning Research Project](SPIE_SAR_Active_Learning.pdf)
In this project I researched many graph-based active learning techniques that works alongside graph-based semi-supervised learning frameworks. Semi-supervised learning is a method of using a small subset of labeled data to predict the remaining/future unlabeled data. The idea behind graph-based active learning is to choose the most optimal points to label given a graph structure that represents the dataset. That way we can have a labeling approach that is more methodological than simply randomly sample points to label. The hope of this approach is to minimize number of labeled data while still obtaining a sufficiently high accuracy or some other performance metric.

The outcome of this research led me to build a [python module](https://jwcalder.github.io/GraphLearning/active_learning.html) for my research professor's ([*Dr. Jeff Calder*](https://www-users.cse.umn.edu/~jwcalder/)) graph-based semi-supervised learning package called [GraphLearning](https://github.com/jwcalder/GraphLearning). You can also click the link in the project title to view the research publication. Check out the link [here](https://github.com/jasonmsetiadi/UROP/blob/main/Signals_Bounds_VOPT.ipynb) if you are interested in learning more about how the active learning methods work through some visualtizations on a toy dataset.

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
