🔥 FireWatch: A Wildfire Risk Dashboard
FireWatch is a web-based dashboard for visualizing wildfire risk. It combines historical satellite data from Google Earth Engine (GEE), a machine learning model, and live data feeds (MODIS hotspots, OpenWeatherMap) to create a comprehensive, multi-layered interactive map.

🗺️ Key Features
ML-Powered Risk Prediction: Trains a Random Forest model on GEE data (MODIS temperature, vegetation, ERA5-Land humidity) to generate a custom wildfire risk map.

Live Data Integration: Overlays real-time fire hotspots from GEE (MODIS) and pulls live weather data from the OpenWeatherMap API.

🚨 Red Flag Warnings: The dashboard banner displays live weather and automatically issues "Red Flag Warnings" for high-risk conditions (e.g., high wind and low humidity).

Interactive Map: Built with Folium and Leaflet, the map allows users to toggle layers for:

ML-Generated Wildfire Risk
Live Fire Hotspots
Points of Interest (e.g., evacuation centers, schools)

⚙️ How It Works
The project has two main parts: a Python data pipeline that generates a map, and an HTML frontend that displays it.

Data Pipeline (Python)
The core logic is contained in pro_automated_notebook_(gee_+_ml_+_map).py. This script can be run locally or directly from the Google Colab Notebook.
It connects to Google Earth Engine (GEE) to fetch historical satellite data.
It trains a RandomForestClassifier (Machine Learning) model on this data to identify risk factors.
It uses this model to predict the current wildfire risk for a specified region (e.g., India) and exports it as an image.
It fetches live fire data (MODIS) from GEE and loads local Points of Interest (POIs).
It combines all these layers (ML risk, live fires, POIs) into a single, interactive HTML file: map_with_layers_india.html.

Frontend (Web Dashboard)

A user opens index.html and selects a region.
This opens shell.html, which is the main dashboard.
shell.html loads the pre-generated map_with_layers_india.html into an <iframe>.

At the same time, shell.html calls the OpenWeatherMap API to fetch live weather for the region and display it in the top banner, checking for "Red Flag" conditions.


Setup: 

1. Access the Colab NotebookYou need to open the notebook file, named pro_automated_notebook_(gee_+ml+_map).ipynb, within the Google Colaboratory environment.
2. Locate the Notebook URL on the project's GitHub page. (https://colab.research.google.com/drive/1XhH50E-WSM-M8uaGKA8LQXy_-JkmNlGz?usp=sharing)
3. Open in Colab: You can typically load the notebook directly by changing the GitHub URL structure or by using the "Open in Colab" badge if provided in the repository's
4. Prepare and Authenticate the EnvironmentOnce the notebook is open, execute the cells sequentially from the beginning.
5. Install Dependencies: Run the cell(s) that install the required Python libraries. Colab is often pre-configured, but you'll likely need to ensure specific packages like earthengine-api, scikit-learn, and folium are installed or updated.Authenticate Google Earth Engine (GEE): This is a critical step for data access.
6. Run the cell containing the authentication code:This will provide a link. Click the link, log in with your GEE-registered account, and copy the authorization code.Paste the code back into the input field in the Colab cell and press Enter.Configure OpenWeatherMap API Key: Locate the cell where the API key for OpenWeatherMap is configured.
7.  Paste your key into the corresponding variable.3. Execute the Data PipelineRun the remaining cells in the notebook. This step executes the core logic detailed in the project description:Fetch historical satellite data from GEE.Train the RandomForestClassifier (ML model).
8.  Predict and generate the wildfire risk map.Fetch live MODIS fire data and OpenWeatherMap data.Combine all layers into the final HTML map file: map_with_layers_india.html.
9.   Download the Output MapSince the interactive map file is generated on the Colab server, you must download it to your local machine to view the dashboard.Use the Code
10.   Download Function: Run the following code in a new cell after the generation is complete:
11.   Alternatively, use the Files tab (folder icon) on the left sidebar in Colab, right-click the file name (map_with_layers_india.html), and select Download.
12.   View the Dashboard LocallyPlace the File: Ensure the downloaded map_with_layers_india.html file is placed in the root directory of the local FireWatch GitHub repository clone.
13.   Launch the Dashboard: Double-click the index.html file in your local directory to open the dashboard in your web browser. This dashboard will load the main interface (shell.html) and integrate the map you generated via Colab.This process allows you to utilize Colab's powerful environment for the compute-intensive parts of the project before deploying the final web component locally.
