# IBM Data Science Capstone Project: SpaceX rocket stage 1 landing outcome
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
- Web Requests: `requests`, `js`
- Package Management: `piplite`

## Process
**Data Collection with API**
- Fetched rocket launch data using a static JSON URL and filter the dataset to only include launches before the 13th of November 2020.
- Called the SpaceX API to acquire additional details such as booster version, launch site, payload, reuse status and launch outcome.
- Filtered the data to only include Falcon 9 launches and impute missing values with the mean.  

**Data Collection with Webscraping**
- Scraped a Wikipedia page containing launch records to extract table data and column headers.
- Populated a dictionary with this data, gradually adding values from each row of the table and convert this to a dataframe. 

**Data Wrangling**
- Checked the percentage of null values and incorrect data types.
- Calculated the number of launches for each launch site, orbit type and landing outcome.
- Created a landing outcome label and calculated the average landing success rate.  

**Exploratory Data Analysis with Pandas and Matplotlib**
- Visualized relationships between the landing outcome and features such as payload mass and flight number in scatterplots.
- Visualized the success rate of each orbit type in a barplot and calculated the average yearly success rate in a lineplot.
- One-hot encoded categorical columns and converted the data type of all columns to float. 

**Exploratory Data Analysis with SQL**
- Acquired data and loaded it into an SQL table.
- Performed queries to explore the launch sites, payload masses and landing outcomes.
- Ran specific queries to retrieve successful booster landings, timebased data and rankings of landing outcomes.   

**Interactive Visual Analytics with Folium**
- Generated a folium map centered at NASA Johnson Space Center with circle and marker icons for each launch site, indication their location and name.
- Created green and red markers for success and failure for each launch of a launch site.
- Calculated the distances between each launch site and the nearest coast, railway, highway and city with lines and markers specifying the distance. 

**Model Training and Evaluation**
- Loaded the original and one-hot encoded dataframes, created the target variable Y and standardized the features X.
- Split the data into training and testing dataframes and trained machine learning models such as logistic regression using hyperparameters, grid search and 10-fold cross validation.
- Evaluated machine learning models by calculating their accuracy and plotting their confusion matrix. 

## Insights 
- The highest chance of landing failure is at the landing site of CCAFS LC-40, a payload mass greater than 8000 kg, an orbit type of GTO or where the booster version is v1.1.
- The positive landing outcomes are increasing each year. 
- The launch site KSC has the highest success rate.
- All launch sites are close to the ocean and far away from cities.
- The booster FT has the most successful outcomes. 
- Each model has an accuracy of about 83% for the testing dataframe.
- The decision tree model has the highest accuracy for the training dataframe at almost 89%.

## Improvements
Each model was trained on a lot of different features, so the likelihood of one or more features adding noise is high. By reducing the scope of features used, we should be able to attain even higher accuracies for the models. 
