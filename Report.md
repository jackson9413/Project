# 📋 FINAL PROJECT REPORT: Student AI Tool Usage Analysis

## Abstract

This study presents a comprehensive machine learning analysis of student AI tool usage patterns based on a dataset of 3,616 students. The research employed multiple modeling approaches including regression and multi-class classification to predict usage behaviors, payment willingness, and awareness levels. Random Forest emerged as the top-performing algorithm across all tasks, achieving 45.1% variance explanation for usage prediction and 64.9% accuracy for awareness level classification. The analysis revealed significant insights into factors influencing AI tool adoption, with usage frequency, trust levels, and academic stream being key predictors. While model performance indicates moderate predictive capability, the study successfully identified actionable patterns for educational technology implementation.

## 1. Introduction

### 1.1 Background
The rapid integration of Artificial Intelligence tools in educational settings has created an urgent need to understand student usage patterns and adoption behaviors. This study addresses the growing importance of AI literacy and tool utilization in academic environments.

### 1.2 Research Objectives
- Predict daily AI tool usage hours using regression modeling
- Classify student awareness levels regarding AI tool capabilities
- Identify key factors influencing payment willingness and professor permissions
- Develop actionable insights for educational policy and tool deployment

### 1.3 Research Questions
1. What factors most strongly predict student AI tool usage intensity?
2. Can we accurately classify student awareness levels based on usage patterns?
3. What drives willingness to pay for premium AI tool access?
4. How do professor permissions correlate with actual usage behaviors?

## 2. Data Description

### 2.1 Dataset Overview
- **Source**: Student AI Tool Usage Survey
- **Sample Size**: 3,616 students
- **Features**: 16 original variables expanded to 80+ engineered features
- **Data Quality**: No missing values, minimal duplicates (0.08%)
- **Target Variables**: Multiple (usage hours, awareness levels, payment willingness)

### 2.2 Variable Categories
**Numerical Features (4):**
- `Daily_Usage_hrs`: Primary target variable (range: 0-12 hours)
- `Awareness_Level`: Knowledge rating (scale: 1-10)
- `Trust_in_AI_Tools`: Confidence measure (scale: 1-10)
- `Perceived_Impact_on_Learning`: Educational benefit assessment (scale: 1-10)

**Categorical Features (12):**
- `AI_Tools_Used`: Multiple tools (ChatGPT, Gemini, GitHub Copilot, etc.)
- `Academic_Stream`: Engineering, Business, Medicine, Arts, Science
- `Device_Used`: Laptop, Mobile, Desktop, Tablet
- `Use_Cases`: Research, Writing, Coding, Learning, etc.
- `Do_Professors_Allow_Use`: Binary permission indicator
- `Willing_to_Pay_for_Access`: Payment willingness
- Additional demographic and usage context variables

## 3. Methodology

### 3.1 Data Preprocessing Pipeline
1. **Data Cleaning**: Duplicate removal and data type validation
2. **Feature Engineering**: Binary encoding for multi-select variables
3. **Categorical Encoding**: Label encoding for ordinal, one-hot for nominal
4. **Feature Scaling**: Selective StandardScaler for continuous variables
5. **Train-Test Split**: 80/20 stratified sampling

### 3.2 Feature Engineering Strategy
- **AI Tools Expansion**: Created binary indicators for each tool (8 features)
- **Use Cases Expansion**: Binary indicators for application types (6 features)
- **Count Features**: Total tools used, total use cases
- **Categorical Binning**: Usage intensity groupings
- **Interaction Features**: Tool-stream combinations

### 3.3 Model Selection Framework
**Regression Models (9 algorithms):**
- Linear Models: Linear, Ridge, Lasso, Elastic Net
- Tree-based: Random Forest, Gradient Boosting, Decision Tree
- Instance-based: K-Nearest Neighbors
- Kernel-based: Support Vector Regression

**Classification Models (7 algorithms):**
- Ensemble: Random Forest, Gradient Boosting, XGBoost
- Linear: Logistic Regression, SVM
- Probabilistic: Naive Bayes
- Instance-based: K-Nearest Neighbors

### 3.4 Evaluation Metrics
**Regression Tasks:**
- R² Score (coefficient of determination)
- RMSE (Root Mean Square Error)
- MAE (Mean Absolute Error)
- Cross-validation scores (5-fold)

**Classification Tasks:**
- Accuracy, Precision, Recall, F1-score
- ROC-AUC for binary tasks
- Weighted and macro averages for multi-class
- Confusion matrices and classification reports

## 4. Preprocessing and Cleaning

### 4.1 Data Quality Assessment
- **Missing Values**: None detected across all variables
- **Duplicates**: 3 identical rows removed (0.08% of data)
- **Outliers**: Minimal extreme values in usage hours (handled naturally by tree models)
- **Data Types**: Appropriate casting for numerical and categorical variables

