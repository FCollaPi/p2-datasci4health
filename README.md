# Project 2 - DataSci4Health
# Predicting Death on Violence Scenarios, Psychotropic Abuse, Anxiety Settings, and Stress

## Introduction
We created this project in the context of the graduate subject [Data Science and Visualization for Health](https://ds4h.org/) for the 2022.1 term at Unicamp.

|        Name       |       RA      |   Concentration   |
| :---------------: | ------------- | ----------------- |
|  Felipe Pinheiro  |     155298    | Computer Science  |
| Guilherme Jardim  |     203438    | Computer Science  |

## Contextualization
Literature has shown us how much stress impacts day-to-day life, so it was very intuitive to circle stress-triggering variables (e.g., Violence Scenarios, Intimate Abuse) and the consequences of said stress and compute a possible interaction between them.<br><br>
News and articles on psychotropic-substances abuse as a cause of stress in different settings, either home or work-related, underpinned our decision to move forward with the attempt to find a relation of available parameters discussed in this report.<br><br>
This decision-making process happened concurrently with the data analysis and a debate on what we should be searching. Finally, after available data seemed empirically satisfying, we decided to put together an actual question, so the process of assessing the data could be as tangible as possible.<br><br>
The question mentioned above panned out as: "What is the death prognostic for patients submitted to depression screenings?".<br><br>
Data analysis and trials on tests and scores showed unsatisfying results and a weak causal relation between those variables, which led us to evolve the search question to:<br><br>
"What is the death prognostic to victims of violence in environments and/or intimate partner abuse (also referred to as IPV) who are diagnosed with severe anxiety, stress, major depression disorder and show unhealthy psychotropic substances abuse?".

### Tools
1. Python
	- Pandas
	- Numpy
	- SQLite3
2. SQL
3. Orange

## Methodology
In the preliminary analysis, we went through all the available tables to understand what kind of data was available. Then, with that in hand, we held a brief discussion to shepherd our decisions moving forward - and we reached a consensus that mental health awareness should serve as a foundation for our analysis.<br><br>
Since we aimed at a direct relation between the aforementioned parameters, with no socio-economic constraint, we could drop tables containing data with prices, vendors, or anything that could sidetrack us from our goal, such as:

-   Allergies
-   Care plans
-   Claims
-   Organizations
-   Etc.

The overall procedure was circular. First, we gathered data, developed a model, and conducted testing - if the results were not satisfactory, we would return to gathering data.<br><br>
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

### 1st Scenario
For the first scenario, this is the timeframe in which we added them:
|                           | 1st Trial | 2nd Trial | 3rd Trial | 
| :-----------------------: | :-------: | :-------: | :-------: |
| Severe Anxiety            |      •    |           |           |
| Stress                    |      •    |           |           |
| Major Depression          |      •    |           |           |
| Unhealthy Acohol Drinking |           |     •     |           |
| Opioid Abuse              |           |     •     |           |
| Drug Overdose             |           |     •     |           |
| Misuses Drugs             |           |     •     |           |
| Smokes Tobacco            |           |     •     |           |
| Reports of Violence       |           |           |     •     |
| Partner Abuse             |           |           |     •     |

### Used Bases
We only used the given bases as follows:

-   Scenario01
-   Scenario02

No other base of reference was needed, nor were the extended bases provided.

## Obtained Results

## Expansion

## Discussion

## Reasoning

## References
- https://pubmed.ncbi.nlm.nih.gov/30914444/
- https://mecp.springeropen.com/articles/10.1186/s43045-021-00157-x
- https://www.nctsn.org/what-is-child-trauma/trauma-types/intimate-partner-violence
- https://pubmed.ncbi.nlm.nih.gov/15652265/
- https://www.apa.org/news/press/releases/2021/10/stress-pandemic-decision-making
- https://www.apa.org/news/press/releases/2021/10/stress-pandemic-decision-making
- https://www.mentalhealth.org.uk/a-to-z/s/stress
