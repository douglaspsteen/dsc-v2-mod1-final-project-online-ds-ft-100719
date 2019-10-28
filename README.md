<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Final-Project-Submission" data-toc-modified-id="Final-Project-Submission-0.1">Final Project Submission</a></span></li></ul></li><li><span><a href="#PROJECT-OVERVIEW" data-toc-modified-id="PROJECT-OVERVIEW-1">PROJECT OVERVIEW</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#The-objective-of-this-project-is-to-use-the-King-County-house-dataset-to-produce-a-multiple-linear-regression-model-to-predict-sale-prices.-The-motivation-behind-this-study-is-to-help-homeowners-identify-areas-in-which-they-can-maximize-profts-when-selling-their-homes." data-toc-modified-id="The-objective-of-this-project-is-to-use-the-King-County-house-dataset-to-produce-a-multiple-linear-regression-model-to-predict-sale-prices.-The-motivation-behind-this-study-is-to-help-homeowners-identify-areas-in-which-they-can-maximize-profts-when-selling-their-homes.-1.0.1">The objective of this project is to use the King County house dataset to produce a multiple linear regression model to predict sale prices. The motivation behind this study is to help homeowners identify areas in which they can maximize profts when selling their homes.</a></span></li><li><span><a href="#First,-I-import-the-relevant-python-libraries-and-dataset,-inspect-the-data,-and-remove-extraneous-information-from-the-dataset." data-toc-modified-id="First,-I-import-the-relevant-python-libraries-and-dataset,-inspect-the-data,-and-remove-extraneous-information-from-the-dataset.-1.0.2">First, I import the relevant python libraries and dataset, inspect the data, and remove extraneous information from the dataset.</a></span></li><li><span><a href="#Second,-I-scrub-the-data-to-address-null,-missing,-and-placeholder-values,-while-deciding-how-to-handle-categorical-variables-and-inspecting-variables-for-multicollinearity.-During-the-scrub-phase,-I-use-the-latitude-and-longitude-information-to-engineer-a-new-feature-representing-the-distance-each-home-from-downtown-Seattle." data-toc-modified-id="Second,-I-scrub-the-data-to-address-null,-missing,-and-placeholder-values,-while-deciding-how-to-handle-categorical-variables-and-inspecting-variables-for-multicollinearity.-During-the-scrub-phase,-I-use-the-latitude-and-longitude-information-to-engineer-a-new-feature-representing-the-distance-each-home-from-downtown-Seattle.-1.0.3">Second, I scrub the data to address null, missing, and placeholder values, while deciding how to handle categorical variables and inspecting variables for multicollinearity. During the scrub phase, I use the latitude and longitude information to engineer a new feature representing the distance each home from downtown Seattle.</a></span></li><li><span><a href="#Third,-I-explore-the-scrubbed-data-by-visualizing-distributions,-linearity-between-variables,-and-detection-of-outliers-using-an-IQR-score-method.-During-the-explore-phase,-I-also-perform-one-hot-encoding-for-several-variables,-logarithmically-transform-two-variables,-and-set-all-independent-numerical-variables-to-the-same-min-max-scale." data-toc-modified-id="Third,-I-explore-the-scrubbed-data-by-visualizing-distributions,-linearity-between-variables,-and-detection-of-outliers-using-an-IQR-score-method.-During-the-explore-phase,-I-also-perform-one-hot-encoding-for-several-variables,-logarithmically-transform-two-variables,-and-set-all-independent-numerical-variables-to-the-same-min-max-scale.-1.0.4">Third, I explore the scrubbed data by visualizing distributions, linearity between variables, and detection of outliers using an IQR score method. During the explore phase, I also perform one-hot encoding for several variables, logarithmically transform two variables, and set all independent numerical variables to the same min-max scale.</a></span></li><li><span><a href="#Fourth,-I-use-recursive-feature-elimination-(RFE)-to-determine-the-most-important-features-in-my-initial-model,-and-use-plots-of-r-squared-and-mean-squared-error-(MSE)-to-determine-the-ideal-number-of-features-to-select-for-linear-regression.-During-the-model-phase,-I-use-these-selected-features-in-the-statsmodels-OLS-function-to-create-an-initial-model." data-toc-modified-id="Fourth,-I-use-recursive-feature-elimination-(RFE)-to-determine-the-most-important-features-in-my-initial-model,-and-use-plots-of-r-squared-and-mean-squared-error-(MSE)-to-determine-the-ideal-number-of-features-to-select-for-linear-regression.-During-the-model-phase,-I-use-these-selected-features-in-the-statsmodels-OLS-function-to-create-an-initial-model.-1.0.5">Fourth, I use recursive feature elimination (RFE) to determine the most important features in my initial model, and use plots of r-squared and mean squared error (MSE) to determine the ideal number of features to select for linear regression. During the model phase, I use these selected features in the statsmodels OLS function to create an initial model.</a></span></li><li><span><a href="#Finally,-I-revise-the-initial-model-by-(1)-checking-for-missed-non-linearity-in-variables,-(2)-including-zip-codes-in-the-revised-linear-regression-model,-and-(3)-using-the-simple-linear-regression-of-each-variable-against-the-target-as-a-means-for-feature-selection-in-the-revised-linear-regression-model,-instead-of-RFE." data-toc-modified-id="Finally,-I-revise-the-initial-model-by-(1)-checking-for-missed-non-linearity-in-variables,-(2)-including-zip-codes-in-the-revised-linear-regression-model,-and-(3)-using-the-simple-linear-regression-of-each-variable-against-the-target-as-a-means-for-feature-selection-in-the-revised-linear-regression-model,-instead-of-RFE.-1.0.6">Finally, I revise the initial model by (1) checking for missed non-linearity in variables, (2) including zip codes in the revised linear regression model, and (3) using the simple linear regression of each variable against the target as a means for feature selection in the revised linear regression model, instead of RFE.</a></span></li></ul></li></ul></li><li><span><a href="#OBTAIN" data-toc-modified-id="OBTAIN-2">OBTAIN</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Import-relevant-libraries-and-data" data-toc-modified-id="Import-relevant-libraries-and-data-2.0.1">Import relevant libraries and data</a></span></li><li><span><a href="#Removing-the-'id'-and-'date'-columns,-as-they-will-not-be-relevant-to-the-regression" data-toc-modified-id="Removing-the-'id'-and-'date'-columns,-as-they-will-not-be-relevant-to-the-regression-2.0.2">Removing the 'id' and 'date' columns, as they will not be relevant to the regression</a></span></li></ul></li></ul></li><li><span><a href="#SCRUB" data-toc-modified-id="SCRUB-3">SCRUB</a></span><ul class="toc-item"><li><span><a href="#ADDRESS-NULL/MISSING-VALUES-AND-POTENTIAL-CATEGORICAL-VARIABLES" data-toc-modified-id="ADDRESS-NULL/MISSING-VALUES-AND-POTENTIAL-CATEGORICAL-VARIABLES-3.1">ADDRESS NULL/MISSING VALUES AND POTENTIAL CATEGORICAL VARIABLES</a></span><ul class="toc-item"><li><span><a href="#Get-an-overview-of-all-columns-using-check_column-function" data-toc-modified-id="Get-an-overview-of-all-columns-using-check_column-function-3.1.1">Get an overview of all columns using check_column function</a></span></li><li><span><a href="#CONCLUSIONS-ON-NULL/MISSING-VALUES:" data-toc-modified-id="CONCLUSIONS-ON-NULL/MISSING-VALUES:-3.1.2">CONCLUSIONS ON NULL/MISSING VALUES:</a></span><ul class="toc-item"><li><span><a href="#--'waterfront'---Lots-of-null-values.-STRATEGY:-Replace-null-values-with-most-common-value,-0.0" data-toc-modified-id="--'waterfront'---Lots-of-null-values.-STRATEGY:-Replace-null-values-with-most-common-value,-0.0-3.1.2.1">- 'waterfront' - Lots of null values. STRATEGY: Replace null values with most common value, 0.0</a></span></li><li><span><a href="#-'view'---Some-null-values.-STRATEGY:-Replace-null-values-with-most-common-value,-0.0" data-toc-modified-id="-'view'---Some-null-values.-STRATEGY:-Replace-null-values-with-most-common-value,-0.0-3.1.2.2">-'view' - Some null values. STRATEGY: Replace null values with most common value, 0.0</a></span></li><li><span><a href="#-'yr_renovated'---Lots-of-null-values,-column-entries-mostly-have-value-of-0.0.-STRATEGY:-Drop-entire-column-from-dataset" data-toc-modified-id="-'yr_renovated'---Lots-of-null-values,-column-entries-mostly-have-value-of-0.0.-STRATEGY:-Drop-entire-column-from-dataset-3.1.2.3">-'yr_renovated' - Lots of null values, column entries mostly have value of 0.0. STRATEGY: Drop entire column from dataset</a></span></li><li><span><a href="#-'sqft_basement'---Placeholder-variable-'?'.-STRATEGY:-Replace-'?'-with-most-common-value,-0.0" data-toc-modified-id="-'sqft_basement'---Placeholder-variable-'?'.-STRATEGY:-Replace-'?'-with-most-common-value,-0.0-3.1.2.4">-'sqft_basement' - Placeholder variable '?'. STRATEGY: Replace '?' with most common value, 0.0</a></span></li></ul></li><li><span><a href="#Replace-identified-null-values,-remove-'yr_renovated'-column,-change-'sqft_basement'-to-categorical" data-toc-modified-id="Replace-identified-null-values,-remove-'yr_renovated'-column,-change-'sqft_basement'-to-categorical-3.1.3">Replace identified null values, remove 'yr_renovated' column, change 'sqft_basement' to categorical</a></span></li><li><span><a href="#CONCLUSIONS-ON-CATEGORICAL-VARIABLES-&amp;-DATA-TYPES" data-toc-modified-id="CONCLUSIONS-ON-CATEGORICAL-VARIABLES-&amp;-DATA-TYPES-3.1.4">CONCLUSIONS ON CATEGORICAL VARIABLES &amp; DATA TYPES</a></span><ul class="toc-item"><li><span><a href="#--'sqft_basement'---I-want-to-re-cast-as-categorical.-STRATEGY:-Convert-to-a-categorical-variable-(0-=-no-basement,-1-=-has-basement)" data-toc-modified-id="--'sqft_basement'---I-want-to-re-cast-as-categorical.-STRATEGY:-Convert-to-a-categorical-variable-(0-=-no-basement,-1-=-has-basement)-3.1.4.1">- 'sqft_basement' - I want to re-cast as categorical. STRATEGY: Convert to a categorical variable (0 = no basement, 1 = has basement)</a></span></li><li><span><a href="#--'waterfront',-'view',-'condition',-should-be-categorical-variables.-STRATEGY:-Convert-these-to-categorical-variables" data-toc-modified-id="--'waterfront',-'view',-'condition',-should-be-categorical-variables.-STRATEGY:-Convert-these-to-categorical-variables-3.1.4.2">- 'waterfront', 'view', 'condition', should be categorical variables. STRATEGY: Convert these to categorical variables</a></span></li></ul></li></ul></li><li><span><a href="#FEATURE-ENGINEERING:-DISTANCE-FROM-DOWNTOWN-SEATTLE-(dist_dt)" data-toc-modified-id="FEATURE-ENGINEERING:-DISTANCE-FROM-DOWNTOWN-SEATTLE-(dist_dt)-3.2">FEATURE ENGINEERING: DISTANCE FROM DOWNTOWN SEATTLE (dist_dt)</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Using-lat_lon_dist_calc-function-to-calculate-distance-from-observation-to-downtown-Seattle" data-toc-modified-id="Using-lat_lon_dist_calc-function-to-calculate-distance-from-observation-to-downtown-Seattle-3.2.0.1">Using lat_lon_dist_calc function to calculate distance from observation to downtown Seattle</a></span></li><li><span><a href="#I-am-using-this-feature-to-replace-the-'lat',-'long',-and-'zipcode'-columns-as-I-believe-it-will-capture-information-from-all-three" data-toc-modified-id="I-am-using-this-feature-to-replace-the-'lat',-'long',-and-'zipcode'-columns-as-I-believe-it-will-capture-information-from-all-three-3.2.0.2">I am using this feature to replace the 'lat', 'long', and 'zipcode' columns as I believe it will capture information from all three</a></span></li><li><span><a href="#I-hypothesize-that-there-will-be-a-decreasing-relationship-with-price-as-dist_dt-increases" data-toc-modified-id="I-hypothesize-that-there-will-be-a-decreasing-relationship-with-price-as-dist_dt-increases-3.2.0.3">I hypothesize that there will be a decreasing relationship with price as dist_dt increases</a></span></li></ul></li><li><span><a href="#Question-#1:-Do-any-features-display-high-collinearity-(>0.75)-that-should-be-removed-before-modeling?" data-toc-modified-id="Question-#1:-Do-any-features-display-high-collinearity-(>0.75)-that-should-be-removed-before-modeling?-3.2.1">Question #1: Do any features display high collinearity (&gt;0.75) that should be removed before modeling?</a></span></li><li><span><a href="#ASSESS-MULTICOLLINEARITY-OF-FEATURES" data-toc-modified-id="ASSESS-MULTICOLLINEARITY-OF-FEATURES-3.2.2">ASSESS MULTICOLLINEARITY OF FEATURES</a></span></li><li><span><a href="#Question-#1-Answer:-Multicollinearity-observaions" data-toc-modified-id="Question-#1-Answer:-Multicollinearity-observaions-3.2.3">Question #1 Answer: Multicollinearity observaions</a></span><ul class="toc-item"><li><span><a href="#--sqft_living-is-highly-correlated-(R->-0.75)-to-sqft_above,-bathrooms,-grade,-sqft_living15" data-toc-modified-id="--sqft_living-is-highly-correlated-(R->-0.75)-to-sqft_above,-bathrooms,-grade,-sqft_living15-3.2.3.1">- sqft_living is highly correlated (R &gt; 0.75) to sqft_above, bathrooms, grade, sqft_living15</a></span></li><li><span><a href="#-Since-it-is-highly-correlated-to-many-other-variables,-it-makes-sense-to-remove-sqft_living-before-proceeding-with-regression" data-toc-modified-id="-Since-it-is-highly-correlated-to-many-other-variables,-it-makes-sense-to-remove-sqft_living-before-proceeding-with-regression-3.2.3.2">-Since it is highly correlated to many other variables, it makes sense to remove sqft_living before proceeding with regression</a></span></li></ul></li><li><span><a href="#Removal-of-collinear-features-for-scrubbed-df" data-toc-modified-id="Removal-of-collinear-features-for-scrubbed-df-3.2.4">Removal of collinear features for scrubbed df</a></span></li><li><span><a href="#SUMMARY-OF-INITIAL-DATA-SCRUB:" data-toc-modified-id="SUMMARY-OF-INITIAL-DATA-SCRUB:-3.2.5">SUMMARY OF INITIAL DATA SCRUB:</a></span><ul class="toc-item"><li><span><a href="#--Variables-dropped-from-dataset:" data-toc-modified-id="--Variables-dropped-from-dataset:-3.2.5.1">- Variables dropped from dataset:</a></span></li><li><span><a href="#--Variables-left-as-continuous-numerical:" data-toc-modified-id="--Variables-left-as-continuous-numerical:-3.2.5.2">- Variables left as continuous numerical:</a></span></li><li><span><a href="#--Variables-added-through-feature-engineering-as-continuous-numerical:" data-toc-modified-id="--Variables-added-through-feature-engineering-as-continuous-numerical:-3.2.5.3">- Variables added through feature engineering as continuous numerical:</a></span></li><li><span><a href="#--Variables-to-be-treated-as-categorical-using-cat.codes:" data-toc-modified-id="--Variables-to-be-treated-as-categorical-using-cat.codes:-3.2.5.4">- Variables to be treated as categorical using cat.codes:</a></span></li></ul></li></ul></li></ul></li><li><span><a href="#EXPLORE" data-toc-modified-id="EXPLORE-4">EXPLORE</a></span><ul class="toc-item"><li><span><a href="#VISUALIZING-DISTRIBUTIONS-AND-SCATTER-PLOTS" data-toc-modified-id="VISUALIZING-DISTRIBUTIONS-AND-SCATTER-PLOTS-4.1">VISUALIZING DISTRIBUTIONS AND SCATTER PLOTS</a></span><ul class="toc-item"><li><span><a href="#Question-#2:-Can-variable-distributions-be-improved-by-objective-outlier-detection-and-removal?" data-toc-modified-id="Question-#2:-Can-variable-distributions-be-improved-by-objective-outlier-detection-and-removal?-4.1.1">Question #2: Can variable distributions be improved by objective outlier detection and removal?</a></span></li></ul></li><li><span><a href="#OUTLIER-DETECTION-AND-REMOVAL" data-toc-modified-id="OUTLIER-DETECTION-AND-REMOVAL-4.2">OUTLIER DETECTION AND REMOVAL</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Outlier-detection-performed-using-IQR-Scores" data-toc-modified-id="Outlier-detection-performed-using-IQR-Scores-4.2.0.1">Outlier detection performed using IQR Scores</a></span></li><li><span><a href="#All-outliers-identified-using-IQR-+/--1.5-for-non-categorical-variables-have-now-been-removed,-and-stored-in-new-df-(df_out_rem)." data-toc-modified-id="All-outliers-identified-using-IQR-+/--1.5-for-non-categorical-variables-have-now-been-removed,-and-stored-in-new-df-(df_out_rem).-4.2.0.2">All outliers identified using IQR +/- 1.5 for non-categorical variables have now been removed, and stored in new df (df_out_rem).</a></span></li></ul></li><li><span><a href="#Question-#2-Answer:-Yes,-'price',-'bedrooms',-'bathrooms',-'sqft_lot',-'sqft_above',-'sqft_living15',-'sqft_lot15',-and-'dist_dt'-are-much-more-normally-distributed-after-outlier-detection-and-removal." data-toc-modified-id="Question-#2-Answer:-Yes,-'price',-'bedrooms',-'bathrooms',-'sqft_lot',-'sqft_above',-'sqft_living15',-'sqft_lot15',-and-'dist_dt'-are-much-more-normally-distributed-after-outlier-detection-and-removal.-4.2.1">Question #2 Answer: Yes, 'price', 'bedrooms', 'bathrooms', 'sqft_lot', 'sqft_above', 'sqft_living15', 'sqft_lot15', and 'dist_dt' are much more normally distributed after outlier detection and removal.</a></span></li><li><span><a href="#Question-#3:-After-outlier-removal,-would-any-features-benefit-from-log-transformation?" data-toc-modified-id="Question-#3:-After-outlier-removal,-would-any-features-benefit-from-log-transformation?-4.2.2">Question #3: After outlier removal, would any features benefit from log transformation?</a></span></li><li><span><a href="#Question-#3-Answer:-Yes,-both-'sqft_above'-and-'sqft_living15'-both-have-more-normal-distributions-after-log-transformation." data-toc-modified-id="Question-#3-Answer:-Yes,-both-'sqft_above'-and-'sqft_living15'-both-have-more-normal-distributions-after-log-transformation.-4.2.3">Question #3 Answer: Yes, both 'sqft_above' and 'sqft_living15' both have more normal distributions after log transformation.</a></span></li></ul></li><li><span><a href="#ONE-HOT-ENCODING-OF-CATEGORICAL-VARIABLES" data-toc-modified-id="ONE-HOT-ENCODING-OF-CATEGORICAL-VARIABLES-4.3">ONE-HOT ENCODING OF CATEGORICAL VARIABLES</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Need-to-do-this-for-all-categoricals-before-performing-regression" data-toc-modified-id="Need-to-do-this-for-all-categoricals-before-performing-regression-4.3.0.1">Need to do this for all categoricals before performing regression</a></span></li><li><span><a href="#--'basement_coded'-and-'wf_coded'-are-already-in-the-correct-format" data-toc-modified-id="--'basement_coded'-and-'wf_coded'-are-already-in-the-correct-format-4.3.0.2">- 'basement_coded' and 'wf_coded' are already in the correct format</a></span></li><li><span><a href="#--Use-pandas-to-get-dummy-variables-for-'view_coded'-and-'cond_coded'" data-toc-modified-id="--Use-pandas-to-get-dummy-variables-for-'view_coded'-and-'cond_coded'-4.3.0.3">- Use pandas to get dummy variables for 'view_coded' and 'cond_coded'</a></span></li></ul></li></ul></li><li><span><a href="#MIN/MAX-SCALING-OF-FEATURES" data-toc-modified-id="MIN/MAX-SCALING-OF-FEATURES-4.4">MIN/MAX SCALING OF FEATURES</a></span></li></ul></li><li><span><a href="#MODEL" data-toc-modified-id="MODEL-5">MODEL</a></span><ul class="toc-item"><li><span><a href="#RECURSIVE-FEATURE-ELIMINATION-(RFE)---INITIAL-MODEL" data-toc-modified-id="RECURSIVE-FEATURE-ELIMINATION-(RFE)---INITIAL-MODEL-5.1">RECURSIVE FEATURE ELIMINATION (RFE) - INITIAL MODEL</a></span><ul class="toc-item"><li><span><a href="#Now-I-want-to-compare-r^2-to-MSE-as-I-increase-#-of-features,-to-find-point-of-diminishing-returns" data-toc-modified-id="Now-I-want-to-compare-r^2-to-MSE-as-I-increase-#-of-features,-to-find-point-of-diminishing-returns-5.1.1">Now I want to compare r^2 to MSE as I increase # of features, to find point of diminishing returns</a></span></li><li><span><a href="#The-above-R-squared-and-MSE-'elbow'-plots-indicate-that-I-can-safely-select-5-as-the-number-of-features.-Below-I-am-using-the-most-important-5-features-for-linear-regression-using-statsmodels,-as-indicated-by-RFE." data-toc-modified-id="The-above-R-squared-and-MSE-'elbow'-plots-indicate-that-I-can-safely-select-5-as-the-number-of-features.-Below-I-am-using-the-most-important-5-features-for-linear-regression-using-statsmodels,-as-indicated-by-RFE.-5.1.2">The above R-squared and MSE 'elbow' plots indicate that I can safely select 5 as the number of features. Below I am using the most important 5 features for linear regression using statsmodels, as indicated by RFE.</a></span></li><li><span><a href="#Initial-model-uses-the-following-five-features:-'sqft_living15_log',-'dist_dt',-'sqft_above_log',-'view_4',-and-'grade'" data-toc-modified-id="Initial-model-uses-the-following-five-features:-'sqft_living15_log',-'dist_dt',-'sqft_above_log',-'view_4',-and-'grade'-5.1.3">Initial model uses the following five features: 'sqft_living15_log', 'dist_dt', 'sqft_above_log', 'view_4', and 'grade'</a></span><ul class="toc-item"><li><span><a href="#-R-squared-=-0.59-(R-squared-and-adj-R-squared-are-identical)" data-toc-modified-id="-R-squared-=-0.59-(R-squared-and-adj-R-squared-are-identical)-5.1.3.1">-R-squared = 0.59 (R-squared and adj-R-squared are identical)</a></span></li><li><span><a href="#-p-value-=-0.00" data-toc-modified-id="-p-value-=-0.00-5.1.3.2">-p-value = 0.00</a></span></li><li><span><a href="#-Skewness-and-kurtosis-values-indicate-that-the-distribution-of-residuals-is-likely-normal-and-homoscedastic" data-toc-modified-id="-Skewness-and-kurtosis-values-indicate-that-the-distribution-of-residuals-is-likely-normal-and-homoscedastic-5.1.3.3">-Skewness and kurtosis values indicate that the distribution of residuals is likely normal and homoscedastic</a></span></li></ul></li></ul></li></ul></li><li><span><a href="#iNTERPRET" data-toc-modified-id="iNTERPRET-6">iNTERPRET</a></span><ul class="toc-item"><li><span><a href="#CHECK-MODEL-AGAINST-LINEAR-REGRESSION-ASSUMPTIONS" data-toc-modified-id="CHECK-MODEL-AGAINST-LINEAR-REGRESSION-ASSUMPTIONS-6.1">CHECK MODEL AGAINST LINEAR REGRESSION ASSUMPTIONS</a></span><ul class="toc-item"><li><span><a href="#1)-Assess-normality-of-Residuals-using-Histograms-and-Q-Q-Plots" data-toc-modified-id="1)-Assess-normality-of-Residuals-using-Histograms-and-Q-Q-Plots-6.1.1">1) Assess normality of Residuals using Histograms and Q-Q Plots</a></span></li><li><span><a href="#2)-Assess-Heteroscedasticity-of-Residuals" data-toc-modified-id="2)-Assess-Heteroscedasticity-of-Residuals-6.1.2">2) Assess Heteroscedasticity of Residuals</a></span></li><li><span><a href="#CONCLUSION:-It-appears-the-assumptions-of-linear-regression-are-not-violated.-The-Q-Q-plot-and-histogram-of-residuals-indicate-some-right-skew,-but-this-does-not-seem-alarming.-The-model-residuals-appear-to-be-homoscedastic." data-toc-modified-id="CONCLUSION:-It-appears-the-assumptions-of-linear-regression-are-not-violated.-The-Q-Q-plot-and-histogram-of-residuals-indicate-some-right-skew,-but-this-does-not-seem-alarming.-The-model-residuals-appear-to-be-homoscedastic.-6.1.3">CONCLUSION: It appears the assumptions of linear regression are not violated. The Q-Q plot and histogram of residuals indicate some right-skew, but this does not seem alarming. The model residuals appear to be homoscedastic.</a></span></li></ul></li><li><span><a href="#MODEL-VALIDATION" data-toc-modified-id="MODEL-VALIDATION-6.2">MODEL VALIDATION</a></span><ul class="toc-item"><li><span><a href="#Train-Test-Split-Validation" data-toc-modified-id="Train-Test-Split-Validation-6.2.1">Train-Test-Split Validation</a></span><ul class="toc-item"><li><span><a href="#The-Train-and-Test-RMSE's-are-nearly-identical.-This-tells-us-that-our-model-is-not-being-undertrained-or-overtained-on-the-train-test-split---there-is-a-good-balance-here." data-toc-modified-id="The-Train-and-Test-RMSE's-are-nearly-identical.-This-tells-us-that-our-model-is-not-being-undertrained-or-overtained-on-the-train-test-split---there-is-a-good-balance-here.-6.2.1.1">The Train and Test RMSE's are nearly identical. This tells us that our model is not being undertrained or overtained on the train-test-split - there is a good balance here.</a></span></li><li><span><a href="#The-train-test-split-tells-us-that-the-standard-deviation-of-model-residuals-is-about-$122-123k." data-toc-modified-id="The-train-test-split-tells-us-that-the-standard-deviation-of-model-residuals-is-about-$122-123k.-6.2.1.2">The train-test-split tells us that the standard deviation of model residuals is about $122-123k.</a></span></li></ul></li><li><span><a href="#K-fold-Cross-Validation" data-toc-modified-id="K-fold-Cross-Validation-6.2.2">K-fold Cross Validation</a></span><ul class="toc-item"><li><span><a href="#The-k-fold-RMSE-for-10-bins-is-~-$123k,-virtually-identical-to-the-RMSE-from-train-test-split." data-toc-modified-id="The-k-fold-RMSE-for-10-bins-is-~-$123k,-virtually-identical-to-the-RMSE-from-train-test-split.-6.2.2.1">The k-fold RMSE for 10 bins is ~ $123k, virtually identical to the RMSE from train-test-split.</a></span></li></ul></li></ul></li><li><span><a href="#INITIAL-MODEL-SUMMARY" data-toc-modified-id="INITIAL-MODEL-SUMMARY-6.3">INITIAL MODEL SUMMARY</a></span><ul class="toc-item"><li><ul class="toc-item"><li><span><a href="#Five-features-selected-('sqft_living15_log',-'dist_dt',-'sqft_above_log',-'view_4',-'grade')-using-sklearn-RFE" data-toc-modified-id="Five-features-selected-('sqft_living15_log',-'dist_dt',-'sqft_above_log',-'view_4',-'grade')-using-sklearn-RFE-6.3.0.1">Five features selected ('sqft_living15_log', 'dist_dt', 'sqft_above_log', 'view_4', 'grade') using sklearn RFE</a></span></li><li><span><a href="#Linear-regression-model-produced-using-these-five-features-in-statsmodels-OLS" data-toc-modified-id="Linear-regression-model-produced-using-these-five-features-in-statsmodels-OLS-6.3.0.2">Linear regression model produced using these five features in statsmodels OLS</a></span></li><li><span><a href="#R-squared-=-0.59" data-toc-modified-id="R-squared-=-0.59-6.3.0.3">R-squared = 0.59</a></span></li><li><span><a href="#Residuals-are-primarily-normally-distributed,-homoscedastic" data-toc-modified-id="Residuals-are-primarily-normally-distributed,-homoscedastic-6.3.0.4">Residuals are primarily normally distributed, homoscedastic</a></span></li><li><span><a href="#RMSE-of-train-test-split-and-k-fold-cross-validation-is-~-$123k" data-toc-modified-id="RMSE-of-train-test-split-and-k-fold-cross-validation-is-~-$123k-6.3.0.5">RMSE of train-test-split and k-fold cross validation is ~ $123k</a></span></li></ul></li></ul></li><li><span><a href="#REVISED-MODEL" data-toc-modified-id="REVISED-MODEL-6.4">REVISED MODEL</a></span><ul class="toc-item"><li><span><a href="#Goal:-See-if-I-can-improve-the-model-r-squared-value-while-reducing-errors,-and-maintaining-predictability-of-the-initial-model." data-toc-modified-id="Goal:-See-if-I-can-improve-the-model-r-squared-value-while-reducing-errors,-and-maintaining-predictability-of-the-initial-model.-6.4.1">Goal: See if I can improve the model r-squared value while reducing errors, and maintaining predictability of the initial model.</a></span></li><li><span><a href="#Strategy:" data-toc-modified-id="Strategy:-6.4.2">Strategy:</a></span></li><li><span><a href="#1)-Check-for-any-missed-non-linearity-between-the-variables-that-could-possibly-be-corrected" data-toc-modified-id="1)-Check-for-any-missed-non-linearity-between-the-variables-that-could-possibly-be-corrected-6.4.3">1) Check for any missed non-linearity between the variables that could possibly be corrected</a></span></li><li><span><a href="#2)-Include-zip-codes-as-a-categorical-variable-in-the-list-of-features-(previously-excluded)" data-toc-modified-id="2)-Include-zip-codes-as-a-categorical-variable-in-the-list-of-features-(previously-excluded)-6.4.4">2) Include zip codes as a categorical variable in the list of features (previously excluded)</a></span></li><li><span><a href="#3)-Instead-of-RFE,-check-simple-linear-regression-for-each-predictor-on-its-own-to-choose-top-5-features" data-toc-modified-id="3)-Instead-of-RFE,-check-simple-linear-regression-for-each-predictor-on-its-own-to-choose-top-5-features-6.4.5">3) Instead of RFE, check simple linear regression for each predictor on its own to choose top 5 features</a></span></li><li><span><a href="#I-don't-see-an-obvious-transformation-to-improve-the-linearity-of-any-features,-so-I-will-move-on-to-step-2." data-toc-modified-id="I-don't-see-an-obvious-transformation-to-improve-the-linearity-of-any-features,-so-I-will-move-on-to-step-2.-6.4.6">I don't see an obvious transformation to improve the linearity of any features, so I will move on to step 2.</a></span></li><li><span><a href="#Revised-model-uses-the-following-five-features:-'zip_coded',-'grade',-'sqft_living_15_log',-'dist_dt',-and-'sqft_above_log'" data-toc-modified-id="Revised-model-uses-the-following-five-features:-'zip_coded',-'grade',-'sqft_living_15_log',-'dist_dt',-and-'sqft_above_log'-6.4.7">Revised model uses the following five features: 'zip_coded', 'grade', 'sqft_living_15_log', 'dist_dt', and 'sqft_above_log'</a></span><ul class="toc-item"><li><span><a href="#-R-squared-=-0.77-(R-squared-and-adj-R-squared-are-almost-identical)" data-toc-modified-id="-R-squared-=-0.77-(R-squared-and-adj-R-squared-are-almost-identical)-6.4.7.1">-R-squared = 0.77 (R-squared and adj-R-squared are almost identical)</a></span></li><li><span><a href="#-p-value-=-0.00" data-toc-modified-id="-p-value-=-0.00-6.4.7.2">-p-value = 0.00</a></span></li><li><span><a href="#-Some-more-skewness-and-kurtosis-than-in-the-initial-model;-I-will-explore-this-below" data-toc-modified-id="-Some-more-skewness-and-kurtosis-than-in-the-initial-model;-I-will-explore-this-below-6.4.7.3">-Some more skewness and kurtosis than in the initial model; I will explore this below</a></span></li></ul></li></ul></li><li><span><a href="#1)-Assess-normality-of-Residuals-using-Histograms-and-Q-Q-Plots" data-toc-modified-id="1)-Assess-normality-of-Residuals-using-Histograms-and-Q-Q-Plots-6.5">1) Assess normality of Residuals using Histograms and Q-Q Plots</a></span><ul class="toc-item"><li><span><a href="#CONCLUSION:-The-histogram-indicates-some-right-skew,-but-this-does-not-seem-alarming.-The-model-residuals-appear-to-be-homoscedastic,-and-the-Q-Q-plot-indicates-that-the-distribution-is-not-quite-normal." data-toc-modified-id="CONCLUSION:-The-histogram-indicates-some-right-skew,-but-this-does-not-seem-alarming.-The-model-residuals-appear-to-be-homoscedastic,-and-the-Q-Q-plot-indicates-that-the-distribution-is-not-quite-normal.-6.5.1">CONCLUSION: The histogram indicates some right-skew, but this does not seem alarming. The model residuals appear to be homoscedastic, and the Q-Q plot indicates that the distribution is not quite normal.</a></span></li><li><span><a href="#REVISED-MODEL-Train-Test-Split-Validation" data-toc-modified-id="REVISED-MODEL-Train-Test-Split-Validation-6.5.2">REVISED MODEL Train-Test-Split Validation</a></span><ul class="toc-item"><li><span><a href="#The-revised-model-Train-and-Test-RMSE's-are-nearly-identical.-This-tells-us-that-our-revised-model-is-not-being-undertrained-or-overtained-on-the-train-test-split---there-is-a-good-balance-here." data-toc-modified-id="The-revised-model-Train-and-Test-RMSE's-are-nearly-identical.-This-tells-us-that-our-revised-model-is-not-being-undertrained-or-overtained-on-the-train-test-split---there-is-a-good-balance-here.-6.5.2.1">The revised model Train and Test RMSE's are nearly identical. This tells us that our revised model is not being undertrained or overtained on the train-test-split - there is a good balance here.</a></span></li><li><span><a href="#The-train-test-split-tells-us-that-the-standard-deviation-of-revised-model-residuals-is-$92-93k." data-toc-modified-id="The-train-test-split-tells-us-that-the-standard-deviation-of-revised-model-residuals-is-$92-93k.-6.5.2.2">The train-test-split tells us that the standard deviation of revised model residuals is $92-93k.</a></span></li></ul></li></ul></li></ul></li><li><span><a href="#CONCLUSIONS-&amp;-RECOMMENDATIONS" data-toc-modified-id="CONCLUSIONS-&amp;-RECOMMENDATIONS-7">CONCLUSIONS &amp; RECOMMENDATIONS</a></span><ul class="toc-item"><li><span><a href="#Conclusion" data-toc-modified-id="Conclusion-7.1">Conclusion</a></span><ul class="toc-item"><li><span><a href="#The-most-important-predictors-of-sales-price-in-King-County-are:-zip-code-('zip_coded'),-construction/design-grade-('grade'),-size-of-neighborhood-interior-living-space-('sqft_living15_log'),-distance-from-downtown-Seattle-('dist_dt'),-and-size-of-house-above-ground-level-('sqft_above_log).-Grade,-size-of-neighborhood-interior-living-space-(log-transformed),-and-size-of-house-above-ground-(log-transformed)-have-a-positive-relationship-with-price.-Distance-from-downtown-Seattle-has-a-negative-relationship-with-price.-Zip-code-is-more-complex-in-interpretation---however,-the-zip-code-in-which-a-home-is-located-is-generally-a-good-predictor-of-price.-These-five-features-together-can-explain-77%-of-the-variability-in-King-County-housing-prices." data-toc-modified-id="The-most-important-predictors-of-sales-price-in-King-County-are:-zip-code-('zip_coded'),-construction/design-grade-('grade'),-size-of-neighborhood-interior-living-space-('sqft_living15_log'),-distance-from-downtown-Seattle-('dist_dt'),-and-size-of-house-above-ground-level-('sqft_above_log).-Grade,-size-of-neighborhood-interior-living-space-(log-transformed),-and-size-of-house-above-ground-(log-transformed)-have-a-positive-relationship-with-price.-Distance-from-downtown-Seattle-has-a-negative-relationship-with-price.-Zip-code-is-more-complex-in-interpretation---however,-the-zip-code-in-which-a-home-is-located-is-generally-a-good-predictor-of-price.-These-five-features-together-can-explain-77%-of-the-variability-in-King-County-housing-prices.-7.1.1">The most important predictors of sales price in King County are: zip code ('zip_coded'), construction/design grade ('grade'), size of neighborhood interior living space ('sqft_living15_log'), distance from downtown Seattle ('dist_dt'), and size of house above ground level ('sqft_above_log). Grade, size of neighborhood interior living space (log transformed), and size of house above ground (log transformed) have a positive relationship with price. Distance from downtown Seattle has a negative relationship with price. Zip code is more complex in interpretation - however, the zip code in which a home is located is generally a good predictor of price. These five features together can explain 77% of the variability in King County housing prices.</a></span></li></ul></li><li><span><a href="#Recommendations" data-toc-modified-id="Recommendations-7.2">Recommendations</a></span><ul class="toc-item"><li><span><a href="#While-zip-code-and-distance-from-downtown-Seattle-are-factors-that-are-largely-outside-of-homeowners'-control,-they-could-ensure-that-desireable-locations-are-emphasized-during-the-selling-process.-Homeowners-looking-to-maximize-sales-profit-can-also-make-additions-to-their-homes-to-increase-size,-as-well-as-use-high-quality-construction-and-design-in-their-initial-home-build-or-renovations." data-toc-modified-id="While-zip-code-and-distance-from-downtown-Seattle-are-factors-that-are-largely-outside-of-homeowners'-control,-they-could-ensure-that-desireable-locations-are-emphasized-during-the-selling-process.-Homeowners-looking-to-maximize-sales-profit-can-also-make-additions-to-their-homes-to-increase-size,-as-well-as-use-high-quality-construction-and-design-in-their-initial-home-build-or-renovations.-7.2.1">While zip code and distance from downtown Seattle are factors that are largely outside of homeowners' control, they could ensure that desireable locations are emphasized during the selling process. Homeowners looking to maximize sales profit can also make additions to their homes to increase size, as well as use high quality construction and design in their initial home build or renovations.</a></span></li></ul></li><li><span><a href="#Future-Work" data-toc-modified-id="Future-Work-7.3">Future Work</a></span><ul class="toc-item"><li><span><a href="#Given-more-time,-I-would-explore-a-method-to-more-judiciously-remove-outliers-in-the-data-set.-Using-the-IQR-score-method-for-each-variable-resulted-in-loss-of-~23%-of-original-data." data-toc-modified-id="Given-more-time,-I-would-explore-a-method-to-more-judiciously-remove-outliers-in-the-data-set.-Using-the-IQR-score-method-for-each-variable-resulted-in-loss-of-~23%-of-original-data.-7.3.1">Given more time, I would explore a method to more judiciously remove outliers in the data set. Using the IQR score method for each variable resulted in loss of ~23% of original data.</a></span></li><li><span><a href="#I-would-explore-whether-zip-codes-could-be-binned-into-&quot;regions&quot;-of-several-zip-codes,-to-see-if-these-would-produce-more-signifcant-or-interpretable-modeling-results." data-toc-modified-id="I-would-explore-whether-zip-codes-could-be-binned-into-&quot;regions&quot;-of-several-zip-codes,-to-see-if-these-would-produce-more-signifcant-or-interpretable-modeling-results.-7.3.2">I would explore whether zip codes could be binned into "regions" of several zip codes, to see if these would produce more signifcant or interpretable modeling results.</a></span></li></ul></li></ul></li><li><span><a href="#Code-for-Figures-for-Presentation" data-toc-modified-id="Code-for-Figures-for-Presentation-8">Code for Figures for Presentation</a></span></li></ul></div>

