# UK Weather Analytics

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.7%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)

## Overview

This [research](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/report/uk_weather_analytics_report.pdf) project analyzes United Kingdom (UK) weather patterns using machine learning approaches, combining both unsupervised and supervised learning algorithms. Our analysis:

- Identifies distinct regional weather station clusters based on natural variations in weather patterns
- Develops classification models to predict station regions with high accuracy
- Investigates potential correlations between weather conditions and happiness metrics in the UK

The complete analysis workflow is automated and reproducible, with all code and data publicly available.

## Tech Stack

- **Core Language:** Python 3.7+
- **Key Libraries:**
  - NumPy: Scientific computing and array operations
  - Pandas: Data manipulation and analysis
  - Matplotlib: Data visualization
  - scikit-learn: Machine learning algorithms
  - Jupyter: Interactive notebook environment
- **Scripting:** Bash

## Datasets

Our analysis leverages two primary public datasets:

1. **UK Historic Weather Data** (Met Office)
   - Comprehensive monthly weather station records
   - Geographical distribution shown in Figure 1 below

2. **UK Personal Well-being Estimates** (Office for National Statistics)
   - Annual Population Survey data (April 2014 - March 2015)
   - Includes geographical breakdown

![map_weather_stations_60](https://github.com/nabilshadman/python-uk-weather-analytics/assets/13073461/e289bcc0-6b45-4005-9b2d-b1e283160941)  
**Figure 1:** Geographic distribution of UK weather stations

### Feature Descriptions

| Dataset | Feature | Definition |
|---------|----------|------------|
| Historic Station Data | tmax | Mean daily maximum temperature (°C) |
| | tmin | Mean daily minimum temperature (°C) |
| | af | Days of air frost |
| | rain | Total rainfall (mm) |
| | sun | Total sunshine duration (hours) |
| Personal Well-being | average rating | Mean happiness rating (0-10 scale) |

## Development Environment

### Prerequisites

- Anaconda Distribution (Recommended)
- Python 3.7 or higher
- Jupyter Notebook

### Setup Instructions

1. Install [Anaconda Distribution](https://www.anaconda.com/download)
2. Launch Anaconda Navigator
3. Start Jupyter Notebook via the "Launch" button
4. Navigate to the project directory

## Automated Workflow

Our end-to-end automated pipeline ensures reproducibility and efficient data processing. The workflow consists of five main stages:

### 1. Weather Data Acquisition
```bash
code/test_automation/download_weather_data.ipynb
```
- Downloads station data based on `stations.txt` configuration
- Creates cleaned text files without metadata

### 2. Happiness Data Collection
```bash
code/test_automation/download_happiness_data.ipynb
```
- Fetches personal well-being estimates
- Stores data in Excel format

### 3. Weather Clustering Analysis
```bash
code/test_automation/perform_clustering_weather_data.ipynb
```
- Processes and cleans station data
- Performs clustering analysis
- Generates visualizations
- Saves intermediate results for subsequent stages

### 4. Regional Classification
```bash
code/test_automation/perform_classification_weather_data.ipynb
```
- Builds classification models
- Evaluates regional prediction accuracy
- Produces performance metrics

### 5. Weather-Happiness Regression
```bash
code/test_automation/perform_regression_weather_happiness_datasets.ipynb
```
- Combines weather and well-being datasets
- Conducts regression analysis
- Generates statistical summaries

![data_science_workflow](https://github.com/nabilshadman/python-uk-weather-analytics/assets/13073461/267c5459-6bd4-46d8-8f69-785e0a9e9f52)  
**Figure 2:** Complete data science pipeline and file dependencies

## Documentation

For detailed methodology, analysis, and conclusions, please refer to our comprehensive [research report](https://github.com/nabilshadman/python-uk-weather-analytics/blob/main/report/uk_weather_analytics_report.pdf).

## Contributing

We welcome contributions! Please feel free to submit pull requests or open issues for any improvements.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## Citation

If you use this work in your research, please cite:

```bibtex
@misc{uk-weather-analytics,
  author = {Shadman, Nabil},
  title = {UK Weather Analytics},
  year = {2021},
  publisher = {GitHub},
  url = {https://github.com/nabilshadman/python-uk-weather-analytics}
}
```
