# 1. UK Weather Analytics

In this [study](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/report/uk_weather_analytics_report.pdf), we analyse weather data of the United Kingdom (UK) using both unsupervised and supervised learning algorithms. Due to the natural variation of weather observed by the UK’s weather stations at the tails of their distributions, some clusters of stations are identified. The variation of weather observed regionally enables the building of classification models to predict the region of a station with decent accuracies. Also, we investigate whether the weather in the UK has a linear relationship with happiness in the UK. The analysis demonstrates that the weather in the UK has a negligible effect on happiness in the UK. The entire workflow of this analysis is automated, and the code and the data are made available for anyone interested in expanding on this work. 

**Tech Stack:** Python (numpy, pandas, matplotlib, scikit-learn, jupyter), Bash  


# 2. Data  
We use two publicly available datasets for the analysis. The first dataset is the historic [weather](https://www.metoffice.gov.uk/research/climate/maps-and-data/historic-station-data) of the UK with monthly records of weather stations, made available by the Met Office of the UK. Figure 1 maps the weather stations. The second dataset is the personal [well-being](https://www.ons.gov.uk/peoplepopulationandcommunity/wellbeing/datasets/personalwellbeingestimatesgeographicalbreakdown) estimates of the UK from the Annual Population Survey (April 2014 to March 2015) with geographical breakdown, made available by the Office for National Statistics (ONS) of the UK. Table 1 describes the features used from these datasets for the analysis.  


![map_weather_stations_60](https://github.com/nabilshadman/python-uk-weather-analytics/assets/13073461/e289bcc0-6b45-4005-9b2d-b1e283160941)  
**Figure 1:** Map of weather stations in the UK.  


| **Dataset**                       | **Feature**       | **Definition**                                                                                                                                                                                     |
|-----------------------------------|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Historic station data**         | tmax              | Mean daily maximum temperature (°C)                                                                                                                                                                |
|                                   | tmin              | Mean daily minimum temperature (°C)                                                                                                                                                                |
|                                   | af                | Days of air frost                                                                                                                                                                                  |
|                                   | rain              | Total rainfall (mm)                                                                                                                                                                                |
|                                   | sun               | Total sunshine duration (hours)                                                                                                                                                                    |
| **Personal well-being estimates** | average rating    | Mean happiness rating on a scale of 0-10 where 0   is ‘not at all happy’ and 10 is   ‘completely happy’.   The question asked in the survey was, ‘Overall, how   happy did you feel yesterday?’    |  

**Table 1:** Features from the two publicly available datasets used in this analysis.  

# 3. Environment  
We recommend installing **Anaconda Distribution** before running the notebooks as Anaconda provides a powerful package management system called Conda, which can handle complex software environments and ensures compatibility between different packages. Conda simplifies the setup process and avoids version conflicts.  

(1) Download Anaconda Distribution from this [page](https://www.anaconda.com/download) and run the installer.  

(2) Once installation is finished, launch Anaconda Navigator, which provides a graphical user interface to manage your Anaconda environment.  

(3) In Anaconda Navigator, you should see a button labeled "Launch" under the Jupyter Notebook section. Click on it to start Jupyter Notebook in your default web browser.  

(4) Navigate to the directory of this project on your system.  


# 4. Workflow    
In this section, we describe the end-to-end automation of this data science project. The entire workflow has been automated. The whole process could be rerun easily with opportunities to change parameters at certain places. As we have taken a data science pipeline approach in this project, some intermediate datasets that can be reused in later stages of the pipeline are saved to disk  for reducing computational cost.  

Here are the steps below to run the process end-to-end:  

(1) Open the folder [code](https://github.com/nabilshadman/python-uk-weather-analytics/tree/main/code), then open the folder [test_automation](https://github.com/nabilshadman/python-uk-weather-analytics/tree/main/code/test_automation). The folder has five Jupyter notebooks and two text files.  

(2) Download the weather data files by running the [download_weather_data.ipynb](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/download_weather_data.ipynb) notebook. To run the notebook, open the notebook first. Then, in the toolbar of the notebook, click on the option **Run** and then select **Run All Cells** from the dropdown menu. The notebook will start executing each cell sequentially from top to bottom. The notebook fetches data from the alterable [stations.txt](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/stations.txt) file to determine the subset of stations it needs to download the data for. The program will create a new folder called **weather_data** and will store  the original data files in there. After all the files have been downloaded, the script creates new text files where the data from the original files are copied over without the metadata at the top and at the  bottom of the original files.  

(3) Download the happiness data by running [download_happiness_data.ipynb](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/download_happiness_data.ipynb) notebook. This will create a new folder named **happiness_data** and will store the Excel file of personal well-being estimates dataset in the folder.  

(4) Perform clustering of weather data by running [perform_clustering_weather_data.ipynb](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/perform_clustering_weather_data.ipynb) notebook. This script fetches data from the [stations.txt](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/stations.txt) file, and from the text data files (with removed metadata) in the **weather_data** folder. The program cleans the data and stores the cleaned  pandas dataframes in a dictionary, which is saved to disk *(stations_dict.pkl)* in the **weather_data** folder for reuse in the regression stage. The dataset with extreme weather values is also saved in the  **weather_data** folder for reuse in the classification stage. The later parts of the program visualise data and run clustering algorithms.   

(5) Perform classification by running [perform_classification_weather_data.ipynb](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/perform_classification_weather_data.ipynb) notebook. The program loads the extreme values dataset that was saved to disk from the previous stage (i.e., *stations_aggregates.xlsx*). The latitude data is fetched from the original text data files of the weather stations. The rest of the program visualises data, runs classification algorithms, and prints results.  

(6) Perform regression of weather and happiness datasets by running [perform_regression_weather_happiness_datasets.ipynb](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/perform_regression_weather_happiness_datasets.ipynb) notebook. This notebook loads the census  regions from the [regions.txt](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/code/test_automation/regions.txt) file, happiness ratings data from the **happiness_data** folder, cleaned  weather stations data from the *stations_dict.pkl* file (created in the clustering stage), and latitude and longitude data from the original text data files of stations. The data from all these files are joined  to create the final dataset to be fed into the regression models. The rest of the program visualises data, computes summary statistics, runs linear regressions, and prints model evaluation metrics.  

Figure 2 illustrates the entire project’s workflow and the relationships of the Jupyter notebooks with the intermediate files created in the process.  

![data_science_workflow](https://github.com/nabilshadman/python-uk-weather-analytics/assets/13073461/267c5459-6bd4-46d8-8f69-785e0a9e9f52)    
**Figure 2:** End-to-end project workflow including relationships of notebooks with intermediate files.   


# 5. Report  
We provide the [report](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/report/uk_weather_analytics_report.pdf) associated with this repository where we introduce the study, discuss methods applied, analyse results, discuss automation of the analysis, and discuss conclusions.  
