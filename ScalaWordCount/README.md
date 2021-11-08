Prerequiries: 
- vagrant image should be taken from this repository: [vagrant-hadoop-hive-spark](https://github.com/martinprobson/vagrant-hadoop-hive-spark).
- Everything should be run from root.
- Commands for launching hdfs should be taken from this repository: [vagrant-hadoop-spark](https://github.com/s3u/vagrant-hadoop-spark).
- Scala and sbt should be installed with [sdkman.io](https://sdkman.io/).
- Scala project should look like in this folder
- Scala project should be build with `sbt package`.
- Make sure that `.jar` executable in `target/` folder contains `MainClass.class` instance ([Viewing the Contents of a JAR File](https://docs.oracle.com/javase/tutorial/deployment/jar/view.html)).


Running job: 
```bash 
root@node1:~$ spark-submit --class MainClass --master yspark://node1:7077 --num-executors 10     --executor-cores 2     /usr/local/spark-2.3.0-bin-hadoop2.7/examples/myWordCountJob/target/scala-2.11/spark-wordcount_2.11-1.0.jar alice.txt alica_wordcount_scala_spark
```


Output of running job:
```bash

root@node1:~# hdfs dfs -ls
SLF4J: ...
Found 4 items
drwxr-xr-x   - root supergroup          0 2021-11-08 06:20 .sparkStaging
drwxr-xr-x   - root supergroup          0 2021-11-08 07:14 alica_wordcount_scala_spark
-rw-r--r--   1 root supergroup     173595 2021-11-08 06:17 alice.txt
drwxr-xr-x   - root supergroup          0 2021-11-08 06:20 output

root@node1:~# hdfs dfs -cat output/part-0000* | tail   
SLF4J: ...
(Magpie,1)
(‘on,1)
(always,11)
(now--but,1)
(Foundation,14)
(silence,,2)
(louder,1)
(up:,1)
(passionate,1)
(became,2)
root@node1:~# 
```
