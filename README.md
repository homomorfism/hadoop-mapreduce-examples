# hadoop-mapreduce-examples
Backup from my  big data labs at University Innopolis, where we were working with hadoop jobs


Run vagrant image:
- `vagrant up`
- `vagrant ssh server-1`

How to compile hadoop jobs (I am working on a vagrant hadoop machine):
- install java on machine: 
  - `sudo apt-get update`
  - `sudo apt install openjdk-8-jdk-headless `
  - `sudo apt install default-jdk`

- make sure that you have run start-dfs.sh and start-yarn.sh
- move .java files somewhere in home directory (/home/vagrant)
- compile java code, e.x. : `javac  -cp $(hadoop classpath) WordCount.java`
- make .jar archive, e.x. : `jar -cvf WordCount.jar WordCount*.class`
- run hadoop job, e.x. : `hadoop jar WordCount.jar WordCount alice.txt OutputDirLab05`
- check output of job, e.x. : `hdfs dfs -cat OutputDirLab05/part-r-00000 | grep "rabbit"`