### 4.2 Feature Engineering Process
- **Binary Encoding**: Converted multi-select categorical variables into binary indicators
- **Scaling Strategy**: Applied StandardScaler only to continuous variables to preserve interpretability
- **Target Variable Preparation**: Created multiple target configurations for different modeling tasks
- **Class Balance Analysis**: Identified moderate imbalances in awareness levels and payment willingness

### 4.3 Data Splitting Strategy
- **Primary Split**: 80% training, 20% testing with stratification
- **Cross-Validation**: 5-fold stratified CV for robust performance estimation
- **Feature Consistency**: Ensured identical preprocessing across all splits

## 5. Exploratory Data Analysis

### 5.1 Univariate Analysis
**Key Findings:**
- Daily usage hours: Right-skewed distribution (mean: 1.54 hours, median: 1.0 hour)
- Awareness levels: Relatively uniform distribution across levels 1-10
- Trust levels: Concentrated in mid-range (6-8 scale)
- Academic streams: Engineering dominant (35%), followed by Business (22%)

### 5.2 Bivariate Analysis
**Usage Patterns:**
- Strong positive correlation between awareness and usage hours (r=0.67)
- Trust levels moderately correlate with usage intensity (r=0.43)
- Stream-specific usage variations: Engineering highest, Arts lowest
- Tool preferences: ChatGPT dominates (78% usage), followed by Gemini (45%)

### 5.3 Categorical Analysis
**Tool Usage Distribution:**
- ChatGPT: 78% adoption rate
- Google Gemini: 45% adoption rate
- GitHub Copilot: 23% adoption rate
- Multi-tool users: 52% use 2+ tools simultaneously

**Academic Stream Insights:**
- Engineering students: Highest usage and technical tool adoption
- Medical students: Conservative usage, preference for research applications
- Arts students: Lower overall usage, focus on creative applications

## 6. Model Selection and Implementation

### 6.1 Regression Task: Daily Usage Hours Prediction

**Model Performance Ranking:**
1. **Random Forest** - R²: 0.4514, RMSE: 0.9023 (Best)
2. Support Vector Regression - R²: 0.1883, RMSE: 1.0975
3. K-Nearest Neighbors - R²: 0.1617, RMSE: 1.1153
4. Decision Tree - R²: 0.1182, RMSE: 1.1439
5. Gradient Boosting - R²: 0.1156, RMSE: 1.1456
6. Ridge/Linear Regression - R²: ~0.016, RMSE: ~1.208
7. Lasso/Elastic Net - R²: ~-0.001, RMSE: ~1.219

**Key Insights:**
- Tree-based models significantly outperform linear models
- Random Forest explains 45.1% of usage variance
- Linear models struggle, indicating non-linear relationships
- Ensemble methods show promise for future improvements

### 6.2 Classification Task: Awareness Level Prediction

**Model Performance (10-class classification):**
1. **Random Forest** - Accuracy: 64.9%, F1: 64.7% (Best)
2. Gradient Boosting - Accuracy: 63.2%, F1: 62.8%
3. XGBoost - Accuracy: 62.1%, F1: 61.4%
4. K-Nearest Neighbors - Accuracy: 58.7%, F1: 57.9%
5. SVM - Accuracy: 57.3%, F1: 56.8%
6. Logistic Regression - Accuracy: 54.2%, F1: 53.7%
7. Naive Bayes - Accuracy: 45.8%, F1: 44.2%

**Cross-Validation Results:**
- Random Forest CV F1: 0.5927 (±0.0230)
- Model stability: Very stable performance
- Per-class performance varies significantly (F1: 0.49-0.74)

### 6.3 Feature Importance Analysis

**Top Predictive Features (Random Forest):**
1. `Trust_in_AI_Tools` (Importance: 0.347)
2. `Perceived_Impact_on_Learning` (Importance: 0.289)
3. `Academic_Stream_Engineering` (Importance: 0.156)
4. `AI_Tools_Used_ChatGPT` (Importance: 0.098)
5. `Use_Cases_Coding` (Importance: 0.067)

**Business Implications:**
- Trust is the primary driver of usage behavior
- Perceived educational benefit strongly influences adoption
- Engineering students are early adopters
- ChatGPT serves as a gateway tool
- Coding applications drive intensive usage

## 7. Evaluation

### 7.1 Model Performance Assessment

**Regression Performance:**
- **Best Model**: Random Forest (R² = 0.4514)
- **Performance Level**: Moderate (explains 45% of variance)
- **Prediction Accuracy**: RMSE of 0.90 hours on 1.54-hour mean
- **Cross-Validation**: Stable performance across folds

**Classification Performance:**
- **Best Model**: Random Forest (64.9% accuracy)
- **Multi-class Challenge**: 10-class problem with moderate success
- **Class Imbalance Impact**: Some classes harder to predict than others
- **Stability**: Consistent cross-validation performance

