### What is a Paired t-test?

A **paired t-test** is a type of statistical hypothesis test used to compare **two related groups** or **two measurements** on the same subjects. The key idea here is that the data points are not independent; instead, they are paired because they come from the same individuals or conditions measured twice.

### When and Why Do We Use the Paired t-test?

You use a paired t-test when:
1. **You have two sets of measurements** from the same subjects or units.
2. These two measurements are **related or paired** in some meaningful way. For example, they might represent two different methods measuring the same thing, or measurements taken at two different time points (e.g., pre-test and post-test).
3. You want to compare these two sets of measurements to see if there is a statistically significant difference between them.

The test helps answer the question: **Are the differences between the two sets of paired data significant or could they have occurred by random chance?**

### How Does the Paired t-test Work?

The paired t-test works by calculating the differences between the paired observations, and then testing whether the **mean** of these differences is significantly different from zero.

1. **Difference Calculation**:
   - For each subject, calculate the difference between the two paired measurements:
     
     $d_i = \text{A}_i - \text{B}_i$
    
   - $d_i$ represents the difference in pose estimation for the $i-th$subject.

2. **Test Statistic (t-value)**:
   - The paired t-test then computes the mean difference $\overline{d}$ and the standard deviation of the differences ($s_d$).
   - The t-statistic is calculated as:
     $t = \frac{\overline{d}}{s_d / \sqrt{n}}$
   - Where:
     - $\overline{d}$ is the average of the differences.
     - $s_d$ is the standard deviation of the differences.
     - $n$ is the number of paired observations.

3. **Null Hypothesis**:
   - The paired t-test tests the **null hypothesis** that the **mean difference** between the paired measurements is zero, i.e., there is no significant difference between the two methods.
   - The alternative hypothesis is that the mean difference is not zero, i.e., there **is** a significant difference between the two methods.

### Outcomes of the Paired t-test

1. **t-value**:
   - The t-value represents how many standard deviations the sample mean of the differences is from the hypothesized population mean (which is zero under the null hypothesis).
   - A **larger t-value** suggests a larger difference between the two paired groups relative to the variability of the differences.

2. **p-value**:
   - The p-value tells you the probability of observing a difference as large (or larger) than the one you calculated, assuming the null hypothesis is true (i.e., assuming there is no real difference between method A and method B).
   - **If the p-value is less than your significance level (usually 0.05)**, you reject the null hypothesis and conclude that there is a statistically significant difference between the two methods.
   - **If the p-value is greater than 0.05**, you fail to reject the null hypothesis, meaning the difference between method A and method B is not statistically significant.

### Interpreting Results

- **Significant p-value (< 0.05)**: If you find a significant p-value, this suggests that there is a significant difference between the two methods (e.g., method A might be more or less accurate than method B). The mean of the differences is statistically different from zero.
  
- **Non-significant p-value (≥ 0.05)**: A non-significant p-value indicates that the differences between method A and method B are not statistically significant, meaning both methods may perform similarly in terms of accuracy for this dataset.

### Assumptions of the Paired t-test

1. **Normality of Differences**: The differences between the paired observations should be approximately normally distributed. If this assumption is violated, especially with small sample sizes, a non-parametric test (like the Wilcoxon signed-rank test) might be a better choice.
   
2. **Paired Data**: The data points must be paired, meaning each observation in one group corresponds to an observation in the other group. In your case, each method A estimate corresponds to an method B estimate for the same pose and subject.

----
### Example: Paired t-Test

#### Scenario:
Imagine you want to check if drinking coffee before a workout helps people do more push-ups. You ask 5 people to do as many push-ups as they can, once **without coffee** and once **with coffee**. Here are their results:

- **Without coffee**: 15, 18, 14, 16, 12
- **With coffee**: 20, 22, 19, 21, 16

#### Step-by-Step Process:

1. **Calculate the differences**: Subtract the number of push-ups **without coffee** from the number **with coffee**:
   - Differences: 20-15 = 5, 22-18 = 4, 19-14 = 5, 21-16 = 5, 16-12 = 4

2. **Mean difference**: Add up all the differences and divide by the number of people:
   - (5 + 4 + 5 + 5 + 4) / 5 = 4.6

3. **t-statistic**: -18.78 (calculate by a calculator or a statistics program)

4. **p-value**: 0.000047  (calculate by a calculator or a statistics program)

#### What Does It Mean?
Since the **p-value = 0.000047** is much smaller than 0.05, it suggests that drinking coffee **does have a real effect** on how many push-ups people can do.
- The result is **statistically significant**, meaning that the increase in push-ups is likely due to the coffee and not just random chance.
The t-statistic is -18.78, which is quite large in magnitude. This indicates that the difference in push-ups before and after drinking coffee is very large, meaning coffee made a significant difference.

Absolutely! Let's now go through a paired t-test example comparing two methods.

### Example: Comparing Two Methods

#### Scenario:
Imagine you are testing two different study techniques to see which one helps students score higher on a test. You have 6 students, and they try **Method A** (like reading a book) and **Method B** (like watching videos). You want to compare their test scores using these two methods:

- **Scores using Method A**: 70, 65, 80, 75, 85, 90
- **Scores using Method B**: 75, 70, 82, 78, 88, 92

#### Step-by-Step Process:

1. **Calculate the differences**: Subtract the scores for **Method A** from the scores for **Method B**:
   - Differences: 
     - 75 - 70 = 5
     - 70 - 65 = 5
     - 82 - 80 = 2
     - 78 - 75 = 3
     - 88 - 85 = 3
     - 92 - 90 = 2

2. **Mean difference**: Add up the differences and divide by the number of students:
   - (5 + 5 + 2 + 3 + 3 + 2) / 6 = **3.33**

3. **t-statistic**: -5.98 (calculate by a calculator or a statistics program
  
4. **p-value**: 0.00188  (calculate by a calculator or a statistics program)

#### What Does It Mean?

Since the **p-value = 0.00188**, which is less than 0.05, you can say that **Method B** is statistically better than Method A at improving test scores.
- The average difference (3.33 points higher for Method B) is **statistically significant**, meaning it’s unlikely this improvement is just by chance.
The t-statistic is -5.98. This is also a large t-value, meaning the difference between the two study methods is notable and not likely due to random variation.

