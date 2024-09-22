# What is ANOVA?

ANOVA (Analysis of Variance) is a statistical method used to compare **three or more groups** to see if there is a significant difference between their means. It helps answer the question: **Are these groups significantly different from each other, or is any difference just due to random chance?**

## When and Why Do We Use ANOVA?

We use ANOVA when:
1. **You have three or more groups** you want to compare.
2. **You want to see if the means of these groups are significantly different**.

### Example Scenario

Let’s say you’re studying the effect of **three different diets** on weight loss. You have three groups of people:
1. **Diet A**
2. **Diet B**
3. **Diet C**

After a month, you measure the weight loss for each group. Now, you want to know: **Is there a significant difference in the average weight loss between the three diets?**

This is where ANOVA comes in. It helps you compare the mean weight loss between Diet A, Diet B, and Diet C to determine if one diet leads to more weight loss than the others.

## How Does ANOVA Work?

ANOVA works by breaking down the total variation in your data into two parts:
1. **Variation Between Groups**: How different the group means are from each other.
2. **Variation Within Groups**: How much the data points vary within each group.

The key question ANOVA answers is whether the **between-group variation** is large enough to be considered statistically significant.

## Test Statistic: F-value

The test statistic for ANOVA is the **F-value**. The F-value is the ratio of:
$F = \frac{\text{Variance Between Groups}}{\text{Variance Within Groups}}$
- A **higher F-value** means that the variation between groups is larger compared to the variation within the groups, which suggests that at least one group is significantly different.
- A **lower F-value** means that the groups are not significantly different, and any variation is likely due to chance.

## Null Hypothesis in ANOVA

In ANOVA, the **null hypothesis** is that the means of all groups are equal:
$H_0: \mu_1 = \mu_2 = \mu_3$
This means that any observed differences in the group means are just due to random variation, and the different diets don’t actually affect weight loss.

The **alternative hypothesis** is that at least one group mean is different from the others:
$H_A: \text{At least one group mean is different}$

## Outcomes of ANOVA

1. **F-value**: The ratio of the variance between groups to the variance within groups. A **larger F-value** suggests that there is a larger difference between group means.
   
2. **p-value**: The probability of observing a given F-value if the null hypothesis is true.
   - **p-value < 0.05**: You reject the null hypothesis and conclude that at least one group mean is significantly different.
   - **p-value ≥ 0.05**: You fail to reject the null hypothesis, meaning there is no statistically significant difference between the groups.

# Assumptions of ANOVA

Before using ANOVA, you should check these assumptions:
1. **Normality**: The data in each group should be approximately normally distributed.
2. **Homogeneity of variances**: The variance within each group should be roughly equal.
3. **Independent observations**: The data points in each group should be independent of each other.


# But Wait… Which Groups are Different?
### What are Post-hoc Tests?
**Post-hoc tests** are additional statistical tests conducted **after** an ANOVA reveals that there are significant differences among the group means. ANOVA tells you **if at least one group is different**, but it does **not specify which groups** are different from each other. That's where post-hoc tests come into play — they help you identify exactly **which pairs of groups** differ significantly.

One of the most common post-hoc tests is **Tukey’s HSD (Honestly Significant Difference)**, which compares all possible pairs of groups to determine which ones have significant differences in their means.

### Why Do We Perform Post-hoc Tests?

ANOVA compares the means of **three or more groups** and simply tells us whether a **statistically significant difference** exists between them. However, it doesn't specify **which groups** are significantly different from each other. Without this information, we can't know which of the multiple comparisons (i.e., group pairs) are driving the overall difference.

Performing multiple t-tests (comparing pairs of groups) could seem like a solution, but there's a problem with that approach: as you conduct more t-tests, the chance of making a **Type I error** (incorrectly rejecting a true null hypothesis, or finding a false positive) increases. For example, if you run enough t-tests, you're bound to eventually find a difference by random chance, even if none actually exists.

**Post-hoc tests**, like Tukey’s HSD, are designed to control for this increased risk of error by adjusting for the number of comparisons being made. Essentially, these tests help us find **where** the significant differences lie, while keeping the error rate controlled.

### How Does Tukey’s HSD Work?

**Tukey’s HSD** compares the means of all pairs of groups and determines whether the **difference between any two means** is larger than what would be expected by chance. It works by calculating a critical value, based on the **distribution of the differences** and the **overall variability** of the data (similar to how a t-test works), but with a correction for multiple comparisons.

