# Group Notes — Resilience for Rare Hydrologic Events Management

Use this shared notebook to capture meeting highlights, decisions, and follow-up tasks for Innovation Summit Group 15.

- Summarize key takeaways after each working session.
- Note data sources, analysis ideas, and open questions.
- Assign owners and due dates for action items so nothing slips through the cracks.
- Drop helpful links, screenshots, or file references so the team can find them later.

## Questions

- How are current river management practices affecting communities and ecosystems?
- What is the response of river communities and ecosystems to hydrologic and meteorologic events?
- How do we measure response and resilience?

Original question:

- How might we improve resilience (define?) to rare hydrologic and meteorologic events (e.g. flood, drought, tornado) across communities and ecosystems through management practices?

![](images/Group15.png)
![](images/revisedGroup15.png)
![](images/Group15Notes.png)

## Study Area

- Green, Snake and Wind Rivers and their watersheds
  - Snake: Resist due to protect property
  - Wind: Accept due to Tribal influence
  - Green: Direct via ag practices
- bounded by second major reservoir for each river
- dams and lakes

## Measurements

- water-drought relationship
- Watersheds and their changes over time.
- Response variables (some possible metrics)
  - air: atmospheric -- mean, median, min, max daily %RH 
  - water: streamflow -- mean, median, sd, IQR, 5%, 95% of mean daily streamflow at gages
  - earth: land cover -- fraction of NLCD
  - fire: soil moisture -- unsure how to estimate.

## Group 15 Draft AI Task
**_This comes from Brian and Jason discussion with Tyson about using Claude to automate development of GitHub repo._**

I want to create a new scientific project. The goal is to download data from three adjacent rivers in Wyoming: Snake River, Green River and Wind River. These should bounded by their headwaters and the second major reservoir for each river. I want to download _atmospheric, stream flow, land cover and soil moisture data_. **[Use these data sources: ?]**

Download the data for a range of dates from **2020-2024**. Store the data in this project folder.

Write python scripts to analyze the daily to monthly variations in **___ and ___** for the sites.

_Create a topographic map with river features including DEM that delineates the three watersheds in their bounded regions._

Create beautiful plots that describe these patterns and highlight the variations between them.

I recommend that you create and save a plan.md that documents how you expect to execute these steps first, before using the MCP tools.

## Socioeconomic Forcings (Pseudomodel based on RAD Framework)
- Green, Snake and Wind Rivers and their watersheds stakeholders are hypothesized to place different values on water use.
  *hypothesized reponses based on a mostly uniformed prior*
  - Snake: Resistance to water and landuse changes that might affect property values for wealthy land owners
  - Wind: Accept due low socioeconomic power. Engineered solutions are not generally the preferred alternative.
  - Green: Direct changes in water use to favor production of food crops -- water is managed towards the storage of irrigation water.

### Thoughts on data science approach
- Let the data define the question -- null prior

## Draft refined questions:
1) What are the most important responses in atmospheric, streamflow, land cover, and soil mosture metrics to differential management strategies in the headwaters of the Snake River, Wind River, and Green River?
2) How do we expect these diffrential responses to affect water loss (PET), stream ecohydrology, land use patterns over time, soil mosture drought -> streamflow drought.
5) Are there ways to test these expectations from a resiliance, responce, community healing/empowerment framework?

## Thoughts on methodological approach

Gepeto (ChatGPT 5 - thinking) weighing in here

*Prompt: If I have a set of data in three different groups is there a random forest or another method to identify which variables are most important in identifying the differences?* 

### 1. Random Forest (RF)
**Setup:** Treat your groups as the response variable (factor with 3 levels) and your predictors as explanatory variables.

**Output:** RF provides variable importance measures, most commonly:
- Mean Decrease in Accuracy (MDA): how much accuracy drops when a variable is permuted.
- Mean Decrease in Gini (MDG): how much a variable contributes to node purity.

**Strengths:** Handles nonlinear relationships, interactions, and doesn’t require scaling.

**Caution:** Variable importance scores can be biased *if predictors differ in scale or number of categories*. Conditional random forests (via party::cforest in R) reduce this bias.

### 2. Gradient Boosted Trees (XGBoost, LightGBM, CatBoost)

**Setup:** Same as RF, but uses boosting instead of bagging.

**Output:** Feature importance can be computed from:
- Gain (how much a variable improves splits),
- Split count,
- SHAP values (model-agnostic and interpretable).

**Strengths:** Often more accurate than RF, with well-calibrated importance scores using SHAP.

### 3. Model-Agnostic Methods

**Permutation Importance:** Repeatedly shuffle each variable and measure how predictive performance drops. Works with any model.

**SHAP Values:** Assign local importance to each variable for each observation, then aggregate to see global drivers of group separation. Great for interpretability.

### 4. Alternative Approaches

- Multinomial Logistic Regression with Regularization (Elastic Net):
  - Coefficients show variable contributions to group separation.
  - Shrinkage helps identify most relevant predictors.

- Linear Discriminant Analysis (LDA):
  - Classic method for multi-group separation.
  - Produces linear combinations of variables that maximize group differences.
  - Loadings can highlight which variables matter most, though it assumes linearity and equal covariances.

### ✅ Recommendation:

Start with a random forest or gradient boosting model to get a nonparametric view of variable importance.

Use permutation importance or SHAP values for more robust and interpretable rankings.

If you want a simpler, more classical approach, try LDA or multinomial logistic regression for confirmation.
