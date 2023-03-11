sources: https://www.analyticsvidhya.com/blog/2021/11/model-explainability/


# What is Model Explainability?

Model explainability refers to the concept of being able to understand the machine learning model. For example – If a healthcare model is predicting whether a patient is suffering from a particular disease or not. The medical practitioners need to know what parameters the model is taking into account or if the model contains any bias. So, it is necessary that once the model is deployed in the real world. Then, the model developers can explain the model. 

# Why is Model Explainability Required?

1. Being able to interpret a model increases trust in a machine learning model. This becomes all the more important in scenarios involving life-and-death situations like healthcare, law, credit lending, etc. For example – If a model is predicting cancer, the healthcare providers should be aware of the available variables.

2. Once we understand a model, we can detect if there is any bias present in the model. For example – If a healthcare model has been trained on the American population, it might not be suitable for Asian people.

3. Model Explainability becomes important while debugging a model during the development phase.

4. Model Explainability is critical for getting models to vet by regulatory authorities like Food and Drug Administration (FDA), National Regulatory Authority, etc. It also helps to determine if the models are suitable to be deployed in real life.

# Ways to Interpret a Model 

Global vs Local interpretation 

=================================================================================
|Global Interpretation            |    Local Interpretation                     |
=================================================================================
|This helps in understanding how  |This helps in understanding how the model    |
|a mode makes decisions for the   |makes decisions for a single instance.       |
|overall structure.               |                                             |
---------------------------------------------------------------------------------
|Using global interpretation we   |Local interpretation helps in understanding  |
|can explain the complete behavior|the local behavior of the model in the local |
|of the model for deployment.     |neighborhood.                                |
--------------------------------------------------------------------------------- 
|Global interpretation help in    |Local interpretation helps in understanding  |
|understanding the suitability of |the behavior of the model in the local       |
|the model for deployment.        |neighborhood. Example: understanding why a   |
|                                 |specific person has high risk of a disease.  |
---------------------------------------------------------------------------------


# Local Interpretation 

1. LIME (Local Interpretable Model-agnostic Explainations).
2. SHAP (SHapley Additive exPlanations).

# LIME (Local Interpretation Model-agnostic Explanations)

LIME provides a local interpretation by modifying feature values of a single sample and observing its impact on the output. It builds a surrogate model from the input (sample generation) and model predictions. An interpretation model can be used as a surrogate model. Because LIME is a modela agnostic technqiue. Therefore it can be used on my  model.

## STEPS involved in LIME


1. It creates a permutation (fake) of the given data.

2. It calculates the distance between permutations and the original observations. Also, we can specify the distance measured.

3. Then, it makes predictions on the new data using some black-box models.

4. It picks “m” features that describe the complex model. It is an outcome from the permuted data in the best possible way through the maximum likelihood approach. Here, we can decide the number of features i.e. the value of “m” we want to use.

5. It picks the “m” features and fits a simple model to the permuted data with the similarity score as weights.

6. The weights from the simple model are used to provide explanations for the complex model’s local behavior.

# SHAPY (SHaply Additive exPlanations)

SHAP shows the impact of each feature by interpreting the impact of a certain value compared to a baseline value. The baseline used for prediction is the average of all the predictions. SHAP values allow us to determine any prediction as a sum of the effects of each feature value.

The only disadvantage with SHAP is that the computing time is high. The Shapley values can be combined together and used to perform global interpretations also.

# Global Interpretaton

1. PDP (Partial Dependency Plot).
2. ICE (Individual Conditional Expectation).

# PDP (Partial Dependency Plot)

PDP explains the global behavior of a model by showing the relationship of the marginal effect of each of the predictors on the response variable.

It shows a relationship between the target variable and a feature variable. Such a relationship could be complex, monotonic, or even a simple linear one. The plot assumes that the feature of interest (whose partial dependence is being computed) is not highly correlated with the other features. If the features of the model are correlated, then PDP does not provide the correct interpretation. We cannot plot PDP for all complex classifiers like Neural Networks.

# ICE (Individual Conditional Expectation)

ICE is an extension of PDP(global method) but they are more intuitive to understand as compared to PDP. Using ICE, we can explain heterogeneous relationships. While PDP supports two feature explanations using ICE we can explain only one feature at a time.

Thus, it provides a plot of the average predicted outcomes. These outcomes are for different values of a feature while keeping the values of other feature values are constant.