The test computes a **minimum significant difference** (HSD), which is the smallest difference between two means that would be considered statistically significant, given the variability in the data and the number of comparisons being made.

The formula for calculating the **Tukey HSD** is:
$HSD = q \cdot \sqrt{\frac{MS_{within}}{n}}$
Where:
- $q$ is the **studentized range statistic** (based on the number of groups and the degrees of freedom).
- $MS_{within}$ is the **mean square within groups** (which comes from the ANOVA table and measures the variance within groups).
- $n$ is the **number of observations** per group (assuming equal group sizes).

Tukey's test then compares each pair of group means and determines if their difference exceeds the **HSD value**. If it does, the test concludes that those two groups are significantly different.

### Example of Tukey’s HSD

Let’s say you conducted an ANOVA to compare the test scores of students using **three different study methods** (Group A, Group B, and Group C). ANOVA tells you that there is a significant difference in scores between at least two of these groups, but it doesn't tell you which groups differ.

You then run **Tukey’s HSD** to compare all possible pairs of groups:
1. Compare **Group A vs. Group B**
2. Compare **Group A vs. Group C**
3. Compare **Group B vs. Group C**

Tukey’s HSD tells you exactly which pairs of groups are significantly different and by how much. For instance:
- Group A and Group B might **not** differ significantly.
- Group A and Group C might have a significant difference in scores.
- Group B and Group C might also differ significantly.

This insight allows you to say, for example, that **Group C’s study method leads to significantly higher test scores** compared to the other groups.

### Key Insights from Post-hoc Tests

1. **Identify Specific Differences**: Post-hoc tests help you determine **which specific groups** differ after ANOVA shows that **some** groups are different. This gives you more detailed insights into the nature of the differences.
   
2. **Control Type I Error**: When you compare multiple groups, the likelihood of falsely finding significant differences (Type I error) increases. Post-hoc tests, like Tukey’s HSD, **correct for multiple comparisons** to prevent this error.

3. **Detailed Comparison**: While ANOVA provides a general result (at least one group is different), post-hoc tests provide **pairwise comparisons**, telling you which specific pairs of groups are significantly different from each other.

### When to Use Tukey's HSD

- **When ANOVA results are significant**: Only run a post-hoc test like Tukey’s HSD if your ANOVA test shows that there is a significant difference between the group means. If ANOVA doesn’t show a significant difference, there's no need for further testing.
- **When you have equal or similar group sizes**: Tukey’s HSD is most appropriate when group sizes are approximately equal. If group sizes differ greatly, other post-hoc tests like **Games-Howell** might be more appropriate.
  
### Other Common Post-hoc Tests

1. **Bonferroni Correction**: This is a very simple method for adjusting p-values when making multiple comparisons. It’s more conservative than Tukey’s HSD and divides the alpha level (e.g., 0.05) by the number of comparisons made to avoid Type I errors.
   
2. **Scheffé’s Test**: This is a flexible post-hoc test that is more conservative (less likely to detect significant differences) but can be used in a variety of comparisons, even if the comparisons weren’t planned before running the ANOVA.

3. **Dunnett’s Test**: This test is used when you want to compare several groups to a **control group**, rather than making all possible pairwise comparisons.

# ANOVA models

### One-Way ANOVA

#### What Is It?
A **one-way ANOVA** is used to determine whether there are any statistically significant differences between the means of **three or more independent (unrelated) groups**, but it looks at just **one independent variable** (or factor). 

#### Example
Let’s say you’re testing the effect of **different fertilizers** (Fertilizer A, Fertilizer B, Fertilizer C) on **plant growth**.
- **Independent variable**: Type of fertilizer (A, B, or C).
- **Dependent variable**: Plant growth (measured in centimeters).

In this case, you are only testing **one factor** (fertilizer type) to see if it affects the dependent variable (plant growth). If the ANOVA test results in a significant difference, you can conclude that the type of fertilizer has an impact on plant growth.

#### When Do You Use It?
- When you have **one independent variable** (with at least three levels or groups) and want to see if it influences the dependent variable.
- For example: comparing test scores across three teaching methods, or measuring blood pressure across three different diets.

### Two-Way ANOVA

#### What Is It?
A **two-way ANOVA** is used to see how two **independent variables** (factors) influence the **dependent variable**, and also to see if there’s an **interaction** between the two independent variables. It lets you evaluate the **individual** and **combined effects** of the two independent variables.

There are three types of effects you analyze in a two-way ANOVA:
1. **Main Effect of Factor 1**: The impact of the first independent variable on the dependent variable.
2. **Main Effect of Factor 2**: The impact of the second independent variable on the dependent variable.
3. **Interaction Effect**: Whether the combination of Factor 1 and Factor 2 has an effect on the dependent variable.

