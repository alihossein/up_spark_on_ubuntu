# Install Packages Required for Spark
```
sudo apt install default-jdk scala git -y

java -version
scala -version
git --version
```

# Download and Set Up Spark on Ubuntu
```
wget https://downloads.apache.org/spark/spark-3.0.1/spark-3.0.1-bin-hadoop2.7.tgz

tar xvf spark-*

sudo mv spark-3.0.1-bin-hadoop2.7 /opt/spark
```

# Configure Spark Environment
```
vi ~/.profile
```
```
# test spark
export SPARK_HOME=/home/alihossein/Documents/sheypoor_test/spark
export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
export PYSPARK_PYTHON=/usr/bin/python3
export PYSPARK_DRIVER_PYTHON=ipython3
```

```
source ~/.profile
```
# Start Standalone Spark Master Server
```
start-master.sh
```

# see panel
```
http://localhost:8080/
```

# Start Spark Slave Server (Start a Worker Process)
```
start-slave.sh spark://ubuntu1:7077
```

#### Now that a worker is up and running, if you reload Spark Master’s Web UI, you should see it on the list

# Specify Resource Allocation for Workers

#### number of cores by passing the -c flag to the ``` start-slave ``` command.
```
start-slave.sh -c 1 spark://ubuntu1:7077
```
#### To start a worker and assign it a specific amount of memory, add the -m option and a number. For gigabytes, use G and for megabytes, use M.
```
start-slave.sh -m 512M spark://ubuntu1:7077
```
# Test Spark Shell

```
spark-shell
```
#### ou should get a screen with notifications and Spark information. Scala is the default interface, so that shell loads when you run spark-shell.

# Test Python in Spark
```
pyspark
```
# Basic Commands to Start and Stop Master Server and Workers
#### To start a master server 
```
start-master.sh
```
#### To stop the master
```
stop-master.sh
```
#### To stop a running worker
```
stop-slave.sh
```
#### start both master and server
```
start-all.sh
```
#### can stop all instances
```
stop-all.sh
```
