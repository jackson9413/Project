# Impact_on_Grades Regression Analysis Summary

## Overview
This analysis demonstrates how to use `Impact_on_Grades` as a target variable for regression modeling, comparing it with `Daily_Usage_Hours` prediction to show the versatility of the modeling approach.

## Target Variable: Impact_on_Grades

### Characteristics
- **Range**: -5 to +5 (11-point scale)
- **Distribution**: Fairly balanced around 0 (mean = 0.00)
- **Interpretation**: 
  - Negative values: Perceived negative impact on grades
  - Zero: No perceived impact
  - Positive values: Perceived positive impact on grades
- **Data Quality**: No missing values, 3,614 total samples

### Distribution Analysis
- **Most Common Values**: 
  - +2 (14.5% of samples) - Slight positive impact
  - +1 (13.2% of samples) - Minimal positive impact
  - 0 (12.9% of samples) - No impact
- **Extreme Values**: 
  - -5 and +5 each represent ~2.5% of samples
  - Strong negative impacts (-4 to -5): 5.3% of samples
  - Strong positive impacts (+4 to +5): 5.1% of samples

## Regression Modeling Results

### Model Performance Ranking
1. **Random Forest**: R² = 0.268 (26.8% variance explained) ⭐ **BEST**
2. **Support Vector Regression**: R² = 0.084 (8.4% variance explained)
3. **Gradient Boosting**: R² = 0.061 (6.1% variance explained)
4. **K-Nearest Neighbors**: R² = 0.053 (5.3% variance explained)
5. **Linear Regression**: R² = 0.016 (1.6% variance explained)
6. **Ridge Regression**: R² = 0.016 (1.6% variance explained)
7. **Lasso Regression**: R² = -0.002 (Poor performance)
8. **ElasticNet**: R² = -0.002 (Poor performance)
9. **Decision Tree**: R² = -0.366 (Severe overfitting)

### Key Insights
- **Random Forest dominates**: Significantly outperforms all other models
- **Non-linear relationships**: Tree-based models perform much better than linear models
- **Moderate predictability**: Best model explains ~27% of variance
- **Linear models struggle**: Similar to Daily_Usage_Hours, linear relationships are weak

## Feature Importance Analysis

### Top 15 Most Important Features (Random Forest)
1. **Awareness_Level** (0.142) - Student awareness of AI capabilities
2. **Trust_in_AI_Tools** (0.099) - Trust level in AI technologies
3. **Year_of_Study** (0.096) - Academic year/experience level
4. **device_used_Tablet** (0.040) - Using tablet devices
5. **uses_learning_new_topics** (0.038) - Learning applications
6. **ai_tool_copilot** (0.037) - GitHub Copilot usage
7. **uses_exam_preparation** (0.035) - Exam preparation usage
8. **ai_tool_chatgpt** (0.034) - ChatGPT usage
9. **uses_doubt_solving** (0.032) - Doubt-solving applications
10. **ai_tool_gemini** (0.031) - Google Gemini usage

### Business Insights
- **Awareness & Trust**: The two most important predictors of grade impact
- **Academic Experience**: Year of study significantly affects perceived impact
- **Usage Patterns**: Specific use cases (learning, exam prep) matter more than general usage
- **Tool Preference**: Different AI tools have varying impacts on grade perception

## Comparison: Impact_on_Grades vs Daily_Usage_Hours

### Performance Comparison
| Model | Impact_on_Grades R² | Daily_Usage_Hours R² | Better Target |
|-------|---------------------|----------------------|---------------|
| Random Forest | 0.268 | 0.446 | Daily_Usage_Hours |
| Gradient Boosting | 0.061 | 0.104 | Daily_Usage_Hours |
| Linear Regression | 0.016 | 0.016 | Tie |
| Support Vector Regression | 0.084 | 0.181 | Daily_Usage_Hours |

### Key Findings
1. **Daily_Usage_Hours is MORE PREDICTABLE** (44.6% vs 26.8% variance explained)
2. **Both targets struggle with linear models** (R² < 0.02 for linear approaches)
3. **Tree-based models excel** for both prediction tasks
4. **Impact_on_Grades** has moderate predictability - suitable for insights but needs improvement

## Practical Applications

### For Impact_on_Grades Prediction
- **Business Use**: Understanding factors that influence grade perception
- **Intervention Targeting**: Identify students at risk of negative grade impact
- **Feature Engineering**: Focus on awareness, trust, and usage patterns
- **Model Deployment**: Random Forest with 27% accuracy (±2.0 points average error)

### Recommendations
1. **Enhance Awareness Programs**: Most important factor for grade impact
2. **Build Trust**: Second most important predictor
3. **Tailor by Academic Level**: Year of study significantly affects perception
4. **Focus on Learning Applications**: More impactful than general usage
5. **Consider Device Type**: Tablet usage shows different impact patterns

### Model Improvement Strategies
1. **Collect More Features**: 
   - Academic performance metrics
   - Specific assignment outcomes
   - Time-based usage patterns
   - Peer influence factors

2. **Advanced Modeling**:
   - Ensemble methods combining top models
   - Neural networks for complex patterns
   - Ordinal regression (since target is ordered scale)

3. **Feature Engineering**:
   - Interaction terms (awareness × trust)
   - Usage intensity metrics
   - Temporal patterns

## Conclusion

The `Impact_on_Grades` column provides a valuable target for regression modeling, offering insights into student perceptions of AI tool effectiveness. While predictability is moderate (27% variance explained), it's sufficient for:

- **Strategic Decision Making**: Understanding key drivers of grade impact
- **Student Intervention**: Identifying at-risk perception patterns  
- **Product Development**: Focusing on awareness and trust-building features
- **Educational Policy**: Informing AI tool integration strategies

The analysis demonstrates that regression modeling can be effectively applied to various numeric targets in educational datasets, with each providing unique insights for different business objectives.

---
*Analysis completed using comprehensive regression modeling with 9 different algorithms*
*Dataset: 3,614 students, 27 predictive features*
*Best Model: Random Forest (R² = 0.268, RMSE = 2.02)*
