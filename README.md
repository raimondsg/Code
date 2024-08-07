# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles I fltered out the most popular positions, and got the top 5 skills for the top 3 roles. This query highlights the most popular job titles and their top skills , showing which skills Data Analysts should pay attention to depending on the role they're targeting.

View my notebook with detailed steps here: [Skill_Demand.ipynb](PYTHON_DATA_PROJECT/3_Project/2_Skill_Demand.ipynb)


### Visualize Data 

```python
fig, ax = plt.subplots(len(job_titles), 1)


for i, job_title in enumerate(job_titles):
    df_plot = df_skills_count[df_skills_count['job_title_short'] == job_title].head(5)[::-1]
    sns.barplot(data=df_plot, x='skill_count', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')

plt.show()
```

### Results

![Visualization of top skills for data nerds](PYTHON_DATA_PROJECT/3_Project/images/skill_visualization.png)

### Insights

- Python is a versatile and highly demanded skill across all 3 roles. Most prominent for Data scientists and Data Engineers where it is 72% and 65% likely to appear in a job posting.
- SQL is most requested for Data Analysts and Data Scientists with half of all job postings having it as a skill. It's essential for Data Engineers appearing in 68% of job postings.
- Data Engineers tend to require more specialized knowledge of cloud coding (AWS, Azure, Spark) compared to Analysts and Scientists, who are expected to be profficient in more general data management tools (Excel Tableu) etc.

## 2. What are the in-demand skills for data analysts, what is their trend?

### Visualize Data

```python


df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10', legend='full')

from matplotlib.ticker import PercentFormatter
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()
```
### Results
![Trending Top Skills for Data Analysts in the US](PYTHON_DATA_PROJECT/3_Project/images/in_demand_skills.png)*Line chart visualizing the trending top skills for data analysts in the US in 2023.*

### Insights:
- SQL is the most demanded skill and remains so for the whole year, but there was a decrease in demand towards end of 2023.
- Excel was also highly saught, and came in 2nd, also dropped down as the year went on.
- Python and Tableu fight for 3rd place and remain in a similar bracket of 25-30% of Data Analyst job postings. sas is the 5th most demanded, but it's relatively low.

## 3. How well do jobs and skills pay for Data Analysts?

### Salary Analysis for Data Nerds
#### Visualie Data

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', order = job_order)

ax = plt.gca()
ax.xaxis.set_major_formatter(plt.FuncFormatter(lambda x, pos: f'${int(x/1000)}K'))
plt.xlim(0,600000)
plt.show()

```

#### Results
![Salary Distributions of Data Jobs in the US](PYTHON_DATA_PROJECT/3_Project/images/salary_distribution_roles.png)
*Box plot visualizaing the salary distributions for the top 6 data job titles in the US*

#### Insights
- As the boxplot graph shows there's a lot of variation between pay across different job titles. Senior Data Scientist and Senior Data Engineers have the highest salaries and higher top-end of salaries. This is indicative of higher value of experience and advanced skills.
- Data Analysts earn the least, and have the least high-earner outliers. Moreover, Senior Analysts tend to earn less then even junior Data Engineers and Data Scientists. Indicating that Data Analysis in the basic form is not valued as high as some other skills.
- Median salaries diverge from outliers quite a lot for Data Scientists and Engineers demonstrating that despite most values being cose to the median, there are a lot of people who earn more (and also less). PS Data analysts have fewer outliers.

### Highest Paid & Most in-demand skills for Data Analysts
#### Visualize Data

```Python
#top 10 highest paying skills for DA
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, ax=ax[0], hue='median', palette='dark:b_r')

#top 10 most popular skills in DA
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, ax=ax[1], hue='median', palette='light:b')

```

![Highest Paid & Most in-demand skills for Data Analysis in the US](PYTHON_DATA_PROJECT/3_Project/images/popular_expensive_skills_DA.png)*Two separate bar charts visualizing the highest-paid skills and most in-demand skills for data analysts in the US*

#### Insights
- The top graph shows that specialized skills such as `dplyr`, `bitbucket` and `gitlab` are associated with highest sallaries up to $200k median. Despite the high salary, these job postings are rather rare to find.

- The bottom graph highlights that foundational data analysis skills such as `excel`, `powerpoint` and `sql` are still some of the most-often demanded ones. Additionally, knowledge of `R` and `python` certainly would not harm your chances.

- Now even though there is a clear distinction between the two brackets of skills, a Data Nerd should always start with the basics. To develop towards a higher-paying skill down the road certainly isn't something unimaginable as well. Just don't remember that sometimes you still need to learn how to walk before running.