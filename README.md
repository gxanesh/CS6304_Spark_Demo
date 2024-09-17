# Spark

### General Information:

* Operating System:         Mac -> Microsoft Remote Desktop, Windows -> Default Remote Desktop, Ubuntu -> Remmina
* Machine:                  cs6304-<mst_username>-01.class.mst.edu
* User:                     <mst_username>
* Default Password:         <mst_password>



### Spark Demo
Please follow the instructions from commands.txt file.

### Install Spark
DO NOT install Spark again if it has already been installed in your VM.  
You can consider the below section as a self-note.  
We consider that Java and Hadoop are already installed.
Follow the below steps:
1. Open a terminal and enter the below commands
```
sudo apt update
```
```
wget https://dlcdn.apache.org/spark/spark-3.5.2/spark-3.5.2-bin-hadoop3.tgz
tar xvf spark-3.5.2-bin-hadoop3.tgz
rm spark-3.5.2-bin-hadoop3.tgz
sudo mv spark-3.5.2-bin-hadoop3/ /opt/spark 
```
```
sudo tee /etc/profile.d/spark.sh <<'EOF'
export SPARK_HOME=/opt/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
EOF
```
2. Go to the top right corner and select the power button -> Log Out [Don't power off]
3. Log in to the remote desktop again. Now your spark path is set and you can type "spark-shell" in the terminal to access spark.
You can access spark by typing absolute path "/opt/spark/bin/spark-shell" also.
 

### Run a scala file
Run a scala file using the following command 
spark-shell -i '/home/gs37r/test_scala.scala'


### Hadoop Commands
Open new tab on the terminal
```
hadoop fs -rm -r InputFolder				//remove inputfolder if exist
hadoop fs -mkdir InputFolder				//make the inputfolder
hadoop fs -copyFromLocal '/home/cloudera/Downloads/Spark_Demo-master/input1.txt' InputFolder
hadoop fs -copyFromLocal '/home/cloudera/Downloads/Spark_Demo-master/input2.txt' InputFolder
							//copy input1.txt and input2.txt to hdfs inputfolder
hadoop fs -rm -r OutputFolder				//remove outputfolder if exist
hadoop fs -ls OutputFolder				//see the files in outputfolder
hadoop fs -cat OutputFolder/part-00000			//see the content of the result
```

Please replace the paths according to your file locations. If you are facing issues please make sure you are giving the correct paths while loading the Hadoop file from the HDFS
