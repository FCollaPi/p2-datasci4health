
# Project 2 - DataSci4Health
# Predicting Death on Stress, Psychotropic Abuse, Violence Scenarios, and Anxiety Settings

## Intro
We developed this project in the context of the graduate subject [Data Science and Visualization for Health](https://ds4h.org/) for the 2022.1 term at Unicamp.

|        Name       |       RA      |  Especialization  |
| :---------------: | ------------- | ----------------- | 
| Felipe Pinheiro   |     155298    | Computer Science  |
| Guilherme Jardim  |     203438    | Computer Science  |

## Contextualization

Literature has shown us how much stress impacts day-to-day life, so it was very intuitive to circle stress-triggering variables (e.g., Violence Scenarios, Intimate Abuse) and the consequences of said stress and compute a possible interaction between them.

News and articles on psychotropic-substances abuse as a cause of stress in different settings, either home or work-related, underpinned our decision to move forward with the attempt to find a relation of available parameters discussed in this report.

This decision-making process happened concurrently with the data analysis and a debate on what we should be searching. Finally, after available data seemed empirically satisfying, we decided to put together an actual question, so the process of assessing the data could be as tangible as possible.

The question mentioned above panned out as: "What is the death prognostic for patients submitted to depression screenings?".

Data analysis and trials on tests and scores showed unsatisfying results and a weak causal relation between those variables, which eventually led us to evolve the search question to:

"What is the death prognostic to victims of violence in environments and/or intimate partner abuse (also referred to as IPV) who are diagnosed with severe anxiety, stress, major depression disorder and show unhealthy psychotropic substances abuse?"

We used the same toolset as the one presented during classes, which consisted on:
### Tools
1. Python
	- Pandas
	- Numpy
	- SQLite3
2. SQL
3. Jupyter Notebook
	- on MyBinder
	- on Visual Studio Code
4. Orange

## Methodology
Professors provided the data used in this project through [DataSci4Health on GitHub](https://github.com/datasci4health/home). In addition, such data was extracted from [Synthea](https://synthea.mitre.org), a synthetic health data generator. The tables provided on the DataSci4Health page are divided into four different scenarios, of which two were used in this analysis.

We went through the tables to understand the available data during the preliminary analysis. Then, with that in hand, we had a brief discussion to shepherd our decisions moving forward - and we achieved a consensus that mental health awareness should serve as the foundation for our analysis.

Since we aimed at a direct relation between the aforementioned parameters, with no socio-economic constraint, we could drop tables containing data with prices, vendors, or anything that could sidetrack us from our goal, such as:
-   Allergies
-   Care plans
-   Claims
-   Organizations
-   Etc.

The procedure was circular across-the-board. First, we compiled data, designed a model, and executed testing - if the results were not satisfactory, we would return to assembling data.

In this context, we used the following parameters, as labeled in the Conditions table::
-   Severe Anxiety
-   Stress
-   Major Depression Disorder
-  Unhealthy Alcohol Drinking Behavior
-   Opioid Abuse
-   Drug Overdose
-   Misuses Drugs
-   Smokes Tobacco Daily
-   Reports of Violence in the Environment
-   Victim of Intimate Partner Abuse

We built our models using data from the first scenario and then moved on to the second scenario after gathering enough tangible results.

### Used Bases
We exclusively used the given bases as follows:

-   Scenario01
-   Scenario02

No other base of reference was required, nor were the extended bases provided.

## Project Evolution & Obtained Results
We have been gathering results since the modeling part of the proposed problem. They pointed the direction toward our goal and helped us evolve the models in an intricate way to how they performed.

We had a `classification model` for assessing data related to death status (where 0 is for alive and 1 for dead) and a `regression model` targeting prognostics to evaluate how long it would take for a patient in the given scenario to die.

Since the development process evolved, we will discuss the changes over time for each trial:

### 1st Scenario
As previously stated, we wanted to tackle mental health issues and their relation to death. However, mental health thinned down to Depression Screening relatively soon since the available data was not granular enough.

This scenario was also our first approach. However, unfortunately, we had to drop this attempt due to the lack of statistical relevance.

We added more interest variables and the `Principal Component Analysis` to enhance the likelihood of assembling a more robust model from the second trial on.

On Jupyter, we iterated through the available CSVs using SQL queries to understand the tendencies and create other tables that we could export and use on Orange, as recommended by the professors.

Intuitively, on the first run, we created tables from the following relations:
-   Patient-Encounter
-   Patient-Procedure
-   Patient-Condition

Once we assessed those tables from the `depression screening` standpoint and realized they were not enough, we added up more, so we ended with the following tables constrained on a timeframe:

|                            |  Trial 1 | Trial 2 | Trial 3 | 
| :------------------------: | :------: | :-----: | :-----: |
| Patient-Encounter          |     •    |         |         |
| Patient-Condition          |     •    |         |         |
| Patient-Drugs              |     •    |         |         |
| Depressive                 |          |     •   |         |
| Depression-Death           |          |     •   |         |
| Death-Conditions           |          |     •   |         |
| Conditions-Death-Counts    |          |     •   |         |
| Contidions-Type-Counts     |          |     •   |         |
| Encounters-Reasons-Counts  |          |         |    •    |
| Encounters-Type-Counts     |          |         |    •    |
| Medications-Reasons-Counts |          |         |    •    |
| Medications-Type-Counts    |          |         |    •    |

We will further explain the reasoning behind each addition alongside the results acquired after each trial due to their strong relationship.

As for the parameters, this is the timeframe in which they took place within our analysis:

|                            |  Trial 1 | Trial 2 | Trial 3 | 
| :------------------------: | :------: | :-----: | :-----: |
| Severe Anxiety             |     •    |         |         |
| Stress                     |     •    |         |         |
| Major Depression           |     •    |         |         |
| Unhealthy Alcohol Drinking |          |     •   |         |
| Opioid Abuse               |          |     •   |         |
| Drug Overdose              |          |     •   |         |
| Misuses Drugs              |          |     •   |         |
| Smokes Tobacco             |          |     •   |         |
| Reports of Violence        |          |         |     •   |
| Partner Abuse              |          |         |     •   |

#### Trial 1
`input: depressive.csv`

For this first trial, we used the following parameters:
- Severe Anxiety
- Stress
- Major Depression

The results proved the data were not promising, which made us add more symptoms to strive for better success since the `Area Under Curve` was barely the same as a coin toss.

Due to the lack of a significant `Area Under Curve`, we opted not to deepen our analysis on this trial. Nevertheless, we gathered all results.

#### Classification Model

|          Model       |   AUC   |    CA   |    F1   | Precision |  Recall |
| :------------------: | :-----: | :-----: | :-----: | :-------: | :-----: |
| Tree                 |  1.000  |  1.000  |  1.000  |   1.000   |  1.000  |
| Neural Network       |  0.574  |  0.873  |  0.830  |   0.889   |  0.873  |
| Logistic Regression  |  0.500  |  0.850  |  0.782  |   0.723   |  0.850  |

The tree results were not feasible and made us realize we used the dead status as one of the analyzed variables instead of targeting it.

We also decided to drop the `Neural Network` moving forward due to the time required to obtain results.

The following ROC Curve (we are aware that this is not an actual curve) is not good. At all.

<img width="650" alt="roc-1st" src="https://user-images.githubusercontent.com/54454569/169718522-1c2b6be3-6de4-4527-9a10-03c9bfadfe1b.png">


##### Confusion Matrix
The `Confusion Matrix` results also clearly converged to a mistake in some settings chosen thus far.

In a similar fashion, the total absence of false positives for all the matrixes in the first trial was alone a motive to raise suspicion.

######  Tree
|   0  |   0  |   1  |   Σ  |
| ---: | ---: | ---: | ---: |
|   0  | 1990 |  0   | 1990 |
|   1  |  350 |  0   | 350  |
|   Σ  | 2340 |  0   | 2340 |

######  Neural Network
|   0  |   0  |   1  |   Σ  |
| ---: | ---: | ---: | ---: |
|   0  | 1990 |  0   | 1990 |
|   1  |  298 |  52  | 350  |
|   Σ  | 2288 |  52  | 2340 |

######  Logistic Regression
|   0  |   0  |   1  |   Σ  |
| ---: | ---: | ---: | ---: |
|   0  | 1990 |  0   | 1990 |
|   1  |    0 |  350 | 350  |
|   Σ  | 1990 |  350 | 2340 |

#### Regression Model
At this point, we were already convinced the model was a total failure, and the R2 results for the `Linear Regression` did not led us otherwise.

|          Model       |          MSE           |      RMSE     |      MAE      |   R2  |
| :------------------: | :--------------------: | :-----------: | :-----------: | :---: |
| Linear Regression    | 343035556174557248.000 | 585692373.328 | 334186392.087 | 0.192 |


#### Trial 2
`input: Patient-Drugs.csv`

With the previous experience in hand, we decided to add more variables so we could search for more complex interactions. As a result, the model developed for this scenario also needed to be more complex in robustness.

The variables added for analysis were:
- Unhealthy Alcohol Drinking
- Opioid Abuse
- Drug Overdose
- Misuses Drugs
- Smokes Tobacco

Halfway through the modeling, during discussions, we felt the urge to add a few more variables (more on this later). However, we had much better results right out of the bat for the time being.


Halfway through the modeling, during discussions, we felt the urge to add a few more variables (more on this later). However, we had much better results right out of the bat for the time being.

#### Classification Model
The PCA was a new addition to the analysis, which we had not included in the previous trial. In addition, the setup of the PCA required extra literature reading since we were not super confident about the relation between the number of components and the explained variance.

Besides that, correcting the fault mentioned above (of not targeting the correct variable) enhanced the results immensely.

##### PCA
Literature did not recommend a manual selection of the number of components. Instead, picking an `Explained Variance` between 95-99% was the preferred way of setting up the PCA across the board.

For this trial, we had to settle for 94% of explained variance to achieve the number of 9 components. Anything equal and beyond 95% would increase the number of components to 10, which did not sound right.

<img width="650" alt="pca-2" src="https://user-images.githubusercontent.com/54454569/169718528-17e63118-ceb7-4d8f-9379-0d32e5d435b2.png">


Despite the results being remarkably good, we again felt this might have been a confirmation bias, which served as the rationale for the third trial to this first scenario.

Nonetheless, we did a detailed results analysis to evolve the model better.

|         Model       |   AUC   |    CA   |    F1   | Precision |  Recall |
| :-----------------: | :-----: | :-----: | :-----: | :-------: | :-----: |
| Tree                |  0.953  |  0.970  |  0.969  |   0.970   |  0.970  |
| Logistic Regression |  0.956  |  0.940  |  0.939  |   0.940   |  0.940  |

Even though this might have been the optimal model, we were not feeling confident due to the behemoth jump between the first and second attempts.

Going from 50/50 chances to a 95% did not sound plausible, even though the `ROC Curve` is now actually a curve.

<img width="650" alt="roc-2" src="https://user-images.githubusercontent.com/54454569/169718535-61fde6be-df41-49b6-b7aa-47fff2361e79.png">

Reassessing the model made us realize that all those positive results came from the `prognostic` being among the features and not set as a target.

Afterward, the debate inclined us to laugh at ourselves and add other plausible variables to this domain, not in this particular order. So from this point on, all analysis was solemnly to gather more metadata to improve the subsequent trial.

##### Confusion Matrix
Since all data was tainted with wrong inputs, additional analysis of the Matrixes would not be valuable in any shape or form.

######  Tree
|   0  |   0   |   1   |    Σ   |
| ---: | ----: | ----: | -----: |
|   0  | 89710 |  560  | 90270  |
|   1  | 3034  | 25286 | 28320  |
|   Σ  | 92744 | 25846 | 118590 |

######  Logistic Regression
|   0  |   0   |   1   |    Σ   |
| ---: | ----: | ----: | -----: |
|   0  | 88437 |  1833 | 90270  |
|   1  | 5271  | 23049 | 28320  |
|   Σ  | 93708 | 24882 | 118590 |

#### Regression Model
The following `Scatter Plot` is a soul representation of how mistakes can taint an evaluation:

<img width="1000" alt="scatter-2" src="https://user-images.githubusercontent.com/54454569/169718555-e52b29be-9411-480f-88cb-ec650123345d.png">

If it were not for our suspicion, we could have assumed this model was an evident success. Being aware of the statistical behaviors and second guess results when they seemed too promising led us to the third and final trial.

#### Trial 3
input: Patient-Drugs.csv

Following the same principles as in the previous trials, we added the following variables:
- Reports of Violence
- Partner Abuse

After settling for these variables, we held no further debate to improve the model.

#### Classification Model
This model underperformed when compared to the previous. Nonetheless, the results were good enough to proceed with the trial.

|          Model       |   AUC   |    CA   |    F1   | Precision |  Recall |
| :------------------: | :-----: | :-----: | :-----: | :-------: | :-----: |
| Decision Tree        |  0.860  |  0.867  |  0.849  |   0.877   |  0.867  |
| Logistic Regression  |  0.667  |  0.817  |  0.787  |   0.811   |  0.817  |

The Neural Network's ROC Curve delivered us from the fear of not achieving a satisfactory statistical foundation while being feasible within parameters discussed with our peers.

<img width="650" alt="roc-3" src="https://user-images.githubusercontent.com/54454569/169718566-1cb48a94-c637-4faa-9dd3-1989f336c334.png">

#### PCA
We opted for 98% of `Explained Variance`, which resulted in 9 components that we will further analyze and refer to as analysis inputs.

<img width="650" alt="pca-3" src="https://user-images.githubusercontent.com/54454569/169718571-bf1f6b69-6b55-4c4a-8818-87d270b5c221.png">

##### Confusion Matrix
Even though the confusion matrixes were far from excellent, they showed precision good enough to move on with this model without significant compromise.

######  Logistic Regression
|   0  |    0   |    1   |    Σ   |
| ---: | -----: | -----: | -----: |
|   0  | 87645  |  2616  | 90270  |
|   1  | 19057  |  9263  | 28320  |
|   Σ  | 106711 |  11879 | 118590 |

######  Decision Tree
|   0  |    0   |    1   |    Σ   |
| ---: | -----: | -----: | -----: |
|   0  | 89434  |   836  | 90270  |
|   1  | 14961  |  13359 | 28320  |
|   Σ  | 104395 |  14195 | 118590 |

#### Regression Model
The R2 results made us shiver, but debates with our peers showed commonality in finding it hard to achieve a model that could tick all the checkboxes in quality.

So we decided to stick to it since the process that led us here was enriching itself.

|          Model       |     MSE     |    RMSE  |   MAE    |  R2   |
| :------------------: | :---------: | :------: | :------: | :---: |
| Regression Tree      | 7936089.717 | 2817.107 | 1268.487 | 0.175 |
| Linear Regression    | 9273105.390 | 3045.177 | 1514.036 | 0.037 |

##### Best-Performing Component


##### Worst-Performing Component


### 2nd Scenario
> TO-DO


## Discussion
> TO-DO

## Wrap-Up
> TO-DO

## References
- https://pubmed.ncbi.nlm.nih.gov/30914444/
- https://mecp.springeropen.com/articles/10.1186/s43045-021-00157-x
- https://www.nctsn.org/what-is-child-trauma/trauma-types/intimate-partner-violence
- https://pubmed.ncbi.nlm.nih.gov/15652265/
- https://www.apa.org/news/press/releases/2021/10/stress-pandemic-decision-making
- https://www.apa.org/news/press/releases/2021/10/stress-pandemic-decision-making
- https://www.mentalhealth.org.uk/a-to-z/s/stress
