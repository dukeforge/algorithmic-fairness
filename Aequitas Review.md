# [Aequitas](http://www.datasciencepublicpolicy.org/projects/aequitas/) Review

## Overview 
Aequitas is an open-source bias audit toolkit developed by the Center for Data Science and Public Policy at the University of Chicago. It is intended to be used by developers and policymakers alike to audit risk-assessment tools that utilize machine learning. 

The tool offers the ability for the user to try auditing one of two sample datasets (COMPAS or US Adult Income Data), or upload their own data. For uploading their own data, there are clear instructions on how to format the data so that the tool can work properly. We will focus on the Compas walkthrough for this review.

One note: The home page for the project (linked in the title) is very comprehensive and offers a great overview of how the tool works. However, the link for the 'Learn More' button leads to a broken web page, so the creators should fix that for future users. 


## Select Protected Groups
![Aequitas 1](/images/aequitas_1.png)

The web demo for COMPAS on Aequitas operates as a wizard, so the user can specify parameters on each page and click on the 'Next!' button to go to the next step. After choosing COMPAS as our dataset and clicking forward, we get to the 'Select Protected Groups' page. The tool shows minimal but essential information that explains what the protected group selection entails. This part is relatively straightforward, additional information about reference group definitions in relation to bias could be useful here for those who are not familiar with this area of research. We'll go ahead and select 'Majority Group' and proceed. 

## Select Fairness Metrics
![Aequitas 2](/images/aequitas_2.png)

The final page before the Bias Report involves selecting the fairness metrics that will be evaluated. To explain these different metrics, the Fairness Tree (shown above) is used to highlight how a decision can be made. We felt that this was a really intuitive way of providing guidance for the decision, since most users will care most about how equitable their model is under different circumstances and want a deeper understanding of how these fairness metrics can help to evaluate that. There could still be some more information shown here for non-technical users (such as defining PPV), but the Fairness Tree is an overall great way of displaying a large amount of complex information and informing decision-making for the user. 

The other option on the page is for setting the Disparity Intolerance, which is described as the threshold for the audit to pass. Intuititvely, it makes sense that this will determine how strict/loose our audit will be, but it would be nice to have some more information on how varying this threshold would change the final result.

We'll select all of the fairness metrics and set the Disparity Intolerance at 90%. 

## Bias Report

This page shows the detailed results of the bias that was found in the dataset. The top of the page summarizes the choices by the user, which is a nice reminder of what parameters are affecting the displayed results. 

![Aequitas 3](/images/aequitas_3.png)

Scrolling down brought us to the Audit Results and Audit Results Summary. The first part contains hyperlinks that link to other sections of the report, which really allows for ease of navigation. In the summary section, it shows which of the bias metrics passed or failed, according to the intolerance threshold that we set in the previous screen. Hovering over the metric name shows some information, but this is the same for each metric and is generally not useful (ex. Fail/Pass test if the Predicted Positive Rate Disparity of each group is within the range allowed by the fairness threshold selected). Providing useful information in this tooltip would be a great change. Clicking on the 'Details' hyperlink takes us to that metric section in the Results section, which can also be seen by continuing to scroll down. 

![Aequitas 4](/images/aequitas_4.png)

This section shows a detailed overview of the impact of the bias metric and the magnitude of the failure/passing for each reference group. We really liked this section because they broke it down into what would be most important to the user: what is the metric and when does it matter? The groups section could probably have been better utilized and displayed as graphs instead of text, but this is overall a really useful and well-designed section. Hovering over the groups brings up the predicted positive ratio compared to the reference group, which is also a thoughtful comparison. 

![Aequitas 5](/images/aequitas_5.png)

Finally, the bottom section is a table that breaks down the different bias metrics for each attribute. As indicated by the hovertips, the numbers shown here are the metric value of the group divided by the metric value of the reference group. The choice of displaying this ratio is a good one because it is easy to understand that values much larger or much smaller than 1.0 are problematic. This is further highlighted by the choice of colors, which makes the values easy to follow but could negatively impact those who are red-green colorblind. As in the other sections, the use of graphs here would greatly improve the readability of this information. Seeing a large amount of numbers on a page can be overwhelming, especially for those who aren't used to it.   

## Additional Information

Similar to the other tools we've reviewed, the authors provided a [Github repository](https://github.com/dssg/aequitas) and an [API Details](https://dssg.github.io/aequitas/30_seconds_aequitas.html) page. The API page actually contains a more comprehensive COMPAS analysis in Python, which can be easily replicated in a Jupyter notebook. This information, along with the details provided in the Github README, is actually more informative and insightful than the demo itself. It requires a bit more time and technical expertise, but if they could find a middle ground between the demo and the technical documentation, that would be a great overview for all users. 

## Overview

We were impressed with Aequitas on COMPAS overall, finding it to be very user-friendly and informative. Cleaning up broken links and integrating more graphic visuals into the Bias Report would greatly improve the usefulness of the tool, and while we dug deeper into the API details and Github repo, most users might never get to this information. Integrating this information into the web demo and creating interactive notebooks for users to walk through would ensure that the benefits of the tool are properly showcased. 

|     Pros                                                              |     Cons                                          |
|     :---:                                                             |     :---:                                         |
| Demo is clean, well-designed, and provides enough information         | No visuals or graphs in web demo                        |
| COMPAS walkthrough in API Documentation is detailed and comprehensive  | Use of color could be problematic for red-green colorblind users                    |
| Intuitive presentation of bias measure results   | Hovertips are often repetitive and not useful     |
