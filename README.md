# The-Battle-of-Neighborhoods-Week-1
Coursera Data Science Capstone Project: The Battle of Neighborhoods (Week 1)

Review criterialess 
This capstone project will be graded by your peers. This capstone project is worth 70% of your total grade.
The project will be completed over the course of 2 weeks.
Week 1 submissions will be worth 30% whereas week 2 submissions will be worth 40% of your total grade.

For this week, you will required to submit the following:
A description of the problem and a discussion of the background. (15 marks)
A description of the data and how it will be used to solve the problem. (15 marks)
For the second week, the final deliverables of the project will be:

A link to your Notebook on your Github repository, showing your code. (15 marks)
A full report consisting of all of the following components (15 marks):
Introduction where you discuss the business problem and who would be interested in this project.
Data where you describe the data that will be used to solve the problem and the source of the data.
Methodology section which represents the main component of the report where you discuss and describe any exploratory data analysis that you did, any inferential statistical testing that you performed, if any, and what machine learnings were used and why.
Results section where you discuss the results.
Discussion section where you discuss any observations you noted and any recommendations you can make based on the results.
Conclusion section where you conclude the report.
3. Your choice of a presentation or blogpost. (10 marks)

Week 1:
Objective:
Use clustering algorithm such as KMeans to group together similar neighborhoods

Introduction:
I chose the city of Paris, where I live, so that I could use my first hand experience to tally the results.

Methodology:

Part 1:
The Wikipedia page for Paris Districts was chosen to extract the basic details of the 20 districts (also called arrondissement) from 
https://en.wikipedia.org/wiki/Arrondissements_of_Paris

The original idea was to get all "Places of Interest" from each of the individual Wiki pages of each of the arrondissement and use it in conjunction to FourSquare APIs but this was abandoned due to lack of time.

On the Wiki page we see that columns for Arrondissement, Area and Population Density needed some additional data wrangling to make it cleaner.

At the same time, I used data from these two files: mainly for the latitude and longitude.
Formats de fichiers plats
https://opendata.paris.fr/explore/dataset/arrondissements/download/?format=csv&timezone=Europe/Berlin&use_labels_for_header=true

Formats de fichiers géographiques
https://opendata.paris.fr/explore/dataset/arrondissements/download/?format=geojson&timezone=Europe/Berlin

Again here, I faced issues automating this so I had to manually download the csv files and use it in the project.

To add here itself, another remark was the dependency of packages that were likely to be used. I faced some issues but I was able to resolve them.
At https://labs.cognitiveclass.ai, I did not find any option to upload the files, so I used Jupyter notebook with Python 3 on my laptop.

So after having scrapped the Wiki page and the csv file containing latitude and longitude, I had the final working dataframe: paris_et_arrondissements_df.

Part 2:
The next step was to prot the map of Paris with its arrondissements using Folium.

Part 3:
The next part is to setup the credentials for Foursquare API

Part 4: Using FourSquare API calls
I used function to retrieve nearby avenues, number of venues per districts, and the unique categories discovered.
We then use one hot encoding to convert Venue Category into categorical variables for each of the venues types.

We proceed with grouping the results per each of the districts.
We then find the top 10 venues of each neighborhood

Part 5:
KMeans clustering is applied taking kclusters = 5 and proceed to visualize these clusters and the most common venues for each of the clusters are determined.

Conclusions:
Cluster 1: From all 20 districts: The most popular are French restaurants with the exception of 18th (bar), 18th (bar), 20th districts (Pizza) and 6th (Italian). I believe that bars should have shown up in the 3rd, 6th or 10th and 11th districts.
The 2nd most popular choice is between hotel and French restaurants.

Cluster 2: From only 1 district: 12th arrondissement: The most popular choice is the zoo exhibit and the 2nd is the park. It is quite evident as there is Zoo de Vincennes and Park de Vincennes which are quite popular.

Cluster 3: From only 1 district: It is the 15th district and Foresquare tags it as 'lake' being most popular but realistically, most people go there to see the eiffel tower and take a river cruise on the river, Seine. The next popular is Pizza, which is quite obvious after some rigorous sightseeing.

Cluster 4: From 4 districts: Mostly for French restaurant and Hotel (7, 8, 17 arrondissements: These are quite touristic quartiers of Paris and perhaps the samples taken into account accounts for this bias (if FourSquare users are also rich). The 14th arrondissement is popular among the young and budget travellers.

Summary:
Paris being a very touristic city, the results are bound to be more biased towards hotels and French restaurants.
A more detailed study is necessary to find popular venues apart from these.
Perhaps a higher order to clustering could improve the results.
