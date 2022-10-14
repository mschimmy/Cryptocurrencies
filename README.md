# Cryptocurrencies

## Overview of Analysis
The client, Accountability Accounting, is a prominent investment bank and is interested in offering a new cryptocurrency investment portfolio for its customers. The client requests a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.
The cryptocurrency data was provided by the client and must undergo processing to fit the machine learning model.

### Purpose
The purpose of this analysis is to discover trends in the cryptocurrency dataset and group the cryptocurrencies using unsupervised machine learning algorithms. The results of the grouping algorithm will be visualized and shared with the client so they may make data-driven decisions to invest in cryptocurrencies.


## Process & Results

### Preprocessing the Data for PCA
Five preprocessing steps were performed on the dataset to organize it through formatting, cleaning, and sampling so that it is set up for the unsupervised learning model. The cryptocurrency dataset was filtered to show only cryptocurrencies that are currently being traded, have a working algorithm and have coins being mined, and any cryptocurrencies with null values were removed. The resulting dataframe was then encoded using get_dummies() to ensure only numerical data is used, and the values were scaled with StandardScaler.fit_transform() to ensure that the variance between the values won't skew results.

### Reducing Data Dimensions Using PCA
The Principal Component Analysis (PCA) algorithm was applied to the scaled data and reduced the dimensions of the dataset to three principal components. The results of the PCA algorithm are displayed in the pca_df below.
![PCA DataFrame](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/PCA_df.png)
<sub>PCA DataFrame</sub>

### Clustering Cryptocurrencies Using K-Means
An elbow curve was created to determine the best value for K. The result of the elbow curve is below and demonstrates that the best value for K is four.
![Elbow Curve](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/Elbow_Curve.png)
<sub>Elbow Curve</sub>

The K-Means model was initialized with the desired number of clusters (four) and tested on the pca_df to identify and predict clusters. The results of the K-Means algorithm are shown in the "Class" column of the clustered_df below, along with the PCA results and the cryptocurrency features.
![Clustered DataFrame](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/Clustered_df.png)
<sub>Clustered DataFrame</sub>

### Visualizing Cryptocurrencies Results
The results of the clustered_df were visualized in a 3D scatter plot using Plotly Express and hvplot to show the distinct groups that correspond to the three principal components.
![Clustered DataFrame 3D Scatter Plot](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/clustered_df_3D_scatter_plot.png)
<sub>Clustered DataFrame 3D Scatter Plot</sub>

The following table shows the currently tradable cryptocurrencies using the hvplot.table() function. The total number of tradable cryptocurrencies is 532.
![Tradeable Cryptocurrencies Table](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/tradable_cryptocurrencies_table.png)
<sub>Tradable Cryptocurrencies Talbe</sub>

The "Total Coin Supply" and Total Coins Mined columns were scaled using MinMaxScaler.fit_transform() method to create the plot_df. This DataFrame was then used to create a scatter plot that visualizes the tradable cryptocurrencies.
![Plot DataFrame](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/plot_df.png)
<sub>Plot DataFrame</sub>

![Tradable Cryptocurrencies Scatter Plot](https://github.com/mschimmy/Cryptocurrencies/blob/main/Resources/tradable_cryptocurrencies_scatter_plot.png)
<sub>Tradable Cryptocurrencies Scatter Plot</sub>
