Project Description:
This project analyzes the relationship between Systemic Immune Inflammation (SII) and cognitive function/cortical thickness in HIV+ and HIV- individuals.

Required Dataset must include the following variables:
→ HIV status; where 0 == negative and 1 == positive
→ Sex; where 0 == male and 1 == female 
→ Age
→ Cognitive Z-scores (Learning, Delayed Recall, Executive Function, Processing Memory,  Language, Total)
→ Cortical thickness measures (Frontal, Parietal, Temporal, Occipital, Mean)

Output:
→ data_clean.csv
→ Blood_work_error_check.png
→ boxplot_SII_by_HIV_Status.png
→ SII_Cortical_Frontal_Thickness_HIV.png
→ SII_Cortical_Mean_Thickness_HIV.png
→ SII_Cortical_Occipital_Thickness_HIV.png
→ SII_Cortical_Parietal_Thickness_HIV.png
→ SII_Cortical_Temporal_Thickness_HIV.png

Steps of Analysis: 
1. Data Preparation/Organization
→ Potential identifying information is removed: (study_id, redcap_event_name, related_study_id)
→ Duplicates are dropped with priority being given to blood count not being null
→ Identified outliers in blood count assuming data entry by hand 
→ Unusual blood count values are dropped
→ SII is computed and appended as a new column:
                                        SII = Platelets x NeutrophilsLymphocytes
2. Demographics Analysis
	→ T-test is performed to identify any age related biases between HIV groups
	→ Chi-square test is done on gender to identify biases in our dataset 
            → Using ols, a linear regression model is performed and used create an ANOVA  table
                 which compares  SII in patients HIV+ and HIV-; while controlling for sex and age by          
     designating these covariates as constants 
            → A boxplot comparing HIV status and SII will be produced in an output folder 

3. Analysis of Cognitive Function 
	→ Data is split into HIV+ and HIV- groups, each its own variable  
	→ Within a for loop, Z-columns are placed into an array and null values are dropped for 
	      either the z column or SII. Pearson correlation function for negative and positive are
	      calculated. If the p value is significant, **, will be displayed as an indicator 

4. Analysis of Cortical Thickness
	→ Data is split into HIV+ and HIV- groups, each its own variable 
	→ Within a for loop, Cortical thickness columns are placed into an array and null values   
	     are dropped. 
	→ A linear regression model is done for each category (HIV+/HIV-), with the predictor
	     of interest being SII’s effect on cortical thickness 
→ Independent variable, SII is plotted on the x-axis and dependent cortical thickness is 
     plotted on the y-axis alongside the actual values

Requirements:
The following libraries/API support should support python version 3.9 and greater
→ pandas
→ numpy
→ scipy
→ statsmodels
→ matplotlib
→ seaborn

How to Run:
In the jupyter notebook, load in the dataset of interest, select run all. All analysis will be generated automatically. 
 
Author: Noor Albhadli 
Date: December 2025


