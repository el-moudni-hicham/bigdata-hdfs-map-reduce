# Big Data with Hadoop HDFS and Map Reduce

<img src="https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/3915b5e6-9365-4b5b-98cd-776ae4c8c17b" width="20%"/>

### What is this repository for ?

``` 
The GitHub repository Big Data with Hadoop HDFS and Map Reduce applications contains a collection
of applications that demonstrate how to use Hadoop HDFS and MapReduce to process datasets.
The applications are implemented in Java and are designed to be run on a Hadoop cluster.
```


## Table of Contents

* [Overview](#overview)
    * What is MapReduce?
    * How MapReduce Works?
* [Applications](#applications)
    * [Sales per cities](#sales-per-cities)
    * [Logs analysis](#logs-analysis)
    * [Words count](#words-count)
   
## Overview 

### What is MapReduce?
MapReduce is a programming model or pattern within the Hadoop framework that
is used to access big data stored in the Hadoop File System (HDFS).

#### How MapReduce Works?
At the crux of MapReduce are two functions: Map and Reduce. They are sequenced one after the other.

* The `Map` function takes input from the disk as <key,value> pairs, processes them, and produces another set of intermediate <key,value> pairs as output.

* The `Reduce` function also takes inputs as <key,value> pairs, and produces <key,value> pairs as output.

<img src="https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/757a8dd2-0ebd-4e8e-907a-1acbbdde383b" width="70%"/>

## Applications

### Sales per cities
This project aims to calculate the sum of sales per cities.

[link to project](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/tree/master/ventes-map-reduce)

### Logs analysis
This project aims to analyse log files and extract the number of success request for each IP address.

[link to project](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/tree/master/logs-analysis-map-reduce)

### Words count
This project aims to calculate the number of each word in a file.

[link to project](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/tree/master/words-count-map-reduce)


  
