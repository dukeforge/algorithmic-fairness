# Google's What-If Tool Review

Overview: Google's What-If tool is a visual interface for digging deeper into your machine learning models, regardless of your technical background. The tool offers various capabilities, including comparing model performance, comparing counterfactuals to datapoints, and testing pre-defined algorithmic fairness constraints. 

There are various web and Colab notebook demos available; for our purposes, we'll focus on the COMPAS Recidivism Classifier notebooks. Google offers two versions of this notebook: one with feature attributions (using the SHAP library) and another without these attributions. Both notebooks follow a similar workflow, so we'll show our walkthrough of the COMPAS with SHAP notebook.

![What-If Top](/images/whatif_1.png)

Upon opening of the notebook, we see a description of the notebook contents, along with links to background content on ML fairness with COMPAS. This information, along with the additional context in this text block, does a good job of acquaiting the user with the appropriate use of the What-If tool. That being said, there are a couple of opportunities for improvment for non-technical audiences: 

a) The notebook assumes familiarity with the Colab runtime, but those who haven't used Colab before might be unsure about how to run the notebook

b) There is no background information on SHAP values, including how they are calculated or how to intepret them. Data scientists are probably familiar with SHAP, but SHAP is also one of many available variable importance metrics, and there is no information provided for why SHAP was chosen over other metrics.

Continuing along the notebook, there are code blocks to import the COMPAS data, preprocess the data, and train the Keras prediction model. Comments are provided to explain some of the code, and while some of the commenting could be improved, most non-technical users probably won't dig too deep into these details. The larger issue is that there are certain deprecation errors that arise after running these code blocks. Most of these are related to the change from TensorFlow 1.x to 2.0, and while there doesn't seem to be any change in the output, this could cause issues in the future. 

![What-If Code](/images/whatif_2.png)

Finally, the last part of the notebook contains the code necessary to run the What-If tool itself. This tool has three primary components:

## Datapoint Editor
![What-If Datapoint Editor](/images/whatif_3.png)

This tab provides an overview of the datapoints, labelled by their inference value (Low risk vs. Medium/High risk of recidivism). Clicking on a datapoint brings up its feature values, along with how much that value attributes to the prediction. This is a nice interface for being able to visually understand how changes in data values can lead to changes in model prediction, and the layout is intuitive and clear. 

The variable names are kept from the raw data, and there isn't any explanation of what these variables mean/how they are calculated; while the names are relatively self-explanatory, users who are not familiar with COMPAS may have a little trouble following along. There are also additional parameters that can be changed, but no explanation for how they might be used; for example, the choice between L1 and L2 distance is available, but no further information is provided (see Additional Information below). 

## Performance & Fairness
![What-If Performance & Fairness](/images/whatif_4.png)

The next tab shows performance curves (AUC & PR) and allow the user to adjust the threshold value to visualize the difference in the false positive and false negative rate. This is an important consideration as a data scientist (or model user), and I'm a huge fan of how this view was created. Each of the configuration options are clearly explained, with hyperlinks for more information and context. Using the slider to adjust the treshold and view the decision criteria change on the graph was also simple and easy to use and understand. 

## Features
![What-If Features](/images/whatif_5.png)

The final tab in this tool shows the distribution of features across the dataset. Immediately, I found the text hard to read; the gray text is very difficult to pick out on the white background. Additionally, I'm not entirely sure what the purpose of this tab is; I believe that it was intended to provide summary statistics on the various features in the dataset, but this data is just shown in a plain table. As a data scientist, I would simply create these plots/distributions myself, so I don't gain any additional information from this tab. For a non-technical user, this tab would only be useful if they had a specific question about the distribution of a certain feature, but this view does not lend itself for easy intepretation.


## Additional Information
The question mark button in the top right takes you to the [Github README](https://github.com/PAIR-code/what-if-tool/blob/master/README.md) for the What-If tool, which does provide some great additional context and information (such as links to SHAP and other feature attribution values). However, there are typos throughout the document, and while it is comprehensive, it is also quite cumbersome to read through it all and find the information that might be relevant. It might have been more useful to have hovertips enabled in the tooltip itself, so that a non-technical user can get a quick summary of what the various parameters mean. This was somewhat achieved through the information buttons displayed next to some of the parameters, but this could be expanded.

## Overview
The What-If tool is a solid comprehensive tool for model examination and explainability. For the COMPAS notebook demo, there are TensorFlow version issues and missing background information that might make it a little difficult for a non-technical user to follow along. For the tool itself, the Datapoint Editor and Performance & Fairness tabs are insightful and encourage the user to tinker with the data. Conversely, the Features tab is virtually useless and hard to read, so that is a huge area for potential improvement. The additional documentation provided on Github is useful, but it would be nice to have this information displayed across the demo itself so that the burden on the user is lessened.

|     Pros                                                    |     Cons                                          |
|     :---:                                                   |     :---:                                         |
| Notebook is well-documented and runs with one click         | Package version issues                            |
| Datapoint Editor and Performance & Fairness tabs are useful | Features tab provides no value                    |
| Links are provided for additional background information    | Additional context is hidden in Github README     |
