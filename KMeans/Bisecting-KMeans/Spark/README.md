# Bisecting K-Means: Spark Implementation
## Requirements
 - Python 2 (version 2.7.12)
 - Hadoop (2.7.3)
 - Spark (version 2.4.4)
 - Numpy (version 1.15.1)
 
 ## Steps to Run the Script
  - Start HDFS Namenode and Datanode Servers
  - Add data to HDFS
    - `hdfs dfs -mkdir -p input`
    - `hdfs dfs -put <path_to_data_file_on_your_local_filesystem> input`
  - Change your current directory to this directory
  - Run the bkmeans.py script
    - `$SPARK_HOME/bin/spark-submit <path_to_the_bkmeans_script> <path_to_data_file_in_hdfs>
      <no_of_clusters> <no_of_iterations_for_each_bisection> <convergence_distance>`
    - Sample:
      `$SPARK_HOME/bin/spark-submit ./bkmeans.py input/TCL10M13D 5 3 0.1`

### Notes:
  - The logger is currently set to error right now. To disable that comment out 
    `sc.setLogLevel("ERROR")` in the script.
  - The code is slightly complicated but well commented and can be easily understood.
  - If your data is not tab separated, then simply change the value passed to split
    parameter of parseVector function.
