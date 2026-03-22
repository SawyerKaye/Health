# Sawyer Kaye, CS781 Project Update

# Title: Machine Learning in Anesthesia PLan Development

## Introduction

The VitalDB dataset has over 6000 records of patient data for surgeries, with many pre/intraoperative data points per patient. The objective of this project is to develop a ChatBot aid for Anesthesiologists/CRNAs to use to develop an anesthesia plan for upcoming surgeries based on patient data.

# Materials and Method

## Dataset Description

This project is being implemented via Jupyter Notebook. The VitalDB dataset has a Python Library containing all relevant data. The dataset has multiple subsets, with the most prominent being the clinical data. The clinical data dataset contains all patient records with key information such as height, weight, age, surgery type, along with a number of preoperative vital signs. It additionally contains intraoperative anesthesia data (more on this in results)

The dataset additionally has 'tracks' for a number of different drugs and stats during the surgery, giving injection rates and volume given throughout a surgery. This has resulted in part of the issue with the project thus far, as these tracks do not necessarily agree with drug amounts given in the clinical dataset. The dataset descriptions do not address these differences, and so after looking through both I have come to the assumption that drug amounts given in the clincal dataset (which are simply given in lump sum amounts) are related to the induction means (i.e. drugs given to put the patient unconscious initially) while the track amounts are the amount given throughout the surgery to maintain the sedation levels.

## Method

After data exploration, my intention was to use different classification/regression models from scikit-learn's python library to train multiple models that could make predictions for different drug amounts given patient data. More discussion on this in results/progress

# Research Results/Progress

## Data Exploration

Looking through the data, there are mixed results. I have analyzed/compensated for NAN values as well as looked through for correlations and drug amounts. Some commentary on those below.

### Correlation Heatmap

The following correlation heat map shows overall weak correlation throughout the dataset. This will obviously lead to difficulty in proper drug prediction.

HEATMAP HERE

### Histograms

The following drug histograms show that there is some stark variation in whether or not certain drugs are used, which will further complicate anesthesia plan development

Propofol Histogram
PPF HISTOGRAM

Rocuronium Histogram
OTHER HISTOGRAM

## Model Accuracy

When attempting to predict drug amounts based on patient data, I started by using various regression models (Linear Regression, Lasso, RandomForestRegressor). These models had poor accuracy, with high RMSE values and low R2 values. Looking at the data, I decided to shift my approach: instead of recommend, for example 34mg of propofol for a given induction, instead recommending bins: either >100mg, 1-100mg, or 0mg of propofol. Taking the regression problem and making it more of a classification problem has improved accuracy (>60% now, still could use a lot of work but better than before), and I believe is still consistent with the goal of the project, as an AI generated anesthesia plan should be a jumping off point for an anesthesiologist or CRNA, not necessarily a perfect product.

Overall, there is still more refinement to do, and I would still like to incorporate the maintenance plan, but I am encouraged by the pivot in approach.

# Remaining Tasks and Next Steps

I still have to develop the chatbot and then integrate the chatbot with the prediction models. Per my initial proposal timeline, my goal was to be done with all prediction models by this point. Based on the accuracy still needing improvement as well as the maintenance plan prediction development still needing work, I would say I am currently behind schedule. A portion of this is due to the dataset limitations, as it took me longer than I expected to work through how all the data related. However, I am encouraged by my recent developments and expect to be on track within the next two weeks.

My current goal is to finish prediction modeling this week and start looking into chatbot development, finishing the simple chatbot next week and making sure the two are fully integrated by 20 April, giving me enough time to clean up any issues and finish the project recording in time.
