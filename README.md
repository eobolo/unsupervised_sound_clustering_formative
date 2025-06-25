# Sound Data Clustering Project

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)![NumPy](https://img.shields.io/badge/NumPy-yellow?logo=numpy&logoColor=white)![SciPy](https://img.shields.io/badge/SciPy-lightgreen?logo=scipy&logoColor=white)![scikit-learn](https://img.shields.io/badge/scikit--learn-orange?logo=scikit-learn&logoColor=white)![Matplotlib](https://img.shields.io/badge/Matplotlib-purple?logo=matplotlib&logoColor=white)![librosa](https://img.shields.io/badge/librosa-red?logo=librosa&logoColor=white)![Jupyter](https://img.shields.io/badge/Jupyter-black?logo=jupyter&logoColor=white)

## Overview
This project explores clustering techniques on sound data using Mel Spectrogram features. It implements dimensionality reduction with PCA and t-SNE, followed by K-Means and DBSCAN clustering, optimized using the elbow method, silhouette score, and Davies-Bouldin Index. The goal is to compare clustering performance across reduction methods and algorithms, leveraging non-linear structures in sound patterns.

## Data Loading and Access

### Data Source
The dataset is available at: [drive](https://drive.google.com/file/d/1bme1IuScdIWjzFkYPOcWzFOgD50MS_zR/view). This Google Drive link contains the sound data for clustering analysis.

### Fetching Data from Google Drive
1. Download the file from the provided link.
2. Unzip the downloaded file to extract the sound data.
3. Upload the unzipped folder to your Google Drive under the path: `/unsupervised/sound/`.
4. Mount Google Drive in Colab which is already provided in the notebook.
5. Load the data from the path: `/content/drive/My Drive/unsupervised/sound/<thefoldername>/`.

## Features
- **Data Loading and Feature Extraction:** Extracts Mel Spectrogram features from sound files.
- **Dimensionality Reduction:** Applies PCA (3 components, 77.62% variance) and t-SNE (3 components, perplexity=30) for visualization.
- **Clustering:** Implements K-Means (optimized k=7 on PCA, k=10 on t-SNE) and DBSCAN (optimized eps=13, min_samples=8 on PCA, eps=1, min_samples=8 on t-SNE).
- **Evaluation:** Assesses cluster compactness and separation with silhouette score, Davies-Bouldin Index, and visualizations.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/eobolo/unsupervised_sound_clustering_formative.git
   cd unsupervised_sound_clustering_formative
   ```
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
## Results
- **PCA Best:** K-Means (k=7) with Silhouette 0.35, DBI 0.88; DBSCAN (eps=13, min_samples=8) with Silhouette 0.25, DBI 0.77.
- **t-SNE Best:** K-Means (k=10) with Silhouette 0.37, DBI 0.90; DBSCAN (eps=1, min_samples=8) with Silhouette 0.61, DBI 0.52 (noted for potential overfitting).
- **Conclusion:** t-SNE’s non-linear reduction enhances K-Means (k=10) slightly over PCA, while DBSCAN benefits from small eps on t-SNE but may overfit.

## Challenges
- High-dimensional Mel Spectrograms (128+ dimensions) were unvisualizable without reduction, leading to cluttered plots.
- DBSCAN on t-SNE produced errors with large eps (e.g., eps=7, 1 cluster), highlighting parameter sensitivity.