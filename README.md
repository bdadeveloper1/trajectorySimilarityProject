# trajectorySimilarityProject


README Documentation
Overview
This Python script aims to process, analyze, and visualize GPS trajectory data. It uses a dataset from Microsoft Research's GeoLife project, which provides trajectories of 182 users over a period of over three years (from April 2007 to August 2012). These GPS trajectories were collected in Beijing, China.

The script's key functionality includes extracting and loading GPS trajectory data, mapping GPS points to nodes in a road network, creating sequence input data for a neural network, and visualizing the resultant spatial-temporal embeddings.

Pre-requisites
To run this script, you will need:

Python 3.7 or above
Libraries including numpy, pandas, osmnx, scikit-learn, zipfile, datetime, concurrent.futures, torch, matplotlib, scipy, and google.colab
Access to Kaggle API to download the dataset. You'll need to upload your kaggle.json API key file.
Instructions
Setup: This script uses a specific version of numpy, scikit-learn, and osmnx. If you already have these installed, the script first uninstalls them and then reinstalls the required versions.

Dataset Download: The script downloads the GeoLife dataset from Kaggle. You'll need to upload your kaggle.json API key file.

Data Extraction: This function parallel_extract_and_load_geolife_trajectories extracts GPS trajectory data from the dataset. It uses parallel processing to speed up this operation.

Mapping GPS Points to Nodes: The script constructs a road network graph using osmnx and uses a KDTree to map each GPS point in the trajectories to the nearest node in the road network.

Preparing Input Data for Neural Network: The function prepare_input_data creates sequence input data for the neural network. Each sequence consists of node IDs from the mapped trajectories.

Neural Network Training: The script defines a PyTorch model ST2Vec, which is trained on the sequence input data using mean squared error loss. This model generates an embedding for each sequence.

Embedding Visualization: The script uses t-SNE to visualize the embeddings in a 2-dimensional space.

Running the Code
To run the code, simply execute the script in a Python environment that meets the pre-requisites mentioned above. In case you are using Jupyter notebook or Google Colab, you can run each cell sequentially from top to bottom.

Output
The script will output a scatter plot visualizing the t-SNE embeddings of the GPS sequences in a 2-dimensional space.

Dataset Description
The dataset used in this script is the GeoLife GPS Trajectory dataset collected by Microsoft Research. It contains GPS trajectories collected in a period of over three years (from April 2007 to August 2012) by 182 users. The dataset was collected with a variety of GPS loggers and devices, such as smartphones, to record users' outdoor movements with a variety of outdoor activities, such as walking, driving, cycling, and taking buses. The dataset includes information like latitude, longitude, and altitude recorded along with a timestamp.