## Final Project Submission

Please fill out:
* Student name: Doug Steen
* Student pace: Full time (ds-100719)
* Scheduled project review date/time: 10/30/2019 9:15 AM CT
* Instructor name: James M Irving, Ph.D.
* Blog post URL: https://douglaspsteen.github.io/handling_categorical_variables_with_statsmodels_ols


# PROJECT OVERVIEW
### The objective of this project is to use the King County house dataset to produce a multiple linear regression model to predict sale prices. The motivation behind this study is to help homeowners identify areas in which they can maximize profts when selling their homes.
### First, I import the relevant python libraries and dataset, inspect the data, and remove extraneous information from the dataset. 
### Second, I scrub the data to address null, missing, and placeholder values, while deciding how to handle categorical variables and inspecting variables for multicollinearity. During the scrub phase, I use the latitude and longitude information to engineer a new feature representing the distance each home from downtown Seattle. 
### Third, I explore the scrubbed data by visualizing distributions, linearity between variables, and detection of outliers using an IQR score method. During the explore phase, I also perform one-hot encoding for several variables, logarithmically transform two variables, and set all independent numerical variables to the same min-max scale.
### Fourth, I use recursive feature elimination (RFE) to determine the most important features in my initial model, and use plots of r-squared and mean squared error (MSE) to determine the ideal number of features to select for linear regression. During the model phase, I use these selected features in the statsmodels OLS function to create an initial model.
### Finally, I revise the initial model by (1) checking for missed non-linearity in variables, (2) including zip codes in the revised linear regression model, and (3) using the simple linear regression of each variable against the target as a means for feature selection in the revised linear regression model, instead of RFE.

