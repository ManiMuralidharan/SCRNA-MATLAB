# scRNA-seq analysis using MATLAB
# Author: Muralidharan Mani 
# Affiliation: University of Wisconsin-Madison
SCRNA MATLAB based analysis
this code in MATLAB step-by-step.

1. Setting up Your Environment

Data Location:
Ensure that your scRNA-seq data is located in the specified folder C:\Users\mmani\Desktop\PD-L1.
Within that folder, you should have four subfolders: BP_iso, BP_PD_1, BS_iso, and BS_PD_1.
Each of these subfolders should contain the files barcodes.tsv, features.tsv, and matrix.mtx.
MATLAB Working Directory:
Open MATLAB and set your current working directory to the folder where you want to save your analysis results (e.g., your desktop or a dedicated analysis folder).
2. Running the Data Loading Code

Copy and Paste:
Copy the provided MATLAB code and paste it into a new MATLAB script (create a new .m file).
Run the Script:
Run the script. MATLAB will:
Load the data from each of the four folders.
Display the size of the loaded matrices.
Store the data in a structure named data.
3. Normalizing the Data

Select Dataset:
The example uses data.BP_iso.expression_matrix, but you can choose any of the four datasets (e.g., data.BP_PD_1.expression_matrix).
Copy and Paste:
Copy the normalization code and paste it into your MATLAB script (after the data loading code).
Run the Code:
Run this section of the code. MATLAB will:
Calculate the total counts per cell.
Normalize the expression data.
Log-transform the normalized data.
Convert the sparse matrix to a full matrix.
4. Performing PCA

Copy and Paste:
Copy the PCA code and paste it into your MATLAB script.
Run the Code:
Run this section of the code. MATLAB will:
Perform PCA on the normalized data.
Plot the explained variance.
Determine the number of principal components to keep.
Extract the reduced data (scores).
Adjusting NumComponents:
The code sets 'NumComponents', 50. You can change this number if you have a very large number of genes.
Adjusting explained_variance_threshold:
The code sets explained_variance_threshold = 95;. Depending on your data, you might want a different threshold.
5. Performing K-means Clustering

Copy and Paste:
Copy the K-means clustering code and paste it into your MATLAB script.
Run the Code:
Run this section of the code. MATLAB will:
Perform K-means clustering on the PCA-reduced data.
Plot the PCA result colored by clusters.
Adjusting num_clusters:
The code sets num_clusters = 10;. This is a critical parameter.
Use the elbow method or silhouette scores to determine the optimal number of clusters.
6. Performing UMAP

Python Setup:
Ensure you have Python installed and that the umap-learn library is installed.
You might need to configure MATLAB to use your Python environment.
Copy and Paste:
Copy the UMAP code and paste it into your MATLAB script.
Run the Code:
Run this section of the code. MATLAB will:
Convert the reduced data to a Python-compatible format.
Run UMAP.
Convert the UMAP embedding back to MATLAB.
Plot the UMAP result colored by clusters.
Parameter Tuning:
Experiment with n_neighbors, min_dist, and metric to optimize UMAP.
7. Saving and Loading Data

Saving All Variables:
To save all variables, run:
Matlab

save('my_large_data.mat', '-v7.3');
Saving Specific Variables:
To save specific variables, run:
Matlab

save('my_large_data.mat', 'data', 'reduced_data', 'umap_embedding', 'cluster_idx', '-v7.3');
Loading Data:
To load the data later, run:
Matlab

load('my_large_data.mat');
Important Notes:

Memory: scRNA-seq data can be very large. If you encounter memory issues, consider:
Using sparse matrices where possible.
Filtering out low-quality cells and genes.
Increasing your computer's RAM.
Parameter Optimization:
The parameters for K-means and UMAP should be carefully optimized.
Use visualization tools and evaluation metrics to guide your parameter selection.
Further Analysis:
This script provides a foundation for scRNA-seq analysis.
You can extend it with differential gene expression analysis, cell type annotation, and other downstream analyses.
Python:
Pay close attention to the python enviroment requirements, and make sure MATLAB can access the python module.
