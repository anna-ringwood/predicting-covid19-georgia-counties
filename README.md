# A Predictive Model for COVID-19 Death Rates in Georgia Counties

In the United States, communities of color and those of lower economic status have long been subject to significantly lower-quality healthcare, and these same patterns have been highlighted with the onset of the COVID-19 pandemic. Thus, many researchers have conducted investigations into where these disparities occur and how they affect COVID-19-related outcomes.

A study done on the socio-economic disparities and COVID-19 in the U.S. concluded that the disparities primarily affect racial and ethnic minorities, an occurrence which is “particularly true for the southern states.” These disparities include the “stereotyping of race and ethnicity within the healthcare system since studies show that racial minorities have been “disproportionately affected” by COVID-19 starting from the newly developing stages of the pandemic. (Paul et al.)

Since the greater distribution of socio-economic, environmental, and structural resources have shown to help in containing the disease, it is important that these health inequities are addressed among racial minorities with most cities and states not reporting race along with case and fatality counts/rates. (Kullar et al.)

Therefore, this study aims to derive a predictive model of COVID-19 death rates in Georgia counties using health behavior, social, economic, and environmental predictor variables. We hope that our model will highlight certain variables which exacerbate death rates to a greater extent, so that those factors can be the focus of local and federal intervention.

## Methods

Data was obtained from three publicly-available sources:
* The 2020 County Health Rankings (CHR) report for the state of Georgia contains socioeconomic and health behavior data at the county level, reported as percentages of county populations.
* The American Community Survey (ACS) 2015-2019 5-Year Data Profiles contain county-level raw estimates, percentages, and margins of error for social, economic, housing, and demographic variables. From these, the percent estimate for each measure was extracted. 
* The Georgia Department of Public Health (DPH) provides daily records of the state’s COVID-19 cases, deaths, and tests since February 1, 2020, via its COVID-19 Daily Status Report. Data at the county level was retrieved on April 24, 2021.

Missing data was present only in the data set from the CHR (M=0.61%, SD=1.58%). After removing variables missing more than 10% of total observations, a random forest iterative imputation method, missForest, was used to address the remaining missing observations.

From the CHR, 58 predictor variables were extracted, 16 of which contained imputed data. From the ACS data sets, 501 variables were extracted, none of which contained missing data.

Multiple lasso regressions were conducted using the glmnet method with COVID-19 deaths per 100,000 people as the outcome variable. The resulting models were evaluated using R-squared values, root mean squared error (RMSE) values, and total number of final predictors. One of these models is presented here.

## Results and Discussion

The present model indicates that the percentage of adults who have had some college education and the percentage of infants with a low birth weight have the greatest predictive capacity for COVID-19 death rates.

The model was able to account for 37.1% of the overall variance in the COVID-19 death rates. More absolutely, the predictions made by our model are generally off by approximately 88 deaths per 100,000 people.

The predictive model indicated 12 predictors that impact COVID-19 death rates in Georgia counties, and accounts for nearly 40% of the variance in death rates. These 12 variables are:
* College Enrollment Rate (percentage of adults aged 25-44 with at least some college education)
* Low Birth Weight Rate
* Children in Poverty Rate
* Single-Parent Household Rate
* Frequency of Housing Problems (percentage of households with at least one of these housing problems: overcrowding, high housing costs, lack of kitchen facilities, lack of plumbing facilities.)
* Life Expectancy (years)
* Social Associations per 10,000 people
* Limited Healthy Food Access Rate
* Number of Premature Deaths
* High School Graduation Rate
* Physical Inactivity Rate
* Free or Reduced Lunch Enrollment Rate

Of the 12 variables, the prevalence of low birth weight is related most positively with death rates, and the rate of adults with at least some college education is related most negatively. As low birth weight is often considered an indicator of health behaviors, it is to be expected that this variable would be involved in a county’s COVID-19 death rate. Further, because discussion of the pandemic has taken place primarily in a technical, scientific context, the negative correlation between college enrollment (and subsequently education level) is also a reasonable inclusion in the model, as a lesser amount of education can prevent individuals from fully understanding topics discussed in this manner.

A surprising result is the absence of an explicitly race-related variable in the final model. The variables highlighted by the model all relate most closely to lifestyle areas such as health and socioeconomics, but it is important to recognize that these factors are often heavily correlated with variables such as race and ethnicity. Thus, to assume that race is inherently present in the model is not unreasonable.

In the future, we would like to conduct a factor analysis on the predictors included in the present model. Such an analysis would provide insight into the broader areas of living that impact COVID-19 death rates.

In addition, this model is only one of four that were obtained through lasso regression. A comparison of all four models would allow patterns to be discerned regarding which predictors are consistently included in the resulting models and potentially inform the development of a new model that is more generalizable or has greater power.

## Acknowledgements

The authors would like to acknowledge and thank Dr. Ben Miller (*Emory Writing Program, Emory University*) for his direction on outlining, drafting, refining, and presenting the results of a data analysis project. They would also like to acknowledge and thank Dr. Kevin McAlister (*Quantitative Theory and Methods, Emory University*) for his guidance and assistance in the data analysis for this project.

## References

Georgia Department of Public Health. (n.d.). *COVID-19 Status Report*. Retrieved April 5, 2021, from https://dph.georgia.gov/covid-19-daily-status-report

Karmakar, M., Lantz, P. M., & Tipirneni, R. (2021). Association of social and demographic factors With COVID-19 incidence and death rates in the us. *JAMA network open, 4*(1), 
https://www.doi.org/10.1001/jamanetworkopen.2020.36462

Kullar, R., Marcelin, J. R., Swartz, T. H., Piggott, D. A., Macias Gil, R., Mathew, T. A., Tan, T., & on behalf of the Infectious Diseases Society of America Inclusion, D., Access, and Equity Task Force. (2020). Racial Disparity of Coronavirus Disease 2019 in African American Communities. *The Journal of Infectious Diseases, 222*(6), 890–893. https://doi.org/10.1093/infdis/jiaa372

Paul, A., Englert, P., & Varga, M. (2020). Socio-economic disparities and COVID-19 in the USA. *MedRxiv*, 2020.09.10.20192138. https://doi.org/10.1101/2020.09.10.20192138

Stekhoven, Daniel J. (2013). missForest: Nonparametric Missing Value Imputation using Random Forest. R package version 1.4.

U.S. Census Bureau. (n.d.). *Data Profiles*. https://www.census.gov/acs/www/data/data-tables-and-tools/data-profiles/2019/

U.S. Census Bureau. (2020, October 16). *The Importance of the American Community Survey and the 2020 Census*. https://www.census.gov/programs-surveys/acs/about/acs-and-census.html