#### Example
Let’s say you are studying the effect of **fertilizer type** and **amount of water** on plant growth. The two factors (independent variables) are:
- **Fertilizer type**: Fertilizer A, B, or C.
- **Water amount**: 100 mL, 200 mL, or 300 mL.

The dependent variable is plant growth (measured in centimeters).

#### Possible Effects:
1. **Main effect of Fertilizer type**: How does the type of fertilizer affect plant growth?
2. **Main effect of Water amount**: How does the amount of water affect plant growth?
3. **Interaction effect**: Does the effect of fertilizer depend on the amount of water used? In other words, does one fertilizer work better with a specific amount of water?

#### When Do You Use It?
- When you have **two independent variables**, and you want to study their individual effects as well as how they interact with each other.
- For example: studying the effects of **teaching method** (lecture vs. online) and **study time** (1 hour, 2 hours) on test scores.

### Three-Way ANOVA

#### What Is It?
A **three-way ANOVA** is used when you have **three independent variables** (factors) and you want to study their effects on the dependent variable, as well as their **interaction effects**. It’s an extension of the two-way ANOVA.

In three-way ANOVA, you examine:
1. **Three main effects** (one for each independent variable).
2. **Three two-way interaction effects** (how each pair of independent variables interacts).
3. **One three-way interaction effect** (how all three independent variables together affect the dependent variable).

#### Example
Suppose you want to study the effects of **fertilizer type**, **water amount**, and **sunlight exposure** on plant growth. Your independent variables are:
- **Fertilizer type**: Fertilizer A, B, or C.
- **Water amount**: 100 mL, 200 mL, or 300 mL.
- **Sunlight exposure**: 4 hours, 6 hours, or 8 hours per day.

#### Possible Effects:
1. **Main effects**: 
   - Effect of **fertilizer type** on plant growth.
   - Effect of **water amount** on plant growth.
   - Effect of **sunlight exposure** on plant growth.
2. **Two-way interactions**: 
   - Interaction between fertilizer type and water amount.
   - Interaction between fertilizer type and sunlight exposure.
   - Interaction between water amount and sunlight exposure.
3. **Three-way interaction**: 
   - Does the combination of fertilizer type, water amount, and sunlight exposure together affect plant growth in a significant way?

#### When Do You Use It?
- When you have **three independent variables** and want to study their individual effects and how they interact with each other and with the dependent variable.
- For example: studying the effects of **drug dosage**, **age**, and **gender** on health outcomes.

### Going Beyond Three-Way ANOVA (n-way ANOVA)

You can extend this logic to **four-way ANOVA** or even **n-way ANOVA**, where you have more than three independent variables. However, as you add more factors, the complexity of the analysis increases, and interpreting interaction effects becomes more challenging.

In an **n-way ANOVA**, you would have:
- **n main effects** (one for each independent variable).
- **Multiple two-way, three-way, and higher-order interactions**.

### Interaction Effects: Why Are They Important?

Interaction effects are important because they tell you whether the effect of one independent variable **depends** on the level of another independent variable. If there’s a significant interaction effect, it means that the independent variables work **together** in a way that influences the dependent variable.

For example:
- If you find a significant interaction between **fertilizer type** and **water amount**, it might mean that Fertilizer A works well only with 100 mL of water, while Fertilizer B works best with 200 mL of water.

### Summary of Differences:

| ANOVA Type        | Number of Independent Variables | What It Tests |
|-------------------|---------------------------------|-------------------------------------------------|
| **One-Way ANOVA** | 1                               | Tests whether the means of three or more groups are different for **one factor**. |
| **Two-Way ANOVA** | 2                               | Tests the main effects of two factors, plus their interaction. |
| **Three-Way ANOVA** | 3                               | Tests the main effects of three factors, two-way interactions, and the three-way interaction. |
| **n-Way ANOVA**   | n                               | Tests the main effects and all interaction effects for **n factors**. |

### Key Takeaways:
- **One-way ANOVA**: Tests the effect of one independent variable (factor) on a dependent variable.
- **Two-way ANOVA**: Tests the effects of two independent variables, as well as their interaction.
- **Three-way ANOVA**: Extends the two-way ANOVA to test the effects of three independent variables and their interactions.
- **n-way ANOVA**: Allows for testing of multiple independent variables and their interactions, but becomes complex as the number of factors increases.