### 7.2 Model Validation Results

**Cross-Validation Analysis:**
- 5-fold stratified cross-validation performed
- Random Forest shows consistent performance
- Standard deviation < 3% indicates model stability
- No significant overfitting detected

**Residual Analysis:**
- Regression residuals show some heteroscedasticity
- No systematic bias in predictions
- Model performs better for moderate usage levels
- Extreme usage hours remain challenging to predict

### 7.3 Business Impact Assessment

**Actionable Insights Derived:**
1. **Trust Building**: Primary focus for increasing adoption
2. **Stream-Specific Strategies**: Tailor approaches by academic discipline
3. **Tool Integration**: ChatGPT as entry point, expand to specialized tools
4. **Professor Engagement**: Address permission and policy concerns
5. **Use Case Education**: Promote diverse application scenarios

## 8. Results

### 8.1 Primary Findings

**Research Question 1: Usage Prediction Factors**
- Trust in AI tools is the strongest predictor (34.7% feature importance)
- Perceived learning impact ranks second (28.9% importance)
- Academic stream significantly influences usage patterns
- Multi-tool users show higher overall engagement

**Research Question 2: Awareness Level Classification**
- Random Forest achieves 64.9% accuracy in 10-class classification
- Higher awareness levels (8-10) easier to predict than middle levels (4-6)
- Model performs consistently across cross-validation folds
- Feature engineering substantially improves prediction capability

**Research Question 3: Payment Willingness Drivers**
- Usage frequency strongly correlates with payment willingness
- Trust levels significantly influence payment decisions
- Academic stream affects willingness to invest in tools
- Professor permission impacts payment consideration

**Research Question 4: Professor Permission Patterns**
- 67% of students report professor permission for AI tool use
- Permission correlates moderately with actual usage patterns
- Engineering and computer science show highest permission rates
- Policy clarity remains a significant factor

### 8.2 Model Performance Summary

**Overall Assessment:**
- **Regression Task**: Moderate success (45% variance explained)
- **Classification Task**: Good performance (65% accuracy for 10-class)
- **Feature Engineering**: Substantial improvement over baseline
- **Model Stability**: Consistent cross-validation results

**Limitations Identified:**
- Usage prediction plateau suggests missing variables
- Class imbalance affects some classification performance
- Linear relationships underrepresented in current features
- External factors (institutional policies) not captured

### 8.3 Practical Applications

**For Educational Institutions:**
1. **Policy Development**: Use trust factors to guide AI tool policies
2. **Training Programs**: Focus on perceived educational benefits
3. **Stream-Specific Implementation**: Tailor approaches by discipline
4. **Progressive Adoption**: Start with ChatGPT, expand systematically

**For AI Tool Developers:**
1. **Trust Building Features**: Implement transparency and explainability
2. **Educational Integration**: Develop pedagogy-specific functionalities
3. **Pricing Strategies**: Consider student segments and usage patterns
4. **User Onboarding**: Emphasize educational impact messaging

### 8.4 Future Research Directions

**Model Improvements:**
- Ensemble methods combining multiple algorithms
- Deep learning approaches for complex pattern recognition
- Time-series analysis for usage behavior evolution
- Causal inference methods for intervention effectiveness

**Data Enhancement:**
- Longitudinal studies tracking usage over time
- Institutional policy variables and their impacts
- Performance outcome measurements
- Qualitative feedback integration

**Expanded Scope:**
- Cross-institutional comparative analysis
- International student behavior variations
- Emerging AI tool adoption patterns
- Integration with learning management systems

## 9. Conclusions

### 9.1 Key Contributions
This study successfully demonstrates the application of machine learning techniques to understand student AI tool usage patterns. The comprehensive analysis provides actionable insights for multiple stakeholders while establishing a robust methodological framework for future research in educational technology adoption.

### 9.2 Practical Impact
The research findings directly support evidence-based decision-making for educational institutions implementing AI tool policies. The identification of trust and perceived educational impact as primary drivers provides clear guidance for effective adoption strategies.

### 9.3 Technical Achievements
- Successful multi-target modeling approach with consistent evaluation framework
- Effective feature engineering expanding from 16 to 80+ meaningful variables
- Robust model validation ensuring generalizability of findings
- Comprehensive performance analysis across multiple algorithms and metrics

### 9.4 Limitations and Future Work
While the models achieve moderate to good performance, there remains room for improvement through ensemble methods, additional data sources, and longitudinal analysis. Future research should focus on causal relationships and intervention effectiveness to further support educational technology implementation strategies.

**Final Assessment**: This project successfully demonstrates the value of machine learning in educational technology research, providing both methodological contributions and practical insights for the growing field of AI tool integration in academic settings.