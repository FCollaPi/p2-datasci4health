
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
	- on VSCode
4. Orange

## Methodology
We went through the tables to understand the available data during the preliminary analysis. Then, with that in hand, we had a brief discussion to shepherd our decisions moving forward - and we achieved a consensus that mental health awareness should serve as the foundation for our analysis.

Since we aimed at a direct relation between the aforementioned parameters, with no socio-economic constraint, we could drop tables containing data with prices, vendors, or anything that could sidetrack us from our goal, such as:
-   Allergies
-   Care plans
-   Claims
-   Organizations
-   Etc.

The procedure was circular across-the-board. First, we compiled data, designed a model, and executed testing - if the results were not satisfactory, we would return to assembling data.

In this context, we used the following parameters:
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

We decided to deal with the scenarios incrementally. So, we approached the first scenario before moving on to the second, following the established framework.

### 2nd Scenario
> TO-DO

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
As previously stated, the first scenario tackled mental health issues and their relation to death. However, mental health thinned down to Depression Screening relatively soon since the available data was not granular enough.

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

We also decided to drop the `Tree Model` moving forward.

![](https://i.imgur.com/t2vOswY.png)


##### Confusion Matrix
The `Confusion Matrix` results also clearly converged to a mistake in some settings chosen thus far.

In a similar fashion, the total absence of `False Positives` for all the matrixes in the first trial was alone a motive to raise suspicion.

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
At this point we were already convinced the model was a total failure, and the R2 results for the `Linear Regression` did not led us otherwise.

|          Model       |          MSE           |      RMSE     |      MAE      |   R2  |
| :------------------: | :--------------------: | :-----------: | :-----------: | :---: |
| Linear Regression    | 343035556174557248.000 | 585692373.328 | 334186392.087 | 0.192 |


#### Trial 2
`input: Patient-Drugs.csv`
>TO-DO

#### Classification Model
>TO-DO

##### PCA
![](https://i.imgur.com/Kzc8zNW.png)

|         Model       |   AUC   |    CA   |    F1   | Precision |  Recall |
| :-----------------: | :-----: | :-----: | :-----: | :-------: | :-----: |
| Tree                |  0.953  |  0.970  |  0.969  |   0.970   |  0.970  |
| Logistic Regression |  0.956  |  0.940  |  0.939  |   0.940   |  0.940  |

>TO-DO


![](https://i.imgur.com/ZclLh3u.png)


##### Confusion Matrix
>TO-DO

######  Tree
|   0  |   0   |   1   |    Σ   |
| ---: | ----: | ----: | -----: |
|   0  | 89710 |  560  | 90270  |
|   1  | 3034  | 25286 | 28320  |
|   Σ  | 92744 | 25846 | 118590 |
>TO-DO

######  Logistic Regression
|   0  |   0   |   1   |    Σ   |
| ---: | ----: | ----: | -----: |
|   0  | 88437 |  1833 | 90270  |
|   1  | 5271  | 23049 | 28320  |
|   Σ  | 93708 | 24882 | 118590 |
>TO-DO

#### Regression Model
>TO-DO

![](https://i.imgur.com/mmy7O3L.jpg)

#### Trial 3
input: Patient-Drugs.csv
>TO-DO

#### Classification Model
>TO-DO

|          Model       |   AUC   |    CA   |    F1   | Precision |  Recall |
| :------------------: | :-----: | :-----: | :-----: | :-------: | :-----: |
| Neural Network       |  0.860  |  0.867  |  0.849  |   0.877   |  0.867  |
| Logistic Regression  |  0.667  |  0.817  |  0.787  |   0.811   |  0.817  |

![](https://i.imgur.com/SLW5LFw.png)

> TO-DO

#### PCA
![](https://i.imgur.com/fmgeLiY.png)

>TO-DO

##### Confusion Matrix
>TO-DO

######  Regression Model
|   0  |    0   |    1   |    Σ   |
| ---: | -----: | -----: | -----: |
|   0  | 87645  |  2616  | 90270  |
|   1  | 19057  |  9263  | 28320  |
|   Σ  | 106711 |  11879 | 118590 |
>TO-DO

######  Tree
|   0  |    0   |    1   |    Σ   |
| ---: | -----: | -----: | -----: |
|   0  | 89434  |   836  | 90270  |
|   1  | 14961  |  13359 | 28320  |
|   Σ  | 104395 |  14195 | 118590 |
>TO-DO

#### Targeting Prognostic
|          Model       |     MSE     |    RMSE  |   MAE    |  R2   |
| :------------------: | :---------: | :------: | :------: | :---: |
| Regression Tree      | 7936089.717 | 2817.107 | 1268.487 | 0.175 |
| Linear Regression    | 9273105.390 | 3045.177 | 1514.036 | 0.037 |

>TO-DO

### 2nd Scenario
> TO-DO
#### Trial 1
> TO-DO



## Expansion
> TO-DO

## Discussion
> TO-DO

## Reasoning
> TO-DO

## References
- https://pubmed.ncbi.nlm.nih.gov/30914444/
- https://mecp.springeropen.com/articles/10.1186/s43045-021-00157-x
- https://www.nctsn.org/what-is-child-trauma/trauma-types/intimate-partner-violence
- https://pubmed.ncbi.nlm.nih.gov/15652265/
- https://www.apa.org/news/press/releases/2021/10/stress-pandemic-decision-making
- https://www.apa.org/news/press/releases/2021/10/stress-pandemic-decision-making
- https://www.mentalhealth.org.uk/a-to-z/s/stress
