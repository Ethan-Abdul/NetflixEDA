<h1>Netflix Exploratory Data Analysis (EDA) & Statistical Testing</h1>



<h2> 📌 Overview</h2>
This personal project utilises <b>EDA</b>, <b>Statistical Testing</b>, and external research to examine Netflix's catalogue expansion and release-scheduling tactics to drive user engagement and mitigate subscriber churn.

<h3>EDA Uncovers Netflix's:</h3>

- Favoured content format (movies vs. TV shows)
- Content scheduling preferences to mitigate churn
- Desire to become more globally diverse
- Target audiences over time

<h3>Statistical Testing Verifies if Netflix is:</h3>

- Gradually shifting from standalone feature films to TV shows
- Centering content releases around the New Year to combat holiday attrition
- Attempting to cultivate a more family-oriented viewer base

The two inference pipelines implemented in statistical testing are:

1. A <b>Chi-Square Test of Independence</b> with <b>Cramer's V</b>
2. A <b>One-Way Analysis of Variance (ANOVA)</b>  with <b>Eta-Squared</b> 

Both Chi-Square and One-Way ANOVA return p-values to determine whether there is a significant dependence between variables, with Cramer's V and Eta-Squared, respectively, providing context regarding the effect size of the dependence.



<h2> 👨🏻‍💻 Languages & Libraries Used</h2>

<h3>Python:</h3>

- <b>DataFrame Manipulation:</b> numpy, pandas
- <b>Visualisation:</b> geopandas, matplotlib, seaborn
- <b>Statistics:</b> pingouin, scipy



<h2> 📊 Main Data Findings</h2>
<h3>1. January Front-Loading proves a viable Churn Mitigation Strategy until 2021</h3>

<p align="center">
<br />
<img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/a9614be6-744e-46a2-be18-ebc594dfc2ba" />
</p>

<h3>2. The US dominates as the leading region in Netflix releases</h3>

<p align="center">
<br />
<img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/baf7bac7-63a8-4bb8-8133-f3a7baa7c62a" />
</p>

<h3>3. Catering to younger audiences after a historic mature-audience focus</h3>

<table>
 <br />
  <tr>
    <td width="50%">
      <img width="850" height="547" alt="image" src="https://github.com/user-attachments/assets/cdecf8fb-0796-403e-a0aa-be089c1d3642" />
    </td>
    <td width="50%">
      <img width="850" height="547" alt="image" src="https://github.com/user-attachments/assets/ff2cbbf9-4cfb-412d-b7b6-806d83387f6d" />
    </td>
  </tr>
</table>



<h2> 🔍 Statistical Findings</h2>

<h3>1. Chi-Square Test of Independence: Netflix's 2019-2020 US Content Shift from Movies to TV Shows</h3>

The test is defined as follows:
- $H_0$ (Null Hypothesis): The distribution of catalogue additions in the US by content type (Movies vs. TV Shows) is independent of the release calendar year (2019 vs. 2020).
- $H_1$ (Alternative Hypothesis): The distribution of catalogue additions in the US by content type is dependent on the release calendar year.

With a significance level $(\alpha)$ of $1 \% \space (\alpha = 0.01)$.

The first step was creating a contingency table from US content releases across 2019 and 2020:

| Release_Year | 2019 | 2020 |
| --- | --- | --- |
| Category | | |
| Movie | 554 | 437 |
| TV Show | 178 | 241 |

Statistical Test Output:

| Chi-Square | dof | $p$-value | crit-region | Cramer's $V$ |
| --- | --- | --- | --- | --- |
| 20.71 | 1 | 5.3e-6 | $(6.635, \space + \infty)$ | 0.1212 |

Implications:
- There is a significant relationship between the <b>Content Type</b> (Movies vs. TV Shows) and <b>Release Year</b> (2019 vs. 2020), as the Chi-Square statistic falls comfortably within the critical region ($\chi^2$ > 6.635, $p$ < 0.01).
- A Cramer's $V$ of 0.1212 indicates a small to moderate effect size ($V$ > 0.10 for $d.f.$ = 1). This confirms that the observed transition to episodic content was a deliberate, non-random shift in catalogue composition. <br />


<h3>2. One-Way ANOVA: Netflix's reliance on High Content Output to Mitigate Churn</h3>

The One-Way ANOVA is a statistical test used to determine whether there are statistically significant differences among the means of three or more independent groups. For this analysis, the One-Way ANOVA was conducted to evaluate whether monthly content release volume significantly impacts subscriber churn in the subsequent month.

The One-Way ANOVA test is defined as follows:
- $H_0$ (Null Hypothesis): The volume of content additions does not affect customer retention. The mean subscriber churn rate is equal across months categorised by low, medium, and high release volumes ($\mu_{Low} = \mu_{Med} = \mu_{High}$).
- $H_1$ (Alternative Hypothesis): The volume of content additions significantly impacts customer retention. At least one release volume tier results in a distinct mean subscriber churn rate ($\mu_i \ne \mu_j$ for at least one pair of output tiers ($i \ne j$)).

This evaluates whether aggressive catalogue front-loading actively suppresses customer churn during high-attrition periods, or if subscriber retention operates independently of output volume.

DataFrame Sample:

| Volume Tier | Lagged Churn Rate (%) |
| --- | --- |
| Medium | 2.20 |
| Low | 1.95 |
| Low | 1.88 |
| Medium | 2.40 |
| High | 2.42 |

DataFrame Structure & Methodology:
1. The "Volume Tier" column, which denotes content output for a given month, is split into 'Low', 'Medium', and 'High' groups.
2. The testing dataframe is in chronological order from December 2018 to December 2020.
3. A one-month time lag was applied to the churn rate column to align subscriber cancellation with the preceding month's content output. This accounts for decision latency in subscriber behaviour, which directly tests whether prior release activity drives subsequent month-on-month churn.

Statistical Test Output:

| Source | F | $p$-value | Eta-Squared |
| --- | --- | --- | --- |
| Volume Tier | 3.898495 | 0.036321 | 0.270757 |

Implications:
- there 


<h3>3. Chi-Square Test of Independence: Netflix'sTransition to Family-Centered Cotent</h3>

kdshjfpanv

| Chi-Square | dof | $p$-value | crit-region | Cramer's $V$ |
| --- | --- | --- | --- | --- |
| 20.71 | 1 | 1e-5 | (3.841, $\infty$) | 0.1212 |



<h2> ⚠️ Disclaimers & Limitations</h2>

- This dataset was sourced from Kaggle and may not be fully representative of Netflix's true catalogue.

- The data may not be fully up to date, reflecting Netflix's catalogue at the time of collection and/or releases from a specific region/regions.

- The research conducted alongside the analysis of this dataset is simply an attempt to ground the findings into reality and not an attempt to prove the findings to be definitively true.



<h2> ➡️ Next Steps</h2>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
