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

<h3>1. 2019 to 2020 US shift from Movies to TV Shows</h3>

The first step was creating a contingency table from US content releases across 2019 and 2020:

| Release_Year | 2019 | 2020 |
| --- | --- | --- |
| Category | | |
| Movie | 554 | 437 |
| TV Show | 178 | 241 |

Yielding results:

| Chi-Square | dof | $p$-value | crit-region | Cramer's $V$ |
| --- | --- | --- | --- | --- |
| 20.71 | 1 | 1e-5 | (3.841, $\infty$) | 0.1212 |

The implications of these results are as follows:
- There is a significant relationship between the <b>Content Type Release</b> (Movies vs. TV Shows) and <b>Release Year</b> (2019 vs. 2020), as the Chi-Square statistic falls in the critical region and the p-value is less than  (20.71 > 3.841 <=> 1e-5 < 0.05).
- Cramer's $V$ value is greater than 0.1, ...<br />

<h3>2. Netflix's reliance on high content output to mitigate churn</h3> <br />
Briefly explain what this test aims to uncover, then table, then implications of results...

| Source | F | $p$-value | Eta-Squared |
| --- | --- | --- | --- |
| Volume | 3.898495 | 0.036321 | 0.270757 |

The "Volume" column is split into 'Low', 'Medium', and 'High' output tiers.

<h3>3. </h3> <br />

| Chi-Square | dof | $p$-value | crit-region | Cramer's $V$ |
| --- | --- | --- | --- | --- |
| 20.71 | 1 | 1e-5 | (3.841, $\infty$) | 0.1212 |

<h2> ⚠️ Disclaimers & Limitations</h2>

- This dataset was sourced from Kaggle and may not be fully representative of Netflix's true catalogue.

- The data may not be fully up to date, reflecting Netflix's catalogue at the time of collection and/or releases from a specific region/regions.

- The research conducted alongside the analysis of this dataset is simply an attempt to ground the findings into reality and not an attempt to prove the findings to be definitively true.


<h2> 👨🏻‍💻 Languages & Libraries Used</h2>

<h3>Python:</h3> 

- <b>DataFrame Manipulation:</b> numpy, pandas 

- <b>Visualisation:</b> geopandas, matplotlib, seaborn

- <b>Statistics:</b> pingouin, scipy


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
