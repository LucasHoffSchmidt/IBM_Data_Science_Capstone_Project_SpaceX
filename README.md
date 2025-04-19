# IBM Data Science Capstone Project: SpaceX rocket stage 1 landing outcome
Developing a classification model for predicting whether or not SpaceX will successfully land stage 1 of a rocket for a given launch.

## Quick Links
- Detailed overview of the project process: [Project Report](https://github.com/LucasHoffSchmidt/IBM_Data_Science_Capstone_Project_SpaceX/blob/main/Data_Science-SpaceX-Report.pdf)
- Jupyter Notebooks of the development process of the classification model: [Jupyter Notebooks](https://github.com/LucasHoffSchmidt/IBM_Data_Science_Capstone_Project_SpaceX/tree/main/Jupyter_Notebooks)
- Plotly Dash screenshots of launch results across launch sites and payload ranges: [Plotly Dash Screenshots](https://github.com/LucasHoffSchmidt/IBM_Data_Science_Capstone_Project_SpaceX/tree/main/Plotly_Dash_Screenshots)
- Other projects I have made: [Portfolio Website](https://lucashoffschmidt.github.io/)

## Problem
We are a competitor to SpaceX called SpaceY and we are interested in making a model that can predict whether SpaceX will successfully land stage 1 of a rocket for a given launch, to help us determine whether we will be able to compete against it. 

## Technologies Used
**Tools and Platforms**
- Development: Jupyterlab
- Visualization: Plotly Dash, Microsoft PowerPoint Online.

**Libraries**
- Web Scraping: `beautifulsoup4` 
- Data Analysis: `pandas`, `numpy`
- Visualization:  `matplotlib`, `seaborn`, `folium`
- Machine Learning: `scikit-learn`
- Database: `sqlite3`
- Text Processing: `re`
- Formatting: `prettytable`
- Text Normalization: `unicodedata`
- Date and Time Handling: `datetime`
- Mathematical Operations: `math`
- File Handling: `io`
- Web Requests: `requests`, `js`
- Package Management: `piplite`

## Process
**Data Collection with API**
- We use a static json url to get core information about rocket launches. 
- We convert this data into a dataframe called data and reduce it to just the columns that we need, including restricting the dates of the launches to before the 13th of November 2020.
- We then use the data dataframe to call the SpaceX API and get more rocket related data such as booster version, launch site, payload, whether the rocket was reused, launch outcome etc.
- Then we populate a new dataframe called launch_data with the data acquired from the SpaceX API.
- We filter the dataframe to only include Falcon 9 launches, and handle missing values by imputing the mean.

**Data Collection with Webscraping**
- We acquire the text of a wikipedia page containing launch records, and extract column names by using the table headers.
- We then create a dictionary called launch_dict to contain information from each column of the tables. 
- We gradually extend the keys of the launch_dict with column information from the tables, by inserting values on a row by row basis.
- We then convert the launch_dict to a dataframe.  

**Data Wrangling**
- We calculate the percentage of null values for each column and check the data types. 
- We get the number of launches for each launch site, the count of each orbit type and the count of different landing outcomes such as success or failure and if the rocket landed on the ground or in the ocean. 
- We create a landing outcome label and use it to calculate the average landing success rate. 

**Exploratory Data Analysis with Pandas and Matplotlib**
- We visualize the relationships between different features of the launch data dataframe on the landing outcome.
- We use categorical plots to visualize the relationship between payload mass and flight number, flight number and launch site and payload mass and launch site. 
- We use a barplot to visualize the success rate of each orbit type.
- We then proceed to make categorical plots of flight number and orbit type and payload mass and orbit type. 
- We create a year column and use it to calculate the average yearly success rate. 
- We one-hot encode categorical columns and change the data type of all columns to float. 

**Exploratory Data Analysis with SQL**
- We acquire data and convert it to a dataframe. 
- We then convert the dataframe to an SQL table.
- We display the name of each launch site, 5 records of launch sites beginning with CCA and the total payload mass carried by boosters launched by NASA.
- We display the average payload mass carried by booster version F9 v1.1 and the date of the first successful ground pad landing. 
- We list the names of the boosters with successful landing outcomes on a drone ship with a payload mass between 4000 and 6000. 
- We get the total number of successful and failed landing outcomes and the names of boosters which have carried the maximum payload mass. 
- We display specific records for the months of the year 2015. 
- We rank landing outcomes by descending count between the dates of 2010-06-04 and 2017-03-20. 

**Interactive Visual Analytics with Folium**
- We get the coordinates for each launch site.
- We create a folium map centered at the NASA Johnson Space Center and create circle and marker icons for each launch site that indicate their location and name.
- We check the dataframe to see that each launch site is connected to a class indicating whether the landing outcome was a success or a failure. 0 indicates failure, 1 indicates success.
- We create red and green markers for failures and successes for each launch site based on the class column and place them in a marker cluster.
- We add a mouse position to the map.
- We calculate the distances between each launch site and its proximities of coast, railway, highway and city.
- We create markers specifying the distance along with lines from the launch site to the proximities. 

**Model Training and Evaluation**
- We load the original launch data and the one-hot encoded features as dataframes.
- We create the target variable Y and standardize the features X.
- We split the data into training and testing dataframes.
- We conduct the following procedures for the machine learning models logistic regression, support vector classification, decision tree and K nearest neighbors:
  - We create the model with hyperparameters and tune it using grid search with a cross validation split of 10.
  - We calculate the accuracy of the model on the test dataframe and plot its confusion matrix. 
- We compare the accuracy of each model. 

## Results
**Key insights** 
- The highest chance of landing failure is at the landing site of CCAFS LC-40, a payload mass greater than 8000 kg, an orbit type of GTO or where the booster version is v1.1.
- The positive landing outcomes are increasing each year. 
- The launch site KSC has the highest success rate.
- All launch sites are close to the ocean and far away from cities.
- The booster FT has the most successful outcomes.

**Model performance** 
- Each model has an accuracy of about 83% for the testing dataframe.
- The decision tree model has the highest accuracy for the training dataframe at almost 89%.

## Improvements
Each model was trained on a lot of different features, so the likelihood of some features adding noise is high. By reducing the scope of features used, we should be able to attain even higher accuracies for the models. 
