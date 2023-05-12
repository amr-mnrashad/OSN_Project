# OSN_Project
This project goes through all of the phases of a data science project. From building a database, to creating visualization after performing different types of analysis.

 NOTE: In this repository, I can only share the notebook but I cannot share the postgres dump file or the PowerBI reports due to confidentiality.

So let's start by showing you the roadmap of my presentation, where I first start by doing a quick introduction on how I approached this challenge and then I'm gonna discuss in details the different types of analysis I have applied, which are Descriptive analysis, Skills analysis, where I have basically applied cosine similarity, PCA and K-means clustering, I am going to explain the concepts in a brief manner so no worries if some of them might be unfamiliar. Then the last type of analysis is Network analysis.

So to start off this challenge I had to organize, clean and gather the tables into one database, where all of the tables are connected together. I was able to do that by running an automated script that we have developed where csv files are cleaned and added to a Postgres DB. I then decided to approach this challenge by making it as a well connected story, where I ask meaningful questions and get interesting insights. In order to do so I have developed several queries in order to generate the tables that I want in order to perform some visualizations.


The queries have been written on pgAdmin which is the postgres environment, I then integrated the database with PowerBI in order to perform the visualization that I want.

Like I mentioned earlier, I wanted to present this challenge as a story. So I first started by dividing this into 3 parts, each part is focusing on a specific category, the 3 categories are jobs, skills and companies. 

After doing some descriptive analysis and some visualizations on PowerBI, the next step was to build a recommendation system and also to view the job skills in clusters based on the similarities between them. By similarity I mean the number of occurences two skills for example occur together.

I have applied cosine similarity to create a recommendation system, a simple explanation of it is: it measures the anlge between two vectors, in our case two skills and if the angle is small then they are similar, the smaller the angle the more similar they are, the wider the angle the less similar they are. This type of recommendation system is an item-based on, where the aim is to provide a list of items based on the input of the user. So for isntance in the notebook we can see that the user has entered the job cateogory and the skill, he would then get the 5 most similar skills to that one in that job category, in order. So the most similar is gonna be the first one and then the second is less similar and so on and so forth. 

After performing cosine similarity I wanted to cluster the skills based on their similarity, in order to see, for example in one cluster we can see that statistics, ML and R are in one cluster, this means that usually these three types of skills occur together frequently, this can be helpful for the company to use as it can advise candidates on which skills to focus on based on what they already know or have learnt.

To perform clustering I had to deal with the dimensionality issue, where my matrix is composed of over a hundred columns, in order to do so, I have performed PCA (principal component analysis), the simple explanation is I try to reduce the dimensions as much as possible while still able to explain most of the data. In my case, for the job categories Consulting and end user I was able to explain more than 90% of the data by shrinking it down to 3 dimensions, while for the tech start up I reduced it even more, to just two dimensions. 

Regarding the clustering mechanism, I have performed k-means where each data point is clustered with the nearest datapoint that have similar means. Basically the clustering is performed based on similarities. And for each category I wanted to know the optimal number of clusters that can best explain my data. By performing an elbow plot we can see that for consulting the optimal number is 4, 5 for enduser and 3 for tech start up.

Such feature might not be used very often by big companies, however I believe it can be very beneficial for some of the smaller ones. For instance, I've seen a lot of start ups putting a vague job requirements and not being specific on the type of skills they want their applicants to have. So something like this can make the job requirements field on the website more detailed which also might help the candidates to know whether or not they have the qualifications for such job, so this actually goes hand in hand with a problem we have identified earlier in our descriptive analysis, where most of the applicants are getting refused because they don't meet the basic requirements, this could be one of many solutions that can be applied to reduce such number. 


The last type of analysis which is network analysis, where I have built a bipartite graph showing the main companies/universities being referenced by the candidates. This could help identify potential accounts and also could be an opportunity to offer workshops and laboratory sessions for students who are interested in working the STEM fields.
