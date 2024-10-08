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



## Test process

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


Sample Size Calculator

This code calculates the minimum sample size required for an A/B test, assuming a two-group design (control and treatment). The steps are as follows:

    Effect Size: Set to 0.01, representing the expected difference between the control and treatment groups.
    Alpha: Set to 0.05, indicating a 5% significance level (confidence level).
    Power: Set to 0.8, meaning there's an 80% probability of detecting a true effect.
    Ratio: Set to 1, meaning the sample sizes for the control and treatment groups are equal.

Using these parameters, the TTestIndPower class from the statsmodels library calculates the minimum sample size needed to achieve sufficient statistical power for detecting the given effect size. The result is then rounded up using math.ceil()


Conclusion :

We can observe that both Strategy 1 and Strategy 2 have shown varying degrees of improvement in achieve rates compared to the control group. Specifically:

    Strategy 1 increased the achieve rate by 0.2 percentage points.
    Strategy 2 saw a larger improvement, increasing the achieve rate by 1.3 percentage points.

To confirm if these improvements are statistically significant, we performed hypothesis testing for both strategies. The details of the hypothesis test for Strategy 2 are as follows:
a. Null Hypothesis and Alternative Hypothesis

Let p1​ be the achieve rate for the control group and p2p be the achieve rate for Strategy 2. The hypotheses are formulated as:

    Null Hypothesis (H₀): p1≥p2 (No significant improvement in achieve rate for Strategy 2)
    Alternative Hypothesis (H₁): p1<p2​ (significant)

b. Distribution Type, Test Type, and Significance Level

    The samples are assumed to follow a binomial distribution as the event is binary (achieved or not achieved).
    This is a two-sample Z-test for proportions because the samples are independent and both sample sizes n>30.
    Since the population mean and standard deviation are unknown, we use the Z-test to compare the click rates between the two groups.
    The significance level αα is set to 0.05.

The notebook shows that hypothesis testing (Z-test) was performed for two strategies, and here are the key outputs:

    Strategy 1 Test Result:
        Z-score: -59.6660
        p-value: 0.0
        statistical power: 1>0.8

    This result suggests that Strategy 1 shows a statistically significant improvement over the control group because the p-value is 0 (less than the significance level of 0.05). The extremely negative Z-score suggests a large deviation between the control and Strategy 1, indicating that Strategy 1 is likely performing better in terms of the measured label.

    Strategy 2 Test Result:
        Z-score: -14.3627
        p-value: 4.43e-47
        statistical power: 1>0.8

    Similar to Strategy 1, Strategy 2 also shows a statistically significant improvement over the control group, with an extremely small p-value (much lower than 0.05). The Z-score also shows a significant difference between Strategy 2 and the control group.


Summary: 

    Both Strategy 1 and Strategy 2 have significantly improved the measured outcome (label) compared to the control group, as evidenced by their very small p-values.
    Strategy 1 has a greater impact based on the Z-score, which is much more extreme than that of Strategy 2.



## AA test
The purpose is to verify whether the user segmentation is reasonable. The main goal is to check if the control group and the strategy group exhibit similar conversion rates under identical experimental conditions, without any actual differences. The A/A test uses the same experimental conditions to verify whether there is no statistically significant difference between the two groups. If the conversion rates between the two groups are not significantly different, it indicates that the user segmentation is reasonable.

    Total rate: 0.012442544261473528
    A/A Test - z-score: -2.5418134831300656, p-value: 0.011027900460504928
    A/A Test rejected the null hypothesis, user segmentation may have issues.

    Total rate A1 vs A3: 0.012392782621291188
    A/A Test A1 vs A3 - z-score: -2.038684138526655, p-value: 0.0414815617913717
    A/A Test A1 vs A3 rejected the null hypothesis, user segmentation may have issues.

Based on the A/A test results, we suspect that the user segmentation may not be entirely reasonable, as the tests have indicated potential significant differences between the randomly assigned groups. Further analysis is needed to better understand and address the segmentation issues.


## PSM

When an A/A test reveals significant differences between groups (p-value < 0.05), it indicates that randomization did not result in balanced groups. In such cases, Propensity Score Matching (PSM) is a useful statistical method to address these differences. PSM can help reduce group imbalances and ensure that the treatment and control groups are more comparable.


Why Use PSM?

The purpose of an A/A test is to verify the effectiveness of randomization. If significant differences are found between groups, it suggests that the randomization process may have failed or certain confounding variables have not been adequately controlled.

PSM helps reduce group differences by matching treatment and control group members based on their propensity scores. The propensity score is the probability of a user being in the treatment group based on observed characteristics, such as age, income, gender, or other factors.
Advantages of PSM:

    Control Confounding Variables: PSM allows us to control for confounding variables by matching users with similar characteristics from the treatment and control groups, ensuring the groups are balanced.
    Remediation for Non-Randomized Experiments: When randomization does not fully eliminate differences between groups, PSM can be used as a remedial method to achieve better comparability between the groups.


Steps to Apply PSM When A/A Test Fails
1. Identify Confounding Variables

The first step is to identify key confounding variables (e.g., age, income, gender, or other relevant features) that could explain the differences between groups.
2. Estimate Propensity Scores

Using a logistic regression model, propensity scores can be estimated based on these identified variables. The propensity score represents the probability that a user would be in the treatment group, given their observed characteristics.
3. Match Treatment and Control Groups

Using the propensity scores, we can match each treatment group member with one or more control group members who have similar scores. Techniques like nearest-neighbor matching can be used to perform this matching.
4. Analyze the Matched Data

After matching, the treatment and control groups should be more balanced in terms of the confounding variables. The effect of the treatment can then be evaluated by analyzing the matched data.
。


Conduct A/A Test After PSM

Objective: Validate that the propensity score matching was successful and that the test and control groups are equivalent.
Action:
    Randomly divide the population into two groups (A1 and A2), both receiving the same treatment.
    Measure key performance metrics (e.g., click-through rate, conversion rate).
    Perform an independent t-test to compare the means of the two groups.
Hypothesis:
    Null hypothesis H0H0​: There is no significant difference between the two groups (A1 and A2).
    Alternative hypothesis H1H1​: There is a significant difference between the two groups.



Conduct A/B Test to Evaluate Experimental Effect

Objective: Measure the effect of the experimental change on a key performance metric by comparing the test group (B) with the control group (A).
Action:
    Assign users to Group A (control) and Group B (treatment) based on the PSM process.
    Apply the experimental condition to Group B (e.g., a new algorithm, design, or marketing strategy) and leave Group A unchanged.
    Collect performance data for both groups (e.g., click-through rates, conversion rates).
Hypothesis:
    Null hypothesis H0H0​: There is no significant difference between Group A and Group B.
    Alternative hypothesis H1H1​: There is a significant difference between Group A and Group B.


Evaluate Results and Draw Conclusions

    If the p-value in the A/B test is significant, it suggests that the experimental condition applied to Group B has a meaningful effect on the chosen metrics (e.g., conversion rates, engagement).
    If the p-value is not significant, it indicates that there is no statistical evidence to support that the experimental condition has an effect, and further investigation or adjustment of the experiment may be required.
