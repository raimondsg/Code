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