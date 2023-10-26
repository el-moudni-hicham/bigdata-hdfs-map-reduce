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

### How MapReduce Works?
At the crux of MapReduce are two functions: Map and Reduce. They are sequenced one after the other.

* **The Map** function takes input from the disk as `<key,value>` pairs, processes them, and produces another set of intermediate `<key,value>`pairs as output.

* **The Reduce** function also takes inputs as `<key,value>` pairs, and produces `<key,value>` pairs as output.

Exemple to count letters in a text file :
<p align="center">
   <img src="https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/757a8dd2-0ebd-4e8e-907a-1acbbdde383b" width="70%"/>
</p>

## Applications

### Sales per cities
This project aims to calculate the sum of sales per cities.

[link to project](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/tree/master/ventes-map-reduce)

Here are the steps to create the Hadoop MapReduce Project in Java :

**Step 1 : Create classes.**

* Implementation of Mapper Class :

```java
public class SalesMapper extends Mapper<LongWritable, Text, Text, DoubleWritable> {
    @Override
    protected void map(LongWritable key, Text value, Context context) throws IOException, InterruptedException {
        String[] tokens = value.toString().split(",");
        context.write(new Text(tokens[1]), new DoubleWritable(Double.valueOf(tokens[3])));
    }
}
```

* Implementation of ReducerClass :

```java
public class SalesReducer extends Reducer<Text, DoubleWritable, Text, DoubleWritable> {
    @Override
    protected void reduce(Text key, Iterable<DoubleWritable> values, Context context) throws IOException, InterruptedException {
        long sum = 0;
        for (DoubleWritable value : values) {
            sum += value.get();
        }
        context.write(key, new DoubleWritable(sum));
    }
}
```

* Implementation of Driver Class :

```java
public class SalesDriver {
    public static void main(String[] args) throws Exception {
        Configuration conf = new Configuration();
        Job job = Job.getInstance(conf, "Sales");
        job.setJarByClass(SalesDriver.class);
        job.setMapperClass(SalesMapper.class);
        job.setReducerClass(SalesReducer.class);
        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(DoubleWritable.class);
        FileInputFormat.addInputPath(job, new Path(args[0]));
        FileOutputFormat.setOutputPath(job, new Path(args[1]));
        System.exit(job.waitForCompletion(true) ? 0 : 1);
    }
}
```

**Step 2 : Creating the Jar File of the Project.**

by running command `maven install` and the jar will be appear in the target folder :

![image](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/9eba8035-ee49-4ac8-80a3-d5d06e893055)

**Step 3 : Creating the Text File.**

![image](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/c507d617-ce31-4692-9222-cfe927ba1bd3)

**Step 4 : Putting the file in HDFS root.**

by using the below command :

`hdfs dfs -put sales.txt /`

**Step 5 : Execute the Hadoop MapReduce application.**

by using the below execution command :

`hadoop jar sales-map-reduce-2.jar SalesDriver /sales.txt /salesPerCity`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/4813bf37-8bda-4fc6-97d0-47057b674ece)
![image](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/4c7c4aba-ff5a-46ce-b3ea-befb3bb62ac7)

**Step 5 : Exploring the output result.**

by using the below command :

`hdfs dfs -cat /salesPerCity/part-r-00000`

![image](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/assets/85403056/5dc9d52c-b1cd-4dcf-85a4-3528814505a7)


### Logs analysis
This project aims to analyse log files and extract the number of success request for each IP address.

[link to project](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/tree/master/logs-analysis-map-reduce)

### Words count
This project aims to calculate the number of each word in a file.

[link to project](https://github.com/el-moudni-hicham/bigdata-hdfs-map-reduce/tree/master/words-count-map-reduce)


  
