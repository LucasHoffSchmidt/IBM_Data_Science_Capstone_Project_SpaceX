<img width="298" height="56" alt="image" src="https://github.com/user-attachments/assets/6f0932e2-7859-4a65-bebe-c3d3b6f79ffd" /># IBM Data Science Capstone Project: SpaceX rocket stage 1 landing outcome
Developing a classification model for predicting whether or not SpaceX will successfully land stage 1 of a rocket for a given launch, to determine if the competitor SpaceY can compete against it.

## Quick Links
- Detailed overview of the project process: [Project Report](https://github.com/LucasHoffSchmidt/IBM_Data_Science_Capstone_Project_SpaceX/blob/main/Data_Science-SpaceX-Report.pdf)
- Jupyter Notebooks of the development process of the classification model: [Jupyter Notebooks](https://github.com/LucasHoffSchmidt/IBM_Data_Science_Capstone_Project_SpaceX/tree/main/Jupyter_Notebooks)
- Plotly Dash screenshots of launch results across launch sites and payload ranges: [Plotly Dash Screenshots](https://github.com/LucasHoffSchmidt/IBM_Data_Science_Capstone_Project_SpaceX/tree/main/Plotly_Dash_Screenshots)
- Other projects I have made: [Portfolio Website](https://lucashoffschmidt.github.io/)

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
- Web Requests: `requests`, `fetch`
- Package Management: `piplite`

## Process
**Data Collection with API**
- Imported necessary packages (requests, pandas, numpy, datetime).
- Fetched rocket launch data using a static JSON URL.
<img src="images/api_fetch.jpg" alt="Fetching rocket launch data from a static JSON URL" width="350">

- Created a subset dataframe of the rocket launch data.
<img src="images/api_subset.jpg" alt="Subsetting the dataframe to a select few features" width="800">

- Created empty list variables for the full launch dataframe.
<img src="images/api_variables.jpg" alt="Creating empty lists for the full launch dataframe" width="150">

- Created helper functions to acquire specific data from the SpaceX API.
<img src="images/api_helper.jpg" alt="Helper function that fetches data from the spaceX API" width="700">

- Called the helper functions with the subset dataframe to create the full launch dataframe.
<img src="images/api_helper_call.jpg" alt="Calling helper function" width="200">

- Filtered the data to Falcon 9 launches.
<img src="images/api_filter.jpg" alt="Filtering data to only falcon 9 launches" width="700">

- Imputed missing values with the mean payload mass.  
<img src="images/api_impute.jpg" alt="Imputing NaN values with the mean payload mass" width="600"><br><br>

**Data Collection with Webscraping**
- Imported necessary packages (requests, BeautifulSoup, re, unicodedata, pandas)
- Fetched and stored html from the falcon9 launch page in BeautifulSoup object
<img src="images/web_store_html.jpg" alt="Storing HTML in BeautifulSoup object" width="400">

- Found and stored first launch table
<img src="images/web_store_table.jpg" alt="Storing first launch table in variable" width="300">

- Used helper function to extract table headers
- Used helper function to loop through the launch table, identifying rows that represented a valid flight number and extracting all launch details from that row into a dictionary
- Converted the dictionary to a dataframe

<img src="images/web_convert_dataframe.jpg" alt="Converting dictionary to dataframe" width="700"><br><br>

**Data Wrangling**
- Imported necessary packages (pandas, numpy).
- Checked the percentage of null values for each column.
<img src="images/wrangling_nulls.jpg" alt="Checking relative amount of nulls for each column" width="250">

- Checked that datatypes were correct.
<img src="images/wrangling_datatypes.jpg" alt="Checking that datatypes are correct" width="90">

- Calculated the number of launches for each launch site, orbit type and landing outcome.
<img src="images/wrangling_value_counts.jpg" alt="Calculating counts for each category" width="370">

- Created a bad outcomes set.
<img src="images/wrangling_bad_outcomes.jpg" alt="Creating a set of bad outcomes" width="420">

- Created a landing outcome list, specifying 0 for failed outcomes and 1 for successful outcomes and converted it into a dataframe column.
<img src="images/wrangling_landing_class.jpg" alt="Creating a landing class column with bad outcomes as 0 and good outcomes as 1" width="270">

- Calculated the average landing success rate.

<img src="images/wrangling_success_rate.jpg" alt="Calculating the average success rate" width="150"><br><br>

**Exploratory Data Analysis with Pandas and Matplotlib**
- Imported necessary packages (pandas, numpy, matplotlib.pyplot, seaborn, fetch, io)
- Acquired rocket launch dataset from an URL
<img src="images/mat_data.jpg" alt="Fetching rocket launch data from an URL" width="800">

- Visualized relationships between the landing outcome and different features.
<img src="images/mat_catplot.jpg" alt="Categorical plot between launch site, flight number and landing class" width="800">
<img src="images/mat_success_orbit.jpg" alt="Bar plot of success rate by orbit type" width="500">

- Visualized the average yearly success rate.
<img src="images/mat_avg_success.jpg" alt="Average yearly success rate of landing outcome in a lineplot" width="500">

- One-hot encoded categorical columns (new binary column for each category)
<img src="images/mat_one_hot.jpg" alt="One-hot-encoding categorical variables" width="900">

- Converted the data type of all columns to float (since all columns are numerical now)
<img src="images/mat_convert_to_float.jpg" alt="Converting all columns to the float data type" width="400"><br><br>

**Exploratory Data Analysis with SQL**
- Imported necessary packages (sqlite3, prettytable, pandas)
- Acquired data and loaded it into an SQL table.
<img src="images/sql_create_table.jpg" alt="Creating sql table" width="600">

- Performed queries to explore the launch site data
<img src="images/sql_task1.jpg" alt="Unique launch sites" width="400">
<img src="images/sql_task2.jpg" alt="Launch sites that begin with CCA" width="850">
<img src="images/sql_task3.jpg" alt="Total payload mass carried by boosters launched by NASA" width="500">
<img src="images/sql_task4.jpg" alt="Average payload carried by booster version F9 v1.1" width="400">
<img src="images/sql_task5.jpg" alt="Date when the first successful landing occurred" width="550">
<img src="images/sql_task6.jpg" alt="Boosters with successful landings on drone ship with payload mass between 4000 and 6000" width="800">
<img src="images/sql_task7.jpg" alt="Total number of successful and failure mission outcomes" width="650">
<img src="images/sql_task8.jpg" alt="Booster version that have carried the maximum payload mass" width="700">
<img src="images/sql_task9.jpg" alt="Landing outcomes, booster versions and launch sites on drone shops for the months in 2015" width="850">
<img src="images/sql_task10.jpg" alt="Ranking landing outcomes by count" width="850"><br><br>

**Interactive Visual Analytics with Folium**
- Imported necessary packages (folium, pandas, MarkerCluster, MousePosition, DivIcon, fetch, io, sin, cos, sqrt, atan2, radians)
- Generated a folium map centered at NASA Johnson Space Center with circle and marker icons for each launch site, indicating their location and name.
<img src="images/folium_map.jpg" alt="Folium map showing launch sites locations and names" width="800">

- Created red and green markers for success and failure for each launch of a launch site.
<img src="images/folium_red_and_green.jpg" alt="Red and green markers specifying failed and successful launches" width="400">

- Calculated the distances between each launch site and the nearest coast, railway, highway and city with lines and markers specifying the distance.

<img src="images/folium_distances.jpg" alt="Distance between launch site and coast" width="800"><br><br>

**Model Training and Evaluation**
- Imported necessary packages (pandas, numpy, matplotlib, seaborn, preprocessing, train_test_split, GridSearchCV, LogisticRegression, SVC, DecisionTreeClassifier and KNeighborsClassifier)
- Loaded the original and one-hot encoded dataframes (for the y and X variables respectively)
- Created the target variable Y and standardized the features X.
<img src="images/machine_x_y.jpg" alt="Specifying y and X variables" width="350">

- Split the data into training and testing dataframes
<img src="images/machine_training_testing.jpg" alt="Splitting dataset into training and testing" width="700">

- Used gridsearch to find the best hyperparameters for different machine learning models, such as logistic regression
<img src="images/machine_gridsearch.jpg" alt="Performing a grid search to find the best hyperparameters for logistic regression" width="700">

- Evaluated machine learning models by calculating their accuracy on the test data and plotting their confusion matrix.
<img src="images/machine_evaluate_log.jpg" alt="Evaluating the accuracy of logistic regression on the test dataset" width="250">
<img src="images/machine_confusion.jpg" alt="Plotting the confusion matrix of logistic regression for the test set accuracy" width="500">

- Compared training and testing accuracy for the machine learning models
<img src="images/machine_overview.jpg" alt="Printing an overview of the accuracies of the different machine learning models" width="800"><br><br>

**Plotly Interactive Visualization**
- Loaded the launch dataset with minimum and maximum payload
- Created a dash app layout
- Created a pie chart specifying the launch outcome for different launch sites
- Created a scatter chart specifying launch outcome for payload mass and booster versions<br><br>

## Insights 
- The highest chance of landing failure is at the landing site of CCAFS LC-40, a payload mass greater than 8000 kg, an orbit type of GTO or where the booster version is v1.1.
- The positive landing outcomes are increasing each year. 
- The launch site KSC has the highest success rate.
- All launch sites are close to the ocean and far away from cities.
- The booster FT has the most successful outcomes. 
- Each model has an accuracy of about 83% for the testing dataframe.
- The decision tree model has the highest accuracy for the training dataframe at almost 89%.

## Improvements
We used 83 features to train the models, so performing a more rigorous feature selection process to determine the very best features, may help to maximize the generalization capability of the models. 
