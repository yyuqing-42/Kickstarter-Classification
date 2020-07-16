# Kickstarter Classification: Successful or Failed

Kai Chen Tan, Qi Jing Yap, Yuqing Yang, Steven Salmeron

## Background Information
Kickstarter is a fundraising platform with the goal to help “bring creative projects to life” by providing a way for creators and artists to be funded directly by fans of their projects. The platform was launched on April 28, 2009 and has seen over 450,000 projects pass through it since then. We obtained the data from Kaggle:https://www.kaggle.com/kemical/kickstarter-projects/ The dataset being analyzed for this project was scraped from Kickstarter platform by a Kaggle user, Mickaël Mouillé. This dataset contains information of over 300,000 Kickstarter projects up to January 2, 2018.

## Goal
We are trying to predict whether a project successful or failed.

## Guiding Questions 
#### 1. Which category is the most well-funded?
Top 3 categories by success rate are Dance, Theater, and Comics.
Top 3 categories that visitors to Kickstarter care about and fund the most are Design, Techology, and Games.

#### 2. What are some highly successful projects?
We looked at projects that have fundraised amounts far exceeding their goals (variable: percent_funded). We found that most projects with outlier success have very low goals, as low as $1, are mostly from category Music and Art. And Highly sucessful projetcs with resonable goals are mostly from category Games and Design.

Also factors such as popularity, extremely low goal or meme/joke projects influence the success rate of a project.

#### 3. What are some factors that may impact the outcome of a project?
We found that successful projects tend to have lower goals. Alsoe we indeed notice a consistent trend where failed projects tend to have a longer project_length than successful projects. That's why Kickstarter suggests a maximum project length is 30 days. Lastly, we can see that the average pledged_per_backer is higher for successful projects across all categories.

## Data Analysis and Data Modeling

## Conclusions

## Limitations and Further Research