# OBTAIN

### Import relevant libraries and data


```python
# Import revlevant libraries and initiating desired settings
import warnings
import matplotlib.pyplot as plt
import matplotlib as mpl
import seaborn as sns
import numpy as np
import pandas as pd
import math
import itertools
%matplotlib inline

plt.style.use('seaborn-whitegrid')
sns.set_style('whitegrid')

# Ignore pink warnings
warnings.filterwarnings('ignore')

# Allow for a large # of columns in pandas dataframes
pd.set_option('display.max_columns', 0)
```


```python
# Check contents of the working directory
%ls
```

     Volume in drive C is Windows-SSD
     Volume Serial Number is 7A4A-3281
    
     Directory of C:\Users\dougl\Learn.co_lessons\mod_1_proj\dsc-v2-mod1-final-project-online-ds-ft-100719
    
    10/27/2019  05:14 PM    <DIR>          .
    10/27/2019  05:14 PM    <DIR>          ..
    10/22/2019  08:59 AM               146 .gitignore
    10/22/2019  09:11 AM    <DIR>          .ipynb_checkpoints
    10/22/2019  08:59 AM                93 .learn
    10/22/2019  08:59 AM         1,425,341 awesome.gif
    10/22/2019  08:59 AM             1,120 column_names.md
    10/22/2019  08:59 AM             1,846 CONTRIBUTING.md
    10/22/2019  08:59 AM         2,475,934 kc_house_data.csv
    10/22/2019  08:59 AM             1,354 LICENSE.md
    10/22/2019  08:59 AM            79,134 module1_project_rubric.pdf
    10/22/2019  07:32 PM            12,421 OSEMIN_scaffolding.ipynb
    10/22/2019  08:59 AM            13,290 README.md
    10/27/2019  05:14 PM         3,724,923 student.ipynb
    10/22/2019  07:24 PM           988,619 study_group_starter.ipynb
                  12 File(s)      8,724,221 bytes
                   3 Dir(s)  192,488,935,424 bytes free
    


