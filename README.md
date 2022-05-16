# Project 2 - DataSci4Health
# Predicting Death on Stress, Psychotropic Abuse, Violence Scenarios, and Anxiety Settings

## Intro
We created this project in the context of the graduate subject Data Science and Visualization for Health (https://ds4h.org/) for the 2022.1 term at Unicamp.

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

### Tools
1. Python
	- Pandas
	- Numpy
	- SQLite3
2. SQL
3. Orange

## Methodology
In the preliminary analysis, we went through all the available tables to understand what kind of data was available. Then, with that in hand, we held a brief discussion to shepherd our decisions moving forward - and we reached a consensus that mental health awareness should serve as a foundation for our analysis.

Since we aimed at a direct relation between the aforementioned parameters, with no socio-economic constraint, we could drop tables containing data with prices, vendors, or anything that could sidetrack us from our goal, such as:
-   Allergies
-   Care plans
-   Claims
-   Organizations
-   Etc.

The overall procedure was circular. First, we gathered data, developed a model, and conducted testing - if the results were not satisfactory, we would return to gathering data.
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

We decided to deal with the scenarios incrementally, so we first approached the first scenario and circled the above loop to only deal with the second scenario afterward.

More on the procedures for each scenario:

### 1st Scenario
On Jupyter, we iterated through the available CSVs using SQL queries to understand the tendencies and create other tables that we could export and use on Orange, as recommended by the professors.

Intuitively, on the first run, we created tables from the following relations:
-   Patient-Encounter
-   Patient-Procedure
-   Patient-Condition

Once we assessed those tables from the depression screening standpoint and realized they were not enough, we added up more, so we ended with the following tables constrained on a timeframe:

|                            |  1st Trial | 2nd Trial | 3rd Trial | 
| :------------------------: | :--------: | :-------: | :-------: |
| Patient-Encounter          |   •        |           |           |
| Patient-Condition          |      •     |           |           |
| Patient-Drugs              |     •      |           |           |
| Depressive                 |            |    •      |           |
| Depression-Death           |            |    •      |           |
| Death-Conditions           |            |     •     |           |
| Conditions-Death-Counts    |            |     •     |           |
| Contidions-Type-Counts     |            |     •     |           |
| Encounters-Reasons-Counts  |            |           |    •      |
| Encounters-Type-Counts     |            |           |    •      |
| Medications-Reasons-Counts |            |           |    •      |
| Medications-Type-Counts    |            |           |    •      |

Due to their strong relationship, we will further explain the reasoning behind each addition and the results obtained after each trial in the "Obtained Results" session.

As for the parameters, this is the timeframe in which they took place within our analysis:

|                            | 1st Trial | 2nd Trial | 3rd Trial | 
| :------------------------: | :-------: | :-------: | :-------: |
| Severe Anxiety             |      •    |           |           |
| Stress                     |      •    |           |           |
| Major Depression           |      •    |           |           |
| Unhealthy Alcohol Drinking |           |     •     |           |
| Opioid Abuse               |           |     •     |           |
| Drug Overdose              |           |     •     |           |
| Misuses Drugs              |           |     •     |           |
| Smokes Tobacco             |           |     •     |           |
| Reports of Violence        |           |           |     •     |
| Partner Abuse              |           |           |     •     |

### 2nd Scenario


### Used Bases
We only used the given bases, as it follows:

-   Scenario01
-   Scenario02

No other base of reference was needed, nor the extended bases provided.

## Obtained Results

## Expansion

## Discussion

## Reasoning
