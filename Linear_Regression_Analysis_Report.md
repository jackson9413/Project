# Linear Regression Analysis Report
## Daily Usage Hours Prediction Model

### Executive Summary
This report presents the results of comprehensive linear regression modeling for predicting `Daily_Usage_Hours` in student AI tool usage. Four linear regression variants were trained and evaluated using the optimized dataset with 28 features.

### Model Performance Summary

| Model | Test R² | Test RMSE | Test MAE | CV R² (mean±std) | Status |
|-------|---------|-----------|----------|------------------|--------|
| **ElasticNet** | **0.0181** | **1.2071** | **1.0543** | **0.0108±0.0089** | **Best** |
| Ridge Regression | 0.0166 | 1.2080 | 1.0527 | 0.0075±0.0106 | Good |
| Linear Regression | 0.0159 | 1.2084 | 1.0526 | 0.0065±0.0107 | Baseline |
| Lasso Regression | 0.0008 | 1.2177 | 1.0672 | -0.0036±0.0061 | Poor |

### Key Findings

#### 1. **Model Performance**
- **Best Model**: ElasticNet with 1.8% variance explained
- **Prediction Accuracy**: ±1.05 hours average error
- **Performance Grade**: **POOR** - Model explains less than 10% of variance

#### 2. **Feature Importance (ElasticNet)**
**Top Positive Predictors** (increase usage):
1. `uses_doubt_solving` (+0.0713)
2. `Impact_on_Grades` (+0.0513)
3. `uses_exam_preparation` (+0.0427)
4. `Willing_to_Pay_for_Access_encoded` (+0.0333)
5. `preferred_ai_tool_ChatGPT` (+0.0276)

**Top Negative Predictors** (decrease usage):
1. `ai_tool_copilot` (-0.0857)
2. `preferred_ai_tool_Other` (-0.0495)
3. `device_used_Tablet` (-0.0286)

#### 3. **Model Validation Results**
- **Linearity**: ❌ Weak correlation (r=0.1355)
- **Normality**: ⚠️ Residuals deviate from normal distribution
- **Homoscedasticity**: ✅ Assumption satisfied
- **Prediction Accuracy**: 58.5% within 1 standard deviation

### Business Insights

#### Usage Drivers
1. **Academic Purpose**: Students using AI for doubt-solving and exam preparation tend to use tools more
2. **Grade Impact**: Perceived positive impact on grades correlates with higher usage
3. **Payment Willingness**: Students willing to pay show higher engagement
4. **Tool Preference**: ChatGPT users show higher usage patterns

#### Usage Inhibitors
1. **Copilot Users**: Surprisingly show lower daily usage (specialized use case)
2. **Tablet Users**: Lower usage compared to desktop/laptop users
3. **Alternative Tools**: Users preferring "other" tools show reduced usage

### Technical Analysis

#### Model Selection
- **ElasticNet** selected as best linear model due to:
  - Highest R² score (0.0181)
  - Balanced L1/L2 regularization
  - Feature selection capability (10 features eliminated)
  - Robust cross-validation performance

#### Regularization Impact
- **Best Parameters**: α=0.1, l1_ratio=0.1
- **Feature Selection**: 18 of 28 features retained
- **Overfitting**: Minimal (low difference between train/test scores)

### Limitations and Recommendations

#### Model Limitations
1. **Poor Predictive Power**: Only 1.8% variance explained
2. **Linear Assumption**: Weak linear relationship suggests non-linear patterns
3. **Feature Limitations**: Current features insufficient for accurate prediction

#### Recommendations
1. **Model Strategy**: 
   - Consider non-linear models (Random Forest, Neural Networks)
   - Explore polynomial features and interactions
   - Implement ensemble methods

2. **Data Enhancement**:
   - Collect behavioral data (session length, frequency patterns)
   - Add temporal features (time of day, day of week)
   - Include contextual variables (academic pressure, assignment deadlines)

3. **Feature Engineering**:
   - Create interaction terms between usage patterns and tools
   - Develop composite behavioral scores
   - Add demographic and academic performance features

### Conclusion

While the linear regression models provide interpretable insights into usage patterns, they demonstrate **poor predictive performance** for daily usage hours. The analysis reveals that:

1. **Academic-focused usage** (doubt-solving, exam prep) drives higher engagement
2. **Tool preference and payment willingness** are significant factors
3. **Linear models are insufficient** for this prediction task

**Next Steps**: Implement non-linear modeling approaches (Random Forest, Gradient Boosting) and enhance feature engineering to achieve better predictive performance.

---
*Report Generated: Analysis of Linear Regression Models for Daily Usage Hours Prediction*
*Dataset: Students_Cleaned_Encoded_correlation_optimized.csv (3,614 samples, 28 features)*