```python
# Load data set, view head, display variable info
df = pd.read_csv('kc_house_data.csv')
display(df.head())
df.info()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>7129300520</td>
      <td>10/13/2014</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>3</td>
      <td>7</td>
      <td>1180</td>
      <td>0.0</td>
      <td>1955</td>
      <td>0.0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <td>1</td>
      <td>6414100192</td>
      <td>12/9/2014</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3</td>
      <td>7</td>
      <td>2170</td>
      <td>400.0</td>
      <td>1951</td>
      <td>1991.0</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <td>2</td>
      <td>5631500400</td>
      <td>2/25/2015</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3</td>
      <td>6</td>
      <td>770</td>
      <td>0.0</td>
      <td>1933</td>
      <td>NaN</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <td>3</td>
      <td>2487200875</td>
      <td>12/9/2014</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5</td>
      <td>7</td>
      <td>1050</td>
      <td>910.0</td>
      <td>1965</td>
      <td>0.0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1954400510</td>
      <td>2/18/2015</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3</td>
      <td>8</td>
      <td>1680</td>
      <td>0.0</td>
      <td>1987</td>
      <td>0.0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
</div>


    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 21597 entries, 0 to 21596
    Data columns (total 21 columns):
    id               21597 non-null int64
    date             21597 non-null object
    price            21597 non-null float64
    bedrooms         21597 non-null int64
    bathrooms        21597 non-null float64
    sqft_living      21597 non-null int64
    sqft_lot         21597 non-null int64
    floors           21597 non-null float64
    waterfront       19221 non-null float64
    view             21534 non-null float64
    condition        21597 non-null int64
    grade            21597 non-null int64
    sqft_above       21597 non-null int64
    sqft_basement    21597 non-null object
    yr_built         21597 non-null int64
    yr_renovated     17755 non-null float64
    zipcode          21597 non-null int64
    lat              21597 non-null float64
    long             21597 non-null float64
    sqft_living15    21597 non-null int64
    sqft_lot15       21597 non-null int64
    dtypes: float64(8), int64(11), object(2)
    memory usage: 3.5+ MB
    

### Removing the 'id' and 'date' columns, as they will not be relevant to the regression


```python
df.drop(['id', 'date'], axis=1, inplace=True)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>3</td>
      <td>7</td>
      <td>1180</td>
      <td>0.0</td>
      <td>1955</td>
      <td>0.0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <td>1</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3</td>
      <td>7</td>
      <td>2170</td>
      <td>400.0</td>
      <td>1951</td>
      <td>1991.0</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <td>2</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3</td>
      <td>6</td>
      <td>770</td>
      <td>0.0</td>
      <td>1933</td>
      <td>NaN</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <td>3</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5</td>
      <td>7</td>
      <td>1050</td>
      <td>910.0</td>
      <td>1965</td>
      <td>0.0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <td>4</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>3</td>
      <td>8</td>
      <td>1680</td>
      <td>0.0</td>
      <td>1987</td>
      <td>0.0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
</div>



# SCRUB

## ADDRESS NULL/MISSING VALUES AND POTENTIAL CATEGORICAL VARIABLES

### Get an overview of all columns using check_column function


```python
# check_column returns the datatype, null values and unique values of input series
def check_column(series_feature, series_target=None):  # ,max_unique=10):
    """Takes a series from a dataframe (df[col]), 
    reports back info on unique values, nulls, .describe() stats.


    Args:
        series (series (DataFrame column)): column to report    
    """
    dashes = '---'*25
    series = series_feature

    print(dashes)

    print(f"series dtype is {series.dtype}\n")
    print(f'- Unique Values for {series.name}')
    display(series.value_counts())  # [:max_unique])

    print('n- Null Values ')
    nulls = series.isna().sum()
    print(nulls)

    print('\n\tDescribe')
    print(series.describe())

    if series.dtype != 'object':
        sns.distplot(series)
        plt.show()
    else:
        print(f"{series.name} is a string column and cannot be plotted")

#     if series_target is not None:

        pass
```


```python
# Loop through the columns with check_columns
for col in df.columns:
    check_column(df[col])
```

    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for price
    


    350000.0    172
    450000.0    172
    550000.0    159
    500000.0    152
    425000.0    150
               ... 
    870515.0      1
    336950.0      1
    386100.0      1
    176250.0      1
    884744.0      1
    Name: price, Length: 3622, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    2.159700e+04
    mean     5.402966e+05
    std      3.673681e+05
    min      7.800000e+04
    25%      3.220000e+05
    50%      4.500000e+05
    75%      6.450000e+05
    max      7.700000e+06
    Name: price, dtype: float64
    


