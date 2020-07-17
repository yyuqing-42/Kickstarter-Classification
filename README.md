# Kickstarter Classification: Successful or Failed

Kai Chen Tan, Qi Jing Yap, Yuqing Yang, Steven Salmeron

## Background Information
Kickstarter is a fundraising platform with the goal to help “bring creative projects to life” by providing a way for creators and artists to be funded directly by fans of their projects. The platform was launched on April 28, 2009 and has seen over 450,000 projects pass through it since then. We obtained the data from Kaggle:https://www.kaggle.com/kemical/kickstarter-projects/ The dataset being analyzed for this project was scraped from Kickstarter platform by a Kaggle user, Mickaël Mouillé. This dataset contains information of over 300,000 Kickstarter projects up to January 2, 2018.

## Discussion of Varibales
1. Each Column 
- ID is the internal Kickstarter ID, unique for each project.
- name is the name of a project.
- category is the subcategory a project belongs to. There are 5 to 20 subcategories within each main category.
- main_category is a classification of projects based on shared characteristics. There are 15 main categories set by Kickstarter.
- currency is the local currency used for the campaign.
- deadline is the date a project was scheduled to end.
- goal is the fundraising goal set by the creator of a project. Data in this column is of different currency types and not standardized.
- launched gives the date and time the project was started in the platform.
- pledged is the amount of money a project fundraised. Data in this column is of different currency types and not standardized.
- state indicates the outcome of a project, whether it was successful, failed, cancelled or suspended. Ongoing projects are labeled as live, and some project status are undefined.
- backers is the number of backers who have agreed to contribute to a project.
- country gives the abbreviation of the country where the Kickstarter project was launched.
- usd pledged is the conversion of the pledged column to US dollars (conversion done by Kickstarter).
- usd_pledged_real is the amount of money a project fundraised. Data in the pledged column is converted to USD and standardized.
- usd_goal_real is the fundraising goal. Data in the goal column is converted to USD and standardized.

2. Each Row
Each row is a record of the performance of one unique project with the Kickstarter internal ID as the unique identifier.

## Goal
We are trying to predict whether a project successful or failed.

## Exploratory Analysis of the Data
We have decided to remove the columns pledged and goal because data in these two columns are in different currency types and not standardized. Instead, we will be using columns usd_pledged_real and usd_goal_real, which are the same numbers converted to USD and standardized. In addition, usd pledged is removed because the conversion done by this column is more problematic. The same information is provided by the variable usd_pledged_real.

We also checked for duplicates and removed problematic rows, the shape of our DataFrame has gone from (378661,15) to (374847, 15), a removal of approximately 1.01% of the original data.

In order to prepare the data for further analysis and modeling, we have created a few new features from existing ones. The list of features created are as follows:

- project_length: This feature tracks the number of days between a project's launch date and deadline where a project was active for. 
- pledged_per_backer: This feature tracks the mean amount of money (converted to USD) pledged by each individual backer. 
- percent_funded: This feature tracks the percentage of the goal amount achieved.

Finally, we have decided to keep only rows with states "Failed" or "Successful" because we are only interested in these two outcomes of the projects. The final dataset that is going to be used for analysis in this project has a shape of (292819,15).

## Guiding Questions 
#### 1. Which category is the most well-funded?
Top 3 categories by success rate are Dance, Theater, and Comics.
Top 3 categories that visitors to Kickstarter care about and fund the most are Design, Techology, and Games.

#### 2. What are some highly successful projects?
We looked at projects that have fundraised amounts far exceeding their goals (variable: percent_funded). We found that most projects with outlier success have very low goals, as low as $1, are mostly from category Music and Art. And Highly sucessful projetcs with resonable goals are mostly from category Games and Design.

Also factors such as popularity, extremely low goal or meme/joke projects influence the success rate of a project.

#### 3. What are some factors that may impact the outcome of a project?
We found that successful projects tend to have lower goals. Alsoe we indeed notice a consistent trend where failed projects tend to have a longer project_length than successful projects. That's why Kickstarter suggests a maximum project length is 30 days. Lastly, we can see that the average pledged_per_backer is higher for successful projects across all categories.

## Data Modeling
Achieved 74% test accuracy with KNN model and 68% test accuracy with logistic regression model

## Conclusions
Although the biggest factor in determining the success of a project is the content and the project itself, there are some external factors that could influence the probability of success. From our investigation, we found that the most well-funded projects on Kickstarter are of the categories Games, Design, and Technology, which gives creators a sense of the target audience they are reaching when they decide to launch their projects on Kickstarter. We have also found that setting a reasonable goal will improve success rate. 

Lastly, based on our logistic model, we have discovered that the relationships between the variables goal, project length, and pledged per backer are significant in influencing the outcome of the project. Thus, creators should take note of these basic setup of their projects prior to launch.

## Limitations and Further Research
- If we have data regarding the reward tiers set up by creators, we can see whether there is an optimal number of rewards or reward pledge amount that would incentivize backers to pledge more and increase the probability of success.

- While we were working on the project, we wanted to investigate the probability of success of projects that were relaunched but we were limited since we could not easily decide whether projects with the same name are necessarily the same projects. It would be helpful if we also had the names of creators in the dataset.
Information suggested by prior research, such as whether a campaign includes a video, the length of the description, or the social media presence of the team behind a project simply were not present in this dataset and should be looked into if collected.

- Lastly, it would also be helpful if we have variables that inform us of the number of visits each project has received, and also whether or not the project has been featured or recommended on the platform. This information would help us come up with more insights to advise creators on how to improve the probability of success for their projects.
