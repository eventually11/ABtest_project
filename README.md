# ABtest_project

## AB Test Project Background

In this project, we aim to evaluate the effectiveness of changes made to a specific feature in an online product through an A/B testing approach. The purpose of this test is to determine whether the new version of the feature (Version B) performs better than the current version (Version A) based on key metrics such as user engagement and conversion rates.



## Introduction to A/B Testing

A/B testing, also known as split testing, is a controlled experiment where a population is randomly divided into two or more groups. One group, referred to as the control group, remains exposed to the current version of a product or feature, while the other group, called the experimental group, is exposed to a modified or improved version of the feature. The objective is to compare the performance of the different versions and determine whether the experimental version leads to statistically significant improvements.

Principle:
The core principle of A/B testing is the control variable method. By ensuring that the only difference between the control group and the experimental group is the product version they experience, any differences in performance metrics (such as conversion rates or user engagement) can be attributed to the tested changes. This method ensures that all other variables, such as time and user demographics, remain consistent across the groups.

Hypothesis Testing:
A/B testing relies on hypothesis testing, which is a method used to determine whether the observed differences between the control and experimental groups are statistically significant or if they could be due to random chance. The most common hypothesis testing methods include the z-test, t-test, chi-square test, and F-test.

The idea is to ensure that the experimental results support or reject the hypothesis of the experiment. For example, if the hypothesis is that the experimental version will result in a higher conversion rate, the statistical tests will indicate whether any observed improvement is likely due to the experimental changes rather than random variations in user behavior.



P-value: The p-value is the probability of obtaining a test statistic at least as extreme as the one observed, assuming that the null hypothesis (H0) is true. It helps in determining whether the observed data are consistent with the null hypothesis. A smaller p-value indicates stronger evidence against H0.

Relation between p-value and α:

    If the p-value is less than α (the significance level), it indicates that the observed effect is statistically significant, leading to the rejection of H0.
    If p-value > α, then there is insufficient evidence to reject H0.
    In a left-tailed test, the p-value is the area under the curve to the left of the test statistic. In a right-tailed test, the p-value is the area to the right.

Null Hypothesis (H0) and Alternative Hypothesis (H1):

    H0 typically states that there is no effect or no difference. For example, in an A/B test, H0 might suggest that both groups (A and B) perform the same.
    H1 suggests that there is a statistically significant effect or difference between groups. The comparison typically includes scenarios where the test statistic is equal, greater than, or less than a threshold.

Testing Results:

    For a one-tailed test:
        If p > α, do not reject H0.
        If p < α, reject H0.
    For a two-tailed test:
        If p > ½ α, do not reject H0.
        If p < ½ α, reject H0.

Types of Errors in Hypothesis Testing

    Type I Error (α):
        This occurs when H0 is rejected when it is actually true (a "false positive" or rejecting a true null hypothesis). The probability of committing a Type I error is denoted by α, also known as the significance level.
    Type II Error (β):
        This occurs when H0 is accepted when it is false (a "false negative" or failing to reject a false null hypothesis). The probability of committing a Type II error is denoted by β.

In hypothesis testing, we typically aim to minimize both α and β, but reducing one can often increase the other unless the sample size is increased. Controlling Type I error (α) is more common in practical applications.


## Statistical Power

Statistical power refers to the probability of correctly rejecting a false null hypothesis (H0). It is calculated as 1−β1−β. High statistical power means that the test is more likely to detect an actual effect when it exists, reducing the chances of Type II errors.

In hypothesis testing, we generally aim to maximize the statistical power by increasing the sample size, reducing random error, or improving the measurement quality.



# Test process

Objective

To investigate the impact of changing rider clothing color on delivery efficiency.
Data Variables

    strategy_id: Marketing strategy identifier, representing the different groups in the AB test:
        1: Control group (no change in clothing color)
        2: Marketing Strategy One (first variation of clothing color)
        3: Marketing Strategy Two (second variation of clothing color)

    user_id: Unique identifier for each rider.

    label: Indicates whether the rider changed their clothing color:
        0: Did not change clothing color
        1: Changed clothing color