![png](output_14_3.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for bedrooms
    


    3     9824
    4     6882
    2     2760
    5     1601
    6      272
    1      196
    7       38
    8       13
    9        6
    10       3
    11       1
    33       1
    Name: bedrooms, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean         3.373200
    std          0.926299
    min          1.000000
    25%          3.000000
    50%          3.000000
    75%          4.000000
    max         33.000000
    Name: bedrooms, dtype: float64
    


![png](output_14_7.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for bathrooms
    


    2.50    5377
    1.00    3851
    1.75    3048
    2.25    2047
    2.00    1930
    1.50    1445
    2.75    1185
    3.00     753
    3.50     731
    3.25     589
    3.75     155
    4.00     136
    4.50     100
    4.25      79
    0.75      71
    4.75      23
    5.00      21
    5.25      13
    5.50      10
    1.25       9
    6.00       6
    5.75       4
    0.50       4
    8.00       2
    6.25       2
    6.75       2
    6.50       2
    7.50       1
    7.75       1
    Name: bathrooms, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean         2.115826
    std          0.768984
    min          0.500000
    25%          1.750000
    50%          2.250000
    75%          2.500000
    max          8.000000
    Name: bathrooms, dtype: float64
    


![png](output_14_11.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for sqft_living
    


    1300    138
    1400    135
    1440    133
    1660    129
    1010    129
           ... 
    4970      1
    2905      1
    2793      1
    4810      1
    1975      1
    Name: sqft_living, Length: 1034, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean      2080.321850
    std        918.106125
    min        370.000000
    25%       1430.000000
    50%       1910.000000
    75%       2550.000000
    max      13540.000000
    Name: sqft_living, dtype: float64
    


![png](output_14_15.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for sqft_lot
    


    5000      358
    6000      290
    4000      251
    7200      220
    7500      119
             ... 
    1448        1
    38884       1
    17313       1
    35752       1
    315374      1
    Name: sqft_lot, Length: 9776, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    2.159700e+04
    mean     1.509941e+04
    std      4.141264e+04
    min      5.200000e+02
    25%      5.040000e+03
    50%      7.618000e+03
    75%      1.068500e+04
    max      1.651359e+06
    Name: sqft_lot, dtype: float64
    


![png](output_14_19.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for floors
    


    1.0    10673
    2.0     8235
    1.5     1910
    3.0      611
    2.5      161
    3.5        7
    Name: floors, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean         1.494096
    std          0.539683
    min          1.000000
    25%          1.000000
    50%          1.500000
    75%          2.000000
    max          3.500000
    Name: floors, dtype: float64
    


![png](output_14_23.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for waterfront
    


    0.0    19075
    1.0      146
    Name: waterfront, dtype: int64


    n- Null Values 
    2376
    
    	Describe
    count    19221.000000
    mean         0.007596
    std          0.086825
    min          0.000000
    25%          0.000000
    50%          0.000000
    75%          0.000000
    max          1.000000
    Name: waterfront, dtype: float64
    


![png](output_14_27.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for view
    


    0.0    19422
    2.0      957
    3.0      508
    1.0      330
    4.0      317
    Name: view, dtype: int64


    n- Null Values 
    63
    
    	Describe
    count    21534.000000
    mean         0.233863
    std          0.765686
    min          0.000000
    25%          0.000000
    50%          0.000000
    75%          0.000000
    max          4.000000
    Name: view, dtype: float64
    


![png](output_14_31.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for condition
    


    3    14020
    4     5677
    5     1701
    2      170
    1       29
    Name: condition, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean         3.409825
    std          0.650546
    min          1.000000
    25%          3.000000
    50%          3.000000
    75%          4.000000
    max          5.000000
    Name: condition, dtype: float64
    


![png](output_14_35.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for grade
    


    7     8974
    8     6065
    9     2615
    6     2038
    10    1134
    11     399
    5      242
    12      89
    4       27
    13      13
    3        1
    Name: grade, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean         7.657915
    std          1.173200
    min          3.000000
    25%          7.000000
    50%          7.000000
    75%          8.000000
    max         13.000000
    Name: grade, dtype: float64
    


![png](output_14_39.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for sqft_above
    


    1300    212
    1010    210
    1200    206
    1220    192
    1140    184
           ... 
    2601      1
    440       1
    2473      1
    2441      1
    1975      1
    Name: sqft_above, Length: 942, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean      1788.596842
    std        827.759761
    min        370.000000
    25%       1190.000000
    50%       1560.000000
    75%       2210.000000
    max       9410.000000
    Name: sqft_above, dtype: float64
    


![png](output_14_43.png)


    ---------------------------------------------------------------------------
    series dtype is object
    
    - Unique Values for sqft_basement
    


    0.0       12826
    ?           454
    600.0       217
    500.0       209
    700.0       208
              ...  
    1930.0        1
    2570.0        1
    266.0         1
    2310.0        1
    274.0         1
    Name: sqft_basement, Length: 304, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count     21597
    unique      304
    top         0.0
    freq      12826
    Name: sqft_basement, dtype: object
    sqft_basement is a string column and cannot be plotted
    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for yr_built
    


    2014    559
    2006    453
    2005    450
    2004    433
    2003    420
           ... 
    1933     30
    1901     29
    1902     27
    1935     24
    1934     21
    Name: yr_built, Length: 116, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean      1970.999676
    std         29.375234
    min       1900.000000
    25%       1951.000000
    50%       1975.000000
    75%       1997.000000
    max       2015.000000
    Name: yr_built, dtype: float64
    


![png](output_14_49.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for yr_renovated
    


    0.0       17011
    2014.0       73
    2003.0       31
    2013.0       31
    2007.0       30
              ...  
    1946.0        1
    1959.0        1
    1971.0        1
    1951.0        1
    1954.0        1
    Name: yr_renovated, Length: 70, dtype: int64


    n- Null Values 
    3842
    
    	Describe
    count    17755.000000
    mean        83.636778
    std        399.946414
    min          0.000000
    25%          0.000000
    50%          0.000000
    75%          0.000000
    max       2015.000000
    Name: yr_renovated, dtype: float64
    


![png](output_14_53.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for zipcode
    


    98103    602
    98038    589
    98115    583
    98052    574
    98117    553
            ... 
    98102    104
    98010    100
    98024     80
    98148     57
    98039     50
    Name: zipcode, Length: 70, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean     98077.951845
    std         53.513072
    min      98001.000000
    25%      98033.000000
    50%      98065.000000
    75%      98118.000000
    max      98199.000000
    Name: zipcode, dtype: float64
    


![png](output_14_57.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for lat
    


    47.6624    17
    47.5491    17
    47.5322    17
    47.6846    17
    47.6711    16
               ..
    47.2785     1
    47.4162     1
    47.3870     1
    47.2313     1
    47.2715     1
    Name: lat, Length: 5033, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean        47.560093
    std          0.138552
    min         47.155900
    25%         47.471100
    50%         47.571800
    75%         47.678000
    max         47.777600
    Name: lat, dtype: float64
    


![png](output_14_61.png)


    ---------------------------------------------------------------------------
    series dtype is float64
    
    - Unique Values for long
    


    -122.290    115
    -122.300    111
    -122.362    104
    -122.291    100
    -122.372     99
               ... 
    -121.403      1
    -121.804      1
    -121.726      1
    -121.895      1
    -121.893      1
    Name: long, Length: 751, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean      -122.213982
    std          0.140724
    min       -122.519000
    25%       -122.328000
    50%       -122.231000
    75%       -122.125000
    max       -121.315000
    Name: long, dtype: float64
    


![png](output_14_65.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for sqft_living15
    


    1540    197
    1440    195
    1560    192
    1500    180
    1460    169
           ... 
    4890      1
    2873      1
    952       1
    3193      1
    2049      1
    Name: sqft_living15, Length: 777, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count    21597.000000
    mean      1986.620318
    std        685.230472
    min        399.000000
    25%       1490.000000
    50%       1840.000000
    75%       2360.000000
    max       6210.000000
    Name: sqft_living15, dtype: float64
    


![png](output_14_69.png)


    ---------------------------------------------------------------------------
    series dtype is int64
    
    - Unique Values for sqft_lot15
    


    5000      427
    4000      356
    6000      288
    7200      210
    4800      145
             ... 
    11036       1
    8989        1
    871200      1
    809         1
    6147        1
    Name: sqft_lot15, Length: 8682, dtype: int64


    n- Null Values 
    0
    
    	Describe
    count     21597.000000
    mean      12758.283512
    std       27274.441950
    min         651.000000
    25%        5100.000000
    50%        7620.000000
    75%       10083.000000
    max      871200.000000
    Name: sqft_lot15, dtype: float64
    


![png](output_14_73.png)


### CONCLUSIONS ON NULL/MISSING VALUES:
#### - 'waterfront' - Lots of null values. STRATEGY: Replace null values with most common value, 0.0
#### -'view' - Some null values. STRATEGY: Replace null values with most common value, 0.0
#### -'yr_renovated' - Lots of null values, column entries mostly have value of 0.0. STRATEGY: Drop entire column from dataset
#### -'sqft_basement' - Placeholder variable '?'. STRATEGY: Replace '?' with most common value, 0.0

### Replace identified null values, remove 'yr_renovated' column, change 'sqft_basement' to categorical


```python
# Replace nulls in 'waterfront' with 0.0
df.waterfront.fillna(value=0.0, inplace=True)

# Replace nulls in 'view' with 0.0
df.view.fillna(value=0.0, inplace=True)

# Drop 'yr_renovated' from dataframe
df.drop('yr_renovated', axis=1, inplace=True)

# Replace '?' values in 'sqft_basement' with 0.0
df.sqft_basement = df.sqft_basement.apply(
    lambda x: 0 if x == '0.0' else 0 if x == '?' else 1)
```

### CONCLUSIONS ON CATEGORICAL VARIABLES & DATA TYPES
#### - 'sqft_basement' - I want to re-cast as categorical. STRATEGY: Convert to a categorical variable (0 = no basement, 1 = has basement)
#### - 'waterfront', 'view', 'condition', should be categorical variables. STRATEGY: Convert these to categorical variables


```python
# Make basement a categorical variable, create a new colunn with cat.codes
df.sqft_basement = df.sqft_basement.astype('category')
df['basement_coded'] = df.sqft_basement.cat.codes
df.basement_coded.value_counts()
```




    0    13280
    1     8317
    Name: basement_coded, dtype: int64




```python
# Make waterfront a categorical variable, create new column with cat.codes
df.waterfront = df.waterfront.astype('category')
df['wf_coded'] = df.waterfront.cat.codes
df.wf_coded.value_counts()
```




    0    21451
    1      146
    Name: wf_coded, dtype: int64




```python
# Make view a categorical variable, create new column with cat.codes
df.view = df.view.astype('category')
df['view_coded'] = df.view.cat.codes
df.view_coded.value_counts()
```




    0    19485
    2      957
    3      508
    1      330
    4      317
    Name: view_coded, dtype: int64




```python
# Make condition a categorical variable, create new column with cat.codes
df.condition = df.condition.astype('category')
df['cond_coded'] = df.condition.cat.codes
df.cond_coded.value_counts()
```




    2    14020
    3     5677
    4     1701
    1      170
    0       29
    Name: cond_coded, dtype: int64



## FEATURE ENGINEERING: DISTANCE FROM DOWNTOWN SEATTLE (dist_dt)
#### Using lat_lon_dist_calc function to calculate distance from observation to downtown Seattle
#### I am using this feature to replace the 'lat', 'long', and 'zipcode' columns as I believe it will capture information from all three
#### I hypothesize that there will be a decreasing relationship with price as dist_dt increases


```python
# function to calculate distance (meters) from downtown Seattle using lat and lon
# default lat_0 and lon_0 are downtown Seattle


def lat_lon_dist_calc(lat_1, lon_1, lat_0=47.6050, lon_0=-122.3344):
    """Returns the distance (meters) between two lat/long coordinates.

    Args:
        lat_0 (value or series): latitude of reference point or first point (default is downtown Seattle)
        lon_0 (value or series): longitude of reference point or first point (default is downtown Seattle)
        lat_1 (value or series): latitude of comparison point or second point
        lon_1 (value or series): longitude of comparison point or second point
    """
    R = 6372800  # Earth's radius in meters

    phi1, phi2 = np.radians(lat_0), np.radians(
        lat_1)  # Converting given latitudes to radians
    # Change in latitude conversion to radians
    dphi = np.radians(lat_1 - lat_0)
    # Change in longitude conversion to radians
    dlambda = np.radians(lon_1 - lon_0)

    # Haversine formula to calculate the great-circle distance between two points
    a = np.sin(dphi/2)**2 + np.cos(phi1)*np.cos(phi2)*np.sin(dlambda/2)**2
    c = 2*np.arctan2(np.sqrt(a), np.sqrt(1 - a))
    return R*c
```


```python
dist_dt = lat_lon_dist_calc(
    lat_1=df.lat, lon_1=df.long, lat_0=47.6050, lon_0=-122.3344)
dist_dt.head()
```




    0    11941.535518
    1    12953.726115
    2    16618.820484
    3    10346.572376
    4    21740.172916
    dtype: float64




```python
# Add dist_downtown column to df
df = pd.concat([df, dist_dt], axis=1)
```


```python
df = df.rename(columns={0: 'dist_dt'})
```


```python
# Drop lat, long, and zipcode columns from df
df = df.drop(['lat', 'long', 'zipcode'], axis=1)
```

### Question #1: Do any features display high collinearity (>0.75) that should be removed before modeling?

### ASSESS MULTICOLLINEARITY OF FEATURES


```python
# Plotting correlation matrix to see relationships between independent variables, assess multicollinearity
plt.figure(figsize=(15, 15))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1b8ba0964e0>




![png](output_31_1.png)


### Question #1 Answer: Multicollinearity observaions
#### - sqft_living is highly correlated (R > 0.75) to sqft_above, bathrooms, grade, sqft_living15
#### -Since it is highly correlated to many other variables, it makes sense to remove sqft_living before proceeding with regression

### Removal of collinear features for scrubbed df


```python
# Dropping sqft_living from scrubbed dataframe due to collinearity (df_scrub)
# Removing sqft_basement, waterfront, view from df_scrub, since we have their cat.codes
df_scrub = df.drop(['sqft_living', 'sqft_basement',
                    'waterfront', 'view', 'condition'], axis=1)
```


```python
df_scrub.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 21597 entries, 0 to 21596
    Data columns (total 15 columns):
    price             21597 non-null float64
    bedrooms          21597 non-null int64
    bathrooms         21597 non-null float64
    sqft_lot          21597 non-null int64
    floors            21597 non-null float64
    grade             21597 non-null int64
    sqft_above        21597 non-null int64
    yr_built          21597 non-null int64
    sqft_living15     21597 non-null int64
    sqft_lot15        21597 non-null int64
    basement_coded    21597 non-null int8
    wf_coded          21597 non-null int8
    view_coded        21597 non-null int8
    cond_coded        21597 non-null int8
    dist_dt           21597 non-null float64
    dtypes: float64(4), int64(7), int8(4)
    memory usage: 1.9 MB
    

### SUMMARY OF INITIAL DATA SCRUB:
####  - Variables dropped from dataset: 
    - 'id', 'date' - These variabes will not add valuable information to a regression model
    - 'yr_renovated' - So many null and zero values that it will be easier to remove this column entirely
    - 'lat, long, zipcode' - These variables were removed in favor of the engineered feature 'dist_dt', which represents the distance of an observation from downtown Seattle
    - 'sqft_living' - Displayed collinearity with multiple other variables
#### - Variables left as continuous numerical:
    - 'price'
    - 'bedrooms'
    - 'bathrooms'
    - 'sqft_lot'
    - 'floors'
    - 'grade'
    - 'sqft_above'
    - 'yr_built'
    - 'sqft_living15'
    - 'sqft_lot15'
#### - Variables added through feature engineering as continuous numerical:
    - 'dist_dt' - Calculated distance from the observation to downtown Seattle
#### - Variables to be treated as categorical using cat.codes:
    - 'basement_coded' - Represents either '0' (no basement) or '1' (has a basement). Placeholders '?' replaced with 0.
    - 'wf_coded' - Represents either '0' (not waterfront) or '1' (is waterfront). Null values were replaced with 0.
    - 'view_coded' - Index from 0 to 4 on the quality of the view of property. Null values were replaced with 0.
    - 'cond_coded' - Index 0 to 4 on property condition

# EXPLORE

## VISUALIZING DISTRIBUTIONS AND SCATTER PLOTS
    -Check distribution shapes
    -Check linearity of data
    -View potential outliers


```python
# Plot histogram and scatter/regline plots for each variable in df_scrub
for col in df_scrub.columns:
    plt.figure(figsize=(12, 6))
    plt.subplot(121)
    ax1 = sns.distplot(df_scrub[col])
    plt.subplot(122)
    ax2 = sns.regplot(df_scrub[col], df_scrub.price)
    plt.suptitle(f'Column: {col}')
    plt.show()
```


![png](output_39_0.png)



![png](output_39_1.png)



![png](output_39_2.png)



![png](output_39_3.png)



![png](output_39_4.png)



![png](output_39_5.png)



![png](output_39_6.png)



![png](output_39_7.png)



![png](output_39_8.png)



![png](output_39_9.png)



![png](output_39_10.png)



![png](output_39_11.png)



![png](output_39_12.png)



![png](output_39_13.png)



![png](output_39_14.png)


- Outliers seem to be present for several variables that may also be skewing distributions
- These outliers should be identified and removed, if appropriate, before continuing

### Question #2: Can variable distributions be improved by objective outlier detection and removal?

## OUTLIER DETECTION AND REMOVAL
#### Outlier detection performed using IQR Scores


```python
# Identify outliers for df_scrub non-categorical variables

non_cat_cols = ['price', 'bedrooms', 'bathrooms', 'sqft_lot', 'floors',
                'grade', 'sqft_above', 'yr_built', 'sqft_living15', 'sqft_lot15', 'dist_dt']
out_index = []

for col in df_scrub[non_cat_cols]:
    q1, q3 = np.percentile(a=df_scrub[col], q=[25, 75])
    iqr = q3 - q1
    lower_bound = q1 - (1.5*iqr)
    upper_bound = q3 + (1.5*iqr)
#     outliers = []
#     for i in df_scrub[col]:
#         if i < lower_bound or i > upper_bound:
#             outliers.append(i)
    out_index.append(list(
        df_scrub[(df_scrub[col] < lower_bound) | (df_scrub[col] > upper_bound)].index))


outlier_index = set(list(itertools.chain.from_iterable(out_index)))

df_out_rem = df_scrub.drop(outlier_index)

display(df_scrub.info())
display(df_out_rem.info())
display(len(outlier_index))
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 21597 entries, 0 to 21596
    Data columns (total 15 columns):
    price             21597 non-null float64
    bedrooms          21597 non-null int64
    bathrooms         21597 non-null float64
    sqft_lot          21597 non-null int64
    floors            21597 non-null float64
    grade             21597 non-null int64
    sqft_above        21597 non-null int64
    yr_built          21597 non-null int64
    sqft_living15     21597 non-null int64
    sqft_lot15        21597 non-null int64
    basement_coded    21597 non-null int8
    wf_coded          21597 non-null int8
    view_coded        21597 non-null int8
    cond_coded        21597 non-null int8
    dist_dt           21597 non-null float64
    dtypes: float64(4), int64(7), int8(4)
    memory usage: 1.9 MB
    


    None


    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 16624 entries, 0 to 21596
    Data columns (total 15 columns):
    price             16624 non-null float64
    bedrooms          16624 non-null int64
    bathrooms         16624 non-null float64
    sqft_lot          16624 non-null int64
    floors            16624 non-null float64
    grade             16624 non-null int64
    sqft_above        16624 non-null int64
    yr_built          16624 non-null int64
    sqft_living15     16624 non-null int64
    sqft_lot15        16624 non-null int64
    basement_coded    16624 non-null int8
    wf_coded          16624 non-null int8
    view_coded        16624 non-null int8
    cond_coded        16624 non-null int8
    dist_dt           16624 non-null float64
    dtypes: float64(4), int64(7), int8(4)
    memory usage: 1.6 MB
    


    None



    4973


#### All outliers identified using IQR +/- 1.5 for non-categorical variables have now been removed, and stored in new df (df_out_rem).


```python
# Plot histogram and scatter/regline plots for each variable in df_out_rem
for col in df_out_rem.columns:
    plt.figure(figsize=(12, 6))
    plt.subplot(121)
    ax1 = sns.distplot(df_out_rem[col])
    plt.subplot(122)
    ax2 = sns.regplot(df_out_rem[col], df_out_rem.price)
    plt.suptitle(f'Column: {col}')
    plt.show()
```


![png](output_45_0.png)



![png](output_45_1.png)



![png](output_45_2.png)



![png](output_45_3.png)



![png](output_45_4.png)



![png](output_45_5.png)



![png](output_45_6.png)



![png](output_45_7.png)



![png](output_45_8.png)



![png](output_45_9.png)



![png](output_45_10.png)



![png](output_45_11.png)



![png](output_45_12.png)



![png](output_45_13.png)



![png](output_45_14.png)


### Question #2 Answer: Yes, 'price', 'bedrooms', 'bathrooms', 'sqft_lot', 'sqft_above', 'sqft_living15', 'sqft_lot15', and 'dist_dt' are much more normally distributed after outlier detection and removal.

### Question #3: After outlier removal, would any features benefit from log transformation?
    'sqft_above' and 'sqft_living15' are a bit right skewed. I will log transform fhose ones.
    -The others generally have some skew but look ok. I'm going to leave them alone for now.


```python
# Perform log transformation on 'sqft_above', and observe resulting histogram

df_out_rem['sqft_above_log'] = np.log(df_out_rem.sqft_above)
sns.distplot(df_out_rem.sqft_above_log)
plt.show()

df_out_rem['sqft_living15_log'] = np.log(df_out_rem.sqft_living15)
sns.distplot(df_out_rem.sqft_living15_log)
plt.show()
```


![png](output_48_0.png)



![png](output_48_1.png)


### Question #3 Answer: Yes, both 'sqft_above' and 'sqft_living15' both have more normal distributions after log transformation.


```python
# Updading df with transformed variables
df_trans = df_out_rem.drop(['sqft_above', 'sqft_living15'], axis=1)
```


```python
df_trans.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>grade</th>
      <th>yr_built</th>
      <th>sqft_lot15</th>
      <th>basement_coded</th>
      <th>wf_coded</th>
      <th>view_coded</th>
      <th>cond_coded</th>
      <th>dist_dt</th>
      <th>sqft_above_log</th>
      <th>sqft_living15_log</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>5650</td>
      <td>1.0</td>
      <td>7</td>
      <td>1955</td>
      <td>5650</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>11941.535518</td>
      <td>7.073270</td>
      <td>7.200425</td>
    </tr>
    <tr>
      <td>1</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>7242</td>
      <td>2.0</td>
      <td>7</td>
      <td>1951</td>
      <td>7639</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>12953.726115</td>
      <td>7.682482</td>
      <td>7.432484</td>
    </tr>
    <tr>
      <td>2</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>10000</td>
      <td>1.0</td>
      <td>6</td>
      <td>1933</td>
      <td>8062</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>16618.820484</td>
      <td>6.646391</td>
      <td>7.908387</td>
    </tr>
    <tr>
      <td>3</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>5000</td>
      <td>1.0</td>
      <td>7</td>
      <td>1965</td>
      <td>5000</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>4</td>
      <td>10346.572376</td>
      <td>6.956545</td>
      <td>7.215240</td>
    </tr>
    <tr>
      <td>4</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>8080</td>
      <td>1.0</td>
      <td>8</td>
      <td>1987</td>
      <td>7503</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>21740.172916</td>
      <td>7.426549</td>
      <td>7.495542</td>
    </tr>
  </tbody>
</table>
</div>



## ONE-HOT ENCODING OF CATEGORICAL VARIABLES

#### Need to do this for all categoricals before performing regression
#### - 'basement_coded' and 'wf_coded' are already in the correct format
#### - Use pandas to get dummy variables for 'view_coded' and 'cond_coded'


```python
view_dummies = pd.get_dummies(df_trans.view_coded, drop_first=True, prefix='view')
cond_dummies = pd.get_dummies(df_trans.cond_coded, drop_first=True, prefix='cond')
```


```python
df_trans = df_trans.drop(['view_coded', 'cond_coded'], axis=1)
df_trans = pd.concat([df_trans, view_dummies, cond_dummies], axis=1)
```


```python
df_trans.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>grade</th>
      <th>yr_built</th>
      <th>sqft_lot15</th>
      <th>basement_coded</th>
      <th>wf_coded</th>
      <th>dist_dt</th>
      <th>sqft_above_log</th>
      <th>sqft_living15_log</th>
      <th>view_1</th>
      <th>view_2</th>
      <th>view_3</th>
      <th>view_4</th>
      <th>cond_1</th>
      <th>cond_2</th>
      <th>cond_3</th>
      <th>cond_4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>5650</td>
      <td>1.0</td>
      <td>7</td>
      <td>1955</td>
      <td>5650</td>
      <td>0</td>
      <td>0</td>
      <td>11941.535518</td>
      <td>7.073270</td>
      <td>7.200425</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>7242</td>
      <td>2.0</td>
      <td>7</td>
      <td>1951</td>
      <td>7639</td>
      <td>1</td>
      <td>0</td>
      <td>12953.726115</td>
      <td>7.682482</td>
      <td>7.432484</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>10000</td>
      <td>1.0</td>
      <td>6</td>
      <td>1933</td>
      <td>8062</td>
      <td>0</td>
      <td>0</td>
      <td>16618.820484</td>
      <td>6.646391</td>
      <td>7.908387</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>5000</td>
      <td>1.0</td>
      <td>7</td>
      <td>1965</td>
      <td>5000</td>
      <td>1</td>
      <td>0</td>
      <td>10346.572376</td>
      <td>6.956545</td>
      <td>7.215240</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <td>4</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>8080</td>
      <td>1.0</td>
      <td>8</td>
      <td>1987</td>
      <td>7503</td>
      <td>0</td>
      <td>0</td>
      <td>21740.172916</td>
      <td>7.426549</td>
      <td>7.495542</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



## MIN/MAX SCALING OF FEATURES


```python
X = df_trans.drop(['price'], axis=1)
y = df_trans['price']

X_sc = pd.DataFrame([])

for col in X.columns:
    scaled_var = (X[col] - min(X[col])) / (max(X[col]) - min(X[col]))
    X_sc = pd.concat([X_sc, scaled_var], axis=1)

X_sc.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>grade</th>
      <th>yr_built</th>
      <th>sqft_lot15</th>
      <th>basement_coded</th>
      <th>wf_coded</th>
      <th>dist_dt</th>
      <th>sqft_above_log</th>
      <th>sqft_living15_log</th>
      <th>view_1</th>
      <th>view_2</th>
      <th>view_3</th>
      <th>view_4</th>
      <th>cond_1</th>
      <th>cond_2</th>
      <th>cond_3</th>
      <th>cond_4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0.333333</td>
      <td>0.090909</td>
      <td>0.275495</td>
      <td>0.0</td>
      <td>0.333333</td>
      <td>0.478261</td>
      <td>0.295816</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.233689</td>
      <td>0.438120</td>
      <td>0.435422</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>0.333333</td>
      <td>0.545455</td>
      <td>0.360990</td>
      <td>0.4</td>
      <td>0.333333</td>
      <td>0.443478</td>
      <td>0.413516</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.255618</td>
      <td>0.734854</td>
      <td>0.566527</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0.000000</td>
      <td>0.090909</td>
      <td>0.509103</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.286957</td>
      <td>0.438547</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.335021</td>
      <td>0.230196</td>
      <td>0.835396</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>0.666667</td>
      <td>0.818182</td>
      <td>0.240589</td>
      <td>0.0</td>
      <td>0.333333</td>
      <td>0.565217</td>
      <td>0.257353</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.199135</td>
      <td>0.381266</td>
      <td>0.443792</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <td>4</td>
      <td>0.333333</td>
      <td>0.454545</td>
      <td>0.405993</td>
      <td>0.0</td>
      <td>0.666667</td>
      <td>0.756522</td>
      <td>0.405468</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.445974</td>
      <td>0.610195</td>
      <td>0.602153</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



# MODEL

## RECURSIVE FEATURE ELIMINATION (RFE) - INITIAL MODEL


```python
# Use recursive feature selection from sklearn to start building model
from sklearn.feature_selection import RFE
from sklearn.linear_model import LinearRegression
linreg = LinearRegression()

# Testing out the RFE to find the 5 most important features
selector = RFE(linreg, n_features_to_select=1)
selector = selector.fit(X_sc, y)
```


```python
selected_features = list(zip(selector.support_, X.columns))
ranked_features = list(zip(selector.ranking_, X.columns))
```


```python
ranked_features
```




    [(17, 'bedrooms'),
     (12, 'bathrooms'),
     (20, 'sqft_lot'),
     (19, 'floors'),
     (5, 'grade'),
     (6, 'yr_built'),
     (18, 'sqft_lot15'),
     (16, 'basement_coded'),
     (7, 'wf_coded'),
     (2, 'dist_dt'),
     (3, 'sqft_above_log'),
     (1, 'sqft_living15_log'),
     (14, 'view_1'),
     (15, 'view_2'),
     (13, 'view_3'),
     (4, 'view_4'),
     (11, 'cond_1'),
     (10, 'cond_2'),
     (9, 'cond_3'),
     (8, 'cond_4')]



### Now I want to compare r^2 to MSE as I increase # of features, to find point of diminishing returns


```python
r_squared = []
for x in range(1, len(X_sc.columns)):
    selector = RFE(linreg, n_features_to_select=x)
    selector.fit(X_sc, y)
    linreg.fit(X_sc[X_sc.columns[selector.support_]], y)
    r_sq = linreg.score(X_sc[X_sc.columns[selector.support_]], y)
    r_squared.append(r_sq)
```


```python
from sklearn.metrics import mean_squared_error

mse = []
for x in range(1, len(X_sc.columns)):
    selector = RFE(linreg, n_features_to_select=x)
    selector.fit(X_sc, y)
    linreg.fit(X_sc[X_sc.columns[selector.support_]], y)
    y_pred = linreg.predict(X_sc[X_sc.columns[selector.support_]])
    mse.append(mean_squared_error(y, y_pred))
```


```python
plt.figure(figsize=(12,6))
plt.title('R-squared and MSE vs # of Features')

ax1 = plt.subplot(121)
ax1.plot(range(1, len(X_sc.columns)), r_squared)
ax1.set_ylabel('R-squared')
ax1.set_xlabel('# of Features')

ax2 = plt.subplot(122)
ax2.plot(range(1, len(X_sc.columns)), mse)
ax2.set_ylabel('MSE')
ax2.set_xlabel('# of Features')

plt.show()
```


![png](output_66_0.png)


### The above R-squared and MSE 'elbow' plots indicate that I can safely select 5 as the number of features. Below I am using the most important 5 features for linear regression using statsmodels, as indicated by RFE.


```python
import statsmodels.api as sm
predictors = X_sc[['sqft_living15_log', 'dist_dt', 'sqft_above_log', 'view_4', 'grade']]
predictors_int = sm.add_constant(predictors)
model_RFE = sm.OLS(y, predictors_int).fit()
model_RFE.summary()
```




<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.588</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.588</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   4747.</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Sun, 27 Oct 2019</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>18:57:08</td>     <th>  Log-Likelihood:    </th> <td>-2.1835e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 16624</td>      <th>  AIC:               </th>  <td>4.367e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 16618</td>      <th>  BIC:               </th>  <td>4.368e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>     5</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
          <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>const</th>             <td> 2.154e+05</td> <td> 3923.760</td> <td>   54.891</td> <td> 0.000</td> <td> 2.08e+05</td> <td> 2.23e+05</td>
</tr>
<tr>
  <th>sqft_living15_log</th> <td> 3.181e+05</td> <td> 8342.542</td> <td>   38.128</td> <td> 0.000</td> <td> 3.02e+05</td> <td> 3.34e+05</td>
</tr>
<tr>
  <th>dist_dt</th>           <td>-4.916e+05</td> <td> 4791.176</td> <td> -102.605</td> <td> 0.000</td> <td>-5.01e+05</td> <td>-4.82e+05</td>
</tr>
<tr>
  <th>sqft_above_log</th>    <td> 2.492e+05</td> <td> 8177.071</td> <td>   30.481</td> <td> 0.000</td> <td> 2.33e+05</td> <td> 2.65e+05</td>
</tr>
<tr>
  <th>view_4</th>            <td> 2.107e+05</td> <td> 1.38e+04</td> <td>   15.280</td> <td> 0.000</td> <td> 1.84e+05</td> <td> 2.38e+05</td>
</tr>
<tr>
  <th>grade</th>             <td> 1.902e+05</td> <td> 4848.677</td> <td>   39.227</td> <td> 0.000</td> <td> 1.81e+05</td> <td>    2e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>659.886</td> <th>  Durbin-Watson:     </th> <td>   1.968</td> 
</tr>
<tr>
  <th>Prob(Omnibus):</th> <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td> 803.517</td> 
</tr>
<tr>
  <th>Skew:</th>          <td> 0.449</td>  <th>  Prob(JB):          </th> <td>3.30e-175</td>
</tr>
<tr>
  <th>Kurtosis:</th>      <td> 3.594</td>  <th>  Cond. No.          </th> <td>    20.8</td> 
</tr>
</table><br/><br/>Warnings:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.



### Initial model uses the following five features: 'sqft_living15_log', 'dist_dt', 'sqft_above_log', 'view_4', and 'grade'
#### -R-squared = 0.59 (R-squared and adj-R-squared are identical)
#### -p-value = 0.00
#### -Skewness and kurtosis values indicate that the distribution of residuals is likely normal and homoscedastic

# iNTERPRET

## CHECK MODEL AGAINST LINEAR REGRESSION ASSUMPTIONS

### 1) Assess normality of Residuals using Histograms and Q-Q Plots


```python
plt.figure(figsize=(8, 5))
plt.hist(model_RFE.resid, bins=100)
plt.xlabel('Residuals (Price in $)')
plt.ylabel('Frequency')
plt.title('Distribution of Model Residuals')
plt.show()
```


![png](output_73_0.png)



```python
sm.graphics.qqplot(model_RFE.resid, line='45', fit=True)
plt.title('Q-Q Plot of Model Residuals')
plt.show()
```


![png](output_74_0.png)


### 2) Assess Heteroscedasticity of Residuals


```python
res_x = list(range(0, len(X_sc)))

plt.figure(figsize=(8, 5))
plt.scatter(res_x, model_RFE.resid, s=1)
plt.hlines(y=0, xmin=0, xmax=len(X_sc), color='red')
plt.xlabel('Observation')
plt.ylabel('Residuals (Price in $)')
plt.show()
```


![png](output_76_0.png)


### CONCLUSION: It appears the assumptions of linear regression are not violated. The Q-Q plot and histogram of residuals indicate some right-skew, but this does not seem alarming. The model residuals appear to be homoscedastic.

## MODEL VALIDATION

### Train-Test-Split Validation


```python
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.linear_model import LinearRegression
```


```python
X_train, X_test, y_train, y_test = train_test_split(
    predictors, y, test_size=0.25)
```


```python
linreg = LinearRegression()
linreg.fit(X_train, y_train)

y_hat_train = linreg.predict(X_train)
y_hat_test = linreg.predict(X_test)
```


```python
train_rmse = np.sqrt(mean_squared_error(y_train, y_hat_train))
test_rmse = np.sqrt(mean_squared_error(y_test, y_hat_test))
print('Train Root Mean Squarred Error ($ Price):', train_rmse)
print('Test Root Mean Squarred Error($ Price):', test_rmse)
```

    Train Root Mean Squarred Error ($ Price): 122658.29567947419
    Test Root Mean Squarred Error($ Price): 122037.36062175455
    

#### The Train and Test RMSE's are nearly identical. This tells us that our model is not being undertrained or overtained on the train-test-split - there is a good balance here.

#### The train-test-split tells us that the standard deviation of model residuals is about $122-123k.

### K-fold Cross Validation


```python
from sklearn.model_selection import cross_val_score

k_fold_RMSE = np.mean(np.sqrt(-cross_val_score(linreg,
                                               predictors, y, cv=10,  scoring='neg_mean_squared_error')))
print(f'k-fold RMSE is: {k_fold_RMSE}')
```

    k-fold RMSE is: 122881.68252268476
    

#### The k-fold RMSE for 10 bins is ~ $123k, virtually identical to the RMSE from train-test-split.

## INITIAL MODEL SUMMARY
#### Five features selected ('sqft_living15_log', 'dist_dt', 'sqft_above_log', 'view_4', 'grade') using sklearn RFE
#### Linear regression model produced using these five features in statsmodels OLS
#### R-squared = 0.59
#### Residuals are primarily normally distributed, homoscedastic
#### RMSE of train-test-split and k-fold cross validation is ~ $123k

## REVISED MODEL
### Goal: See if I can improve the model r-squared value while reducing errors, and maintaining predictability of the initial model.
### Strategy: 
### 1) Check for any missed non-linearity between the variables that could possibly be corrected
### 2) Include zip codes as a categorical variable in the list of features (previously excluded)
### 3) Instead of RFE, check simple linear regression for each predictor on its own to choose top 5 features


```python
# Strategy Step 1: Check for missed non-linearity
# Re-examine previous plots for comparison of features to price
for col in X_sc.columns:
    plt.figure(figsize=(12, 6))
    plt.subplot(121)
    ax1 = sns.distplot(X_sc[col])
    plt.subplot(122)
    ax2 = sns.regplot(X_sc[col], y)
    plt.suptitle(f'Column: {col}')
    plt.show()
```


![png](output_90_0.png)



![png](output_90_1.png)



![png](output_90_2.png)



![png](output_90_3.png)



![png](output_90_4.png)



![png](output_90_5.png)



![png](output_90_6.png)



![png](output_90_7.png)



![png](output_90_8.png)



![png](output_90_9.png)



![png](output_90_10.png)



![png](output_90_11.png)



![png](output_90_12.png)



![png](output_90_13.png)



![png](output_90_14.png)



![png](output_90_15.png)



![png](output_90_16.png)



![png](output_90_17.png)



![png](output_90_18.png)



![png](output_90_19.png)


### I don't see an obvious transformation to improve the linearity of any features, so I will move on to step 2.


```python
# Strategy Step 2: Include zip codes in features for selection

# Get zip codes from original data, and convert column to category
df_2 = pd.read_csv('kc_house_data.csv')
df_zip = pd.DataFrame([])
df_zip['zipcodes'] = df_2.zipcode
df_zip.zipcodes = df_zip.zipcodes.astype('category')
df_zip['zip_coded'] = df_zip.zipcodes.cat.codes

# Remove rows previously identified as contaning outliers using outLier_index
df_zip_out = df_zip.drop(outlier_index)
```


```python
# Remove old column of zip codes
df_zip_coded = df_zip_out.drop(['zipcodes'], axis=1)
df_zip_coded.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>zip_coded</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>66</td>
    </tr>
    <tr>
      <td>1</td>
      <td>55</td>
    </tr>
    <tr>
      <td>2</td>
      <td>16</td>
    </tr>
    <tr>
      <td>3</td>
      <td>58</td>
    </tr>
    <tr>
      <td>4</td>
      <td>37</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Strategy Step 3: Run simple linear regression for each predictor on its own against price to determine top 5 features

# Concatenate dataframe with zip code data
df_rev = pd.concat([df_trans, df_zip_coded], axis=1)
df_rev.info()

X_rev = df_rev
y_rev = y
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 16624 entries, 0 to 21596
    Data columns (total 22 columns):
    price                16624 non-null float64
    bedrooms             16624 non-null int64
    bathrooms            16624 non-null float64
    sqft_lot             16624 non-null int64
    floors               16624 non-null float64
    grade                16624 non-null int64
    yr_built             16624 non-null int64
    sqft_lot15           16624 non-null int64
    basement_coded       16624 non-null int8
    wf_coded             16624 non-null int8
    dist_dt              16624 non-null float64
    sqft_above_log       16624 non-null float64
    sqft_living15_log    16624 non-null float64
    view_1               16624 non-null uint8
    view_2               16624 non-null uint8
    view_3               16624 non-null uint8
    view_4               16624 non-null uint8
    cond_1               16624 non-null uint8
    cond_2               16624 non-null uint8
    cond_3               16624 non-null uint8
    cond_4               16624 non-null uint8
    zip_coded            16624 non-null int8
    dtypes: float64(6), int64(5), int8(3), uint8(8)
    memory usage: 1.7 MB
    


```python
# Running simple linear regression for each predictor on its own to select top 5 features

# This cell is modified version of code provided in starter notebook by J.I.
# Statsmodels ~C() within OLS should be able to handle the zipcodes category without having to manually one-hot encode

import statsmodels.api as sm
import statsmodels.formula.api as smf
import scipy.stats as stats
import statsmodels.stats.api as sms


# log_price = np.log(df['price'])
# df['log_price'] = log_price

target_var = 'price'
col_names = df_rev.drop('price', axis=1).columns

# Create results list for saving the output statstics for each predictor
results = [['ind_var', 'r_squared', 'intercept', 'slope', 'p-value']]

for idx, val in enumerate(col_names):

    # Use the names of the columns to determine format of forumla
    if val.startswith('zip'):

        df_rev[val] = df_rev[val].astype('category').cat.as_ordered()
        f = f'{str(target_var)}~C({val})'

    else:

        f = f'{str(target_var)}~{val}'

    # Run the ols models
    model = smf.ols(formula=f, data=df_rev).fit()
    model.summary()

    # Append results
    results.append([val, model.rsquared, model.params[0],
                    model.params[1], model.pvalues[1]])

# Turn results into dataframe with correct index and columns
res_df = pd.DataFrame(results)
res_df.columns = res_df.iloc[0]
res_df = res_df[1:]
res_df.set_index('ind_var', inplace=True)
res_df.sort_values('r_squared', ascending=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>r_squared</th>
      <th>intercept</th>
      <th>slope</th>
      <th>p-value</th>
    </tr>
    <tr>
      <th>ind_var</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>zip_coded</td>
      <td>0.5319</td>
      <td>268055</td>
      <td>-32083.2</td>
      <td>0.01067</td>
    </tr>
    <tr>
      <td>grade</td>
      <td>0.288459</td>
      <td>-477864</td>
      <td>126042</td>
      <td>0</td>
    </tr>
    <tr>
      <td>sqft_living15_log</td>
      <td>0.209721</td>
      <td>-1.87508e+06</td>
      <td>312114</td>
      <td>0</td>
    </tr>
    <tr>
      <td>dist_dt</td>
      <td>0.162188</td>
      <td>592555</td>
      <td>-7.80051</td>
      <td>0</td>
    </tr>
    <tr>
      <td>sqft_above_log</td>
      <td>0.158279</td>
      <td>-1.08583e+06</td>
      <td>211020</td>
      <td>0</td>
    </tr>
    <tr>
      <td>bathrooms</td>
      <td>0.127073</td>
      <td>247880</td>
      <td>104613</td>
      <td>0</td>
    </tr>
    <tr>
      <td>bedrooms</td>
      <td>0.0600529</td>
      <td>259736</td>
      <td>59901.4</td>
      <td>7.31859e-226</td>
    </tr>
    <tr>
      <td>floors</td>
      <td>0.043065</td>
      <td>349555</td>
      <td>72790.8</td>
      <td>3.87036e-161</td>
    </tr>
    <tr>
      <td>basement_coded</td>
      <td>0.0415507</td>
      <td>425278</td>
      <td>79951.7</td>
      <td>2.00822e-155</td>
    </tr>
    <tr>
      <td>view_2</td>
      <td>0.0240708</td>
      <td>450446</td>
      <td>161128</td>
      <td>4.52162e-90</td>
    </tr>
    <tr>
      <td>view_4</td>
      <td>0.016622</td>
      <td>454376</td>
      <td>355624</td>
      <td>1.51291e-62</td>
    </tr>
    <tr>
      <td>view_3</td>
      <td>0.0143827</td>
      <td>453504</td>
      <td>205467</td>
      <td>2.63523e-54</td>
    </tr>
    <tr>
      <td>cond_4</td>
      <td>0.0100273</td>
      <td>450457</td>
      <td>70529.1</td>
      <td>2.58842e-38</td>
    </tr>
    <tr>
      <td>view_1</td>
      <td>0.00948158</td>
      <td>453945</td>
      <td>163390</td>
      <td>2.59526e-36</td>
    </tr>
    <tr>
      <td>sqft_lot15</td>
      <td>0.00491637</td>
      <td>486775</td>
      <td>-4.42055</td>
      <td>1.41784e-19</td>
    </tr>
    <tr>
      <td>sqft_lot</td>
      <td>0.00379082</td>
      <td>480529</td>
      <td>-3.45748</td>
      <td>1.9362e-15</td>
    </tr>
    <tr>
      <td>cond_1</td>
      <td>0.00351515</td>
      <td>456994</td>
      <td>-142185</td>
      <td>2.00219e-14</td>
    </tr>
    <tr>
      <td>yr_built</td>
      <td>0.00321778</td>
      <td>1.17604e+06</td>
      <td>-365.477</td>
      <td>2.49466e-13</td>
    </tr>
    <tr>
      <td>wf_coded</td>
      <td>0.00315658</td>
      <td>455744</td>
      <td>335547</td>
      <td>4.19418e-13</td>
    </tr>
    <tr>
      <td>cond_2</td>
      <td>0.00183085</td>
      <td>467194</td>
      <td>-17113.2</td>
      <td>3.40943e-08</td>
    </tr>
    <tr>
      <td>cond_3</td>
      <td>1.08176e-05</td>
      <td>456463</td>
      <td>-1424.07</td>
      <td>0.67154</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Revised model, based on individual R-squared, will include 'zip_coded', 'grade', 'sqft_living15_log', 'dist_dt', 'sqft_above_log'
import statsmodels.formula.api as smf

f_rev = 'price~C(zip_coded)+grade+sqft_living15_log+dist_dt+sqft_above_log'
model_rev = smf.ols(formula=f_rev, data=df_rev).fit()
model_rev.summary()
```




<table class="simpletable">
<caption>OLS Regression Results</caption>
<tr>
  <th>Dep. Variable:</th>          <td>price</td>      <th>  R-squared:         </th>  <td>   0.766</td>  
</tr>
<tr>
  <th>Model:</th>                   <td>OLS</td>       <th>  Adj. R-squared:    </th>  <td>   0.765</td>  
</tr>
<tr>
  <th>Method:</th>             <td>Least Squares</td>  <th>  F-statistic:       </th>  <td>   743.6</td>  
</tr>
<tr>
  <th>Date:</th>             <td>Sun, 27 Oct 2019</td> <th>  Prob (F-statistic):</th>   <td>  0.00</td>   
</tr>
<tr>
  <th>Time:</th>                 <td>18:57:33</td>     <th>  Log-Likelihood:    </th> <td>-2.1364e+05</td>
</tr>
<tr>
  <th>No. Observations:</th>      <td> 16624</td>      <th>  AIC:               </th>  <td>4.274e+05</td> 
</tr>
<tr>
  <th>Df Residuals:</th>          <td> 16550</td>      <th>  BIC:               </th>  <td>4.280e+05</td> 
</tr>
<tr>
  <th>Df Model:</th>              <td>    73</td>      <th>                     </th>      <td> </td>     
</tr>
<tr>
  <th>Covariance Type:</th>      <td>nonrobust</td>    <th>                     </th>      <td> </td>     
</tr>
</table>
<table class="simpletable">
<tr>
           <td></td>             <th>coef</th>     <th>std err</th>      <th>t</th>      <th>P>|t|</th>  <th>[0.025</th>    <th>0.975]</th>  
</tr>
<tr>
  <th>Intercept</th>          <td> -1.93e+06</td> <td> 2.86e+04</td> <td>  -67.572</td> <td> 0.000</td> <td>-1.99e+06</td> <td>-1.87e+06</td>
</tr>
<tr>
  <th>C(zip_coded)[T.1]</th>  <td> 3.783e+04</td> <td> 8915.971</td> <td>    4.243</td> <td> 0.000</td> <td> 2.04e+04</td> <td> 5.53e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.2]</th>  <td> 9829.5916</td> <td> 8031.561</td> <td>    1.224</td> <td> 0.221</td> <td>-5913.130</td> <td> 2.56e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.3]</th>  <td> 3.847e+05</td> <td> 1.39e+04</td> <td>   27.672</td> <td> 0.000</td> <td> 3.57e+05</td> <td> 4.12e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.4]</th>  <td>  2.33e+05</td> <td> 1.37e+04</td> <td>   16.978</td> <td> 0.000</td> <td> 2.06e+05</td> <td>  2.6e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.5]</th>  <td> 1.944e+05</td> <td> 1.11e+04</td> <td>   17.519</td> <td> 0.000</td> <td> 1.73e+05</td> <td> 2.16e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.6]</th>  <td> 1.451e+05</td> <td>  1.3e+04</td> <td>   11.137</td> <td> 0.000</td> <td>  1.2e+05</td> <td> 1.71e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.7]</th>  <td> 1.673e+05</td> <td> 1.08e+04</td> <td>   15.453</td> <td> 0.000</td> <td> 1.46e+05</td> <td> 1.88e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.8]</th>  <td> 1.334e+05</td> <td>  1.6e+04</td> <td>    8.312</td> <td> 0.000</td> <td> 1.02e+05</td> <td> 1.65e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.9]</th>  <td> 6.545e+04</td> <td> 1.07e+04</td> <td>    6.091</td> <td> 0.000</td> <td> 4.44e+04</td> <td> 8.65e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.10]</th> <td> 1.166e+05</td> <td> 1.78e+04</td> <td>    6.561</td> <td> 0.000</td> <td> 8.17e+04</td> <td> 1.51e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.11]</th> <td> 6.735e+04</td> <td> 9785.368</td> <td>    6.883</td> <td> 0.000</td> <td> 4.82e+04</td> <td> 8.65e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.12]</th> <td> 1.818e+05</td> <td> 9.29e+04</td> <td>    1.958</td> <td> 0.050</td> <td> -201.001</td> <td> 3.64e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.13]</th> <td> -522.9736</td> <td> 7051.772</td> <td>   -0.074</td> <td> 0.941</td> <td>-1.43e+04</td> <td> 1.33e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.14]</th> <td> 1.696e+05</td> <td> 2.09e+04</td> <td>    8.101</td> <td> 0.000</td> <td> 1.29e+05</td> <td> 2.11e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.15]</th> <td> 1.569e+05</td> <td> 9728.419</td> <td>   16.133</td> <td> 0.000</td> <td> 1.38e+05</td> <td> 1.76e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.16]</th> <td> 4.545e+04</td> <td> 1.04e+04</td> <td>    4.364</td> <td> 0.000</td> <td>  2.5e+04</td> <td> 6.59e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.17]</th> <td> 1.634e+05</td> <td> 8562.281</td> <td>   19.082</td> <td> 0.000</td> <td> 1.47e+05</td> <td>  1.8e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.18]</th> <td>-2.693e+04</td> <td> 8404.799</td> <td>   -3.204</td> <td> 0.001</td> <td>-4.34e+04</td> <td>-1.05e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.19]</th> <td>-3.685e+04</td> <td> 8813.063</td> <td>   -4.181</td> <td> 0.000</td> <td>-5.41e+04</td> <td>-1.96e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.20]</th> <td>-2.307e+04</td> <td> 1.09e+04</td> <td>   -2.121</td> <td> 0.034</td> <td>-4.44e+04</td> <td>-1752.325</td>
</tr>
<tr>
  <th>C(zip_coded)[T.21]</th> <td> 2.132e+05</td> <td> 1.12e+04</td> <td>   19.060</td> <td> 0.000</td> <td> 1.91e+05</td> <td> 2.35e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.22]</th> <td> 9.255e+04</td> <td> 1.01e+04</td> <td>    9.195</td> <td> 0.000</td> <td> 7.28e+04</td> <td> 1.12e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.23]</th> <td> 3.001e+04</td> <td> 7010.131</td> <td>    4.282</td> <td> 0.000</td> <td> 1.63e+04</td> <td> 4.38e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.24]</th> <td> 4.832e+05</td> <td> 3.97e+04</td> <td>   12.181</td> <td> 0.000</td> <td> 4.05e+05</td> <td> 5.61e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.25]</th> <td> 3.128e+05</td> <td> 1.42e+04</td> <td>   21.964</td> <td> 0.000</td> <td> 2.85e+05</td> <td> 3.41e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.26]</th> <td> -380.1147</td> <td> 7118.389</td> <td>   -0.053</td> <td> 0.957</td> <td>-1.43e+04</td> <td> 1.36e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.27]</th> <td> 1.796e+05</td> <td>  1.1e+04</td> <td>   16.302</td> <td> 0.000</td> <td> 1.58e+05</td> <td> 2.01e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.28]</th> <td> 1.672e+05</td> <td> 9547.519</td> <td>   17.514</td> <td> 0.000</td> <td> 1.49e+05</td> <td> 1.86e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.29]</th> <td>  1.92e+05</td> <td> 9058.660</td> <td>   21.194</td> <td> 0.000</td> <td> 1.74e+05</td> <td>  2.1e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.30]</th> <td>-4.045e+04</td> <td> 1.02e+04</td> <td>   -3.962</td> <td> 0.000</td> <td>-6.05e+04</td> <td>-2.04e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.31]</th> <td> 1.149e+04</td> <td> 1.07e+04</td> <td>    1.078</td> <td> 0.281</td> <td>-9397.646</td> <td> 3.24e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.32]</th> <td>-2.434e+04</td> <td> 8710.341</td> <td>   -2.794</td> <td> 0.005</td> <td>-4.14e+04</td> <td>-7262.583</td>
</tr>
<tr>
  <th>C(zip_coded)[T.33]</th> <td> 2288.3092</td> <td> 9542.371</td> <td>    0.240</td> <td> 0.810</td> <td>-1.64e+04</td> <td>  2.1e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.34]</th> <td> 1.405e+05</td> <td> 8304.063</td> <td>   16.917</td> <td> 0.000</td> <td> 1.24e+05</td> <td> 1.57e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.35]</th> <td> 1.251e+05</td> <td> 2.22e+04</td> <td>    5.624</td> <td> 0.000</td> <td> 8.15e+04</td> <td> 1.69e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.36]</th> <td> 8.862e+04</td> <td> 1.08e+04</td> <td>    8.218</td> <td> 0.000</td> <td> 6.75e+04</td> <td>  1.1e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.37]</th> <td>   1.5e+05</td> <td> 9143.252</td> <td>   16.409</td> <td> 0.000</td> <td> 1.32e+05</td> <td> 1.68e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.38]</th> <td> 1.782e+05</td> <td> 1.09e+04</td> <td>   16.396</td> <td> 0.000</td> <td> 1.57e+05</td> <td> 1.99e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.39]</th> <td>  1.23e+05</td> <td> 1.89e+04</td> <td>    6.494</td> <td> 0.000</td> <td> 8.59e+04</td> <td>  1.6e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.40]</th> <td>-1.595e+04</td> <td> 8116.422</td> <td>   -1.965</td> <td> 0.049</td> <td>-3.19e+04</td> <td>  -42.355</td>
</tr>
<tr>
  <th>C(zip_coded)[T.41]</th> <td> 2.383e+05</td> <td> 1.73e+04</td> <td>   13.807</td> <td> 0.000</td> <td> 2.04e+05</td> <td> 2.72e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.42]</th> <td> 1.881e+05</td> <td> 1.29e+04</td> <td>   14.632</td> <td> 0.000</td> <td> 1.63e+05</td> <td> 2.13e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.43]</th> <td> 2.507e+05</td> <td> 1.44e+04</td> <td>   17.451</td> <td> 0.000</td> <td> 2.23e+05</td> <td> 2.79e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.44]</th> <td>-1630.9575</td> <td> 1.34e+04</td> <td>   -0.122</td> <td> 0.903</td> <td>-2.78e+04</td> <td> 2.45e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.45]</th> <td> 1.846e+05</td> <td> 1.36e+04</td> <td>   13.574</td> <td> 0.000</td> <td> 1.58e+05</td> <td> 2.11e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.46]</th> <td>-1.275e+04</td> <td> 1.46e+04</td> <td>   -0.874</td> <td> 0.382</td> <td>-4.14e+04</td> <td> 1.59e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.47]</th> <td> 2.564e+05</td> <td> 1.73e+04</td> <td>   14.862</td> <td> 0.000</td> <td> 2.23e+05</td> <td>  2.9e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.48]</th> <td> 2.697e+05</td> <td> 1.57e+04</td> <td>   17.143</td> <td> 0.000</td> <td> 2.39e+05</td> <td> 3.01e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.49]</th> <td> 2.094e+05</td> <td> 1.23e+04</td> <td>   16.954</td> <td> 0.000</td> <td> 1.85e+05</td> <td> 2.34e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.50]</th> <td> 1.737e+05</td> <td> 1.42e+04</td> <td>   12.258</td> <td> 0.000</td> <td> 1.46e+05</td> <td> 2.01e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.51]</th> <td> 2.089e+05</td> <td> 1.23e+04</td> <td>   17.035</td> <td> 0.000</td> <td> 1.85e+05</td> <td> 2.33e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.52]</th> <td> 4.727e+04</td> <td> 1.29e+04</td> <td>    3.665</td> <td> 0.000</td> <td>  2.2e+04</td> <td> 7.25e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.53]</th> <td>  2.55e+05</td> <td> 1.55e+04</td> <td>   16.406</td> <td> 0.000</td> <td> 2.25e+05</td> <td> 2.86e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.54]</th> <td> 1.404e+05</td> <td> 1.55e+04</td> <td>    9.081</td> <td> 0.000</td> <td>  1.1e+05</td> <td> 1.71e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.55]</th> <td> 9.313e+04</td> <td> 1.15e+04</td> <td>    8.126</td> <td> 0.000</td> <td> 7.07e+04</td> <td> 1.16e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.56]</th> <td> 8.968e+04</td> <td> 1.34e+04</td> <td>    6.684</td> <td> 0.000</td> <td> 6.34e+04</td> <td> 1.16e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.57]</th> <td>  6.08e+04</td> <td> 1.06e+04</td> <td>    5.716</td> <td> 0.000</td> <td> 3.99e+04</td> <td> 8.16e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.58]</th> <td> 1.492e+05</td> <td> 1.35e+04</td> <td>   11.090</td> <td> 0.000</td> <td> 1.23e+05</td> <td> 1.76e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.59]</th> <td> 9.411e+04</td> <td>  1.5e+04</td> <td>    6.277</td> <td> 0.000</td> <td> 6.47e+04</td> <td> 1.24e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.60]</th> <td> 1.335e+04</td> <td> 1.23e+04</td> <td>    1.085</td> <td> 0.278</td> <td>-1.08e+04</td> <td> 3.75e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.61]</th> <td>-2.936e+04</td> <td> 1.52e+04</td> <td>   -1.935</td> <td> 0.053</td> <td>-5.91e+04</td> <td>  385.669</td>
</tr>
<tr>
  <th>C(zip_coded)[T.62]</th> <td> 6.859e+04</td> <td> 1.01e+04</td> <td>    6.797</td> <td> 0.000</td> <td> 4.88e+04</td> <td> 8.84e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.63]</th> <td> 3.865e+04</td> <td> 1.13e+04</td> <td>    3.418</td> <td> 0.001</td> <td> 1.65e+04</td> <td> 6.08e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.64]</th> <td>-4.968e+04</td> <td> 1.21e+04</td> <td>   -4.114</td> <td> 0.000</td> <td>-7.33e+04</td> <td> -2.6e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.65]</th> <td> 1.348e+05</td> <td> 1.15e+04</td> <td>   11.678</td> <td> 0.000</td> <td> 1.12e+05</td> <td> 1.57e+05</td>
</tr>
<tr>
  <th>C(zip_coded)[T.66]</th> <td>-1.508e+04</td> <td> 1.17e+04</td> <td>   -1.285</td> <td> 0.199</td> <td>-3.81e+04</td> <td> 7919.998</td>
</tr>
<tr>
  <th>C(zip_coded)[T.67]</th> <td>-3.369e+04</td> <td>  1.2e+04</td> <td>   -2.800</td> <td> 0.005</td> <td>-5.73e+04</td> <td>-1.01e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.68]</th> <td>-1405.8434</td> <td> 9051.750</td> <td>   -0.155</td> <td> 0.877</td> <td>-1.91e+04</td> <td> 1.63e+04</td>
</tr>
<tr>
  <th>C(zip_coded)[T.69]</th> <td> 2.361e+05</td> <td>  1.4e+04</td> <td>   16.892</td> <td> 0.000</td> <td> 2.09e+05</td> <td> 2.64e+05</td>
</tr>
<tr>
  <th>grade</th>              <td> 3.991e+04</td> <td> 1280.741</td> <td>   31.162</td> <td> 0.000</td> <td> 3.74e+04</td> <td> 4.24e+04</td>
</tr>
<tr>
  <th>sqft_living15_log</th>  <td> 1.442e+05</td> <td> 3777.951</td> <td>   38.164</td> <td> 0.000</td> <td> 1.37e+05</td> <td> 1.52e+05</td>
</tr>
<tr>
  <th>dist_dt</th>            <td>   -6.3546</td> <td>    0.436</td> <td>  -14.572</td> <td> 0.000</td> <td>   -7.209</td> <td>   -5.500</td>
</tr>
<tr>
  <th>sqft_above_log</th>     <td> 1.406e+05</td> <td> 3076.503</td> <td>   45.712</td> <td> 0.000</td> <td> 1.35e+05</td> <td> 1.47e+05</td>
</tr>
</table>
<table class="simpletable">
<tr>
  <th>Omnibus:</th>       <td>1883.370</td> <th>  Durbin-Watson:     </th> <td>   1.965</td>
</tr>
<tr>
  <th>Prob(Omnibus):</th>  <td> 0.000</td>  <th>  Jarque-Bera (JB):  </th> <td>4964.571</td>
</tr>
<tr>
  <th>Skew:</th>           <td> 0.642</td>  <th>  Prob(JB):          </th> <td>    0.00</td>
</tr>
<tr>
  <th>Kurtosis:</th>       <td> 5.349</td>  <th>  Cond. No.          </th> <td>2.60e+06</td>
</tr>
</table><br/><br/>Warnings:<br/>[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.<br/>[2] The condition number is large, 2.6e+06. This might indicate that there are<br/>strong multicollinearity or other numerical problems.



### Revised model uses the following five features: 'zip_coded', 'grade', 'sqft_living_15_log', 'dist_dt', and 'sqft_above_log'
#### -R-squared = 0.77 (R-squared and adj-R-squared are almost identical)
#### -p-value = 0.00
#### -Some more skewness and kurtosis than in the initial model; I will explore this below

## 1) Assess normality of Residuals using Histograms and Q-Q Plots


```python
plt.figure(figsize=(8, 5))
plt.hist(model_rev.resid, bins=100)
plt.xlabel('Residuals (Price in $)')
plt.ylabel('Frequency')
plt.title('Distribution of Revised Model Residuals')
plt.show()
```


![png](output_99_0.png)



```python
sm.graphics.qqplot(model_rev.resid, line='45', fit=True)
plt.title('Q-Q Plot of Revised Model Residuals')
plt.show()
```


![png](output_100_0.png)



```python
rev_res_x = list(range(0, len(X_rev)))

plt.figure(figsize=(8, 5))
plt.scatter(rev_res_x, model_rev.resid, s=1)
plt.hlines(y=0, xmin=0, xmax=len(X_rev), color='red')
plt.xlabel('Observation')
plt.ylabel('Residuals (Price in $)')
plt.show()
```


![png](output_101_0.png)


### CONCLUSION: The histogram indicates some right-skew, but this does not seem alarming. The model residuals appear to be homoscedastic, and the Q-Q plot indicates that the distribution is not quite normal.

### REVISED MODEL Train-Test-Split Validation


```python
rev_predictors = df_rev[['zip_coded', 'grade',
                         'sqft_living15_log', 'dist_dt', 'sqft_above_log']]
X_rev_train, X_rev_test, y_rev_train, y_rev_test = train_test_split(
    rev_predictors, y_rev, test_size=0.25)
```


```python
df_rev_train = pd.concat([X_rev_train, y_rev_train], axis=1)
df_rev_test = pd.concat([X_rev_test, y_rev_test], axis=1)

y_hat_rev_train = model_rev.predict(X_rev_train)
y_hat_rev_test = model_rev.predict(X_rev_test)
```


```python
train_rev_rmse = np.sqrt(mean_squared_error(y_rev_train, y_hat_rev_train))
test_rev_rmse = np.sqrt(mean_squared_error(y_rev_test, y_hat_rev_test))
print('Train Root Mean Squarred Error - Revised Model ($ Price):', train_rev_rmse)
print('Test Root Mean Squarred Error - Revised Model($ Price):', test_rev_rmse)
```

    Train Root Mean Squarred Error - Revised Model ($ Price): 92324.69677351491
    Test Root Mean Squarred Error - Revised Model($ Price): 92115.63224518576
    

#### The revised model Train and Test RMSE's are nearly identical. This tells us that our revised model is not being undertrained or overtained on the train-test-split - there is a good balance here.

#### The train-test-split tells us that the standard deviation of revised model residuals is $92-93k.

# CONCLUSIONS & RECOMMENDATIONS
## Conclusion
### The most important predictors of sales price in King County are: zip code ('zip_coded'), construction/design grade ('grade'), size of neighborhood interior living space ('sqft_living15_log'), distance from downtown Seattle ('dist_dt'), and size of house above ground level ('sqft_above_log). Grade, size of neighborhood interior living space (log transformed), and size of house above ground (log transformed) have a positive relationship with price. Distance from downtown Seattle has a negative relationship with price. Zip code is more complex in interpretation - however, the zip code in which a home is located is generally a good predictor of price. These five features together can explain 77% of the variability in King County housing prices.

## Recommendations
### While zip code and distance from downtown Seattle are factors that are largely outside of homeowners' control, they could ensure that desireable locations are emphasized during the selling process. Homeowners looking to maximize sales profit can also make additions to their homes to increase size, as well as use high quality construction and design in their initial home build or renovations.

## Future Work
### Given more time, I would explore a method to more judiciously remove outliers in the data set. Using the IQR score method for each variable resulted in loss of ~23% of original data. 
### I would explore whether zip codes could be binned into "regions" of several zip codes, to see if these would produce more signifcant or interpretable modeling results.

# Code for Figures for Presentation


```python
# Figure #1: Zip Code vs Price - Seaborn boxenplot

fig_1 = plt.figure(figsize=(20, 10))
sns.set_context('talk')
sns.set_style('whitegrid')
sns.boxenplot(x=X_rev.zip_coded, y=y_rev, palette='colorblind')
plt.title('Sale Price by Zip Code')
plt.ylabel('Price ($)')
plt.xlabel('')
plt.xticks(ticks=[])
fig_1.show()
```


![png](output_110_0.png)



```python
# Figure #2: Final Model Selected Features Plots vs. Price
# Grade, sqft_living_15_log, sqft_above_log, dist_dt - Seaborn Regplots

fig_2 = plt.figure(figsize=(18, 10))
sns.set_context('paper')
sns.set_style('whitegrid')
ax1 = plt.subplot(221)
ax1 = sns.regplot(x=X_rev.grade, y=y_rev, line_kws={
                  "color": "black", 'alpha': 0.2}, color='mediumaquamarine', scatter_kws={'alpha': 0.5, 's': 15})
plt.title('Construction/Design Grade', fontsize=15)
plt.ylabel('Price ($)', fontsize=12)
plt.xlabel('Grade', fontsize=12)
ax2 = plt.subplot(222)
ax2 = sns.regplot(x=X_rev.sqft_living15_log, y=y_rev, line_kws={
                  "color": "black", 'alpha': 0.2}, color='dodgerblue', scatter_kws={'alpha': 0.5, 's': 15})
plt.title('Living Area of Neighbors', fontsize=15)
plt.ylabel('Price ($)', fontsize=12)
plt.xlabel('Area (log(sqft))', fontsize=12)
ax3 = plt.subplot(223)
ax3 = sns.regplot(x=X_rev.dist_dt*0.000621371, y=y_rev, line_kws={
                  "color": "black", 'alpha': 0.2}, color='mediumpurple', scatter_kws={'alpha': 0.5, 's': 15})
plt.title('Distance from Downtown Seattle', fontsize=15)
plt.ylabel('Price ($)', fontsize=12)
plt.xlabel('Miles', fontsize=12)
ax4 = plt.subplot(224)
ax4 = sns.regplot(x=X_rev.sqft_above_log, y=y_rev, line_kws={
                  "color": "black", 'alpha': 0.2}, color='lightcoral', scatter_kws={'alpha': 0.5, 's': 15})
plt.title('Home Size (Excl. Basement)', fontsize=15)
plt.ylabel('Price ($)', fontsize=12)
plt.xlabel('Area (log(sqft))', fontsize=12)

plt.subplots_adjust(hspace=0.3)
fig_2.show()
```


![png](output_111_0.png)

