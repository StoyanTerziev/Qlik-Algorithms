# Qlik-Algorithms
Different stand-alone algorithms grouped in libraries


# Clustering animation chart in QlikView

Sub KMeansCluster_RandomizedElements(Elements, xAxisLen, yAxisLen, Clusters, EnableLog, StoragePath)

Arguments Explained:

Elements = That's the number of random elements that we will plot on the scatterPlot
xAxisLen = Maximum random value on the x axis
yAxisLen = Maximum random value on the y axis
Clusters = That's the K - number of cluster groups where the elements will be assigned
EnableLog = 1 to enable Log; 0 to disable log
StoragePath = dedicated folder to store all the temp files to avoid bandwidth issues with the RAM during exectuion


1. Put the code below in your QlikView app and hit Reload.

//Load the Random Clustering function
$(Include=https://raw.githubusercontent.com/StoyanTerziev/Qlik-Algorithms/master/Clusters.qvs);
//Call function with the appropriate settings
Call KMeansCluster_RandomizedElements(1000, 800, 500, 4, 0, 'C:\Clusters\')
//Load the clustering data output
ClustersData: LOAD * FROM $(vClustersStorePath)\ClusterState*.qvd (qvd);

2. Don't fortet to change the 'C:\Clusters\' location variable.
3. Craete a Scatter Chart
   Add the 3 dimensions: State, Dimension, Flag
   Add the 3 measures: Avg(MeasureA); Avg(MeasureB); if(Flag='Attribute', 10, 100)
   In the Dimensions tab hit 'Animate' and click Animate on First Dimension.
  
